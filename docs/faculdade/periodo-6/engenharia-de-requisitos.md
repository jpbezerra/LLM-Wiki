# ENGENHARIA DE REQUISITOS

---

A disciplina (IF1008, Centro de Informática da UFPE, professora **Jéssyka Vilela**) ensina o processo completo de **Engenharia de Requisitos (ER)**: elicitar, analisar, especificar, validar e gerenciar requisitos de software, assegurando atributos de qualidade. O curso combina aulas teóricas com um **projeto real** (registrado como projeto de extensão), em que cada time trabalha com um cliente de verdade, orientado por um gerente de projeto.

!!! note "Avaliação e ementa"
    - **Avaliação**: Seminários (20%) + Atividades (30%) + Projeto — especificação de requisitos, desenvolvimento e entregas parciais (50%). Frequência mínima de 75%.
    - **Ementa**: fundamentos e processo de ER; identificação de stakeholders; elicitação; técnicas de especificação (textual, casos de uso, histórias de usuário); tipos de requisitos (funcionais, não funcionais, regras de negócio); características de bons requisitos; Design Thinking; validação; rastreabilidade.
    - **Bibliografia básica**: Kotonya & Sommerville, *Requirements Engineering: Processes and Techniques* (Wiley, 1998); Wiegers, *Software Requirements* (2ª ed., Microsoft Press, 2003); Pressman, *Engenharia de Software: Uma Abordagem Profissional* (6ª ed., Bookman McGraw-Hill, 2011).
    - **Ferramentas citadas em aula**: UML (Visual Paradigm Community, Astah, Draw.io, LucidChart), Miro, Figma, Trello/Jira, Bizagi Modeler.

## O processo de Engenharia de Requisitos

### Por que ER é difícil

Programar um algoritmo isolado ("programming in the small") é bem diferente de fazer Engenharia de Software ("programming in the large"): dezenas de desenvolvedores, milhões de linhas de código, múltiplos clientes e versões, integrações externas, requisitos não funcionais e manutenção por anos. Um clássico cartum ilustra a "dificuldade de desenvolver software": cliente, líder de projeto, analista, programador e consultor de negócios frequentemente imaginam coisas completamente diferentes a partir da mesma solicitação.

!!! danger "Caso real: o Boeing 737 MAX"
    Em 2018, o voo da Lion Air e, pouco depois, um segundo acidente na Etiópia envolveram o **MCAS** (*Maneuvering Characteristics Augmentation System*), um sistema que movia automaticamente a cauda horizontal da aeronave com base em dados incorretos recebidos da unidade de referência inercial de dados aéreos (**ADIRU**). O caso é citado em aula como exemplo de como falhas de requisitos/software podem ter consequências catastróficas (documentado no documentário *Downfall: The Case Against Boeing*, Netflix).

    Citação de **Nancy Leveson**: *"The serious problems that have happened with software have to do with requirements, not coding errors."* Segundo dados apresentados em aula, **33%** dos erros de projeto acontecem em engenharia de requisitos, e **36%** dos erros em ER ocasionam falha do projeto.

### O custo de errar nos requisitos

A citação de **Gause & Weinberg** (*Exploring Requirements: Quality Before Design*) resume o motivo de se investir em ER: *"encontrar e corrigir defeitos de requisitos após a entrega do sistema é muitas vezes 100 vezes mais caro do que encontrá-los e corrigi-los durante as fases de requisitos e design"* (Boehm e Basili, 2001).

| Fase em que o erro é corrigido | Custo relativo (Development Phase x Cost Ratio) |
|---|---|
| Requisitos | 1x (baseline) |
| Design | 3–6x |
| Implementação | 10x |
| Testes de desenvolvimento | 15–40x |
| Testes de aceitação | 30–70x |
| Pós-lançamento (produção) | 40–1000x |

Um estudo sobre 300 projetos T&M (*time and materials*) traz valores absolutos médios para o custo de corrigir um erro de requisito por etapa: Requisitos R$150,77 → Projeto R$376,92 → Construção R$753,85 → Testes R$1.130,77 → Aceite R$2.261,54 → Operação R$4.900,00.

### Definição formal e objetivos da ER

> "Engenharia de requisitos (ER) é um conjunto de atividades relacionadas à **identificação e comunicação** do **propósito** de um sistema e os **contextos** nos quais será usado. Portanto, ER atua como uma ponte entre **as necessidades do mundo real** de usuários, clientes e outros **envolvidos** afetados pelo software, e as **capacidades e oportunidades** proporcionadas por tecnologias."

