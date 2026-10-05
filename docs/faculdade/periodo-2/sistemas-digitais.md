# SISTEMAS DIGITAIS

## O que é um sistema digital?

Um **sistema digital** é um sistema no qual os sinais têm um número finito de valores discretos, em contraposição aos sistemas **analógicos**, nos quais os sinais assumem valores pertencentes a um conjunto contínuo (infinito).

## Conversores analógico-digitais (ADC)

O **conversor analógico-digital (ADC)** é um dispositivo eletrônico capaz de gerar uma representação digital a partir de uma grandeza analógica — normalmente um sinal representado por um nível de tensão ou intensidade de corrente elétrica (por exemplo, uma senoide). Essa representação é feita através de microprocessadores, sensores e transistores, sendo traduzida em binário (base do sistema de codificação ASCII) para o computador.

Quando os conversores fazem essas representações, parte das informações é perdida, como mostrado na imagem:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled.png)

É perceptível que, durante a conversão, muitas informações são perdidas; mas, de acordo com a quantidade de bits (resolução) do conversor, menos informação é perdida (é impossível recuperar 100% da informação original). Com mais bits, menos "quadrado" fica o gráfico à direita:

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%201.png)

### Atributos de um ADC

- **Resolução** — determina a precisão (qualidade) da conversão, e é medida em bits (quanto mais bits, maior a precisão).
- **Precisão** — mostra o quão fiel o valor do sinal digital está em relação ao valor do sinal analógico original; dependendo da precisão, podem ocorrer sinais indesejados durante a conversão (ruídos).
- **Taxa de amostragem** — frequência com que o sinal analógico é amostrado e convertido em valores digitais, medida em SPS (*samples* por segundo).
- **Faixa dinâmica** — amplitude máxima (tamanho dos sinais analógicos) que o conversor consegue suportar (ler) e representar com precisão.
- **Tempo de conversão** — tempo necessário para o conversor realizar a conversão completa.
- **Conectividade** — forma como um conversor se conecta a outros sistemas e dispositivos.

### Tipos de ADC

**ADC $\Delta\Sigma$ (delta-sigma)**

Utilizado principalmente em aplicações dinâmicas que requerem a melhor resolução possível. É comumente encontrado em áudio, som, vibração e outras aplicações de aquisição de dados, pois preserva a fidelidade sonora utilizando alta resolução e alta relação sinal-ruído, em detrimento da taxa de amostragem e do consumo de energia. Possui um design complexo e poderoso, o que o torna ideal para aplicações dinâmicas que requerem maior resolução em altas faixas dinâmicas — tipicamente, utiliza-se uma resolução de 24 bits.

Por causa de sua ótima resolução, esse tipo de conversor também possui ótima precisão, o que faz com que o sinal captado analogicamente seja convertido digitalmente com pouquíssima perda de informação, além de reduzir o ruído. Possui também alta faixa dinâmica, o que permite ao conversor converter sinais com amplitudes muito diferentes, desde sinais fracos até sinais fortes.

**Funcionamento.** Os ADCs delta-sigma funcionam sobre-amostrando os sinais numa taxa muito mais alta do que a taxa de amostragem selecionada; essa sobreamostragem pode ser centenas de vezes maior do que a taxa selecionada pelo usuário. O DSP, então, cria um fluxo de dados de alta resolução a partir desses dados sobre amostrados, na taxa que o usuário selecionou.

!!! note "Tecnologia DSP"
    O **DSP** (*Digital Signal Processing*) é uma tecnologia que lida com a manipulação e conversão de sinais no formato digital, como áudio, vídeo e sinais de dados. Entre suas principais funções estão:

    - **Compressão** — reduz o tamanho dos arquivos de áudio e vídeo, permitindo armazenamento e transmissão mais eficientes.
    - **Equalização** — ajusta a frequência do som para melhorar a qualidade de áudio, de acordo com a preferência do usuário ou do ambiente.
    - **Redução de ruído** — elimina ruídos indesejados presentes em gravações de áudio ou sinais de comunicação.
    - **Cancelamento de ruído** — neutraliza sons indesejados através da geração de ondas sonoras "espelhadas", que se anulam ao se encontrarem com o ruído original.
    - **Melhora de áudio** — aplicação de efeitos sonoros, como reverberação e *chorus*, para enriquecer a experiência sonora.
    - **Codificação e decodificação de sinais** — processamento utilizado em telefonia celular, transmissão de rádio e TV digital.
    - **Reconhecimento de voz** — extrai informações a partir de sinais de voz, como em assistentes virtuais e sistemas de reconhecimento de voz.

