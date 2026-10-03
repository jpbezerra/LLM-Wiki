# Matemática Discreta

## Lógica Proposicional

A lógica proposicional trabalha com **proposições**: afirmações que só podem assumir dois valores, verdadeiro (T) ou falso (F) — nunca os dois, nunca nenhum.

### Operadores lógicos

| Símbolo | Nome | Significado |
|---|---|---|
| $\lnot P$ | negação | inverte o valor: se $P$ é T, $\lnot P$ é F |
| $P \land Q$ | conjunção ("e") | só é T quando **ambas** $P$ e $Q$ são T |
| $P \lor Q$ | disjunção ("ou") | é T se **pelo menos uma** das duas for T |
| $P \oplus Q$ | ou exclusivo (xor) | é T se **exatamente uma** das duas for T |
| $P \to Q$ | condicional ("se-então") | é F apenas quando $P$ é T e $Q$ é F |
| $P \leftrightarrow Q$ | bicondicional ("se e somente se") | é T quando $P$ e $Q$ têm o **mesmo** valor |

!!! example "Exemplos"
    - $\land$: Sendo $P$: "$1+2=3$" e $Q$: "$5+1=7$", temos $P \land Q = F$ (pois $Q$ é falsa).
    - $\lor$: Sendo $P$: "$5+3=8$" e $Q$: "$2+4=7$", temos $P \lor Q = T$ (pois $P$ é verdadeira).
    - $\oplus$: Sendo $P$: "$5^2=25$" e $Q$: "$2+4=7$", temos $P \oplus Q = T$ (uma verdadeira, a outra falsa).

O condicional $P \to Q$ costuma confundir por sua tabela-verdade: ele só é falso quando a hipótese ($P$) é verdadeira e a conclusão ($Q$) é falsa. Em qualquer outro caso (incluindo quando $P$ é falsa), $P \to Q$ é considerado verdadeiro ("vacuously true").

![](../../assets/faculdade/periodo1/20231026222904.png)

O bicondicional $P \leftrightarrow Q$ é equivalente a $(P\to Q) \land (Q\to P)$:

![](../../assets/faculdade/periodo1/20231028144105.png)

### Proposição composta

Uma proposição composta é formada combinando variáveis proposicionais com operadores lógicos (ex.: $P \land (Q \lor \lnot R)$).

### Variações do condicional

A partir de um condicional $P \to Q$, podemos construir três proposições relacionadas, mas que **não têm o mesmo valor de verdade** entre si (exceto a contrapositiva):

| Nome | Forma | Equivalência |
|---|---|---|
| Contrapositiva | $\lnot Q \to \lnot P$ | **sempre** equivalente a $P \to Q$ |
| Conversa (recíproca) | $Q \to P$ | não preserva o valor de verdade de $P\to Q$ |
| Inversa | $\lnot P \to \lnot Q$ | não preserva o valor de verdade de $P\to Q$ |

!!! tip "Observações"
    - A negação de $\le$ é $>$ (e vice-versa).
    - A **precedência** dos operadores lógicos (do mais "forte" ao mais "fraco") é:

    ![](../../assets/faculdade/periodo1/20231031213933.png)

## Equivalência Proposicional

### Tautologia e contradição

Uma **tautologia** é uma proposição composta que é sempre verdadeira, independentemente do valor de suas variáveis.

![](../../assets/faculdade/periodo1/20231031214536.png)

Uma **contradição** é uma proposição composta que é sempre falsa, independentemente do valor de suas variáveis.

![](../../assets/faculdade/periodo1/20231031214643.png)

### Equivalência lógica

Duas proposições $p$ e $q$ são **logicamente equivalentes** se elas possuem o mesmo valor em cada linha da tabela-verdade:

![](../../assets/faculdade/periodo1/20231031214814.png)

Note que $p \leftrightarrow q$ é verdadeira exatamente quando $p$ e $q$ possuem o mesmo valor em todas as linhas (lembrando que $p$ e $q$ podem ser proposições compostas). Isso nos permite definir equivalência lógica em termos de tautologia: **$p$ e $q$ são logicamente equivalentes se e somente se $p \leftrightarrow q$ é uma tautologia**.

![](../../assets/faculdade/periodo1/20231031215312.png)

Usamos a notação $p \equiv q$ como abreviação de "$(p \leftrightarrow q)$ é uma tautologia", ou "$p$ é logicamente equivalente a $q$". O símbolo $\equiv$ **não** é um operador lógico, e $(p \equiv q)$ **não** é uma proposição composta — é uma afirmação sobre duas proposições.

### Como provar equivalência lógica

Há dois caminhos: construir a tabela-verdade completa de ambos os lados e compará-las, ou substituir trechos por proposições equivalentes usando as **leis da lógica proposicional** (De Morgan, distributividade, absorção, etc.) até transformar um lado no outro.

![](../../assets/faculdade/periodo1/20231031215903.png)
![](../../assets/faculdade/periodo1/20231031215918.png)
![](../../assets/faculdade/periodo1/20231031215938.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231101175324.png)

## Predicados e Quantificadores

### Predicados

Um predicado aparece em funções proposicionais do tipo $p(x) = $ "$x$ é maior que $3$", onde $x$ é a variável e "é maior que $3$" é o predicado. O valor-verdade da proposição depende do valor atribuído à variável.

### Quantificadores

Quantificadores expressam **até que ponto** um predicado é verdadeiro dentro de um domínio.

**Quantificador universal** ($\forall$). É comum falarmos de propriedades válidas para todos os elementos de um domínio; o quantificador universal de $p(x)$ afirma que $p(x)$ é verdadeiro para **todo** valor de $x$ nesse domínio.

![](../../assets/faculdade/periodo1/20231101190905.png)

Notação: $\forall x\, p(x)$, lido como "para todo $x$ do domínio, $p(x)$ é verdadeiro".

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231101191541.png)

    ![](../../assets/faculdade/periodo1/20231101191715.png) — neste caso, a proposição é falsa.

**Quantificador existencial** ($\exists$). Afirma que existe **pelo menos um** elemento do domínio para o qual $p(x)$ é verdadeiro.

![](../../assets/faculdade/periodo1/20231101191926.png)

$\exists x\, p(x)$ é falso somente se $p(x)$ for falso para **todos** os elementos do domínio.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231101192111.png)

### Lei de De Morgan para quantificadores

Negar um quantificador universal produz um existencial (da negação do predicado), e vice-versa:

$$\lnot \forall x\, p(x) \equiv \exists x\, \lnot p(x) \qquad \lnot \exists x\, p(x) \equiv \forall x\, \lnot p(x)$$

![](../../assets/faculdade/periodo1/20231101192211.png)

## Prova Matemática

Uma **prova** de uma proposição é um argumento que demonstra que ela é verdadeira. Quando uma proposição é provada, ela passa a ser chamada de **teorema**. Toda teoria matemática precisa de um ponto de partida — proposições assumidas como verdadeiras sem demonstração, chamadas **postulados** ou **axiomas** — a partir das quais outras proposições são provadas.

![](../../assets/faculdade/periodo1/20231103205308.png)

### Tipos de prova

**Desaprovando afirmações (contraexemplo).** Basta encontrar uma situação em que a afirmação seja falsa.

!!! example "Exemplo"
    Um colega disse que $n^2+n+41$ é sempre primo. Para refutar, basta um contraexemplo: com $n=41$,

    $$41^2+41+41 = 41\cdot41 + 41\cdot2 = 41(41+2) = 41\cdot43,$$

    que não é primo.

**Prova exaustiva.** Verificamos todas as possibilidades (só funciona quando o domínio é finito e pequeno).

!!! example "Exemplo"
    Prove que $(n+1)^3 \ge 3^n$ se $n$ é inteiro positivo com $n \le 4$. Verificamos $\forall n \in \{1,2,3,4\}$:

    $$p(1): 8 \ge 3 \quad p(2): 27 \ge 9 \quad p(3): 64 \ge 27 \quad p(4): 125 \ge 81$$

**Provas por regras de inferência.** Inferência é a operação pela qual afirmamos a verdade de uma proposição em decorrência de sua ligação com outras já reconhecidas como verdadeiras (teoremas, axiomas, leis de equivalência lógica).

