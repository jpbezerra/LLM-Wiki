# OTIMIZAÇÃO DE TOKENS E ROTEAMENTO DE MODELOS

!!! note "Correção de premissa"
    O ponto de partida foi um "conceito de LLM wiki" atribuído ao Spotify — mas esse termo **não aparece** no artigo original deles. O que o Spotify descreveu é **roteamento de modelos** (model routing/delegation): desviar tarefas mecânicas do modelo caro para um modelo barato. A ideia de "wiki" persistente da codebase é um padrão relacionado, mas diferente — coberto na seção 3.

## 1. O caso Portal/Spotify

Artigo: [Portal by Spotify cut my Claude Code token usage by 90%](https://engineering.atspotify.com/2026/9/portal-by-spotify-cut-my-claude-code-token-usage-by-90).

**Ideia central**: a maior parte do que um agente de código faz **não é raciocínio, é I/O** — ler vários arquivos grandes para responder uma pergunta simples, ou gerar boilerplate repetitivo (testes, stubs de config) seguindo padrões já existentes. Isso consome tokens caros do modelo principal sem precisar da "inteligência" dele.

### Arquitetura em 3 camadas

1. **Modes** (agentes declarativos leves, "Lambda para agentes") — dois modes criados, ambos rodando num modelo barato (Gemini 2.5 Flash):
      - `bulk-reader`: lê arquivos grandes e devolve um resumo estruturado em bullets;
      - `code-writer`: gera código seguindo o padrão de um arquivo de referência.
2. **Hooks** no Claude Code que interceptam chamadas de leitura: se um arquivo passa de um limite de linhas (default **350**), a leitura é bloqueada e o Claude é instruído a usar o `bulk-reader` em vez de ler o arquivo inteiro.
3. **Scripts + Skills** que ensinam o Claude quando e como chamar esses modes via CLI.

**Resultado reportado**: testado num monorepo Java em quatro cenários, comparando tokens que o Claude consumiria lendo arquivos diretamente vs. consumindo o resumo do `bulk-reader` — **economia média em torno de 90%** nas leituras em massa.

### O que não funciona (limites admitidos pelo artigo)

- **Não dá para delegar edição** — o resumo do modelo worker não tem números de linha confiáveis; para editar, o Claude principal ainda precisa ler a seção específica diretamente.
- **Não dá para delegar raciocínio** — o modelo worker encontrou padrões superficiais, mas perdeu um bug sutil de thread-safety que o modelo principal pegou na hora. Debugging, decisões arquiteturais e código crítico de segurança ficam fora da delegação.
- **Latência**: cada delegação é uma ida e volta de rede (10–30s) — só compensa para leituras grandes (daí o threshold de linhas).

### Quando vale a pena aplicar

- Faz sentido em **bases de código grandes**, com muita leitura repetitiva de arquivos extensos e geração de boilerplate previsível (testes seguindo padrão, stubs). Se o uso é majoritariamente análise profunda, debugging ou decisões de arquitetura, a economia é marginal.
- É otimização de **contexto de time/empresa em projetos maiores**, não de uso pessoal casual: monorepos grandes, times já gastando centenas de dólares por dev/mês em tokens, fluxos repetitivos. Em projetos pequenos, o overhead de montar hooks/scripts/modes provavelmente não compensa.
- O princípio generaliza bem mesmo sem a infraestrutura específica do Spotify (Portal/AiKA): "nem toda tarefa do agente precisa do modelo mais caro" — separar I/O mecânico de raciocínio e rotear o primeiro para algo mais barato vale a pena com qualquer ferramenta.

## 2. Roteamento dinâmico nativo no Claude Code

Sem precisar de infraestrutura tipo Portal, o próprio Claude Code já tem um mecanismo equivalente: **subagents** com campo `model` no frontmatter.

```yaml
---
name: file-reader
description: Lê e resume arquivos grandes da codebase
model: haiku
tools: Read, Grep, Glob
---
```

Quando o modelo principal precisa entender vários arquivos, dispara esse subagent (via Task tool) rodando em Haiku, que devolve um resumo sem o conteúdo bruto entrar no contexto do modelo caro — essencialmente o mesmo padrão do Spotify, nativo.

!!! warning "Ponto de atenção"
    Há relatos de bugs no roteamento de modelo de subagents (campo `model` sendo ignorado em certas versões/condições, especialmente combinado com variáveis de ambiente tipo `CLAUDE_CODE_SUBAGENT_MODEL`). Vale testar e confirmar que o subagent realmente roda no modelo barato antes de contar com isso para economia de custo.

## 3. O padrão "codebase wiki" — cache persistente, não delegação por chamada

O que inspirou a pergunta original (gerar uma wiki/resumo persistente da codebase, usada depois como contexto pelo modelo bom) é um padrão **diferente e complementar** ao Portal. O Portal faz delegação **por chamada** (cada pergunta dispara nova leitura pelo modelo barato, nada é persistido). Uma wiki persistente é mais próxima de um **cache/índice**, ainda mais eficiente porque não se paga o custo de I/O repetidamente.

Na prática: um processo (modelo barato ou batch) varre a codebase e gera arquivos de resumo por módulo/serviço/padrão arquitetural (`docs/wiki/service-x.md`), versionados no repo. O modelo principal lê primeiro o resumo e só vai ao código-fonte quando precisa editar algo específico. Esse padrão já existe informalmente como `CLAUDE.md`/`ARCHITECTURE.md` mantidos manualmente — a diferença proposta é **automatizar** a geração/atualização com um modelo barato.

**Quando usar cada abordagem:**

- **Projetos grandes e estáveis** → wiki persistente (paga o custo de gerar o resumo uma vez, não a cada pergunta).
- **Código que muda muito rápido** → a wiki fica desatualizada rápido; delegação por chamada é mais confiável, mesmo custando mais por chamada.
- **Ideal** → combinar os dois: wiki como primeira camada de contexto (barata, resumo geral), delegação sob demanda como segunda camada quando a wiki não é suficiente ou está desatualizada — a arquitetura de 3 camadas do Spotify mais uma camada de cache.

## 4. Implementação completa de referência (kit `codebase-wiki`)

Estrutura de arquivos combinando wiki + subagents + hook:

```
.claude/
├── settings.json          # hooks (intercepta leituras grandes)
├── agents/
│   ├── bulk-reader.md      # subagent, model: haiku
│   └── code-writer.md      # subagent, model: haiku
├── skills/
│   └── codebase-wiki/
│       └── SKILL.md        # ensina quando/como usar a wiki + subagents
├── hooks/
│   └── check-file-size.sh  # script chamado pelo hook
└── context/
    └── wiki/
        ├── auth-service.md
        ├── payments-module.md
        └── _index.md        # mapa geral, aponta pros outros arquivos
```

### Subagents

```yaml
---
name: wiki-writer
description: Gera/atualiza resumos de módulos da codebase em context/wiki/
model: haiku
tools: Read, Grep, Glob, Write
---
Você resume código para uma wiki de referência. Leia os arquivos do
módulo indicado e escreva um resumo estruturado em bullets:
responsabilidade do módulo, principais funções/classes com assinatura,
padrões de nomenclatura, dependências externas. Nunca inclua código
completo. Seja denso e objetivo.
```

Um segundo subagent, `bulk-reader`, faz a mesma coisa sob demanda (pergunta pontual, sem persistir), para quando a wiki não cobre o necessário.

### Hook

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Read",
        "hooks": [{ "type": "command", "command": ".claude/hooks/check-file-size.sh" }]
      }
    ]
  }
}
```

```bash
#!/usr/bin/env bash
# PreToolUse hook for the "Read" tool.
# Blocks reads of large files and points Claude to the codebase-wiki skill
# instead. Targeted reads (offset/limit set) pass through.
set -euo pipefail

