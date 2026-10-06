# JEV: MODELOS DE DECISÃO

## 1. O que é o Jev

**Jev** é um modelo de IA lançado pela empresa **TypeSafe AI** em 15 de setembro de 2026, apresentado como o primeiro "modelo de decisão" público — categoria diferente dos LLMs tradicionais (ChatGPT, Claude). A TypeSafe o descreve como o primeiro modelo **"System One"** da empresa: um modelo de IA para **decisões legíveis por máquina**, não para prosa legível por humanos (referência a pensamento rápido/intuitivo, tipo 1, vs. deliberativo, tipo 2).

**Diferença central**: enquanto um LLM gera texto token por token, o Jev é desenhado em torno da própria decisão. Recebe:

- **Estado (state)**: dados relevantes da aplicação (conversa de suporte, dados de conta, detalhes de pedido).
- **Perguntas (questions)**: questões estruturadas sobre esse estado — verdadeiro/falso, escolha entre opções predefinidas, ou pontuação numa escala.

Devolve dados estruturados (não prosa): escolha, score, probabilidade e nível de confiança — usáveis diretamente pelo software, sem "extrair" informação de texto gerado.

!!! note "Sobre a origem da empresa"
    A empresa é ligada a Diogo Almeida, apresentado como coinventor do RLHF e do InstructGPT. Isso não significa que ele inventou o ChatGPT sozinho — é um detalhe de marketing a se ler com ressalva.

**Especificações técnicas** (`jev-1.13.0`): contexto de 64k tokens (32k reservados para state + a pergunta mais longa); apenas texto (sem multimodal); US$ 0,042 por milhão de tokens de entrada, output gratuito; latência declarada de 70–500ms; idioma de treino principal inglês.

## 2. Primitivos de pergunta

| Primitivo | O que pergunta | O que retorna | Uso típico |
| --- | --- | --- | --- |
| **Choice** | Escolher uma opção declarada | Escolha + distribuição de probabilidade + confiança | Rotear para código, modelo especializado ou humano |
| **Score** | Classificar em uma escala definida | Nota + probabilidades por nível + confiança | Avaliar urgência, qualidade, prioridade |
| **Noul** | Avaliar uma afirmação sim/não | Probabilidade de "sim" | Decidir um desvio (ex.: "isso é um pedido de reembolso?") |

### Estrutura de input

```json
{
  "state": "Help! My payouts have been failing for 3 days.",
  "questions": {
    "is_urgent": {
      "type": "noul",
      "instructions": "Does this convey urgency?",
      "criteria": { "true": "Explicitly time-sensitive", "false": "No urgency expressed" }
    },
    "department": {
      "type": "choice",
      "instructions": "Which team should handle this?",
      "criteria": {
        "billing": "Payments, invoicing, refunds",
        "technical": "Bugs, outages, integrations"
      }
    }
  }
}
```

`state` é o material bruto a avaliar (texto, JSON ou arrays). `questions` é um dicionário onde cada pergunta tem `type`, `instructions` (em linguagem natural) e `criteria` — que ancora o *significado* semântico de cada rótulo, não só o nome. Várias perguntas podem ir na mesma chamada, avaliadas todas contra o mesmo `state`, em paralelo, sem custo adicional relevante de tempo.

### Estrutura de output

```json
{
  "model": "jev-1.13.0",
  "answers": {
    "is_urgent": { "type": "noul", "noul": 0.94 },
    "department": {
      "type": "choice",
      "choice": "billing",
      "confidence": 0.88,
      "probabilities": { "billing": 0.88, "technical": 0.09, "sales": 0.03 }
    }
  },
  "usage": { "input_tokens": 210, "output_tokens": 31 }
}
```

Pontos-chave da saída: sem texto para interpretar (JSON estruturado direto); impossível sair do schema declarado em `criteria` (ver ressalva na seção 6); confiança calibrada como propriedade de primeira classe do treino, não emendada via prompt engineering depois.

## 3. Como o modelo "entende" o input