!!! example "Exemplos"
    **Se $x$ e $y$ são pares, prove que $x+y$ é par.**

    Assuma $x,y$ inteiros pares. Como $x$ é par, existe $k \in \mathbb{Z}$ tal que $x=2k$; similarmente, $y=2k'$. Logo $x+y = 2k+2k' = 2(k+k')$, que é par.

    **Se $x$ e $y$ são ímpares, prove que $x+y$ é par.**

    Como $x$ é ímpar, $x=2k+1$; como $y$ é ímpar, $y=2k'+1$. Logo $x+y = 2k+1+2k'+1 = 2(k+k'+1)$, que é par.

**Prova direta.** Para provar $P\to Q$: supomos $P$ como verdade (hipótese) e, após uma sequência finita de passos lógicos, chegamos a $Q$. Uma vez provada a implicação, não importa mais se $P$ em si é verdadeira ou falsa — a suposição é descartada.

**Prova por contrapositiva (prova indireta).** Como $P\to Q \equiv \lnot Q \to \lnot P$, às vezes é mais fácil provar a contrapositiva do que a proposição original.

!!! example "Exemplos"
    **Para qualquer inteiro $n$, se $n^2$ é par, então $n$ é par.**

    A contrapositiva é: se $n$ é ímpar, então $n^2$ é ímpar. Como $n$ é ímpar, $n=2k+1$, logo

    $$n^2 = (2k+1)^2 = 4k^2+4k+1 = 2(2k^2+2k)+1,$$

    que é ímpar. ✓

    **Se $n=ab$, então $a \le \sqrt{n}$ ou $b \le \sqrt{n}$.**

    A contrapositiva é: se $a>\sqrt{n}$ e $b>\sqrt{n}$, então $ab \neq n$. Tomando $a,b$ com $a>\sqrt n$ e $b>\sqrt n$: $a\cdot b > \sqrt n \cdot \sqrt n = n$, logo $ab \neq n$. ✓

**Provas de equivalência.** Para provar $P \leftrightarrow Q$, usamos $P \leftrightarrow Q \equiv (P\to Q) \land (Q\to P)$ e construímos uma prova para cada uma das duas implicações.

!!! example "Exemplo"
    **Para qualquer inteiro $n$, $n$ é par se e somente se $n^2$ é par.**

    *(⇒)* Se $n$ é par, $n=2k$, logo $n^2=4k^2=2(2k^2)$, que é par.

    *(⇐)* Usamos a contrapositiva (mais fácil): se $n$ é ímpar, $n=2k+1$, logo $n^2 = 4k^2+4k+1 = 2(2k^2+2k)+1$, que é ímpar — logo, se $n^2$ é par, $n$ é par.

**Provas por contradição (redução ao absurdo).** Assumimos o oposto do que queremos provar; ao chegar a uma contradição, a prova está concluída.

!!! example "Exemplos"
    **Prove que "se $3n+2$ é ímpar, então $n$ é ímpar".**

    Assumimos o oposto: $3n+2$ é ímpar e $n$ é par. Como $n$ é par, $n=2k$, logo

    $$3n+2 = 6k+2 = 2(3k+1),$$

    que é **par** — contradizendo a hipótese de que $3n+2$ é ímpar. Absurdo! Logo, a afirmação original é verdadeira.

    **Prove que $\sqrt{2}$ é irracional.**

    Assuma que $\sqrt{2}$ é racional, isto é, $\sqrt{2} = p/q$ com $p,q \in \mathbb{Z}$, $q \neq 0$, e a fração já simplificada ao máximo (sem fatores comuns). Então:

    $$2 = \frac{p^2}{q^2} \;\Rightarrow\; p^2 = 2q^2 \;\Rightarrow\; p^2 \text{ é par} \;\Rightarrow\; p \text{ é par.}$$

    Se $p=2k$, então $(2k)^2 = 2q^2 \Rightarrow q^2 = 2k^2$, logo $q^2$ também é par, e portanto $q$ é par. Mas se $p$ e $q$ são ambos pares, a fração não poderia estar simplificada ao máximo — contradição. Logo, $\sqrt{2}$ não é racional.

**Provas por casos.** Quando existe um conjunto de casos possíveis e sabemos que pelo menos um deles é verdadeiro (mas não sabemos qual), provamos a afirmação separadamente em cada caso.

!!! example "Exemplos"
    **Prove que, para qualquer inteiro $n$, $n \le n^2$.**

    - Caso 1 ($n \ge 1$): $n^2 \ge n$.
    - Caso 2 ($n=0$): $0^2 \ge 0$.
    - Caso 3 ($n \le -1$): $n^2 \ge n$ (pois $n^2 \ge 0 > n$).

    Os três casos cobrem todos os inteiros, logo a afirmação é verdadeira.

    **Existem números irracionais $x$ e $y$ tais que $x^y$ é racional.**

    Considere $x=y=\sqrt{2}$. Há dois casos: $\sqrt{2}^{\sqrt{2}}$ é racional, ou é irracional.

    - Se $\sqrt{2}^{\sqrt{2}}$ é racional, encontramos o exemplo diretamente.
    - Se $\sqrt{2}^{\sqrt{2}}$ é irracional, tome $x = \sqrt{2}^{\sqrt{2}}$ e $y=\sqrt{2}$: então $x^y = (\sqrt{2}^{\sqrt{2}})^{\sqrt{2}} = \sqrt{2}^2 = 2$, que é racional.

    !!! note "Prova não construtiva"
        Mesmo após concluir a prova, não sabemos qual dos dois casos é verdadeiro, logo não conseguimos exibir explicitamente os números irracionais que satisfazem o teorema. Esse é um exemplo de **prova não construtiva**: um teorema existencial foi provado sem construir um exemplo concreto.

**Prova por indução.** Geralmente usada para provar afirmações do tipo "$\forall n \in \mathbb{N}, P(n)$". Tem dois passos:

1. **Passo base:** mostramos que $P(1)$ (ou $P(0)$) é verdadeiro.
2. **Passo indutivo:** mostramos que, se $P(k)$ é verdadeiro, então $P(k+1)$ também é.

!!! example "Exemplo: a soma dos $n$ primeiros números ímpares é igual a $n^2$"
    **Passo base ($P(1)$):** $1 = 1^2$. Verdadeiro.

    **Passo indutivo ($P(k) \to P(k+1)$):** suponha que $P(k)$ é verdadeiro, isto é,

    $$1+3+\dots+(2k-1) = k^2.$$

    Somando $2k+1$ aos dois lados:

    $$1+3+\dots+(2k-1)+(2k+1) = k^2+2k+1 = (k+1)^2,$$

    que é exatamente $P(k+1)$. Logo, por indução, $P(n)$ vale para todo $n \ge 1$.

!!! example "Mais exemplos de indução"
    **Prove que, para $n \ge 1$, $1+2^1+2^2+\dots+2^n = 2^{n+1}-1$:**

    ![](../../assets/faculdade/periodo1/20231121092932.png)

    ![](../../assets/faculdade/periodo1/20231121092953.png)

    ![](../../assets/faculdade/periodo1/20231121093121.png)

    ![](../../assets/faculdade/periodo1/20231121094930.png)

    ![](../../assets/faculdade/periodo1/20231121094958.png)

    ![](../../assets/faculdade/periodo1/20231121095013.png)

    **Prove que o conjunto das partes de um conjunto com $n$ elementos possui $2^n$ elementos:**

    ![](../../assets/faculdade/periodo1/20231123233553.png)

**Fazendo conjecturas.** Antes de provar por indução, muitas vezes é preciso primeiro **conjecturar** (adivinhar) a fórmula geral observando padrões em casos pequenos.

![](../../assets/faculdade/periodo1/20231126094632.png)

### Definições recursivas

Usamos definições recursivas em funções, operações, algoritmos, conjuntos e sequências: a definição se refere a si mesma em casos "menores", com um caso base que interrompe a recursão.

![](../../assets/faculdade/periodo1/20231126211631.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231126211747.png)
    ![](../../assets/faculdade/periodo1/20231126215504.png)
    ![](../../assets/faculdade/periodo1/20231126220540.png)

**Sequência de Fibonacci.** Clássico exemplo de definição recursiva: cada termo é a soma dos dois anteriores.

![](../../assets/faculdade/periodo1/20231126221817.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231126221830.png)
    ![](../../assets/faculdade/periodo1/20231126222124.png)

    ![](../../assets/faculdade/periodo1/20231126221841.png)
    ![](../../assets/faculdade/periodo1/20231126222150.png)

## Conjuntos

Um **conjunto** é uma coleção desordenada de objetos, sem repetição de elementos (listar o mesmo elemento duas vezes não muda o conjunto):

$$\{1,2,3,4\} = \{1,1,2,2,2,3,4,4,4,4\} = \{3,2,4,3,2,2,1,4,3\}$$

**Notações básicas:**

- $a \in A$: o elemento $a$ pertence ao conjunto $A$.
- $a \notin A$: o elemento $a$ não pertence ao conjunto $A$ (formalmente, $a\notin A \equiv \lnot(a\in A)$).
- $A \subset B$: todos os elementos de $A$ estão em $B$, mas $A \neq B$ (subconjunto próprio).
- $A \subseteq B$: todos os elementos de $A$ estão em $B$, podendo $A = B$.

Em conjuntos de conjuntos, os elementos ficam sempre separados pelas vírgulas mais externas:

![](../../assets/faculdade/periodo1/20231110210556.png)

![](../../assets/faculdade/periodo1/20231126185541.png)
![](../../assets/faculdade/periodo1/20231110211021.png)

Dois conjuntos $A$ e $B$ são **iguais** se e somente se $\forall x\,(x\in A \leftrightarrow x\in B)$.

### Conjunto vazio

O conjunto vazio, sem nenhum elemento, é representado por $\{\}$ ou $\varnothing$.

**Propriedades:**

- $x \in \varnothing \equiv F$ (nunca é verdade)
- $\varnothing = \{x \mid F\}$

!!! warning "Atenção"
    $\{\varnothing\}$ e $\varnothing$ são coisas diferentes: $\varnothing$ é o conjunto vazio, enquanto $\{\varnothing\}$ é um conjunto que **contém** o conjunto vazio como seu único elemento (portanto tem cardinalidade $1$, não $0$).

### Subconjuntos

$A$ é subconjunto de $B$ se e somente se $\forall x\,(x\in A \to x\in B)$. Se $A \subseteq B$ e $A \neq B$, dizemos que $A$ é **subconjunto próprio** de $B$.

![](../../assets/faculdade/periodo1/20231110212255.png)

![](../../assets/faculdade/periodo1/20231110212333.png)

Se $P(S)$ é o conjunto das partes de $S$ e $n$ é o número de elementos de $S$, então $|P(S)| = 2^n$. O conjunto vazio está contido em **todo** conjunto.

**Propriedades:**

- Para todo conjunto $S$: $\varnothing \subseteq S$ e $S \subseteq S$.
- $A = B \equiv (A\subseteq B) \land (B\subseteq A)$.
- Um conjunto é **finito** se contém $n$ elementos distintos, com $n \ge 0$; é **infinito** se não é finito.

### Cardinalidade

Para um conjunto finito $S$, $|S|$ denota a cardinalidade de $S$, isto é, a quantidade de elementos distintos.

!!! example "Exemplos"
    - $|\{5,2,89\}| = 3$
    - $|\{1,1,1,1,1,1,2\}| = 2$ (repetições não contam)
    - $|\{\varnothing\}| = 1$ — cuidado: é um conjunto com um elemento (o vazio), não o próprio vazio.
    - $|\{\{1,2,3\}, \varnothing, \{5,6,7,\dots\}\}| = 3$ — aqui contamos os três elementos do conjunto externo (dois dos quais são, eles próprios, conjuntos).

### Conjunto das partes

O conjunto das partes de $S$, denotado $P(S)$, contém **todos** os subconjuntos de $S$ (incluindo $\varnothing$ e o próprio $S$).

!!! example "Exemplos"
    $$P(\{0,1,2\}) = \{\varnothing, \{0\}, \{1\}, \{2\}, \{0,1\}, \{0,2\}, \{1,2\}, \{0,1,2\}\}$$

    ![](../../assets/faculdade/periodo1/20231111171237.png)

    $$P(\varnothing) = \{\varnothing\} \qquad P(\{\varnothing\}) = \{\varnothing, \{\varnothing\}\} \qquad P(\{\varnothing,\{\varnothing\}\}) = \{\varnothing, \{\varnothing\}, \{\varnothing,\{\varnothing\}\}\}$$

### Conjunto universo

O conjunto universo $U$ é o conjunto com todos os elementos relevantes ao problema que estamos tratando.

### Tuplas

Uma **tupla** é um conjunto **ordenado** de elementos — a ordem importa. $(1,2,3)$ e $(3,2,1)$ são tuplas de 3 elementos diferentes entre si, já que seus primeiros elementos diferem.

### Produto cartesiano

O produto cartesiano $A \times B$ é o conjunto de todos os pares ordenados $(a,b)$ com $a\in A$ e $b\in B$.

![](../../assets/faculdade/periodo1/20231110221412.png)
![](../../assets/faculdade/periodo1/20231110221424.png)

Um subconjunto de um produto cartesiano é chamado de **relação** (voltaremos a isso mais adiante).

**Propriedades:**

![](../../assets/faculdade/periodo1/20231110221516.png)

O número de elementos do produto cartesiano é o produto das cardinalidades: se $|A|=m$, $|B|=n$, $|C|=o$, então $|A\times B \times C| = m\cdot n\cdot o$.

### Operadores de conjuntos

**União** ($A\cup B$): elementos que estão em $A$ **ou** em $B$ (ou ambos).

![](../../assets/faculdade/periodo1/20231110222125.png)

Propriedade: ![](../../assets/faculdade/periodo1/20231110222154.png) — o "ou" ($\lor$) lógico corresponde à união ($\cup$) de conjuntos.

!!! example "Exemplo de prova"
    ![](../../assets/faculdade/periodo1/20231110222335.png)

**Interseção** ($A\cap B$): elementos que estão em $A$ **e** em $B$ simultaneamente.

![](../../assets/faculdade/periodo1/20231110225404.png)

Propriedade: ![](../../assets/faculdade/periodo1/20231110225420.png) — o "e" ($\land$) lógico corresponde à interseção ($\cap$) de conjuntos.

**Conjuntos disjuntos.** $A$ e $B$ são disjuntos se $A \cap B = \varnothing$.

!!! example "Exemplo"
    $\{1,2,3,4\}$ e $\{5,6,7,8,9,10\}$ são disjuntos.

**Cardinalidade da união.** $|A\cup B| = |A|+|B|-|A\cap B|$, pois os elementos de $A\cap B$ seriam contados duas vezes se simplesmente somássemos $|A|+|B|$.

**Diferença** ($A - B$, complemento de $B$ em relação a $A$): elementos de $A$ que **não** estão em $B$.

!!! example "Exemplo"
    $\{1,2,3,4\} - \{2,3\} = \{1,4\}$

Propriedade: ![](../../assets/faculdade/periodo1/20231110230040.png)

**Complemento** ($\bar{A}$ ou $A^c$): elementos do universo $U$ que não estão em $A$, isto é, $U - A$.

![](../../assets/faculdade/periodo1/20231110232813.png)

Propriedade: ![](../../assets/faculdade/periodo1/20231110232827.png)

**Lógica em conjuntos.** As operações de conjuntos espelham diretamente os operadores lógicos, trocando "pertence a $A$" por uma proposição $p$ e "pertence a $B$" por $q$:

![](../../assets/faculdade/periodo1/20231110232854.png)
![](../../assets/faculdade/periodo1/20231110232909.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231110233041.png)

    ![](../../assets/faculdade/periodo1/20231111125314.png)

**União generalizada.** É a união de $n$ conjuntos ao mesmo tempo.

![](../../assets/faculdade/periodo1/20231111125509.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231111125524.png)

    ![](../../assets/faculdade/periodo1/20231111130136.png)

**Interseção generalizada.** É a interseção de $n$ conjuntos ao mesmo tempo.

![](../../assets/faculdade/periodo1/20231111125634.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231111130045.png) — resposta: conjunto vazio.

    ![](../../assets/faculdade/periodo1/20231111130942.png) — resposta: $3$.

## Funções

Uma função $f$ de $A$ para $B$ relaciona **cada** elemento de $A$ a **exatamente um** elemento de $B$.

![](../../assets/faculdade/periodo1/20231111131120.png)
![](../../assets/faculdade/periodo1/20231111131202.png)

$A$ é o **domínio** de $f$ e $B$ é o **contradomínio** de $f$. O **conjunto imagem** de $f$ é formado por todo elemento de $B$ que de fato se relaciona com algum elemento de $A$.

![](../../assets/faculdade/periodo1/20231111131713.png)

Se $f(x)=y$, dizemos que $y$ é a **imagem** de $x$, e $x$ é a **pré-imagem** de $y$. Duas funções são iguais se possuem o mesmo domínio, contradomínio, e associam cada elemento da mesma forma.

### Classificação de funções

**Função injetiva (injetora).** Elementos diferentes do domínio sempre têm imagens diferentes — nunca dois elementos "colidem" na mesma imagem.

![](../../assets/faculdade/periodo1/20231111133128.png)

**Função sobrejetiva (sobrejetora).** Todo elemento do contradomínio é imagem de pelo menos um elemento do domínio — a imagem coincide com o contradomínio inteiro.

![](../../assets/faculdade/periodo1/20231111133612.png)

![](../../assets/faculdade/periodo1/20231111133729.png)

**Função bijetiva (bijetora).** É simultaneamente injetiva e sobrejetiva.

![](../../assets/faculdade/periodo1/20231111133757.png)

A função identidade é um exemplo clássico de função bijetiva.

### Função inversa

Uma função $f$ possui inversa $f^{-1}$ se e somente se $f$ é bijetiva. A inversa desfaz exatamente o que $f$ faz.

![](../../assets/faculdade/periodo1/20231111152408.png)
![](../../assets/faculdade/periodo1/20231111152454.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231111153210.png)

    A função $g^{-1}$: $g^{-1}(50)=a$, $g^{-1}(20)=b$, $g^{-1}(60)=c$, $g^{-1}(10)=d$, $g^{-1}(30)=e$, $g^{-1}(40)=f$.

### Função composta

![](../../assets/faculdade/periodo1/20231111161121.png)
![](../../assets/faculdade/periodo1/20231111161558.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231114100220.png)

    **Resposta:** $(g\circ f)$ não possui inversa, pois toda função inversa pressupõe uma bijeção. Nesse caso, $g\circ f: A\to C$ tem $A$ e $C$ com dois elementos cada, mas a função resultante é sobrejetiva sem ser injetiva — não é uma bijeção, logo não possui inversa.

### Outras funções importantes

**Função floor (piso), $\lfloor x \rfloor$:** o maior inteiro menor ou igual a $x$.

![](../../assets/faculdade/periodo1/20231111164346.png)

!!! example "Exemplo"
    $\lfloor 1/2 \rfloor = 0$, $\lfloor -2 \rfloor = -2$, $\lfloor -1/2 \rfloor = -1$.

**Função ceiling (teto), $\lceil x \rceil$:** o menor inteiro maior ou igual a $x$.

![](../../assets/faculdade/periodo1/20231111165643.png)

!!! example "Exemplo"
    $\lceil 1/2 \rceil = 1$, $\lceil -2 \rceil = -2$, $\lceil -1/2 \rceil = 0$.

**Propriedades de floor e ceiling:**

![](../../assets/faculdade/periodo1/20231114101000.png)
![](../../assets/faculdade/periodo1/20231114101009.png)
![](../../assets/faculdade/periodo1/20231114101019.png)
![](../../assets/faculdade/periodo1/20231114101051.png)
![](../../assets/faculdade/periodo1/20231114101100.png)
![](../../assets/faculdade/periodo1/20231114101112.png)
![](../../assets/faculdade/periodo1/20231114101128.png)

## Sequências e somatórios

Uma **sequência** é uma lista ordenada de termos, geralmente dada por uma fórmula, denotada $a_n$.

!!! example "Exemplo"
    Para $a_n = 1/n$: $a_1=1$, $a_2=1/2$, $a_3=1/3$, ...

Sequências podem ser **aritméticas** (diferença constante entre termos) ou **geométricas** (razão constante entre termos). A **sequência de Fibonacci** é um exemplo de sequência **recursiva**, onde cada termo é calculado em função de termos anteriores.

### Sequências infinitas

Uma sequência infinita tem uma quantidade ilimitada de termos. Infinitos, porém, não são todos "do mesmo tamanho": conjuntos infinitos podem ser **enumeráveis** ou **não enumeráveis**.

**Conjuntos enumeráveis.** Um conjunto é enumerável se é finito, ou se existe uma **bijeção** entre ele e o conjunto dos naturais.

- **Naturais, naturais não nulos e pares não nulos.** Esses três conjuntos têm a mesma cardinalidade: existe uma bijeção entre cada natural e um par não nulo (por exemplo $n \mapsto 2n$):

    ![](../../assets/faculdade/periodo1/20231114205140.png)

    Logo, $\text{card}(\mathbb{N}) = \text{card}(\text{pares não nulos})$ — mesmo os pares sendo "metade" dos naturais intuitivamente, em cardinalidade infinita eles têm o mesmo tamanho.

- **Inteiros.** Também são enumeráveis, por uma bijeção que alterna entre positivos e negativos:

    ![](../../assets/faculdade/periodo1/20231114230450.png)

    Logo, $\text{card}(\mathbb{Z}) = \text{card}(\mathbb{N})$.

- **Racionais.** Também são enumeráveis. A prova clássica arranja os racionais em uma "matriz" (numerador na linha, denominador na coluna) e percorre essa matriz em diagonais, listando todos os racionais em sequência:

    ![](../../assets/faculdade/periodo1/20231115092723.png)

    Como é possível enumerá-los dessa forma, $\text{card}(\mathbb{Q}) = \text{card}(\mathbb{N})$.

**Conjuntos não enumeráveis.** O conjunto dos **reais** (que abrange racionais e irracionais) é não enumerável. A prova clássica é por absurdo, usando o **argumento da diagonal de Cantor**:

1. Suponha, por absurdo, que o conjunto dos reais é enumerável.
2. Observe o intervalo $(0,1)$ e liste números reais aleatoriamente, um para cada natural:

    ![](../../assets/faculdade/periodo1/20231115110654.png)

3. Construa um novo número tomando o $i$-ésimo dígito decimal do $i$-ésimo número da lista, e somando $1$ a cada dígito (com $9+1=0$):

    ![](../../assets/faculdade/periodo1/20231115111445.png)

4. Esse número construído difere do primeiro número da lista no primeiro dígito, do segundo no segundo dígito, e assim por diante — logo ele **não pode estar na lista**.
5. Portanto, existe pelo menos um real que não foi associado a nenhum natural: a lista não é sobrejetiva (nem bijetiva), e o conjunto dos reais **não é enumerável**. Logo, $\text{card}(\mathbb{R}) > \text{card}(\mathbb{N})$.

**Números transfinitos.** Associamos à cardinalidade dos naturais, inteiros e racionais um número transfinito chamado **aleph-null**, $\aleph_0$ (uma forma rigorosa de "contar" conjuntos infinitos, com suas próprias regras de aritmética):

$$\aleph_0 + 1 = \aleph_0 \qquad 2\aleph_0 = \aleph_0$$

De acordo com a **hipótese do contínuo** de Cantor, a cardinalidade de $P(\mathbb{N})$ é maior que a de $\mathbb{N}$: $2^{\aleph_0} > \aleph_0$. Além disso, a cardinalidade de $P(\mathbb{N})$ é igual à cardinalidade dos reais, logo $2^{\aleph_0} = \aleph_1$. Essa lógica se estende indefinidamente: $2^{\aleph_1} = \aleph_2$, e assim por diante. Associamos à cardinalidade dos reais o transfinito **aleph-one**, $\aleph_1$ (ou $2^{\aleph_0}$). Não existe nenhum número "entre" $|\mathbb{N}|$ e $|\mathbb{R}|$, ou seja, entre $\aleph_0$ e $\aleph_1$.

### Somatório

O **índice de soma** indica a variável que percorre os valores a serem somados, junto com seus limites inferior e superior:

![](../../assets/faculdade/periodo1/20231114193741.png)

## Análise combinatória

### Princípios básicos da contagem

Uma regra mnemônica útil: **"ou" soma e "e" multiplica**.

**Regra do produto.** Se uma tarefa pode ser dividida em etapas sucessivas e independentes, com $n_1$ opções na primeira, $n_2$ na segunda, etc., o número total de formas de realizar a tarefa é $n_1 \cdot n_2 \cdot \dots \cdot n_k$.

![](../../assets/faculdade/periodo1/20231201082150.png)
![](../../assets/faculdade/periodo1/20231201082448.png)
![](../../assets/faculdade/periodo1/20231201082528.png)

**Regra da soma.** Se uma tarefa pode ser feita de $n_1$ formas **ou** de $n_2$ formas (categorias mutuamente exclusivas), o número total é $n_1+n_2$.

![](../../assets/faculdade/periodo1/20231201082614.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231201082731.png)
    ![](../../assets/faculdade/periodo1/20231201082715.png)

    ![](../../assets/faculdade/periodo1/20231201082758.png)

**Princípio da inclusão-exclusão (caso de 2 conjuntos).** Usa a ideia de cardinalidade da união de conjuntos para evitar contar duplicado:

![](../../assets/faculdade/periodo1/20231201082829.png)
![](../../assets/faculdade/periodo1/20231201082923.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231201082953.png)

### Permutação, arranjo e combinação

| Conceito | A ordem importa? | Usa todos os elementos? |
|---|---|---|
| **Permutação** | Sim | Sim |
| **Arranjo** | Sim | Não (subconjuntos ordenados) |
| **Combinação** | Não | Não (subconjuntos) |

**Permutação.** Agrupa todos os elementos do conjunto, e a ordem importa.

![](../../assets/faculdade/periodo1/20231201081728.png)
![](../../assets/faculdade/periodo1/20231201081817.png)

**Arranjo.** Agrupa apenas parte dos elementos (um número de subconjuntos ordenados), diferente da permutação, que usa todos.

![](../../assets/faculdade/periodo1/20231201081903.png)
![](../../assets/faculdade/periodo1/20231201081851.png)

**Combinação.** Agrupa um determinado número de elementos, mas a ordem **não** importa.

![](../../assets/faculdade/periodo1/20231204234628.png)

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

![](../../assets/faculdade/periodo1/20231204234653.png)

### Binômio de Newton

**Termo geral.**

![](../../assets/faculdade/periodo1/20231025215905.png)

Expandindo o binômio:

![](../../assets/faculdade/periodo1/20231205003846.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240124111719.png)

!!! tip "Observações importantes"
    - Em $(x-y)^n$, é o **expoente ímpar** do $y$ que determina o **sinal negativo** do termo.
    - Se a questão pedir um termo "inválido" (fora do intervalo de expoentes possíveis), o coeficiente correspondente é zero.
    - Para saber a soma de **todos** os coeficientes de uma expansão, basta substituir todas as variáveis por $1$.

    !!! example "Exemplo"
        ![](../../assets/faculdade/periodo1/20240122221731.png)

**Triângulo de Pascal:**

![](../../assets/faculdade/periodo1/20231205002636.png)

**Igualdades importantes do binômio:**

![](../../assets/faculdade/periodo1/20231204235410.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20231204235427.png)

![](../../assets/faculdade/periodo1/20231205004520.png)

![](../../assets/faculdade/periodo1/20231204235527.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20231205000538.png)

![](../../assets/faculdade/periodo1/20231204235541.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20231205000618.png)

![](../../assets/faculdade/periodo1/20231205005022.png)

Com o auxílio do triângulo de Pascal: ![](../../assets/faculdade/periodo1/20231205005423.png)

**Identidade de Vandermonde:** ![](../../assets/faculdade/periodo1/20231205002935.png)

**Elemento central da linha do triângulo de Pascal.** É o coeficiente de maior valor numérico naquela linha. Se $n$ é par, o elemento central corresponde a $k=n/2$; se $n$ é ímpar, a $k=(n-1)/2$.

### Princípio da casa dos pombos

Se distribuirmos mais objetos ("pombos") do que o número de "casas" disponíveis, pelo menos uma casa deverá conter mais de um objeto.

![](../../assets/faculdade/periodo1/20231215185146.png)

Isso ocorre porque, em qualquer distribuição possível, há sempre pelo menos 2 pombos na mesma casa quando pombos $>$ casas.

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231215185233.png)

    Sim, pelo menos 6 alunos possuem médias iguais.

    ![](../../assets/faculdade/periodo1/20231215185322.png)
    ![](../../assets/faculdade/periodo1/20231215185405.png)

    ![](../../assets/faculdade/periodo1/20231215185542.png)
    ![](../../assets/faculdade/periodo1/20231215185620.png)

**Generalizando.**

![](../../assets/faculdade/periodo1/20231215185709.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231215185743.png)

    ![](../../assets/faculdade/periodo1/20231215190012.png)

    ![](../../assets/faculdade/periodo1/20231215185906.png)

    ![](../../assets/faculdade/periodo1/20231215190104.png)

!!! tip "Observação"
    Em exemplos como "quantos números entre 1 e 401 são divisíveis por 2", usamos a função floor, pois queremos a parte inteira da divisão: neste caso, $\lfloor 401/2 \rfloor = 200$.

### Princípio da inclusão-exclusão (caso geral)

![](../../assets/faculdade/periodo1/20231215191519.png)

A fórmula diz que a cardinalidade da união de $n$ conjuntos é igual à soma das cardinalidades individuais ($|A_i|$), menos a soma das interseções dois a dois ($|A_i \cap A_j|$), mais a soma das interseções três a três ($|A_i\cap A_j\cap A_k|$), e assim por diante, alternando sinal (dependendo da paridade de $n$, representado por $(-1)^{n+1}$) até a interseção de todos os $n$ conjuntos:

$$|A_1\cup\dots\cup A_n| = \sum|A_i| - \sum|A_i\cap A_j| + \sum|A_i\cap A_j\cap A_k| - \dots + (-1)^{n+1}|A_1\cap\dots\cap A_n|$$

Note que $|A_i|$ é simplesmente $\binom{n}{1}$ "escolhas" de conjunto, $|A_i\cap A_j|$ corresponde a $\binom{n}{2}$ escolhas, etc. Portanto, o **número de termos** na fórmula para a cardinalidade da união de $A_1,\dots,A_n$ segue o padrão $\binom{n}{1} - \binom{n}{2} + \binom{n}{3} - \dots + (-1)^{n+1}\binom{n}{n}$ (lembrando que $\binom{n}{n}=1$ sempre).

![](../../assets/faculdade/periodo1/20231215191550.png)
![](../../assets/faculdade/periodo1/20231215190827.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231215195742.png)

    $1°: 30;\quad 2°: 29;\quad 3°: 24$

    ![](../../assets/faculdade/periodo1/20231215200446.png)
    ![](../../assets/faculdade/periodo1/20231215200507.png)

    ![](../../assets/faculdade/periodo1/20231215201125.png)
    ![](../../assets/faculdade/periodo1/20231215201133.png)

    ![](../../assets/faculdade/periodo1/20231217121355.png)
    ![](../../assets/faculdade/periodo1/20231217124324.png)

    ![](../../assets/faculdade/periodo1/20231217121413.png)
    ![](../../assets/faculdade/periodo1/20231217124314.png)

## Teoria dos números

### Divisibilidade de números inteiros

![](../../assets/faculdade/periodo1/20231217124550.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231217124625.png)

**Propriedades:**

![](../../assets/faculdade/periodo1/20231217124653.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231217125040.png)

**Algoritmo da divisão** (divisão com resto):

![](../../assets/faculdade/periodo1/20231217130348.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231217130947.png)

### Conjunto dos divisores, MDC e números primos

![](../../assets/faculdade/periodo1/20231217131335.png)

**MDC (máximo divisor comum):**

![](../../assets/faculdade/periodo1/20231217131425.png)

**Números primos.** Um número é primo se seus únicos divisores positivos são $1$ e ele mesmo.

![](../../assets/faculdade/periodo1/20231217131443.png)
![](../../assets/faculdade/periodo1/20231217131546.png)
![](../../assets/faculdade/periodo1/20231217131611.png)

**Teorema fundamental da aritmética.** Todo inteiro maior que $1$ pode ser escrito de forma única como um produto de primos (a menos da ordem dos fatores).

![](../../assets/faculdade/periodo1/20231217131846.png)
![](../../assets/faculdade/periodo1/20231217131909.png)
![](../../assets/faculdade/periodo1/20231217132221.png)

**MMC (mínimo múltiplo comum):**

![](../../assets/faculdade/periodo1/20231217133249.png)
![](../../assets/faculdade/periodo1/20231217133734.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231217133757.png)

### Algoritmo de Euclides

O Algoritmo de Euclides calcula o MDC de dois números repetidamente aplicando a divisão com resto, até o resto chegar a zero.

![](../../assets/faculdade/periodo1/20231217143214.png)
![](../../assets/faculdade/periodo1/20231217143247.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231217143705.png)

**Identidade de Bézout.** Garante que o MDC de dois inteiros $a$ e $b$ pode sempre ser escrito como uma combinação linear $ax+by = \text{mdc}(a,b)$, para certos inteiros $x,y$.

![](../../assets/faculdade/periodo1/20231217143925.png)
![](../../assets/faculdade/periodo1/20231217144022.png)

**Algoritmo de Euclides Estendido.** Encontra, além do MDC, os coeficientes $x,y$ da identidade de Bézout, "desenrolando" as divisões do Algoritmo de Euclides de trás para frente.

![](../../assets/faculdade/periodo1/20231217144111.png)
![](../../assets/faculdade/periodo1/20231217144209.png) (em 6, é $6 = 18\cdot17 - 300\cdot1$)

!!! example "Exemplo: $\text{mdc}(57,10)$"
    ![](../../assets/faculdade/periodo1/20231218195307.png)

**Aplicação: Equação Diofantina Linear.** Uma equação do tipo $ax+by=c$, com soluções inteiras.

![](../../assets/faculdade/periodo1/20231217221246.png)
![](../../assets/faculdade/periodo1/20231217221334.png)

!!! example "Fazendo o exemplo"
    ![](../../assets/faculdade/periodo1/20231218200343.png)

![](../../assets/faculdade/periodo1/20231217221356.png)

!!! note
    O "$d$" é o $\text{mdc}(a,b)$ (o slide original continha um erro nesse ponto). Se existe uma solução, então existem **infinitas** soluções:

    ![](../../assets/faculdade/periodo1/20231217223911.png)
    ![](../../assets/faculdade/periodo1/20231217225743.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231218200816.png) (os números só podem ser multiplicados por inteiros positivos)

    **Primeiro exemplo:** ![](../../assets/faculdade/periodo1/20231218214049.png)

    **Segundo exemplo:** ![](../../assets/faculdade/periodo1/20231218214104.png)

    **Terceiro exemplo:** ![](../../assets/faculdade/periodo1/20231218214212.png)

**Consequências:**

![](../../assets/faculdade/periodo1/20231217230017.png)

### Aritmética modular

Dizemos que $a \equiv b \pmod{m}$ (lê-se "$a$ é congruente a $b$ módulo $m$") se $m$ divide $a-b$:

![](../../assets/faculdade/periodo1/20231226011240.png)

$$m \mid (a-b) \iff a \pmod m = b \pmod m$$

!!! example "Exemplo"
    $7 \equiv 2 \pmod 5$, pois $7 \bmod 5 = 2$ e $2 \bmod 5 = 2$.

![](../../assets/faculdade/periodo1/20231226012735.png)
![](../../assets/faculdade/periodo1/20231226014908.png)

!!! example "Exemplo: calcular horas em um relógio"
    $$23+3 \equiv \big(23 \bmod 12 + 3 \bmod 12\big) \pmod{12}$$

    $$14 \bmod 12 = 2 \qquad \text{ou, direto: } 26 \bmod 12 = 2$$

    $$23 \cdot 3 \equiv \big(23 \bmod 12 \cdot 3 \bmod 12\big) \pmod{12}$$

    $$33 \bmod 12 = 9 \qquad \text{ou, direto: } 69 \bmod 12 = 9$$

![](../../assets/faculdade/periodo1/20231226015039.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20231226015256.png)
    ![](../../assets/faculdade/periodo1/20231226015418.png)

**Algumas aplicações de congruência:**

![](../../assets/faculdade/periodo1/20231226015514.png)
![](../../assets/faculdade/periodo1/20231226020008.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231226021044.png)
    ![](../../assets/faculdade/periodo1/20231226021057.png)

**Propriedades:**

![](../../assets/faculdade/periodo1/20231226021906.png)
![](../../assets/faculdade/periodo1/20231226021914.png)

**Congruência linear.** Uma equação do tipo $ax \equiv b \pmod m$. Nem sempre existe solução; uma forma de checar é usando a identidade de Bézout:

![](../../assets/faculdade/periodo1/20231226022733.png)
![](../../assets/faculdade/periodo1/20231226025342.png)
![](../../assets/faculdade/periodo1/20231226024105.png)
![](../../assets/faculdade/periodo1/20231226024215.png)
![](../../assets/faculdade/periodo1/20231226024315.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231226025343.png)
    ![](../../assets/faculdade/periodo1/20231226025355.png)

**Algoritmo.**

![](../../assets/faculdade/periodo1/20231226025453.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231226030036.png)
    ![](../../assets/faculdade/periodo1/20231226030554.png)

    **Encontre $x$ para $7x \equiv 5 \pmod{11}$:**

    ![](../../assets/faculdade/periodo1/20231227002317.png)

    ![](../../assets/faculdade/periodo1/20240122222946.png)

    ![](../../assets/faculdade/periodo1/20240122223003.png)
    ![](../../assets/faculdade/periodo1/20240122223012.png)
    ![](../../assets/faculdade/periodo1/20240122223025.png)

    ![](../../assets/faculdade/periodo1/20240123163633.png)

    ![](../../assets/faculdade/periodo1/20240123163653.png)
    ![](../../assets/faculdade/periodo1/20240123163710.png)

### Teorema chinês do resto

Permite resolver **sistemas** de congruências lineares simultaneamente, quando os módulos são coprimos entre si.

**Contexto.**

![](../../assets/faculdade/periodo1/20231227002843.png)

**Teorema.** Encontrar um único "$x$" que satisfaça todas as equações do sistema simultaneamente.

![](../../assets/faculdade/periodo1/20231227002858.png)

**Fórmula.**

![](../../assets/faculdade/periodo1/20231227002938.png)

!!! example "Resolução do exemplo"
    ![](../../assets/faculdade/periodo1/20231227003218.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20231227004101.png)
    ![](../../assets/faculdade/periodo1/20231227011001.png)

### Pequeno Teorema de Fermat

Usado, entre outras aplicações, em **testes de primalidade**: se $p$ é primo e $a$ não é múltiplo de $p$, então $a^{p-1} \equiv 1 \pmod p$.

**Contexto: teste de primalidade.**

![](../../assets/faculdade/periodo1/20231227015124.png)

![](../../assets/faculdade/periodo1/20231227015040.png)
![](../../assets/faculdade/periodo1/20231227015139.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20231227021812.png)
    ![](../../assets/faculdade/periodo1/20231227021759.png)

    (o último termo fica $3^{204} \equiv 4 \pmod{11}$)

    ![](../../assets/faculdade/periodo1/20231227021830.png)
    ![](../../assets/faculdade/periodo1/20231227023254.png)

    ![](../../assets/faculdade/periodo1/20240123165521.png)
    ![](../../assets/faculdade/periodo1/20240123165532.png)

    ![](../../assets/faculdade/periodo1/20240205220635.png)
    ![](../../assets/faculdade/periodo1/20240205220524.png)
    ![](../../assets/faculdade/periodo1/20240205220900.png)

**Aplicações: criptografia.** O Pequeno Teorema de Fermat é um dos fundamentos teóricos por trás de sistemas de criptografia de chave pública, como o RSA.

![](../../assets/faculdade/periodo1/20231227023356.png)
![](../../assets/faculdade/periodo1/20231227023457.png)
![](../../assets/faculdade/periodo1/20231227023505.png)
![](../../assets/faculdade/periodo1/20231227023539.png)
![](../../assets/faculdade/periodo1/20231227023601.png)

### Fórmula quadrática modular

Usada em casos de $ax^2 \pm bx \pm c \equiv 0 \pmod m$. Para aplicar, basta usar a fórmula de Bhaskara convencional, lembrando que todas as operações (incluindo a divisão por $2a$, que precisa ser trocada pelo **inverso modular**) são feitas em módulo $m$. Se as soluções obtidas não satisfazerem $ax^2\pm bx \pm c \equiv 0 \pmod m$ ao serem testadas, a equação quadrática não possui soluções modulares.

## Relações

Seja $S$ um conjunto de pessoas. Suponha que queremos escolher os pares ordenados de $S \times S$ cujos componentes iniciam com a mesma letra; esse subconjunto de $S\times S$ é chamado de **relação binária** sobre $S$.

**Notações:**

- $R = \{(x,y) \mid x,y \in S \text{ e } x,y \text{ começam com a mesma letra}\}$
- $xRy \leftrightarrow x,y\in S$ e $x,y$ começam com a mesma letra

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240209104225.png)

    ![](../../assets/faculdade/periodo1/20240209104239.png)

    $R_1 = \{(1,1),(2,2),(3,3)\}$

    ![](../../assets/faculdade/periodo1/20240209104318.png)

    $R_2 = \{(1,2),(1,3),(2,3)\}$

    ![](../../assets/faculdade/periodo1/20240209104359.png)

