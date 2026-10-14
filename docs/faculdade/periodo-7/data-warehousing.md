# DATA WAREHOUSING

---

Disciplina **IF696 — Integração de Dados e Warehousing**, do Centro de Informática da UFPE, ministrada pelo **Prof. Robson do Nascimento Fidalgo** (rdnf@cin.ufpe.br). O material desta página combina (1) o conteúdo teórico da aula introdutória "DW e OLAP" e (2) um estudo de caso real — uma dissertação de mestrado que aplica a modelagem dimensional de Kimball para construir um DW institucional de acompanhamento de evasão universitária, usado aqui como referência de projeto.

!!! note "Dados da disciplina (slides de abertura)"
    - **Público-alvo**: interessados em pesquisar e/ou adquirir competências para projetos de *Business Intelligence* (DW e OLAP) e Engenharia de Dados para Big Data.
    - **Ementa**: conceitos básicos, modelos, técnicas de modelagem e ferramentas para projetar e construir bancos de dados para ambientes de BI (DW e OLAP) e Big Data.
    - **Objetivo**: discutir e por em prática ETL, Data Warehouse, OLAP, painéis de indicadores e Big Data.
    - **Avaliação**: defesa de um projeto em equipe.
    - **Bibliografia principal**: KIMBALL, Ralph; ROSS, Margy. *The Data Warehouse Toolkit: The Definitive Guide to Dimensional Modeling*. Wiley, 2019.
    - **Bibliografia complementar**: LAGO, Karine; ALVES, Laennder. *Dominando o Power BI* (3ª ed. atualizada). DATAB, 2021.

## Motivação: Business Intelligence

Vivemos uma "época de calamiDADOS" — o volume de dados gerados pelas organizações cresce muito mais rápido do que a capacidade de analisá-los. **Business Intelligence (BI)** é o termo guarda-chuva que representa toda a infraestrutura teórica e tecnológica para organizar e analisar dados de diversas fontes.

A arquitetura típica de BI flui assim: fontes operacionais (sistema operacional, ERP, CRM, planilhas, SQL) → **Extract** → processo **ETL** (Validação → Limpeza → Transformação → Agregação → Carga) → **Data Warehouse** (com seus *Data Marts*) → consumo por OLAP, *Data Mining* (fora do escopo desta disciplina), visualização de dados, relatórios, *dashboards* e alertas.

### BI x Sistemas Operativos

| Business Intelligence | Sistemas Operativos (OLTP) |
|---|---|
| Visão da corporação (melhorar o entendimento) | Visão de um negócio da corporação (melhorar o controle) |
| Processamento analítico (carga e consulta) | Processamento transacional (inclusão, atualização, exclusão, consulta) |
| Agiliza e facilita análises para tomada de decisão | Agiliza e automatiza funções repetitivas |
| Histórico — grande volume, poucas atualizações (em lote) | Status corrente — menor volume, muitas atualizações (on-line) |
| Consultas *ad-hoc* e longas (agrupamentos) | Consultas pré-definidas e diretas (seleções pontuais) |
| BD desnormalizado (poucas junções, mais redundância, esquema simples) | BD normalizado (mais junções, menos redundância, esquema complexo) |

Dada essa heterogeneidade, é interessante separar os dados em dois ambientes: o **operacional** (que normalmente já existe) e o de **Business Intelligence** (a construir — o Data Warehouse).

## O que é um Data Warehouse

Um DW é um **banco de dados estruturado** (normalmente relacional) que armazena dados homogeneizados e históricos para tomada de decisão, integrando diferentes dados de uma empresa em um único repositório. Serve para: integrar dados de múltiplas fontes; facilitar análise sem impactar os sistemas operacionais; obter informação de qualidade; atender diferentes usuários finais; dar flexibilidade a novas análises; e prover autonomia ao tomador de decisão.

!!! quote "Duas definições clássicas"
    **William H. Inmon** (o "pai do DW"): "Um DW é um conjunto de dados **orientado por assuntos, não volátil, variável com o tempo e integrado**, criado para dar suporte à decisão."

    **Ralph Kimball**: "É uma **cópia dos dados transacionais** especificamente estruturada para consulta e análise — é o lugar onde as pessoas podem acessar seus dados."

As quatro características da definição de Inmon: **orientado por assunto** (organizado por processo, não por aplicação); **não volátil** (carga em lote, sem sobrescrever); **variável com o tempo** (dados históricos); **integrado** (homogeneizado e consistente).