Tecnicamente ainda é um modelo neural de linguagem — a diferença está no **objetivo de treino**. Um LLM comum usa RLHF (respostas que humanos preferem) ou RLVR (saídas que um programa consegue verificar). O Jev usa **RLCD**, otimizado especificamente para produzir probabilidades calibradas e epistemicamente honestas em tarefas de decisão.

### Generalização semântica sem retreino

No ML clássico, as classes de saída estão codificadas nos pesos/arquitetura — mudar uma categoria exige retreino. No Jev, as classes são **texto dentro do `criteria`**, resolvidas em tempo de inferência via generalização semântica (mesma base tipo-LLM): durante o pré-treino massivo em texto, o modelo aprende um espaço de representação onde conceitos semanticamente próximos ficam próximos matematicamente. "Fatura", "cobrança", "reembolso" e "billing" ocupam regiões vizinhas desse espaço, mesmo que o modelo nunca tenha visto a palavra exata associada àquele caso de uso específico.

Isso é zero-shot / in-context — não é exclusividade do Jev, é a mesma capacidade que já existe em qualquer LLM moderno ao pedir "classifique esse texto em: [urgente, normal, baixa]". A capacidade vem do pré-treino (seguir instruções, julgamento contextual via RLHF); o RLCD é o pós-treino que especializa essa capacidade para emitir julgamentos numéricos honestos em vez de continuar "no modo conversa".

!!! note "Formulação correta"
    Não é que o modelo "associa labels específicas que viu no treino" — é que ele "aprendeu a entender linguagem de forma geral o suficiente para interpretar labels que nunca viu", desde que a descrição seja dada em `criteria`. O treino não ensina "billing = X"; ensina "como interpretar qualquer descrição textual de categoria e julgar se um texto se encaixa nela". Existem rotinas de retreino do modelo em si (`jev-1.13.0` → `jev-1.14.0`), mas isso melhora a capacidade geral — não "aprende" critérios específicos de um usuário, que continuam sendo passados em toda chamada, como dado de entrada.

## 4. RLCD (Reinforcement Learning for Calibrated Decisions)

Um modelo é **calibrado** quando a probabilidade declarada bate com a frequência real de acerto — se o Jev diz "85% de confiança", o ideal é que ~85% desses casos realmente estejam certos. LLMs comuns são ruins nisso: tendem a gravitar em torno de números que "soam plausíveis" porque foram treinados para soar convincente (RLHF), não para ser estatisticamente honestos — o mesmo fenômeno de alucinação, aplicado a números de confiança.

| Método | O que o reward otimiza | Risco típico |
| --- | --- | --- |
| **RLHF** | Respostas que humanos avaliadores preferem | Otimiza para "soar bem", não para estar certo |
| **RLVR** | Saídas que um programa consegue verificar como corretas | Só funciona onde existe verificação automática objetiva |
| **RLCD** | Probabilidades calibradas em decisões estruturadas | Precisa de muitos exemplos rotulados para medir calibração de verdade |

A TypeSafe não publicou os detalhes matemáticos completos — só que o reward do RL não é só "acertou sim/não", mas quão bem a distribuição de probabilidade emitida bateu com o resultado real, agregado sobre muitos exemplos (compatível, em ML clássico, com *proper scoring rules* como Brier score e log-loss). Mudança arquitetural adicional: em vez do sampler autoregressivo padrão (token após token), o Jev usa um **sampler paralelo** que gera todas as saídas numa única passada — é essa combinação (arquitetura sem decodificação sequencial + treino para calibração) que dá a latência baixa e a saída sempre dentro do schema. Por isso adicionar uma quarta pergunta na mesma chamada quase não aumenta o tempo de resposta.

!!! tip "Síntese do que é o Jev"
    Um classificador/estimador de probabilidade com generalização de LLM, treinado especificamente para fazer esse tipo de julgamento com confiança calibrada — categoria intermediária entre classificador clássico e LLM generativo comum.

## 5. Onde vale a pena usar