![](../../assets/faculdade/periodo1/20240209104445.png)

Toda relação possui um **sentido direto** e um **sentido inverso**:

- Sentido direto: $R = \{(a,b),(c,d)\}$
- Sentido inverso: $R^{-1} = \{(b,a),(d,c)\}$

**Função como relação.** Toda função pode ser vista como um caso particular de relação (em que cada elemento do domínio aparece em exatamente um par).

![](../../assets/faculdade/periodo1/20240209104652.png)

### Propriedades das relações

**Reflexividade.** $R$ é reflexiva se contém **todos** os pares do tipo $(a,a)$ (pode conter outros pares também).

![](../../assets/faculdade/periodo1/20240209105831.png)

!!! example "Exemplo ($S=\{1,2,3\}$)"
    - $R_1 = \{(1,1),(2,2),(3,3)\}$
    - $R_2 = \{(1,1),(1,3),(2,1),(2,2),(3,2),(3,3)\}$
    - $R_3 = \{(1,1),(2,1),(2,2),(3,3)\}$

    Todas são reflexivas.

**Simetria.** $R$ é simétrica se, sempre que $(a,b) \in R$, também vale $(b,a) \in R$.

![](../../assets/faculdade/periodo1/20240209110215.png)

!!! example "Exemplo ($S=\{1,2,3\}$)"
    - $R_1 = \{(1,2),(1,3),(2,1),(2,3),(3,1),(3,2)\}$
    - $R_2 = \{(1,1),(2,2),(3,3)\}$
    - $R_3 = \{(1,1),(1,2),(1,3),(2,1),(2,2),(2,3),(3,1),(3,2),(3,3)\}$
    - $R_4 = \{(1,2),(2,1),(2,2)\}$

    Todas são simétricas.

