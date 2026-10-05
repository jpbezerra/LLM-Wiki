# ESTATÍSTICA E PROBABILIDADE P/ COMPUTAÇÃO

Referências da disciplina:

- [cin.ufpe.br/~et586cc](https://www.cin.ufpe.br/~et586cc/)
- [Tabelas estatísticas (IN1119)](https://sites.google.com/a/cin.ufpe.br/in1119/tabelas?authuser=0)

## Probabilidade

### Conceitos de probabilidade

Existem diferentes formas de interpretar o que significa "probabilidade":

- **Clássico** — baseado em espaços amostrais com resultados igualmente prováveis.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled.png)

- **Frequentista** — baseado na frequência relativa observada em repetições do experimento.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%201.png)

- **Subjetivo** — baseado no grau de crença pessoal sobre a ocorrência de um evento.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%202.png)

- **Formal (axiomático)** — baseado nos axiomas de Kolmogorov, que fundamentam matematicamente a probabilidade independentemente de interpretação.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%203.png)

### Experimento aleatório

Um **experimento aleatório** é aquele em que há possibilidade de ocorrência de diversos resultados (eventos), sem que se possa prever com certeza qual deles vai ocorrer.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%204.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%205.png)

### Espaço amostral

O **espaço amostral** ($\Omega$) é o conjunto de todos os resultados possíveis de um experimento. Um resultado do espaço amostral é chamado de **evento**. $\Omega$ pode ser:

- **Quantitativo** — abordagem numérica para a coleta de dados.
    - **Discreto** — resulta de um conjunto finito (ou enumerável) de valores possíveis.

        !!! example
            ??? note "Imagem de referência"
                ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%206.png)

    - **Contínuo** — resulta de um número infinito de valores possíveis, associados a pontos de uma escala contínua.

        !!! example
            ??? note "Imagem de referência"
                ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%207.png)

- **Qualitativo** — abordagem não numérica para a coleta de dados.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%208.png)

!!! example "Exemplos de espaço amostral"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%209.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2010.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2011.png)

### Classe de eventos aleatórios

A **classe de eventos aleatórios** é o conjunto de todos os subconjuntos (eventos) do espaço amostral — ou seja, o conjunto das partes de $\Omega$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2012.png)

**Propriedades**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2013.png)

**Operações sobre eventos**

- **União** ($A \cup B$):

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2014.png)

- **Interseção** ($A \cap B$):

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2015.png)

- **Complementação** ($A^c$ ou $\overline{A}$):

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2016.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2017.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2018.png)

**Propriedades das operações**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2019.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2020.png)

**Partição**

Uma **partição** do espaço amostral é uma coleção de eventos mutuamente exclusivos cuja união é o próprio $\Omega$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2021.png)

**Eventos mutuamente exclusivos**

Dois eventos são **mutuamente exclusivos** (ou disjuntos) quando não podem ocorrer simultaneamente, isto é, $A \cap B = \emptyset$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2022.png)

### Experimentos de contagem

Técnicas de contagem (análise combinatória) são usadas para calcular o número de resultados possíveis em experimentos complexos, essencial para calcular probabilidades no conceito clássico.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2023.png)

**Combinação** — escolha de $k$ elementos de um conjunto de $n$, **sem** considerar a ordem: $\binom{n}{k} = \dfrac{n!}{k!(n-k)!}$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2024.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2025.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2026.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2027.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2028.png)

**Permutação** — arranjo de $n$ elementos **considerando a ordem**: $P_n = n!$ (ou $\dfrac{n!}{(n-k)!}$ para arranjos de $k$ elementos escolhidos entre $n$).

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2029.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2030.png)

### Teoremas de probabilidade

!!! example "Teorema 1"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2031.png)

!!! example "Teorema 2"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2032.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2033.png)

!!! example "Teorema 3"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2034.png)

!!! example "Teorema 4"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2035.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2036.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2037.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2038.png)

### Probabilidades dos espaços amostrais

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2039.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2040.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2041.png)

### Exercício

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2042.png)

| Item | Probabilidade |
|---|---|
| a | $30/55$ |
| b | $27/55$ |
| c | $13/55$ |
| d | $42/55$ |
| e | $13/55$ |
| f | $15/55$ |

