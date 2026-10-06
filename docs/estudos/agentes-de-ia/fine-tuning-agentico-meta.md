# FINE-TUNING AGÊNTICO: A ABORDAGEM DA META

**Artigo original:** [Organizational second brain: how AI learns from experts](https://engineering.fb.com/2026/09/02/ml-applications/organizational-second-brain-ai-learns-from-experts/) (Meta Engineering)

O artigo descreve um agente de IA construído para um domínio de compliance, mas que serve como blueprint geral para "capturar" conhecimento de especialistas **sem retreinar o modelo**. Em vez de fine-tuning tradicional (ajustar pesos), a Meta faz uma espécie de "fine-tuning" via **edição automatizada e validada de arquivos de texto** (base de conhecimento + procedimentos), com um loop de auto-melhoria acionado por feedback de especialistas humanos.

## 1. A arquitetura em 4 camadas

O sistema tem quatro camadas, cada uma resolvendo um problema específico e dependentes entre si — remover uma degrada as outras:

1. **Knowledge system** ("second brain" organizacional) — o quê o agente sabe.
2. **Recipes** (camada de raciocínio/procedimentos) — como o agente raciocina.
3. **Evaluation framework** — o que garante que mudanças não quebram nada.
4. **Self-improvement loop** — o que conecta feedback humano a mudanças permanentes.

!!! note "Princípio de design central"
    Conhecimento é declarativo, procedimento é imperativo, e eles nunca se misturam no mesmo arquivo.

## 2. Camada 1 — Knowledge system ("second brain")

Em vez de RAG puro (recuperar chunks de documentos brutos em tempo de inferência), a Meta roda um **processo offline de longa duração** que lê as fontes originais e destila esse conhecimento em arquivos estruturados — mais de 200 arquivos organizados em taxonomia estrita:

- **Position files**: posições oficiais da organização sobre questões do domínio, com restrições, condições de contorno e implicações de roteamento "machine-actionable" (dizem à camada de raciocínio quando aplicar aquela posição).
- **Taxonomy/vocabulary files**: glossário autoritativo de termos do domínio — single source of truth.
- **Routing indexes**: mapeiam características do input para as posições/procedimentos relevantes, sem depender só de similaridade de embeddings — tornando a recuperação determinística e auditável (não é RAG semântico puro).
- **Gateway files**: testes de threshold que o agente precisa passar antes de entrar num domínio analítico — evita aplicar conhecimento especializado fora de contexto.

Cada arquivo declara em YAML frontmatter `depends_on` e `referenced_by`, formando um **grafo de dependências bidirecional** — o que torna editar/auditar o sistema em escala viável: quando um arquivo muda, dá para rastrear tudo que pode ser afetado.

### Critério de particionamento: wiki curada vs. RAG

A decisão do que vai para a wiki estruturada vs. busca semântica/lexical é baseada em **densidade de informação × frequência de uso**:

- **Alta densidade + uso frequente → wiki** (posições, frameworks de decisão, exemplos de fronteira) — consultado quase todo turno, precisa estar sempre atualizado.
- **Esparso + situacional → RAG** (specs detalhadas de produto, registros históricos, conhecimento externo nichado) — carregar tudo na wiki diluiria a atenção do modelo.

A ideia compartilhada com referências citadas como o "LLM Wiki" do Karpathy (grafo navegável de arquivos) e o "Open Knowledge Format" do Google é **pré-extrair e estruturar conhecimento explicitamente**, com disclosure progressivo, em vez de re-derivar tudo a cada query.

### Exemplo de position file

```yaml
---
id: pos-data-retention-003
type: position
depends_on: [tax-entity-types, gw-data-domain]
referenced_by: [recipe-risk-assessment, recipe-intake-triage]
applies_when:
  - "input.category == 'user_data_retention'"
  - "input.region in ['EU', 'BR']"
version: 4
---

## Position
User data tied to a closed account must be retained no
longer than 90 days beyond the closure date, unless a
legal hold flag is present.

## Constraints
- Applies only to first-party product data.
- Does not apply to aggregated / anonymized analytics.

## Boundary examples
- Closed account, no legal hold -> delete at day 90.
- Closed account, active legal hold -> retain, escalate
  to recipe-legal-escalation.
```

## 3. Camada 2 — Recipes (raciocínio composável)

Recipes são **procedimentos imperativos** que espelham como um especialista de fato trabalha passo a passo (ex.: um analista financeiro seguindo um modelo de valuation). Cada recipe especifica: o que examinar primeiro, qual conhecimento carregar em cada etapa, quais critérios de decisão seguir, e o que conta como análise completa.

**Separação estrita (ponto de design central):**

- Recipes referenciam knowledge files, mas **não contêm fatos de domínio**.
- Knowledge files declaram posições, mas **não prescrevem procedimentos**.

Consequências práticas: adicionar uma posição organizacional = adicionar um knowledge file + atualizar índice de roteamento, sem tocar no recipe. Corrigir uma falha de metodologia = editar um recipe, sem tocar nos knowledge files. **A atribuição de falha fica limpa**: foi o conhecimento que estava errado, ou o procedimento?

Recipes se compõem em pipelines (analogia: chef de cozinha com receita-mestra que delega a sub-receitas sem conter os detalhes de cada uma). Um recipe de roteamento no topo examina o input e decide quais recipes downstream invocar.

**Progressive disclosure**: em vez de um único arquivo de instrução monolítico carregado inteiro sempre (abordagem inicial da Meta, com RAG semântico geral), cada etapa do recipe carrega só as instruções/conhecimento relevantes àquela fase. Resultado reportado: **redução de ~80% em tokens consumidos por turno** após essa reestruturação.

```yaml
id: recipe-risk-assessment
type: recipe
steps:
  - name: gateway_check
    load: [gw-data-domain]
    action: verify_applicable_domain
    on_fail: exit("not_in_scope")

  - name: load_position
    load: [pos-data-retention-003, tax-entity-types]
    action: apply_position_to_input

  - name: checkpoint_review
    surface_to: human_expert
    payload: [reasoning_trace, applied_positions]
    wait_for: expert_confirmation

  - name: escalate_if_ambiguous
    condition: "confidence < 0.7"
    action: route_to(recipe-legal-escalation)

  - name: emit_assessment
    output_schema: risk_assessment_v2
```

Note que nenhum fato de domínio aparece aqui — só chamadas a arquivos de conhecimento e controle de fluxo.

## 4. Humano no controle: checkpoints e escalations

Dois mecanismos mantêm o especialista humano com autoridade sobre o resultado:

- **Checkpoints**: pontos definidos onde o agente expõe seu raciocínio intermediário para revisão antes de prosseguir.
- **Escalations**: disparadas quando há ambiguidade genuína — em vez de forçar uma resolução, o agente delega a decisão ao expert.

Servem a três propósitos simultâneos: controle de qualidade/direção, **sinal de treino** para o loop de auto-melhoria, e calibração de confiança (o expert vê o raciocínio, não só o output final).

## 5. Camadas 3+4 — o self-improvement flywheel

O coração "agêntico" do sistema — tratado explicitamente como **um problema de compilação**, não de retreino. Toda correção de especialista passa por 4 fases.

### Fase 1 — Diagnóstico (root cause attribution)

A primeira abordagem da Meta (classificar feedback pela forma conversacional: "se o expert deu uma informação, é gap de conhecimento; se redirecionou, é problema de procedimento") **falhou**, porque a forma da conversa é um proxy ruim para a causa raiz.

A abordagem que funcionou separa extração de classificação: extrai todo sinal substantivo do expert + o "manifesto de conhecimento" completo do agente (todo arquivo carregado, quando e como foi usado), lê os knowledge files reais e aplica um teste único — **"o agente poderia ter chegado à conclusão correta a partir do material que tinha?"**

- Material continha a resposta certa, mas o agente errou → **problema de recipe**.
- Material não continha a resposta certa → **gap de conhecimento**.
- Experts discordam entre si → **ambiguidade**, escalada para discussão humana.

```python
def diagnose(issue, manifest, knowledge_files):
    signal = extract_expert_signal(issue)
    could_answer = attribution_test(signal, knowledge_files)

    if experts_disagree(signal):
        return Diagnosis("ambiguity", route="human_discussion")
    if could_answer:
        return Diagnosis("recipe_bug", target="recipe-risk-assessment")
    return Diagnosis("knowledge_gap", target="pos-data-retention-003")
```

### Fase 2 — Compilação (edições cirúrgicas multi-agente)

Um "compilador" traduz cada issue diagnosticada em edições mínimas de arquivo. Sub-agentes analisam impacto em paralelo (cross-references, conflitos com posições existentes, impacto no orçamento de tokens, cobertura de teste, risco de duplicação). Dois mecanismos de confiança:

- **Revisão adversarial independente**: um agente separado, em contexto novo (sem saber a razão da mudança), recebe só os diffs propostos e procura problemas — por não compartilhar contexto com quem propôs, não herda os mesmos pontos cegos.
- **Validação estrutural determinística**: um linter (não probabilístico) checa referências quebradas, violação de orçamento de tamanho de arquivo, colisão de identificadores, ciclos de dependência.

```python
def compile_fix(diagnosis):
    diff = proposing_agent.draft_edit(diagnosis)
    review = adversarial_agent.review(diff, context="none")

    if not lint_passes(diff):
        return retry(diagnosis, reason="structural_lint_failed")
    if review.flags:
        return retry(diagnosis, reason=review.flags)

    branch = f"auto-fix/{diagnosis.issue_id}"
    git.create_branch(branch)
    git.apply_diff(diff)
    return github.create_pull_request(
        branch=branch,
        title=f"[auto-fix] {diagnosis.target}: {diagnosis.issue_id}",
        body=render_pr_description(diagnosis, diff, review),
        labels=["auto-generated", "knowledge-edit"],
    )
```

### Fase 3 — Avaliação (prova de que a correção funciona)

- **Targeted replay**: roda o agente no cenário original que gerou o feedback (ele não sabe que está sendo testado). Um juiz separado avalia o novo output contra o feedback original **sem saber o que mudou** (design cego, para evitar viés de confirmação). Se falhar, recompila.
- **Regression testing**: roda múltiplos benchmarks (suites de Q&A estruturadas) para o domínio, com juiz LLM independente dando pass/fail. Se falhar, recompila com um prompt atualizado descrevendo onde regrediu, junto com o issue original.

```yaml
name: validate-knowledge-edit
on:
  pull_request:
    paths: ["knowledge/**", "recipes/**"]

jobs:
  structural_lint:
    steps:
      - run: python tools/lint_knowledge_graph.py
        # dangling refs, size budget, id collisions, cycles

  targeted_replay:
    needs: structural_lint
    steps:
      - run: python tools/replay.py --scenario $ISSUE_RUN_ID
      - run: python tools/blind_judge.py --output replay.json
        # judge does not know what changed

  regression_suite:
    needs: structural_lint
    steps:
      - run: python tools/run_benchmark.py --domain compliance
      - run: python tools/judge_pass_fail.py --min-pass-rate 0.98

  gate:
    needs: [targeted_replay, regression_suite]
    steps:
      - run: fail_if_any_stage_failed()
```

### Fase 4 — Landing e enriquecimento (retornos compostos)

O output do pipeline é um PR (diff) com trilha de auditoria completa — o humano revisa uma correção já provada, não debuga uma falha crua. Uma vez aprovado, o cenário que falhou original + a resposta validada correta são **automaticamente adicionados à suite de regressão**: cada correção eleva permanentemente a barra, já que mudanças futuras precisam preservar o comportamento já corrigido.

```json
{
  "test_id": "reg-2026-08-22-0091",
  "origin_issue": "exp-fb-2026-08-22-0091",
  "scenario": "anonymized_analytics_retention_check",
  "expected": "pos-data-retention-003 NOT applied",
  "added_on_merge_of_pr": "#4821"
}
```

!!! tip "O que fecha o flywheel"
    O gate de CI é o que faz o sistema ser confiável sem retreino: nada chega a `main` sem passar por lint estrutural + replay cego + regressão. E o passo final fecha o ciclo: cada PR mergeado adiciona automaticamente um novo caso à suíte de regressão, então o próximo PR já não pode reintroduzir aquele erro.

## 6. Resultados reportados (3 sprints, 6 semanas)

- Experts avaliaram os outputs como úteis quase o tempo todo (vs. retrabalho substancial nas versões iniciais).
- Redução de **dias para minutos** no tempo de avaliação individual.
- Auto-melhoria automatizada produzindo edições validadas numa taxa que antes exigia sprints de engenharia inteiros.
- **Zero regressões** entre ciclos de melhoria.
- Experts reportam que o agente cobre a maioria do trabalho analítico, liberando-os para casos genuinamente ambíguos.

## 7. Como implementar na prática

Quatro requisitos, segundo o artigo:

1. **Sistema de conhecimento estruturado**: arquivos com limites explícitos, cross-references, e grafo de dependências (YAML frontmatter com `depends_on`/`referenced_by` é literalmente reproduzível).
2. **Camada procedural** separando conhecimento de metodologia (recipes).
3. **Suite de avaliação automatizada** que cresce a cada ciclo de melhoria (regression tests alimentados pelas próprias correções).
4. **Checkpoints human-in-the-loop** calibrados ao risco do domínio.

Passos práticos derivados do texto:

- Comece convertendo documentos/playbooks existentes em arquivos "position" curtos e declarativos — não jogue documentos brutos num RAG.
- Escreva um linter simples cedo (referências quebradas, tamanho de arquivo, ciclos) — é barato e pega uma classe inteira de erros.
- Construa o pipeline de diagnóstico com o teste de atribuição único ("o material continha a resposta?") antes de tentar heurísticas de classificação por forma de conversa — evite o erro que a Meta cometeu.
- Implemente o judge de replay como **cego** (não sabe o que mudou) desde o início — é o que evita confirmation bias.
- Trate cada correção resolvida como candidata automática a novo caso de regressão — isso é o que torna o ganho permanente em vez de pontual.

## 8. Prós e contras

**Prós:**

- **Sem retreino de modelo**: toda a "aprendizagem" vive em arquivos de texto versionáveis, diffáveis, revisáveis em segundos por humanos — muito mais barato e auditável que fine-tuning de pesos.
- **Atribuição de falha limpa** graças à separação conhecimento/procedimento.
- **Redução real de custo de contexto** (~80% menos tokens/turno) via disclosure progressivo.
- **Loop verdadeiramente compounding**: cada correção vira teste de regressão permanente.
- **Generalizável** a qualquer domínio "governado por texto recuperável" (finanças, segurança, compliance, engenharia), segundo os próprios autores.
- **Governança forte**: checkpoints/escalations mantêm humano com autoridade real, não apenas cosmética.

**Contras / limitações (algumas implícitas, não ditas abertamente pela Meta):**

- **Custo de engenharia inicial alto**: construir 200+ arquivos curados, taxonomia, grafo de dependências, linter, pipeline multi-agente de compilação e replay é um projeto de plataforma.
- **Depende de domínio "textualizável"** — funciona bem onde o conhecimento é majoritariamente declarativo/procedimental; domínios de expertise perceptual/tácita (julgamento visual, intuição de produto) podem não se encaixar tão bem.
- **Ainda depende de LLM-as-judge** em vários pontos (replay, regressão), com suas próprias falhas de calibração.
- **Overhead de manutenção do grafo de dependências** — curar `depends_on`/`referenced_by` corretamente em escala é trabalho manual que pode virar gargalo.
- **Não é low-code**: exige múltiplos agentes especializados, infraestrutura de teste e um linter customizado — é uma stack de "compiler engineering" aplicada a conhecimento.
- **O artigo é promocional/vago em números concretos** — difícil avaliar reprodutibilidade real fora do contexto interno da Meta.
- **Risco de "conhecimento fossilizado"**: se a wiki não for atualizada com a mesma disciplina do design original, position files desatualizados podem virar fonte de erro sistemático — silenciosamente autoritativos mesmo quando errados.