**Antissimetria.** $R$ é antissimétrica se, sempre que $(a,b)\in R$ e $(b,a)\in R$, então $a=b$ (ou seja, não há pares "ida e volta" entre elementos distintos).

![](../../assets/faculdade/periodo1/20240209111445.png)

!!! example "Exemplo ($A=\{1,2,3\}$)"
    - $R_1 = \{(1,2),(1,3),(2,3),(3,2)\}$ — não é antissimétrica? Na verdade, contém $(2,3)$ e $(3,2)$ com $2\neq3$, o que violaria antissimetria; os demais exemplos abaixo são de fato antissimétricos.
    - $R_2 = \{(1,1),(2,2),(3,3)\}$
    - $R_3 = \{(1,1)\}$
    - $R_4 = \{(1,1),(2,1),(3,2)\}$

**Transitividade.** $R$ é transitiva se, sempre que $(a,b)\in R$ e $(b,c)\in R$, então $(a,c)\in R$.

![](../../assets/faculdade/periodo1/20240209112201.png)

!!! example "Exemplo ($T=\{1,2,3\}$)"
    - $R_1 = \{(1,2),(1,3),(2,3)\}$
    - $R_2 = \{(1,1),(1,2),(1,3),(2,3),(3,2)\}$
    - $R_3 = \{(1,1),(1,2),(1,3),(2,2),(2,3),(3,3)\}$

    Todas são transitivas.