## Probabilidade condicional

A **probabilidade condicional** $P(A \mid B)$ mede a probabilidade de $A$ ocorrer, dado que sabemos que $B$ já ocorreu.

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2043.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2044.png)

!!! example "Exemplo 1 — lançamento de dois dados"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2045.png)

!!! example "Exemplo 2"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2046.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2047.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2048.png)

### Teorema do produto

O **teorema do produto** permite calcular a probabilidade da interseção de dois eventos a partir da probabilidade condicional: $P(A \cap B) = P(A \mid B) \cdot P(B)$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2049.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2050.png)

### Independência estatística

Dois eventos $A$ e $B$ são **estatisticamente independentes** quando a ocorrência de um não afeta a probabilidade do outro: $P(A \mid B) = P(A)$, o que equivale a $P(A \cap B) = P(A) \cdot P(B)$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2051.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2052.png)

### Teorema de Bayes

O **Teorema de Bayes** permite "inverter" uma probabilidade condicional, relacionando $P(A \mid B)$ com $P(B \mid A)$:

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2053.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2054.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2055.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2056.png)

## Variáveis aleatórias

Uma **variável aleatória** é uma variável que assume um único valor numérico, determinado pelo acaso, para cada resultado de um experimento.

- **Discreta** — tem um número finito de valores, ou uma quantidade **enumerável** de valores ("enumerável" significa que, mesmo havendo infinitos valores possíveis, eles podem ser associados a um processo de contagem, como os números naturais).

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2057.png)

- **Contínua** — tem infinitos valores possíveis, associados a medidas em uma escala contínua, sem "pulos" ou interrupções.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2058.png)

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2059.png)

### Função de probabilidade (distribuição de probabilidade)

É um gráfico, tabela ou fórmula que dá a probabilidade de cada valor possível da variável aleatória — a associação entre a variável aleatória e sua probabilidade.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2060.png)

**Representações**

- Gráfica:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2061.png)

- Tabela:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2062.png)

**Função de uma variável aleatória**

Qualquer função de uma variável aleatória também é, ela mesma, uma variável aleatória.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2063.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2064.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2065.png)

### Função de distribuição (de repartição)

Seja $X$ uma variável aleatória discreta. A função de distribuição $F(x)$ é definida como a probabilidade de que $X$ assuma um valor menor ou igual a $x$: $F(x) = P(X \leq x)$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2066.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2067.png)

**Propriedades**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2068.png)

### Função de densidade de probabilidade (fdp)

Seja $X$ uma variável aleatória contínua. A função de densidade de probabilidade $f(x)$ satisfaz as seguintes condições (não-negatividade e integral total igual a 1):

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2069.png)

!!! note
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2070.png)

!!! example "Exemplos"
    1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2071.png)

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2072.png)

    2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2073.png)

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2074.png)

    3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2075.png)

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2076.png)

    4. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2077.png)

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2078.png)

        (Utiliza o conceito de esperança matemática, abordado a seguir.)

## Medidas de variáveis aleatórias

### Medidas de posição

#### Esperança matemática (valor esperado ou média)

O **valor esperado** de uma variável aleatória é a soma do produto de cada valor possível pela sua respectiva probabilidade — é um número real, e também pode ser visto como uma **média ponderada**. Notação: $\mu$ ou $\mu_X$.

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2079.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2080.png)

**Esperança de uma variável discreta**

Seja $X$ uma variável aleatória discreta com valores possíveis $x_1, x_2, \ldots, x_n$, e seja $p(x_i) = P(X = x_i)$, $i = 1, \ldots, n$. O valor esperado de $X$ é:

$$E(X) = \sum_{i=1}^{n} x_i \cdot p(x_i)$$

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2081.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2082.png)

**Esperança de uma variável contínua**

Seja $X$ uma variável aleatória contínua com função de densidade $f(x)$. O valor esperado de $X$ é:

$$E(X) = \int_{-\infty}^{\infty} x \cdot f(x)\, dx$$

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2083.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2084.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2085.png)

**Propriedades**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2086.png)

