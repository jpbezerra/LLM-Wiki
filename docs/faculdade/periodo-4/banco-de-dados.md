# BANCO DE DADOS

## Conceitos Básicos

Antes de falar de bancos de dados propriamente, vale separar quatro ideias que costumam ser confundidas:

| Conceito | Definição |
| --- | --- |
| **Dado** | Um elemento bruto, sem contexto. |
| **Metadado** | Dados que descrevem outros dados, dando-lhes significado (ex.: o tipo e o tamanho de uma coluna). |
| **Informação** | Um dado com significado, interpretado de forma útil. |
| **Conhecimento** | O uso da informação para tomar decisões. |

Um **banco de dados** é uma coleção organizada de informações estruturadas sobre um domínio específico. Em uma arquitetura MVC (Model-View-Controller), os dados são acessados na camada mais baixa, o **Model** — a camada que contém toda a lógica de CRUD e fornece os dados para as demais camadas.

Já o **Sistema Gerenciador de Banco de Dados (SGBD)** é o software que gerencia e controla o banco de dados, permitindo aos usuários realizar CRUD e outras operações — é o "motor" que lê, organiza e escreve os dados (MySQL, PostgreSQL, Oracle, etc.).

### Evolução dos SGBDs

A história dos SGBDs é, em boa parte, a história de como foram sendo resolvidos os problemas de confiabilidade e redundância que surgiam a cada geração anterior.

**Sistemas de arquivos (década de 1960).** Antes do SGBD, os usuários utilizavam diretamente os sistemas de arquivos do sistema operacional. Cada aplicação tinha o seu próprio arquivo, e todo o controle de qualidade dos dados dependia inteiramente dos programadores. Isso trazia vários problemas:

- **Redundância de dados e de código**: como cada aplicação tinha seu próprio arquivo, o mesmo dado podia estar repetido em vários lugares — gerando inconsistência quando atualizado em apenas um deles, sem saber qual versão é a correta.

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image.png)

- **Dificuldade de acesso**: todo acesso dependia do programador estar disponível para escrever o código necessário.
- **Formatos heterogêneos**: dados dispersos em arquivos isolados podiam ter formatos e valores diferentes, dificultando a escrita de programas que precisassem acessar vários deles.
- **Falta de atomicidade**: se uma operação dependia de várias transações e uma delas falhasse, o resultado podia ficar inconsistente — garantir que os dados voltassem ao último estado consistente (atomicidade) não era fácil de implementar manualmente.
- **Concorrência**: acesso simultâneo ao mesmo dado podia gerar inconsistências.

Foi exatamente para resolver esses problemas que o SGBD foi criado.

**1ª geração (década de 1970).**

| Modelo | Estrutura | Características |
| --- | --- | --- |
| **SGBD Hierárquico** | Árvore, baseada em ponteiros (cada pai aponta para seus filhos) | Primeiro SGBD com controle centralizado; só permite relações 1:N |
| **SGBD em Rede** | Grafo (ainda baseado em ponteiros, mas sem redundância) | Reconhece a natureza não hierárquica dos dados e permite relações M:N; porém é complexa de entender e manter, com baixa independência entre dados e programas, e manipulação feita em linguagem de baixo nível |

**2ª geração (década de 1980) — SGBD Relacional.** Não é baseado em ponteiros, e tem fundamento matemático sólido (relações, funções, conjuntos, álgebra relacional). Os dados são representados por **tabelas (relações)**, organizadas em linhas e colunas, com **chaves primárias** e **estrangeiras**; a manipulação é feita por SQL. É hoje o modelo mais utilizado quando é preciso garantir integridade dos dados (Oracle, PostgreSQL, etc.).

| Tipo de chave | Definição |
| --- | --- |
| **Chave primária (PK)** | Identificador único de cada linha de uma tabela; garante que duas linhas nunca tenham o mesmo valor; não pode ser nula. |
| **Chave estrangeira (FK)** | Campo que referencia a PK de outra tabela, permitindo criar relações 1:N e M:N — se os valores de FK puderem se repetir, é 1:N; se puderem ser todos diferentes, a relação tende a M:N. |

**3ª geração (década de 1990).**

- **SGBD Orientado a Objetos**: o modelo mais natural para expressar a realidade ("tudo é objeto"), surgido sob a influência da POO da época. Não tem linguagem padronizada nem base teórica sólida, e o paradigma não foi bem aceito pelo mercado.

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%201.png)

- **SGBD Relacional-Objeto**: combina o melhor dos dois mundos, aplicando conceitos de OO sobre estruturas relacionais — suporte a tipos de dados abstratos (objetos complexos), baseado em SQL padrão mas com extensões proprietárias de POO (Oracle, PostgreSQL, etc.).

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%202.png)

**4ª geração (década de 2000) — SGBD Não-Relacional (NoSQL).** Voltado para grandes volumes de dados, priorizando alto desempenho, disponibilidade e consistência eventual, em vez de organizar dados estritamente em linhas/colunas com PK/FK. O esquema é semi-estruturado (admite replicação e ausência de campos, como em JSON), e a escalabilidade é predominantemente **horizontal** (múltiplos servidores) — ao contrário dos SGBDs relacionais, tipicamente escaláveis verticalmente (MongoDB, Redis, Cassandra).

---

## Modelo Entidade Relacionamento (MER)

O **MER** é uma linguagem diagramática usada para modelar bancos de dados e especificar esquemas conceituais.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%203.png)

### Entidades, relacionamentos e atributos

Os componentes básicos do diagrama são:

- **Retângulos → Entidades**: abstrações de um conceito concreto (cliente, livro) ou abstrato (conta, empréstimo). Uma ocorrência de uma entidade é chamada de **instância**.
- **Losangos → Relacionamentos**: abstrações de uma associação entre instâncias de uma ou mais entidades. Em um relacionamento, todas as instâncias envolvidas devem existir; a cada ocorrência chamamos de **instância do relacionamento** (cada uma carrega uma informação diferente).
- **Elipses → Atributos**: propriedades descritivas de uma entidade ou relacionamento.
- **Linhas**: ligam atributos a entidades/relacionamentos, e entidades a relacionamentos.

#### Relacionamentos: grau, papel, cardinalidade e participação

O **grau** de um relacionamento é a quantidade de entidades envolvidas: **unário** (auto-relacionamento), **binário** (duas entidades) ou **N-ário** (N entidades). O **papel** é a função que uma dada entidade desempenha no relacionamento:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%204.png)

A **cardinalidade** (ou multiplicidade, ou cardinalidade máxima) expressa o número máximo de vezes que uma instância de uma entidade pode, no pior caso, participar do relacionamento. Pode ser representada por qualquer inteiro positivo, mas por convenção usa-se $1$ (um) e $N$ (muitos) — resultando em relacionamentos $1{:}1$, $1{:}N$ ou $M{:}N$.

A **participação** (ou obrigatoriedade, ou cardinalidade mínima) especifica se uma instância, para ser cadastrada, *precisa* estar relacionada com alguma instância de outra entidade do relacionamento. Quando a condição é exigida, a participação é **total** (relacionamento obrigatório); quando não, é **parcial** (relacionamento opcional). Por convenção, usam-se os valores $0$ (participação parcial) e $1$ (participação total).