Principais objetivos de um DW: prover dados **consistentes** (tratando heterogeneidades de nomes/valores/tipos — ex.: "ECivil", "EC", "1", "S" todos convergindo para `EstadoCivil = Solteiro`); ser **flexível** a mudanças (sem invalidar aplicações existentes); ser um **lugar seguro** (controle de acesso a dados confidenciais); **facilitar o acesso** (dados e ferramentas intuitivos para o tomador de decisão, não para desenvolvedores); e ser **bem aceito** — aceitação tem mais a ver com simplicidade do que com tecnologia de ponta, e, diferente de um sistema operacional, o uso do DW é **opcional**.

### Data Warehouse x Data Mart

- **Data Warehouse (DW)**: banco otimizado para fornecer uma imagem global da realidade de negócio da organização; demorado, complexo e custoso de implementar.
- **Data Mart (DM)**: um DW específico a um assunto/negócio/processo — subconjunto do DW que atende aos requisitos de uma atividade de negócio específica. Reduz tempo, complexidade e custo de implantação, mas exige planejamento prévio para evitar "ilhas de dados".

### Inmon x Kimball: duas filosofias de construção

| | Inmon | Kimball |
|---|---|---|
| Implementação | Monolítica (Top-Down) | Modular (Bottom-Up) |
| Fluxo | DW central → se ramifica em Data Marts | Data Marts → convergem para o DW |
| Normalização | DW/DM podem ser normalizados | Não recomenda normalizar |
| Classificação (Breslin, 2004) | *Data-driven* — repositório central no menor nível de detalhe (*atomic data warehouse*), com agregações feitas a nível departamental | *Process oriented* — granularidade e agregações definidas para atender a demanda de um processo de negócio específico |
| Primeiro passo | Integrar os dados disponíveis, entendê-los e só então determinar quais requisitos eles atendem | Levantar requisitos de negócio/dados e avaliar a capacidade da organização de fornecê-los |

Constatação prática (reforçada tanto nos slides quanto na dissertação usada como estudo de caso): a solução completa é complexa demais para ser feita de uma vez — o ideal é **planejar o todo e construir por partes**, com um gestor "caxias" e um patrocinador influente, priorizando entregas rápidas que agradem aos usuários e justifiquem o investimento.

## Elementos básicos do Data Warehousing

**Data Warehouse** (o banco de dados em si) é diferente de **Data Warehousing** (o processo de construí-lo). A arquitetura típica (KIMBALL et al., 2002) tem 4 colunas:

1. **Operational Source Systems** — os sistemas operacionais de onde os dados são extraídos.
2. **Data Staging Area** — onde os dados são limpos, combinados e padronizados ("conformados"); não oferece consulta ao usuário; usa arquivos simples/tabelas relacionais e processamento sequencial.
3. **Data Presentation Area** — onde os Data Marts dimensionais (atômicos e sumarizados, baseados em um único processo de negócio) ficam disponíveis, conectados entre si por um **"DW Bus"** de fatos e dimensões conformados.
4. **Data Access Tools** — ferramentas de consulta *ad hoc*, geradores de relatório, aplicações analíticas, modelagem preditiva.

O processo de **ETL** (Extrair, Transformar, Carregar) resume-se a: **Extrair** (dados operacionais e externos) → **Transformar** (filtrar, limpar, recodificar, padronizar, integrar) → **Carregar** (povoar, indexar, testar) → resultado: o Data Mart/DW.

## Modelo Dimensional

O objetivo da modelagem dimensional é **tornar o esquema do BD mais simples** (menos tabelas), **intuitivo** (nomes significativos) e **otimizado** (desnormalizado, poucas junções) para favorecer consultas e análises. Seus dois componentes principais:

- **Tabelas de dimensão** — propriedades descritivas (o contexto).
- **Tabelas de fato** — medidas (o que aconteceu).

### Esquema Estrela (Star Schema)

Uma tabela fato central, com chaves estrangeiras para cada dimensão e as medidas do processo de negócio, cercada pelas tabelas de dimensão (cada uma desnormalizada, 1FN). É o modelo mais recomendado por Kimball:

!!! tip "Por que Kimball não recomenda normalizar as dimensões"
    1. Depois da carga inicial, as dimensões crescem pouco — é a tabela fato que mais cresce, e ela já é bem normalizada por natureza.
    2. O espaço economizado ao normalizar dimensões é pequeno (dimensões são ~10% do volume do DW).
    3. A perda de performance causada pelas junções (*joins*) extras é grande.

### Esquema Floco de Neve (Snowflake Schema)