!!! tip "Interpretação prática"
    Do ponto de vista estatístico, a média pode indicar a "honestidade" de um determinado evento: quando a média tende a um valor menor que o esperado por acaso, isso pode sugerir que o evento não é justo (por exemplo, um jogo manipulado).

#### Mediana

A **mediana** de uma variável aleatória é o valor que divide a distribuição em duas partes iguais, ou seja, $F(M_d) = 0{,}5$, onde $M_d$ é a mediana e $F(X)$ é a função de distribuição.

**Aplicações**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2087.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2088.png)

#### Moda

- **Definição discreta** — o valor de $X$ com **maior probabilidade**.
- **Definição contínua** — o valor de $X$ com **maior densidade**.

!!! example
    Discreta:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2089.png)

    Contínua:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2090.png)

### Medidas de dispersão

#### Variância

A **variância** de uma variável aleatória mede o quanto seus valores se afastam, em média, da esperança:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2091.png)

- Para $X$ **discreta**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2092.png)

    A variância de $X$ é o somatório de $(x_i - E(X))^2$ ponderado pela probabilidade $p(x_i)$.

- Para $X$ **contínua**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2093.png)

    A variância de $X$ é a integral, de $-\infty$ a $+\infty$, de $(x - E(X))^2 \cdot f(x)$.

**Propriedades**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2094.png)

#### Desvio padrão

O **desvio padrão** é a raiz quadrada da variância: $\sigma = \sqrt{\text{Var}(X)}$.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2095.png)

### Exemplos

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2096.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2097.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2098.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%2099.png)

4. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20100.png)

    (Exemplo ainda não totalmente compreendido — revisar com o material da disciplina.)

5. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20101.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20102.png)

    (Resolução possivelmente contém erro — revisar.)

## Distribuições de probabilidade

### Modelos de distribuição discretas

As distribuições discretas mais comuns compartilham a ideia de "ensaios" (tentativas) com dois ou mais resultados possíveis. A tabela a seguir resume as principais:

| Distribuição | Cenário típico | $E(X)$ | $\text{Var}(X)$ |
|---|---|---|---|
| Bernoulli | Um único ensaio, sucesso/fracasso | $p$ | $pq$ |
| Binomial | $n$ ensaios independentes, com reposição | $np$ | $npq$ |
| Geométrica | Ensaios até o primeiro sucesso | $1/p$ | $q/p^2$ |
| Poisson | Ocorrências em um intervalo de tempo/espaço | $\lambda$ | $\lambda$ |
| Hipergeométrica | Amostragem sem reposição | — | — |

#### Distribuição de Bernoulli

Seja $X$ uma variável aleatória com dois resultados possíveis: fracasso ou sucesso. A probabilidade de sucesso é $P(X=1) = p$, e a de fracasso é $P(X=0) = 1-p = q$.

- Valor esperado: $E(X) = \mu_X = p$.
- Variância: $\text{Var}(X) = \sigma^2 = pq$.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20103.png)

#### Distribuição binomial

Modela sucessos ou fracassos **sucessivos e independentes** (como ensaios com reposição), em que a probabilidade $p$ (e $1-p$) é a mesma em cada ensaio.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20104.png)

**Função de probabilidade**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20105.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20106.png)

Seja $X$ uma variável aleatória binomial com parâmetros $n$ (número de ensaios) e $p$ (probabilidade de sucesso): $X \in \{0, 1, 2, \ldots, n\}$.

- Valor esperado: $E(X) = \mu_X = np$.
- Variância: $\text{Var}(X) = \sigma^2 = npq$.

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20107.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20108.png)

#### Distribuição geométrica

Modela o número de tentativas sucessivas **até o primeiro sucesso**, com dois resultados possíveis por tentativa, probabilidades constantes ($p$ e $1-p$) e ensaios independentes (com reposição).

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20109.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20110.png)

**Função de probabilidade**

Considerando uma sequência de ensaios de Bernoulli, a distribuição geométrica dá a probabilidade de que sejam necessários $k$ ensaios até o primeiro sucesso:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20111.png)

onde $p$ é a probabilidade de sucesso, $(1-p)$ a de fracasso e $k$ o número de ensaios.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20112.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20113.png)

    (O expoente correto no denominador/contagem de ensaios é $k - 1$, não $k$.)