Objetivos centrais: conhecer os requisitos pertinentes; alcançar consenso entre stakeholders; documentar os requisitos sistematicamente; compreender e registrar os desejos e necessidades reais dos envolvidos. A comunicação é tão importante quanto a análise — e qualidade significa, antes de tudo, *adequação à finalidade*: não se pode avaliar qualidade sem entender o propósito do sistema.

### As quatro etapas do processo (modelo adotado na disciplina)

Todas as aulas seguintes se encaixam em um único diagrama de processo, usado como mapa da disciplina: quatro etapas centrais, cruzadas por um bloco transversal de **Gerenciamento** (que cuida de **Rastreabilidade** e **Consistência** do início ao fim):

```
Elicitação → Análise e Negociação → Especificação → Validação
   (Gerenciamento: Rastreabilidade + Consistência, atravessando todas as etapas)
```

| Etapa | Conteúdo |
|---|---|
| **Elicitação** | Levantamento de informações; técnicas de coleta de dados; detalhamento do domínio e das regras de negócio |
| **Análise e Negociação** | Resolução de conflitos; verificação de consistência das informações |
| **Especificação** | Descrição do sistema em linguagem natural e/ou diagramas |
| **Validação** | Resolução de conflitos residuais; consistência final |

!!! note "Engenharia de requisitos não é exclusiva de metodologias ágeis"
    Dados do survey **NaPiRE** (*Naming the Pain in Requirements Engineering*, [napire.org](https://www.napire.org/), replicado a cada dois anos em dezenas de países, incluindo o Brasil) mostram que times ágeis **não escapam** dos problemas clássicos de ER — falhas de comunicação entre cliente e equipe, "alvos móveis" (requisitos que mudam constantemente) e dificuldade de acessar as necessidades reais do cliente aparecem como os principais problemas em empresas de todos os tamanhos.

### Modelos de processo de software (contexto)

A disciplina revisita rapidamente os principais modelos de ciclo de vida que moldam como a ER se encaixa no desenvolvimento: **Cascata** (requisitos → projeto → implementação → integração → operação, com retroalimentação), **Incremental** (especificação, desenvolvimento e validação simultâneos gerando versões sucessivas), **Espiral de Boehm** (ciclos de determinar objetivos → avaliar riscos → desenvolver → planejar, com protótipos crescentes), **RUP** (fases Iniciação/Elaboração/Construção/Transição cruzadas com disciplinas como Requisitos e Gerenciamento de Projeto), o **Modelo V** (cada fase de especificação tem uma fase de teste espelhada: requisitos↔testes de aceitação, arquitetura↔testes de integração, design detalhado↔testes unitários) e os métodos ágeis (**XP**, com suas práticas de Time Coeso, Jogo do Planejamento, Integração Contínua etc.; e **Scrum**, com Product Owner, Sprint Backlog, Daily Scrum e Sprint Review).

## Elicitação de requisitos

**ELICITAR** = eliciar + clarear + extrair + descobrir — tornar explícito, obter o máximo de informação possível junto a usuários finais, gerentes, engenheiros e especialistas de domínio (os **stakeholders**).

### Técnicas de elicitação

| Técnica | Quando usar | Vantagens | Desvantagens |
|---|---|---|---|
| **Questionários/Formulários** | Medir atitudes, opiniões e comportamentos em larga escala | Baixo custo; grande volume de dados; anonimato possível; não exige presença do entrevistador | Precisam ser bem elaborados; questões mal feitas geram dúvidas; baixa taxa de resposta |
| **Análise de documentos** | Manuais, documentação, relatórios e diagramas já existentes | Geralmente combinada com outras técnicas | — |
| **Etnografia** | Compreender a política organizacional e a cultura de trabalho real | Revela requisitos de como as pessoas *realmente* trabalham (não como deveriam); percebe o que não é verbalizado | Influência do entrevistador; custo elevado; exige conhecimento especializado |
| **Grupos focais** | Reunião de 8–12 participantes, 1–2h, com moderador e perguntas abertas | Sinergia e espontaneidade; baixo custo e rapidez | Dados difíceis de analisar; risco de conflito de opiniões; moderador precisa de treinamento |
| **Prototipação** | Explorar interface, viabilidade de requisitos de desempenho | Feedback antecipado; "não há requisitos errados, apenas requisitos esperando para ser descobertos" | Pode elevar expectativas; protótipo não descartado pode gerar software difícil de manter |
| **Reuso** | Reutilizar especificações, glossários, templates e código de projetos anteriores | Menor custo e tempo; melhor qualidade | Maiores custos de manutenção; dificuldade em adaptar componentes reusáveis |
| **GERSE** | Guia específico para elicitação em Sistemas Embarcados de pequeno/médio porte | Processo estruturado em pré-fase e fase principal | Escopo específico (sistemas embarcados) |
| **Entrevistas** | Dados personalizados que exigem aprofundamento | Flexibilidade; profundidade; leitura de expressões corporais | Custo mais alto; exige entrevistadores especializados |

### Entrevistas: a técnica mais detalhada do curso

As entrevistas podem ser **estruturadas** (roteiro fixo), **não-estruturadas** (conversa aberta) ou **semi-estruturadas** (roteiro com liberdade para desviar). O processo se divide em três etapas:

**1) Preparação** — definir o propósito, selecionar a pessoa certa ("quem mais possui conhecimento semelhante ao seu?"), pesquisar sobre o entrevistado, decidir o formato e os tipos de pergunta (abertas vs. fechadas), planejar a logística.

**2) Condução** — construir relacionamento (profissional, pessoal e em relação ao produto); definir expectativas desde o início; fazer perguntas significativas; **ouvir ativamente** — a distinção central aqui é entre **requisitos declarados** (o que o stakeholder *diz* que precisa) e **requisitos reais** (o que ele *realmente* precisa); encerrar dentro do tempo planejado (30 min a 1h), resumindo o que foi coberto.