THRESHOLD="${SHUNT_MIN_LINES:-350}"
INPUT="$(cat)"

FILE_PATH="$(echo "$INPUT" | grep -o '"file_path"[[:space:]]*:[[:space:]]*"[^"]*"' | sed -E 's/.*"file_path"[[:space:]]*:[[:space:]]*"([^"]*)"/\1/')"
HAS_OFFSET="$(echo "$INPUT" | grep -c '"offset"' || true)"

if [ "$HAS_OFFSET" -gt 0 ]; then
  echo "$INPUT"; exit 0
fi
if [ -z "$FILE_PATH" ] || [ ! -f "$FILE_PATH" ]; then
  echo "$INPUT"; exit 0
fi

LINE_COUNT="$(wc -l < "$FILE_PATH" | tr -d ' ')"
if [ "$LINE_COUNT" -gt "$THRESHOLD" ]; then
  cat <<EOF
{
  "decision": "block",
  "reason": "Arquivo tem $LINE_COUNT linhas (limite: $THRESHOLD). Consulte .claude/context/wiki/ primeiro, ou use o subagent bulk-reader para uma pergunta pontual."
}
EOF
  exit 0
fi
echo "$INPUT"
```

!!! warning "Bug encontrado: `$CLAUDE_CONFIG_DIR` não existe em hooks"
    O comando do hook usava `$CLAUDE_CONFIG_DIR`, variável que **não existe** na execução de hooks (confusão com a variável de config geral do Claude Code). A variável correta de projeto seria `$CLAUDE_PROJECT_DIR`, mas nem essa serve aqui, pois o hook fica em `~/.claude`, fora do projeto. Resultado: a variável virou string vazia e o comando ficou literalmente `/hooks/check-file-size.sh`, gerando `No such file or directory`.

    **Correção**: usar `$HOME` em vez de `$CLAUDE_CONFIG_DIR` — exportada normalmente pelo shell (inclusive Git Bash no Windows): `"command": "$HOME/.claude/hooks/check-file-size.sh"`.

### Skill (`skills/codebase-wiki/SKILL.md`)

```markdown
---
name: codebase-wiki
description: Roteia leitura e escrita de código através de um cache persistente (wiki) e subagents baratos, para economizar tokens do modelo principal. Use SEMPRE que precisar entender um módulo, arquivo grande ou padrão existente antes de responder uma pergunta ou fazer uma alteração. Também use antes de gerar código boilerplate que deveria seguir um padrão já existente no repo. Não use para debugging, decisões de arquitetura, ou leitura pontual/pequena que já vai ser editada na mesma resposta.
---