Normaliza as tabelas de dimensão, quebrando-as em dimensões "principais" e "secundárias" encadeadas (ex.: Produto → Marca → Categoria). Resultado: mais tabelas, consultas mais complexas e mais lentas — mas esquema mais "limpo" sem redundância.

| Critério | Estrela | Floco de Neve |
|---|---|---|
| Clareza | Mais fácil | Mais difícil |
| Número de tabelas | Menor | Maior |
| Complexidade de consultas | Mais simples | Mais complexa |
| Performance | Mais rápida | Mais lenta |

### Esquema Constelação (Fact Constellation)

Permite que **múltiplas tabelas de fatos compartilhem tabelas de dimensões** — por exemplo, `Fato_Vendas` e `Fato_Compras` compartilhando `Dim_Funcionario` e `Dim_Produto`.

### Modelagem tradicional x modelagem dimensional

Um esquema tradicional (normalizado, tipo ERP, com dezenas/centenas de tabelas — ilegível para um usuário final) visa refletir fielmente os relacionamentos entre os dados e eliminar redundância; é inadequado para tomada de decisão porque vai contra os princípios de recuperação intuitiva e de alta performance do DW. A partir de um esquema tradicional único, **vários esquemas dimensionais (Data Marts)** podem ser derivados, cada um focado em um processo de negócio específico (ex.: DM_Vendas, DM_Estoque, DM_Produção).

As "5 W e 3 H" ajudam a identificar dimensões típicas: **When** (Quando), **Where** (Onde), **What** (O quê) e **Who** (Quem) são os tipos de dimensão mais comuns; **Why** (Por quê) e **How** (Como) raramente viram dimensões; **How many/How much** corresponde às medidas/fatos.

## Tabela de Dimensão

Correspondem aos pontos de entrada das consultas e são fundamentais para tornar o DW compreensível — seus campos armazenam descrições de negócio e definem rótulos, restrições e agrupamentos dos relatórios.

- **Qualidade dos campos**: devem refletir a terminologia do negócio, ser textuais e categóricos (ex.: idade/salário → faixa etária/faixa salarial), com rótulos intuitivos (evitar abreviaturas) e nunca armazenar "valores inteligentes" (códigos com significado embutido).
- **Hierarquias implícitas**: uma dimensão pode ter várias hierarquias (ex.: Tempo pode ter H1: Ano→Semestre→Trimestre; H2: Ano→Bimestre→Mês→Dia). O nível hierárquico mais baixo define o **grão** da dimensão.
- **Granularidade** = nível de detalhe, ilustrada pela metáfora da peneira: peneira de furos grandes (granularidade grande, ex. vendas por ano) retém poucos dados; peneira de furos pequenos (granularidade pequena, ex. vendas por dia) retém muitos dados.
- **Volume**: dimensões têm muitos campos mas poucos registros (normalmente < 10% do volume total do DW).
- **Chaves substitutas (*surrogate keys*)**: as dimensões usam PKs simples — inteiros autoincrementáveis, sem significado de negócio — que garantem estabilidade e ficam transparentes para o usuário, servindo apenas de ligação entre dimensões e fatos. Evitar chaves "naturais" ou "inteligentes" (datas, códigos de negócio) como PK; usá-las apenas para manter o vínculo com a fonte.

### Técnicas avançadas de dimensões

