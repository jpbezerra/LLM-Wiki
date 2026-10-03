# COMPILADORES

!!! info "Referências do curso"
    - [Playlists do professor Leopoldo Teixeira (CIn/UFPE)](https://www.youtube.com/@LeopoldoTeixeiraCInUFPE/playlists)
    - [Material do curso IF688](https://if688.github.io)
    - [Repositório do curso no GitHub](https://github.com/if688/if688.github.io/tree/master)

## Conceitos

Uma **linguagem** é um sistema de comunicação baseado em símbolos e regras — essencial para qualquer forma de comunicação, humana ou não. A pergunta que motiva toda essa disciplina é: como expressar uma linguagem que o computador entenda? A resposta prática são as **linguagens de programação**.

Antes que um programa possa ser executado, é preciso traduzi-lo para algo que o computador consiga realmente processar. Essa tradução é feita por um **compilador**: um programa cuja função é traduzir de uma **linguagem fonte** para uma **linguagem alvo**.

Existem linguagens que fazem esse processo de compilação explicitamente, antes de executar o programa — chamadas de **linguagens compiladas**:

![image.png](../../assets/faculdade/periodo4/compiladores/image.png)

Ao ser compilado, o programa alvo se torna um executável. Já existem linguagens que abstraem completamente essa etapa de compilação e executam o programa diretamente — chamadas de **linguagens interpretadas**:

![image.png](../../assets/faculdade/periodo4/compiladores/image%201.png)

E existem linguagens que misturam as duas abordagens, usando um programa intermediário e uma máquina virtual para executar os programas: um tradutor gera um **código intermediário**, e uma máquina virtual executa esse código.

![image.png](../../assets/faculdade/periodo4/compiladores/image%202.png)

!!! tip "Dividir para conquistar"
    Os compiladores não tentam traduzir o código inteiro de uma só vez — eles aplicam a estratégia de "dividir para conquistar", quebrando o processo em módulos independentes. Por isso, todo compilador possui duas grandes fases: **análise** e **síntese**.

---

## Fases da Compilação

O **Front End** corresponde à fase de análise, e o **Back End** à fase de síntese:

![image.png](../../assets/faculdade/periodo4/compiladores/image%203.png)

## Análise

A fase de análise transforma o código fonte textual em uma **representação intermediária (IR)** válida, correta e livre de erros, para que o compilador consiga entender e trabalhar com o programa. Ela se divide em três etapas sequenciais: léxica, sintática e semântica.

### Análise Léxica (Scanner)

O **analisador léxico** (ou *scanner*) converte o texto do programa em **tokens**, identificando a estrutura básica do código — cada token pode carregar um valor associado.

![image.png](../../assets/faculdade/periodo4/compiladores/image%204.png)

**Terminologia fundamental:**

| Termo | Definição |
| --- | --- |
| **Token** | Par formado pelo nome do token e atributos opcionais; os tipos de token são especificados por meio de expressões regulares. |
| **Lexema** | A sequência de caracteres concreta que casa com o padrão de um tipo de token. |
| **Padrão** | A descrição dos possíveis lexemas associados a um tipo de token. |

O projetista do compilador caracteriza o analisador léxico por meio de **expressões regulares (ERs)** — a geração do analisador léxico a partir dessas ERs pode ser automatizada.

#### Expressões regulares

Uma expressão regular é um formalismo denotacional definido a partir de conjuntos básicos, concatenação e união. Os operadores regulares fundamentais são:

| Operador | Significado | Exemplo |
| --- | --- | --- |
| `.` | Reconhece qualquer caractere exceto `\n` | `a.c` → `abc`, `aac`, `acc`, `a9c`, etc. |
| `*` | Zero ou mais repetições de `r` | `r*` reconhece `""`, `"r"`, `"rr"`, etc. |
| `+` | Uma ou mais repetições | ![image.png](../../assets/faculdade/periodo4/compiladores/image%205.png) |
| `?` | Zero ou uma ocorrência (opcional) | ![image.png](../../assets/faculdade/periodo4/compiladores/image%206.png) |
| `\|` | "Ou" | `r1 \| r2` → `r1` ou `r2` |

Também existem **classes de caracteres**:

![image.png](../../assets/faculdade/periodo4/compiladores/image%207.png)

A notação `[^xyz]` significa qualquer caractere **exceto** `x`, `y` e `z` — por exemplo, `[^0-9]` casa qualquer caractere que não seja dígito.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%208.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%209.png)

Para implementar um analisador léxico, é preciso: definir a **microssintaxe** da linguagem (tokens e lexemas), estabelecer critérios de separação e agregação de palavras, definir palavras especiais/reservadas, e implementar o analisador a partir dessa especificação.

!!! example "Especificações léxicas"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2010.png)
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2011.png)

#### Reconhecimento de tokens

Para reconhecer os tokens, constrói-se **diagramas de transição** e, em seguida, implementa-se uma máquina de estados que combina esses diagramas.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2012.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2013.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2014.png)

O **lexer** interage diretamente com o **parser**, o que ajuda no reconhecimento de erros mais cedo no pipeline:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2015.png)

### Análise Sintática (Parser)

O **parser** usa os tokens gerados pela análise léxica para construir uma **árvore sintática**, verificando se a estrutura do código segue a gramática da linguagem. Cada nó interno da árvore representa uma operação, e seus filhos representam os argumentos dessa operação. A análise sintática serve, portanto, para detectar erros de **estrutura**.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2016.png)

Há três desfechos possíveis: (1) o parsing ocorre perfeitamente, e a sintaxe do programa está correta; (2) ocorre um erro de sintaxe (violação das regras gramaticais); (3) independentemente do caso, o programa ainda pode conter erros que só serão capturados (ou não) pelo *type checker* na análise semântica.

#### Gramáticas livres de contexto

A **gramática livre de contexto (GLC)** caracteriza a linguagem, e o parser pode ser gerado automaticamente a partir dela — para cada classe gramatical da GLC, existirá uma estrutura de dados correspondente no compilador.

Derivamos palavras de uma gramática $G$ a partir do seu símbolo inicial, substituindo repetidamente não-terminais pelo corpo de uma produção. A linguagem gerada por $G$, denotada $L(G)$, inclui todas as strings obtidas através de derivações em $G$.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2017.png)

**Expressões regulares vs. gramáticas livres de contexto.** Tudo que pode ser escrito com uma ER também pode ser escrito com uma GLC, mas as ERs têm vantagens práticas importantes:

- regras léxicas são especificadas mais simplesmente com ER;
- ERs geralmente são mais concisas e simples;
- é possível gerar analisadores léxicos mais eficientes a partir de ERs;
- isso estrutura/modulariza o front-end do compilador.

Na prática, ERs são convenientes para especificar a estrutura de construções léxicas (identificadores, constantes, palavras-chave), enquanto gramáticas são usadas para especificar estruturas **aninhadas** (parênteses balanceados, `begin`-`end`, `if`-`then`-`else`, etc.).

**Derivação**: dada uma gramática $G$, produz uma string $s \in L(G)$.

![image.png](../../assets/faculdade/periodo4/compiladores/image%2018.png)

#### Parsing

Dada uma string $s \in L(G)$, o **parsing** produz uma árvore sintática que demonstra como obter uma derivação de $s$:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2019.png)

Para gramáticas livres de contexto, é sempre possível construir um parser com complexidade $O(n^3)$ para processar $n$ tokens — mas, na prática, o parsing de linguagens de programação normalmente pode ser feito **linearmente**, com uma travessia da esquerda para a direita, olhando um token por vez.

!!! note "O marcador de fim de arquivo"
    Parsers devem ler não apenas os símbolos terminais, mas também o marcador de fim de entrada. Usa-se `$` para representá-lo, e costuma-se aumentar a gramática com uma produção extra $S' \to S\$$.