!!! note "Look-here vs. look-across"
    A cardinalidade e a participação podem ser especificadas do lado da entidade de origem (**look-here**) ou de destino (**look-across**):

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%205.png)

    - **Look-here**: a FK está na entidade de *origem* — ela armazena a referência para a de destino, e os dados relacionados ficam do lado de origem. Está relacionada à **participação**: "esta entidade *precisa* participar do relacionamento?"
    - **Look-across**: é preciso olhar para a entidade de *destino* para encontrar os dados relacionados — a FK está do lado de destino. Está relacionada à **cardinalidade**: "quantos da entidade destino se relacionam com a de origem?"

    Na notação de Elmasri & Navathe, a participação é representada por linhas simples (parcial) ou duplas (total); a notação $(min, max)$ é usada quando os valores mínimo e máximo diferem dos padrões ($0$/$1$ e $1$/$N$).

!!! example "Exemplos de cardinalidade/participação"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%206.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%207.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%208.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%209.png)

Duas entidades podem ter **mais de um relacionamento** entre elas:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2010.png)

#### Tipos de atributos

| Tipo | Definição | Exemplo |
| --- | --- | --- |
| Simples | Indivisível | CPF, saldo |
| Composto | Formado por sub-atributos | Endereço (rua, bairro, complemento) |
| Monovalorado | Admite um único valor por instância | CPF, saldo |
| Multivalorado | Admite vários valores por instância | E-mail, telefone |
| Derivado | Calculado a partir de outros atributos | Média de notas, saldo médio |
| Identificador | Cada valor é único | CPF, código de matrícula |
| Discriminador | Identificador *parcial* — sozinho não identifica, mas combinado com um identificador de outra entidade sim (geralmente vindo de uma entidade forte relacionada) | Data de pagamento |

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2011.png)

Toda entidade deve ter atributos, mas nem todo relacionamento precisa ter. A própria **cardinalidade** do relacionamento influencia onde inserir atributos: é comum colocar atributos em relacionamentos $M{:}N$, mas pouco comum em relacionamentos $1{:}1$, $1{:}N$ ou $N{:}1$ — nestes últimos, é melhor colocar o atributo na entidade do lado $N$ em vez do relacionamento.

!!! tip "Entidade ou relacionamento?"
    Se existe um identificador (ID) próprio, trata-se de uma entidade; caso contrário, pode ser um relacionamento. Um relacionamento com muitos atributos tende, na prática, a "virar" uma entidade.

!!! example "Exemplos"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2012.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2013.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2014.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2015.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2016.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2017.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2018.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2019.png)

### Relacionamento unário

Envolve apenas uma entidade, que assume dois papéis diferentes na mesma associação (por exemplo, "funcionário supervisiona funcionário").

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2020.png)

### Relacionamento identificador

Permite usar o atributo identificador de uma **entidade forte** para identificar outra **entidade fraca** — útil quando essa segunda entidade não tem, por si só, atributos capazes de identificá-la unicamente.

Uma entidade que tem um atributo **discriminador** é, por definição, uma **entidade fraca**: ela depende do identificador de uma entidade forte e, portanto, não possui seu próprio atributo identificador. Toda instância de entidade fraca deve estar relacionada a **no máximo uma** instância de entidade forte. Decorre daí que:

- relações $1{:}1$ não devem ter atributo discriminador;
- relações $1{:}N$ devem ter o discriminador na entidade fraca;
- a cardinalidade do lado da entidade forte é sempre $1$;
- a participação da entidade fraca é sempre obrigatória (linha dupla) — ou seja, a entidade fraca é **existencialmente dependente** da entidade forte.

!!! warning "Cuidado ao usar"
    Não é uma boa prática usar o relacionamento identificador apenas para *impor* participação obrigatória — é melhor usar participação obrigatória sem relacionamento identificador nesses casos, pois o identificador aumenta o acoplamento entre entidades e dificulta a manutenção/legibilidade.

Na notação, o relacionamento identificador fica com losango duplo, a entidade fraca com retângulo duplo, e o atributo identificador composto (herdado) fica sublinhado:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2021.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2022.png)

    Aqui, o atributo identificador das entidades fracas é a concatenação encadeada de atributos da entidade forte: identificador de Agência $= (numB, numA)$ e de Conta $= (numB, numA, numC)$.

### Relacionamento N-ário

Um relacionamento é genuinamente **N-ário** quando toda vez que ele ocorre envolve, de fato, as mesmas $N$ entidades simultaneamente — e não pode ser decomposto em relacionamentos binários independentes.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2023.png)

**Como descobrir a cardinalidade de uma entidade em um relacionamento N-ário.** É preciso considerar sempre o pior caso, no formato: "1 instância de X e 1 instância de Y podem se relacionar com, no máximo, quantas instâncias de Z (1 ou N)?"

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2024.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2025.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2026.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2027.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2028.png)

**Participação em relacionamentos N-ários:**

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2029.png)

No primeiro esquema, nenhuma das três entidades é obrigada a participar do relacionamento "contrata" — o cadastro de qualquer uma delas independe das outras. No segundo, o cadastro de produto só acontece se ele já estiver relacionado a um cliente e uma conta (produto não existe sem a relação "contrata", pois depende de cliente e conta). Em ambos os esquemas, sempre que a relação ocorre, ela envolve exatamente um cliente, um produto e uma conta.

#### Relacionamento N-ário vs. binário

!!! warning "Atenção: nem todo relacionamento com 3+ entidades é ternário"
    Se todos os clientes de uma conta sempre têm os mesmos produtos, então na verdade existe apenas um relacionamento **binário** entre conta e produto:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2030.png)

    Apesar de cliente não estar diretamente relacionado a produto, a partir de conta é possível descobrir todos os produtos de um cliente por transitividade.

    Um sinal de alerta é: se, em um relacionamento aparentemente ternário, **uma entidade tem cardinalidade $1$**, provavelmente existe uma relação binária escondida por trás, e não uma relação ternária genuína. No caso a seguir, teríamos duas relações binárias:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2031.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2032.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2033.png)

    Nesse exemplo, apesar de 1 cliente com 1 conta corrente só poder fazer parte de 1 agência, 1 cliente pode fazer parte de N agências — gerando uma contradição. Já "1 conta corrente pode fazer parte de apenas 1 agência" está logicamente correto. O problema é que a relação, como modelada, permite que uma mesma conta esteja atrelada a mais de uma agência:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2034.png)

    A solução correta separa as relações:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2035.png)

    Em geral: se, a partir de uma instância de entidade A, é possível **determinar** uma instância de entidade B, então A e B formam um relacionamento binário, não N-ário.

Por outro lado, o inverso também é verdade: **3 relacionamentos binários não substituem 1 relacionamento ternário genuíno** — quando as três entidades realmente só fazem sentido combinadas simultaneamente, decompor em pares perde informação.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2036.png)

### Entidade associativa

Quando um relacionamento pode ocorrer **sem** a presença de uma terceira entidade (isto é, quando as entidades podem se relacionar entre si de forma independente, mas também é útil capturar uma relação conjunta), usa-se uma **entidade associativa** em vez de um relacionamento N-ário.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2037.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2038.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2039.png)

**Entidade associativa vs. relacionamento N-ário** — a diferença central:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2040.png)

### Herança

A **herança** cria uma hierarquia de entidades, em que sub-entidades herdam todos os atributos e relacionamentos das super-entidades. É recomendável usá-la apenas quando as sub-entidades têm atributos ou relacionamentos **específicos** — caso contrário, um atributo simples resolve melhor.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2041.png)

