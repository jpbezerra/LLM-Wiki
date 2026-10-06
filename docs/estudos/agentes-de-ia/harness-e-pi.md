# HARNESS E PI

## O que é um "harness"

**Harness** ("arreio") é o termo usado para o runtime/framework que envolve um modelo de linguagem e o transforma num agente funcional. Não é o modelo em si — é toda a infraestrutura em volta dele: o loop de execução, as ferramentas disponíveis (ler/escrever arquivos, rodar shell, buscar na web), o sistema de permissões, o gerenciamento de contexto, a interface.

Exemplos de "coding agent harness": **Claude Code, Cursor, Aider, Cline** — cada um é essencialmente um harness diferente rodando sobre um LLM.

### Origem do termo

"Harness" existe há décadas em engenharia de software, antes de qualquer IA. Um **test harness** é o conjunto de código que prepara o ambiente, executa os testes e coleta os resultados de um programa: fornece dados de entrada, simula dependências externas (mocks), roda o código sob teste, verifica saídas. A palavra vem literalmente de "arreio" — equipamento para controlar um cavalo e fazê-lo puxar uma carroça — uma estrutura de suporte que permite operar algo que, sozinho, não conseguiria funcionar de forma útil.

### Por que um LLM precisa de um harness

Um LLM sozinho só sabe **gerar texto**. Sem um harness em volta, ele não consegue:

- ler ou editar arquivos no computador;
- rodar comandos de terminal;
- lembrar o que aconteceu muitas mensagens atrás (o contexto é limitado);
- decidir sozinho "agora preciso buscar na web, depois rodar um teste, depois corrigir o código";
- pedir permissão antes de uma ação arriscada.

O harness resolve isso, com cinco responsabilidades centrais:

1. **Loop de execução** — pega a resposta do modelo, interpreta se ele quer usar uma ferramenta, executa essa ferramenta, devolve o resultado ao modelo, repete até a tarefa terminar.
2. **Ferramentas (tools)** — acesso a ações reais: ler/escrever arquivos, executar shell, buscar na web, chamar APIs.
3. **Gerenciamento de contexto** — decide o que manter na "memória" do modelo conforme a conversa cresce.
4. **Permissões e segurança** — decide quando pedir confirmação ao usuário antes de uma ação (ex.: antes de deletar um arquivo).
5. **Interface** — terminal, chat, IDE, etc.

!!! note "A síntese que fica"
    O harness é **um orquestrador que dita o comportamento do modelo**: decide que ferramentas ele pode chamar, como o loop funciona (chama modelo → executa ação → devolve resultado → repete), o que entra/sai do contexto, e quando parar para pedir permissão. O modelo em si só "pensa" e produz texto; é o harness que transforma isso em ação no mundo real. É por isso que o mesmo modelo (ex.: Claude) se comporta de forma bem diferente dentro do Claude Code (agente autônomo com terminal/arquivos) e dentro do claude.ai (mais conversacional) — o "cérebro" é o mesmo, o "corpo" muda o que ele consegue fazer.

## Pi (pi.dev) — um harness minimalista

**Pi** é um agente de codificação minimalista — um harness hospedado em `pi.dev`, criado por **Mario Zechner** (autor da libGDX), hoje mantido pela **Earendil Works**.

### Características

- Instalação: `curl -fsSL https://pi.dev/install.sh | sh`.
- Filosofia declarada: **"adapte o Pi ao seu workflow, não o contrário"** — vem com padrões enxutos e **sem** recursos como sub-agentes ou "plan mode" prontos.
- Extensível via **pacotes** (extensions, skills, prompt templates, themes), instaláveis via npm ou git (`pi install npm:<pacote>`).
- Quatro modos de uso: interativo, print/JSON, RPC e SDK.
- Requisitos: Node.js ≥ 22.19.0, npm ≥ 11.12.1.

"Pi" é ao mesmo tempo o nome do harness em si e a marca do ecossistema de pacotes construídos sobre ele — daí nomes como `pi-harness`, `pi-team-harness`, `pi-subagents`, `pi-peer`: pacotes de terceiros que adicionam funcionalidades ao núcleo (orquestração multi-agente, temas, políticas de execução), não o próprio harness "oficial".

### Núcleo mínimo

O núcleo do Pi é deliberadamente "burro": apenas **quatro ferramentas** — `read`, `write`, `edit`, `bash` — e um loop básico de execução. Tudo que vem depois (sub-agentes, permissões, memória, RAG, integração com Slack, etc.) é customizável via extensões, em vez de herdar decisões já tomadas por quem criou a ferramenta.

## Vale a pena usar o Pi?

**Faz sentido se o usuário:**

- gosta de mexer e customizar — a proposta central é "molde a ferramenta, não se adapte a ela";
- quer controle sobre qual provedor de modelo usar (suporta 15+ provedores, incluindo endpoints self-hosted, sem depender de backend SaaS);
- valoriza código aberto e licença permissiva (MIT, sem vendor lock-in);
- é desenvolvedor experiente, capaz de lidar com riscos de segurança por conta própria.

**Não faz tanto sentido se o usuário:**

- quer algo que funcione bem "out of the box", sem configuração;
- precisa de sandbox de segurança e sistema de permissões robusto — um dos avisos mais consistentes sobre o Pi é que ele **não** tem isso embutido, ao contrário de ferramentas como o Claude Code;
- trabalha em equipe/produção com necessidade de estabilidade — a API de configuração e extensões muda rápido;
- quer suporte comercial ou é iniciante em CLI.

!!! tip "Síntese"
    O Pi é bom para quem trata "harness" como um projeto de engenharia próprio, com prazer em construir as peças que faltam — não para quem quer plug-and-play seguro desde o primeiro uso.

## Pi vs. Claude Code — comparação filosófica

| | Pi | Claude Code |
| --- | --- | --- |
| Orquestração padrão | Mínima, deliberadamente "burra" (4 ferramentas) | Bastante orquestração "opinativa" embutida |
| Sandbox / permissões | Não tem embutido — responsabilidade do usuário | Sandbox e sistema de permissões robustos |
| Sub-agentes, plan mode | Ausentes por padrão; adicionados via extensão | Prontos, já integrados |
| Filosofia | "Você constrói os próprios limites" | "Você customiza dentro de limites definidos" |

É basicamente o oposto filosófico: o Pi dá um núcleo mínimo e deixa por conta do usuário construir/instalar o resto; o Claude Code já vem com bastante orquestração pronta (sandbox, permissões, sub-agentes), e a customização acontece dentro desses limites.