Existem três grandes categorias de métodos de parsing: os **métodos universais** (funcionam para qualquer gramática, mas são ineficientes demais para uso prático), os métodos **top-down**, e os métodos **bottom-up**.

### Parsing Top-Down

Métodos top-down constroem a árvore sintática a partir da **raiz**, em direção às folhas. O método geral é:

1. A partir do símbolo inicial da gramática, consumir tokens da esquerda para a direita.
2. Decidir qual produção aplicar, de acordo com o token lido.
3. Continuar até que um dos casos a seguir se torne verdadeiro:
    - todas as folhas são símbolos terminais e não há mais tokens a ler;
    - ocorre uma incompatibilidade entre a entrada e as folhas da árvore parcialmente construída — nesse caso, usa-se **backtracking**, restaurando o estado anterior à última escolha.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2020.png)

#### Backtracking e parsing preditivo

Backtracking é indesejável — causa ineficiência de código, principalmente em parsers top-down com derivação mais-à-esquerda. A solução ideal é realizar um **parsing preditivo (predictive parsing)**: o token lido como próximo terminal deve fornecer informação suficiente para decidir, sem ambiguidade, qual produção aplicar.

Duas situações geram problemas para o parsing preditivo: **recursão à esquerda** e **ambiguidade**.

**Recursão à esquerda.** Uma gramática é recursiva à esquerda se existe um não-terminal $A$ tal que $A$ deriva $A\alpha$ para alguma string $\alpha$. Existem técnicas para eliminar essa recursão automaticamente:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2021.png)

- **Reescrever as produções, tornando-as recursivas à direita:** ![image.png](../../assets/faculdade/periodo4/compiladores/image%2022.png)

    !!! example
        ![image.png](../../assets/faculdade/periodo4/compiladores/image%2023.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2024.png)

- **Fatoração à esquerda**: técnica de transformação de gramática que combina os casos em que há mais de uma alternativa a partir do reconhecimento de um único token (existem algoritmos sistemáticos para realizá-la).

    !!! example
        ![image.png](../../assets/faculdade/periodo4/compiladores/image%2025.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2026.png)

        Solução: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2027.png)

**Ambiguidade.** Uma gramática é dita **ambígua** quando gera mais de uma árvore sintática para a mesma string — e a interpretação do programa pode mudar dependendo de qual estrutura foi derivada.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2028.png)

#### Gramática preditiva (LL(1))

Uma **gramática preditiva** é uma gramática **LL(1)**: o primeiro **L** significa que o parser lê a entrada da esquerda para a direita; o segundo **L** significa que ele produz uma derivação mais-à-esquerda (*leftmost*); e o **(1)** significa que usa exatamente 1 símbolo de *lookahead* para decidir qual regra aplicar.

Uma gramática LL(1) precisa ser:

- **não ambígua** — cada entrada (símbolo terminal) leva a, no máximo, uma produção possível;
- **não recursiva à esquerda** — não pode ter produções que começam com o próprio não-terminal;
- **fatorada à esquerda** — se duas produções do mesmo não-terminal começam com o mesmo prefixo, esse prefixo precisa ser extraído.

![image.png](../../assets/faculdade/periodo4/compiladores/image%2029.png)

A construção de parsers top-down (e também bottom-up) é auxiliada pelos conjuntos **FIRST** e **FOLLOW**, que ajudam o parser a decidir qual produção aplicar com base no próximo símbolo de entrada. A classe LL(1), apesar de restrita, é rica o suficiente para cobrir a maioria das construções de linguagens de programação reais.

**FIRST.** $\text{FIRST}(\alpha)$, onde $\alpha$ é qualquer string de símbolos da gramática, é o conjunto de terminais que podem iniciar strings derivadas a partir de $\alpha$. Se $\alpha$ pode gerar $\varepsilon$, então $\varepsilon \in \text{FIRST}(\alpha)$.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2030.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2031.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2032.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2033.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2034.png)

*Como calcular $\text{FIRST}(X)$:*

- se $X$ é terminal, $\text{FIRST}(X) = \{X\}$;
- se $X \to \varepsilon$, então $\varepsilon \in \text{FIRST}(X)$;
- se $X \to Y_1Y_2\ldots Y_k$, então $\text{FIRST}(Y_1Y_2\ldots Y_k) \subseteq \text{FIRST}(X)$, onde $\text{FIRST}(Y_1Y_2\ldots Y_k)$ é:
    - $\text{FIRST}(Y_1)$, se $\varepsilon \notin \text{FIRST}(Y_1)$;
    - $(\text{FIRST}(Y_1) \setminus \{\varepsilon\}) \cup \text{FIRST}(Y_2\ldots Y_k)$, se $\varepsilon \in \text{FIRST}(Y_1)$;
    - e $\varepsilon \in \text{FIRST}(Y_1Y_2\ldots Y_k)$ se $\varepsilon \in \text{FIRST}(Y_j)$ para todo $j$ de $1$ a $k$.

**FOLLOW.** $\text{FOLLOW}(A)$, onde $A$ é um não-terminal, é o conjunto de terminais $a$ que podem aparecer imediatamente à direita de $A$ em alguma derivação. Se $A$ pode ser a produção mais à direita da gramática, então $\$ \in \text{FOLLOW}(A)$.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2035.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2036.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2037.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2038.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2039.png)

*Como calcular $\text{FOLLOW}(A)$:*

- $\$ \in \text{FOLLOW}(S)$, onde $S$ é o símbolo inicial;
- se existe produção $A \to \alpha B \beta$, tudo que está em $\text{FIRST}(\beta)$ exceto $\varepsilon$ está em $\text{FOLLOW}(B)$;
- se existe produção $A \to \alpha B$, tudo que está em $\text{FOLLOW}(A)$ está em $\text{FOLLOW}(B)$;
- se existe produção $A \to \alpha B \beta$ e $\varepsilon \in \text{FIRST}(\beta)$, tudo que está em $\text{FOLLOW}(A)$ está em $\text{FOLLOW}(B)$.

#### LL(1) table-driven parsing

A **tabela de parsing** diz qual ação tomar com base no estado atual e no próximo símbolo de entrada — representada como uma matriz bidimensional $M[A, a]$, onde $A$ é não-terminal e $a$ é terminal (incluindo `$`), construída a partir de FIRST e FOLLOW:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2040.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2041.png)

**Algoritmo de construção da tabela:**

1. Para cada produção $A \to \alpha$ de $G$:
    - para todo $a \in \text{FIRST}(\alpha)$, adicione $A \to \alpha$ em $M[A, a]$;
    - se $\varepsilon \in \text{FIRST}(\alpha)$, então, para todo $b \in \text{FOLLOW}(A)$ (incluindo `$`), adicione $A \to \alpha$ em $M[A, b]$.
2. Posições em branco na tabela representam **erro**.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2042.png)

#### Gramática LL(1): definição formal e exemplos

$G$ é LL(1) se, e somente se, para quaisquer duas produções distintas $A \to \alpha \mid \beta$:

1. para nenhum terminal $a$, tanto $\alpha$ quanto $\beta$ geram palavras iniciadas em $a$;
2. no máximo um de $\alpha, \beta$ deriva a palavra vazia;
3. se $\beta$ deriva $\varepsilon$, $\alpha$ não pode derivar palavras iniciadas com terminais de $\text{FOLLOW}(A)$;
4. se $\alpha$ deriva $\varepsilon$, $\beta$ não pode derivar palavras iniciadas com terminais de $\text{FOLLOW}(A)$.