A herança é classificada em dois eixos independentes:

| Eixo | Valores | Significado |
| --- | --- | --- |
| Disjunção | **Disjunta** (`d`) | Cada instância da super entidade se especializa em **exatamente uma** sub-entidade. |
| | **Sobreposta** (`o`) | Pelo menos uma instância se especializa em **mais de uma** sub-entidade simultaneamente. |
| Totalidade | **Total** (linha dupla) | Toda instância da super entidade é especializada em pelo menos uma sub-entidade. |
| | **Parcial** (linha simples) | Pelo menos uma instância não é especializada em nenhuma sub-entidade. |

!!! example "As quatro combinações"
    - Herança **PD** (Parcial/Disjunta): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2042.png)
    - Herança **TD** (Total/Disjunta): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2043.png)
    - Herança **PO** (Parcial/Sobreposta): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2044.png)
    - Herança **TO** (Total/Sobreposta): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2045.png)

Se existe apenas **uma** sub-entidade, a herança é dita **direta**, e não pode ser classificada como disjunta/sobreposta nem total/parcial (essas classificações só fazem sentido com múltiplas sub-entidades concorrendo entre si):

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2046.png)

Se as sub-entidades não têm atributos ou relacionamentos específicos, é preferível usar um atributo simples do tipo "tipo"/"categoria" no lugar de modelar herança:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2047.png)

### Particularidades e limitações do MER

O MER tem **poder de expressão limitado** — valores válidos e pré/pós-condições de negócio precisam ser documentados separadamente, fora do diagrama. Além disso, esquemas ER *diferentes* podem acabar sendo **equivalentes** na prática:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2048.png)

### Dúvidas frequentes de modelagem

| Dúvida | Regra de decisão | Ilustração |
| --- | --- | --- |
| Atributo ou entidade? | Meramente descritivo → atributo. Tem identificador explícito → entidade. | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2049.png) |
| Atributo composto/multivalorado ou entidade? | Exclusivo de uma entidade → atributo. Pode ser compartilhado entre várias entidades → entidade. | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2050.png) |
| Atributo ou herança? | Pode haver inconsistência entre os conceitos → herança. Caso contrário → atributo. | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2051.png) |
| Relacionamento ou entidade? | Tem identificador explícito → entidade. Caso contrário → pode ser relacionamento. | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2052.png) |
| Relacionamento N-ário ou entidade associativa? | Sempre envolve todas as entidades simultaneamente → relacionamento N-ário. Caso contrário → entidade associativa. | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2053.png) |

### Requisitos para um bom MER

Um bom esquema MER precisa satisfazer vários requisitos simultaneamente:

**1. Ser sintaticamente correto** — respeitar as regras de construção do diagrama.

!!! example "Erros sintáticos comuns"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2054.png)

**2. Ser semanticamente correto** — o esquema não pode ter atributos, cardinalidades, participações ou graus mal especificados, nem capturar mais de uma realidade ao mesmo tempo:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2055.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2056.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2057.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2058.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2059.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2060.png)

**3. Evitar (ou controlar) construções redundantes** — redundância pode melhorar desempenho em certos cenários, mas também pode gerar dados inconsistentes se não for cuidadosamente controlada:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2061.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2062.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2063.png)

**4. Capturar o aspecto temporal**, quando relevante — ou seja, guardar o histórico de um atributo em vez de apenas seu valor atual:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2064.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2065.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2066.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2067.png)

**5. Ser completo** — é muito mais fácil corrigir um erro no projeto conceitual do que em qualquer fase posterior do projeto do banco de dados. O projeto conceitual pode ser construído a partir de:

- **Informações já existentes**, usando:
    - **Engenharia reversa**: feita automaticamente por uma ferramenta CASE a partir de um banco já existente;
    - **Estratégia Bottom-Up**: 1º atributos → 2º entidades → 3º relacionamentos → 4º herança.
- **Conhecimento de especialistas**, usando:
    - **Estratégia Top-Down**: 1º entidades → 2º relacionamentos → 3º heranças → 4º atributos;
    - **Estratégia Inside-Out**: igual à Top-Down, mas começando pelas entidades mais importantes do domínio.

---

## Modelo Relacional

O **modelo relacional** é um modelo **lógico** — menos abstrato que o conceitual (MER), mas que ainda não considera aspectos físicos de armazenamento, acesso ou desempenho. Tem uma base formal sólida (teoria dos conjuntos) e é construído sobre conceitos simples: relações, atributos, tuplas e domínios. É baseado em tabelas que **não podem ter subtabelas**, e é a base direta sobre a qual o SQL foi definido. Vale notar que diversos conceitos do modelo conceitual não são implementados de forma tão direta no modelo relacional — é justamente esse "gap" que o processo de **mapeamento** (visto mais adiante) precisa resolver.

### Definições fundamentais

- **Domínio**: conjunto de valores atômicos possíveis para um atributo.
- **Relação**: dados os conjuntos $D_1, \ldots, D_n$ (domínios não necessariamente distintos), $R$ é uma relação sobre esses $n$ conjuntos se $R$ é um conjunto de tuplas $\langle v_1, \ldots, v_n \rangle$ onde $v_1 \in D_1, \ldots, v_n \in D_n$ — ou seja, $R$ é um subconjunto do produto cartesiano $D_1 \times \cdots \times D_n$.

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2068.png)

!!! note "Relação vs. tabela: terminologia"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2069.png)

**Propriedades de uma relação:**

- toda relação tem um número **fixo** de atributos distintos;
- o valor `NULL` é usado quando um atributo não tem valor, ou este é desconhecido;
- a ordem dos atributos e das tuplas é **irrelevante** — não há ordenação implícita entre tuplas, e os valores se associam aos atributos independentemente de qualquer ordem.

### Chaves

O conceito de **chave** serve para identificar e referenciar tuplas de forma inequívoca.

| Tipo de chave | Definição |
| --- | --- |
| **Chave candidata** | Um atributo (chave simples) ou concatenação de atributos (chave composta) cujos valores distinguem uma tupla de todas as demais da relação — uma possível PK, que deve ter valores distintos e obrigatórios. |
| **Chave primária (PK)** | A chave candidata *escolhida* para identificar as tuplas; frequentemente usada para seleção; nunca admite `NULL`. |
| **Chave estrangeira (FK)** | Atributo (ou concatenação) que referencia a PK de *outra* tabela, usada para relacionar tuplas entre relações; admite `NULL` quando a participação é opcional (não precisa ser única nem obrigatória). |
| **Chave alternativa (AK)** | A chave candidata que **não** foi escolhida como PK; não participa de relacionamentos via FK. |

Uma chave candidata deve ser **mínima**: se é simples, já é mínima por definição; se é composta, é preciso verificar que nenhum subconjunto próprio dos atributos já seria suficiente para identificar a tupla (senão haveria redundância na chave).

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2070.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2071.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2072.png)

!!! example "Auto-relacionamento"
    Um auto-relacionamento é uma relação entre a *mesma* entidade/tabela, diferenciando-se apenas pelos papéis desempenhados (ex.: um funcionário que supervisiona outro funcionário):

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2073.png)

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2074.png)

### Restrições de integridade

As **restrições de integridade** são regras sobre os valores armazenados nas relações, com o objetivo de garantir sua consistência:

| Restrição | Regra |
| --- | --- |
| **De domínio** | Todo valor de um atributo deve ser atômico (simples e monovalorado) e pertencer ao domínio definido para aquele atributo. |
| **De chave** | Todo valor de chave primária deve ser mínimo e único na relação. |
| **De integridade da entidade** | Chaves primárias nunca podem ter valor `NULL`. |
| **De integridade referencial** | Todo valor de uma chave estrangeira deve aparecer na chave primária da tabela referenciada (ou ser `NULL`, se a FK for opcional). |

!!! example "Integridade referencial na prática"
    - Inserções e atualizações: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2075.png)
    - Exclusões: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2076.png)

Além das restrições de integridade (estruturais, aplicadas automaticamente pelo SGBD), existem as **restrições semânticas**, que impõem regras de negócio e precisam ser implementadas explicitamente pelos programadores, já que não são garantidas automaticamente pelo modelo relacional — por exemplo, "um empregado não pode ter salário maior que seu superior imediato".

### Notação simplificada

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2077.png)

### Álgebra relacional

A **álgebra relacional** foi desenvolvida para descrever operações sobre um banco de dados relacional, e serve de base conceitual para entender o próprio SQL (uma linguagem de consulta estruturada construída sobre essas operações).

**Compatibilidade de domínio.** Duas relações $A(a_1, \ldots, a_n)$ e $B(b_1, \ldots, b_n)$ são **compatíveis em domínio** se ambas têm o mesmo grau $n$ e $\text{Dom}(a_i) = \text{Dom}(b_i)$ para todo $1 \leq i \leq n$ — pré-requisito para as operações de conjunto a seguir.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2078.png)

#### Operações sobre conjuntos

| Operação | Notação | Definição |
| --- | --- | --- |
| União | $A \cup B$ | Une as tuplas de $A$ e $B$. |
| Interseção | $A \cap B$ | Retorna as tuplas comuns a $A$ e $B$. |
| Diferença | $A - B$ | Retorna as tuplas de $A$ que não estão em $B$. |
| Produto cartesiano | $A \times B$ | Combina cada tupla de $A$ com cada tupla de $B$. |
| União exclusiva | $A \mathbin{\overline{\cup}} B$ | $(A \cup B) - (A \cap B)$ — tuplas que estão em $A$ ou $B$, mas não em ambas. |

!!! example "Exemplos"
    - União: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2079.png)
    - Interseção: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2080.png)
    - Diferença: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2081.png)
    - Produto cartesiano: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2082.png)
    - União exclusiva: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2083.png)

#### Operações relacionais unárias

Produzem, a partir de uma única relação de origem, uma nova relação que é um subconjunto **horizontal** (muda linhas) ou **vertical** (muda colunas) dela.

- **Seleção** ($\sigma$) — subconjunto horizontal: filtra linhas segundo uma condição. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2084.png) *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2085.png)
- **Projeção** ($\pi$) — subconjunto vertical: seleciona apenas algumas colunas. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2086.png) *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2087.png)
- **Seleção + Projeção** combinadas: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2088.png)

#### Operações relacionais binárias

Produzem uma nova relação que é, essencialmente, um subconjunto (via seleção) do produto cartesiano das relações envolvidas. Em geral, após o produto cartesiano, é necessário comparar atributos compatíveis em domínio para filtrar as tuplas do resultado final.

- **Junção** ($\bowtie$): retorna apenas as tuplas do produto cartesiano que satisfazem uma condição dada. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2089.png) *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2090.png)
- **Divisão** ($\div$): produz uma relação $R(X)$ com as tuplas de $R_1(A)$ que se combinam com **todas** as tuplas de $R_2(B)$. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2091.png) *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2092.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2093.png)

### Mapeamento EER → Relacional

Um mesmo esquema EER pode gerar **várias** possibilidades de esquema relacional — existem diferentes maneiras válidas de mapear relacionamentos e heranças. Ao escolher entre elas, três prioridades guiam a decisão (nessa ordem):

1. **Evitar junções** → consultas mais rápidas;
2. **Diminuir o número de chaves** → índices menores e mais rápidos;
3. **Evitar campos opcionais** → menos testes de qualidade de dados necessários.

Na nomeação de relações e atributos, usa-se nomes curtos, sem espaços ou caracteres especiais, seguindo um padrão consistente.

#### Passo 1 — Mapear entidades regulares e seus atributos

Cada entidade regular é mapeada para uma relação, cuja PK é o atributo identificador da entidade. Atributos comuns, compostos ou derivados são mapeados como atributos simples da relação. Já um atributo **multivalorado** tem duas opções:

- $N$ atributos separados (desde que $N$ seja pequeno), ou
- uma **nova relação**, cuja PK é o próprio atributo multivalorado combinado com a PK migrada (como FK) da relação de origem.

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2094.png)

#### Passo 2 — Mapear entidades fracas e seus atributos

Cada entidade fraca é mapeada para uma relação onde a PK da entidade forte migra como FK; a PK da nova relação é formada por essa FK, combinada com o discriminador (quando existir). Os demais atributos seguem as mesmas regras das entidades regulares.

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2095.png)

#### Passo 3 — Mapear super/subentidades (herança)

Existem quatro alternativas, com trade-offs diferentes:

| Alternativa | Quando usar bem | Pontos fortes | Pontos fracos |
| --- | --- | --- | --- |
| **Uma relação por entidade** (super e cada sub) | Qualquer tipo de herança | Funciona universalmente; reduz atributos opcionais e testes de qualidade | Exige junções para reconstruir o objeto completo |
| **Uma relação por subentidade** (herança total apenas) | Herança total, disjunta ou sobreposta | Reduz atributos opcionais, testes e junções | Gera redundância de dados em heranças sobrepostas |
| **Uma única relação para herança disjunta/direta** | Herança definida por um predicado simples | Reduz junções | Só funciona com predicado claro; exige atributos opcionais e testes de povoamento |
| **Uma única relação para herança sobreposta** | Poucas sub-entidades, poucos atributos específicos | Reduz junções e redundância | Exige atributos opcionais e testes; desaconselhada se as sub-entidades têm muitos atributos/relacionamentos próprios |

Nas duas últimas alternativas, superentidade e subentidades colapsam em uma única relação, cuja PK é o identificador da superentidade; na disjunta, o predicado/condição da herança se torna um atributo cujo domínio cobre as subentidades; na sobreposta, cria-se um atributo booleano por subentidade. Em todos os casos, atributos comuns, compostos, derivados ou multivalorados seguem as mesmas regras já vistas.

!!! example "Exemplos das quatro alternativas"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2096.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2097.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2098.png)
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2099.png)

#### Passo 4 — Mapear entidades associativas

Cada entidade associativa é mapeada para uma relação; as PKs das relações envolvidas migram como FKs obrigatórias; atributos do relacionamento (se existirem) ficam na relação mapeada; e a PK da nova relação depende do grau e da cardinalidade do relacionamento original (mesmas regras usadas para relacionamentos comuns).

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20100.png)

#### Passo 5 — Mapear relacionamentos e seus atributos

Existem três estratégias gerais:

**A. Fusão de relações** — funde duas relações relacionadas $1{:}1$ em uma única. Reduz junções, mas exige atributos opcionais e testes de qualidade (desaconselhada quando as entidades têm muitos atributos/relacionamentos próprios).