#### Distribuição de Poisson

Modela o número de ocorrências de um evento em um intervalo específico de tempo ou espaço.

!!! example "Exemplos de aplicação"
    Erros tipográficos por página; defeitos por unidade de área/comprimento em uma peça fabricada; mortes por ataque cardíaco por ano.

**Propriedades**

- A probabilidade de uma ocorrência é a mesma para quaisquer dois intervalos de igual tamanho.
- A ocorrência (ou não) em um intervalo é independente da ocorrência em qualquer outro intervalo.

**Função de probabilidade**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20114.png)

Onde:

- $X$ é o número de ocorrências (sucessos).
- $P(X)$ é a probabilidade de $X$ ocorrências em um intervalo.
- $\lambda$ é o valor esperado (número médio de ocorrências no intervalo).
- $e$ é o número de Euler ($\approx 2{,}71828$).
- Valor esperado: $E(X) = \lambda$.
- Variância: $\text{Var}(X) = \lambda$.

!!! example "Exemplo 1"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20115.png)

!!! example "Exemplo 2"
    Numa fita de som, há um defeito a cada 200 pés. Qual é a probabilidade de que:

    **a) em 500 pés não aconteça nenhum defeito?**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20116.png)

    **b) em 800 pés ocorram pelo menos 3 defeitos?**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20117.png)

#### Distribuição hipergeométrica

Semelhante à binomial, mas composta por $r$ ensaios **sem reposição** — ou seja, os ensaios passam a ser **dependentes**. O conjunto é composto por dois tipos de objetos (dois resultados possíveis).

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20118.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20119.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20120.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20121.png)

**Função de probabilidade**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20122.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20123.png)

#### Exemplos (distribuições discretas)

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20124.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20125.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20126.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20127.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20128.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20129.png)

### Modelos de distribuição contínuas

#### Distribuição uniforme

Considera um intervalo $[a, b]$ dentro do qual qualquer valor é igualmente provável.

!!! example
    Suponha que o tempo de voo possa ser qualquer valor no intervalo entre 120 e 140 minutos; seja $X$ a variável aleatória que representa o tempo de voo de uma aeronave viajando de Chicago a Nova York.

**Função de probabilidade**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20130.png)

**Gráfico**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20131.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20132.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20133.png)

#### Distribuição exponencial

Útil para descrever o tempo necessário para completar uma tarefa.

!!! example "Exemplos de aplicação"
    Tempo entre chegadas de pacotes em um roteador; tempo de vida de aparelhos; tempo de espera em restaurantes ou caixas de banco.

- Parâmetro: $\lambda$ (média ou valor esperado).
- Está intimamente ligada à distribuição de Poisson (o tempo entre eventos de Poisson segue uma exponencial).

**Função de probabilidade**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20134.png)

O $\lambda$ aqui segue a mesma lógica do $\lambda$ da distribuição de Poisson.

**Gráfico**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20135.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20136.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20137.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20138.png)

    O resultado final é a soma de uma parte com a outra.

#### Distribuição normal

Usada em uma ampla variedade de aplicações práticas, para variáveis como altura, peso, medições e índices em geral.

- Parâmetros: $\mu$ (média) e $\sigma$ (desvio padrão).

!!! example
    Os salários dos diretores de empresas em São Paulo se distribuem normalmente, com média de R\$ 20.000,00 e desvio padrão de R\$ 500,00.

**Função de probabilidade**

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20139.png)

**Gráfico**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20140.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20141.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20142.png)

#### Exemplos (distribuições contínuas)

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20143.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20144.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20145.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20146.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20147.png)

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20148.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20149.png)

    Observação: `0,31` é o Z-Score correspondente a `0,12` na tabela da normal.

### Exemplos gerais sobre distribuições

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20150.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20151.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20152.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20153.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20154.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20155.png)

4. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20156.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20157.png)

5. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20158.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20159.png)

6. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20160.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20161.png)

7. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20162.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20163.png)

## Análise exploratória

### Tabela estatística

Toda tabela estatística deve ter: **cabeçalho** (breve descrição do propósito), **corpo** (os registros de dados) e **rodapé** (fonte dos dados).

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20164.png)

### Séries estatísticas