# Codebase Wiki

Roteamento em 3 camadas para reduzir tokens gastos lendo código: uma wiki
persistente (cache), subagents baratos sob demanda, e o modelo principal
só entra para editar de fato.

## Fluxo de decisão
1. Verificar se existe `.claude/context/wiki/<módulo>.md` e se está atual.
2. Se não existir/estiver desatualizada, disparar `wiki-writer`.
3. Para pergunta pontual que a wiki não cobre, disparar `bulk-reader`.
4. Para código repetitivo (testes, stubs, config), disparar `code-writer`.
5. Só ler o arquivo-fonte diretamente para editar de fato — nunca delegar edição.

## Checando se a wiki está velha
Desatualizada quando `updated_at` no frontmatter é mais antigo que o
último commit relevante do módulo (`git log -1 --format=%ct -- <path>`),
ou não existe arquivo de wiki para o módulo ainda. Em dúvida, regenerar
(custo baixo vs. risco de contexto errado).
```

### Por que usar uma Skill para isso

Sem a skill, depende-se de o modelo "lembrar" de checar a wiki antes de ler tudo — inconsistente. Com a skill, o padrão é descoberto automaticamente sempre que relevante. Combo robusto: **hook (força) + skill (orienta) + subagent (executa barato)** — mesmo que o modelo não leia a skill, o hook ainda bloqueia a leitura cara.

## 5. Escopo de instalação: repo vs. pessoal

| | Escopo do repo (`.claude/`) | Escopo pessoal (`~/.claude/`) |
| --- | --- | --- |
| Onde fica | Dentro do projeto, versionado no git | Na home, fora de qualquer repo |
| Quem usa | Todo o time que clona o repo | Só o usuário, em qualquer projeto |
| Bom para | A **wiki em si** (descreve código específico daquele repo) | Os **subagents** e a **skill** (genéricos, não dependem de projeto) |

Decisão prática: agents e skill ficam em escopo **pessoal** — funcionam em qualquer repositório sem reconfiguração. A wiki de conteúdo fica **sempre por repo**, pois descreve código daquele repo específico. Para padronizar entre todo um time, o passo seguinte é empacotar como **plugin** do Claude Code (mesma ideia do `shunt` do Spotify).

## 6. claude.ai vs. Claude Code — o que realmente economiza tokens

Os "agents" (subagents em modelo barato) e os "hooks" (bloqueio automático de leituras grandes) são mecanismos **específicos do Claude Code**. O painel de Habilidades do claude.ai funciona em qualquer superfície, mas **dentro de uma conversa de chat normal não existe como invocar um subagent rodando em outro modelo, nem interceptar leituras de arquivo com hook** — isso só roda dentro do Claude Code.

- A **skill em si** (o `SKILL.md` com o fluxo de decisão) pode ser salva no claude.ai e vale para qualquer superfície, inclusive Claude Code.
- O **roteamento de tokens de verdade** (Haiku fazendo I/O, hook bloqueando leitura) só acontece quando a skill está ativa dentro do Claude Code, com `agents/` e `hooks/` também instalados lá.
- Salvar a skill no claude.ai sozinha, sem Claude Code, **não economiza tokens** — só orienta como manter/consultar a wiki manualmente.