Essa abordagem cria um fluxo de dados de resolução muito alta (24 bits é comum), e tem a vantagem de permitir a filtragem anti-*aliasing* (AAF) em vários estágios, tornando virtualmente impossível digitalizar sinais falsos.

!!! note "Filtragem anti-aliasing (AAF)"
    O **aliasing** ocorre quando a frequência de amostragem é insuficiente para capturar fielmente a frequência do sinal original. Para evitar o aliasing, a filtragem anti-aliasing é aplicada antes da conversão analógico-digital: esse filtro atenua as frequências do sinal analógico que estão acima de um limite determinado pela frequência de amostragem. Ao remover essas frequências altas, o filtro garante que o sinal amostrado represente fielmente o sinal original, dentro da limitação da taxa de amostragem.

No entanto, esse processo impõe uma espécie de limite de velocidade; por isso, os ADCs delta-sigma não são tão rápidos quanto os ADCs SA (de aproximações sucessivas).

## Circuitos digitais

São circuitos cujos valores de entrada e saída são bits, pois são baseados na lógica booleana e em suas funções (circuitos lógicos).

### Lógica booleana

Uma **função lógica booleana** é uma função que possui uma ou mais variáveis de entrada e produz um resultado que depende somente dos valores dessas variáveis.

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%202.png)

    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%203.png)

**Como otimizar uma função booleana**

- **Simplificação** — eliminação de termos redundantes.
- **Implementação de hardware** — usar portas lógicas eficientes e operações bit a bit, utilizando a tabela-verdade como referência.
- **Transformação de expressão** — por exemplo, utilizar NAND como combinação de NOT + AND, entre outras transformações equivalentes.

**Teoremas de De Morgan** — leis fundamentais da álgebra booleana que estabelecem relações entre negação, conjunção e disjunção; são ferramentas essenciais para simplificar expressões lógicas, realizar análises de circuitos digitais e construir sistemas lógicos complexos.

1. $\neg(A \land B) \equiv (\neg A) \lor (\neg B)$
2. $\neg(A \lor B) \equiv (\neg A) \land (\neg B)$

### Álgebra de Boole

É a álgebra implementada para a realização de circuitos digitais.

!!! note
    Nessa notação, "$\cdot$" e "$*$" representam a mesma operação que "and" (conjunção); "$+$" representa a mesma operação que "or" (disjunção); e $\overline{X}$ representa a mesma operação que "not $X$" (negação).

**Regras**

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%204.png)

**Teoremas**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%205.png)

    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%206.png)

### Portas lógicas

=== "NOT"
    Inverte o sinal de entrada: $\overline{A}$.

    **Tabela-verdade**

    | A | NOT |
    |---|---|
    | 0 | 1 |
    | 1 | 0 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%207.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%208.png)

=== "AND"
    Saída `1` apenas quando **ambas** as entradas são `1`.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 0 |
    | 0 | 1 | 0 |
    | 1 | 0 | 0 |
    | 1 | 1 | 1 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%209.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2010.png)

=== "NAND"
    Negação do AND: saída `0` apenas quando ambas as entradas são `1`.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 1 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 0 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2011.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2012.png)

=== "OR"
    Saída `1` quando **pelo menos uma** entrada é `1`.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 0 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 1 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2013.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2014.png)

=== "NOR"
    Negação do OR: saída `1` apenas quando ambas as entradas são `0`.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 1 |
    | 0 | 1 | 0 |
    | 1 | 0 | 0 |
    | 1 | 1 | 0 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2015.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2016.png)

=== "XOR"
    Saída `1` quando as entradas são **diferentes**.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 0 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 0 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2017.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2018.png)

=== "XNOR"
    Negação do XOR: saída `1` quando as entradas são **iguais**.

    **Tabela-verdade**

    | A | B | X |
    |---|---|---|
    | 0 | 0 | 1 |
    | 0 | 1 | 0 |
    | 1 | 0 | 0 |
    | 1 | 1 | 1 |

    ??? note "Símbolo da porta e tabela-verdade (imagens de referência)"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2019.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2020.png)