Uma **série estatística** é qualquer tabela que apresenta a distribuição de um conjunto de dados em função da época (fator temporal), do local (onde o fenômeno ocorre) ou da espécie (o fato/fenômeno em si).

| Tipo | Fator variável | Fatores fixos |
|---|---|---|
| **Temporal (cronológica)** | Época | Local e espécie |
| **Geográfica (histórica)** | Local | Época e espécie |
| **Específica (categórica)** | Espécie | Época e local |

!!! example "Série temporal"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20165.png)

!!! example "Série geográfica"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20166.png)

!!! example "Série específica"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20167.png)

**Distribuições de frequência** — tabela em que os valores da variável não aparecem individualmente, mas agrupados em classes.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20168.png)

### População e amostra

- **População** — conjunto de elementos que compartilham uma determinada característica. Pode ser finita ou infinita (algumas populações finitas são tratadas como infinitas para fins práticos).
- **Amostra** — qualquer subconjunto **não vazio** da população, com número de elementos menor que o da população.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20169.png)

A escolha de como selecionar a amostra depende, entre outros fatores, do grau de conhecimento sobre a população e dos recursos disponíveis. O objetivo é que a amostra seja o mais representativa possível da população de origem.

**Tipos de amostragem**

- **Amostragem aleatória** — cada elemento é retirado aleatoriamente de toda a população (com ou sem reposição); toda amostra possível tem a mesma probabilidade de ser selecionada.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20170.png)

- **Amostragem estratificada** — subdivide a população em pelo menos dois grupos (estratos) que compartilham alguma característica, e depois coleta uma amostra de cada estrato (tipicamente por amostragem aleatória dentro de cada um).

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20171.png)

- **Amostragem sistemática** — usada quando os elementos da população já estão ordenados, e a retirada ocorre periodicamente (por exemplo, a cada $k$-ésimo elemento).

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20172.png)

### Variável (estatística)

Uma **variável** é uma característica observável nos elementos da população, com pelo menos um resultado possível para cada elemento observado.

- **Qualitativa** — o resultado é um atributo ou qualidade.
    - **Ordinal** — admite uma ordenação natural entre as categorias.

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20173.png)

    - **Nominal** — não existe ordenação entre as categorias.

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20174.png)

- **Quantitativa** — o resultado é um número em uma escala pré-determinada.
    - **Discreta** — resultados possíveis são números inteiros (ex.: número de alunos).
    - **Contínua** — o resultado está em um intervalo dos números reais (ex.: atraso de transmissão de bytes em uma rede).

### Gráficos

Gráficos representam resultados obtidos, permitindo tirar conclusões sobre a evolução de um fenômeno ou sobre como se relacionam os valores de uma série.

- **Gráfico de barras** (barras horizontais):

    ??? note "Imagem de referência"
        ![image.png](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/image.png)

- **Gráfico de colunas** (barras verticais), útil para mostrar alterações ao longo do tempo ou comparar itens:

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20175.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20176.png)

- **Gráfico de setor (pizza)**, útil para mostrar a importância relativa de proporções, trabalhando com porcentagens:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20177.png)

- **Gráfico de hastes**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20178.png)

- **Histogramas** — representação gráfica de uma distribuição de frequências por meio de retângulos justapostos.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20179.png)

**Distribuição de frequência**

O método mais útil para descrever os resultados de uma variável é a **distribuição de frequência**: uma tabela em que os valores não aparecem individualmente, mas agrupados em classes.

!!! warning "Cuidado ao escolher o número de classes"
    - Com **muitos** intervalos, corremos o risco de não realçar aspectos relevantes (ruído em excesso).
    - Com **poucos** intervalos, os grupos ficam muito abrangentes, impedindo maior precisão.

**Polígono de frequências** — representação gráfica da distribuição de frequências, usando os pontos médios dos intervalos de classe, conectados por segmentos de linha.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20180.png)

**Polígono de frequência acumulada** — cada ponto do gráfico representa a soma de todas as frequências das classes anteriores, mais a frequência da classe correspondente ao ponto.

!!! example
    Tabela:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20181.png)

    Polígono de frequência acumulada:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20182.png)

#### Como construir uma tabela de distribuição de frequência