!!! tip "Observação"
    Relações do tipo $R = \{(a,a),(a{+}1,a{+}1),\dots,(a{+}n,a{+}n)\}$ (só pares "espelho") são simultaneamente reflexivas, simétricas, antissimétricas e transitivas.

!!! example "Exemplo: $S=\{1,2,3,4,5\}$, dê exemplos de relações que são..."
    - **Apenas reflexivas:** $R_1 = \{(1,1),(2,2),(3,3),(4,4),(5,5)\}$
    - **Apenas simétricas:** $R_2 = \{(1,2),(2,1)\}$
    - **Apenas antissimétricas:** $R_3 = \{(1,3),(4,5)\}$
    - **Apenas transitivas:** $R_4 = \{(1,2),(1,3),(2,3),(4,4),(4,5),(5,4),(5,5)\}$
    - **Nenhuma propriedade:** $R_5 = \{(1,2),(1,3),(1,4),(2,1),(2,5)\}$
    - **Reflexiva, simétrica, antissimétrica e transitiva:** $R_6 = \{(1,1),(2,2),(3,3),(4,4),(5,5)\}$

### Combinando e compondo relações

Como relações são conjuntos de pares, podemos aplicar as operações usuais de conjuntos (união, interseção, diferença) a elas:

![](../../assets/faculdade/periodo1/20240221072858.png)

**Composição de relações.** Dadas $R \subseteq A\times B$ e $S \subseteq B\times C$:

![](../../assets/faculdade/periodo1/20240221073100.png)

$$S\circ R = \{(a,c) \mid a\in A, c\in C, \exists\, b\in B: (a,b)\in R \land (b,c)\in S\}$$

![](../../assets/faculdade/periodo1/20240221073446.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240221074000.png)

    Para achar $S\circ R$: fixamos o primeiro par de $R$ e percorremos $S$, de modo que, se o segundo elemento do par de $R$ coincidir com o primeiro elemento de algum par de $S$, então o par (primeiro elemento de $R$, segundo elemento de $S$) pertence a $S\circ R$. Repetimos para cada par de $R$.

    !!! note
        A relação à direita do "$\circ$" é a relação cujos pares fixamos primeiro.

    ![](../../assets/faculdade/periodo1/20240221075126.png)
    ![](../../assets/faculdade/periodo1/20240221075206.png)
    ![](../../assets/faculdade/periodo1/20240221075225.png)
    ![](../../assets/faculdade/periodo1/20240221075314.png)
    ![](../../assets/faculdade/periodo1/20240221075332.png)

    Logo, $S\circ R = \{(1,0),(1,1),(2,1),(2,2),(3,0),(3,1)\}$.

### Potências de uma relação

$$R^n = \underbrace{R \circ R \circ \dots \circ R}_{n \text{ vezes}}$$

![](../../assets/faculdade/periodo1/20240221075615.png)

Logo, $R^2 = R\circ R$, $R^3 = R^2 \circ R$, e assim por diante.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240221075716.png)
    ![](../../assets/faculdade/periodo1/20240221080413.png)
    ![](../../assets/faculdade/periodo1/20240221080449.png)
    ![](../../assets/faculdade/periodo1/20240221080506.png)
    ![](../../assets/faculdade/periodo1/20240221080520.png)

    A partir de um certo ponto, as potências de relações começam a se repetir (estabilizam).

!!! tip
    Se $R$ é reflexiva, $R^n$ também é, para todo $n\ge1$.

**Teorema.**

![](../../assets/faculdade/periodo1/20240221081526.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20240221081540.png)

    $(a,b)\in R \land (b,c)\in R \to (a,c)\in R$

    ![](../../assets/faculdade/periodo1/20240221081549.png)

    Prova por indução: ![](../../assets/faculdade/periodo1/20240221083003.png)

### Representando relações

**Usando matrizes.**

![](../../assets/faculdade/periodo1/20240221083632.png)

!!! note "Observações"
    - O número de linhas da matriz é dado pelo número de elementos de $A$, e o número de colunas pelo número de elementos de $B$ (pois a relação vai de $A$ para $B$; se fosse de $B$ para $A$, seria a matriz transposta).
    - É possível compor relações multiplicando suas matrizes: basta que o resultado da multiplicação (booleana) seja maior que $0$ para que $M_{ij}=1$ na matriz composta.

!!! example "Exemplo: represente a relação usando matrizes"
    ![](../../assets/faculdade/periodo1/20240221083657.png)
    ![](../../assets/faculdade/periodo1/20240221084856.png)

    **Potências de $R$:**

    ![](../../assets/faculdade/periodo1/20240221095633.png)

!!! example "Exemplo: represente a união, interseção e composição das relações usando matrizes"
    ![](../../assets/faculdade/periodo1/20240221091347.png)

    **União:** ![](../../assets/faculdade/periodo1/20240221091406.png)

    **Interseção:** ![](../../assets/faculdade/periodo1/20240221111016.png)

    **Composição:** ![](../../assets/faculdade/periodo1/20240221091430.png) ![](../../assets/faculdade/periodo1/20240221111331.png)

**Usando dígrafos (grafo direcionado).**

![](../../assets/faculdade/periodo1/20240221091806.png)
![](../../assets/faculdade/periodo1/20240221091826.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240221094223.png)

    **Potências de $R$:**

    ![](../../assets/faculdade/periodo1/20240221094935.png)

!!! example "Exemplo: represente a união, interseção e composição das relações usando dígrafos"
    ![](../../assets/faculdade/periodo1/20240221103527.png)

    **União:** ![](../../assets/faculdade/periodo1/20240221103618.png)

    **Interseção:** ![](../../assets/faculdade/periodo1/20240221110112.png)

    **Composição:** ![](../../assets/faculdade/periodo1/20240221110051.png)

### Caminho de uma relação

![](../../assets/faculdade/periodo1/20240225234957.png)

O **tamanho** do caminho é o número de arestas percorridas.

**Teorema.**

![](../../assets/faculdade/periodo1/20240225235016.png)

!!! example "Exemplo"
    Dada a relação $R = \{(1,1),(1,3),(2,1),(2,5),(3,1),(3,4),(4,2)\}$, qual o menor caminho de $(1,5)$?

    ![](../../assets/faculdade/periodo1/20240226010055.png)

    O menor caminho tem tamanho $n=4$: $1 \to 3 \to 4 \to 2 \to 5$.

### Fechos

O **fecho** de uma relação em relação a uma propriedade é a união entre essa relação e o menor conjunto adicional de pares necessário para que a propriedade seja satisfeita.

**Fecho reflexivo.**

![](../../assets/faculdade/periodo1/20240223195243.png)

!!! example "Exemplo"
    Seja $A=\{1,2,3,4\}$ e $R=\{(1,2),(3,4),(4,4)\}$. Qual o fecho reflexivo de $R$?

    $$\Delta = \{(1,1),(2,2),(3,3)\}$$

    $$\text{Fecho reflexivo}(R) = R \cup \Delta = \{(1,2),(3,4),(4,4)\} \cup \{(1,1),(2,2),(3,3)\}$$

    $$= \{(1,1),(1,2),(2,2),(3,3),(3,4),(4,4)\}$$

**Fecho simétrico.**

![](../../assets/faculdade/periodo1/20240225233520.png)

A relação $R^{-1}$ equivale à matriz transposta de $R$.

!!! example "Exemplo"
    Com o mesmo $R$ acima: $R^{-1} = \{(2,1),(4,3),(4,4)\}$.

    $$\text{Fecho simétrico}(R) = R \cup R^{-1} = \{(1,2),(3,4),(4,4)\} \cup \{(2,1),(4,3),(4,4)\}$$

    $$= \{(1,2),(2,1),(3,4),(4,3),(4,4)\}$$

**Fecho transitivo.**

![](../../assets/faculdade/periodo1/20240226004301.png)

!!! note
    $R^* = R \cup R^2 \cup R^3 \cup \dots$

![](../../assets/faculdade/periodo1/20240226004618.png)
![](../../assets/faculdade/periodo1/20240226010553.png)
![](../../assets/faculdade/periodo1/20240226010628.png)

!!! example "Exemplo"
    Dado $A=\{1,2,3,4\}$ e $R=\{(1,2),(2,1),(2,3),(3,4),(4,1)\}$, ache o fecho transitivo de $R$.

    ![](../../assets/faculdade/periodo1/20240226020817.png)
    ![](../../assets/faculdade/periodo1/20240226020836.png)
    ![](../../assets/faculdade/periodo1/20240226020845.png)
    ![](../../assets/faculdade/periodo1/20240226020852.png)

    O fecho transitivo de $R$ é a relação representada pela matriz $M_{R^*}$.

### Relação de equivalência

Uma relação é de **equivalência** se é reflexiva, simétrica e transitiva simultaneamente.

![](../../assets/faculdade/periodo1/20240226021605.png)

Se $R$ é relação de equivalência, $(a,b)\in R \leftrightarrow a$ é equivalente a $b$.

!!! example "Exemplo: $R = \{(a,b) \mid a-b \in \mathbb{Z}\}$"
    ![](../../assets/faculdade/periodo1/20240226022419.png)

    - **Reflexiva:** $a-a=0$, que é inteiro, logo todo par $(a,a)$ está na relação.
    - **Simétrica:** se $a-b$ é inteiro, $b-a$ também é (é o negativo), logo $(a,b)\in R \Rightarrow (b,a)\in R$.
    - **Transitiva:** suponha $(a,b)$: $a-b=I\in\mathbb{Z}$, e $(b,c)$: $b-c=Z\in\mathbb{Z}$. Então $b=a-I$, logo $a-I-c=Z \Rightarrow a-c = I-Z$ (inteiro). Logo $(a,c)\in R$.