### Mintermos e maxtermos

- **Mintermos** — são as linhas da tabela-verdade cujo resultado é 1. Para obter a expressão em soma de produtos (SOP), faz-se a soma de todos os mintermos dessas linhas.

    !!! example
        ??? note "Imagens de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2021.png)

            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2022.png)

- **Maxtermos** — são as linhas da tabela-verdade cujo resultado é 0. Para obter a expressão em produto de somas (POS), faz-se o produto de todos os maxtermos dessas linhas.

    !!! example
        ??? note "Imagens de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2023.png)

            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2024.png)

### Mapa de Karnaugh

É uma ferramenta gráfica para simplificação de expressões booleanas a partir de tabelas-verdade.

**Como montar um mapa de Karnaugh**

!!! example "Tabela-verdade de exemplo"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2025.png)

    **Mintermos**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2026.png)

1. **Identificar as combinações** que resultam em 1 na tabela-verdade.

2. **Colocar no mapa de Karnaugh** todas as combinações:

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2027.png)

    A primeira linha simboliza o valor de $P_1$, e a primeira coluna simboliza os valores de $P_2$ e $P_3$, nessa ordem.

3. **Formar grupos** de potências de dois ($1, 2, 4, 8, \ldots$) que contenham as combinações cujo valor é 1. Para formar os grupos, é preciso considerar as células (os quadrados) adjacentes (esquerda, direita, acima ou abaixo), formando os grupos com o maior número de células possível.

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2028.png)

4. **Identificar, dentro de cada grupo**, células que apresentam uma variável em sua forma normal e em sua forma complementar. Quando isso acontece, devemos excluir essa variável do termo produto final.

5. **Montar o termo produto final.** No exemplo, o produto final de cada célula ficou da seguinte forma:

    - Célula 1:

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2029.png)

        $f(P_1, P_2, P_3) = P_1$ (o $P_2$ e o $P_3$ se cancelam, pois assumem valores complementares).

    - Célula 2:

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2030.png)

        $f(P_1, P_2, P_3) = \emptyset$ (o $P_1$, o $P_2$ e o $P_3$ se cancelam, pois assumem valores complementares).

    - Célula 3:

        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2031.png)

        $f(P_1, P_2, P_3) = P_2$ (o $P_1$ e o $P_3$ se cancelam, pois assumem valores complementares).

    Produto final: $f(P_1, P_2, P_3) = P_1 + P_2$.

**Exemplos**

!!! example "Exemplo 1"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2032.png)

    Termo produto final: $f(x,y,z) = z'x' + x'y' + z'y'$

!!! example "Exemplo 2"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2033.png)

    Termo produto final: $f(x,y,z) = z'y' + x'$

!!! example "Exemplo 3"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2034.png)

    Termo produto final: $f(a,b,c,d) = ac'd + b'c$

!!! example "Exemplo 4"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2035.png)

    Termo produto final: $f(a,b,c,d) = cd + ad + b$

**Terminologia**

??? note "Imagens de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2036.png)

    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2037.png)

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2038.png)

### Exemplo — projetando circuitos a partir do mapa de Karnaugh

O objetivo é projetar os circuitos digitais para as funções abaixo, utilizando o mapa de Karnaugh para otimizá-los.

!!! example "Função 1"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2039.png)

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2040.png)

    **Mapa de Karnaugh**

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2041.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2042.png)

    Produto final: $f(a,b,c,d) = a'c + a'b + c'd + ac'$ (os termos $a'b$ e $c'd$ são primos não essenciais, logo podemos escolher apenas um deles para a solução mínima).

    !!! warning
        Esta tabela-verdade foi marcada no material original para revisão — pode conter um erro que ainda não foi verificado.

!!! example "Função 2"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2043.png)

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2044.png)

    **Mapa de Karnaugh**

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2045.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2046.png)

    Produto final: $f(a,b,c,d) = a'c + ac' + abcd$

    **Circuito correspondente**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2047.png)

### Clock

O **clock** é um tipo de sinal digital pulsante quadrado, que fornece a referência de tempo sincronizada para o funcionamento do circuito — ou seja, serve para manter o circuito sincronizado (são pulsos de sincronia). Como é um sinal quadrado, possui uma borda de descida e uma borda de subida, que podem ser usadas para acionar eventos dentro do circuito.