!!! example "Passo a passo"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20183.png)

    **1º passo — determinar a amplitude total**: maior valor menos menor valor. Nesse caso, $18{,}1 - 4{,}7 = 13{,}4$.

    **2º passo — estimar o número de intervalos.** Dois métodos comuns:

    - Seja $n$ o número de observações: para $n > 25$, $K = \sqrt{n}$; para $n \leq 25$, $K = 5$. Nesse exemplo, $K = \sqrt{50} \approx 7{,}07$.
    - **Fórmula de Sturges**: $K = 1 + 3{,}22 \log n$. Nesse caso, $K = 1 + 3{,}22 \log 50 \approx 7$.

    Dada a importância de escolher um número razoável de intervalos, vamos com $K = 7$.

    **3º passo — estimar a amplitude dos intervalos**: dividimos a amplitude total pelo número de intervalos. Nesse caso, $h = 13{,}4 / 7 = 1{,}914 \approx 1{,}92$.

    **4º passo — esquematizar a tabela** de acordo com as informações anteriores:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20184.png)

**Diagramas de dispersão** — usados para identificar se existe correlação (forte, fraca, moderada, positiva, negativa) entre duas variáveis.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20185.png)

**Gráfico de curvas** — usado em processos para acompanhar a evolução de uma variável em relação a um ou mais limites existentes.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20186.png)

!!! tip "Considerações sobre a escolha do gráfico"
    Gráficos setoriais (pizza) são particularmente úteis para visualizar diferenças entre poucas classes, mas não acomodam bem muitas categorias. Nesse caso, é melhor reagrupar as categorias menos importantes em um grupo "outros", ou usar um gráfico de barras com as categorias separadas.

**Melhores gráficos para cada tipo de dado**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20187.png)

### Exercício

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20188.png)

## Medidas estatísticas descritivas

Ferramentas básicas para medir e descrever características de um conjunto de dados.

### Medidas de posição central

Representam um fenômeno pelo seu valor "médio" — o valor em torno do qual os dados tendem a se concentrar.

#### Média

É o valor médio de uma distribuição, calculado segundo uma regra fixada a priori, usado para representar o conjunto de valores. Representada por $\bar{x}$.

=== "Aritmética"
    $$\bar{x} = \frac{1}{n}\sum_{i=1}^n x_i$$

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20189.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20190.png)

    **Para dados agrupados:**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20191.png)

    !!! example
        ??? note "Imagens de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20192.png)

            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20193.png)

=== "Ponderada"
    É uma média aritmética em que cada ocorrência tem um peso específico.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20194.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20195.png)

=== "Harmônica"
    Equivale ao inverso da média aritmética dos inversos de $n$ valores.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20196.png)

=== "Geométrica"
    É a raiz de ordem $n$ do produto dos valores da amostra.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20197.png)

!!! note "Relação entre as médias"
    As médias geométrica e harmônica são sempre **menores ou, no máximo, iguais** à aritmética. A igualdade só ocorre quando todos os valores da amostra são idênticos. Quanto maior a variabilidade dos dados, maior a diferença entre a média aritmética e as médias harmônica/geométrica.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20198.png)

#### Mediana

É o valor que, com os dados ordenados, separa a metade inferior da amostra da metade superior.

- Se $n$ é **ímpar**, a mediana é o valor central:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20199.png)

- Se $n$ é **par**, a mediana é a média simples dos dois valores centrais:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20200.png)

**Para dados agrupados**: calcula-se $n/2$, identifica-se em qual classe esse valor se encontra (a partir das frequências acumuladas), e aplica-se a fórmula:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20201.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20202.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20203.png)

#### Moda

É o valor que ocorre com maior frequência; numa amostra, a moda pode não existir, ou pode ser múltipla (amostra **multimodal**).

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20204.png)

**Moda para dados agrupados** — usa-se a **fórmula de King**:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20205.png)

Onde:

- $l$ — limite inferior da classe modal.
- $\Delta_1$ — diferença entre a frequência da classe modal e a da classe anterior.
- $\Delta_2$ — diferença entre a frequência da classe modal e a da classe posterior.
- $h$ — amplitude da classe modal.

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20206.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20207.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20208.png)