- Melhor caso ($1{:}1$ Total/Total): funde as duas relações; a PK fundida é uma das PKs originais (preferencialmente a mais consultada), e a outra PK vira uma chave alternativa — notada com `[]` (chave alternativa) e `!` (obrigatória). ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20101.png)
- Caso alternativo ($1{:}1$ Total/Parcial): a PK fundida deve ser a da relação com participação **parcial**; a outra se torna AK (avaliar custo x benefício caso a caso). ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20102.png)

**B. Adição de chave estrangeira** — reduz atributos opcionais e testes, mas exige junção.

- Melhor caso ($1{:}N$): a PK do lado $1$ migra como FK para a relação do lado $N$ (obrigatória, com `!`, se o lado $N$ for total); atributos do relacionamento migram junto. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20103.png)
- Caso alternativo ($1{:}1$): dependendo das participações — Parcial/Parcial: FK única e opcional (`[]`) em qualquer um dos lados; Total/Parcial: FK única e obrigatória (`[]` + `!`) do lado parcial; Total/Total: FK única e obrigatória em qualquer um dos lados. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20104.png)

**C. Criação de relação** — reduz atributos opcionais e testes, mas também exige junção.

- Melhor caso ($M{:}N$): cada relacionamento $M{:}N$ gera uma nova relação; as PKs das duas relações envolvidas migram como FK, e a composição delas forma a PK da nova relação; atributos do relacionamento ficam nela. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20105.png)
- Caso alternativo $1{:}N$ (evitar): o relacionamento gera uma relação onde a FK do lado $N$ se torna a própria PK, e a outra FK se torna obrigatória.
- Caso alternativo $1{:}1$ (evitar): a PK é escolhida a partir das participações — Parcial/Parcial: qualquer FK; Total/Parcial: a FK do lado parcial; Total/Total: qualquer FK — e a outra FK se torna AK obrigatória (`[]` + `!`).
- Relacionamentos N-ários: migram todas as PKs como FK obrigatórias; a PK da nova relação depende da cardinalidade — $N{:}N{:}N$ → PK formada por todas as FK; $1{:}N{:}N$ → PK dupla com as FK do lado $N$; $1{:}1{:}N$ e $1{:}1{:}1$ → casos raros e complexos, tratados individualmente. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20106.png)

#### Exemplo completo de mapeamento

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20107.png)

- Mapeando entidades: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20108.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20109.png)
- Mapeando herança: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20110.png)
- Mapeando entidade associativa: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20111.png)
- Mapeando relacionamento $1{:}1$: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20112.png)
- Mapeando relacionamento $1{:}N$: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20113.png)
- Mapeando relacionamento $M{:}N$: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20114.png)
- Mapeando relacionamento N-ário: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20115.png)

### Normalização

A **normalização** é um processo matemático fundamentado na teoria dos conjuntos, que aplica uma série de regras sobre as tabelas de um banco de dados para verificar (e corrigir) seu projeto. Os objetivos principais são:

- decompor uma relação até que fique com pouca ou nenhuma redundância de dados;
- impedir anomalias de inserção, atualização e exclusão;
- representar eficientemente os dados do mundo real, tornando o modelo mais estável e fácil de manter;
- validar um modelo relacional já gerado por outras transformações, ou servir de método para gerar um modelo a partir de documentos da organização.

!!! warning "Nem sempre é ideal na prática"
    Do ponto de vista de desempenho, a normalização completa nem sempre é desejável — em cenários de leitura intensiva, por exemplo, alguma desnormalização controlada pode ser mais eficiente. Na prática, costuma-se normalizar até a **3FN** ou a **FNBC**:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20116.png)

#### Dependências funcionais

| Conceito | Definição |
| --- | --- |
| **Dependência funcional (DF)** | Quando um conjunto de atributos $A_1$ identifica um conjunto $A_2$, dizemos que há uma DF entre eles: $A_1 \to A_2$ ("$A_1$ determina $A_2$", ou "$A_2$ depende de $A_1$"). |
| **DF Parcial (DFP)** | Ocorre quando um atributo depende apenas de **parte** de uma chave composta (não da chave completa). |
| **DF Total (DFT)** | Ocorre quando um atributo depende de **toda** a chave composta. |
| **DF Transitiva** | Dada uma relação, existe DF transitiva quando $A_3$ depende de $A_2$ (que não é PK), e $A_2$ depende funcionalmente da PK $A_1$ — ou seja, se $A_1 \to A_2$ e $A_2 \to A_3$, então $A_3$ depende transitivamente de $A_1$, *através de* $A_2$. |

!!! example
    - DF: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20117.png)
    - DFP: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20118.png)
    - DF Transitiva: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20119.png)

#### Formas normais

**1ª Forma Normal (1FN).** Uma relação está na 1FN quando os domínios de **todos** os seus atributos são atômicos — ou seja, a relação não pode ter atributos compostos ou multivalorados.

*Transformação*: decompor o atributo em atributos simples, colocando-os na mesma relação ou em uma nova:

- Atributo **composto** monovalorado → colocar na mesma relação: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20120.png)
- Atributo **composto** multivalorado → colocar em nova relação: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20121.png)
- Atributo **multivalorado** com quantidade pequena e conhecida a priori → colocar na mesma relação: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20122.png)
- Atributo **multivalorado** com quantidade desconhecida ou grande → colocar em nova relação: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20123.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20124.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20125.png)

**2ª Forma Normal (2FN).** Uma relação está na 2FN quando está na 1FN, a PK é composta, e **todas** as colunas fora da PK dependem de **toda** a PK (isto é, não existe DFP).

*Transformação*: retirar os atributos com DFP da relação original, criando uma (ou mais) nova relação, composta pela parte da PK responsável pela dependência mais seus atributos dependentes — essa parte da PK se torna a nova PK da tabela criada.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20126.png)

!!! example "DFP"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20127.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20128.png)

**3ª Forma Normal (3FN).** Uma relação está na 3FN quando está na 2FN e todos os atributos fora da PK dependem **exclusivamente** dela — ou seja, não há DF transitiva. Na prática, normalizar até a 3FN costuma ser suficiente (embora a literatura defina formas normais ainda mais rigorosas).

*Transformação*: retirar os atributos com DF transitiva, criando uma (ou mais) nova relação formada pelo atributo determinante (como nova PK) mais suas colunas dependentes — verificando a 2FN em cada tabela nova. Além de eliminar DF transitiva, relações em 3FN não devem conter atributos com valores calculados/derivados.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20129.png)

!!! example "DF Transitiva"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20130.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20131.png)

**Forma Normal de Boyce-Codd (FNBC).** Um refinamento da 3FN, usado em casos particulares: uma relação está na FNBC quando **todo** determinante da relação é uma chave candidata (ou alternativa).

*Transformação*: decompor a relação original em duas ou mais, separando os atributos que dependem de um determinante que **não** é chave candidata — esse determinante passa a fazer parte da PK das novas relações, verificando a 3FN em cada uma delas.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20132.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20133.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20134.png)

---

## SQL

O **SQL** é a ferramenta de programação usada para interagir com bancos de dados relacionais, dividida em quatro famílias de comandos.

### DDL — Data Definition Language

A DDL permite criar, manter e eliminar objetos do banco: tabelas, índices, sequências, views.