!!! example "A gramática é LL(1)?"
    **1.** ![image.png](../../assets/faculdade/periodo4/compiladores/image%2043.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2044.png)

    Não — a produção $A \to Abc$ é recursiva à esquerda. Além disso, $\text{FIRST}(Abc)$ contém $\text{FIRST}(A) = \{b\}$, o que faria $M[A, b]$ conter duas produções simultaneamente.

    **2.** ![image.png](../../assets/faculdade/periodo4/compiladores/image%2045.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2046.png)

    $\text{FIRST}(eS) = \{e\}$, logo $M[S', e] = S' \to eS$. Porém, como $\varepsilon \in \text{FIRST}(\varepsilon)$, é preciso olhar $\text{FOLLOW}(S') = \{\$, e\}$: para `$`, $M[S', \$] = S' \to \varepsilon$; para `e`, $M[S', e] = S' \to \varepsilon$ — mas $M[S', e]$ já contém $S' \to eS$, gerando um **conflito**. Logo, **não** é LL(1).

!!! example "Exemplo completo"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2047.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2048.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2049.png)

#### Parsing preditivo não recursivo

Um parser preditivo **não recursivo** pode ser construído mantendo uma pilha explícita, em vez de usar chamadas recursivas implícitas. Se $w$ é a entrada já casada, a pilha mantém uma sequência de símbolos da gramática $\alpha$ tal que $S \Rightarrow^* w\alpha$.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2050.png)

#### Recursive-descent parsing

É um método de análise sintática top-down em que um conjunto de **procedimentos recursivos** processa a entrada — cada procedimento associado a um não-terminal da gramática. O parsing preditivo é um caso especial de recursive-descent parsing, em que o símbolo de lookahead determina, sem ambiguidade, qual procedimento chamar para cada não-terminal.

### Parsing Bottom-Up

Métodos bottom-up constroem a árvore sintática a partir das **folhas**, com a ideia de converter o programa de entrada no símbolo inicial. O parser lê tokens até encontrar uma subpalavra $w$ que case com o lado direito de uma produção $A \to w$; ao chegar nesse ponto, substitui $w$ por $A$, se isso resultar em uma derivação válida. Essa substituição é chamada de **redução**.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2051.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2052.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2053.png)

Formalmente, uma redução transforma a entrada $uwv$ em $uAv$ se $A \to w$ é uma produção da gramática.

#### Handles

Um **handle** é uma substring $w$ e uma produção $A \to w$ tal que, reduzindo $uwv \to uAv$, ainda é possível alcançar o símbolo inicial a partir de $uAv$ — ou seja, é uma redução que pode ser aplicada sem causar um beco sem saída.

!!! warning "Um \"falso\" handle"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2054.png)

#### Análise shift-reduce

A ideia central é dividir a entrada em duas partes, separadas por um marcador `|` (ou `•`): à direita, terminais ainda não reduzidos; à esquerda, terminais e não-terminais já processados. A parte mais à direita da substring esquerda (ou imediatamente adjacente ao marcador) contém o candidato a handle. Handles e reduções só ocorrem dentro da substring esquerda; a direita contém apenas terminais ainda não vistos.

A cada passo, é preciso decidir entre duas ações:

- **Shift**: desloca o foco para a direita, "jogando" um terminal para a substring esquerda. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2055.png)
- **Reduce**: aplica uma redução a um handle. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2056.png)

Se nenhuma das duas ações for possível, há um **erro sintático**.

#### Shift-reduce parsing com pilha

Toda redução ocorre na parte mais à direita da substring esquerda — representando-a como uma **pilha**, o `shift` empilha um token, e o `reduce` desempilha os símbolos de $w$ (reduzindo $A \to w$) e empilha $A$ em seu lugar. A redução ocorre quando o conteúdo do topo da pilha corresponde exatamente a um handle:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2057.png)

Para reconhecer handles, observa-se tanto a pilha quanto o lookahead:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2058.png)

!!! tip "Prefixos viáveis são regulares"
    O conjunto de prefixos viáveis de uma gramática forma uma **linguagem regular** — por isso é possível usar AFDs para determinar se o conteúdo da pilha corresponde a um prefixo viável.

#### Gramáticas LR(0)

Toda gramática **LR(0)** pode ser analisada por um shift-reduce parser. A classificação do nome segue a convenção:

- **L** → lê a entrada da esquerda para a direita;
- **R** → procura a derivação mais à direita;
- **(k)** → número de tokens de lookahead lidos, mas não consumidos.

Uma gramática LR(0) pode ser processada olhando **apenas** o conteúdo da pilha, sem usar lookahead para decidir entre shift e reduce — é, por isso, uma classe razoavelmente **fraca** de gramáticas, mas o algoritmo de construção de tabelas LR(0) é uma introdução valiosa aos algoritmos LR(1).

!!! example "Construção da tabela de parsing LR(0)"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2059.png)

    Regras de notação: `sn` → shift e vá para o estado $n$; `gn` → vá para o estado $n$ (goto); `rk` → reduza pela regra $k$; `a` (accept) → aceite a entrada; células vazias → erro.

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2060.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2061.png)

**Executando o parsing.** Em vez de reescanear a pilha inteira a cada token, pode-se lembrar o estado alcançado em cada elemento da pilha — o algoritmo olha apenas o estado no topo da pilha e o símbolo de entrada atual para decidir a ação:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2062.png)

!!! example "Trace completo de execução"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2063.png)

    1. Empilha o estado 1 inicialmente. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2064.png)
    2. $M[1, (] = s3$ — empilha o estado 3. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2065.png)
    3. $M[3, x] = s2$ — empilha o estado 2. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2066.png)
    4. $M[2, {,}] = r2$ — reduz pela regra 2, substituindo `x` por `S`, volta ao estado 3; $M[3, S] = g7$, empilha 7. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2067.png)
    5. $M[7, {,}] = r3$ — reduz pela regra 3, substituindo `S` por `L`, desempilhando 7 e voltando ao estado 3; $M[3, L] = g5$, empilha 5. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2068.png)
    6. $M[5, {,}] = s8$ — empilha o estado 8. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2069.png)
    7. $M[8, x] = s2$ — empilha o estado 2. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2070.png)
    8. $M[2, )] = r2$ — reduz `x` para `S`, desempilhando 2 e voltando a 8; $M[8, S] = g9$, empilha 9. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2071.png)
    9. $M[9, )] = r4$ — reduz `(L, S)` para `L`, desempilhando 9, 8 e 5 (3 símbolos), voltando a 3; $M[3, L] = g5$, empilha 5. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2072.png)
    10. $M[5, )] = s6$ — empilha o estado 6. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2073.png)
    11. $M[6, \$] = r1$ — reduz `(L)` para `S`, desempilhando 6, 5 e 3 (3 símbolos), voltando a 1; $M[1, S] = g4$, empilha 4. ![image.png](../../assets/faculdade/periodo4/compiladores/image%2074.png)
    12. $M[4, \$] = a$ — **aceita** a entrada.

**Conflitos.** Problemas na gramática, ou limitações da técnica escolhida, podem gerar conflitos na construção da tabela:

- **shift-reduce**: o parser não consegue decidir entre uma ação de shift (ou mais de uma) ou de reduce;
- **reduce-reduce**: não há como decidir entre duas ou mais ações de reduce — geralmente por ambiguidade na gramática, ou algum erro de projeto.

!!! example "Exemplo de conflito shift-reduce em $M[1, +]$"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2075.png)

#### Análise SLR

Para resolver esses conflitos, usa-se a análise **SLR (Simple LR)**, que utiliza o conjunto FOLLOW: a intuição é só reduzir se o próximo token (lookahead) estiver no conjunto FOLLOW do não-terminal associado à produção. Na tabela de parsing, inclui-se uma ação de reduce apenas se o terminal estiver no FOLLOW correspondente.