**3) Acompanhamento** — revisar as notas, planejar novos encontros se necessário, agradecer o entrevistado.

!!! warning "Sete categorias de erros comuns em entrevistas de elicitação"
    Material baseado em Ferrari, Spoletini, Bano & Zowghi — "Common analysts' mistakes in requirements elicitation interviews":

    1. **Formulação da pergunta** — perguntas vagas, técnicas demais, irrelevantes, pedir soluções ao invés de necessidades, perguntas longas/compostas.
    2. **Omissão de perguntas** — não perguntar sobre outros stakeholders, não sondar quando algo não é entendido, não perguntar sobre o processo atual (AS-IS), não perguntar sobre priorização ou sobre o domínio do problema.
    3. **Ordem da entrevista** — começar com perguntas diretas demais, não resumir no final, pular entre tópicos sem lógica, repetir perguntas sem reformular.
    4. **Habilidades de comunicação** — linguagem artificial tipo "interrogatório", erros gramaticais, tom de voz inadequado, escuta pobre.
    5. **Comportamento do analista** — falta de confiança ou excesso de arrogância, atitude passiva, comportamento não profissional.
    6. **Interação com o entrevistado** — não construir relacionamento, tentar influenciar a resposta do entrevistado, interromper sem necessidade.
    7. **Planejamento** — má gestão do tempo, falta de pesquisa prévia sobre o domínio, falta de roteiro, pausas longas e desconfortáveis.

    Um achado notável: o **GNU Coding Standard** recomenda colocar uma atribuição dentro da condição de um `while` — mas dados empíricos mostram 38% mais acertos de interpretação quando essa atribuição é movida para fora, contradizendo a recomendação do guia de estilo.

## Design Thinking

**Design Thinking (DT)** é definido (Brown, 2012) como *"a human-centered approach to innovation that draws from the designer's toolkit to integrate the needs of people, the possibilities of technology, and the requirements for business success."* Está contido dentro do campo mais amplo de **User Experience (UX)** — e a UX, segundo a **ISO 9241-210**, inclui todas as emoções, crenças, preferências e comportamentos do usuário antes, durante e depois do uso de um sistema.

Seis características marcam o DT: **colaborativo**, **centrado no humano**, **"yes, and"** (construir sobre a ideia dos colegas), **interativo** (cíclico, não linear), **tendência à ação** e **adoção de limitação de tempo**. Pode ser entendido de três formas complementares: como **mentalidade** (combinação de pensamento divergente/convergente e prototipação), como **processo** (sequência iterativa de etapas) e como **toolbox** (dezenas de técnicas específicas).

O processo adotado na disciplina (modelo d.school de Stanford) tem 5 etapas:

| Etapa | O que fazer | Técnicas associadas |
|---|---|---|
| **1. Empatizar** | Reunir informações para se colocar no lugar do usuário: o que ele pensa, faz, sente e espera | Análise de stakeholders (mapa e matriz de influência), Brainstorming (7 regras do IDEO), Personas, Mapa de Empatia |
| **2. Definir** | A partir dos dados da empatia, identificar pontos de dor comuns entre usuários diferentes | Cartões de Insight, Diagrama de Afinidades |
| **3. Idealizar** | Reunir o máximo de pessoas e perspectivas para gerar soluções criativas, sem autocensura | Crazy 8's (8 esboços em 8 minutos) |
| **4. Prototipar** | Entender quais componentes das ideias funcionam, analisando impacto vs. viabilidade | Protótipos de baixa/média/alta fidelidade |
| **5. Testar** | Verificar se a solução atendeu às necessidades reais; medir também fatores como tempo de interação e acessibilidade | Testes de usabilidade |