**Convenção de nomes**: devem começar com letra; ter de 1 a 30 caracteres; conter apenas `A-Z`, `a-z`, `0-9`, `_`, `$` e `#`; ser únicos por usuário; e não podem ser palavras reservadas (salvo entre aspas).

!!! tip "Chaves naturais vs. artificiais"
    Chaves naturais só devem ser usadas quando forem pequenas e raramente sofrerem atualização — atualizar uma PK impacta índices e FKs em cascata. Quando a chave natural é grande ou sujeita a mudanças, prefira uma chave **artificial** (ex.: auto-incremento).

**Tipos de dados:**

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20135.png)

**Restrições (constraints):**

| Nível | Exemplos |
| --- | --- |
| Tabela | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20136.png) |
| Coluna | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20137.png) |
| Integridade referencial | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20138.png) |

#### Estudo de caso

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20139.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20140.png)

```sql
CONSTRAINT PK_USUARIOS PRIMARY KEY (CPF)       -- define CPF como PK de PESQUISADOR
CONSTRAINT AK_USU_CPF UNIQUE (NOME, NASCIMENTO) -- cria uma AK/restrição única: impede duas
                                                 -- pessoas com mesmo nome e nascimento
```

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20141.png)
![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20142.png)

```sql
CONSTRAINT PK_ARTIGO PRIMARY KEY (MAT)                         -- define MAT como PK de ARTIGO
CONSTRAINT FK_ART_EVE FOREIGN KEY (COD) REFERENCES EVENTO(COD) -- liga EVENTO e ARTIGO
CONSTRAINT CHK_ART_NOTA CHECK (NOTA BETWEEN 0 AND 10)          -- nota sempre entre 0 e 10
```

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20143.png)

```sql
CONSTRAINT ESCREVE_PK PRIMARY KEY (CPF, MAT)
    -- PK composta: a combinação (CPF, MAT) deve ser única

CONSTRAINT ESCREVEPESQUISADOR_FK FOREIGN KEY (CPF)
    REFERENCES PESQUISADOR ON DELETE CASCADE
    -- ao deletar um pesquisador, a linha correspondente em ESCREVE também é removida

CONSTRAINT ESCREVEARTIGO_FK FOREIGN KEY (MAT)
    REFERENCES ARTIGO ON DELETE CASCADE
    -- ao deletar um artigo, a linha correspondente em ESCREVE também é removida
```

#### Comandos DDL

| Operação | Referência |
| --- | --- |
| Criar tabelas | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20144.png) |
| Alterar tabelas | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20145.png) |
| Excluir ou limpar tabela | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20146.png) |
| Criar/excluir índices | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20147.png) |
| Criar/excluir sequências | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20148.png) |
| Criar/excluir views | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20149.png) |
| Criar/excluir papéis/usuários | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20150.png) |

!!! tip "Quando (não) criar índices"
    **Criar** índices quando: a tabela tem muitas linhas; a coluna tem muitos valores distintos; a coluna é muito usada em filtros; e a coluna sofre pouca atualização.

    **Evitar** índices quando: a tabela é pequena; a coluna tem muitos valores repetidos; a coluna raramente é usada em filtros; e a coluna sofre atualização frequente (todo índice precisa ser atualizado a cada escrita, custando desempenho de escrita em troca de desempenho de leitura).

### DQL — Data Query Language

| Cláusula | Função |
| --- | --- |
| `SELECT` | Seleciona colunas (`*` seleciona todas); pode combinar com funções de agregação; pode qualificar com schema (`SELECT * FROM public.database`). |
| `FROM` | Especifica de qual tabela os dados serão selecionados. |
| `WHERE` | Filtra linhas **antes** de qualquer agrupamento. |
| `ORDER BY` | Ordena resultados; `ASC` (padrão) ou `DESC`; pode ter múltiplos critérios, com prioridade para o mais à esquerda. |
| `GROUP BY` | Agrupa registros — toda coluna não agregada no `SELECT` precisa aparecer aqui. |
| `HAVING` | Filtra grupos **depois** de aplicar funções de agregação (diferente do `WHERE`, que filtra antes do agrupamento). |
| `LIMIT` | Limita a quantidade de linhas retornadas. |
| `OFFSET` | Especifica a partir de qual linha a consulta deve começar. |

```sql
-- Ordena clientes pelo país
SELECT * FROM customers ORDER BY country;
-- Ordena por país em ordem descendente
SELECT * FROM customers ORDER BY country DESC;
-- Ordena por país e nome do contato
SELECT * FROM customers ORDER BY country, contact_name;
-- Ordena por país em ordem ascendente e nome em ordem descendente
SELECT * FROM customers ORDER BY country ASC, contact_name DESC;
```

#### Window functions

`PARTITION BY` divide o conjunto de resultados em partições (janelas), sendo a peça central das **window functions**: funções usadas para calcular algo sobre um conjunto de linhas relacionadas à linha atual, dentro de uma janela definida — permitindo agregar, classificar ou manipular dados **sem** colapsar as linhas em um único valor (diferente de `GROUP BY`). Duas propriedades centrais:

1. Não reduzem o número de linhas do resultado.
2. Definem uma janela/escopo, tipicamente via `PARTITION BY` (podem também ser usadas sem ele, operando sobre o resultado inteiro).

```sql
SELECT
    .
    .
    window_function_name(arg1, arg2, ...) OVER (
      [PARTITION BY partition_expression, ...]
      [ORDER BY sort_expression [ASC | DESC], ...]
    ) AS column_name
FROM
    tabela t;
```

| Categoria | Função | Descrição |
| --- | --- | --- |
| — | `OVER` | Usada com toda window function, define a janela sobre a qual ela é aplicada. |
| Agregação | `COUNT()` | Conta ocorrências (combinada com `GROUP BY`, conta ocorrências por grupo). |
| | `MIN()` / `MAX()` | Valor mínimo / máximo. |
| | `AVG()` / `SUM()` | Média / soma (atenção a arredondamento com `float`). |
| Ranking | `NTILE(n)` | Divide o conjunto ordenado em $n$ grupos aproximadamente iguais. |
| | `RANK()` | Rank único por linha, com lacunas em empates. |
| | `DENSE_RANK()` | Rank único por linha, sem lacunas (contínuo) em empates. |
| | `ROW_NUMBER()` | Número sequencial único por linha dentro da partição. |
| | `PERCENT_RANK()` | Rank relativo como porcentagem: $\text{PERCENT\_RANK} = \dfrac{\text{RANK} - 1}{N - 1}$, onde $N$ é o total de linhas. |
| | `CUME_DIST()` | Distribuição acumulada: $\text{CUME\_DIST} = \dfrac{\text{linhas com valor} \leq \text{atual}}{\text{total de linhas}}$. |
| Valor | `LAG()` | Acessa o valor da linha **anterior** — útil para comparações e tendências. |
| | `LEAD()` | Acessa o valor da linha **seguinte**. |
| | `FIRST_VALUE()` / `LAST_VALUE()` | Primeiro / último valor de uma coluna ou expressão na janela. |
| | `NTH_VALUE(n)` | O $n$-ésimo valor de uma coluna ou expressão. |

#### Esqueleto geral de uma consulta