!!! example "Exemplo: $R = \{(a,b) \mid a\equiv b \pmod m\}$"
    ![](../../assets/faculdade/periodo1/20240226025317.png)

    - **Reflexiva:** $m\mid(a-a)=m\mid0$, verdadeiro.
    - **Simétrica:** se $m\mid(a-b)$, então $mx=a-b$ para algum $x$; multiplicando por $-1$, $m(-x)=b-a$, logo $m\mid(b-a)$.
    - **Transitiva:** suponha $m\mid(a-b)$ e $m\mid(b-c)$, isto é, $mx=a-b$ e $my=b-c$. Somando: $m(x+y) = a-c$, logo $m\mid(a-c)$.

!!! example "Exemplo: $R = \{((a,b),(c,d)) \mid ad=bc\}$"
    ![](../../assets/faculdade/periodo1/20240226032143.png)

    - **Reflexiva:** $(a,b)$ e $(a,b)$: $ab=ab$, verdadeiro.
    - **Simétrica:** se $ad=bc$, então $bc=ad$, logo $(b,a)$ e $(d,c)$ também se relacionam.
    - **Transitiva:** se $ad=bc$ e $cf=de$, então $d/c=b/a$ e $d/c=f/e$, logo $b/a=f/e \Rightarrow af=be$, satisfazendo a transitividade.

**Classes de equivalência.** O conjunto de todos os elementos equivalentes a um dado elemento $a$, denotado $[a]_R$.

![](../../assets/faculdade/periodo1/20240226212134.png)
![](../../assets/faculdade/periodo1/20240226212147.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240226212203.png)

    $[0]_R = \{4k \mid k\in\mathbb{Z}\} \qquad [1]_R = \{1+4k \mid k\in\mathbb{Z}\}$

    ![](../../assets/faculdade/periodo1/20240226212846.png)

    Classes de equivalência de $R$:

    - $[0000]_R = \{0000\}$
    - $[1000]_R = \{1000,0100,0010,0001\}$
    - $[1100]_R = \{1100,1010,1001,0110,0101,0011\}$
    - $[1110]_R = \{1110,1011,1101,0111\}$
    - $[1111]_R = \{1111\}$

**Teorema.** Se dois elementos se relacionam, suas classes de equivalência são **iguais**; consequentemente, $[a]\cap[b] \neq \varnothing$ se e somente se $[a]=[b]$.

![](../../assets/faculdade/periodo1/20240226213302.png)

!!! example "Exemplo"
    Usando o exemplo anterior, $1110$ se relaciona com $0111$; logo $(1110,0111)\in R$ e $[1110]=[0111]$, portanto $[1110]\cap[0111]\neq\varnothing$.

**Partição de um conjunto.** Uma relação de equivalência sobre $S$ sempre induz uma partição de $S$ em classes disjuntas, cuja união recupera $S$ por completo.

![](../../assets/faculdade/periodo1/20240226213420.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240226214531.png)

    Apenas a letra (b) é uma partição válida do conjunto $\{1,2,3,4,5,6\}$: na letra (a), $\{1,2\}\cap\{2,3,4,5,6\} \neq \varnothing$ (não são disjuntos); na letra (c), a união dos subconjuntos é diferente de $\{1,2,3,4,5,6\}$, pois falta o elemento $3$.

    ![](../../assets/faculdade/periodo1/20240226214546.png)

    $$[1]=\{1\} \qquad [2]=[3]=[6]=\{2,3,6\} \qquad [4]=\{4\} \qquad [5]=\{5\}$$

    $$R = \{(1,1),(2,2),(2,3),(2,6),(3,2),(3,3),(3,6),(6,2),(6,3),(6,6),(4,4),(5,5)\}$$

    **Matriz de $R$:** ![](../../assets/faculdade/periodo1/20240226220701.png)

    (elementos que se relacionam ficam agrupados juntos na matriz.)

### Relações de ordem

**Ordem parcial.** Uma relação $R$ em $A$ é de **ordem parcial** se é reflexiva, antissimétrica e transitiva. Se $R$ é ordem parcial, $(a,b)\in R \leftrightarrow a \le b$.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240226221907.png)

**Conjunto parcialmente ordenado (poset).** É um conjunto $S$ junto com uma ordem parcial $R$ (por exemplo, $\subseteq$, $\mid$, etc.), denotado $(S,R)$.

!!! example "Exemplo: $P(S)$ com $\subseteq$"
    ![](../../assets/faculdade/periodo1/20240226222512.png)

    $S=\{a,b,c\}$, $P(S) = \{\varnothing,\{1\},\{2\},\{3\},\{1,2\},\{1,3\},\{2,3\},\{1,2,3\}\}$.

    - $P(S)$ é reflexiva: todo conjunto está contido nele mesmo.
    - $P(S)$ é antissimétrica: se $a\subseteq b$ e $b\subseteq a$, então $a=b$.
    - $P(S)$ é transitiva: se $a\subseteq b$ e $b\subseteq c$, então $a\subseteq c$.

!!! example "Exemplo: $\mathbb{Z}^+$ com $x\le y \leftrightarrow x\mid y$"
    ![](../../assets/faculdade/periodo1/20240226223105.png)

    - Reflexiva: $\forall x\in\mathbb{Z}^+$, $x\mid x$.
    - Antissimétrica: $\forall x,y$, se $x\mid y$ e $y\mid x$, então $x=y$ (pois são positivos).
    - Transitiva: $\forall x,y,z$, se $x\mid y$ e $y\mid z$, então $x\mid z$.

    Nessa relação, é falso que $2 \le 3$ e que $7\le100$, mas é verdade que $2\le10$ (pois $2\mid10$).

    ![](../../assets/faculdade/periodo1/20240226223923.png)
    ![](../../assets/faculdade/periodo1/20240226224021.png)
    ![](../../assets/faculdade/periodo1/20240226230001.png)

**Diagrama de Hasse.** É uma representação mais "enxuta" de uma ordem parcial usando dígrafos, omitindo laços (reflexividade) e arestas implícitas por transitividade. Elementos "menores" ficam na base.

![](../../assets/faculdade/periodo1/20240226225242.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240226224156.png)
    ![](../../assets/faculdade/periodo1/20240226232022.png)

    ![](../../assets/faculdade/periodo1/20240226225726.png)
    ![](../../assets/faculdade/periodo1/20240226232051.png)
    ![](../../assets/faculdade/periodo1/20240226232100.png)

    ![](../../assets/faculdade/periodo1/20240226225800.png)
    ![](../../assets/faculdade/periodo1/20240226232126.png)

    ![](../../assets/faculdade/periodo1/20240226225814.png)
    ![](../../assets/faculdade/periodo1/20240226232238.png)

**Conjunto totalmente ordenado.** Quando quaisquer dois elementos são comparáveis entre si (um sempre $\le$ o outro).

![](../../assets/faculdade/periodo1/20240226230054.png)

**Ordem lexicográfica.** Generaliza a ordem alfabética para tuplas/cadeias, comparando posição por posição.

![](../../assets/faculdade/periodo1/20240228195154.png)
![](../../assets/faculdade/periodo1/20240228195115.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240228195241.png)

    ![](../../assets/faculdade/periodo1/20240228195248.png) — Verdadeiro, Verdadeiro, Verdadeiro.

**Definindo a ordem lexicográfica a partir de $n$ posets:**

![](../../assets/faculdade/periodo1/20240228195342.png)

**Ordem lexicográfica de cadeias (strings de tamanhos diferentes):**

![](../../assets/faculdade/periodo1/20240228195453.png)

!!! example "Exemplo: $(6,8) \le (6,8,0)$?"
    $6 \le_1 6$: iguais, então comparamos a posição seguinte. $8 \le_2 8$: iguais, então comparamos a posição seguinte. Como a primeira tupla "acabou" (posição vazia) e a segunda tem $0$, e vazio $\le 0$, concluímos que $(6,8) \le (6,8,0)$. Verdadeiro.

**Elementos maximais e minimais.** Um elemento é **maximal** se nenhum outro elemento do conjunto é estritamente maior; é **minimal** se nenhum outro é estritamente menor. Pode haver vários maximais/minimais ao mesmo tempo (diferente de maior/menor elemento).

![](../../assets/faculdade/periodo1/20240228213728.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240228214227.png)

    Maximais: $12, 20, 25$. Minimais: $2, 5$.

**Maior/menor elemento.** Diferente de maximal/minimal: o **maior elemento** precisa ser $\ge$ todos os outros do conjunto (e é único, se existir); o **menor elemento**, análogo.

![](../../assets/faculdade/periodo1/20240228213744.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240228223535.png)

    Maior elemento: não existe. Menor elemento: não existe.

**Limitante superior/inferior.** Um limitante superior de um subconjunto $B$ é qualquer elemento (do poset, não necessariamente de $B$) maior ou igual a todos os elementos de $B$; analogamente para limitante inferior.

![](../../assets/faculdade/periodo1/20240228213756.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240228223608.png)

    Limitantes superiores de $\{4,10\}$: $20$. Limitantes inferiores: $2$.

**Supremo e ínfimo.** O **supremo** é o menor dos limitantes superiores; o **ínfimo** é o maior dos limitantes inferiores.

![](../../assets/faculdade/periodo1/20240228213811.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240228223608.png)

    Para $\{4,10\}$: limite superior $20$, limite inferior $2$, supremo $20$, ínfimo $2$.

!!! example "Mais exemplos"
    ![](../../assets/faculdade/periodo1/20240228233725.png)
    ![](../../assets/faculdade/periodo1/20240229002142.png)
    ![](../../assets/faculdade/periodo1/20240229002203.png)

!!! example "Exemplo completo"
    Ache maximais, minimais, maior/menor elemento, limites superiores e inferiores de $\{a,b,c\}$, $\{h,j\}$ e $\{a,c,d,f\}$, bem como seus supremos e ínfimos.

    ![](../../assets/faculdade/periodo1/20240229003531.png)

    - Maximais: $h,j$ — Minimais: $a$
    - Maior elemento: não existe — Menor elemento: $a$
    - Limite superior $\{a,b,c\}$: $e,f,h,j$ — Limite inferior: $a$
    - Supremo $\{a,b,c\}$: $e$ — Ínfimo: $a$
    - Limite superior $\{h,j\}$: não existe — Limite inferior: $a,b,c,d,e,f$
    - Supremo $\{h,j\}$: não existe — Ínfimo: $f$
    - Limite superior $\{a,c,d,f\}$: $f,h,j$ — Limite inferior: $a$
    - Supremo $\{a,c,d,f\}$: $f$ — Ínfimo: $a$

!!! example "Outro exemplo"
    ![](../../assets/faculdade/periodo1/20240229004502.png)

    - Maximais: $l,m$ — Minimais: $a,b,c$
    - Maior/menor elemento: não existem
    - Limite superior $\{a,b,c\}$: $k,l,m$ — Supremo: $k$
    - Limite inferior $\{f,g,h\}$: não existe — Ínfimo: não existe

**Reticulado.** Um poset é um reticulado se **todo** par de elementos possui supremo e ínfimo.

![](../../assets/faculdade/periodo1/20240229002433.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240229002445.png)

    Apenas (a) e (c) são reticulados; em (b), o par $\{b,c\}$ não possui supremo:

    - Limite superior $(\{b,c\})$: $d,e,f$ — Limite inferior: $a$
    - Supremo: não existe — Ínfimo: $a$

**Aplicação.**

![](../../assets/faculdade/periodo1/20240229003234.png)
![](../../assets/faculdade/periodo1/20240229003242.png)
![](../../assets/faculdade/periodo1/20240229003256.png)

## Grafos

Um grafo é uma estrutura formada por **vértices** (ou nós) conectados por **arestas**, usada para modelar relações entre pares de objetos — redes sociais, mapas de estradas, dependências entre tarefas, e muito mais.

![](../../assets/faculdade/periodo1/20240301202359.png)

### Elementos e tipos básicos

Um **laço** é uma aresta que liga um vértice a ele mesmo (par de vértices idênticos).

**Grafo simples.** Sem laços e sem arestas paralelas (no máximo uma aresta entre cada par de vértices).

![](../../assets/faculdade/periodo1/20240308190438.png)
![](../../assets/faculdade/periodo1/20240308190314.png)
![](../../assets/faculdade/periodo1/20240308190510.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308190940.png)
    ![](../../assets/faculdade/periodo1/20240308191247.png)