Em circuitos sequenciais, o clock serve para avisar quando o estado do circuito pode mudar, garantindo que a mudança ocorra de forma ordenada e controlada. O sinal de clock possui uma frequência medida em Hz (5 Hz = 5 pulsos por segundo); quanto maior a frequência, mais rápido as instruções são executadas.

### Flip-flop

Os **flip-flops** funcionam como elementos de memória, armazenando um único bit — podendo ter estado 0 ou 1 — e guardam esse estado até serem instruídos a mudar (geralmente por um sinal de clock, respondendo a uma borda de subida ou de descida). Por isso, são usados para armazenar e transferir dados.

Possuem uma ou duas entradas, e necessariamente duas saídas: $Q$ e $\overline{Q}$, que possuem estados opostos (quando $Q = 0$, $\overline{Q} = 1$, e vice-versa).

**Tipos de flip-flop**

=== "SR (Set-Reset)"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2048.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2049.png)

    Possui duas entradas: *set* ($S$) e *reset* ($R$).

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2050.png)

    Quando $S = 0$ e $R = 0$, o flip-flop mantém o estado anterior/inicial (se, antes do sinal entrar no flip-flop, $Q$ era 0, então permanece 0).

=== "JK"
    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2051.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2052.png)

    É, basicamente, um flip-flop SR aprimorado, com $J$ fazendo o papel de *set* e $K$ o de *reset*.

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2053.png)

    - Quando $J = 0$ e $K = 0$, $Q$ e $\overline{Q}$ mantêm o estado anterior.
    - `CLK` é o sinal de clock (nesse caso, acionado por borda de descida).
    - *Toggle* é o valor invertido do estado anterior: se antes $Q$ era 0, depois será 1.

    !!! example "Exemplo — contador decimal"
        ??? note "Imagens de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2054.png)

            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2055.png)

=== "D (Data)"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2056.png)

    Armazena em $Q$ o dado que foi colocado no pino $D$.

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2057.png)

=== "T (Toggle)"
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2058.png)

    É uma forma resumida do flip-flop JK, juntando as duas entradas $J$ e $K$ em uma única entrada $T$.

    **Tabela-verdade**

    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2059.png)

    - Quando $J = 0$ e $K = 0$, $Q$ e $\overline{Q}$ mantêm o estado anterior.
    - `CLK` é o sinal de clock (nesse caso, acionado por borda de descida).
    - *Toggle* é o valor invertido do estado anterior: se antes $Q$ era 0, depois será 1.

### Tipos de circuitos digitais

**Circuito combinacional** — tipo de circuito digital em que as saídas são determinadas exclusivamente pelas combinações das entradas presentes no momento, sem depender de qualquer estado anterior ou armazenamento de informações. Esses circuitos são baseados em operações lógicas que ocorrem instantaneamente em resposta às entradas, e não têm capacidade de memória.

!!! example
    ??? note "Imagem de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2060.png)

    **Tabela-verdade**

    ??? note "Imagens de referência"
        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2061.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2062.png)

        ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2063.png)

**Circuito sequencial** — tipo de circuito digital em que as saídas são determinadas tanto pelos valores das entradas presentes no momento quanto pelos valores de qualquer estado anterior (ou seja, o output depende do input atual e do input do estado anterior). Esses circuitos armazenam as informações dos estados passados em flip-flops, e possuem clocks:

- **Síncronos** — o clock controla diretamente as mudanças de estado nos flip-flops.
- **Assíncronos** — as mudanças de estado nos flip-flops não são controladas por um clock central, mas por sinais de controle específicos.

**Diferenças principais**: o circuito sequencial possui armazenamento de informações (armazena as informações do estado anterior); o circuito combinacional não possui clock nem flip-flops.

## Máquinas de Estados Finitos (FSM)

Uma **máquina de estados finitos (FSM)** é uma representação matemática de um sistema dependente do tempo, que possui estados e transições. Cada estado representa o sistema em um determinado momento no tempo, e não é possível que uma máquina de estados esteja em dois estados ao mesmo tempo. Quando a máquina está em um estado, ela aguarda que as condições para uma transição sejam atingidas e, assim que isso ocorre, muda para o estado indicado por essa transição, repetindo o ciclo. Toda máquina possui um estado inicial, onde a máquina começa, e pode ter um ou mais estados finais (ou de aceitação), indicando que a máquina terminou a tarefa computacional.