!!! example "Matriz CSD — ponto de partida de um projeto de DT"
    Composta por **Certezas, Suposições e Dúvidas**, responde a três perguntas: O que já se sabe a respeito? Quais as possibilidades ou o que se acredita saber? Quais perguntas podem ser feitas? É o primeiro passo recomendado antes mesmo de empatizar.

Uma pesquisa mapeou dezenas de modelos de processo de DT na literatura — Double Diamond (Discover-Define-Develop-Deliver), IBM DT (Understand-Explore-Prototype-Evaluate), HPI (Understand-Observe-Ideate-Prototype-Test), entre outros — todos variações da mesma lógica de alternar divergência (gerar opções) e convergência (escolher a melhor).

## Tipos de Requisitos

A norma **IEEE 610** define requisito como: (1) uma condição ou capacidade necessária para um usuário resolver um problema ou atingir um objetivo; (2) uma condição ou capacidade que um sistema deve cumprir para satisfazer um contrato, padrão ou especificação; (3) a representação documentada de (1) ou (2).

Um Requisito de Software se divide em três grandes categorias:

### Requisitos Funcionais (RF)

Descrevem **o que** o sistema deve fazer, a nível dos usuários. Template recomendado: *"ATOR deve AÇÃO [sob] CONDIÇÃO"*.

!!! example "Exemplo de RF (sistema de pedidos de padaria)"
    "O Sistema deve enviar notificações à padaria quando um pedido for realizado pelo usuário."

### Regras de Negócio (RN)

São as políticas, condições ou restrições que regem a execução dos processos de uma organização — descrevem *como a organização funciona*, e costumam ser referenciadas dentro das especificações de casos de uso que elas afetam.

!!! example "Exemplo de RN"
    "Os usuários só podem finalizar o pedido se o valor total estiver acima do valor mínimo estabelecido."

### Requisitos Não Funcionais (RNF)

Declaram **características de qualidade** que o sistema deve possuir — e são frequentemente mais críticos do que os funcionais, pois podem afetar a **arquitetura inteira** do sistema (não apenas um componente isolado). Três características marcantes: são **subjetivos** (interpretação varia por pessoa), **relativos** (dependem do sistema) e **interativos** (realizar um RNF pode prejudicar outro).

A classificação de Sommerville organiza os RNFs em três ramos:

```
Requisitos não funcionais
├── Requisitos de produto (eficiência, confiança, proteção, usabilidade)
├── Requisitos organizacionais (reguladores: ambientais/operacionais/desenvolvimento; éticos)
└── Requisitos externos (legais: contábeis, segurança/proteção)
```