Nos autômatos SLR, estados podem conter mais de um item de redução, caso os conjuntos FOLLOW envolvidos sejam distintos entre si, e podem misturar itens de shift com itens de redução, caso os terminais de shift não estejam no FOLLOW dos itens de redução. Mas isso **não elimina todos os tipos de conflito**:

![image.png](../../assets/faculdade/periodo4/compiladores/image%2076.png)

Para um poder de análise ainda maior, existem as gramáticas **LR(1)**.

#### Gramáticas LR(1)

LR(1) é mais poderoso que SLR, e suficiente para cobrir boa parte das linguagens de programação do mundo real. A noção de **item** é mais sofisticada, incluindo o símbolo de lookahead explicitamente. O parser LR(1) simula dois processos simultaneamente:

1. o autômato LR(0) subjacente, para encontrar handles;
2. um rastreador de tokens de lookahead, para determinar qual o lookahead atual.

!!! note
    Remover os lookaheads de um autômato LR(1) produz um autômato LR(0) correto, mas **muito maior**, para a mesma gramática.

**Construção do autômato LR(1):**

![image.png](../../assets/faculdade/periodo4/compiladores/image%2077.png)

!!! example "Construção passo a passo"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%2078.png)

    Passo 1 (pode-se incrementar o conjunto dentro dos colchetes, como $S \to \bullet[\$, +]$): ![image.png](../../assets/faculdade/periodo4/compiladores/image%2079.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2080.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2081.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2082.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2083.png)

    Passo 2: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2084.png)

    Passo 3: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2085.png)

    Passo 4: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2086.png)

    Passo 5: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2087.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2088.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2089.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2090.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2091.png)

    Passo 6: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2092.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2093.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2094.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2095.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2096.png)

    Passo 7: ![image.png](../../assets/faculdade/periodo4/compiladores/image%2097.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2098.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%2099.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20100.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20101.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20102.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20103.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20104.png)

    Passo 8: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20105.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20106.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20107.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20108.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20109.png)

    Passo 9: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20110.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20111.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20112.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20113.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20114.png)

    **Autômato final:** ![image.png](../../assets/faculdade/periodo4/compiladores/image%20115.png)

    **Tabela de parsing resultante:** ![image.png](../../assets/faculdade/periodo4/compiladores/image%20116.png)

### Análise Semântica

A análise semântica valida o **significado** das expressões, detectando erros mais profundos — não mais sobre a *forma* do código, mas sobre o seu *sentido*. Usa a árvore sintática e a tabela de símbolos para checar a consistência semântica com a definição da linguagem (a linguagem pode permitir **coercions**: conversões automáticas entre tipos compatíveis). Uma vez que essa fase termina com sucesso, o programa de entrada é considerado válido. O maior desafio é um equilíbrio: rejeitar o maior número possível de programas incorretos, acertando o maior número possível de programas corretos.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20117.png)

!!! note "Limitações das GLCs"
    Uma gramática livre de contexto, por si só, não consegue responder perguntas como: como prevenir definições de classes duplicadas? Como diferenciar variáveis de um tipo das de outro tipo? Como garantir que uma classe implementa todos os métodos de uma interface? É justamente para isso que servem a análise semântica e a tabela de símbolos.

#### Árvores Sintáticas Abstratas (AST)

A **AST** sintetiza as informações de uma árvore sintática (*parse tree*), focando nas informações importantes e classificando os nós de acordo com seu papel na estrutura da linguagem — é uma representação mais compacta que facilita o trabalho do compilador. Usa-se a AST para criar estruturas de dados em código; idealmente, para toda AST existe um **interpretador** que executa as ações representadas por cada nó, geralmente implementado como uma função recursiva que mantém o estado do programa.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20118.png)

    Árvore sintática (parse tree) completa: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20119.png)

    AST correspondente, mais compacta: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20120.png)

**Direções de modularidade** na organização do front-end: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20121.png)

**Visitor Design Pattern.** É um padrão de modelagem para ASTs que centraliza as funcionalidades em um objeto *Visitor*, que encapsula as operações sobre a AST e recebe a própria árvore como parâmetro de suas funções. Sua finalidade é separar os algoritmos das estruturas de dados sobre as quais operam, permitindo adicionar novas operações a uma estrutura complexa sem precisar modificar as classes dos objetos que a compõem.

#### Checagem de tipos (Type-Checking)

Um **tipo** é uma categoria de elementos de programação. A checagem de tipos é o primeiro passo propriamente dito da análise semântica, composta por duas atividades: **inferência de tipos** e **checagem** propriamente dita — que pode ser feita de forma **estática** (em tempo de compilação) ou **dinâmica** (em tempo de execução).

**Sistema de tipos.** É a coleção de regras que limitam como um programa pode ser escrito, garantindo segurança em tempo de execução; a checagem de tipos verifica se essas regras estão sendo respeitadas. Um sistema é **strong** (fortemente tipado) se nunca permite erros de tipo passarem sem detecção, e **weak** (fracamente tipado) se pode permitir alguns.

**Componentes de um sistema de tipos:**

- **Built-in**: tipos pré-definidos para grupos de dados comuns (números, booleanos, caracteres), que variam entre linguagens.
- **Tipos compostos**: formados por um ou mais objetos, cada um com seu próprio tipo (arrays, strings, enums). É possível criar *structures* (records) que agrupam múltiplos objetos de tipos arbitrários; ponteiros são um tipo especial, capaz de manipular memória diretamente; e novos tipos podem ser criados a partir de tipos já existentes.
- **Equivalência de tipos**: toda linguagem precisa de regras sem ambiguidade para decidir se dois tipos diferentes são equivalentes:
    - **Name equivalence**: dois tipos são equivalentes **sse** têm o mesmo nome — se o programador escolheu nomes diferentes, a linguagem respeita essa escolha. A complexidade de gerenciar essa consistência de nomes cresce com o tempo.
    - **Structural equivalence**: dois tipos são equivalentes se têm a **mesma estrutura** — dois objetos podem ser trocados se têm o mesmo conjunto de campos, na mesma ordem, com tipos equivalentes. Examina as propriedades essenciais que definem o tipo, não seu nome.
- **Regras de inferência**: envolvem os tipos dos operandos e o tipo do resultado de uma expressão (por exemplo, em expressões aritméticas, os tipos dos dois lados de um operador precisam ser compatíveis). Misturar tipos incompatíveis em uma expressão pode ser ilegal, podendo até impedir a compilação — ou o compilador pode aplicar conversões implícitas (*coercions*). Muitas linguagens exigem declaração de variáveis antes do uso, estabelecendo tipos bem definidos desde o início; linguagens que não exigem isso tornam a inferência de tipos mais complexa. A inferência de tipos de expressões normalmente segue a estrutura sintática da própria expressão, e pode depender de procedimentos/funções do programa — por isso, funções normalmente definem **assinaturas de tipo** explícitas.

#### Gramática de atributos

É um formalismo para realizar análise sensível ao contexto, enriquecendo uma GLC com regras que especificam computações: cada regra define um atributo em termos dos valores de outros atributos.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20122.png)

    O atributo `type` é **sintetizado** (calculado a partir dos filhos), e o atributo `in` é **herdado** (definido em termos de nós ancestrais, irmãos, etc.):

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20123.png)

!!! example "Exemplo completo com extensão incremental de regras"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20124.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20125.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20126.png)

    Adicionando novas regras: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20127.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20128.png)

    Adicionando novas regras novamente: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20129.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20130.png)

#### Escopo