- **Dimensões degeneradas**: uma chave (ex.: número de nota fiscal, pedido, tíquete) fica diretamente na tabela de fatos, sem tabela de dimensão própria, porque tem a mesma granularidade da TF — criar uma dimensão à parte geraria sobrecarga desnecessária (cardinalidade 1:1 com a TF).
- **Dimensões com papéis (*role-playing*)**: a mesma dimensão (ex.: Data) aparece várias vezes na TF com papéis diferentes (data do pedido, data de envio). Solução: criar uma *view* por papel, cada uma com nomes de campo distintos, para que cada view seja "vista" como uma dimensão independente nos relatórios.
- **Relacionamentos M:N entre dimensão e fato**: quando o relacionamento esperado 1:N não se sustenta (ex.: um paciente pode ter múltiplos diagnósticos), usa-se uma **tabela ponte** entre a dimensão e o fato, com um "fator de peso" indicando a participação percentual de cada valor (a soma dos pesos de um grupo deve totalizar 100%).
- **Produtos heterogêneos**: quando a organização oferece produtos/serviços muito diferentes entre si (gerando muitos campos "não se aplica"), cria-se uma dimensão/fato geral mais dimensões/fatos específicos por produto, reutilizando a mesma PK da dimensão base nas dimensões específicas.
- **Dimensões conformadas**: têm o **mesmo significado** em todas as tabelas de fato que as referenciam — mesmos nomes, tipos e valores — construídas de forma sincronizada na *staging area*. São essenciais para integrar Data Marts e permitir relatórios que cruzem diferentes processos de negócio; sem conformidade, relatórios ficam com rótulos/agrupamentos inconsistentes. A gestão de uma dimensão conformada cabe a um grupo chamado **"autoridade da dimensão"**.
- **Minidimensões**: fragmentam uma dimensão grande (ex.: Cliente, com até 100 milhões de registros) separando atributos estáticos (dimensão base) dos voláteis (minidimensão), ligadas ambas à tabela fato — controla o crescimento explosivo e preserva histórico. Não é normalização; os atributos da minidimensão devem ter baixa cardinalidade (criar faixas/categorias).
- **Dimensões *outrigger***: ligam-se apenas à dimensão base (não diretamente à TF) — devem ser exceção, não regra.
- **Esquema centopeia (*centipede schema*)**: quando um modelo tem ≥ 25 dimensões, é sinal de dependência excessiva entre dimensões — a solução é fundir as dimensões dependentes.
- **Dimensão bugiganga (*junk dimension*)**: reúne campos de baixa correlação da TF que funcionam como filtros (flags soltas) em uma única dimensão artificial, reduzindo o número de colunas da TF.

### A dimensão Data

Uma das dimensões mais frequentes e relevantes — complexa no mundo real (dia, mês, período fiscal, feriado, trimestre, semestre, ano...). Diferente das demais, pode ser **carregada antecipadamente** (sem precisar de fonte de dados), cobrindo de 5 a 10 anos (passado e futuro). Não se usa diretamente o tipo `DATE`/`TIMESTAMP` do SQL (nem funções como `DATEPART`/`DATEDIFF`) porque eles não capturam particularidades de negócio como calendário fiscal, estações ou feriados — daí a necessidade de uma tabela de dimensão dedicada com dezenas de atributos derivados. Quando a granularidade por dia não basta (ex.: análises por minuto/hora), cria-se uma dimensão **Tempo do Dia** separada, para não sobrecarregar a dimensão Data.

## Tabela de Fato

Basicamente normalizada (3FN), formada principalmente por chaves estrangeiras e medidas; raramente tem PK própria (quando necessária, prefere-se uma *surrogate key*). Tem muitas linhas (milhões/bilhões, crescendo a cada carga) e poucas colunas — representa ~90% do volume de dados do DW, e equivale a um relacionamento n-ário entre as dimensões.

Um **fato** é a interseção das FKs das dimensões + medida(s); as dimensões definem o grão da tabela de fatos.

### Tipos de medida

| Tipo | Regra | Exemplos |
|---|---|---|
| **Aditivas** | `SUM` funciona ao longo de qualquer dimensão | Valor vendido, quantidade vendida |
| **Semi-aditivas** | `SUM` só funciona ao longo de algumas dimensões (tipicamente só pelo nível mais baixo da dimensão Data); nos demais casos, usar `AVG`/`MIN`/`MAX` | Quantidade em estoque, saldo em conta |
| **Não aditivas** | `SUM` nunca funciona; usar `AVG`/`MIN`/`MAX`/`COUNT`, ou modelar como faixa/categoria em dimensão | Valor unitário, percentual de desconto, temperatura |

Medidas textuais também existem (listas pré-definidas, ex.: "Péssimo"/"Bom"/"Ótimo"), mas só permitem contagem (`COUNT`) — prefira transformá-las em atributos de dimensão.

### Tabela de fatos sem medidas (*factless fact table*)

Uma tabela de fatos pode não ter medidas — serve apenas para registrar a **cobertura/abrangência** de uma ação (ex.: "quais produtos entraram em promoção"). Comparando (com `MINUS`/`EXCEPT`) essa tabela de cobertura com a tabela de fatos de vendas, é possível responder perguntas como "quais produtos entraram em promoção e não foram vendidos durante ela".

### Os 3 tipos de tabela de fato