**Pseudografo.** Permite laços e arestas paralelas.

![](../../assets/faculdade/periodo1/20240308191505.png)

**Multigrafo.** Permite arestas paralelas, mas não laços.

![](../../assets/faculdade/periodo1/20240308191259.png)
![](../../assets/faculdade/periodo1/20240308191329.png)

Todo multigrafo é um pseudografo, mas nem todo pseudografo é um multigrafo (pseudografos podem ter laços).

### Grau de um vértice

O **grau** de um vértice é o número de arestas incidentes a ele.

![](../../assets/faculdade/periodo1/20240308192008.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308192015.png)

![](../../assets/faculdade/periodo1/20240308192104.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240308192137.png)

    ![](../../assets/faculdade/periodo1/20240308192535.png)

    Vértices isolados: $5$. Vértices pendentes: $4$. Vértices de grau ímpar: $3,4$. Vértices de grau par: $1,2,5$.

### Mais tipos de grafo

**Grafo regular ($k$-regular).** Todos os vértices têm o mesmo grau $k$.

![](../../assets/faculdade/periodo1/20240308192321.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308192331.png) — é um grafo $2$-regular.

**Grafo nulo (vazio).** Sem nenhuma aresta.

![](../../assets/faculdade/periodo1/20240308195739.png)
![](../../assets/faculdade/periodo1/20240308195814.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308195822.png)

**Grafo completo ($K_n$).** Todo par de vértices é conectado por uma aresta.

![](../../assets/faculdade/periodo1/20240308195849.png)
![](../../assets/faculdade/periodo1/20240308195921.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308195935.png)

### Soma dos graus de um grafo

A soma dos graus de todos os vértices de um grafo é sempre igual a **duas vezes** o número de arestas (cada aresta contribui com $1$ grau para cada um dos seus dois extremos) — e por isso é sempre par.

![](../../assets/faculdade/periodo1/20240308194907.png)

$$|E| = \frac{\sum_v \text{grau}(v)}{2}$$

A soma dos graus de um grafo $k$-regular com $n$ vértices é $kn$, logo o número de arestas é $kn/2$.

![](../../assets/faculdade/periodo1/20240308195118.png)

Para **qualquer** grafo, o número de vértices de grau ímpar é sempre **par** (consequência direta de a soma total dos graus ser par).

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20240308195707.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240308194447.png)
    ![](../../assets/faculdade/periodo1/20240308194454.png)

    Sim, a soma dos graus é par e nenhum vértice ultrapassa o grau máximo possível.

    ![](../../assets/faculdade/periodo1/20240308194750.png)
    ![](../../assets/faculdade/periodo1/20240308194800.png)

    Não — a soma dos graus é ímpar, e não é possível incluir um vértice de grau 5.

    ![](../../assets/faculdade/periodo1/20240308194832.png)

    Não — a soma dos graus é ímpar.

!!! tip "Observações"
    - Em um grafo simples com $k$ vértices, é impossível que algum vértice tenha grau $k$ (ele não pode ter aresta para si mesmo).
    - A quantidade de arestas de $K_n$ é dada por $\dfrac{n(n-1)}{2}$:

    ![](../../assets/faculdade/periodo1/20240308200243.png)
    ![](../../assets/faculdade/periodo1/20240308200328.png)

### Complemento de um grafo

![](../../assets/faculdade/periodo1/20240308200525.png)

O complemento de um grafo $G$ é o grafo $G'$ com o mesmo conjunto de vértices, tal que $G \cup G'$ forma o grafo completo correspondente.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308200810.png)

**Propriedades:**

- Um grafo regular tem complemento regular: o complemento de um grafo $k$-regular com $n$ vértices é um grafo $(n-1-k)$-regular.
- O complemento de $K_n$ é $N_n$ (o grafo nulo com $n$ vértices).

### Outros tipos de grafo

**Grafo cíclico (ciclo, $C_n$).**

![](../../assets/faculdade/periodo1/20240308201808.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308201816.png)

**Grafo roda ($W_n$).** Um ciclo $C_n$ com um vértice central conectado a todos os demais.

![](../../assets/faculdade/periodo1/20240308201838.png)

$W_n$ possui $n+1$ vértices; todos têm grau $3$, exceto o vértice central, que tem grau $n$.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308201847.png)

**Grafo $n$-cúbico ($Q_n$).**

![](../../assets/faculdade/periodo1/20240308202006.png)
![](../../assets/faculdade/periodo1/20240308202012.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308202140.png) — grafo 3-cúbico.

**Grafo orientado (dígrafo).** As arestas têm direção.

![](../../assets/faculdade/periodo1/20240308202307.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308202313.png)

Os vértices de um dígrafo possuem grau de **entrada** e grau de **saída**:

![](../../assets/faculdade/periodo1/20240308202528.png)

**Multigrafo orientado.**

![](../../assets/faculdade/periodo1/20240308202346.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308202435.png)

!!! example "Exemplos de aplicação"
    ![](../../assets/faculdade/periodo1/20240308203629.png)

    Se o grafo regular possui grau $4$, logo é um $K_5$ (possui 5 vértices). Outra forma de resolver: usando $|E| = \dfrac{r|V|}{2}$, com $20 = \dfrac{4|V|}{2} \Rightarrow |V|=5$... (ajustando a fórmula conforme o enunciado específico).

    ![](../../assets/faculdade/periodo1/20240308204024.png)
    ![](../../assets/faculdade/periodo1/20240308234011.png)

### Grafo bipartido

Um grafo é **bipartido** se seus vértices podem ser divididos em dois grupos, de modo que toda aresta conecta vértices de grupos **diferentes** (nunca dentro do mesmo grupo).

![](../../assets/faculdade/periodo1/20240308204949.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240308231918.png)

    ![](../../assets/faculdade/periodo1/20240308232152.png)

    ![](../../assets/faculdade/periodo1/20240308232247.png)

    ![](../../assets/faculdade/periodo1/20240308232324.png)
    ![](../../assets/faculdade/periodo1/20240308232341.png)
    ![](../../assets/faculdade/periodo1/20240308232631.png)
    ![](../../assets/faculdade/periodo1/20240308232610.png)
    ![](../../assets/faculdade/periodo1/20240308232620.png)

!!! tip "Como saber se um grafo pode ser bipartido"
    Basta tentar colorir os vértices com apenas duas cores, de forma que vértices adjacentes nunca tenham a mesma cor. Se isso for possível, o grafo é bipartido; se duas cores iguais ficarem conectadas por uma aresta, não é.

    !!! example "Exemplos"
        ![](../../assets/faculdade/periodo1/20240311183543.png) — não pode ser bipartido.

        ![](../../assets/faculdade/periodo1/20240311183615.png)

**Grafo bipartido completo ($K_{m,n}$).** Todo vértice de um grupo (tamanho $m$) é conectado a todo vértice do outro grupo (tamanho $n$).

![](../../assets/faculdade/periodo1/20240308231401.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240308233624.png)
    ![](../../assets/faculdade/periodo1/20240308233634.png)

    ![](../../assets/faculdade/periodo1/20240308233650.png)
    ![](../../assets/faculdade/periodo1/20240308233700.png)

### Subgrafos

Um **subgrafo** de $G$ usa um subconjunto dos vértices e arestas de $G$ (mantendo a consistência: uma aresta só pode estar presente se seus dois extremos também estiverem).

![](../../assets/faculdade/periodo1/20240308231703.png)

Todo grafo é subgrafo dele mesmo.

![](../../assets/faculdade/periodo1/20240308231759.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308231723.png)

!!! tip "Observação"
    O número de subgrafos de $K_n$ é $2^{|E|}$, onde $|E| = \dfrac{n(n-1)}{2}$ é o número de arestas de $K_n$.

**Subgrafo próprio.** Um subgrafo que é estritamente menor que o grafo original.

![](../../assets/faculdade/periodo1/20240308231740.png)

**Subgrafo induzido.** Dado um subconjunto de vértices, o subgrafo induzido contém **todas** as arestas originais entre esses vértices.

![](../../assets/faculdade/periodo1/20240308231530.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240308231550.png)

**Clique.** Um subconjunto de vértices tal que todos eles são mutuamente adjacentes (formam um subgrafo completo).

![](../../assets/faculdade/periodo1/20240311173313.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311173321.png)

### Representação de grafos

**Lista de adjacência.** Lista, para cada vértice, seus vizinhos diretos.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311174036.png)

**Lista de adjacência em grafos direcionados.**

![](../../assets/faculdade/periodo1/20240311174125.png)

**Matriz de adjacência.** Matriz $n\times n$ onde a entrada $(i,j)$ indica se há aresta entre os vértices $i$ e $j$.

![](../../assets/faculdade/periodo1/20240311174945.png)
![](../../assets/faculdade/periodo1/20240311175651.png)
![](../../assets/faculdade/periodo1/20240311175958.png)
![](../../assets/faculdade/periodo1/20240311175948.png)

!!! note
    Matrizes de grafos direcionados são, essencialmente, matrizes de relações.

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240311175620.png)

    ![](../../assets/faculdade/periodo1/20240311175745.png)

    ![](../../assets/faculdade/periodo1/20240311175823.png)

### Isomorfismo de grafos

Dois grafos são **isomorfos** se existe uma bijeção entre seus vértices que preserva a adjacência (vértices conectados em um correspondem a vértices conectados no outro).

![](../../assets/faculdade/periodo1/20240311181009.png)
![](../../assets/faculdade/periodo1/20240311181027.png)

!!! example "Exemplo: diga se os grafos são isomorfos"
    ![](../../assets/faculdade/periodo1/20240311181111.png)
    ![](../../assets/faculdade/periodo1/20240311183802.png)

    São isomorfos.

**Propriedades.** O isomorfismo preserva:

![](../../assets/faculdade/periodo1/20240311184322.png)

Se $G_1 \approx G_2$ (isomorfos), vale:

![](../../assets/faculdade/periodo1/20240311184425.png)

!!! note
    - Os graus dos vértices vizinhos também são preservados.
    - A matriz de adjacência de grafos isomorfos é a mesma (a menos de uma permutação de linhas/colunas).

!!! example "Mais exemplos"
    ![](../../assets/faculdade/periodo1/20240311185421.png)
    ![](../../assets/faculdade/periodo1/20240311190209.png)

    ![](../../assets/faculdade/periodo1/20240311190522.png)
    ![](../../assets/faculdade/periodo1/20240311191900.png)
    ![](../../assets/faculdade/periodo1/20240311191908.png)

### Conectividade

**Caminho em um grafo não orientado.** Uma sequência de vértices conectados por arestas sucessivas.

![](../../assets/faculdade/periodo1/20240311193324.png)
![](../../assets/faculdade/periodo1/20240311193340.png)

**Caminho em um multigrafo direcionado.**

![](../../assets/faculdade/periodo1/20240311193429.png)
![](../../assets/faculdade/periodo1/20240311193507.png)

**Circuito ou ciclo.** Um caminho que começa e termina no mesmo vértice.

![](../../assets/faculdade/periodo1/20240311193531.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240311193547.png)

    ![](../../assets/faculdade/periodo1/20240311193604.png)

    ![](../../assets/faculdade/periodo1/20240311193633.png)

**Caminho simples ou circuito simples.** Não repete vértices (exceto, no circuito, o inicial/final).

![](../../assets/faculdade/periodo1/20240311193748.png)

**Grafo conexo.** Existe caminho entre todo par de vértices.

![](../../assets/faculdade/periodo1/20240311194018.png)

**Grafo desconexo.** Possui "ilhas" — pares de vértices sem caminho entre si.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311194456.png)

    Não há caminho de $x_4$ a $x_5$, logo o grafo é desconexo.

**Componente conexo.** Cada "ilha" máxima e conectada dentro de um grafo desconexo.

![](../../assets/faculdade/periodo1/20240311194546.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311194558.png)

    $S_1$ e $S_2$ são componentes conexas de $G$.

**Vértice de corte.** Um vértice cuja remoção desconecta o grafo.

![](../../assets/faculdade/periodo1/20240311195105.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311195113.png)

**Ponte.** Uma aresta cuja remoção desconecta o grafo.

![](../../assets/faculdade/periodo1/20240311195212.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240311195220.png)

**Grafo fortemente conexo** (para dígrafos). Existe caminho direcionado de **qualquer** vértice para **qualquer** outro.

![](../../assets/faculdade/periodo1/20240312000424.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240312002026.png)

**Grafo fracamente conexo.** O grafo subjacente (ignorando a direção das arestas) é conexo, mas o dígrafo em si não é fortemente conexo.