### Medidas de dispersão

Quantificam o quanto os valores da amostra estão afastados (dispersos) em relação à média amostral.

**Amplitude total** — diferença entre o maior e o menor valor do conjunto de dados.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20209.png)

**Desvio padrão** — mede a dispersão dos valores em torno da média. Representado por $s$ (amostral) e $\sigma$ (populacional).

- Para uma população de $N$ indivíduos:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20210.png)

- Para uma amostra de $n$ observações:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20211.png)

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20212.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20213.png)

**Dados agrupados** — usa-se a mesma fórmula, mas cada termo do somatório é ponderado pela frequência absoluta da classe, e $x_i$ passa a ser o ponto médio (a "média") da classe.

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20214.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20215.png)

**Coeficiente de variação** — para um conjunto de dados amostrais ou populacionais, expresso como percentual, descreve o desvio padrão relativo à média:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20216.png)

É uma medida **adimensional**, útil para comparar a dispersão de amostras/populações em unidades diferentes. Desvantagem: perde utilidade quando a média está próxima de zero.

**Variância** — medida de dispersão igual ao quadrado do desvio padrão:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20217.png)

!!! warning
    A variância não é expressa nas mesmas unidades dos dados originais (é o quadrado da unidade original), o que dificulta sua interpretação direta.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20218.png)

**Amplitude interquartílica** — amplitude do intervalo entre o primeiro e o terceiro quartil, representada por $IQ$ (ou $Q$):

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20219.png)

É uma medida de variabilidade robusta, pouco afetada por dados atípicos (*outliers*); tem relação com o desvio padrão:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20220.png)

### Medidas de posição (separatrizes)

Dividem a área de uma distribuição de frequência em regiões de áreas iguais.

**Quartil** — qualquer um dos três valores que divide o conjunto ordenado de dados em 4 partes iguais; cada parte representa $1/4$ da amostra ou população.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20221.png)

**Para dados agrupados:**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20222.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20223.png)

**Percentil** — divide o conjunto ordenado de dados em 100 partes iguais, cada parte representando $1/100$ da amostra. O $k$-ésimo percentil $P_k$ corresponde à frequência cumulativa de $N \cdot k/100$, onde $N$ é o tamanho amostral.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20224.png)

**Para dados agrupados:**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20225.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20226.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20227.png)

**Relações entre quartil e percentil**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20228.png)

### Medida de assimetria

Permite analisar uma distribuição a partir das relações entre moda, média e mediana — graficamente, ou apenas pelos valores numéricos. Uma distribuição é dita **simétrica** quando moda, média e mediana coincidem; caso contrário, é **assimétrica**.

Para calcular a assimetria, usa-se o **coeficiente de assimetria de Pearson**:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20229.png)

Onde $\bar{x}$ é a média aritmética, $M_o$ é a moda e $s$ é o desvio padrão. O coeficiente assume valores entre $-1$ e $+1$.

!!! example "Curvas assimétricas"
    - Coeficiente $> 0$ (assimetria positiva, cauda à direita):

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20230.png)

    - Coeficiente $< 0$ (assimetria negativa, cauda à esquerda):

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20231.png)

### Curtose

Mede o grau de "achatamento" de uma distribuição em relação a uma curva normal de referência. Para calcular, usa-se o **coeficiente de Pearson**:

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20232.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20233.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20234.png)

### Exercícios

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20235.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20236.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20237.png)

4. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20238.png)

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20239.png)

5. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20240.png)

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20241.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20242.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20243.png)

6. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20244.png)

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20245.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20246.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20247.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20248.png)

### Exemplos adicionais

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20249.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20250.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20251.png)

## Estimação

### Estatística descritiva vs. inferência estatística

A **estatística descritiva** tem por objetivo resumir ou descrever características importantes de dados populacionais ou amostrais já conhecidos. Já a **inferência estatística** é o processo de tirar conclusões (ou generalizações) sobre uma população, usando apenas informações de uma amostra dela.

### Estimativa

Um **estimador** é uma estatística usada para obter uma aproximação de um parâmetro populacional.

**Estimativa pontual** — um único valor usado para aproximar o parâmetro. A média amostral é a melhor estimativa pontual para a média populacional; a variância amostral, para a variância populacional.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20252.png)