Um mesmo nome pode ter diferentes significados dentro de um programa. **Abstração** é o processo que associa um nome a um fragmento de programa; **binding** é a associação entre o nome e a funcionalidade que ele nomeia, podendo ser feita em diferentes momentos da compilação.

O **escopo** é a região do programa onde o binding de um nome a uma entidade é válido e visível — ele determina onde se pode ver e usar uma variável ou função pelo seu nome. É possível fazer **shadowing**: quando o mesmo nome é usado em escopos diferentes, com significados distintos.

!!! example "Escopo em OO"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20131.png)

**Passadas (passes).** Análise léxica e sintática normalmente podem ser resolvidas com uma única passada sobre a entrada. Alguns compiladores também combinam análise semântica e geração de código na mesma passada — chamados de **single-pass compilers**. Outros fazem múltiplas passadas (**multi-pass compilers**): por exemplo, ler a entrada e construir a AST (1ª passada), caminhar pela AST coletando informações sobre classes (2ª passada), caminhar novamente checando outras propriedades (3ª passada)... Algumas dessas passadas podem ser combinadas, mesmo que sejam logicamente distintas — e, na prática, costumam ser implementadas usando o padrão *Visitor*.

#### Tabelas de símbolos

Uma **tabela de símbolos** é um mapeamento de nomes para a entidade a que esses nomes se referem. Ao processar declarações de tipos, variáveis e funções, associamos os identificadores a seu significado na tabela; ao processar usos desses identificadores, fazemos o *lookup* na tabela.

A implementação deve priorizar eficiência de acesso, e deve ser facilmente expansível. Em geral, implementa-se usando **hash tables**, possivelmente encadeadas conforme o nível de escopo.

!!! note "Spaghetti stacks"
    Uma forma de implementação trata a tabela de símbolos como uma **lista encadeada de escopos**: cada escopo armazena um ponteiro para seu ancestral, mas a recíproca não é verdadeira. Em qualquer ponto do programa, a tabela pode ser vista como uma pilha:

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20132.png)

    (Por exemplo, dois escopos irmãos no mesmo nível — "2b" e "2a" — são essencialmente *sibling nodes*, sem relação direta entre si, apenas com o ancestral comum.)

**Operações básicas da tabela de símbolos:**

![image.png](../../assets/faculdade/periodo4/compiladores/image%20133.png)

Como a maioria das linguagens permite declarar nomes em múltiplos níveis de escopo, a tabela de símbolos precisa se adaptar a essa hierarquia. O compilador precisa fazer **name resolution**, mapeando cada nome referenciado a seu nível de escopo correto; à medida que o compilador sai de um escopo, a tabela encadeada daquele nível é descartada. Isso exige operações adicionais para gerenciar mudanças de escopo:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20134.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20135.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20136.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20137.png)

    No nível 3, para calcular `b = a + b + c + w`, para cada variável o compilador busca o nome no escopo mais próximo do escopo atual: `a` → nível 2b; `b` → nível 1; `c` → nível 3; `w` → nível 0.

---

## Representação Intermediária (IR)

A **IR (Intermediate Representation)** é uma forma abstrata e independente de máquina do programa, que serve de ponte entre o front-end e o back-end. Pode ser uma árvore (AST simplificada), código de três endereços, um bytecode intermediário (LLVM IR, bytecode da JVM), etc. Durante a tradução, um compilador pode construir uma ou mais IRs do mesmo programa.

A separação em fases, junto ao uso de uma IR, traz vantagens práticas, teóricas e arquiteturais substanciais: a separação de fases melhora modularização, tratamento de erros e reuso de código do compilador; e o uso da IR melhora, sobretudo, **portabilidade**, **otimização** e independência tanto de linguagens quanto de máquinas, dando grande flexibilidade ao pipeline:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20138.png)

Compiladores modernos tipicamente usam mais de uma IR, intercaladas com *optimizers* — responsáveis por otimizar as IRs e melhorar o desempenho do programa final:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20139.png)

A IR sempre tenta se aproximar progressivamente da linguagem de máquina final:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20140.png)

Como o conhecimento derivado sobre o código precisa ser transmitido entre as passadas, o compilador precisa de uma representação dos fatos que ele deriva a partir do programa — essa representação precisa ser expressiva o suficiente para registrar tudo que é útil transmitir. Existem vários tipos de IR, e a escolha varia de compilador para compilador: Parse Trees, ASTs e DAGs, entre outras.

### DAG (Grafo Acíclico Dirigido)

Um **DAG** tem o objetivo de **eliminar subexpressões comuns**, resultando em código mais rápido e enxuto. Para construí-lo, lista-se primeiro os nós (cada um representando um operador ou uma variável) e uma tabela de símbolos que mapeia identificadores para o nó do DAG que contém o valor mais recente daquela variável. Para otimizar, realizam-se apenas as operações aritméticas que efetivamente correspondem a um nó.

![image.png](../../assets/faculdade/periodo4/compiladores/image%20141.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20142.png)

### Representações lineares

Como alternativa às representações gráficas, existem as **representações lineares**: sequências de instruções que executam em ordem, impondo uma sequência clara e útil — aproximando-se de código assembly para uma máquina abstrata. Geralmente precisam codificar mecanismos de transferência de controle entre pontos do programa (*jumps* e *conditional branches*).

| Tipo | Modela | Observação |
| --- | --- | --- |
| **One-address code** | Acumuladores e máquinas baseadas em pilha | Código bastante compacto. ![image.png](../../assets/faculdade/periodo4/compiladores/image%20143.png) |
| **Two-address code** | Máquinas com operações destrutivas | Perdeu popularidade com a redução das restrições de memória. |
| **Three-address code** | Máquinas onde a maioria das operações recebe dois operandos e produz um resultado (popularidade das arquiteturas RISC) | O mais usado como código intermediário hoje. |

**Three-address code (TAC)** abstrai um assembler onde cada instrução básica referencia no máximo 3 endereços, com no máximo um operador no lado direito de cada instrução — no formato `x := y op z`. Por exemplo, `x + y * z` é reescrito como:

```text
t1 := y * z
t2 := x + t1
```

**Instruções e operadores típicos de TAC:**

![image.png](../../assets/faculdade/periodo4/compiladores/image%20144.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20145.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20146.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20147.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20148.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20149.png)

**Estruturas de dados.** As instruções de três endereços podem ser representadas por objetos e/ou registros com campos para operadores e operandos. Uma estrutura comum é a **quadruple** ("quad"): contém quatro campos, `op`, `arg1`, `arg2` e `result`. Instruções com operadores unários não usam `arg2`; operadores como `param` não usam `arg2` nem `result`; desvios (jumps) colocam o rótulo (*label*) de destino em `result`.

![image.png](../../assets/faculdade/periodo4/compiladores/image%20150.png)

**Gerando código IR:**

![image.png](../../assets/faculdade/periodo4/compiladores/image%20151.png)

Com a ideia de fluxo de controle, é possível enriquecer a linguagem com estruturas de alto nível que se traduzem para TAC com jumps:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20152.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20153.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20154.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20155.png)

### Control-Flow Graph (CFG)

O **CFG** representa o fluxo de controle do programa, sendo bastante utilizado em análises de otimização, *instruction scheduling* e alocação global de registradores. Seus nós correspondem a **blocos básicos** de código, e as arestas representam a transferência de controle entre eles.

Um **bloco básico** é uma sequência de operações que sempre executam em conjunto — cada instrução de um bloco básico só executa depois que todas as instruções anteriores já executaram (não há pontos de entrada/saída intermediários):

![image.png](../../assets/faculdade/periodo4/compiladores/image%20156.png)

O CFG fornece uma representação gráfica dos caminhos possíveis do programa em tempo de execução (podendo conter caminhos que, na prática, são impossíveis de ocorrer de fato):