| Critério | Transação | Instantâneo periódico | Instantâneo acumulado |
|---|---|---|---|
| Período de tempo | Um ponto no tempo | Intervalos regulares pré-definidos | Indeterminado, geralmente curto |
| Grão | Uma linha por transação | Uma linha por período | Uma linha por "tempo de vida" do processo |
| Carga | `INSERT` | `INSERT` | `INSERT` e `UPDATE` |
| Atualizações | Raras | Raras | Constantes |
| Dimensão tempo | Data da transação | Data de final do período | Várias datas, uma por etapa |
| Exemplo | Transações de venda | Inventário diário/mensal | Pedido com data de recebimento, inspeção, envio, venda |

- **Transação**: captura detalhadamente cada evento/transação ocorrido, usando medidas aditivas; não confundir a frequência da *carga* com a *granularidade* do grão.
- **Instantâneo periódico**: tira uma "fotografia" do estado em cada carga; usa medidas semi-aditivas (TFs densas — uma linha para cada combinação possível, mesmo sem movimento, ex.: estoque de todo produto registrado todo dia, o que pode gerar dezenas de GB/ano, exigindo estratégias como manter uma TF detalhada recente + uma TF histórica agregada).
- **Instantâneo acumulado**: registra múltiplas datas/estágios de um mesmo processo (ex.: recebido → inspecionado → autorizado → enviado), atualizando a mesma linha a cada novo estágio (N-1 updates até o processo completar).

## Matriz de Barramento do DW (*Bus Matrix*)

Ferramenta — inspirada na arquitetura de computadores — para planejar o DW mostrando as interseções entre processos de negócio (linhas) e dimensões comuns/conformadas (colunas). Segundo Kimball, é **"o artefato de análise mais importante do projeto de um DW"**: serve para design técnico, gerência de projeto e comunicação organizacional. Permite que diferentes Data Marts sejam implementados por equipes/momentos diferentes e depois conectados em uma visão integrada, além de identificar imediatamente quais dimensões merecem atenção especial por aparecerem em muitos processos.

## Fases do projeto dimensional

Quatro perguntas norteiam toda modelagem dimensional (Kimball):

1. **Selecionar o processo de negócio** — qual processo é mais crítico e viável? (processo ≠ departamento)
2. **Declarar o grão** — o que descreve uma linha da tabela de fatos?
3. **Identificar as dimensões** — como o pessoal do negócio descreve os dados desse processo?
4. **Identificar as medidas** — o que podemos medir, de forma coerente com o grão escolhido?

## Slowly Changing Dimensions (SCD)

Jargão para o problema de **como refletir, no DW, uma mudança no valor de um atributo de dimensão** vinda do sistema operacional — sem colocar o atributo na tabela de fatos nem tornar as dimensões dependentes da dimensão tempo.

| Tipo | Estratégia | Observação |
|---|---|---|
| **SCD0** | Não faz nada | — |
| **SCD1** | Sobrescreve o valor | Simples e rápido, mas perde o histórico; indicado para correções |
| **SCD2** | Adiciona uma nova linha (nova *surrogate key*) | **A mais usada**; preserva histórico perfeitamente; cuidado em dimensões muito grandes |
| **SCD3** | Adiciona uma nova coluna (valor atual + anterior) | Histórico limitado a uma mudança |
| **SCD4** | Cria uma minidimensão com os dados voláteis | Controla o crescimento da dimensão |
| **SCD5** | SCD4 + SCD1 (view da minidimensão como *outrigger*) | Evita *join* com a TF para saber o valor atual |
| **SCD6** | SCD3 + SCD1 + SCD2 | Complexa, mas permite comparar atual/anterior mantendo todo o histórico |
| **SCD7** | Duas FKs na TF (uma histórica via SCD2, uma atual via SCD1) | Mesmo resultado do SCD6, de forma menos complexa |

Na dúvida entre as estratégias, Kimball recomenda **optar pelo SCD2** — é melhor manter o histórico completo.

## Abstração do DW: o cubo de dados

O **cubo de dados** é uma metáfora para visualizar e organizar os dados, permitindo analisar várias dimensões simultaneamente e manipular agregações em diferentes níveis de hierarquia. Elementos/metadados de um cubo: **medida** (o valor numérico, ex. Vendas_R$), **membro** (um valor específico de uma dimensão, ex. "Abril"), **dimensão** (ex. Tempo), **hierarquia** (ex. Ano→Semestre→Mês), **nível** (ex. "Ano") e **fato** (a célula = interseção de membros).

## OLAP (*On-Line Analytical Processing*)

Conjunto de tecnologias para analisar o DW/cubo de dados: fornece dados agregados (totais, médias, mínimos...), tem alta performance com consultas interativas, lida com a dimensão temporal/histórica, faz cruzamentos de dados e analisa em diferentes níveis de detalhe.