!!! note "Quantos tipos de RNF existem, afinal?"
    Mairiza & Zowghi (SAC'10) levantaram **252 tipos distintos** de RNF citados na literatura — e Ameller, Ayala, Cabot & Franch, em um estudo exploratório com arquitetos de software reais ([IEEE Xplore](https://ieeexplore.ieee.org/document/6345838)), encontraram confusão terminológica generalizada: em muitos projetos, os RNFs foram elicitados exclusivamente pelo arquiteto, sem documentação formal, e sem nenhum suporte de ferramenta dedicado para gerenciá-los.

    Para quem quiser uma referência normativa complementar sobre tipos e qualidade de requisitos, a **ISO/IEC/IEEE 29148:2018** ("Systems and software engineering — Life cycle processes — Requirements engineering") é hoje o padrão internacional de referência para o processo de ER, sucedendo o IEEE 830 citado no material do curso ([BSI](https://knowledge.bsigroup.com/products/systems-and-software-engineering-life-cycle-processes-requirements-engineering)).

## BPMN (Business Process Model and Notation)

BPMN é a notação usada na etapa de **Especificação** para modelar processos de negócio graficamente. Toda leitura de um diagrama BPMN responde a três perguntas: *O que precisa ser feito e quando?* (fluxo de controle); *Quem está fazendo o trabalho?* (recursos); *Em que precisamos trabalhar?* (dados).

### Elementos principais

| Categoria | Elementos |
|---|---|
| **Pools e Lanes** | **Pool**: retângulo com o nome do processo. **Lanes**: divisões internas por setor/papel organizacional. |
| **Objetos de fluxo** | **Eventos** (círculo: verde fino = início, duplo = intermediário, vermelho espesso = fim); **Tarefas** (retângulo, atômicas); **Gateways** (losango, controlam convergência/divergência) |
| **Conexões** | **Sequência** (seta contínua); **Mensagem** (seta tracejada, não pode conectar elementos do mesmo pool); **Associação** (linha pontilhada, liga artefatos a objetos de fluxo) |
| **Artefatos** | Anotação (texto informativo, não afeta o fluxo); Agrupamento; Objeto de dados; Depósito/Banco de dados |

### Tipos de gateway

| Gateway | Ícone | Divergência | Convergência |
|---|---|---|---|
| **Exclusivo (XOR)** | losango com X | Apenas uma rota é tomada, após avaliação condicional | Converge caminhos diferentes em um único resultante |
| **Inclusivo (OR)** | losango com círculo | Várias rotas possíveis, podem ocorrer simultaneamente (baseado em dados), mas não todas obrigatoriamente | Sincroniza as rotas de divergência em um único caminho |
| **Paralelo (AND)** | losango com "+" | Atividades executadas simultaneamente | Só continua quando *todos* os caminhos terminarem |
| **Baseado em eventos** | losango com pentágono | Divide rotas que competem — apenas a que ocorrer primeiro é seguida, as demais ficam inativas | — |
| **Complexo** | losango com asterisco | Usado quando nenhum outro gateway resolve a combinação necessária (ex.: decisão complexa) | Controla *quantas* das N rotas precisam concluir antes de seguir |

### Tipos de tarefa e boas práticas de nomenclatura

Tarefas podem ser de **serviço** (automática, sem intervenção humana), **envio/recebimento** (troca de mensagem), **usuário** (pessoa + sistema), **manual** (sem nenhum apoio de sistema), **regra de negócio** ou **script**. Boas práticas de nomenclatura recomendadas: usar palavras-chave com significado de negócio; evitar abreviações incomuns; não usar o tipo do elemento no nome; evitar artigos/pronomes; usar verbos no infinitivo.

**Eventos de borda**, anexados a atividades, tratam exceções: **interno** (erro na própria atividade, evento Error), **externo** (algo errado fora do processo, evento Message) e **timeout** (demora excessiva, evento Timer) — e podem ser **interruptivos** (borda dupla lisa, interrompe a atividade) ou **não-interruptivos** (borda dupla tracejada, dispara um fluxo paralelo sem interromper).

!!! tip "Boas práticas de modelagem"
    O fluxo segue da esquerda para a direita, respeitando a ordem cronológica — setas "voltando" visualmente (chegando pela esquerda de uma tarefa anterior) são consideradas má prática. Um fluxo de sequência nunca cruza os limites de um pool; só um fluxo de mensagens pode fazer isso.

**Referências normativas do material**: [OMG BPMN Specification](http://www.bpmn.org/) e Dumas, La Rosa, Mendling & Reijers, *Fundamentals of Business Process Management* (2ª ed., Springer, 2018). A versão vigente da especificação é a **BPMN 2.0.2** mantida pela [OMG](https://www.omg.org/spec/BPMN/2.0.1).

## Diagrama e Especificação de Casos de Uso

### Elementos e relacionamentos

| Elemento | Notação | Definição |
|---|---|---|
| **Ator** | boneco-palito | Elemento *externo* ao sistema que *interage* trocando informações com ele (pode ser um cargo, uma organização, outro sistema ou um equipamento) |
| **Caso de uso** | oval | Representa um objetivo que o sistema suporta — nome = verbo + substantivo — sem revelar a estrutura interna |
| **Fronteira do sistema** | retângulo | Delimita o que está sendo desenvolvido |

| Relacionamento | Entre | Semântica |
|---|---|---|
| **Comunicação** | Ator ↔ Caso de uso | Interação direta |
| **Include** | Caso de uso → Caso de uso | Inclui funcionalidade comum obrigatória, necessária para cumprir o objetivo do caso base |
| **Extend** | Caso de uso → Caso de uso | Funcionalidade *opcional*, acionada em pontos de extensão sob condição |
| **Generalização** | Ator↔Ator ou UC↔UC | Especifica variantes de um elemento mais geral |

!!! warning "Não crie casos de uso mínimos demais"
    O `«include»` deve ser usado quando há real ganho de reuso (ex.: "Sacar Dinheiro" e "Transferir Dinheiro" ambos incluindo "Autenticar Usuário") — mas criar um caso de uso para cada detalhe isolado, sem ganho de reuso real, é um erro comum.

### Especificação textual de um caso de uso

A estrutura padrão adotada na disciplina tem os campos: **ID**, **Nome**, **Descrição**, **Pré-condições**, **Fluxo Principal** (passos numerados), **Fluxos Alternativos/Secundários** (variações e desvios do fluxo principal, numerados com letras), **Pós-condições**, **Regras de Negócio** e **Requisitos Não-Funcionais**.

!!! example "Esqueleto de um fluxo alternativo"
    Um fluxo alternativo referencia o passo do fluxo principal onde se desvia, descreve a sequência alternativa e indica onde retorna (ex.: "3a.1. [condição]... 3a.4. Retorna ao passo 2 do Fluxo Principal"). É assim que um caso de uso como "Efetuar Logon" referencia, via `«extend»`, um caso de uso extraído como "Alterar Senha" quando a senha está expirada.

### User Story vs. Caso de Uso

Ambos identificam usuários e são centrados em um objetivo, mas diferem no nível de detalhe: a User Story (*"Como <papel>, eu quero <objetivo>, para que <benefício>"*) deixa deliberadamente de fora detalhes, servindo para suscitar conversa; o Caso de Uso documenta o fluxo de eventos de forma granular e completa, incluindo fluxos alternativos e de exceção.

## Análise, Negociação e Especificação de Requisitos

### Análise: encontrando problemas antes que eles cheguem à implementação

A análise verifica três coisas: **necessidade** (o requisito é mesmo necessário?), **consistência e completude** (há conflitos ou lacunas?) e **viabilidade** (é possível implementar dentro das restrições?). Um checklist típico de avaliação de um requisito pergunta: ele inclui aspectos de arquitetura/implementação (o que não deveria)? poderia ser decomposto? está alinhado aos objetivos de negócio? é ambíguo? é testável?

| Critério de qualidade (em inglês, como usado nos slides) | O que verifica |
|---|---|
| Atomic | O requisito é indivisível |
| Attainable | É alcançável dentro das restrições do projeto |
| Cohesive | Trata de um único assunto |
| Complete | Contém toda a informação necessária |
| Unambiguous | Admite apenas uma interpretação |
| Verifiable | Existe um processo finito e custo-efetivo para verificá-lo |
| Traceable | Pode ser rastreado a um requisito de nível mais alto |

### Priorização: o método MoSCoW

| Categoria | Significado | Critério |
|---|---|---|
| **M**ust Have | Inegociável | Sem isso, o produto não é viável/legal/seguro |
| **S**hould Have | Importante, mas não vital | Doloroso deixar de fora, mas há workaround |
| **C**ould Have | Desejável | Só se houver tempo e orçamento extra |
| **W**on't Have (this time) | Fora do escopo atual | Sem impacto real se ausente |

### Rastreabilidade

Tabelas de rastreamento relacionam requisitos entre si (ou a componentes de projeto), marcando dependências, conflitos e sobreposições em uma matriz. Para poucos requisitos (até ~250) uma planilha resolve; para centenas ou milhares, usa-se uma lista simplificada ("Requisito → Depende de") em vez de uma matriz esparsa.

### Negociação

Objetivo: chegar a um acordo sobre prioridades e sobre compromissos entre requisitos conflitantes, considerando três camadas de stakeholders — **primários** (operam o sistema, priorizam usabilidade), **secundários** (consomem a saída do sistema, geralmente gestores) e **terciários** (gestores de topo, interessados no papel estratégico do sistema). Técnicas de gestão da negociação incluem evitar ataques pessoais, desafiar "bloqueios" sem justificativa, criar opções de ganho mútuo (*win-win*) e evitar ultimatos.

!!! note "Para saber mais: negociação de requisitos como campo de pesquisa"
    Uma revisão sistemática recente (Abdullahi et al., *"Software Requirements Negotiation: a Systematic Literature Review"*) mapeou 67 estudos sobre o tema e aponta técnicas promissoras como **negociação baseada em agentes**, **TAICOS**, **WinWin** e **WinBook** — mas conclui que a pesquisa na área segue insuficiente e carece de propostas mais concretas.

### Especificação: do texto aos modelos formais

Requisitos podem ser especificados de forma **textual** (linguagem natural, sentenças numeradas) ou via **modelos** gráficos. Para sistemas mais complexos, a disciplina apresenta a **SysML** (*Systems Modeling Language*, padrão [OMG](http://www.omg.org/spec/SysML/1.5/)) com seus diagramas de Caso de Uso, Requisitos, Blocos, Sequência, Atividades e Estados — usados, por exemplo, para especificar um veículo híbrido (requisito raiz "HSUV Specification" decomposto em Eco-Friendliness, Performance, Ergonomics etc.).

## Validação e Gerenciamento de Requisitos

### Validação

Consiste em verificar o documento de requisitos quanto a **consistência, completude e acurácia** — perguntando, essencialmente: *"realmente entendi o que o cliente deseja?"*. As principais técnicas são **prototipação**, **desenvolvimento do manual do usuário**, **validação de modelos**, **checklists de revisão** e **reuniões de revisão de requisitos**.

!!! tip "Reuniões de revisão de requisitos"
    Equipe recomendada: 3 a 10 pessoas (especialistas de domínio, usuário final, representante do cliente, engenheiro de requisitos e responsáveis pelo design). Antes da reunião, alguém que não participou da escrita remove erros triviais (ortografia, formatação). Estimativa de produtividade: **20 a 40 requisitos revisados por hora** — um documento de 400 requisitos exige cerca de 50 horas de esforço com uma equipe de 4 pessoas.

### Gerenciamento e rastreabilidade

O **gerenciamento de requisitos** é o processo de compreender e controlar as mudanças nos requisitos — e mudanças são **inevitáveis**: erros, evolução do conhecimento do domínio, mudanças de prioridade do cliente, mudanças organizacionais e ambientais fazem parte do jogo. A **gerência de configuração** controla versões e modificações dos documentos de requisitos.

Seis tipos de rastreamento são descritos: das **fontes** (quem/o quê especificou o requisito), da **razão** (por que foi especificado), **requisito-requisito**, **requisito-arquitetura**, **requisito-projeto** e **requisito-interface**. Padrões de domínios críticos exigem diferentes níveis de rastreabilidade obrigatória — por exemplo, a norma de aviação **RTCA DO-178C** exige 7 caminhos de rastreamento obrigatórios, contra 4 da automotiva **ISO 26262** e da médica **IEC 62304**.

!!! note "Nem todo processo de ER é igual"
    "Os processos de requisitos variam de uma organização para outra" — fatores como maturidade técnica, cultura organizacional e domínio de aplicação tornam impossível um processo "ideal" único. A conclusão prática do material: um processo de ER eficiente existe, sobretudo, para evitar o mal-entendido de comunicação — a causa-raiz mais citada de projetos de software que falham.

## Privacidade na Engenharia de Requisitos

### Da definição clássica à LGPD/GDPR

A noção de privacidade tem raízes antigas (Aristóteles distinguia esfera pública de privada), mas a formulação moderna mais citada é de **Warren e Brandeis (1890)**: privacidade como *"the right to be let alone"*. **Westin (1968)** complementa: *"Privacy is the claim of individuals, groups, or institutions to determine for themselves when, how, and to what extent information about them is communicated to others."*

No Brasil, a **LGPD** (Lei 13.709/2018, inspirada na GDPR europeia) regula o tratamento de dados pessoais em qualquer setor da economia. Define **10 princípios de tratamento** (livre acesso, necessidade, adequação, finalidade, qualidade dos dados, prevenção, segurança, transparência, não discriminação e responsabilização), **bases legais** para tratamento (consentimento, cumprimento de obrigação legal, execução de políticas públicas, execução de contrato, interesse legítimo, entre outras) e **9 direitos do titular** dos dados (confirmação, acesso, correção, anonimização, portabilidade, eliminação, informação sobre compartilhamento, informação sobre a possibilidade de não consentir, e revogação do consentimento).

!!! warning "Desenvolvedores ainda não pensam em privacidade por padrão"
    Pesquisa citada em aula (Hadar et al., 2018; Peixoto et al., 2020) mostra que desenvolvedores de software são frequentemente desencorajados de priorizar privacidade e costumam confundir privacidade com segurança de dados. Um entrevistado resumiu: *"[Privacy is] to make sure that other users, hackers, will not access the client's [data subject] data"* — ignorando toda a dimensão de uso e compartilhamento legítimo (mas indevido) dos dados.

### Privacy by Design — os 7 princípios de Ann Cavoukian

1. **Proativo, não reativo** — antecipa riscos antes que se materializem.
2. **Privacidade como configuração padrão** — se o usuário não fizer nada, sua privacidade permanece protegida.
3. **Privacidade embutida no design** — parte integral da arquitetura, não um "complemento".
4. **Funcionalidade plena** (*positive-sum, não zero-sum*) — evita falsas dicotomias como "privacidade vs. segurança".
5. **Segurança de ponta a ponta** — proteção durante todo o ciclo de vida do dado.
6. **Visibilidade e transparência** — tudo deve funcionar como prometido, de forma verificável.
7. **Respeito pela privacidade do usuário** — mantém o indivíduo no centro, com defaults fortes e opções claras.

### Frameworks de threat modeling de privacidade

| Framework | Foco | Mecânica |
|---|---|---|
| **LINDDUN GO** ([linddun.org](https://linddun.org/go/)) | Ameaças de privacidade em sistemas em geral | Jogo de cartas leve com 33 ameaças em 7 categorias: **L**inking, **I**dentifying, **N**on-repudiation, **D**etecting, **D**ata disclosure, **U**nawareness & unintervenability, **N**on-compliance. Cada carta tem perguntas de elicitação a aplicar a cada "hotspot" do sistema. |
| **PLOT4AI** ([plot4.ai](https://plot4.ai/)) | Ameaças específicas de sistemas de IA/ML | 138 cartas em 8 categorias (Data & Governance, Privacy & Data Protection, Bias & Fairness, Ethics & Human Rights, entre outras), mapeadas ao ciclo de vida de um sistema de IA (Design, Input, Model, Output, Deploy, Monitor) |

### Privacy Criteria Method (PCM) — a contribuição do CIn/UFPE

Método próprio de pesquisa do grupo (Peixoto, Silva, Vilela et al., *Requirements Engineering*, 2023) que ajuda times a incorporar privacidade já na especificação de requisitos, a partir de uma User Story. Quando uma história de usuário envolve **coleta, uso, retenção ou divulgação** de dados pessoais, aciona-se o PCM, com 7 campos: **Atores** (Owner/Controller, Processor, Third Party), **Relação de confiança entre atores**, **Informação pessoal coletada** (classificada em Privada/Pública/Semi-pública), **Propósito e duração do uso/retenção**, **Restrição de privacidade** (preferência e política de conformidade), **Cenário de risco de privacidade** (vulnerabilidade potencial, explorada por uma ameaça — tipicamente uma das 7 categorias do LINDDUN — causando um dano potencial) e **Mecanismos de privacidade** (ex.: pseudonimização, consentimento).

!!! example "User Story reescrita após passar pelo PCM"
    Original: *"Como gerente, eu quero vender os dados pessoais dos meus clientes, de forma que eu possa receber dinheiro."* Após aplicar o PCM, a história ganha critérios de aceitação adicionais obrigatórios: é necessário escolher explicitamente os terceiros com quem os dados serão compartilhados, e o cliente deve consentir explicitamente ao compartilhamento de suas preferências de compra com os parceiros.

## Referências e para saber mais

**Citadas diretamente no material da disciplina:**

- Kotonya, G.; Sommerville, I. *Requirements Engineering: Processes and Techniques*. Wiley, 1998.
- Pressman, R. S. *Engenharia de Software: Uma Abordagem Profissional*. 6ª/7ª ed., Bookman/McGraw-Hill, 2011.
- Dumas, M.; La Rosa, M.; Mendling, J.; Reijers, H. *Fundamentals of Business Process Management*. 2ª ed., Springer, 2018.
- OMG. *Business Process Model and Notation Specification*. [bpmn.org](http://www.bpmn.org/)
- Mairiza, D.; Zowghi, D. *An Investigation into the Notion of Non-Functional Requirements*. SAC'10.
- Ameller, D.; Ayala, C.; Cabot, J.; Franch, X. *How do Software Architects Consider Non-functional Requirements: An Exploratory Study*. [IEEE Xplore](https://ieeexplore.ieee.org/document/6345838)
- Cavoukian, A. et al. *Privacy by Design: The 7 Foundational Principles*. Information and Privacy Commissioner of Ontario, 2009.
- Wuyts, K.; Sion, L.; Joosen, W. *LINDDUN GO: A Lightweight Approach to Privacy Threat Modeling*. EuroS&PW 2020.
- Peixoto, M.; Silva, C.; Araújo, J.; Gorschek, T.; Vasconcelos, A.; Vilela, J. *Evaluating a Privacy Requirements Specification Method by Using a Mixed-Method Approach: Results and Lessons Learned*. Requirements Engineering, 28(2), 2023.
- Parizi, R.; Prestes, M.; Marczak, S.; Conte, T. *How Has Design Thinking Being Used and Integrated Into Software Development Activities? A Systematic Mapping*. Journal of Systems and Software, 2022.

**Enriquecimento externo (não estava no material original, mas complementa diretamente os temas acima):**

- [ISO/IEC/IEEE 29148:2018](https://knowledge.bsigroup.com/products/systems-and-software-engineering-life-cycle-processes-requirements-engineering) — padrão internacional vigente de processos de Engenharia de Requisitos, que atualizou e substituiu o IEEE 830 citado no material original do curso.
- [OMG BPMN 2.0.2](https://www.omg.org/spec/BPMN/2.0.1) — versão vigente da especificação formal do BPMN.
- [napire.org](https://www.napire.org/) — site oficial do survey NaPiRE, com os relatórios completos de cada rodada da pesquisa.
- [LGPD — Lei 13.709/2018](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) — texto oficial da Lei Geral de Proteção de Dados brasileira.