![image.png](../../assets/faculdade/periodo4/compiladores/image%20157.png)

**Construção.** Pode-se construir CFGs tanto para IR de alto nível (traduzindo cada nó de uma AST e compondo os resultados) quanto para IR de baixo nível (analisando labels e instruções de desvio em código de três endereços). O CFG de uma instrução de alto nível $S$, $\text{CFG}(S)$, é um grafo com entrada e saída simples, e pode ser definido **recursivamente**:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20158.png)

!!! example "Construção recursiva"
    Condicionais: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20159.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20160.png)

    Laço de repetição: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20161.png)

    Exemplo completo: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20162.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20163.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20164.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20165.png)

!!! warning "Ineficiência da construção recursiva ingênua"
    Esse algoritmo recursivo gera um CFG com muitos blocos pequenos, o que é ineficiente. Uma construção eficiente deve minimizar o número e o tamanho dos blocos:

    - não devem existir pares de blocos $(B_1, B_2)$ onde $B_2$ é sucessor único de $B_1$, $B_1$ tem apenas uma aresta de saída e $B_2$ tem apenas uma aresta de entrada (nesse caso, $B_1$ e $B_2$ deveriam ser fundidos em um só);
    - não devem existir blocos básicos vazios.

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20166.png)

**CFGs para código de três endereços (TAC):**

![image.png](../../assets/faculdade/periodo4/compiladores/image%20167.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20168.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20169.png)

---

## Otimização

A **otimização** realiza transformações no código com o objetivo de melhorar algum aspecto relevante (desempenho, tamanho, consumo de energia), podendo ser específica a uma arquitetura ou geral, e sem alterar o comportamento observável do programa. O foco da otimização recai sobre as IRs, buscando o máximo de melhoria com o mínimo de esforço de engenharia.

Toda transformação de otimização precisa satisfazer dois critérios:

- **Safety (segurança)**: corretude é o critério mais importante que o compilador deve satisfazer. Como saber que uma transformação é segura? O que, exatamente, é "o sentido" de um programa? (Perguntas que remetem de volta à semântica formal da linguagem.)
- **Profitability (benefício)**: qual a vantagem real de aplicar uma transformação como *loop unrolling*? Pode ser diminuir o número de iterações, evitar trabalho duplicado, ou reduzir a pressão sobre a memória (*memory bound*).

### Granularidade da otimização

| Nível | Escopo |
| --- | --- |
| **Local** | Aplicada a um bloco básico, isoladamente. |
| **Global (intra-procedural)** | Aplicada a um CFG inteiro (um procedimento/método completo). |
| **Inter-procedural** | Aplicada através das fronteiras entre métodos/procedimentos. |

### Otimizações locais

São a forma mais simples de otimização — não é necessário analisar o corpo completo do procedimento.

**Single Assignment Form.** Representação que facilita otimizações: muitas delas se simplificam se cada atribuição é feita a um temporário que ainda não apareceu no bloco básico. Código de três endereços pode ser reescrito nessa forma, conhecida como **Static Single Assignment (SSA)**.

!!! note "SSA"
    SSA é uma disciplina de nomes usada por muitos compiladores modernos para codificar informação sobre fluxo de controle e de dados dos valores — foi concebida especificamente para viabilizar otimizações de código. Na forma SSA, cada nome corresponde unicamente a um ponto específico de definição: cada nome é definido **exatamente uma vez**, e cada uso carrega, implicitamente, informação sobre onde o valor foi originado.

    Um programa está em SSA quando toda definição tem um nome distinto e todo uso se refere a uma única definição. Para transformar um programa em SSA, é necessário inserir funções especiais chamadas **phi ($\phi$)** nos pontos onde o fluxo de controle converge (por exemplo, após um `if`-`else`, onde uma variável pode ter sido definida em dois ramos diferentes).

    A propriedade de single-assignment permite ao compilador ficar alheio a diversas questões associadas ao tempo de vida dos valores: nomes nunca são redefinidos ou "mortos" — o valor está sempre disponível a partir de algum caminho do grafo.

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20170.png)

**Formas de otimização local:**

| Técnica | Descrição | Referência |
| --- | --- | --- |
| Simplificação algébrica | Reescreve expressões usando identidades algébricas (ex.: `x + 0 = x`). | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20171.png) |
| Constant folding | Avalia, em tempo de compilação, expressões cujos operandos são constantes conhecidas. | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20172.png) |
| Copy propagation | Substitui o uso de uma variável pelo valor que lhe foi copiado, eliminando a cópia intermediária. | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20173.png) |
| Copy propagation + Constant folding | As duas técnicas combinadas, aplicadas repetidamente. | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20174.png) |
| Eliminação de subexpressões comuns | Evita recalcular uma expressão já computada antes no mesmo bloco. | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20175.png) |
| Dead code elimination | Remove código cujo resultado nunca é usado. | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20176.png) |

!!! example "Exemplo de otimização encadeada"
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20177.png)

    1. Simplificação algébrica: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20178.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20179.png)
    2. Copy propagation: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20180.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20181.png)
    3. Constant folding: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20182.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20183.png)
    4. Common subexpression elimination: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20184.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20185.png)
    5. Copy propagation (novamente): ![image.png](../../assets/faculdade/periodo4/compiladores/image%20186.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20187.png)
    6. Dead code elimination: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20188.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20189.png)

#### Eliminando expressões redundantes

Suponha que queremos eliminar expressões redundantes de um bloco básico. Uma expressão $e$ é **redundante** em um ponto $p$ se já foi avaliada em **todos** os caminhos que levam a $p$.

![image.png](../../assets/faculdade/periodo4/compiladores/image%20190.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20191.png)

A otimização só pode ser aplicada se não for necessário reavaliar a expressão (*safety*); e é interessante substituir as avaliações redundantes por referências ao valor já computado anteriormente (*profitability*).

!!! note "Local Value Numbering"
    Técnica para implementar essa eliminação em código já em forma SSA. Faz uma travessia do bloco básico, atribuindo números distintos a cada valor que ele computa. A chave é escolher os números de forma que duas expressões $e_i$ e $e_j$ recebam o mesmo número **sse** os valores de seus operandos são, comprovadamente, iguais — usando *hashing* de operações para armazenar expressões já calculadas.

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20192.png)

### Otimizações globais

Operam sobre um procedimento (ou método) inteiro — ou seja, sobre um CFG completo — podendo modificar múltiplos blocos básicos simultaneamente:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20193.png)

Existem situações em que uma otimização aparentemente óbvia **não** pode ser aplicada com segurança, por causa de caminhos de execução que o compilador precisa considerar:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20194.png)

#### Data-flow analysis

Antes de aplicar uma otimização, é preciso localizar os pontos onde o programa pode ser modificado com segurança para melhor. Para coletar essa informação, o compilador usa alguma forma de **análise estática**: tipicamente, primeiro constrói-se o CFG via análise de fluxo de controle, e depois se analisa como os valores *fluem* através do código — a **análise de fluxo de dados** propriamente dita.

Essa análise é feita de forma **iterativa**: geralmente se constrói um conjunto de equações definidas sobre conjuntos, que descrevem como os dados são transferidos entre blocos básicos (**funções de transferência**). A solução dessas equações é obtida por um **algoritmo de ponto fixo**, simples e robusto.

**Corretude.** Para substituir o uso de `x` por uma constante `k`, é preciso garantir que, em **todos** os caminhos que levam a esse uso, a última atribuição a `x` tenha sido `x = k`. Chamamos essa condição de $\Phi$:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20195.png)

Checar essa condição não é trivial: ao quantificar sobre todos os caminhos, é preciso considerar loops e ramos condicionais — o que exige análise **global** (do CFG do método inteiro).