### Principais operações OLAP

- **Drill Down / Roll Up**: caminham pelos níveis de uma hierarquia — *drill down* desce (mais detalhe), *roll up* (ou *drill up*) sobe (mais agregado). Equivalem, em SQL, a mudar o nível do `GROUP BY` (ex.: agregar vendas por Estado → detalhar por Cidade).
- **Treliça de agregados**: estrutura (grafo direcionado) que define a hierarquia de todas as combinações possíveis de `GROUP BY` entre as dimensões de um cubo — cada nó ("cuboid") é um agregado possível, e uma aresta de um nó para outro indica que o segundo pode ser derivado do primeiro.
- **Rotação (*pivot*)**: gira o cubo, trocando a orientação dos eixos para obter diferentes visões dos mesmos dados.
- **Slice and Dice**: "fatia" o cubo, restringindo a análise a um subconjunto dos dados **sem inverter eixos** — semelhante às cláusulas `SELECT`/`WHERE` do SQL. *Slice* corta o cubo em um só eixo; *dice* corta em múltiplos eixos simultaneamente.

### Arquiteturas OLAP: ROLAP, MOLAP, HOLAP

| | ROLAP (Relacional) | MOLAP (Multidimensional) | HOLAP (Híbrido) |
|---|---|---|---|
| Dados de base | Tabela relacional | Cubo proprietário | Tabela relacional |
| Agregações | Tabela relacional | Cubo proprietário | Cubo proprietário |
| Performance de consulta | Rápida | Imediata | Mais rápida |
| Consumo em disco | Baixo | Alto | Médio |
| Manutenção do cubo | Baixa | Alta | Média |

- **ROLAP**: usa SQL sobre um SGBD relacional para manipular dados multidimensionais; lida bem com fatos atômicos e sumarizados, em ambientes dinâmicos com muitas dimensões.
- **MOLAP**: usa um **MDDB** (banco de dados multidimensional) proprietário, com matrizes n-dimensionais, para manipular fatos agregados; não lida bem com fatos atômicos, muitas dimensões ou grandes volumes.
- **HOLAP**: combina os dois — dados-base ficam relacionais (SQL), agregações ficam no cubo multidimensional (MDDB) — mais complexo de administrar, mas equilibra os pontos fortes de ambos.

## Estudo de caso aplicado: um Data Warehouse para acompanhar evasão universitária

Como material de apoio a projeto, a disciplina também trabalha com um exemplo real e completo de aplicação da modelagem de Kimball: a dissertação *"Proposta de um Data Warehouse para Apoio à Tomada de Decisão sobre Evasão Institucional em uma Instituição Federal de Ensino Superior"* (**Felipe Rodrigo de Moraes Mendes**, Mestrado Profissional em Administração, **UNIFEI**, 2020, orientador Prof. Dr. Fabio Favaretto), que constrói um DW para monitorar a evasão de alunos a partir dos dados do **SIGAA** (sistema acadêmico usado pela Unifei e por outras IFES, incluindo a UFRN, que o desenvolveu).

### O problema e a metodologia

A pergunta de pesquisa: *"Como os dados referentes aos discentes armazenados no SIGAA podem ser organizados em um repositório institucional que sirva de apoio à tomada de decisão sobre o fenômeno da evasão?"* O autor combina duas metodologias:

- **Soft Systems Methodology (SSM)**, de Peter Checkland — metodologia geral de pesquisa-ação, baseada em um ciclo de aprendizagem de 4 fases: explorar a situação problemática → investigar ações intencionais relevantes → discutir mudanças possíveis → definir ações de melhoria.
- O **método de Kimball** (definição de requisitos → modelagem dimensional → modelagem física → ETL → implementação) encaixado como uma etapa dentro do ciclo da SSM.

A proposta metodológica resultante tem 5 passos: (1) definir requisitos para o DW sobre evasão; (2) comparar **visões de mundo** da literatura (pesquisa bibliográfica) com a **realidade dos dados** do SIGAA (pesquisa documental); (3) discutir requisitos desejáveis x viáveis (triangulação); (4) criar o DW aplicando o método de Kimball; (5) implementar o DW como ação de melhoria — ciclo que pode se repetir iterativamente.