**Bons casos de uso**: roteamento entre modelos (código determinístico, LLM rápido, modelo de raciocínio, revisão humana); triagem e priorização (score de urgência em tickets de suporte); moderação e detecção de fraude/risco; decidir se repetir etapa de agente, escalar para humano, ou parar; roteamento de intenção em geral.

**Onde não usar**: nunca para aritmética, permissões, cálculos exatos, datas ou lógica de estado — isso fica em código. Nunca como autorizador final de algo consequente (pagamento, acesso) — confiança alta não é autorização. Não é gerador de texto para humanos. Cuidado especial em trading/finanças: pode classificar regime semântico, mas cálculo de risco, tamanho de posição e execução de ordem devem ficar em serviços determinísticos separados.

## 6. Limitações conhecidas

- Tipado não é sinônimo de correto — pode ficar dentro do schema e ainda escolher errado.
- Probabilístico não é determinístico — repetir a mesma pergunta pode dar respostas diferentes.
- Fraco em precisão numérica e comparação de datas; pode se distrair com estado irrelevante grande demais.
- Conjuntos fechados de opções precisam de saída tipo "desconhecido"/"revisão humana" para casos fora do previsto.
- É early access — ainda não é "prova de produção" no sentido amplo.
- Uma análise independente (**Arize**) aponta que a alegação de "não consegue alucinar" é exagerada: o que é verdade é que não pode retornar algo fora do schema — dentro do schema, ainda pode errar a resposta, com único sinal sendo a probabilidade vir mais baixa. Os números de velocidade/custo (40–200x mais rápido, 40–400x mais barato) vêm de benchmarks da própria TypeSafe, sem verificação independente completa até o momento.

## 7. Como usar — SDK Python

```python
from typesafe_sdk import Choice, Noul, TypeSafeClient

with TypeSafeClient(model="jev-1.13.0") as client:
    response = client.system_one(
        state={"request": texto_do_usuario, "risk_class": "normal"},
        questions={
            "route": Choice(
                instructions="Qual handler deve processar `request`?",
                criteria={
                    "deterministic_code": "Uma busca ou cálculo fixo resolve",
                    "fast_llm": "Geração curta, raciocínio limitado",
                    "reasoning_llm": "Precisa de interpretação em várias etapas",
                    "human_review": "Ambíguo, sensível, ou fora das rotas",
                },
            ),
            "needs_current_sources": Noul(
                instructions="O pedido precisa de informação que pode ter mudado recentemente?"
            ),
        },
    )

rota = response.answers["route"]
```

Pontos práticos ao adotar: fixar a versão do modelo (`jev-latest` pode migrar sem avisar); calibrar limiares de confiança conforme a consequência do erro; rodar em modo "shadow" antes de confiar (comparar decisões do Jev com a rota atual); manter fallback determinístico; tratar `state` como superfície de ataque (testar contra prompt injection).

## 8. Paper independente: "JEV-as-a-Judge"

**Autores:** Yubo Li, Yidi Miao, Ramayya Krishnan, Rema Padman (Carnegie Mellon University), preprint arXiv de 22/09/2026.

**Pergunta de pesquisa**: dá para usar o Jev como juiz barato de qualidade de respostas de IA (LLM-as-a-judge), usando a própria confiança dele para saber quando escalar para um avaliador mais caro e forte? Comparação do `jev-as-a-judge` contra 16 outros avaliadores (GPT-4.1 até GPT-6 Astra, Claude Sonnet 5, Gemini 3/3.1, Qwen, e modelos de recompensa como PairRM e Skywork-Reward-V2).

### Onde o Jev se sai bem (a ≤3pp do GPT-6, a ~0,4% do custo)

| Tarefa | Jev | GPT-6 | Diferença |
| --- | --- | --- | --- |
| Preferência comum (RewardBench) | 92,2% | 93,5% | −1,3 pp |
| Factualidade com evidência (HaluEval) | 87,5% | 86,7% | +0,8 pp |
| Adjudicação de resposta final | 94,0% | 96,7% | −2,7 pp |

### Onde o Jev falha feio