!!! warning "Algumas otimizações globais são indecidíveis"
    Otimizações globais em geral dependem de provar que uma propriedade $P$ vale em um ponto particular da execução — e provar $P$ em qualquer ponto exige, em princípio, conhecimento do corpo inteiro do método. Existem otimizações globais genuinamente **indecidíveis** em geral; por isso, a otimização só é aplicada quando se tem certeza absoluta (uma aproximação conservadora e segura).

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20196.png)

#### Global Constant Propagation

Em cada ponto do programa, associa-se um possível valor para cada variável `x`:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20197.png)

!!! example
    1. ![image.png](../../assets/faculdade/periodo4/compiladores/image%20198.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20199.png)
    2. ![image.png](../../assets/faculdade/periodo4/compiladores/image%20200.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20201.png)

Com a informação global disponível, a otimização em si é simples: basta inspecionar as propriedades `x = ?` associadas às instruções que usam `x`; se `x` for constante naquele ponto, substitui-se o uso de `x` pela própria constante. A ideia central é **transferir informação** de uma instrução para a próxima: para cada instrução $s$, computam-se $C_{in}(x, s)$ (valor de `x` imediatamente antes de $s$) e $C_{out}(x, s)$ (valor de `x` imediatamente depois de $s$).

A informação se propaga através de **funções de transferência** entre instruções, definidas por um conjunto de regras:

| Regra | Caso |
| --- | --- |
| 1 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20202.png) |
| 2 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20203.png) |
| 3 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20204.png) |
| 4 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20205.png) |

As regras 1 a 4 relacionam o `in` de uma instrução com o `out` da **mesma** instrução — propagando informação *dentro* de cada statement. Faltam regras relacionando o `out` de uma instrução com o `in` da instrução **seguinte**, para propagar informação *entre* os nós do CFG:

| Regra | Caso |
| --- | --- |
| 5 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20206.png) |
| 6 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20207.png) |
| 7 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20208.png) |
| 8 | ![image.png](../../assets/faculdade/periodo4/compiladores/image%20209.png) |

**Algoritmo:**

1. Para todo nó inicial (statement) $s$ do programa, defina $C_{in}(x, s) = \star$ (valor desconhecido/qualquer).
2. Em todos os demais pontos, defina inicialmente $C_{in}(x, s) = C_{out}(x, s) = \#$ — o valor `#` significa "até o momento, com o que sabemos, o controle não alcança este ponto". Isso garante que a análise consiga alcançar um ponto fixo.
3. Repita: para qualquer statement que não satisfaça as regras 1–8, atualize-o usando a regra apropriada — até que nenhuma mudança mais ocorra.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20210.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20211.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20212.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20213.png)

O algoritmo **termina** porque a relação entre `*`, os valores constantes, e `#` forma uma relação de ordem (um reticulado, *lattice*) de altura finita — garantindo que o processo iterativo converge:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20214.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20215.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20216.png)

### Otimização: análise e transformação

Toda otimização se divide em duas etapas:

- **Análise**: determina onde o compilador pode aplicar otimizações de forma segura e benéfica (análise de fluxo de dados, análise de dependências);
- **Transformação**: usa os resultados da análise para efetivamente reescrever o código de forma mais eficiente.

Diferentes otimizações variam em efeito, escopo, e na quantidade de análise necessária para habilitá-las com segurança.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20217.png)

---

## Síntese

A fase de síntese é responsável por gerar o código alvo final — binário ou bytecode.

### Ambiente de execução

Um compilador precisa implementar precisamente as abstrações definidas pela linguagem fonte: nomes, operadores, escopo, bindings, e assim por diante. Isso é feito cooperando com o sistema operacional e outros softwares para dar suporte a essas abstrações — o compilador cria, nesse processo, um **ambiente de execução** no qual assume que os programas serão executados.

#### Organização da memória

O programa tem seu próprio espaço lógico de memória, onde cada valor tem seu local:

![image.png](../../assets/faculdade/periodo4/compiladores/image%20218.png)

O gerenciamento desse espaço é compartilhado entre compilador, SO e máquina física — o SO mapeia endereços lógicos em físicos, espalhados pela memória real. A representação de um programa nesse espaço lógico consiste de áreas de **dados** e de **programa (código)**.

O tamanho do código gerado é fixo em tempo de compilação, podendo ser colocado em uma área estática; o mesmo vale para alguns objetos de dados (constantes, dados gerados pelo próprio compilador). Decisões de alocação **estática** são feitas apenas com base no texto do programa fonte; decisões **dinâmicas** só podem ser tomadas durante a execução.

Para maximizar o uso do espaço disponível durante a execução, a **heap** e a **pilha (stack)** mudam de tamanho dinamicamente.

#### Pilha — nomes locais a um procedimento

Compiladores de linguagens que usam procedimentos, funções ou métodos como unidade de modularização gerenciam, ao menos parcialmente, a memória de execução em uma **pilha**: ao chamar um procedimento, o espaço para suas variáveis locais é alocado na pilha, e liberado automaticamente ao término da execução.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20219.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20220.png)

**Ativação.** A **ativação** de um procedimento é sua execução completa — o **tempo de vida de uma ativação** é a sequência de passos do início ao fim do corpo do procedimento $p$, incluindo a execução de qualquer procedimento chamado por $p$. Se $a$ e $b$ são ativações de dois procedimentos, seus tempos de vida ou **não se sobrepõem**, ou são **aninhados** — as alocações em pilha não seriam possíveis se as ativações não fossem aninhadas apropriadamente.

Se a ativação de $p$ chama $q$, a ativação de $q$ deve terminar **antes** da de $p$. Três situações são possíveis:

1. a ativação de $q$ termina normalmente, e o controle volta ao ponto de $p$ onde $q$ foi chamado;
2. a ativação de $q$ (ou de algum procedimento que $q$ chamou) aborta, direta ou indiretamente — nesse caso, $p$ encerra simultaneamente com $q$;
3. a ativação de $q$ termina por uma exceção que $q$ não consegue tratar — se $p$ consegue tratá-la, a ativação de $q$ termina enquanto a de $p$ continua (não necessariamente do ponto onde $q$ foi chamada); se $p$ também não consegue tratá-la, a ativação de $p$ termina junto com a de $q$, e presumivelmente outro procedimento tratará a exceção.

**Árvores de ativação.** Podemos representar todas as ativações de procedimento feitas durante a execução de um programa com uma árvore: cada nó corresponde a uma ativação; os filhos de um nó $p$ são as ativações feitas durante a execução de $p$; e as ativações são ordenadas da esquerda para a direita, na ordem em que foram chamadas.

![image.png](../../assets/faculdade/periodo4/compiladores/image%20221.png)

**Registros de ativação (activation records / frames).** Cada ativação viva tem um registro (*frame*) na pilha de controle, com a raiz da árvore de ativação no fundo da pilha; a sequência de registros corresponde ao caminho percorrido na árvore até onde o controle se encontra, com a última ativação no topo. Um registro de ativação tipicamente contém:

- valores temporários, resultantes da avaliação de expressões;
- dados locais pertencentes ao procedimento ativo;
- o estado da máquina imediatamente antes da chamada (endereço de retorno do contador de programa, conteúdo de registradores a restaurar);
- um **link de acesso**, para dados localizados em outros registros de ativação;
- um **link de controle**, apontando para o registro de ativação de quem o chamou;
- o valor de retorno, se houver (usando registradores quando possível);
- os parâmetros reais passados (também usando registradores quando possível).

![image.png](../../assets/faculdade/periodo4/compiladores/image%20222.png)

#### Heap — dados de vida indefinida