!!! note "Como calcular a taxa de evasão"
    A pesquisa bibliográfica revelou três famílias de métodos para calcular taxas de evasão: (1) por **gerações completas** de alunos (até o prazo máximo de integralização); (2) por **coorte de ingressantes** em um período específico; (3) por **acompanhamento de série histórica anual** — este último grupo foi escolhido por ser mais flexível e permitir comparação ano a ano. O autor definiu, com base nesse grupo, as métricas usadas no DW:

    - **VPA** (Veteranos para o Próximo Ano) = ingressantes do ano − evadidos do ano (ano-base); nos anos seguintes, VPA do ano anterior + ingressantes − evadidos − diplomados do ano.
    - **TMA** (Total de Matrículas no Ano) = VPA do ano anterior + ingressantes do ano.
    - **TEA** (Taxa de Evasão no Ano) = evadidos do ano ÷ TMA × 100.

Da pesquisa bibliográfica, foram identificadas **65 variáveis descritivas** de alunos associadas à evasão na literatura (33 pessoais, 32 acadêmicas); confrontando com o que o SIGAA efetivamente registra (pesquisa documental em três *schemas* do PostgreSQL: `comum`, `public` e `ensino`), apenas **23 (35,4%)** estavam disponíveis — o restante (renda familiar, motivação, infraestrutura percebida etc.) simplesmente não é capturado por um sistema transacional acadêmico.

### O modelo dimensional resultante

O projeto usou **duas tabelas fato**, com um esquema estrela de **dimensões conformadas** (Tempo e Curso compartilhadas entre as duas tabelas fato):

- **`fato_discente`** (grão: um registro por aluno) — liga-se a `dimensao_tempo`, `dimensao_pessoa`, `dimensao_curso` e `dimensao_situacao`; armazena os índices acadêmicos de desempenho do aluno (índices de conclusão, de eficiência em períodos letivos, de eficiência em carga horária, de rendimento acadêmico e de eficiência acadêmica).
- **`fato_evasao`** (grão: a taxa de evasão por curso e ano) — liga-se apenas a `dimensao_tempo` e `dimensao_curso`; armazena total de ingressantes, total de evadidos, total de diplomados, VPA, TMA e a taxa de evasão (TEA) já calculada.

As quatro dimensões: `dimensao_pessoa` (CPF, matrícula, nome, sexo, estado civil, nacionalidade, naturalidade, data de nascimento, raça, dados do ensino médio, forma e ano/período de ingresso), `dimensao_tempo` (ano e período letivo), `dimensao_curso` (curso, unidade acadêmica, turno, área CAPES, modalidade de ensino, campus, grau acadêmico) e `dimensao_situacao` (situação do aluno, tipo e data de saída).

O **ETL** foi desenvolvido sob medida em **SQL e Python** (em vez de uma ferramenta comercial de mercado), por ser suficiente para a demanda inicial e evitar custo de licenciamento — seguindo a mesma lógica de "ETL histórica" (uma carga única cobrindo todo o período disponível, de 1998 a 2019) descrita por Kimball. A extração precisou unir **17 tabelas do SIGAA** via `JOIN`s e funções de agregação (`COUNT`) para transformar registros individuais em totais anuais — contra apenas 2 tabelas fato + 4 dimensões para consultar no DW já pronto, uma simplificação drástica para o usuário final.

### Resultado e validação

O protótipo foi apresentado e validado na 27ª Reunião Ordinária do Conselho de Ensino, Pesquisa, Extensão e Administração (CEPEAd) da Unifei, em 2019, e usado para comparar a evolução das taxas de evasão e diplomação entre diferentes unidades acadêmicas ao longo de 20 anos (1998–2018) — revelando, por exemplo, que um aumento abrupto do número de vagas (efeito do REUNI) pôde ser associado a quedas posteriores na taxa de diplomação, sinal de possível retenção de alunos.

## Referências e para saber mais

### Bibliografia da disciplina (slides)