| Tarefa | Jev | GPT-6 | Diferença |
| --- | --- | --- | --- |
| Correção difícil (JudgeBench) | 78,6% | 93,1% | **−14,6 pp** |
| Pares estilo-adversariais (RM-Bench) | 74,8% | 94,6% | **−19,8 pp** |
| Prosa livre sem referência | 52,5% (≈ aleatório) | 55,0% (também ≈ aleatório) | ninguém se sai bem |

Adjudicação humana cega (183 casos de discordância Jev/GPT-6) confirmou: não é ruído de rótulo — favoreceu ainda mais o GPT-6 do que os rótulos originais sugeriam. No JudgeBench, a lacuna é maior justamente em raciocínio (68,4% vs. 95,9%) e código (76,2% vs. 97,6%). Há também um **viés de estilo**: quando a resposta errada é escrita de forma mais elaborada/convincente que a certa, a acurácia do Jev cai quase 10 pontos.

### Custo e latência

Latência mediana do Jev: **0,152s** contra 1,885s do GPT-6 (~12x mais rápido). Custo: **US$ 0,044 por 1.000 julgamentos** contra US$ 12,18 do GPT-6 (~**277x mais barato**).

### A confiança como sinal de quando confiar nele

**Achado central**: a acurácia sobe monotonicamente com a probabilidade máxima declarada — itens com confiança < 60% acertam só 47,7%; itens com 100% de confiança acertam 99,1%. AUROC de detecção de erro: 0,87 / 0,74 / 0,86 nas três tarefas principais — bom o suficiente para sustentar uma política de escalonamento.

**Cascata testada**: aceitar decisão do Jev quando confiança ≥ limiar, senão chamar GPT-6. No limiar de 0,9: reteve **99,6% da acurácia do GPT-6 sozinho**, usando **47% do custo** dele. No RewardBench, a cascata até superou o GPT-6 sozinho (94,0% vs. 93,5% — erram em itens diferentes). No JudgeBench, o mesmo limiar reteve 98,2% a 62% do custo.

!!! warning "Onde o sinal de confiança quebra"
    No RM-Bench (pares estilo-adversariais), o AUROC caiu para 0,77 (pares difíceis) contra 0,90+ (fáceis/normais) — exatamente onde o Jev é enganado por estilo, ele também **fica confiante estando errado**: o pior cenário possível para uma cascata. No teste de prosa livre sem referência, a probabilidade média ficou em 0,90+ mesmo perto do acaso — AUROC de 0,518 (praticamente aleatório).

### Estabilidade

Perguntas idênticas repetidas: zero mudanças de decisão em 96 repetições. Paraphrase da instrução: 4 mudanças em 48 casos. Inversão de ordem dos candidatos (A/B trocados): 3,25% de decisões mudam no RewardBench vs. 11,14% no JudgeBench — em tarefas mais difíceis, a decisão é mais sensível a fatores que não deveriam importar.

### Insights práticos

1. O Jev não é "bom" ou "ruim" genericamente — é bom em tipos específicos de julgamento: preferência comum, checagem factual com evidência, adjudicação de resposta final. Ruim em: verificar derivação lógica passo a passo, resistir a resposta errada mas bem escrita, julgar texto livre sem referência.
2. Confiança alta ≠ permissão para confiar cegamente — fora do "envelope" de domínios bons, confiança se torna sinal falso.
3. A cascata funciona, mas o limiar precisa ser validado por domínio, não copiado de outro cenário.
4. Testar em ambas as ordens (A/B e B/A) importa mais em tarefas difíceis — vale agregar as duas quando a tarefa exige mais "raciocínio".
5. Contar saídas inválidas como erro, não descartá-las, ao comparar modelos.
6. "Não alucina" no sentido estrito (nunca sai do schema) não é garantia de acerto — tipagem garante formato, não verdade.

**Mapa de operação** (derivado da Tabela 2 do paper): "Use Jev" para preferência / factualidade com evidência / adjudicação final; "Escale" para correção difícil e resistência a estilo; "Valide antes" para seleção de múltiplas opções e resumos fundamentados; "Não suportado" para prosa sem referência alguma.