!!! note
    Tecnicamente, a máquina de estados finitos estudada em sistemas digitais é um **transdutor de estados finitos**. A diferença primária entre uma máquina de estados "pura" e um transdutor é que este último não possui um estado de aceitação.

Pode ser definida como uma tupla $(M, S, I, O, \delta, \lambda)$, onde:

- $M$ — o nome da máquina.
- $S$ — o conjunto finito de estados.
- $I$ — o conjunto finito de símbolos de entrada.
- $O$ — o conjunto finito de símbolos de saída.
- $\delta$ — a função de transição, um mapeamento de $S$ em função de $I$ (ou seja, $S \times I$) em $S$.
- $\lambda$ — a função de saída, um mapeamento de $S$ em função de $O$ (ou seja, $S \times O$) em $S$.

### Passo a passo para montar uma FSM

1. **Diagrama de estados** — forma de representação através de desenhos, usada para descrever a operação de um circuito, mostrando todos os estados individuais da máquina e as possíveis sequências de mudança de um estado para outro.

    !!! example
        ??? note "Imagem de referência"
            ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2064.png)

        No exemplo, $X$ é o valor da entrada, e o valor da saída $R$ indica onde a transição ocorre ($R = 0$: não ocorre; $R = 1$: ocorre a transição).

        !!! example "Exemplo de contador"
            ??? note "Imagem de referência"
                ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2065.png)

2. **Fazer a tabela-verdade.**
3. **Fazer o mapa de Karnaugh.**
4. **Fazer o circuito.**

### Tipos de FSM

**Máquina de estados de Moore** — as saídas dependem apenas do estado atual; as saídas só são atualizadas quando os estados variam (transições de estado não síncronas).

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2066.png)

É usada como controlador de semáforos, reconhecimento de padrões e detecção/correção de erros.

**Máquina de estados de Mealy** — as saídas dependem tanto das entradas quanto dos estados. Quando a entrada muda, as saídas são atualizadas imediatamente, sem esperar pelo clock. Esse modelo permite representar comportamentos mais complexos, que dependem da interação entre o estado interno e as entradas externas.

??? note "Imagem de referência"
    ![Untitled](../../assets/faculdade/periodo2/sistemas-digitais/Untitled%2067.png)

## Processador (visão geral de uma arquitetura MIPS simplificada)

!!! note
    Esta seção reúne anotações sobre os principais módulos de um processador didático baseado na arquitetura MIPS, cobrindo a ALU, as unidades de controle, as memórias, o *program counter*, o banco de registradores, o *sign extend* e os multiplexadores (MUX).

A **ALU** (*Arithmetic Logic Unit*) é responsável por realizar as operações aritméticas (`ADD`, `SUB`) e lógicas (`AND`, `OR`), além de operações como `SLT` (*set less than*) e a detecção de zero (usada, por exemplo, em operações de *branch*, definida por padrão). A ALU recebe o código binário `ALUControl`, gerado pela unidade de controle da ALU, e, com base nesse valor, realiza a operação correspondente.

A **unidade de controle da ALU** é responsável por captar os sinais binários `ALUOp` (opcode da ALU) e `funct` das instruções, e, com base neles, gerar o sinal `ALUControl`, que determina qual operação, entre as já implementadas na ALU, deve ser realizada. Primeiro verifica-se o valor de `ALUOp` e, com base nele, examina-se o campo `funct` para determinar a operação final:

- `ALUOp = 00` — operações de *load*/*store*.
- `ALUOp = 01` — operações de *branch*.
- `ALUOp = 10` — operações do tipo R (*R-type*); nesse caso, existe um `case` sobre o campo `funct` que define o `ALUControl` para cada operação R-type específica.

A **unidade de controle principal** é responsável por captar o *opcode* de cada instrução e, com base nele, definir os sinais de controle do processador como um todo. Ela coordena e controla todas as operações dentro do processador, garantindo que cada instrução seja lida da memória, interpretada e executada corretamente — gerando os sinais de controle necessários para que os demais módulos do processador saibam quais operações realizar e quando realizá-las. Isso é feito decodificando o *opcode* da instrução através de um `case` statement, e, para cada caso, os sinais de controle correspondentes são definidos para que os demais módulos trabalhem com base neles.

A **memória de dados** (*data memory*) é responsável por armazenar os dados necessários durante a execução das instruções, fornecer os dados armazenados para a execução de funções que dependem desses valores, e escrever novos dados. Em conjunto com o processador, a unidade de controle gera sinais de escrita na memória que, quando ativados, fazem com que a memória seja escrita nesse módulo; já a unidade de controle da ALU pode usar os dados armazenados na memória de dados para realizar suas operações. Na unidade de controle, as instruções `lw` e `sw` são as que interagem diretamente com essa memória: `sw` faz com que o sinal de escrita na memória seja 1, fazendo com que a memória seja escrita no módulo de *data memory*; já `lw` emite sinais para que os valores sejam lidos da memória.

A **memória de instruções** (*instruction memory*) armazena, de forma binária, todas as instruções do programa que o processador precisa executar, sendo lidas sequencialmente. Durante a execução, o processador lê as instruções da memória de instruções, e cada instrução é lida de um endereço específico, determinado pelo *program counter*. Essas instruções são fornecidas à unidade de controle, que as decodifica e gera os sinais correspondentes a cada uma.

O **program counter (PC)** interage diretamente com a memória de instruções, apontando para o endereço da próxima instrução a ser buscada; após a busca de uma instrução, o PC é atualizado para apontar para a próxima. A função do PC é armazenar o endereço da próxima instrução a ser buscada na memória de instruções; após cada busca, o PC é incrementado em 4, para apontar para a próxima instrução na sequência. No caso de instruções de `jump` e `beq`, o PC é atualizado com o novo endereço de destino, em vez de ser incrementado sequencialmente — o que permite a implementação de laços (*loops*) e funções no código em assembly. A unidade de controle utiliza o valor armazenado no PC para buscar a instrução correta na memória de instruções.

O **banco de registradores** (*register file*) tem a função de armazenar, de forma rápida e temporária, os dados que estão sendo usados ativamente por instruções durante a execução do programa. O módulo permite que o processador leia dados de registradores e escreva novos valores neles, e declara os 32 registradores existentes (já que a arquitetura é de 32 bits). De acordo com as instruções processadas pela unidade de controle e pela unidade de controle da ALU, é possível que dois registradores sejam lidos ao mesmo tempo — por exemplo, a instrução `add` lê os valores de dois registradores, soma-os e armazena o resultado em um registrador de destino. Esse módulo melhora a eficiência, pois o acesso a esses valores é muito mais rápido do que acessá-los diretamente na memória.

O **sign extend** tem a função de aumentar o número de bits de uma constante sem alterar o seu valor numérico, preservando o sinal do número. Por exemplo: as instruções do MIPS que utilizam constantes imediatas (`addi`, `subi`, `lw` e `sw`) frequentemente trabalham com valores de 16 bits, mas o processador é de 32 bits; logo, o *sign extend* expande esses valores para 32 bits, preservando o valor original e tornando-os mais fáceis de manipular. O *sign extend* recebe as instruções que utilizam constantes imediatas e as estende: quando uma instrução é buscada na memória usando o endereço do PC, ela é decodificada pela unidade de controle, e, se essa instrução utilizar uma constante imediata, o *sign extend* estende esse valor de 16 bits para 32 bits.

O **MUX** (multiplexador) tem a função de selecionar, entre várias entradas de dados, uma delas para ser a saída, com base em sinais de controle; o número de entradas e o tamanho de cada uma depende do parâmetro `WIDTH`. No MIPS, o MUX é usado para redirecionar dados entre diferentes componentes do processador:

- Existe um MUX na unidade de controle da ALU — por exemplo, para selecionar entre o valor de um registrador (no caso de `add`) e um valor imediato (no caso de `addi`).
- No PC, o MUX pode escolher entre o próximo endereço sequencial ou um novo endereço, baseado em um `jump`, `jr` ou `beq`.
- Existe um MUX para a memória de dados: quando os dados precisam ser lidos da memória, o MUX pode selecionar qual endereço usar (por exemplo, no caso de `lw`); e, quando os resultados de uma operação precisam ser escritos de volta nos registradores, o MUX pode selecionar entre os resultados da ALU, os dados lidos da memória, ou valores imediatos.

---

Ver também: [Assembly](sistemas-digitais/assembly.md)