A **heap** armazena dados que podem existir **depois** do término de uma chamada de procedimento — dados que vivem potencialmente por tempo indefinido.

À medida que memória é usada e liberada, o espaço da heap se divide entre partes ocupadas e **livres (holes)** — que, em geral, não residem em áreas contíguas. A cada requisição, é preciso encontrar um *hole* grande o suficiente; a menos que seja do tamanho exato solicitado, é preciso dividi-lo ao alocar, o que pode gerar **fragmentação** (muitos espaços livres pequenos e não contíguos).

**Estratégias para reduzir fragmentação:**

- **Controlar antes (na alocação)**: controlar como os objetos são alocados —
    - *first-fit*: aloca o primeiro espaço livre que couber;
    - *best-fit*: divide espaços livres em *bins* de tamanhos variáveis, melhorando a utilização do espaço;
    - *next-fit*: tenta melhorar a localidade espacial, alocando objetos próximos uns dos outros (combinando ideias de *best-fit*).
- **Controlar depois (na desalocação)**: ao liberar um objeto, combinar (*coalesce*) o espaço livre com espaços livres adjacentes — marcando *bins* com um bit indicando se estão ocupados ou livres, ou marcando as fronteiras dos espaços livres quando bins não são usados.

**Desalocação manual.** O gerenciamento manual de memória tende a gerar dois tipos clássicos de erro:

- **Memory leak**: esquecer de liberar dados que não podem mais ser referenciados;
- **Dangling reference**: referenciar dados que já foram liberados.

#### Garbage Collection

**Garbage** são dados que não podem mais ser referenciados pelo programa — um objeto se torna *garbage* quando o programa não tem mais como alcançá-lo. É possível saber, a partir do **tipo** de um objeto, seu tamanho e quais de seus componentes contêm referências a outros objetos (referências sempre apontam para o início de um objeto).

**Reachability (alcançabilidade).** Os dados diretamente acessíveis pelo programa, sem precisar desreferenciar um ponteiro, formam o **root set** — o programa pode alcançar qualquer membro desse conjunto em qualquer momento. Recursivamente, qualquer objeto referenciado (direta ou indiretamente) a partir de um membro do root set também é **alcançável**. O conjunto de objetos alcançáveis muda durante a execução (alocação de objetos, atribuições de referência, etc.).

**Como encontrar objetos inalcançáveis:**

| Estratégia | Quando atua |
| --- | --- |
| **Incremental** | Realiza alguma tarefa a cada instrução executada. |
| **Batch-oriented** | Roda sob demanda, quando o espaço livre se esgota. |

**Reference Counting (incremental).** Adiciona um contador a cada objeto alocado na heap, rastreando quantos ponteiros apontam para ele. Quando o contador chega a zero, o objeto pode ser liberado imediatamente — e liberar um objeto pode, em cascata, levar à liberação de outros.

!!! warning "Problema clássico do Reference Counting"
    Referências cíclicas nunca chegam a contador zero, mesmo quando o ciclo inteiro é inalcançável do resto do programa — causando *memory leaks* persistentes a menos que se use uma técnica adicional para detectar ciclos:

    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20223.png)

**Batch Collectors.** Geralmente executados quando o espaço livre se esgota ou cai abaixo de um limiar. O *collector* pausa a execução do programa, examina a memória alocada para descobrir objetos inutilizados, e libera o espaço correspondente. Em geral, operam em duas fases: descoberta de objetos mortos, e desalocação/"reciclagem" desses objetos.

**Mark-and-Sweep.** A técnica clássica para identificar objetos *live* (vivos) usa um algoritmo de *marking*:

1. O coletor reserva um bit por objeto na heap, chamado **mark bit**, armazenado no cabeçalho do objeto (junto com informações de localização e tamanho).
2. Limpa todos os mark bits, e constrói uma *worklist* a partir de todos os ponteiros em registradores e variáveis acessíveis pelos procedimentos ativos.
3. Caminha pela worklist, seguindo recursivamente quaisquer referências a partir desses ponteiros, marcando tudo que é alcançável.
4. Ao final, objetos **não marcados** (mortos) são inalcançáveis, e podem ser liberados na fase de *sweep* — uma travessia pela heap que libera os objetos inalcançáveis (podendo, opcionalmente, já resetar o mark bit, evitando uma travessia extra na próxima fase de *marking*).

**Definição formal do algoritmo:**

![image.png](../../assets/faculdade/periodo4/compiladores/image%20224.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20225.png) ![image.png](../../assets/faculdade/periodo4/compiladores/image%20226.png)

Todos os algoritmos *batch* (também chamados *trace-based*) computam o conjunto de objetos alcançáveis e usam seu **complemento** para liberar memória — o ciclo geral é: o programa faz requisições de alocação; o garbage collector descobre a reachability; e libera o espaço dos objetos inalcançáveis. Embora implementações variem, esses algoritmos costumam ser descritos em termos de quatro estados gerais para cada região de memória:

| Estado | Significado |
| --- | --- |
| **Free** | Espaço pronto para alocação; não pode conter objeto alcançável. |
| **Unreached** | Presumido inalcançável, a menos que o *tracing* prove o contrário. |
| **Unscanned** | Alcançável, mas seus ponteiros ainda não foram examinados. |
| **Scanned** | Todo objeto *unscanned* eventualmente é observado e transita para este estado. |

**Variações do mark-and-sweep:**

- **Baker's mark-and-sweep**: em vez de examinar a heap inteira, mantém uma lista explícita de objetos alocados.
- **Mark-and-compact**: além de marcar espaço como livre, *move* objetos na heap para eliminar fragmentação.
- **Incremental**: intercala GC e execução do programa — por isso, tende a ser conservador nas suas decisões.
- **Copying collectors**: dividem a heap em duas regiões (*pools*), *old* e *new*; a alocação sempre ocorre a partir de *old*. Na estratégia *stop-and-copy*, quando a alocação falha, todos os dados vivos são copiados de *old* para *new*, e as identidades das duas regiões são invertidas — podendo usar mark-and-sweep ou uma variante incremental internamente.

**Comparações entre estratégias:**

- Com GC vs. sem GC: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20227.png)
- Reference Counting vs. Batch Collectors: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20228.png)
- Mark-and-sweep vs. Copying Collectors: ![image.png](../../assets/faculdade/periodo4/compiladores/image%20229.png)

### Seleção de instruções

Reescreve as operações da IR em operações da linguagem de máquina alvo, ainda abstraindo a quantidade real de registradores disponíveis (trabalhando com "registradores simbólicos"). Pode se beneficiar de operações especiais disponíveis na máquina alvo.

### Alocação de registradores

É muito mais eficiente realizar operações manipulando dados próximos à CPU, em **registradores**, do que na memória RAM. O desafio desta etapa é associar as diversas variáveis do código a um número limitado de registradores físicos, minimizando o **spilling**: o processo de mover variáveis da CPU para a RAM quando não há registradores suficientes disponíveis para todas as variáveis temporárias necessárias — o que afeta significativamente o desempenho final.

### Geração do código de máquina final

Traduz a IR para instruções da arquitetura alvo, produzindo um programa executável que o processador (ou VM) consegue de fato processar. Vários problemas complexos surgem nessa etapa e **interagem entre si** de formas nada triviais:

- reordenar instruções pode acabar *aumentando* o número de registradores necessários simultaneamente;
- a alocação de registradores pode criar uma falsa sensação de dependência entre valores, prejudicando o **instruction scheduling** — a otimização que reorganiza instruções para aumentar o paralelismo em nível de instrução, melhorando o desempenho em máquinas com pipeline de instruções.

!!! example
    ![image.png](../../assets/faculdade/periodo4/compiladores/image%20230.png)