```sql
SELECT -- Quais colunas você quer ver?
    coluna1, coluna2, COUNT(*)
    window_function_name(arg1, arg2, ...) OVER (
          [PARTITION BY partition_expression, ...]
          [ORDER BY sort_expression [ASC | DESC], ...]
        )
FROM -- De qual tabela principal?
    tabela_principal
JOIN -- Quer combinar com qual outra tabela?
    outra_tabela ON tabela_principal.id = outra_tabela.id_principal
WHERE -- Quais filtros você quer aplicar nas linhas?
    coluna1 > 100
GROUP BY -- Quer agrupar as linhas por algum critério?
    coluna2
HAVING -- Quer filtrar os grupos que você criou?
    COUNT(*) > 5
ORDER BY -- Como você quer ordenar o resultado final?
    coluna1 DESC
LIMIT -- Quantas linhas você quer como resultado?
    10
OFFSET -- A partir de qual linha você quer começar?
    20;
```

!!! note "Ordem lógica de execução"
    A ordem em que o SQL é *escrito* não é a ordem em que ele é *processado* — o motor avalia aproximadamente `FROM/JOIN` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY` → `LIMIT/OFFSET`:

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20151.png)

### DML — Data Manipulation Language

| Operação | Referência |
| --- | --- |
| Inserção (`INSERT`) | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20152.png) |
| Atualização (`UPDATE`) | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20153.png) |
| Remoção (`DELETE`) | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20154.png) |
| Funções de manipulação de string | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20155.png) |
| Funções de manipulação de números | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20156.png) |

!!! example "Exemplos"
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20157.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20158.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20159.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20160.png)

#### Joins

**Joins** servem para combinar dados de duas (ou mais) tabelas em uma única consulta, com base em colunas comuns entre elas.

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20161.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20162.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20163.png)

Se o tipo de `JOIN` não for especificado, o padrão é o `INNER`. A palavra-chave `OUTER` descreve explicitamente joins externos — que incluem registros de uma tabela mesmo sem correspondência na outra, preenchendo com `NULL` os valores ausentes. `ON` define a condição de junção.

| Tipo | Uso | Sintaxe |
| --- | --- | --- |
| `INNER JOIN` | Registros com correspondência exata em **ambas** as tabelas. | ```sql SELECT coluna1, coluna2 FROM tabela1 INNER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum; ``` |
| `LEFT JOIN` (ou `LEFT OUTER JOIN`) | Todos os registros da tabela esquerda, com correspondentes da direita (`NULL` quando não houver). | ```sql SELECT coluna1, coluna2 FROM tabela1 LEFT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum; ``` |
| `RIGHT JOIN` (ou `RIGHT OUTER JOIN`) | Inverso do `LEFT JOIN` (menos comum): todos os registros da direita, com correspondentes da esquerda. | ```sql SELECT coluna1, coluna2 FROM tabela1 RIGHT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum; ``` |
| `FULL OUTER JOIN` | União de `LEFT` e `RIGHT`: todos os registros de ambas, com `NULL` onde faltar correspondência. | ```sql SELECT coluna1, coluna2 FROM tabela1 FULL OUTER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum; ``` |
| `CROSS JOIN` | Produto cartesiano das tabelas — cada linha de uma com cada linha da outra; não precisa de `ON`. | ```sql SELECT coluna1, coluna2 FROM tabela1 CROSS JOIN tabela2; ``` |
| `NATURAL JOIN` | Faz o join automaticamente pelas colunas de mesmo nome, sem exigir condição explícita. | ```sql SELECT coluna1, coluna2 FROM tabela1 NATURAL JOIN tabela2; ``` |
| `SELF JOIN` | Join de uma tabela com ela mesma — útil para comparar registros dentro da mesma tabela. | ```sql SELECT a.coluna1, b.coluna2 FROM tabela a INNER JOIN tabela b ON a.coluna_comum = b.coluna_comum; ``` |
| `LATERAL JOIN` | Une tabelas com subconsultas que dependem de cada linha da tabela principal — útil quando a subconsulta precisa de informação da linha atual. | ```sql SELECT coluna1, coluna2 FROM tabela1 JOIN LATERAL (subconsulta) AS alias ON condição; ``` |

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20164.png)

!!! warning "Má prática: join implícito"
    A consulta abaixo não está tecnicamente errada, mas mistura tabelas sem cláusula `JOIN` explícita — evite:

    ```sql
    SELECT A.TITULO, E.SIGLA
    FROM ARTIGO A
    JOIN EVENTO E ON A.TITULO = E.SIGLA;
    ```

    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20165.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20166.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20167.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20168.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20169.png)

#### Subconsultas

Uma **subconsulta** é um comando `SELECT` que fica dentro de outro comando principal, facilitando a resolução de problemas mais complexos. Subconsultas são categorizadas em duas dimensões:

**Quanto ao formato do resultado:**

| Tipo | Retorna |
| --- | --- |
| Escalar | Uma única linha e uma única coluna (um único valor). ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20170.png) |
| Linha | Várias colunas, mas uma única linha. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20171.png) |
| Tabela | Uma ou mais colunas, múltiplas linhas. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20172.png) |

**Quanto à dependência da consulta principal:**

- **Simples**: executa de forma independente, sem precisar de nenhum valor vindo da consulta principal.
- **Correlacionada**: depende de algum valor obtido apenas da consulta principal.
    - **SEMI JOIN**: retorna as linhas de $A$ para as quais existe **pelo menos uma** correspondência em $B$ — feito principalmente com `EXISTS` (mais performático, pois usa índice), mas também com `IN`. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20173.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20174.png)
    - **ANTI JOIN** (ou ANTI SEMI JOIN, negação do SEMI JOIN): retorna as linhas de $A$ para as quais **não existe nenhuma** correspondência em $B$ — feito com `NOT EXISTS` (mais performático) ou `NOT IN`. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20175.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20176.png)

!!! example "Padrões de uso"
    - Subconsulta simples e escalar no `SELECT`/`WHERE`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20177.png)
    - Subconsulta simples e tabela no `FROM`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20178.png)
    - Subconsulta simples e tabela no `HAVING`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20179.png)
    - Avaliação condicional: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20180.png)

#### Set operators

| Operador | Comportamento |
| --- | --- |
| `UNION` | União de dois conjuntos de resultados, **removendo** duplicatas. `UNION ALL` faz o mesmo, mas **mantendo** duplicatas. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20181.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20182.png) |
| `INTERSECT` | Interseção entre dois conjuntos: retorna apenas as linhas presentes em **ambas** as consultas. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20183.png) |
| `EXCEPT` | Retorna as linhas da primeira consulta que **não** existem na segunda. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20184.png) |
| União exclusiva (complemento) | Linhas que estão na primeira **ou** na segunda consulta, mas não em ambas. ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20185.png) |
| Divisão relacional | Dadas duas tabelas, retorna as tuplas da primeira associadas a *todas* as tuplas da segunda — responde perguntas do tipo "quais X estão associados a TODOS os Y de um conjunto?". ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20186.png) |

### DCL — Data Control Language

Gerencia as permissões e o acesso dos usuários ao banco de dados.

- **`GRANT`** — concede privilégios/permissões a um usuário ou grupo: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20187.png)
- **`REVOKE`** — remove privilégios/permissões previamente concedidos: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20188.png)
- **`DENY`** (ausente no Oracle) — cria uma proibição explícita, que se sobrepõe a um `GRANT`.

### TCL — Transaction Control Language

Gerencia transações no banco de dados:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20189.png)

!!! note "Propriedades ACID"
    | Propriedade | Garantia |
    | --- | --- |
    | **Atomicidade** | Todas as operações de uma transação são efetivadas, ou, em caso de falha, nenhuma é. |
    | **Consistência** | A transação sempre leva o banco de um estado válido para outro estado válido. |
    | **Isolamento** | A interação entre transações concorrentes é bem definida, garantindo que não interfiram indevidamente umas nas outras. |
    | **Durabilidade** | Uma vez consolidada, a transação permanece gravada até que novas transações a alterem. |

| Comando | Função |
| --- | --- |
| `START TRANSACTION` / `BEGIN TRANSACTION` | Marca o início de uma transação. |
| `COMMIT` | Salva permanentemente as alterações feitas desde o início da transação. |
| `ROLLBACK` | Descarta as alterações feitas desde o início da transação. |
| `SAVEPOINT` | Cria um marcador intermediário dentro de uma transação longa, para permitir um rollback parcial. |

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20190.png)

---

## PL/SQL

O **PL/SQL** é a linguagem procedural da Oracle, que estende o SQL-DML com comandos que permitem criar blocos de programação (ela **não** aceita SQL-DDL diretamente).

### Estrutura básica

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20191.png)

**Tipos de bloco:**

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20192.png)

**Tipos de identificadores:**

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20193.png)

- **Tipo primitivo**: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20194.png) — exemplos: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20195.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20196.png)
- **Tipo registro** (semelhante a uma struct): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20197.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20198.png)
- **Tipo tabela** (coleção): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20199.png) — manipulando uma coleção do tipo tabela: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20200.png)

**Operadores:**

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20201.png)

### Estrutura de aninhamento

Blocos PL/SQL podem ser aninhados dentro de outros blocos, criando escopos locais:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20202.png)

### Consultas dentro de PL/SQL

| Comando | Referência |
| --- | --- |
| `SELECT` | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20203.png) |
| `INSERT` | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20204.png) |
| `UPDATE` | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20205.png) |
| `DELETE` | ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20206.png) |

### Estruturas de controle de fluxo

**`IF`:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20207.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20208.png)

    !!! warning "Inicializar variáveis no DECLARE"
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20209.png)

**`CASE`:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20210.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20211.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20212.png)

**`LOOP`:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20213.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20214.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20215.png)

**`WHILE`:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20216.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20217.png)

**`FOR`:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20218.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20219.png)

### Cursores

Um **cursor** é semelhante a um ponteiro para manipular, linha a linha, o resultado de uma consulta.

| Tipo | Descrição |
| --- | --- |
| **Implícito** | Declarado e gerenciado automaticamente pelo servidor Oracle para todo comando DML e `SELECT` em PL/SQL. |
| **Explícito** | Declarado e gerenciado pelo programador, gerado apenas a partir de um `SELECT`. |

**Fluxo de uso:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20220.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20221.png)

**Sintaxe:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20222.png)

1. **Abrir** o cursor: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20223.png)
2. **Ler** o cursor: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20224.png)
    - Usando `LOOP`/`EXIT`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20225.png)
    - Usando `WHILE`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20226.png)
3. **Fechar** o cursor: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20227.png)

**Variações:**

- Cursor com tipo registro: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20228.png)
- Cursor com laço `FOR`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20229.png) (e, sem declaração explícita do cursor: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20230.png))
- Cursor com parâmetros: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20231.png)

### Exceções

**Fluxo de tratamento:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20232.png)

**Estrutura do tratamento:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20233.png)

**Exceções predefinidas:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20234.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20235.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20236.png)

**Exceções criadas pelo usuário:**

- Criação: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20237.png)
- Exemplo de uso: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20238.png)

### Subprogramas

Um subprograma é um bloco de código **nomeado** (sem `DECLARE` próprio), podendo ser uma **PROCEDURE** (por padrão, não retorna valor) ou uma **FUNCTION** (por padrão, obrigatoriamente retorna valor):

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20239.png)

**Sintaxe geral:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20240.png)

!!! example
    - Exemplo de procedimento: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20241.png)
    - Exemplo de função: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20242.png)

**Chamando subprogramas:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20243.png)

**Subprogramas parametrizados:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20244.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20245.png)

Os **modos de passagem de parâmetro** (`IN`, `OUT`, `IN OUT`) definem a direção do fluxo de dados entre o chamador e o subprograma:

![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20246.png) ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20247.png)

**Excluindo subprogramas:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20248.png)

#### Organizando subprogramas em pacotes

Um **pacote** (*package*) é a estrutura que agrupa logicamente subprogramas, tipos de dados, variáveis etc., encapsulando-os em um único objeto do banco de dados. Os subprogramas de um pacote devem estar especificados na ordem em que são chamados (um subprograma "chamado" precisa já ter sido declarado antes nesse arquivo). O pacote é formado por duas partes:

- **Especificação** (pública) — a interface visível de fora;
- **Corpo** (privado) — a implementação interna.

**Sintaxe:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20249.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20250.png)

**Chamando pacotes:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20251.png)

**Removendo pacotes:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20252.png)

### Triggers

**Triggers** são códigos PL/SQL armazenados no SGBD, associados a um objeto do banco, e executados **implicitamente** pelo SGBD quando ocorre um determinado evento (ou combinação de eventos). São úteis para registrar modificações (auditoria), garantir regras de negócio, gerar valores de coluna automaticamente e manter tabelas duplicadas sincronizadas.

!!! warning "Boas práticas"
    - Recomenda-se não ultrapassar 60 linhas de código em um trigger — caso contrário, extrair a lógica para subprogramas chamados por ele.
    - Não há como definir a ordem de execução entre múltiplos triggers do mesmo evento.
    - Evite usar triggers para refazer ações que o próprio SGBD já executaria nativamente.

**Sintaxe geral:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20253.png)

**Componentes de um trigger:**

- **Momento**: o instante (`BEFORE`, `AFTER` ou `INSTEAD OF`) em que o trigger deve disparar.
- **Evento**: de DBA (`CREATE`, `ALTER`, `DROP`, `SERVERERROR`, `LOGON`, `LOGOFF`, `STARTUP`, `SHUTDOWN`, `GRANT`, `REVOKE`) ou de DML (`INSERT`, `DELETE`, `UPDATE`).

!!! example "Momento/Evento"
    - DML: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20254.png) (evento DML: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20255.png))
    - VIEW (`INSTEAD OF`): ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20256.png) (evento VIEW: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20257.png))

- **Tipo** (aplicável apenas a eventos DML):
    - **Comando**: disparado antes ou depois de um comando, independentemente deste afetar uma ou mais linhas; não permite acesso às linhas atualizadas; sintaticamente, basta **não** usar `FOR EACH ROW`. *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20258.png)
    - **Linha**: disparado para **cada linha** afetada; `UPDATE` exige a definição explícita do campo (`UPDATE OF campo`). *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20259.png) (com cláusula `WHEN`: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20260.png))
- **Ação**: o bloco PL/SQL associado ao evento. Quando o trigger responde a mais de um evento DML, é preciso usar predicados lógicos para diferenciá-los: `INSERTING`, `UPDATING`, `DELETING` (verdadeiros conforme o comando que disparou o trigger). *Exemplo:* ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20261.png) (impedindo um comando DML: ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20262.png))

**Removendo triggers:** ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20263.png)