- KIMBALL, Ralph; ROSS, Margy. *[The Data Warehouse Toolkit: The Definitive Guide to Dimensional Modeling](https://www.wiley.com/en-us/The+Data+Warehouse+Toolkit%3A+The+Definitive+Guide+to+Dimensional+Modeling%2C+3rd+Edition-p-9781118530801)*. 3ª ed. Wiley, 2019. — obra de referência citada em praticamente todas as figuras da disciplina.
- KIMBALL, R. et al. *The Data Warehouse Toolkit: The Complete Guide to Dimensional Modeling*. 2ª ed. Wiley, 2002. — edição anterior, citada nas figuras clássicas (dimensão Data, tabela de fatos de vendas, minidimensões, *bus matrix* etc.).
- LAGO, Karine; ALVES, Laennder. *Dominando o Power BI*. 3ª ed. atualizada. DATAB, 2021.
- VATOVEC, Evelin. "Intelligent Value Chain Networks: Business Intelligence And Other ICT Tools And Technologies In Supply/Demand Chains". *Supply Chain Management — New Perspectives*, 2011.
- Fonte do diagrama Inmon x Kimball: [dataprix.net/pt-pt/24-data-mart](http://www.dataprix.net/pt-pt/24-data-mart)
- Diagramas de tabela de fato de vendas/estoque no varejo: J. Gamper, [admt06_dw-case-studies.pdf](http://www.inf.unibz.it/dis/teaching/ADMT/ln/admt06_dw-case-studies.pdf) (Unibz).
- Mais sobre os tipos de SCD: [Kimball Group, Design Tip #152 — Slowly Changing Dimension Types 0, 4, 5, 6, 7](https://www.kimballgroup.com/2013/02/design-tip-152-slowly-changing-dimension-types-0-4-5-6-7/).
- Esquema de produtos heterogêneos: [kimballgroup.forumotion.net/t284-heterogeneous-product-schema](https://kimballgroup.forumotion.net/t284-heterogeneous-product-schema).
- Exemplo de *junk dimension*: [support.jetglobal.com — Junk Dimension Automation with the Jet Data Manager](https://support.jetglobal.com/hc/en-us/articles/218952368-Junk-Dimension-Automation-with-the-Jet-Data-Manager).
- Exemplo de modelagem dimensional de vendas em loja: baseado nas aulas de DW do Prof. **Asterio K. Tanaka** (UNIRIO).

### Bibliografia do estudo de caso (dissertação sobre evasão, UNIFEI)

A dissertação de Felipe R. de M. Mendes (2020) traz uma revisão bibliográfica extensa, tanto sobre Data Warehousing quanto sobre o fenômeno da evasão no ensino superior brasileiro. As referências técnicas de DW mais relevantes para esta disciplina:

- INMON, W. H. *Building the Data Warehouse*. 4ª ed. Wiley, 2005.
- KIMBALL, R. et al. *The Data Warehouse Lifecycle Toolkit: Expert Methods for Designing, Developing, and Deploying Data Warehouses*. 2ª ed. Wiley, 2008.
- LAUDON, K.; LAUDON, J. *Sistemas de Informação Gerenciais*. São Paulo: Pearson Prentice Hall, 2014.
- SINGH, Harry. *Data Warehouse: Conceitos, Tecnologias, Implementação e Gerenciamento*. São Paulo: Makron Books, 2001.
- BARBIERI, C. *BI2 — Business Intelligence: Modelagem & Qualidade*. Elsevier, 2011.
- HEUSER, C. A. *Projeto de Banco de Dados*. Bookman, 2009.
- BRESLIN, M. "Data Warehousing Battle of the Giants: Comparing the Basics of the Kimball and Inmon Models". *Business Intelligence Journal*, 2004.
- ALJAWARNEH, I. M. "Design of a data warehouse model for decision support at higher education: A case study". *Information Development*, v. 32, n. 5, 2016.
- ZEA, O. M.; SAMPEDRO, A.; MORA, S. L. "Datawarehouse design for educational data mining". *15th International Conference on Information Technology Based Higher Education and Training (ITHET)*, 2016.
- ZEA, O. M.; GUALTOR, J. P.; MORA, S. L. "A Holistic View of Data Warehousing in Education". *IEEE Access*, v. 6, 2018.
- CHECKLAND, P.; POULTER, J. "Soft Systems Methodology". In: *Systems Approaches to Managing Change: A Practical Guide*. Springer, 2010. — base metodológica (SSM) usada no estudo de caso.

!!! info "Lista completa de referências do estudo de caso"
    A dissertação traz, em seus apêndices, uma tabela com os **principais artigos de periódicos Qualis A1** usados na revisão sobre evasão no ensino superior (22 artigos, publicados em periódicos como *Avaliação (Campinas)*, *Cadernos de Pesquisa*, *Ensaio — Avaliação e Políticas Públicas em Educação* e *Educação em Revista*), além de um dicionário de dados completo e os scripts SQL de criação e extração do DW (ETL). Por ser um material de apoio a projeto (não uma aula da disciplina), essa lista extensa — majoritariamente sobre evasão educacional e fora do escopo técnico de DW/OLAP — não foi reproduzida aqui na íntegra; vale consultar o documento original caso o projeto da disciplina envolva um tema de negócio semelhante (acompanhamento de indicadores institucionais ao longo do tempo).