**Estimativa intervalar** — um intervalo de valores que contém a média da população com uma determinada probabilidade de acerto. O **intervalo de confiança** está associado a um **grau de confiança**, que mede o quão certos estamos de que o intervalo de fato contém o parâmetro populacional.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20253.png)

**Variância conhecida** (usa-se a distribuição normal):

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20254.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20255.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20256.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20257.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20258.png)

**Variância desconhecida** (usa-se a distribuição t-Student):

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20259.png)

**Grau de liberdade** — o número de valores amostrais que podem variar livremente, depois que certas restrições são impostas aos dados.

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20260.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20261.png)

Com isso, o intervalo de confiança é $\bar{x} - E \leq \mu \leq \bar{x} + E$, onde $E$ é a margem de erro calculada pela fórmula do t-Student acima.

**Intervalo de confiança (resumo)**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20262.png)

!!! example
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20263.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20264.png)

### Exemplos

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20265.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20266.png)

## Teste de hipótese

### Definição

Uma **hipótese estatística** é uma afirmação acerca dos parâmetros de uma ou mais populações, ou acerca da distribuição da população — é uma afirmação sobre a **população**, não sobre a amostra.

Normalmente, formulam-se duas hipóteses:

- $H_0$ — **hipótese nula**, a hipótese que, a princípio, não queremos rejeitar sem evidência suficiente.
- $H_a$ — **hipótese alternativa**, aceita quando não é possível sustentar $H_0$ como verdadeira.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20267.png)

### Formas de hipótese

- **Bilateral**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20268.png)

- **Unilateral à direita**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20269.png)

- **Unilateral à esquerda**:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20270.png)

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20271.png)

### Erros de decisão

| | $H_0$ verdadeira | $H_0$ falsa |
|---|---|---|
| **Rejeitar $H_0$** | Erro Tipo I ($\alpha$) | Decisão correta |
| **Não rejeitar $H_0$** | Decisão correta | Erro Tipo II ($\beta$) |

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20272.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20273.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20274.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20275.png)

### Como realizar testes de hipótese

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20276.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20277.png)

!!! note
    Usa-se a distribuição t-Student quando a variância é desconhecida, com $n - 1$ graus de liberdade.

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20278.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20279.png)

### Testes de hipótese em diferentes formas

=== "Bilateral"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20280.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20281.png)

=== "Unilateral à direita"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20282.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20283.png)

=== "Unilateral à esquerda"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20284.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20285.png)

### Exemplos

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20286.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20287.png)

### Teste de hipóteses para duas médias

**Variâncias desconhecidas** — usa-se a distribuição t-Student. A estatística do teste é:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20288.png)

Onde $\bar{x}_1$ e $\bar{x}_2$ são as médias amostrais, $n_1$ e $n_2$ os tamanhos das amostras, e $S_1^2$ e $S_2^2$ as variâncias amostrais das duas populações.

O valor $t$ calculado é comparado a um valor crítico da tabela t-Student, com $\min\{n_1 - 1, n_2 - 1\}$ graus de liberdade (em R, usa-se `qt(1 - nível_de_significância, min(n1 - 1, n2 - 1))`).

**Variâncias conhecidas**:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20289.png)

**Formas**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20290.png)

=== "Bilateral"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20291.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20292.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20293.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20294.png)

=== "Unilateral à direita"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20295.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20296.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20297.png)

=== "Unilateral à esquerda"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20298.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20299.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20300.png)

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20301.png)

**Exemplos**

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20302.png)

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20303.png)

        ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20304.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20305.png)

### Procedimento geral para teste de hipótese

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20306.png)

Para o 5º passo:

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20307.png)

    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20308.png)

### Como interpretar um teste de hipótese

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20309.png)

### Exemplos finais

1. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20310.png)

2. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20311.png)

3. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20312.png)

4. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20313.png)

5. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20314.png)

6. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20315.png)

7. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20316.png)

8. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20317.png)

9. ![Untitled](../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/Untitled%20318.png)

---

Ver também: [Assunções da regressão linear](estatistica-probabilidade-p-computacao/assuncoes-da-regressao-linear.md)