![](../../assets/faculdade/periodo1/20240312002119.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240312002211.png)
    ![](../../assets/faculdade/periodo1/20240312002217.png)

    Pois nunca conseguimos chegar ao $x_7$.

### Caminhos e circuitos eulerianos e hamiltonianos

**Caminho euleriano.** Passa por **todas as arestas** do grafo exatamente uma vez.

![](../../assets/faculdade/periodo1/20240312002238.png)

**Circuito (ou ciclo) euleriano.** É um caminho euleriano que começa e termina no mesmo vértice.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240312002246.png)

**Teorema.** Um grafo conexo possui circuito euleriano se e somente se todo vértice tem grau par; possui caminho euleriano (não necessariamente circuito) se e somente se tem exatamente $0$ ou $2$ vértices de grau ímpar.

![](../../assets/faculdade/periodo1/20240312002318.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20240312002331.png)
    ![](../../assets/faculdade/periodo1/20240312002343.png)
    ![](../../assets/faculdade/periodo1/20240312002356.png)
    ![](../../assets/faculdade/periodo1/20240312002403.png)

**Algoritmo de Hierholzer.** Constrói um circuito euleriano explicitamente, unindo sub-circuitos encontrados sucessivamente.

![](../../assets/faculdade/periodo1/20240312002508.png)

**Passo a passo:**

![](../../assets/faculdade/periodo1/20240312002519.png)

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240312002740.png)

**Teorema.**

![](../../assets/faculdade/periodo1/20240312002816.png)

!!! tip "Resumo"
    Para ser caminho euleriano, o grafo precisa ter $2$ ou $0$ vértices de grau ímpar; para ser circuito euleriano, precisa ter necessariamente $0$ vértices de grau ímpar (todos com grau par).

**Caminho hamiltoniano.** Passa por **todos os vértices** exatamente uma vez (diferente do euleriano, que foca nas arestas).

![](../../assets/faculdade/periodo1/20240312002909.png)

**Circuito (ou ciclo) hamiltoniano.** Um caminho hamiltoniano que retorna ao vértice inicial. Um grafo é dito **hamiltoniano** se possui um ciclo hamiltoniano.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240312015549.png)

![](../../assets/faculdade/periodo1/20240312003218.png)

??? note "Prova"
    ![](../../assets/faculdade/periodo1/20240312003231.png)

Todos os grafos do tipo $2$-regular (ciclos) são hamiltonianos.

**Teoremas úteis para identificar grafos hamiltonianos:**

**Teorema de Dirac.** Se todo vértice de um grafo simples com $n \ge 3$ vértices tem grau $\ge n/2$, o grafo é hamiltoniano.

![](../../assets/faculdade/periodo1/20240312202945.png)

!!! note
    Esse teorema não cobre grafos do tipo $2$-regular, que mesmo assim são hamiltonianos.

**Teorema de Ore.** Se, para todo par de vértices **não adjacentes** $u,v$, $\text{grau}(u)+\text{grau}(v) \ge n$, o grafo é hamiltoniano.

![](../../assets/faculdade/periodo1/20240312203045.png)

!!! note
    Vértices não adjacentes são vértices sem conexão direta entre si.

![](../../assets/faculdade/periodo1/20240312203208.png)

!!! example "Exemplos"
    ![](../../assets/faculdade/periodo1/20240312002924.png)

    ![](../../assets/faculdade/periodo1/20240312002944.png)

!!! tip
    Para ser circuito hamiltoniano, não pode existir nenhum vértice de grau $1$ (ele nunca conseguiria ser "revisitado" numa volta completa).

### Planaridade

Um grafo é **planar** se pode ser desenhado no plano sem que nenhuma aresta cruze outra (duas arestas só podem se encontrar nos vértices onde são incidentes).

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240412010637.png) ($K_4$)

    Apesar de $K_4$ ser planar, dependendo de como é desenhado ele pode *parecer* não planar:

    ![](../../assets/faculdade/periodo1/20240412010737.png)

    Ou seja, para um grafo ser planar, basta que **exista** pelo menos uma representação planar (não importa se outras representações têm cruzamentos).

**Conceitos relacionados:**

- Todo subgrafo de um grafo planar é planar.
- Todo grafo que tem um subgrafo não planar não é planar.
- Todo grafo que contém $K_{3,3}$ ou $K_5$ como subgrafo não é planar.

**Grafos homeomórficos.** Dois grafos são homeomórficos se ambos podem ser obtidos a partir de um mesmo grafo pela inserção de vértices de grau $2$ em suas arestas (uma operação chamada **subdivisão elementar**).

**Teorema de Kuratowski.** Um grafo é planar se e somente se não contém nenhum subgrafo homeomórfico a $K_{3,3}$ ou $K_5$.

**Regiões.** Se $G$ é planar, sua representação planar divide o plano em regiões:

![](../../assets/faculdade/periodo1/20240412011725.png)

**Fórmula de Euler.** Relaciona vértices ($v$), arestas ($e$) e regiões ($f$, incluindo a região externa) de um grafo planar conexo: $v - e + f = 2$.

![](../../assets/faculdade/periodo1/20240412011812.png)

### Coloração

Se $G$ é um grafo simples, uma **coloração** para $G$ é uma atribuição de cores aos vértices de modo que vértices adjacentes tenham sempre cores diferentes. $G$ é dito **$k$-colorível** se é possível colori-lo usando (no máximo) $k$ cores.

O **número cromático** de $G$, denotado $\chi(G)$, é o menor número de cores necessário para colorir $G$.

!!! example "Exemplo"
    ![](../../assets/faculdade/periodo1/20240412013953.png)

**Colorindo vértices:**

![](../../assets/faculdade/periodo1/20240412014058.png)
![](../../assets/faculdade/periodo1/20240412014113.png)
![](../../assets/faculdade/periodo1/20240412020634.png)
![](../../assets/faculdade/periodo1/20240412020705.png)
![](../../assets/faculdade/periodo1/20240412020727.png)
![](../../assets/faculdade/periodo1/20240412020755.png)

**Colorindo mapas.** Uma aplicação clássica: associando cada região de um mapa a um vértice, e cada fronteira entre regiões a uma aresta, colorir o mapa (sem que regiões vizinhas tenham a mesma cor) equivale a colorir esse grafo. O célebre **Teorema das Quatro Cores** garante que todo mapa planar pode ser colorido com no máximo $4$ cores.

![](../../assets/faculdade/periodo1/20240412021811.png)
![](../../assets/faculdade/periodo1/20240412021825.png)

## Árvores

Uma **árvore** é um grafo simples, conexo e **acíclico** (sem ciclos). Árvores aparecem por toda a computação — estruturas de dados, hierarquias de arquivos, árvores de decisão, árvores sintáticas — e têm propriedades combinatórias muito específicas que valem a pena destacar.

### Definição e propriedades básicas

Dado um grafo simples $G$ com $n$ vértices, as afirmações a seguir são **equivalentes** (qualquer uma implica todas as outras):

1. $G$ é uma árvore (conexo e acíclico).
2. $G$ é conexo e possui exatamente $n-1$ arestas.
3. $G$ é acíclico e possui exatamente $n-1$ arestas.
4. $G$ é conexo, e remover qualquer aresta o desconecta (toda aresta é uma ponte).
5. $G$ é acíclico, e adicionar qualquer aresta nova cria exatamente um ciclo.
6. Existe exatamente **um** caminho simples entre qualquer par de vértices de $G$.

!!! tip "Intuição"
    Uma árvore é a forma "mais econômica" possível de manter um grafo conexo: tem o número mínimo de arestas ($n-1$) necessário para conectar $n$ vértices, e qualquer aresta extra criaria um ciclo (redundância).

### Terminologia de árvores enraizadas

Em computação, quase sempre trabalhamos com **árvores enraizadas**: escolhemos um vértice especial, a **raiz**, e orientamos todas as arestas "para fora" dela.

- **Pai** de um vértice $v$ (diferente da raiz): o vértice imediatamente acima de $v$ no caminho até a raiz.
- **Filho** de $v$: todo vértice cujo pai é $v$.
- **Irmãos**: vértices que compartilham o mesmo pai.
- **Ancestral** de $v$: qualquer vértice no caminho entre $v$ e a raiz (incluindo a própria raiz).
- **Descendente** de $v$: qualquer vértice que tem $v$ como ancestral.
- **Folha**: um vértice sem filhos.
- **Vértice interno**: um vértice com pelo menos um filho (inclui a raiz, se ela tiver filhos).
- **Subárvore com raiz em $v$**: a árvore formada por $v$ e todos os seus descendentes.
- **Nível (ou profundidade) de $v$**: o número de arestas no caminho da raiz até $v$ (a raiz tem nível $0$).
- **Altura da árvore**: o maior nível entre todos os vértices (a profundidade máxima).

!!! example "Exemplo"
    Em uma árvore genealógica enraizada em um ancestral comum, cada pessoa é "pai" de seus filhos diretos, "ancestral" de todos os seus descendentes, e uma "folha" se não tiver filhos registrados na árvore.

### Árvores $m$-árias e árvores binárias

Uma árvore enraizada é **$m$-ária** se cada vértice interno tem **no máximo** $m$ filhos; é **$m$-ária completa** se cada vértice interno tem **exatamente** $m$ filhos. O caso $m=2$ é a conhecidíssima **árvore binária**, base de estruturas como heaps, árvores de busca binária (BSTs) e árvores de expressão.

Uma árvore binária é dita **cheia (full)** se todo vértice interno tem exatamente $2$ filhos, e **completa (complete)** se todos os níveis estão totalmente preenchidos, exceto possivelmente o último, que é preenchido da esquerda para a direita.

**Relações entre altura e número de vértices/folhas:**

- Uma árvore $m$-ária completa com $i$ vértices internos tem $n = mi+1$ vértices no total e $\ell = (m-1)i+1$ folhas.
- Uma árvore $m$-ária de altura $h$ tem **no máximo** $m^h$ folhas.
- Se uma árvore $m$-ária com $\ell$ folhas tem altura $h$, então $h \ge \lceil \log_m \ell \rceil$ — e a igualdade vale quando a árvore é completa e balanceada. Essa relação logarítmica é exatamente o motivo pelo qual buscas em árvores binárias balanceadas (como BSTs balanceadas) custam $O(\log n)$: a altura cresce muito mais lentamente do que o número de elementos.

!!! example "Exemplo"
    Uma árvore binária completa e cheia com altura $h=3$ tem, no máximo, $2^3=8$ folhas e $2^4-1=15$ vértices no total (contando todos os níveis, de $0$ a $3$).

### Percursos em árvores (travessias)

Para processar os vértices de uma árvore ordenada (em que os filhos de cada vértice têm uma ordem definida), usamos travessias sistemáticas. As três mais comuns, para árvores binárias, são:

1. **Pré-ordem (preorder):** visita a raiz, depois percorre a subárvore esquerda em pré-ordem, depois a direita em pré-ordem.
2. **Em-ordem (inorder):** percorre a subárvore esquerda em ordem, visita a raiz, depois percorre a subárvore direita em ordem. Em uma árvore de busca binária, essa travessia visita os valores em ordem crescente.
3. **Pós-ordem (postorder):** percorre a subárvore esquerda em pós-ordem, depois a direita em pós-ordem, e só então visita a raiz.

!!! example "Exemplo: árvore de expressão para $(3+5)\times 2$"
    A raiz é $\times$, com filho esquerdo $+$ (que tem filhos $3$ e $5$) e filho direito $2$.

    - Pré-ordem: $\times, +, 3, 5, 2$ (notação prefixa)
    - Em-ordem: $3, +, 5, \times, 2$ (próxima da notação infixa usual)
    - Pós-ordem: $3, 5, +, 2, \times$ (notação pós-fixa, usada em calculadoras RPN)

### Árvores geradoras (spanning trees)

Dado um grafo conexo $G$, uma **árvore geradora** (spanning tree) de $G$ é uma subárvore de $G$ que inclui **todos** os vértices de $G$, usando o menor número possível de arestas ($n-1$) — ou seja, é uma árvore "escondida dentro" do grafo que mantém tudo conectado, removendo arestas redundantes (que fariam parte de algum ciclo).

Todo grafo conexo possui pelo menos uma árvore geradora. Quando as arestas do grafo têm pesos (por exemplo, distâncias ou custos), a **árvore geradora mínima** (minimum spanning tree, MST) é a árvore geradora cuja soma dos pesos das arestas é a menor possível — um problema clássico resolvido por algoritmos como os de Kruskal e Prim, estudados em disciplinas de algoritmos e estruturas de dados.
