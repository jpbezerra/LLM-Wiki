# INFORMÁTICA TEÓRICA

!!! info "Referência"
    Material baseado no curso de Informática Teórica (Teoria da Computação) do CIn/UFPE — [cin.ufpe.br/~if689/1-2025](https://www.cin.ufpe.br/~if689/1-2025/), seguindo de perto o livro *Introduction to the Theory of Computation* de Michael Sipser (pág. 305 a 323 para a parte de complexidade).

Este material percorre a teoria da computação clássica: o que é um algoritmo e o que significa um problema ser "resolvível"; os modelos de computação cada vez mais poderosos (autômatos finitos, autômatos com pilha, máquinas de Turing); e as duas grandes perguntas que a área procura responder — **o que pode ser computado** (computabilidade/decidibilidade) e **o que pode ser computado de forma eficiente** (complexidade).

## Conceitos Iniciais

Antes de entrar nos modelos formais, vale fixar o vocabulário que vai aparecer o tempo todo no resto da disciplina.

Um **método** é um conjunto organizado de passos ou estratégias usado para resolver um problema ou alcançar um objetivo. Um **algoritmo** é a versão precisa dessa ideia: uma sequência finita, precisa e ordenada de instruções que leva à solução de um problema específico. Formalmente, é um método eficaz expresso como uma lista finita de instruções bem definidas para o cálculo de uma função — a partir de um estado inicial e de uma entrada, as instruções descrevem uma computação que avança por um número finito de estados sucessivos bem definidos até produzir uma saída e parar em um estado final.

!!! tip "Algoritmo como máquina de estados"
    Essa definição já antecipa o fio condutor de toda a disciplina: um algoritmo pode ser visto como uma **máquina de estados**. Os modelos que vamos estudar (autômatos finitos, autômatos com pilha, máquinas de Turing) são justamente formalizações cada vez mais poderosas dessa ideia.

### Solubilidade de problemas

Um problema é **solúvel** quando existe um método ou algoritmo que chega a uma conclusão para ele, e é **insolúvel** quando não existe nenhum método ou algoritmo capaz de produzir uma resposta. Resolver um problema matemático, nesse sentido, é aplicar um método/algoritmo para encontrar uma solução, caso ela exista.

Um caso particularmente importante é o dos **problemas de decisão**: problemas cuja resposta é simplesmente sim ou não. Foi justamente a definição de Alan Turing para as máquinas de Turing que permitiu uma definição *exata* de decidibilidade — e, com ela, a possibilidade de demonstrar que certos problemas são, de fato, indecidíveis. Isso ajudou a formalizar matematicamente o próprio conceito de algoritmo.

| Tipo de problema de decisão | Definição |
| --- | --- |
| **Decidível** | É um problema de decisão e é solúvel: existe um algoritmo que sempre termina com a resposta correta (sim/não). |
| **Indecidível** | É um problema de decisão e é insolúvel: não existe nenhum algoritmo que resolva o problema para todas as entradas. |

!!! example "Dois problemas históricos indecidíveis"
    - **Entscheidungsproblem**: existe um algoritmo que, dado qualquer enunciado matemático formal em lógica de primeira ordem, determina se ele é verdadeiro ou falso?
    - **10º problema de Hilbert**: existe um algoritmo que decide se uma equação diofantina tem solução (raízes inteiras)?

    Ambos acabaram se revelando indecidíveis — e a própria tentativa de resolvê-los é o que motivou Church e Turing a formalizar o conceito de algoritmo.

---

## Linguagens Regulares

### Autômatos finitos

Um **autômato finito** é um modelo matemático de computador: uma máquina abstrata com um número finito de estados. É o modelo mais simples que vamos estudar, e serve de base para tudo que vem depois.

Formalmente, um autômato finito é definido por uma **5-upla** $M = (Q, \Sigma, \delta, q_0, F)$, onde:

| Componente | Significado |
| --- | --- |
| $Q$ | conjunto finito de **estados** — as diferentes configurações em que a máquina pode se encontrar |
| $\Sigma$ | **alfabeto** finito de símbolos que o autômato pode ler na cadeia de entrada |
| $\delta$ | **função de transição**, $\delta: Q \times \Sigma \rightarrow Q$ — determina para qual estado a máquina vai, dado o estado atual e o símbolo lido |
| $q_0$ | **estado inicial**, $q_0 \in Q$ |
| $F$ | conjunto de **estados finais/de aceitação**, $F \subseteq Q$ — se, ao terminar de ler a entrada, o autômato estiver em um desses estados, a cadeia é aceita |

#### Diagrama de estados

A forma usual de representar um autômato é por um diagrama de estados: o estado inicial $q_0$ é indicado por uma seta vinda "do nada", os estados de aceitação são desenhados com círculo duplo, e cada seta entre estados (rotulada por um símbolo do alfabeto) é chamada de **transição**. Se, ao final da leitura, a cadeia não termina em um estado de aceitação, ela é rejeitada.

A representação do autômato $M_1$ a seguir ilustra essas convenções:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image.png)

Sua descrição formal é $M_1 = (Q, \Sigma, \delta, q_0, F)$, com $Q = \{q_1, q_2, q_3\}$, $\Sigma = \{0, 1\}$, $q_0 = q_1$, $F = \{q_2\}$, e função de transição:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%201.png)

#### Linguagem de um autômato

Se $A$ é o conjunto de todas as cadeias que uma máquina $M$ aceita, dizemos que $A$ é a **linguagem de $M$**, escrito $L(M) = A$, e que $M$ *reconhece* (ou *aceita*) $A$.

!!! note "Aceitar cadeias vs. reconhecer linguagens"
    Uma máquina aceita *várias* cadeias, mas reconhece apenas *uma* linguagem. Mesmo que uma máquina não aceite cadeia alguma, ela ainda reconhece uma linguagem — o conjunto vazio.

Formalmente: seja $M = (Q, \Sigma, \delta, q_0, F)$ e seja $w = w_1 w_2 \ldots w_n$ uma cadeia com cada $w_i \in \Sigma$. Dizemos que $M$ aceita $w$ se existe uma sequência de estados $r_0, r_1, \ldots, r_n \in Q$ tal que:

1. $r_0 = q_0$ — a máquina começa no estado inicial;
2. $\delta(r_i, w_{i+1}) = r_{i+1}$ para $i = 0, \ldots, n-1$ — a máquina avança de estado em estado conforme a função de transição;
3. $r_n \in F$ — a máquina aceita se termina em um estado de aceitação.

$M$ reconhece a linguagem $A$ se $A = \{w \mid M \text{ aceita } w\}$. Uma linguagem é chamada de **linguagem regular** se algum autômato finito a reconhece.

!!! example "Exemplo"
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%202.png)

    A linguagem reconhecida é $A = \{w \mid w \text{ contém pelo menos um } 1 \text{ e um número par de } 0\text{'s segue após o último } 1 \text{ da cadeia}\}$.

#### Exemplos de autômatos

**1. $M_2$** — aceita cadeias que terminam em 1.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%203.png)

| | 0 | 1 |
| --- | --- | --- |
| $q_1$ | $q_1$ | $q_2$ |
| $q_2$ | $q_1$ | $q_2$ |

$Q = \{q_1, q_2\}$, $\Sigma = \{0,1\}$, $q_0 = q_1$, $F = \{q_2\}$. Linguagem: $A = \{w \mid w \text{ termina em } 1\}$.

**2. $M_3$** — aceita cadeias que terminam em 0 (ou a cadeia vazia).

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%204.png)

A tabela de transição tem exatamente a mesma forma de $M_2$, mas com $F = \{q_1\}$. Linguagem: $A = \{w \mid w \text{ termina em } 0 \text{ ou } w = \varepsilon\}$.

**3. $M_4$** — aceita cadeias que começam e terminam com o mesmo símbolo.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%205.png)

$Q = \{q_1, q_2, s, r_1, r_2\}$, $\Sigma = \{a, b\}$, $q_0 = s$, $F = \{q_1, r_1\}$:

| | a | b |
| --- | --- | --- |
| $q_1$ | $q_1$ | $q_2$ |
| $q_2$ | $q_1$ | $q_2$ |
| $s$ | $q_1$ | $r_1$ |
| $r_1$ | $r_2$ | $r_1$ |
| $r_2$ | $r_2$ | $r_1$ |

**4. $M_5$** — um "contador módulo 3" com um símbolo especial de reset.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%206.png)

$Q = \{q_0, q_1, q_2\}$, $\Sigma = \{0, 1, 2, \langle\text{RESET}\rangle\}$, $F = \{q_0\}$:

| | 0 | 1 | 2 | ⟨RESET⟩ |
| --- | --- | --- | --- | --- |
| $q_0$ | $q_0$ | $q_1$ | $q_2$ | $q_0$ |
| $q_1$ | $q_1$ | $q_2$ | $q_0$ | $q_0$ |
| $q_2$ | $q_2$ | $q_0$ | $q_1$ | $q_0$ |

As regras gerais por trás dessa tabela são: $\delta_i(q_j, 0) = q_j$; $\delta_i(q_j, 1) = q_k$ onde $k = j+1 \bmod i$; $\delta_i(q_j, 2) = q_k$ onde $k = j + 2 \bmod i$; e $\delta_i(q_j, \langle\text{RESET}\rangle) = q_0$. A linguagem reconhecida é $A = \{w \mid$ a soma dos símbolos de $w$ é $0 \bmod 3$, exceto que ⟨RESET⟩ zera o contador$\}$.

### Como projetar um autômato finito

Projetar um autômato segue um roteiro de três passos:

1. **Entender o alfabeto** — quais símbolos a cadeia de entrada pode conter.
2. **Deduzir os estados possíveis ($Q$)** — a partir do alfabeto, descobrir quais "situações" a máquina precisa distinguir; isso já revela quais estados são de aceitação e qual é o estado inicial (geralmente aquele em que a máquina se encontraria ao ler a cadeia vazia).
3. **Mapear as funções de transição** — para cada estado e cada símbolo, decidir para onde a máquina vai.

!!! example "Exemplo 1 — número ímpar de 1's"
    Seja $\Sigma = \{0, 1\}$ e considere a linguagem das cadeias $w$ aceitas se e somente se o número de 1's em $w$ for ímpar. Como o número de 0's não influencia a aceitação, os únicos estados necessários são $q_{par}$ e $q_{ímpar}$, com $q_{ímpar}$ sendo o estado de aceitação. Como a cadeia vazia tem zero 1's (um número par), o estado inicial é $q_{par}$. Nas transições, ler um 0 nunca muda de estado; ler um 1 sempre alterna entre os dois estados.

    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%207.png)

!!! example "Exemplo 2 — cadeias que contêm '001'"
    Com $\Sigma = \{0, 1\}$, queremos aceitar cadeias que contenham a subcadeia "001" em algum ponto. Aqui é preciso rastrear o progresso do casamento do padrão: ainda não viu nada do padrão ($q$), acabou de ver "0" ($q_0$), acabou de ver "00" ($q_{00}$), e acabou de ver "001" ($q_{001}$, estado de aceitação, que passa a ser absorvente). O estado inicial é $q$.

    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%208.png)

### Operações regulares

As **operações regulares** servem para estudar propriedades das linguagens regulares e para construir linguagens novas a partir de linguagens já conhecidas. Dadas linguagens $A$ e $B$:

| Operação | Definição |
| --- | --- |
| União | $A \cup B = \{x \mid x \in A \text{ ou } x \in B\}$ |
| Concatenação | $A \circ B = \{xy \mid x \in A \text{ e } y \in B\}$ |
| Estrela (fecho de Kleene) | $A^* = \{x_1 x_2 \ldots x_k \mid k \geq 0 \text{ e cada } x_i \in A\}$ |

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%209.png)

#### Fecho sob uma operação

Uma coleção de objetos é **fechada** sob uma operação se aplicar essa operação a membros da coleção sempre produz um objeto que ainda está na coleção.

!!! example
    O conjunto dos naturais é fechado sob a multiplicação, mas não sob a divisão: $1$ e $2$ são naturais, mas $1/2$ não é.

**Teorema.** A classe das linguagens regulares é fechada sob união: se $A_1$ e $A_2$ são regulares, $A_1 \cup A_2$ também é.

*Ideia da prova.* Se $A_1$ e $A_2$ são regulares, existem autômatos $M_1$ e $M_2$ que as reconhecem. Para reconhecer $A_1 \cup A_2$, construímos um autômato $M$ que aceita a entrada exatamente quando $M_1$ ou $M_2$ aceitaria. A dificuldade é que não é possível "simular $M_1$ e depois $M_2$": é preciso simular as duas *simultaneamente*, de modo que seus estados fiquem interligados passo a passo.

*Prova.* Sejam $M_1 = (Q_1, \Sigma, \delta_1, q_1, F_1)$ reconhecendo $A_1$ e $M_2 = (Q_2, \Sigma, \delta_2, q_2, F_2)$ reconhecendo $A_2$. Construímos $M = (Q, \Sigma, \delta, q, F)$ como segue:

- **Estados**: $Q = \{(r_1, r_2) \mid r_1 \in Q_1, r_2 \in Q_2\} = Q_1 \times Q_2$, o produto cartesiano — o conjunto de todos os pares de estados.
- **Alfabeto**: como $M_1$ e $M_2$ compartilham o alfabeto, $\Sigma$ permanece o mesmo (se fossem diferentes, $\Sigma = \Sigma_1 \cup \Sigma_2$).
- **Transição**: para cada par $(r_1, r_2) \in Q$ e cada $a \in \Sigma$, $\delta((r_1,r_2), a) = (\delta_1(r_1, a), \delta_2(r_2, a))$ — $M$ avança as duas "simulações" em paralelo.
- **Estado inicial**: $q = (q_1, q_2)$.
- **Estados de aceitação**: $F = \{(r_1, r_2) \mid r_1 \in F_1 \text{ ou } r_2 \in F_2\}$, equivalente a $F = (F_1 \times Q_2) \cup (Q_1 \times F_2)$ — ou seja, $M$ aceita se $M_1$ *ou* $M_2$ chegou a um estado de aceitação, não importando onde a outra parou.

!!! warning "Por que não $F = F_1 \times F_2$?"
    Se definíssemos os estados de aceitação de $M$ como $F_1 \times F_2$, $M$ só aceitaria quando *ambas* as máquinas aceitassem ao mesmo tempo — isso provaria o fecho sob **interseção**, não sob união.

Com essa construção, provamos o fecho sob união. A classe das linguagens regulares é também fechada sob **concatenação** — a ideia é semelhante, mas em vez de aceitar quando $M_1$ *ou* $M_2$ aceita, $M$ precisa aceitar quando a entrada puder ser quebrada em duas partes, a primeira aceita por $M_1$ e a segunda por $M_2$. O obstáculo é que $M$ não sabe *onde* fazer esse corte — e resolver esse problema exige introduzir o **não-determinismo**.

### Não-determinismo

Em uma computação **determinística**, estando em um estado e lendo o próximo símbolo, sempre sabemos exatamente qual é o próximo estado. Em uma máquina **não-determinística**, várias escolhas podem existir para o próximo estado em qualquer ponto da computação. O não-determinismo é uma generalização do determinismo: todo autômato finito determinístico (AFD) é automaticamente um autômato finito não-determinístico (AFN).

#### AFD vs. AFN

| Aspecto | AFD | AFN |
| --- | --- | --- |
| Transições por símbolo | Exatamente uma seta de saída para cada símbolo do alfabeto, em cada estado | Pode ter zero, uma ou várias setas para o mesmo símbolo |
| Rótulos das setas | Apenas símbolos do alfabeto | Símbolos do alfabeto **ou** $\varepsilon$ (transição sem consumir entrada) |
| Forma da computação | Uma única linha (uma "thread") | Uma árvore de possibilidades, com vários ramos computando em paralelo |

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2010.png)

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2011.png)

**Comparação visual** entre um AFN e o AFD equivalente para a mesma linguagem:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2012.png)

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2013.png)

#### Definição formal de AFN

Um AFN é uma 5-upla $(Q, \Sigma, \delta, q_0, F)$, onde a única diferença estrutural para o AFD está na função de transição:

$$\delta: Q \times \Sigma_\varepsilon \rightarrow \mathcal{P}(Q)$$

Aqui, $\Sigma_\varepsilon = \Sigma \cup \{\varepsilon\}$, e $\mathcal{P}(Q)$ é o **conjunto das partes** de $Q$ (o conjunto de todos os subconjuntos de $Q$) — ou seja, a transição pode levar a um *conjunto* de estados possíveis, não a um único estado.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2014.png)

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2015.png)

Formalmente, $N$ aceita $w$ se podemos escrever $w = y_1 y_2 \ldots y_n$ com cada $y_i \in \Sigma_\varepsilon$, e existe uma sequência de estados $r_0, \ldots, r_n \in Q$ tal que:

1. $r_0 = q_0$;
2. $r_{i+1} \in \delta(r_i, y_{i+1})$ para $i = 0, \ldots, n-1$ — ou seja, $r_{i+1}$ é um dos próximos estados *permitidos*;
3. $r_n \in F$.

Uma linguagem é regular se, e somente se, algum AFN a reconhece.

#### Equivalência entre AFN e AFD

Duas máquinas são **equivalentes** se reconhecem a mesma linguagem. O resultado central aqui é:

**Teorema.** Todo AFN tem um AFD equivalente.

*Ideia da prova.* Se o AFN tem $k$ estados, ele tem $2^k$ subconjuntos de estados possíveis. Cada subconjunto corresponde a uma das "configurações simultâneas" que o AFD precisa memorizar — portanto, o AFD equivalente terá $2^k$ estados (um para cada subconjunto).

*Prova.* Seja $N = (Q, \Sigma, \delta, q_0, F)$ um AFN que reconhece $A$. Construímos $M = (Q', \Sigma, \delta', q_0', F')$ que reconhece $A$.

**Caso sem setas $\varepsilon$:**

- $Q' = \mathcal{P}(Q)$ — todo estado de $M$ é um subconjunto de estados de $N$.
- $\delta'(R, a) = \{q \in Q \mid q \in \delta(r, a) \text{ para algum } r \in R\}$ — ao ler $a$ no estado $R$, $M$ olha para onde $a$ leva cada estado de $R$ e toma a união de todos esses destinos.
- $q_0' = \{q_0\}$.
- $F' = \{R \in Q' \mid R \text{ contém algum estado de aceitação de } N\}$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2016.png)

**Caso com setas $\varepsilon$:** além do que já foi descrito, define-se $E(R)$ como a coleção de estados atingíveis a partir de $R$ seguindo apenas setas $\varepsilon$ (incluindo os próprios membros de $R$):

$$E(R) = \{q \mid q \text{ é atingível a partir de } R \text{ por } 0 \text{ ou mais setas } \varepsilon\}, \quad R \subseteq Q$$

A função de transição de $M$ passa a aplicar o fecho-$\varepsilon$ após cada passo: $\delta'(R, a) = \{q \in Q \mid q \in E(\delta(r,a)) \text{ para algum } r \in R\}$. O estado inicial também precisa ser "fechado": $q_0' = E(\{q_0\})$.

#### Conversão passo a passo: de AFN para AFD

Tomando o AFN $N_4$ como exemplo:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2017.png)

**1 — Definir formalmente o AFN.** $Q = \{1, 2, 3\}$, $\Sigma = \{a, b\}$, $q_0 = 1$, $F = \{1\}$. Quando um estado não tem setas $\varepsilon$ explícitas, convencionamos que a transição $\varepsilon$ desse estado é ele mesmo:

| δ | a | b | ε |
| --- | --- | --- | --- |
| 1 | ∅ | {2} | {3} |
| 2 | {2, 3} | {3} | {2} |
| 3 | {1} | ∅ | {3} |

**2 — Definir formalmente o AFD.** $Q'$ contém todos os subconjuntos de $\{1,2,3\}$, um total de $2^3 = 8$ estados: $Q' = \{\emptyset, \{1\}, \{2\}, \{3\}, \{1,2\}, \{1,3\}, \{2,3\}, \{1,2,3\}\}$. Primeiro, montamos $\delta'$ *sem* aplicar o fecho-$\varepsilon$ (quando o resultado de uma transição envolve união de conjuntos, basta unir; quando dá $\emptyset$, ignora-se):

| δ' | a | b |
| --- | --- | --- |
| ∅ | ∅ | ∅ |
| {1} | ∅ | {2} |
| {2} | {2, 3} | {3} |
| {3} | {1} | ∅ |
| {1, 2} | {2, 3} | {2, 3} |
| {1, 3} | {1} | {2} |
| {2, 3} | {1, 2, 3} | {3} |
| {1, 2, 3} | {1, 2, 3} | {2, 3} |

Agora aplicamos o **ECLOSE()**: como $\delta(\{3\}, a) = \{1\}$ e $E(\{1\}) = \{1, 3\}$, toda ocorrência de $\{1\}$ nas transições passa a incluir o $\{3\}$ também (já que $E(\{2\}) = \{2\}$ e $E(\{3\}) = \{3\}$, essas linhas não mudam):

| δ' | a | b |
| --- | --- | --- |
| ∅ | ∅ | ∅ |
| {1} | ∅ | {2} |
| {2} | {2, 3} | {3} |
| {3} | {1, 3} | ∅ |
| {1, 2} | {2, 3} | {2, 3} |
| {1, 3} | {1, 3} | {2} |
| {2, 3} | {1, 2, 3} | {3} |
| {1, 2, 3} | {1, 2, 3} | {2, 3} |

O novo estado inicial é $q_0' = E(\{1\}) = \{1, 3\}$, e os estados finais são todos os que contêm o estado final original: $F' = \{\{1\}, \{1,2\}, \{1,3\}, \{1,2,3\}\}$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2018.png)

**3 — Eliminar estados desnecessários.** Primeiro, removem-se os estados **inalcançáveis** — aqueles que nunca aparecem como destino de nenhuma transição (nas colunas $a$ e $b$ de nenhum outro estado). Nesse exemplo, $\{1\}$ e $\{1,2\}$ nunca são alcançados e podem ser eliminados:

| δ' | a | b |
| --- | --- | --- |
| ∅ | ∅ | ∅ |
| {1} | ∅ | {2} |
| {2} | {2, 3} | {3} |
| {3} | {1, 3} | ∅ |
| {1, 2} | {2, 3} | {2, 3} |
| {1, 3} | {1, 3} | {2} |
| {2, 3} | {1, 2, 3} | {3} |
| {1, 2, 3} | {1, 2, 3} | {2, 3} |

Depois, removem-se estados que **não têm saídas úteis e não são finais** — por exemplo, um estado não final cujas únicas transições apontam para ele mesmo, formando um loop isolado:

| δ' | a | b |
| --- | --- | --- |
| ... | ... | ... |
| q2 | q2 | q2 |
| ... | ... | ... |

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2019.png)

### Fecho sob as operações regulares (via não-determinismo)

Com o AFN em mãos, podemos provar de forma muito mais direta que a classe das linguagens regulares é fechada sob união, concatenação e estrela.

**União.** Dadas as linguagens regulares $A_1$ e $A_2$, tomamos os AFNs $N_1$ e $N_2$ que as reconhecem e os combinamos em um novo AFN $N$: um novo estado inicial ramifica, via setas $\varepsilon$, para os estados iniciais de $N_1$ e $N_2$ — a nova máquina "adivinha" não-deterministicamente qual das duas aceitaria a entrada.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2020.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2021.png)

- $Q = \{q_0\} \cup Q_1 \cup Q_2$ — todos os estados de $N_1$ e $N_2$, mais um novo estado inicial.
- $F = F_1 \cup F_2$ — $N$ aceita se $N_1$ ou $N_2$ aceitaria.
- $\delta$ definida de modo que, para qualquer $q \in Q$ e $a \in \Sigma_\varepsilon$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2022.png)

**Concatenação.** Tomamos $N_1$ e $N_2$ e os combinamos: o estado inicial de $N$ é o de $N_1$; os estados de aceitação de $N_1$ ganham setas $\varepsilon$ extras que ramificam não-deterministicamente para $N_2$ sempre que $N_1$ estiver em um estado de aceitação (sinalizando que encontrou um prefixo da entrada em $A_1$); os estados de aceitação de $N$ são apenas os de $N_2$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2023.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2024.png)

- $Q = Q_1 \cup Q_2$.
- O estado inicial é o mesmo de $N_1$.
- $F = F_2$.
- $\delta$ definida de modo que, para qualquer $q \in Q$ e $a \in \Sigma_\varepsilon$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2025.png)

**Estrela.** Tomamos $N_1$ para $A_1$ e o modificamos para reconhecer $A_1^*$: a máquina resultante aceita quando a entrada puder ser quebrada em várias partes e $N_1$ aceitar cada uma. Isso é obtido adicionando setas $\varepsilon$ dos estados de aceitação de volta ao estado inicial, para que a máquina possa "recomeçar" após aceitar uma parte.

Como $A_1^*$ sempre contém $\varepsilon$, é preciso também garantir que a máquina aceite a cadeia vazia — mas simplesmente tornar o estado inicial antigo também de aceitação adicionaria cadeias indesejadas. A solução correta é criar um **novo** estado inicial, que é também de aceitação, com uma seta $\varepsilon$ para o antigo estado inicial.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2026.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2027.png)

- $Q = \{q_0\} \cup Q_1$.
- $q_0$ é o novo estado inicial.
- $F = \{q_0\} \cup F_1$.
- $\delta$ definida de modo que, para qualquer $q \in Q$ e $a \in \Sigma_\varepsilon$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2028.png)

### Expressões regulares

As operações regulares também servem para montar **expressões** que descrevem linguagens de forma compacta — as expressões regulares.

!!! example
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2029.png)

    A expressão $(0 \cup 1)0^*$ descreve as cadeias que começam por $0$ ou $1$, seguidas de qualquer número de $0$'s. Aqui, $0 \cup 1$ é notação curta para $\{0\} \cup \{1\}$, $0^*$ para $\{0\}^*$, e $(0 \cup 1)0^*$ para $(0 \cup 1) \circ 0^*$.

Dado $\Sigma = \{0, 1\}$, $\Sigma^*$ denota a linguagem de todas as cadeias sobre $\Sigma$; $\Sigma^*1$ denota todas as cadeias que terminam em $1$; e $(0\Sigma^*) \cup (\Sigma^*1)$ descreve todas as cadeias que começam com $0$ ou terminam com $1$.

**Precedência de operadores**: estrela > concatenação > união, salvo uso de parênteses. Além disso, $R^+ \equiv RR^*$ ($R^*$ representa zero ou mais concatenações de $R$, enquanto $R^+$ exige pelo menos uma — e $R^* = R^+ \cup \varepsilon$), e $R^k$ equivale à concatenação de $k$ cópias de $R$.

**Definição formal.** ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2030.png)

Algumas identidades úteis, que não são tão óbvias quanto parecem: $R \cup \emptyset = R$ e $R \circ \varepsilon = R$, mas $R \cup \varepsilon$ **pode não ser** igual a $R$ (se $R = 0$, $L(R) = \{0\}$ mas $L(R \cup \varepsilon) = \{0, \varepsilon\}$), e $R \circ \emptyset$ **pode não ser** igual a $R$ (se $R = 0$, $L(R \circ \emptyset) = \emptyset \neq \{0\}$).

#### Equivalência entre expressões regulares e autômatos finitos

**Teorema.** Uma linguagem é regular se, e somente se, alguma expressão regular a descreve.

A prova se divide em duas direções.

**(⇐) Se uma linguagem é descrita por uma expressão regular, então ela é regular.**

*Ideia.* Mostramos como converter qualquer expressão regular $R$ em um AFN que reconhece a mesma linguagem — e, como um AFN sempre reconhece uma linguagem regular, isso basta.

*Prova.* A conversão de $R$ para um AFN $N$ é feita por indução na estrutura de $R$, com seis casos:

1. $R = a$ para $a \in \Sigma$, $R = \varepsilon$ ou $R = \emptyset$ (casos base): ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2031.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2032.png)
2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2033.png)
3. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2034.png)
4. $R = R_1 \cup R_2$ → usa-se a construção do fecho sob união.
5. $R = R_1 \circ R_2$ → usa-se a construção do fecho sob concatenação.
6. $R = R_1^*$ → usa-se a construção do fecho sob estrela.

!!! example "Convertendo $(ab \cup a)^*$ em AFN"
    O procedimento começa das subexpressões menores e vai compondo as maiores. Vale notar que o AFN resultante **nem sempre é o menor possível** — a construção é sistemática, não otimizada.

    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2035.png)

**(⇒) Se uma linguagem é regular, então ela é descrita por alguma expressão regular.**

*Ideia.* Como a linguagem é regular, ela é aceita por algum AFD; precisamos de um procedimento para converter AFDs em expressões regulares equivalentes. Para isso, introduzimos um novo tipo de autômato: o **autômato finito não-determinístico generalizado (AFNG)**.

Um AFNG é como um AFN, mas suas setas de transição podem ser rotuladas por **expressões regulares inteiras** (não apenas símbolos do alfabeto e $\varepsilon$), e ele lê blocos de símbolos de entrada de uma vez, não necessariamente um por um. Por conveniência, exige-se que todo AFNG tenha um formato especial:

- o estado inicial tem setas saindo para todos os outros estados, mas nenhuma seta chegando a ele;
- existe um único estado de aceitação, com setas chegando de todos os outros estados, mas nenhuma saindo dele (e ele é diferente do estado inicial);
- com exceção desses dois, toda seta entre quaisquer dois estados (inclusive de um estado para ele mesmo) existe e é rotulada por uma expressão da linguagem.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2036.png)

**Definição formal de AFNG.** ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2037.png)

Aqui $\mathcal{R}$ é a coleção de todas as expressões regulares sobre $\Sigma$. Um AFNG aceita $w \in \Sigma^*$ se $w = w_1 w_2 \ldots w_k$ com cada $w_i \in \Sigma^*$ e existe uma sequência de estados $q_0, q_1, \ldots, q_k$ tal que $q_0 = q_{início}$, $q_k = q_{aceita}$ e, para cada $i$, $w_i \in L(R_i)$ onde $R_i = \delta(q_{i-1}, q_i)$ é a expressão sobre a seta de $q_{i-1}$ a $q_i$.

*Prova do teorema.* Seja $M$ o AFD para $A$. Convertemos $M$ em um AFNG $G$ adicionando um novo estado inicial e um novo estado de aceitação, com as setas necessárias. Em seguida, usa-se o procedimento recursivo `CONVERT(G)`, que toma um AFNG e retorna uma expressão regular equivalente:

1. Seja $k$ o número de estados de $G$.
2. Se $k = 2$, $G$ consiste de um estado inicial, um de aceitação e uma única seta rotulada por uma expressão $R$ — retorna-se $R$.
3. Se $k > 2$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2038.png) escolhe-se um estado $q_{rem}$ diferente do inicial e do de aceitação para remover, redirecionando as setas que passavam por ele através de novas expressões regulares que capturam todos os caminhos que antes passavam por $q_{rem}$. Chama-se `CONVERT` recursivamente sobre o AFNG resultante $G'$ (com $k-1$ estados).

**Correção do algoritmo**: prova-se por indução que `CONVERT(G)` é sempre equivalente a $G$.

- *Base* ($k=2$): com apenas uma seta do início ao fim, a expressão que a rotula descreve exatamente as cadeias que levam $G$ ao estado de aceitação.
- *Passo indutivo*: supondo o resultado válido para $k-1$ estados, mostra-se que $G$ e $G'$ (após remover $q_{rem}$) reconhecem a mesma linguagem.
    - Se $G$ aceita $w$ por um ramo que não passa por $q_{rem}$, então $G'$ também aceita $w$, pois cada nova expressão em $G'$ contém a antiga como parte de uma união.
    - Se o ramo passa por $q_{rem}$, a nova expressão entre os estados vizinhos a $q_{rem}$ foi construída exatamente para descrever as cadeias que levavam de um a outro *via* $q_{rem}$ — logo $G'$ também aceita $w$.
    - Reciprocamente, se $G'$ aceita $w$, cada seta de $G'$ descreve as cadeias que levam de um estado a outro em $G$ (direta ou indiretamente via $q_{rem}$), logo $G$ também aceita $w$.

Como a hipótese de indução garante que a chamada recursiva sobre $G'$ (com $k-1$ estados) retorna uma expressão equivalente a $G'$, e $G'$ é equivalente a $G$, o algoritmo e o teorema ficam provados.

!!! example "Exemplos de conversão AFD → expressão regular"
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2039.png)

    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2040.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2041.png)

### Linguagens não-regulares

Nem toda linguagem pode ser reconhecida por um autômato finito — essas são chamadas de **linguagens não-regulares**.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2042.png)

#### Lema do bombeamento

O lema do bombeamento afirma que toda linguagem regular tem uma propriedade especial; se conseguirmos mostrar que uma linguagem **não** tem essa propriedade, temos a garantia de que ela não é regular. A propriedade é que toda cadeia da linguagem com comprimento suficiente pode ser "bombeada": ela contém uma parte que pode ser repetida qualquer número de vezes, permanecendo sempre na linguagem.

**Definição formal.** Se $A$ é regular, existe um número $p$ (o **comprimento de bombeamento**) tal que toda cadeia $s \in A$ com $|s| \geq p$ pode ser dividida em três partes, $s = xyz$, satisfazendo:

1. para cada $i \geq 0$, $xy^iz \in A$ (onde $y^0 = \varepsilon$);
2. $|y| > 0$ (ou seja, $x$ e $z$ podem ser $\varepsilon$, mas $y \neq \varepsilon$);
3. $|xy| \leq p$ (as partes $x$ e $y$ juntas têm comprimento no máximo $p$ — condição técnica, mas útil nas provas).

*Ideia da prova.* Seja $M = (Q, \Sigma, \delta, q_1, F)$ o AFD que reconhece $A$; fazemos $p$ ser o número de estados de $M$.

*Prova.* Se $|s| < p$, o teorema vale por vacuidade. Suponha $|s| = n \geq p$, $s = s_1 s_2 \ldots s_n$, e seja $r_1, \ldots, r_{n+1}$ a sequência de estados por onde $M$ passa ao processar $s$ (com $r_{i+1} = \delta(r_i, s_i)$).

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2043.png)

Essa sequência tem $n+1 \geq p+1$ elementos. Pelo **princípio da casa dos pombos**, entre os primeiros $p+1$ elementos, dois precisam repetir o mesmo estado — sejam $r_j$ e $r_l$ ($j < l \leq p+1$) essa repetição. Definimos $x = s_1 \ldots s_{j-1}$, $y = s_j \ldots s_{l-1}$ e $z = s_l \ldots s_n$.

Como $x$ leva $M$ de $r_1$ a $r_j$, $y$ leva de $r_j$ de volta a $r_j$ (um "laço"), e $z$ leva de $r_j$ a $r_{n+1} \in F$, $M$ aceita $xy^iz$ para qualquer $i \geq 0$ — satisfazendo a condição 1. Como $j \neq l$, $|y| > 0$ (condição 2); e como $l \leq p+1$, $|xy| \leq p$ (condição 3).

**Usando o lema para provar que uma linguagem não é regular:**

1. Suponha, por contradição, que a linguagem é regular.
2. Pelo lema, existe um comprimento de bombeamento $p$ tal que toda cadeia de comprimento $\geq p$ pode ser bombeada.
3. Exiba uma cadeia específica da linguagem, de comprimento $\geq p$, que **não pode** ser bombeada.
4. Mostre isso considerando *todas* as formas possíveis de dividir essa cadeia em $xyz$ e, para cada uma, encontrando um $i$ tal que $xy^iz$ não pertence à linguagem — isso frequentemente exige separar em vários casos.
5. A contradição mostra que a suposição inicial (regularidade) era falsa.

!!! example "Exemplos de aplicação do lema do bombeamento"
    1. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2044.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2045.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2046.png)
    2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2047.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2048.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2049.png)
    3. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2050.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2051.png)
    4. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2052.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2053.png)
    5. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2054.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2055.png)

---

## Linguagens Livres do Contexto

### Gramáticas livres do contexto

As **gramáticas livres do contexto (GLC)** são um método mais poderoso para descrever linguagens do que os autômatos finitos, capaz de capturar estruturas recursivas — o que as torna úteis em uma enorme variedade de aplicações (por exemplo, a sintaxe de linguagens de programação).

Uma GLC consiste em uma coleção de **regras de substituição** (também chamadas **produções**). Cada regra é uma linha da gramática, formada por um **símbolo** e uma **cadeia**, separados por uma seta; a sequência de substituições que leva de um símbolo a uma cadeia final é chamada de **derivação**. O símbolo do lado esquerdo é chamado de **variável**; a cadeia do lado direito é composta por variáveis e por **terminais**. Convencionalmente, variáveis são letras maiúsculas, e terminais são análogos ao alfabeto de entrada (letras minúsculas, números ou símbolos especiais). Uma variável é designada como **variável inicial**, normalmente a do lado esquerdo da primeira regra.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2056.png)

Nesse exemplo, a gramática tem três regras, duas variáveis ($A$ e $B$, com $A$ sendo a inicial) e três terminais ($0$, $1$ e $\#$). Por convenção, abreviamos várias regras com a mesma variável à esquerda usando `|`: por exemplo, $A \to 0A1 \mid B$.

O conjunto de todas as cadeias geradas por essas derivações constitui a **linguagem da gramática**. Qualquer linguagem gerada por alguma GLC é chamada de **linguagem livre do contexto (LLC)**.

**Definição formal.** Uma GLC é uma 4-upla $(V, \Sigma, R, S)$, onde:

- $V$ é um conjunto finito de **variáveis**;
- $\Sigma$ é um conjunto finito, disjunto de $V$, de **terminais**;
- $R$ é um conjunto finito de **regras**, cada uma composta por uma variável e uma cadeia de variáveis e terminais;
- $S \in V$ é a **variável inicial**.

Se $u, v, w$ são cadeias de variáveis e terminais e $A \to w$ é uma regra, dizemos que $uAv$ *origina* $uwv$, escrito $uAv \Rightarrow uwv$. Dizemos que $u$ *deriva* $v$, escrito $u \Rightarrow^* v$, se $u = v$ ou se existe uma sequência $u \Rightarrow u_1 \Rightarrow \ldots \Rightarrow u_k \Rightarrow v$. A linguagem da gramática é $\{w \in \Sigma^* \mid S \Rightarrow^* w\}$.

### Projetando GLCs

GLCs são, em geral, mais difíceis de construir que autômatos finitos. Três técnicas ajudam:

**1. Dividir a gramática.** Muitas LLCs são a união de LLCs mais simples. Se a linguagem puder ser quebrada em partes, é mais fácil construir uma gramática para cada parte separadamente e depois combiná-las: juntam-se todas as regras e adiciona-se $S \to S_1 \mid \ldots \mid S_k$, onde cada $S_i$ é a variável inicial de uma das gramáticas individuais.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2057.png)

**2. Converter um AFD em GLC.** Se a linguagem já é conhecida como regular, é fácil construir uma GLC equivalente a partir de um AFD: cria-se uma variável $R_i$ para cada estado $q_i$ do AFD; adiciona-se a regra $R_i \to aR_j$ sempre que $\delta(q_i, a) = q_j$; adiciona-se $R_i \to \varepsilon$ sempre que $q_i$ for estado de aceitação; e $R_0$ (correspondente ao estado inicial) se torna a variável inicial da gramática.

**3. Lidar com subcadeias correlacionadas.** Certas LLCs têm cadeias com duas subcadeias "ligadas" — uma máquina precisaria memorizar quantidade ilimitada de informação sobre uma para verificar a correspondência com a outra.

!!! example
    A linguagem $\{0^n1^n \mid n \geq 0\}$: uma máquina de estados finitos não consegue memorizar "quantos 0's" viu, porque isso exigiria memória ilimitada. Já a gramática com a regra $R \to 0R1 \mid \varepsilon$ resolve isso naturalmente, pois cada passo da derivação garante que a parte dos $0$'s e a parte dos $1$'s crescem em sincronia.

Em linguagens mais complexas, certas estruturas podem aparecer recursivamente como parte de outras estruturas — ou de si mesmas (como expressões aritméticas com parênteses aninhados). Para capturar isso, basta colocar o símbolo da variável que gera a estrutura exatamente na posição onde ela pode recorrer.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2058.png)

### Ambiguidade

Às vezes, uma gramática pode gerar a mesma cadeia por caminhos diferentes. Quando isso ocorre, a cadeia tem **árvores sintáticas** diferentes — e, portanto, significados potencialmente diferentes, o que é indesejável em muitas aplicações (como compiladores). Dizemos que uma cadeia é **derivada ambiguamente** por uma gramática se ela admite mais de uma árvore sintática, e que a gramática é **ambígua** se gera ambiguamente alguma cadeia.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2059.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2060.png)

!!! note "Derivações diferentes vs. árvores diferentes"
    Duas derivações podem diferir apenas na *ordem* em que substituem variáveis, sem diferir na estrutura. Para evitar essa confusão, definimos a **derivação mais à esquerda**: a cada passo, substitui-se a variável mais à esquerda que ainda resta. Com essa convenção, uma cadeia é ambígua sse tem duas ou mais derivações mais-à-esquerda diferentes.

Algumas gramáticas ambíguas têm uma gramática não ambígua equivalente (que gera a mesma linguagem); mas existem linguagens que só podem ser geradas por gramáticas ambíguas — chamadas **linguagens inerentemente ambíguas**.

### Forma normal de Chomsky

É uma forma simplificada e padronizada para GLCs, muito útil ao trabalhar algoritmicamente com elas.

**Definição formal.** Uma GLC está na **forma normal de Chomsky** se toda regra é da forma $A \to BC$ ou $A \to a$, onde $a$ é qualquer terminal e $A, B, C$ são variáveis quaisquer (com a restrição de que $B$ e $C$ não podem ser a variável inicial). Permite-se adicionalmente a regra $S \to \varepsilon$, onde $S$ é a inicial.

**Teorema.** Toda LLC é gerada por alguma GLC na forma normal de Chomsky.

*Ideia da prova.* A conversão de uma gramática qualquer $G$ para a forma normal de Chomsky passa por estágios: (1) adicionar uma nova variável inicial; (2) eliminar regras $\varepsilon$; (3) eliminar regras unitárias; (4) converter as regras remanescentes para o formato exigido.

*Prova.*

1. **Nova variável inicial.** Adiciona-se $S_0$ e a regra $S_0 \to S$ (sendo $S$ a inicial original), garantindo que a inicial nunca apareça do lado direito de uma regra.
2. **Eliminação das regras $\varepsilon$.** Remove-se uma regra $A \to \varepsilon$ (com $A$ não inicial); para cada ocorrência de $A$ do lado direito de outra regra, adiciona-se uma nova regra com essa ocorrência apagada. Por exemplo, $R \to uAvAw$ gera $R \to uvAw$, $R \to uAvw$ e $R \to uvw$. Se existir uma regra $R \to A$, adiciona-se $R \to \varepsilon$ (a menos que essa regra já tenha sido removida antes). Repete-se até eliminar todas as regras $\varepsilon$ que não envolvem a inicial.
3. **Eliminação das regras unitárias.** Remove-se uma regra unitária $A \to B$; sempre que existir $B \to u$, adiciona-se $A \to u$ (a menos que $A \to u$ já tenha sido removida como unitária). Repete-se até eliminar todas.
4. **Conversão das regras remanescentes.** Substitui-se cada regra $A \to u_1 u_2 \ldots u_k$ (com $k \geq 3$) por $A \to u_1 A_1$, $A_1 \to u_2 A_2$, …, $A_{k-2} \to u_{k-1}u_k$, introduzindo novas variáveis $A_i$; se algum $u_i$ for terminal, substitui-se por uma nova variável $U_i$ com a regra adicional $U_i \to u_i$.

!!! example "Exemplo completo de conversão"
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2061.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2062.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2063.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2064.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2065.png)

### Autômato com pilha

Os **autômatos com pilha (AP)** são semelhantes aos AFNs, mas com um componente extra: uma **pilha**. A pilha oferece memória adicional, além da quantidade finita disponível no controle de estados, permitindo que o AP reconheça algumas linguagens não regulares. Autômatos com pilha são **equivalentes em poder** às GLCs.

| | Autômato finito | Autômato com pilha |
| --- | --- | --- |
| Diagrama esquemático | ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2066.png) | ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2067.png) |

Escrever um símbolo na pilha é chamado **empilhar**; removê-lo é **desempilhar**. Todo acesso à pilha ocorre apenas pelo topo (disciplina LIFO).

A memória ilimitada da pilha é o que torna os APs mais poderosos: um autômato finito é incapaz de reconhecer $\{0^n1^n \mid n \geq 0\}$ porque não pode armazenar números arbitrariamente grandes com memória finita. Um AP consegue, porque pode empilhar um símbolo para cada $0$ lido e desempilhar um para cada $1$ lido — se a pilha esvaziar exatamente quando a entrada terminar, ela é aceita.

APs podem ser **determinísticos** ou **não-determinísticos**, e — diferentemente dos autômatos finitos — essas duas variantes **não são equivalentes em poder**.

**Definição formal.** Um AP é uma 6-upla $(Q, \Sigma, \Gamma, \delta, q_0, F)$, onde $\Gamma$ é o **alfabeto de pilha** e

$$\delta: Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon \rightarrow \mathcal{P}(Q \times \Gamma_\varepsilon)$$

O estado atual, o próximo símbolo da entrada e o símbolo no topo da pilha determinam o próximo movimento; o retorno especifica o próximo estado e o símbolo a empilhar (podendo ser $\varepsilon$ em qualquer uma dessas três posições, e o não-determinismo é incorporado da maneira usual).

Um AP aceita $w = w_1 \ldots w_m$ (cada $w_i \in \Sigma_\varepsilon$) se existem estados $r_0, \ldots, r_m \in Q$ e cadeias de pilha $s_0, \ldots, s_m \in \Gamma^*$ tais que:

1. $r_0 = q_0$ e $s_0 = \varepsilon$ (início no estado e pilha corretos);
2. para $i = 0, \ldots, m-1$, $(r_{i+1}, b) \in \delta(r_i, w_{i+1}, a)$ onde $s_i = at$ e $s_{i+1} = bt$ para algum $a, b \in \Gamma_\varepsilon$ e $t \in \Gamma^*$ (movimento consistente com a pilha);
3. $r_m \in F$.

!!! note
    $\Gamma^*$ (fecho de Kleene sobre o alfabeto de pilha) é o conjunto de todas as cadeias finitas formadas com símbolos de $\Gamma$, incluindo $\varepsilon$.

Nos diagramas de estado de um AP, uma transição anotada "$a, b \to c$" significa: lendo $a$ da entrada, pode-se substituir $b$ (topo da pilha) por $c$. Qualquer um dos três símbolos pode ser $\varepsilon$: se $a = \varepsilon$, a transição não consome entrada; se $b = \varepsilon$, não desempilha; se $c = \varepsilon$, não empilha.

!!! example "Exemplos de AP"
    1. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2068.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2069.png)
    2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2070.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2071.png)

### Equivalência entre APs e GLCs

**Teorema.** Uma linguagem é LLC se, e somente se, algum autômato com pilha a reconhece.

**(⇒) Se $A$ é LLC, algum AP a reconhece.**

*Ideia.* Seja $G$ a GLC que gera $A$. Projetamos um AP $P$ que *simula* $G$: $P$ aceita $w$ exatamente quando existe uma derivação de $G$ para $w$. A dificuldade é descobrir *quais* derivações tentar — mas o não-determinismo do AP resolve isso, permitindo "adivinhar" a sequência correta de substituições. Além disso, $P$ não pode simplesmente guardar a cadeia intermediária inteira na pilha (precisaria localizar variáveis no meio dela, mas só acessa o topo); a solução é manter na pilha apenas a cadeia a partir da *primeira variável* restante, casando imediatamente qualquer terminal que vier antes dela com a entrada.

*Descrição informal de $P$*: empilha-se o marcador $\$$ e a variável inicial; depois, repete-se: se o topo é uma variável $A$, escolhe-se não-deterministicamente uma regra $A \to w$ e substitui-se $A$ por $w$; se o topo é um terminal $a$, lê-se o próximo símbolo da entrada e compara-se com $a$ (rejeitando o ramo se não casar); se o topo é $\$$, entra-se no estado de aceitação (aceitando se toda a entrada já foi lida).

*Prova formal (esboço técnico).* Para implementar "empilhar uma cadeia inteira $u$ de uma vez" usando apenas a primitiva "empilhar um símbolo por transição", introduzem-se estados intermediários encadeados:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2072.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2073.png)

Os estados de $P$ são $Q = \{q_{início}, q_{laço}, q_{aceita}\} \cup E$ (onde $E$ dá suporte à abreviação de empilhar cadeias). As transições principais: $\delta(q_{início}, \varepsilon, \varepsilon) = \{(q_{laço}, S\$)\}$ inicializa a pilha; $\delta(q_{laço}, \varepsilon, A) = \{(q_{laço}, w) \mid A \to w \in R\}$ expande variáveis; $\delta(q_{laço}, a, a) = \{(q_{laço}, \varepsilon)\}$ casa terminais; $\delta(q_{laço}, \varepsilon, \$) = \{(q_{aceita}, \varepsilon)\}$ aceita ao esvaziar a pilha.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2074.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2075.png)

**(⇐) Se algum AP reconhece uma linguagem, ela é LLC.**

*Ideia.* Dado um AP $P$, construímos uma GLC $G$ que gera exatamente as cadeias que $P$ aceita. Para cada par de estados $p, q$ de $P$, a gramática terá uma variável $A_{pq}$ que gera todas as cadeias capazes de levar $P$ de $p$ (com pilha vazia) a $q$ (com pilha vazia novamente). Antes, modifica-se $P$ para ter um único estado de aceitação, esvaziar a pilha antes de aceitar, e fazer com que cada transição empilhe **ou** desempilhe um símbolo, nunca os dois (uma transição que fizesse ambos é quebrada em duas via um novo estado; uma que não fizesse nenhum dos dois ganha um par empilha/desempilha de um símbolo arbitrário).

*Prova.* Seja $P = (Q, \Sigma, \Gamma, \delta, q_0, \{q_{aceita}\})$. As variáveis de $G$ são $\{A_{pq} \mid p, q \in Q\}$, e a inicial é $A_{q_0, q_{aceita}}$. As regras de $G$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2076.png)

Prova-se que $A_{pq}$ gera $x$ se e somente se $x$ leva $P$ de $p$ (pilha vazia) a $q$ (pilha vazia), por indução dupla (no número de passos da derivação, e no número de passos da computação):

- **($A_{pq} \Rightarrow^* x \implies$ computação de $P$)**, por indução no comprimento da derivação:
    - *Base* (1 passo): só pode usar uma regra sem variáveis à direita, isto é, $A_{pp} \to \varepsilon$ — e, de fato, $\varepsilon$ leva $P$ de $p$ a $p$ trivialmente.
    - *Passo indutivo*: o primeiro passo de uma derivação de $k+1$ passos é $A_{pq} \Rightarrow aA_{rs}b$ ou $A_{pq} \Rightarrow A_{pr}A_{rq}$, tratados separadamente: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2077.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2078.png)
- **(computação de $P$ $\implies A_{pq} \Rightarrow^* x$)**, por indução no comprimento da computação:
    - *Base* (0 passos): a computação começa e termina no mesmo estado $p$ com $x = \varepsilon$, e $G$ tem exatamente a regra $A_{pp} \to \varepsilon$.
    - *Passo indutivo*: distinguindo se a pilha fica vazia só no início/fim, ou também em algum ponto intermediário: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2079.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2080.png)

Esse teorema também estabelece uma relação direta entre linguagens regulares e LLCs: como todo autômato finito é, trivialmente, um AP que ignora sua pilha, **toda linguagem regular é também uma LLC**.

### Linguagens não livres do contexto

Assim como existe um lema do bombeamento para linguagens regulares, existe uma versão análoga (porém mais complexa) para LLCs, que permite provar que certas linguagens não são livres do contexto. A diferença é que, agora, a cadeia é dividida em **cinco** partes, das quais a segunda e a quarta podem ser "bombeadas" juntas.

**Lema do bombeamento para LLCs.** Se $A$ é LLC, existe um número $p$ tal que toda $s \in A$ com $|s| \geq p$ pode ser escrita como $s = uvxyz$ satisfazendo:

1. para cada $i \geq 0$, $uv^ixy^iz \in A$;
2. $|vy| > 0$ (ou seja, $v$ ou $y$ não é $\varepsilon$ — senão o teorema seria trivial);
3. $|vxy| \leq p$ (condição técnica útil nas provas).

*Ideia da prova.* Seja $G$ uma GLC para $A$. Toda cadeia suficientemente longa $s \in A$ tem uma árvore sintática cujo caminho mais longo, da raiz a uma folha, precisa conter, pelo princípio da casa dos pombos, alguma variável $R$ repetida. Essa repetição permite substituir a subárvore sob a ocorrência inferior de $R$ pela subárvore sob a ocorrência superior (e vice-versa), ainda produzindo uma árvore sintática válida — isso dá a divisão $s = uvxyz$ com $uv^ixy^iz \in A$ para todo $i \geq 0$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2081.png)

*Prova.* Seja $b$ o número máximo de símbolos do lado direito de qualquer regra de $G$. Nenhum nó de uma árvore sintática tem mais que $b$ filhos; logo, no máximo $b^h$ folhas estão a $h$ passos da raiz — se a árvore tem altura $h$, a cadeia gerada tem comprimento no máximo $b^h$ (e, reciprocamente, uma cadeia de comprimento $\geq b^h + 1$ exige árvore de altura $\geq h+1$).

Seja $|V|$ o número de variáveis de $G$ e $p = b^{|V|+1}$. Se $|s| \geq p$, sua árvore sintática (escolhida, entre possíveis empates, com o menor número de nós) tem altura $\geq |V|+1$, logo contém um caminho raiz-folha com pelo menos $|V|+2$ nós — e, como só há $|V|$ variáveis possíveis, alguma variável $R$ se repete entre as $|V|+1$ variáveis mais próximas da folha nesse caminho.

Dividindo $s = uvxyz$ conforme as duas ocorrências de $R$: a ocorrência superior gera $vxy$, a inferior gera apenas $x$. Substituir a subárvore menor pela maior (repetidamente) produz $uv^ixy^iz$ para qualquer $i \geq 1$; substituir a maior pela menor produz $uxz$ — estabelecendo a condição 1.

Para a condição 2 ($v, y \neq \varepsilon$ simultaneamente impossível): se ambos fossem $\varepsilon$, a árvore obtida substituindo a subárvore maior pela menor teria *menos* nós que a árvore escolhida para $s$ e ainda geraria $s$ — contradizendo a escolha da árvore com o menor número de nós.

Para a condição 3: como as duas ocorrências de $R$ foram escolhidas entre as $|V|+1$ variáveis mais próximas da folha no caminho mais longo, a subárvore onde $R$ gera $vxy$ tem altura no máximo $|V|+1$, logo gera uma cadeia de comprimento no máximo $b^{|V|+1} = p$.

!!! example "Exemplos"
    1. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2082.png)
    2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2083.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2084.png)
    3. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2085.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2086.png)

---

## A Tese de Church-Turing

### Máquinas de Turing

As **máquinas de Turing** são semelhantes aos autômatos finitos, mas com uma memória **ilimitada e irrestrita** — um modelo muito mais fiel a um computador de propósito geral. A máquina usa uma **fita infinita** como memória, com uma cabeça de leitura/escrita que pode se mover para os dois lados. Inicialmente, a fita contém apenas a cadeia de entrada, e está em branco em todo o resto; a máquina pode escrever informação na fita para "lembrar" dela depois, movendo a cabeça de volta quando precisar lê-la. As saídas *aceitar* e *rejeitar* ocorrem ao entrar em estados designados para isso; se a máquina nunca entra em nenhum dos dois, ela simplesmente continua para sempre, sem parar.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2087.png)

| Diferença | Máquina de Turing | Autômato finito |
| --- | --- | --- |
| Acesso à fita | Lê **e** escreve | Só lê |
| Movimento da cabeça | Esquerda ou direita | Só avança |
| Tamanho da fita | Infinita | — (sem fita, só estado) |
| Parada | Aceitar/rejeitar têm efeito imediato | Decisão só ao final da entrada |

#### Definição formal

Uma máquina de Turing é uma **7-upla** $(Q, \Sigma, \Gamma, \delta, q_0, q_{aceita}, q_{rejeita})$, com $Q, \Sigma, \Gamma$ finitos:

- $Q$: estados;
- $\Sigma$: alfabeto de entrada, sem o símbolo em branco $\sqcup$;
- $\Gamma$: alfabeto de fita, com $\sqcup \in \Gamma$ e $\Sigma \subseteq \Gamma$;
- $\delta: Q \times \Gamma \rightarrow Q \times \Gamma \times \{E, D\}$ — a função de transição: se a máquina está em $q$ com a cabeça sobre um símbolo $a$, e $\delta(q, a) = (r, b, E)$, ela escreve $b$ no lugar de $a$, vai para o estado $r$, e move a cabeça para a esquerda ($E$) ou direita ($D$);
- $q_0 \in Q$: estado inicial;
- $q_{aceita}, q_{rejeita} \in Q$: estados de aceitação e rejeição, com $q_{aceita} \neq q_{rejeita}$.

A cabeça começa sobre a célula mais à esquerda, e o primeiro símbolo em branco marca o fim da entrada originalmente escrita. Se a máquina tentar mover a cabeça para além da extremidade esquerda, ela simplesmente permanece no lugar.

#### Configurações

Uma **configuração** captura o estado atual, o conteúdo da fita e a posição da cabeça num instante: para um estado $q$ e cadeias $u, v$ sobre $\Gamma$, escrevemos $uqv$ para dizer que o estado é $q$, a fita contém $uv$, e a cabeça está sobre o primeiro símbolo de $v$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2088.png)

Uma configuração **origina** outra se a máquina pode ir de uma para a outra em um único passo. Formalmente, para $a, b, c \in \Gamma$, $u, v \in \Gamma^*$ e estados $q_i, q_j$: $uaq_ibv$ origina $uq_jacv$ se $\delta(q_i, b) = (q_j, c, E)$ (movimento à esquerda); e $uaq_ibv$ origina $uacq_jv$ se $\delta(q_i, b) = (q_j, c, D)$ (movimento à direita). Casos especiais ocorrem nas extremidades: na esquerda, cuida-se para a cabeça não "cair" da fita; na direita, a configuração $uaq_i$ é tratada como $uaq_i\sqcup$ (pois assume-se que há brancos infinitos após a parte representada).

A configuração **inicial** de $M$ sobre $w$ é $q_0w$. Uma configuração é de **aceitação** se o estado é $q_{aceita}$, e de **rejeição** se é $q_{rejeita}$; ambas são configurações de **parada**, e não originam novas configurações — equivalentemente, poderíamos ter definido $\delta$ apenas sobre $Q' \times \Gamma$, com $Q'=Q \setminus \{q_{aceita}, q_{rejeita}\}$.

#### Linguagens reconhecidas e decididas

Uma linguagem é **Turing-reconhecível** (ou **recursivamente enumerável**) se alguma máquina de Turing a reconhece: $M$ aceita $w$ se existe uma sequência de configurações $C_1, \ldots, C_k$ onde $C_1$ é a inicial sobre $w$, cada $C_i$ origina $C_{i+1}$, e $C_k$ é de aceitação. A coleção de cadeias aceitas por $M$ é $L(M)$.

Uma linguagem é **Turing-decidível** (ou simplesmente **decidível**, ou **recursiva**) se alguma máquina de Turing a *decide*. Toda linguagem decidível é Turing-reconhecível (mas não vice-versa, como veremos).

Ao iniciar uma máquina sobre uma entrada, três resultados são possíveis: **aceitar**, **rejeitar** ou **entrar em loop** (nunca parar, com comportamento simples ou arbitrariamente complexo). Uma máquina pode, portanto, falhar em aceitar uma entrada tanto por rejeitá-la explicitamente quanto por entrar em loop — e muitas vezes é difícil distinguir uma máquina em loop de uma que só está demorando muito. Por isso preferimos máquinas que **sempre param**, chamadas **decisores**: elas sempre tomam uma decisão (aceitar ou rejeitar). Um decisor que reconhece uma linguagem também a *decide*.

!!! example "Exemplos de máquinas de Turing"
    1. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2089.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2090.png) — com função de transição: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2091.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2092.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2093.png)
    2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2094.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2095.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2096.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2097.png)
    3. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2098.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%2099.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20100.png)
    4. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20101.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20102.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20103.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20104.png)

### Variantes de máquinas de Turing

Definições alternativas — com múltiplas fitas, ou com não-determinismo — são chamadas de **variantes** do modelo de máquina de Turing. O modelo original e suas variantes razoáveis têm o mesmo poder computacional, reconhecendo exatamente a mesma classe de linguagens; para mostrar que dois modelos são equivalentes, basta mostrar que um simula o outro. Chamamos de **robustez** a propriedade de uma máquina manter o mesmo poder computacional mesmo quando o modelo básico é alterado ou estendido. Autômatos finitos e autômatos com pilha já são razoavelmente robustos, mas as máquinas de Turing têm robustez ainda mais elevada.

#### Máquinas de Turing multifita

Uma MT **multifita** é como uma MT comum, mas com $k$ fitas, cada uma com sua própria cabeça; inicialmente, a entrada está na fita 1 e as demais começam em branco. A função de transição passa a ser:

$$\delta: Q \times \Gamma^k \rightarrow Q \times \Gamma^k \times \{E, D, P\}^k$$

onde $P$ representa a possibilidade de a cabeça permanecer parada.

Apesar de parecerem mais poderosas, MTs multifita são **equivalentes** a MTs de fita única.

**Teorema.** Toda MT multifita tem uma MT de fita única equivalente.

*Ideia.* Simula-se a MT multifita $M$ (com $k$ fitas) por uma MT de fita única $S$, que armazena o conteúdo de todas as $k$ fitas na sua única fita, separadas pelo novo símbolo delimitador $\#$. Para registrar a posição de cada cabeça, $S$ usa versões "pontuadas" dos símbolos de fita — novos símbolos adicionados ao alfabeto — marcando onde cada cabeça virtual estaria.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20105.png)

*Passo a passo da simulação:* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20106.png)

Com isso, provamos que toda MT multifita pode ser simulada por uma MT de fita única equivalente. Consequentemente, uma linguagem é Turing-reconhecível se e somente se alguma MT multifita a reconhece (uma direção é trivial, pois toda MT de fita única é um caso especial de multifita com $k=1$; a outra segue da equivalência recém-provada).

#### Máquinas de Turing não-determinísticas

Em uma MT **não-determinística**, a máquina pode proceder segundo várias possibilidades simultaneamente, com $\delta: Q \times \Gamma \rightarrow \mathcal{P}(Q \times \Gamma \times \{E, D\})$. A computação é uma **árvore**, cujos ramos correspondem às diferentes possibilidades; a máquina aceita a entrada se **algum** ramo leva ao estado de aceitação.

**Teorema.** Toda MT não-determinística tem uma MT determinística equivalente.

*Ideia.* Simula-se a MT não-determinística $N$ com uma MT determinística $D$ que tenta todos os ramos possíveis da computação de $N$; se $D$ encontra o estado de aceitação em algum ramo, aceita (caso contrário, a simulação pode não terminar). A computação de $N$ sobre $w$ é vista como uma árvore cuja raiz é a configuração inicial, e $D$ precisa buscar nessa árvore por uma configuração de aceitação.

!!! warning "Por que busca em largura, e não em profundidade"
    Uma busca em **profundidade** desceria por um único ramo inteiro antes de voltar — e, se esse ramo for infinito, $D$ nunca encontraria uma configuração de aceitação que estivesse em outro ramo. Por isso, $D$ precisa fazer uma busca em **largura**: explorar todos os ramos numa dada profundidade antes de avançar para a próxima, garantindo que todo nó da árvore será eventualmente visitado.

*Prova.* A MT determinística simuladora $D$ usa 3 fitas (equivalente, pela seção anterior, a uma única fita): a fita 1 guarda a entrada original, nunca alterada; a fita 2 mantém uma cópia da fita de $N$ ao longo de um ramo específico de sua computação; a fita 3 registra a posição de $D$ na árvore de computação não-determinística de $N$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20107.png)

Para representar essa posição, associa-se a cada nó da árvore um **endereço**: uma cadeia sobre $\Sigma_b = \{1, 2, \ldots, b\}$, onde $b$ é o maior número de escolhas possível em qualquer configuração de $N$ (por exemplo, o endereço $231$ identifica o nó alcançado indo da raiz ao 2º filho, depois ao 3º filho deste, depois ao 1º filho deste último). Cada símbolo do endereço diz qual escolha fazer ao simular um passo; se um símbolo não corresponder a nenhuma escolha disponível naquele ponto, o endereço é inválido. A cadeia vazia é o endereço da raiz.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20108.png)

Com essa representação, $D$ enumera sistematicamente todos os endereços (em ordem de comprimento/largura), simulando o ramo correspondente a cada um — provando a equivalência entre MT não-determinística e determinística.

**Corolário.** Uma linguagem é Turing-reconhecível se e somente se alguma MT não-determinística a reconhece (uma direção é trivial — toda MT determinística já é um caso especial de não-determinística — e a outra segue da equivalência provada). Chamamos uma MT não-determinística de **decisor** se *todos* os seus ramos param sobre toda entrada; e uma linguagem é decidível se e somente se alguma MT não-determinística a decide.

#### Enumeradores

Um **enumerador** é uma MT com uma "impressora" anexada, que serve como dispositivo de saída: sempre que a máquina quer adicionar uma cadeia à sua lista, ela a envia para a impressora.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20109.png)

Um enumerador $E$ inicia com a fita de entrada em branco; se não parar, pode imprimir uma lista infinita de cadeias. A **linguagem enumerada** por $E$ é a coleção de todas as cadeias que ela eventualmente imprime (podendo gerá-las em qualquer ordem, com repetições). Formalmente, pode-se definir um enumerador como uma MT de duas fitas, onde uma funciona normalmente e a outra atua como impressora.

**Teorema.** Uma linguagem é Turing-reconhecível se e somente se algum enumerador a enumera.

*(⇒)* Dado um enumerador $E$ para $A$, constrói-se uma MT $M$ que reconhece $A$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20110.png) — $M$ simula $E$ e aceita a entrada se, e quando, $E$ a imprimir.

*(⇐)* Dado um reconhecedor $M$ para $A$, constrói-se um enumerador $E$: seja $s_1, s_2, s_3, \ldots$ uma lista de todas as cadeias em $\Sigma^*$; ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20111.png) — $E$ roda $M$ sobre prefixos crescentes dessa lista por quantidades crescentes de passos, imprimindo qualquer $s_i$ que $M$ aceite. Se $M$ aceita uma cadeia específica $s$, ela aparecerá na lista impressa por $E$ em algum momento — e uma quantidade finita de vezes, já que $E$ reinicia $M$ do zero sobre cada cadeia a cada repetição do laço.

### Definição formal de algoritmo

De forma informal, um **algoritmo** é uma coleção de instruções simples para realizar alguma tarefa. Mas a necessidade de uma definição *precisa* surgiu de um contexto histórico muito específico.

!!! note "Os problemas de Hilbert"
    David Hilbert identificou, no início do século XX, 23 problemas matemáticos como desafios para a área. O 10º deles tratava justamente de algoritmos: *"descrever, em um número finito de operações, se uma dada equação diofantina possui raízes inteiras"* — isto é, encontrar um algoritmo para testar se um polinômio tem raízes inteiras. Hilbert acreditava que tal algoritmo existia e só faltava encontrá-lo.

    Hoje sabemos que **não existe** tal algoritmo — mas, antes de provar isso, os matemáticos da época precisaram primeiro definir formalmente o que *seria* um algoritmo. Alonzo Church usou o λ-cálculo; Alan Turing usou as máquinas de Turing. Mais tarde, provou-se que as duas definições eram equivalentes — resultado conhecido como **tese de Church-Turing**.

Formalizando o 10º problema de Hilbert: seja $D = \{p \mid p$ é um polinômio com uma raiz inteira$\}$ — o problema é, essencialmente, perguntar se $D$ é decidível. A resposta é **não**, mas pode-se mostrar que $D$ é Turing-reconhecível:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20112.png)

Com a tese de Church-Turing em mãos, podemos finalmente definir um **algoritmo como uma máquina de Turing que para em todas as entradas** — formalizar um algoritmo passa a significar descrever uma MT que reconhece uma linguagem Turing-decidível.

#### Terminologia para descrever máquinas de Turing

A entrada de uma MT é sempre uma cadeia. Para fornecer como entrada um objeto que não é naturalmente uma cadeia (um grafo, um autômato, outra máquina de Turing...), primeiro o representamos como cadeia, e a MT é programada para decodificar essa representação apropriadamente. A notação $\langle O \rangle$ denota a codificação do objeto $O$ como cadeia; para vários objetos, $\langle O_1, \ldots, O_k \rangle$ denota a codificação conjunta em uma única cadeia. A escolha específica de codificação não importa, desde que seja razoável — uma MT sempre pode traduzir entre codificações equivalentes.

Por convenção, descrevemos algoritmos de MT como um texto identado entre aspas, dividido em **estágios**, cada um com passos individuais devidamente identados. A primeira linha descreve a entrada esperada: se for simplesmente $w$, a entrada é uma cadeia qualquer; se for uma codificação $\langle O \rangle$, a MT primeiro testa implicitamente se a entrada codifica corretamente um objeto da forma esperada, rejeitando caso contrário.

!!! example
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20113.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20114.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20115.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20116.png)

---

## Decidibilidade

### Linguagens decidíveis

O foco agora são as linguagens relacionadas a autômatos e gramáticas — porque muitos problemas nesse domínio têm aplicações práticas diretas (compiladores, verificação, etc.), e porque, curiosamente, nem todo problema sobre autômatos e gramáticas é decidível.

#### Problemas decidíveis sobre linguagens regulares

**O problema da aceitação.** Testar se um AFD específico $B$ aceita uma cadeia $w$ pode ser expresso como pertinência à linguagem:

$$A_{AFD} = \{\langle B, w \rangle \mid B \text{ é um AFD que aceita } w\}$$

!!! tip "Problemas computacionais como linguagens"
    Esse é um padrão geral: qualquer problema computacional pode ser formulado como testar pertinência em uma linguagem apropriada. Mostrar que a linguagem é decidível é o mesmo que mostrar que o problema computacional é decidível.

**Teorema.** $A_{AFD}$ é decidível.

*Ideia.* Basta apresentar uma MT $M$ que decide $A_{AFD}$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20117.png)

*Prova.* $M$ primeiro verifica se a entrada $\langle B, w \rangle$ representa corretamente um AFD $B$ (uma lista de seus 5 componentes $Q, \Sigma, \delta, q_0, F$) junto com uma cadeia $w$ — rejeitando caso contrário. Em seguida, $M$ simula $B$ diretamente, mantendo na própria fita o registro do estado atual de $B$ e de sua posição na entrada $w$ (inicialmente, estado $q_0$ e posição no símbolo mais à esquerda), atualizando ambos conforme $\delta$. Ao processar o último símbolo de $w$, $M$ aceita se $B$ estiver em estado de aceitação, e rejeita caso contrário.

O mesmo resultado vale para AFNs e para expressões regulares:

- $A_{AFN} = \{\langle B, w \rangle \mid B$ é um AFN que aceita $w\}$ é decidível — a MT $N$ converte o AFN recebido em um AFD equivalente e então chama $M$ (de $A_{AFD}$) como sub-rotina: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20118.png)
- $A_{ExR} = \{\langle R, w \rangle \mid R$ é uma expressão regular que gera $w\}$ é decidível: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20119.png)

Essas três provas mostram que, para fins de decidibilidade, entregar à MT um AFD, um AFN ou uma expressão regular é equivalente — a máquina sempre pode converter de uma representação para outra.

**O problema da vacuidade.** Em vez de testar se um autômato aceita uma cadeia *específica*, podemos testar se ele aceita *alguma* cadeia:

$$V_{AFD} = \{\langle A \rangle \mid A \text{ é um AFD e } L(A) = \emptyset\}$$

**Teorema.** $V_{AFD}$ é decidível.

*Ideia.* Um AFD aceita alguma cadeia se, e somente se, é possível alcançar algum estado de aceitação a partir do estado inicial seguindo setas de transição. Isso é um problema de **alcançabilidade em grafo**, resolvido com um algoritmo de marcação: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20120.png)

**O problema da equivalência.** Podemos também testar se dois AFDs reconhecem a mesma linguagem:

$$EQ_{AFD} = \{\langle A, B \rangle \mid A, B \text{ são AFDs e } L(A) = L(B)\}$$

**Teorema.** $EQ_{AFD}$ é decidível.

*Ideia.* Reduz-se ao problema da vacuidade: constrói-se um novo AFD $C$ que aceita exatamente as cadeias aceitas por $A$ ou por $B$, mas não por ambos — a **diferença simétrica** $L(A) \oplus L(B)$. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20121.png) Essa construção usa as operações de complementação, união e interseção sobre linguagens regulares (todas algoritmicamente realizáveis por MTs). $L(A) = L(B)$ se e somente se $L(C) = \emptyset$ — testável usando o teorema anterior.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20122.png)

#### Problemas decidíveis sobre linguagens livres do contexto

Analogamente, podemos decidir se uma GLC gera uma cadeia específica e se a linguagem de uma GLC é vazia.

**Teorema.** $A_{GLC} = \{\langle G, w \rangle \mid G$ é uma GLC que gera $w\}$ é decidível.

*Ideia.* A abordagem naïve — enumerar todas as derivações de $G$ até achar uma para $w$ — **não funciona**: se $G$ não gera $w$, o algoritmo nunca pararia, pois há infinitas derivações possíveis. Isso dá apenas um *reconhecedor*, não um decisor. A solução é limitar a busca a uma quantidade **finita** de derivações: colocando $G$ na forma normal de Chomsky, qualquer derivação de uma cadeia $w$ de comprimento $n$ tem exatamente $2n-1$ passos — basta, então, verificar apenas as derivações com esse comprimento fixo.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20123.png)

!!! note "Relação com compiladores"
    Esse problema está diretamente relacionado ao de *compilar* (analisar sintaticamente) uma linguagem de programação. O algoritmo descrito é correto, mas extremamente ineficiente — nunca seria usado na prática; a questão da complexidade de tempo é revisitada mais adiante.

**Teorema.** $V_{GLC} = \{\langle G \rangle \mid G$ é uma GLC e $L(G) = \emptyset\}$ é decidível.

*Ideia.* Novamente, tentar usar a MT de $A_{GLC}$ testando todas as $w$ possíveis não funciona (infinitas cadeias). A solução é resolver um problema mais geral: para cada **variável** da gramática, determinar se ela é capaz de gerar *alguma* cadeia de terminais. O algoritmo marca, primeiro, todos os terminais; depois, repetidamente percorre as regras marcando qualquer variável cujo lado direito seja composto inteiramente de símbolos já marcados — até que nenhuma nova marcação seja possível. $L(G) = \emptyset$ se e somente se a variável inicial nunca for marcada.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20124.png)

**O problema da equivalência para GLCs.** Infelizmente, o padrão não se repete aqui:

$$EQ_{GLC} = \{\langle G, H \rangle \mid G, H \text{ são GLCs e } L(G) = L(H)\}$$

A classe das LLCs **não é fechada** sob complementação nem sob interseção — por isso a técnica usada para $EQ_{AFD}$ (reduzir à vacuidade de uma diferença simétrica) não se aplica aqui. De fato, **$EQ_{GLC}$ é indecidível**.

**Toda LLC é decidível.**

*Ideia.* Uma ideia tentadora — e ruim — seria converter diretamente o AP de $A$ em uma MT, simulando sua pilha com a fita (o que é tecnicamente fácil). O problema é que o AP pode ser não-determinístico, e alguns de seus ramos de computação podem rodar para sempre, lendo e escrevendo na pilha indefinidamente sem nunca decidir. A MT simuladora teria os mesmos ramos infinitos e, portanto, não seria um decisor. A prova correta, em vez disso, reutiliza a MT $S$ já projetada para decidir $A_{GLC}$.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20125.png)

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20126.png)

A figura acima resume as relações de contenção entre as classes de linguagens vistas até aqui: regulares ⊂ livres de contexto ⊂ decidíveis ⊂ Turing-reconhecíveis ⊂ todas as linguagens.

### Problemas indecidíveis

#### O problema da parada

O primeiro e mais famoso problema indecidível é determinar se uma MT aceita ou não uma dada entrada:

$$A_{MT} = \{\langle M, w \rangle \mid M \text{ é uma MT e } M \text{ aceita } w\}$$

**Teorema.** $A_{MT}$ é indecidível.

Antes da prova, vale observar que $A_{MT}$ **é** Turing-reconhecível — este teorema mostra, portanto, que **reconhecedores são estritamente mais poderosos que decisores**: exigir que uma MT pare em *toda* entrada restringe genuinamente o conjunto de linguagens alcançáveis.

A seguinte MT $U$ reconhece $A_{MT}$:

> $U$ = "Sobre a entrada $\langle M, w \rangle$, onde $M$ é uma MT e $w$ é uma cadeia:
>
> 1. Simule $M$ sobre a entrada $w$.
> 2. Se $M$ em algum momento entra em seu estado de aceitação, aceite; se $M$ em algum momento entra em seu estado de rejeição, rejeite."

$U$ é chamada de **MT universal**, pois é capaz de simular qualquer outra MT a partir de sua descrição. Mas $U$ entra em loop sobre $\langle M, w \rangle$ sempre que $M$ entra em loop sobre $w$ — e por isso $U$ **não decide** $A_{MT}$. Este é o célebre **Problema da Parada**.

#### Diagonalização

A prova de que o problema da parada é indecidível usa a técnica de **diagonalização**, originalmente desenvolvida por Cantor para comparar tamanhos de conjuntos infinitos.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20127.png)

Um conjunto é **contável** se é finito, ou tem o mesmo tamanho que $\mathbb{N}$ (os naturais). A diagonalização mostra, por exemplo, que o conjunto dos naturais pares tem o mesmo tamanho que $\mathbb{N}$, e que o conjunto dos racionais também tem o mesmo tamanho que $\mathbb{N}$ — apesar da intuição de que "deveriam" ser maiores.

Porém, existem conjuntos **incontáveis** — grandes demais até para esse tipo de correspondência. O exemplo clássico é $\mathbb{R}$, o conjunto dos números reais.

**Teorema.** $\mathbb{R}$ é incontável.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20128.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20129.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20130.png)

Essa prova tem uma aplicação crucial em teoria da computação: ela mostra que algumas linguagens não são decidíveis — e nem mesmo Turing-reconhecíveis — simplesmente porque existe uma quantidade **incontável** de linguagens, mas apenas uma quantidade **contável** de máquinas de Turing. Por puro argumento de cardinalidade, sobram linguagens sem nenhuma MT que as reconheça.

#### Existem linguagens Turing-irreconhecíveis

Para formalizar esse argumento: o conjunto de todas as MTs é contável, porque toda MT tem uma codificação como cadeia $\langle M \rangle$, e o conjunto de todas as cadeias $\Sigma^*$ é contável para qualquer alfabeto $\Sigma$ (basta omitir as cadeias que não codificam MTs legítimas para obter uma lista enumerável de todas as MTs).

Já o conjunto de **todas as linguagens** sobre $\Sigma$ é incontável. Primeiro, mostra-se que o conjunto $B$ de todas as sequências binárias infinitas é incontável (por diagonalização, análoga à usada para $\mathbb{R}$). Depois, estabelece-se uma correspondência entre o conjunto $\mathcal{L}$ de todas as linguagens sobre $\Sigma$ e $B$: enumerando $\Sigma^* = \{s_1, s_2, \ldots\}$, cada linguagem $A \in \mathcal{L}$ corresponde a uma única sequência binária — sua **sequência característica** — cujo $i$-ésimo bit é $1$ se $s_i \in A$ e $0$ caso contrário.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20131.png)

A função $f: \mathcal{L} \rightarrow B$, onde $f(A)$ é a sequência característica de $A$, é injetora e sobrejetora — uma correspondência biunívoca. Como $B$ é incontável, $\mathcal{L}$ também é.

Como $\mathcal{L}$ (incontável) não pode ser colocado em correspondência com o conjunto de todas as MTs (contável), **conclui-se que existem linguagens que nenhuma MT reconhece**.

#### O problema da parada é indecidível (prova completa)

**Teorema.** $A_{MT}$ é indecidível.

*Prova, por contradição.* Suponha que $A_{MT}$ seja decidível, e que $H$ seja um decisor para ela, de modo que

$$H(\langle M, w \rangle) = \begin{cases} \text{aceita} & \text{se } M \text{ aceita } w \\ \text{rejeita} & \text{se } M \text{ não aceita } w \end{cases}$$

Construímos uma nova MT $D$ que usa $H$ como sub-rotina: $D$ chama $H$ para determinar o que $M$ faria se sua entrada fosse sua **própria descrição**, $\langle M \rangle$ — e então $D$ faz exatamente o **oposto**.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20132.png)

Assim, $D(\langle M \rangle) = \text{aceita}$ se $M$ **não** aceita $\langle M \rangle$, e $D(\langle M \rangle) = \text{rejeita}$ se $M$ aceita $\langle M \rangle$.

!!! tip "Uma analogia útil"
    O papel de $D$ aqui é parecido com o de um compilador: um programa capaz de processar (traduzir, ou neste caso, analisar o comportamento de) outros programas — e que, como qualquer compilador escrito na própria linguagem que compila, pode ser aplicado a si mesmo.

Rodando $D$ sobre sua própria descrição $\langle D \rangle$: $D(\langle D \rangle) = \text{aceita}$ se $D$ **não** aceita $\langle D \rangle$, e $D(\langle D \rangle) = \text{rejeita}$ se $D$ aceita $\langle D \rangle$. Ou seja: **qualquer que seja o resultado, $D$ é forçada a fazer exatamente o oposto do que fez** — uma contradição lógica direta. Logo, nem $D$ nem $H$ podem existir, e $A_{MT}$ é indecidível. $\blacksquare$

!!! example "Revisão visual da prova"
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20133.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20134.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20135.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20136.png)

#### Uma linguagem nem Turing-reconhecível

A linguagem $A_{MT}$ é indecidível, mas ainda é Turing-reconhecível. Existem linguagens que sequer têm essa propriedade mais fraca.

Dizemos que uma linguagem é **co-Turing-reconhecível** se é o complemento de uma linguagem Turing-reconhecível.

**Teorema.** Uma linguagem é decidível se, e somente se, ela é Turing-reconhecível **e** co-Turing-reconhecível (isto é, ela e seu complemento são ambas Turing-reconhecíveis).

*Prova.*

- **(⇒)** Se $A$ é decidível, então tanto $A$ quanto seu complemento $A^c$ são decidíveis (o complemento de uma linguagem decidível também é decidível), e toda linguagem decidível é Turing-reconhecível — logo, ambas são Turing-reconhecíveis.
- **(⇐)** Se $A$ e $A^c$ são ambas Turing-reconhecíveis, sejam $M_1$ e $M_2$ seus respectivos reconhecedores. Construímos $M$ que roda $M_1$ e $M_2$ **em paralelo** (em duas fitas, alternando um passo de cada): ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20137.png) Toda cadeia $w$ está em $A$ ou em $A^c$, então uma das duas máquinas necessariamente aceita $w$ — portanto $M$ sempre para, aceitando exatamente as cadeias de $A$. $M$ é um decisor, e $A$ é decidível.

**Corolário.** $A_{MT}^c$ (o complemento de $A_{MT}$) não é Turing-reconhecível — pois, se fosse, $A_{MT}$ seria Turing-reconhecível *e* co-Turing-reconhecível, e portanto decidível, contradizendo o teorema anterior.

---

## Redutibilidade

A **redutibilidade** é o principal método para provar que problemas são computacionalmente insolúveis. Uma **redução** é uma forma de converter um problema em outro, de modo que uma solução para o segundo possa ser usada para resolver o primeiro. A redutibilidade sempre envolve dois problemas, $A$ e $B$: se $A$ se reduz a $B$, então uma solução para $B$ nos dá uma solução para $A$ — mas a redutibilidade, por si só, nada diz sobre a solubilidade de $A$ ou $B$ *isoladamente*, apenas sobre a solubilidade de $A$ *na presença* de uma solução para $B$.

Essa ideia tem papel central tanto na classificação de problemas por decidibilidade quanto, mais adiante, em teoria da complexidade.

### Problemas indecidíveis sobre máquinas de Turing

**O problema da parada "geral" (PARA).** Sabendo que $A_{MT}$ é indecidível, consideremos o problema relacionado de determinar se uma MT *para* (aceitando **ou** rejeitando) sobre uma entrada dada:

$$PARA_{MT} = \{\langle M, w \rangle \mid M \text{ é uma MT e } M \text{ para sobre } w\}$$

**Teorema.** $PARA_{MT}$ é indecidível.

*Ideia.* Por contradição: supondo que $PARA_{MT}$ fosse decidível, mostramos que $A_{MT}$ também seria — contradizendo o que já sabemos. A estratégia é **reduzir $A_{MT}$ a $PARA_{MT}$**.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20138.png)

*Prova.* Supondo que a MT $R$ decida $PARA_{MT}$, construímos $S$ para decidir $A_{MT}$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20139.png) — claramente, se $R$ decide $PARA_{MT}$, então $S$ decide $A_{MT}$. Mas, como $A_{MT}$ é indecidível, $PARA_{MT}$ também deve ser.

**O problema da vacuidade para MTs.** Seja $V_{MT} = \{\langle M \rangle \mid M$ é uma MT e $L(M) = \emptyset\}$.

**Teorema.** $V_{MT}$ é indecidível.

*Ideia.* Novamente por contradição, reduzindo $A_{MT}$ a $V_{MT}$. Dado $R$ que decidiria $V_{MT}$, uma ideia ingênua seria rodar $R$ sobre $\langle M \rangle$ diretamente — mas isso só diria se $L(M)$ é vazia (ou seja, se $M$ aceita *alguma* cadeia), não se $M$ aceita a cadeia específica $w$. Em vez disso, modificamos $\langle M \rangle$ para obter uma máquina $M_1$ que rejeita todas as cadeias *exceto* $w$, mas que, sobre $w$, se comporta como a $M$ original. Assim, $L(M_1) \neq \emptyset$ se e somente se $M$ aceita $w$.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20140.png) $M_1$ incorpora $w$ em sua própria descrição e, dada qualquer entrada $x$, primeiro verifica caractere por caractere se $x = w$ (rejeitando se não for) antes de simular $M$ sobre $w$. Juntando tudo: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20141.png) — $S$ precisa computar a descrição de $M_1$ a partir das descrições de $M$ e $w$, o que é simples (basta adicionar a $M$ os novos estados que implementam o teste $x = w$). Se $R$ fosse um decisor para $V_{MT}$, $S$ seria um decisor para $A_{MT}$ — impossível. Logo, $V_{MT}$ é indecidível.

**O problema da regularidade.** Seja $REGULAR_{MT} = \{\langle M \rangle \mid M$ é uma MT e $L(M)$ é uma linguagem regular$\}$ — equivalente a perguntar se $M$ tem um autômato finito equivalente.

**Teorema.** $REGULAR_{MT}$ é indecidível.

*Ideia.* Reduz-se $A_{MT}$ a $REGULAR_{MT}$ (na direção oposta da anterior): supondo $R$ decide $REGULAR_{MT}$, construímos $S$ que decide $A_{MT}$ modificando $M$ e $w$ para obter uma nova máquina $M_2$ que reconhece uma linguagem **não regular** (como $\{0^n1^n \mid n \geq 0\}$) se $M$ *não* aceita $w$, e a linguagem regular $\Sigma^*$ se $M$ aceita $w$ — tornando a regularidade de $M_2$ equivalente a $M$ aceitar $w$.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20142.png) Se $R$ fosse decisor para $REGULAR_{MT}$, $S$ seria decisor para $A_{MT}$ — contradição.

**O problema da equivalência entre MTs.** Seja $EQ_{MT} = \{\langle M_1, M_2 \rangle \mid M_1, M_2$ são MTs e $L(M_1) = L(M_2)\}$.

**Teorema.** $EQ_{MT}$ é indecidível.

*Ideia.* Pode-se reduzir tanto a partir de $A_{MT}$ quanto a partir de $V_{MT}$ (usando $M_2$ como uma máquina fixa que nunca aceita nada, reduzindo o problema de equivalência ao de vacuidade): ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20143.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20144.png)

### Redução via histórias de computação

Uma **história de computação de aceitação** para $M$ sobre $w$ é a sequência de configurações $C_1, \ldots, C_l$ tal que $C_1$ é a configuração inicial de $M$ sobre $w$, $C_l$ é uma configuração de aceitação, e cada $C_i$ origina legitimamente $C_{i+1}$ segundo as regras de $M$. Uma **história de rejeição** é definida de forma análoga, exceto que $C_l$ é de rejeição. Essa é uma técnica importante para reduzir $A_{MT}$ a certas linguagens — especialmente útil quando o problema a ser mostrado indecidível envolve testar a *existência* de algo.

Histórias de computação são sempre sequências **finitas**: se $M$ não para sobre $w$, nenhuma história (de aceitação ou rejeição) existe para esse par. Máquinas determinísticas têm no máximo uma história de computação sobre qualquer entrada dada; máquinas não-determinísticas podem ter várias, correspondendo aos diferentes ramos possíveis.

### Autômato linearmente limitado (ALL)

Um **autômato linearmente limitado** é uma variante restrita de MT em que a cabeça de leitura/escrita não pode se mover para fora da porção da fita que contém a entrada (se tentar, permanece onde está — como já ocorre na extremidade esquerda de uma MT comum). É, portanto, uma MT com uma quantidade de memória **limitada**: só pode resolver problemas cuja necessidade de memória caiba dentro do espaço ocupado pela entrada. Usar um alfabeto de fita maior que o de entrada permite aumentar a memória disponível por, no máximo, um fator constante — ou seja, para uma entrada de comprimento $n$, a memória disponível é **linear em $n$**.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20145.png)

Toda LLC pode ser decidida por um ALL. Além disso, se $M$ é um ALL com $q$ estados e $g$ símbolos no alfabeto de fita, existem **exatamente** $qng^n$ configurações distintas para uma fita de comprimento $n$ — um fato crucial, pois limita o espaço de busca a um tamanho finito e computável.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20146.png)

**O problema da aceitação para ALLs.** Seja $A_{ALL} = \{\langle M, w \rangle \mid M$ é um ALL que aceita $w\}$.

**Teorema.** $A_{ALL}$ é decidível.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20147.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20148.png) — a ideia central é que, como o número de configurações possíveis é finito ($qng^n$), basta simular $M$ por, no máximo, esse número de passos: se $M$ ainda não parou, ela necessariamente está repetindo uma configuração já vista, e portanto está em loop (e deve ser rejeitada).

**O problema da vacuidade para ALLs.** Seja $V_{ALL} = \{\langle M \rangle \mid M$ é um ALL e $L(M) = \emptyset\}$.

**Teorema.** $V_{ALL}$ é indecidível.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20149.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20150.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20151.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20152.png) (a técnica, mais uma vez, é uma redução via histórias de computação: constrói-se um ALL cuja linguagem é não vazia exatamente quando existe uma história de computação de aceitação de uma MT arbitrária sobre uma entrada arbitrária — reduzindo a indecidibilidade de $A_{MT}$ ao problema de vacuidade de ALLs).

**O problema de totalidade para GLCs.** Seja $TODAS_{GLC} = \{\langle G \rangle \mid G$ é uma GLC e $L(G) = \Sigma^*\}$.

**Teorema.** $TODAS_{GLC}$ é indecidível.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20153.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20154.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20155.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20156.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20157.png)

### O problema da correspondência de Post (PCP)

O **PCP** pede para determinar se uma coleção de "dominós" com cadeias em cima e em baixo admite um **emparelhamento**: uma ordem em que, concatenando as cadeias de cima na ordem escolhida, obtemos exatamente a mesma cadeia que concatenando as de baixo na mesma ordem.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20158.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20159.png)

Formalmente, uma instância do PCP é uma coleção $P$ de dominós $\left[\frac{t_i}{b_i}\right]$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20160.png)

Um **emparelhamento** é uma sequência de índices $i_1, i_2, \ldots, i_l$ tal que $t_{i_1}t_{i_2}\ldots t_{i_l} = b_{i_1}b_{i_2}\ldots b_{i_l}$. O problema é determinar se $P$ tem um emparelhamento:

$$PCP = \{\langle P \rangle \mid P \text{ é uma instância do PCP com um emparelhamento}\}$$

**Teorema.** $PCP$ é indecidível.

*Ideia.* A técnica principal, de novo, é reduzir $A_{MT}$ a $PCP$ via **histórias de computação de aceitação**. Dada qualquer MT $M$ e entrada $w$, construímos uma instância $P$ do PCP tal que um emparelhamento de $P$ corresponde exatamente a uma história de computação de aceitação de $M$ sobre $w$ — se pudermos decidir se $P$ tem emparelhamento, podemos decidir se $M$ aceita $w$. A ideia construtiva é escolher os dominós de $P$ de modo que montar um emparelhamento **force** a ocorrência de uma simulação de $M$: cada dominó conecta uma posição (ou posições) de uma configuração à posição correspondente na configuração seguinte.

Para simplificar a construção, assume-se (sem perda de generalidade, ajustando $M$) que ela nunca tenta mover a cabeça para além da extremidade esquerda; se $w = \varepsilon$, usa-se $\sqcup$ no lugar de $w$. Também é preciso que o emparelhamento comece obrigatoriamente com o primeiro dominó da lista — essa versão restrita é chamada de **Problema de Correspondência de Post Modificado (PCPM)**:

$$PCPM = \{\langle P \rangle \mid P \text{ é uma instância do PCP com um emparelhamento começando pelo primeiro dominó}\}$$

*Prova.* Supomos que $R$ decide o PCP e construímos $S$ que decide $A_{MT}$. Seja $M = (Q, \Sigma, \Gamma, \delta, q_0, q_{aceita}, q_{rejeita})$. $S$ constrói uma instância $P$ do PCP que tem emparelhamento se e somente se $M$ aceita $w$ — construindo primeiro uma instância $P'$ do PCPM:

1. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20161.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20162.png)
2. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20163.png)
3. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20164.png)
4. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20165.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20166.png)
5. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20167.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20168.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20169.png)
6. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20170.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20171.png)
7. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20172.png)

Com isso, $P'$ é construído de forma que seu emparelhamento simula exatamente a computação de $M$ sobre $w$. A diferença entre PCPM e PCP é só a exigência do primeiro dominó — se vista apenas como instância do PCP (sem essa exigência), $P'$ pode ter um emparelhamento trivial, independente de $M$ parar sobre $w$ ou não.

**Convertendo PCPM em PCP.** A ideia é embutir a exigência "começar pelo primeiro dominó" diretamente na estrutura dos dominós, tornando-a automática. Definimos as notações: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20173.png) onde $\star u$ insere um $\star$ antes de cada caractere, $u\star$ insere depois, e $\star u \star$ insere antes e depois. Dada a coleção $P'$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20174.png) construímos $P$ como: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20175.png)

Nessa nova instância $P$ (vista como PCP comum, sem a exigência especial), a *única* cadeia capaz de iniciar um emparelhamento é o dominó $\left[\frac{\star t_1}{\star b_1 \star}\right]$, pois é o único cujos topo e base começam com o mesmo símbolo. Os $\star$'s adicionais se intercalam com os símbolos originais (que passam a ocupar as posições pares do emparelhamento) sem afetar a existência de soluções; o dominó extra $\left[\frac{\star \diamond}{\diamond}\right]$ permite que o topo adicione o $\star$ final que falta ao término do emparelhamento.

Assim, para qualquer MT $M$ e entrada $w$, construímos uma instância $P'$ do PCPM cuja solução existe se e somente se corresponde a uma história de computação de aceitação de $M$ sobre $w$ — ou seja, **$A_{MT}$ se reduz a PCPM**, o que prova que **PCPM é indecidível**. E como qualquer instância do PCPM pode ser convertida em uma instância equivalente do PCP (PCPM se reduz a PCP), concluímos, por transitividade, que **o PCP é indecidível**.

### Redutibilidade por mapeamento

A noção de "reduzir um problema a outro" pode ser formalizada de várias maneiras, dependendo da aplicação. A mais simples e amplamente usada é a **redutibilidade por mapeamento**, que depende primeiro do conceito de **função computável**.

**Função computável.** Uma função $f: \Sigma^* \rightarrow \Sigma^*$ é computável se alguma MT $M$, sobre toda entrada $w$, para com exatamente $f(w)$ escrito em sua fita. Todas as operações aritméticas usuais sobre inteiros são computáveis (por exemplo, uma máquina que recebe $\langle m, n \rangle$ e retorna $m + n$). Funções computáveis também podem transformar descrições de máquinas: por exemplo, uma função $f$ que recebe $w = \langle M \rangle$ e retorna a descrição $\langle M' \rangle$ de uma máquina equivalente a $M$ que nunca tenta mover a cabeça além da extremidade esquerda — bastando adicionar alguns estados de controle a $M$ (e retornando $\varepsilon$ se $w$ não codificar legitimamente uma MT).

**Definição formal.** A linguagem $A$ é **redutível por mapeamento** à linguagem $B$, escrito $A \leq_m B$, se existe uma função computável $f: \Sigma^* \rightarrow \Sigma^*$ tal que, para toda $w$: $w \in A \iff f(w) \in B$. A função $f$ é chamada **redução** de $A$ para $B$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20176.png)

A utilidade prática: se um problema $A$ é redutível por mapeamento a um problema $B$ já resolvido, obtemos automaticamente uma solução para $A$.

**Teorema.** Se $A \leq_m B$ e $B$ é decidível, então $A$ é decidível.

*Prova.* Seja $M$ o decisor para $B$ e $f$ a redução de $A$ para $B$. Descrevemos um decisor $N$ para $A$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20177.png) — sobre entrada $w$, $N$ computa $f(w)$ e roda $M$ sobre $f(w)$, retornando o que $M$ retornar. Como $f$ é redução de $A$ para $B$, $w \in A \iff f(w) \in B$; então $M$ aceita $f(w)$ exatamente quando $w \in A$, e $N$ funciona como desejado.

**Corolário (contrapositiva).** Se $A \leq_m B$ e $A$ é indecidível, então $B$ é indecidível.

Isso dá uma forma mais limpa e direta de reconstruir todas as provas de indecidibilidade vistas antes — basta exibir a redução $f$ explicitamente, em vez de construir uma máquina $S$ "por contradição":

- **$PARA_{MT}$ é indecidível** via $A_{MT} \leq_m PARA_{MT}$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20178.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20179.png)
- **PCP é indecidível** via $A_{MT} \leq_m PCP$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20180.png)
- **$V_{MT}$ é indecidível** via $A_{MT} \leq_m V_{MT}$: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20181.png)

O mesmo esquema se aplica à Turing-reconhecibilidade:

**Teorema.** Se $A \leq_m B$ e $B$ é Turing-reconhecível, então $A$ é Turing-reconhecível (a prova é idêntica à do teorema para decidibilidade, exceto que $M$ e $N$ são reconhecedores em vez de decisores).

**Corolário.** Se $A \leq_m B$ e $B$ não é Turing-reconhecível, então $A$ não é Turing-reconhecível. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20182.png)

**Exemplo culminante:** $EQ_{MT}$ **não é nem Turing-reconhecível nem co-Turing-reconhecível** — um resultado ainda mais forte que simples indecidibilidade, provado reduzindo, de ambos os lados, a partir de $A_{MT}$ e de $A_{MT}^c$. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20183.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20184.png)

---

## Complexidade de Tempo

### Medindo complexidade

Depois de saber *se* um problema é computável, a próxima pergunta natural é *quão eficientemente*. O número de passos que um algoritmo usa sobre uma entrada depende, em princípio, de vários parâmetros — mas, para simplificar, medimos o tempo de execução **puramente como função do comprimento da cadeia de entrada**, ignorando outros fatores.

- Na **análise de pior caso**, consideramos o tempo de execução mais longo entre todas as entradas de um dado comprimento.
- Na **análise de caso médio**, consideramos a média dos tempos de execução entre todas as entradas daquele comprimento.

O **tempo de execução** de uma MT determinística $M$ que para sobre toda entrada é a função $f: \mathbb{N} \rightarrow \mathbb{N}$, onde $f(n)$ é o número máximo de passos que $M$ usa sobre qualquer entrada de comprimento $n$. Dizemos que $M$ **roda em tempo $f(n)$**, ou é uma **MT de tempo $f(n)$**.

### Notações assintóticas

Para estimar tempos de execução de forma útil, usamos **análise assintótica**: entender o comportamento do algoritmo sobre entradas *grandes*, considerando apenas o termo de maior ordem da expressão do tempo de execução — descartando coeficientes e termos de ordem menor, já que o termo dominante prevalece para entradas suficientemente grandes.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20185.png)

**Notação Big-O (notação assintótica de limite superior).** ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20186.png)

$f(n) = O(g(n))$ significa que $f$ é, assintoticamente, menor ou igual a $g$ — descreve, portanto, o **pior caso**: se um algoritmo é $O(n^2)$, ele nunca será assintoticamente pior que $n^2$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20187.png)

Alguns fatos úteis sobre logaritmos e expressões aritméticas dentro da notação Big-O:

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20188.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20189.png)

**Notação little-o.** Usada para dizer que uma função é **estritamente** menor, assintoticamente, que outra — a diferença para Big-O é que a comparação é $<$ (estrita), não $\leq$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20190.png)

!!! example
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20191.png)

### Classes de complexidade de tempo

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20192.png)

!!! example "Analisando o tempo de $A = \{0^k1^k \mid k \geq 0\}$"
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20193.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20194.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20195.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20196.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20197.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20198.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20199.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20200.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20201.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20202.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20203.png)
    ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20204.png)

### Relações de complexidade entre modelos computacionais

A escolha do modelo computacional pode, em princípio, afetar a complexidade de tempo de uma linguagem — mas, na prática, os principais modelos razoáveis diferem apenas por fatores polinomiais.

**Teorema.** Para $t(n) \geq n$, toda MT multifita de tempo $t(n)$ tem uma MT de fita única equivalente de tempo $O(t^2(n))$.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20205.png)

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20206.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20207.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20208.png)

O **tempo de execução de uma MT não-determinística** $N$ é a função $f: \mathbb{N} \rightarrow \mathbb{N}$ onde $f(n)$ é o número máximo de passos que $N$ usa em **qualquer** ramo de sua computação, sobre **qualquer** entrada de comprimento $n$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20209.png)

Essa definição é a base para caracterizar a complexidade de uma classe de problemas particularmente importante — a classe NP.

**Teorema.** Para $t(n) \geq n$, toda MT não-determinística de fita única de tempo $t(n)$ tem uma MT determinística de fita única equivalente de tempo $2^{O(t(n))}$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20210.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20211.png)

### Classe P

Diferenças **polinomiais** em tempo de execução são consideradas pequenas; diferenças **exponenciais** são consideradas grandes. Algoritmos de tempo exponencial costumam surgir de busca por força bruta, e raramente são úteis na prática. Um fato conveniente: todos os modelos computacionais determinísticos razoáveis são **polinomialmente equivalentes** — cada um pode simular qualquer outro com, no máximo, um aumento polinomial de tempo.

**Definição.** $P$ é a classe das linguagens decidíveis em tempo polinomial por uma MT determinística de fita única.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20212.png)

Aqui, $\text{TIME}(f(n)) = \{L \mid L$ é decidida por uma MT determinística em tempo $O(f(n))\}$ é uma **classe de complexidade de tempo determinístico**, e $P = \bigcup_k \text{TIME}(n^k)$.

Como $P$ é invariante sob todos os modelos polinomialmente equivalentes à MT determinística de fita única, ela é uma classe **matematicamente robusta**. $P$ corresponde, aproximadamente, à classe de problemas **realisticamente solúveis** em um computador: quando um problema está em $P$, existe um método que o resolve em tempo $n^k$ para alguma constante $k$.

!!! example "$P$ em ação"
    - **CAM** (caminho em grafo): $CAM = \{\langle G, s, t \rangle \mid G$ é um grafo direcionado com um caminho direcionado de $s$ a $t\}$. $CAM \in P$. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20213.png) *Ideia*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20214.png) *Prova*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20215.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20216.png)
    - **PRIM-ES** (coprimalidade): $PRIM\text{-}ES = \{\langle x, y \rangle \mid x, y$ são primos entre si$\}$. $PRIM\text{-}ES \in P$ (via o algoritmo de Euclides). *Ideia*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20217.png) *Prova*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20218.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20219.png)
    - **Toda LLC está em $P$** — mesmo que o algoritmo direto da seção anterior (testar todas as derivações de comprimento $2n-1$) seja exponencial, existe um algoritmo polinomial (baseado em programação dinâmica, como o algoritmo CYK) para decidir pertinência em uma LLC. *Ideia*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20220.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20221.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20222.png) *Prova*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20223.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20224.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20225.png)

### Classe NP

Um **verificador** para uma linguagem $A$ é um algoritmo $V$ tal que $A = \{w \mid V$ aceita $\langle w, c \rangle$ para alguma cadeia $c\}$ — a cadeia $c$ é chamada **certificado**: uma evidência extra que, se fornecida, torna fácil checar que $w \in A$, mesmo que *encontrar* $c$ seja difícil. O tempo de um verificador é medido apenas em função do comprimento de $w$; um **verificador de tempo polinomial** roda em tempo polinomial em $|w|$. Uma linguagem é **polinomialmente verificável** se tem um verificador de tempo polinomial.

**Definição.** $NP$ é a classe das linguagens que têm verificadores de tempo polinomial.

!!! note "De onde vem o nome NP"
    $NP$ significa **tempo polinomial não-determinístico** — nome que vem de uma caracterização alternativa, equivalente, usando MTs *não-determinísticas* de tempo polinomial (em vez de verificadores). Por definição, $P \subseteq NP$ (todo problema decidível em tempo polinomial é, trivialmente, verificável em tempo polinomial — o certificado pode até ser ignorado).

Assim como $\text{TIME}(f(n))$, define-se $\text{NTIME}(f(n)) = \{L \mid L$ é decidida por uma MT não-determinística em tempo $O(f(n))\}$ — uma classe de complexidade de tempo **não-determinístico**. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20226.png)

**Teorema.** Uma linguagem está em $NP$ se, e somente se, é decidida por alguma MT não-determinística de tempo polinomial.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20227.png) *Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20228.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20229.png)

!!! example "Problemas clássicos em NP"
    - **CAMHAM** (caminho hamiltoniano): $CAMHAM = \{\langle G, s, t \rangle \mid G$ é um grafo direcionado com um caminho hamiltoniano de $s$ a $t\}$ — um caminho direcionado que visita cada nó exatamente uma vez. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20230.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20231.png)
    - **COMPOSTOS**: $COMPOSTOS = \{x \mid x = pq$ para inteiros $p, q > 1\}$ — ou seja, $x$ não é primo. O certificado é simplesmente um fator $p$.
    - **CLIQUE**: $CLIQUE = \{\langle G, k \rangle \mid G$ é um grafo não-direcionado com um $k$-clique$\}$, onde um **clique** é um subgrafo em que todo par de nós é conectado por uma aresta, e um **$k$-clique** é um clique com $k$ nós. $CLIQUE \in NP$: o certificado é o próprio conjunto de $k$ nós do clique. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20232.png) *Prova alternativa*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20233.png)
    - **SOMA-SUBC** (soma de subconjunto): $SOMA\text{-}SUBC = \{\langle S, t \rangle \mid S = \{x_1, \ldots, x_k\}$ e, para algum $\{y_1, \ldots, y_l\} \subseteq S$, $\sum y_i = t\}$. $SOMA\text{-}SUBC \in NP$: o certificado é o subconjunto que soma $t$. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20234.png) *Prova alternativa*: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20235.png)

$\text{coNP}$ é a classe que contém os complementos das linguagens em $NP$. Não se sabe se $\text{coNP} \neq NP$; intuitivamente, verificar que algo **não** está presente é, em geral, mais difícil do que verificar que **está**.

#### P vs. NP

$P$ é a classe das linguagens cuja pertinência pode ser **decidida** rapidamente; $NP$ é a classe das linguagens cuja pertinência pode ser **verificada** rapidamente (dado um certificado). É perfeitamente possível, em princípio, que $P = NP$ — não se conhece nenhuma linguagem que esteja provadamente em $NP \setminus P$.

!!! warning "Um dos maiores problemas abertos da matemática"
    $P \overset{?}{=} NP$ é um dos problemas em aberto mais importantes da computação (e da matemática) — um dos sete Problemas do Milênio do Clay Mathematics Institute. Se $P = NP$, qualquer problema verificável em tempo polinomial seria também decidível em tempo polinomial — com consequências profundas (por exemplo, para a criptografia moderna). ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20236.png)

O melhor método **conhecido** para resolver deterministicamente qualquer linguagem de $NP$ usa tempo exponencial: ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20237.png) — sabe-se provar essa contenção, mas não se sabe se $NP$ está contida em uma classe de tempo determinístico estritamente menor que exponencial.

Um avanço decisivo na compreensão de $P$ vs. $NP$ veio com a descoberta de uma nova classe: os problemas **NP-completos**.

### NP-Completude

Stephen Cook e Leonid Levin descobriram, independentemente, certos problemas em $NP$ cuja complexidade individual está ligada à da classe **inteira**: se existisse um algoritmo de tempo polinomial para qualquer um desses problemas, **todos** os problemas de $NP$ seriam polinomialmente solúveis. Esses problemas são chamados **NP-completos**, e provar que um problema é NP-completo é uma evidência muito forte de que ele **não** é solúvel em tempo polinomial.

O exemplo canônico é o problema **SAT** (satisfazibilidade booleana): determinar se uma fórmula booleana é satisfazível.

$$SAT = \{\langle \phi \rangle \mid \phi \text{ é uma fórmula booleana satisfazível}\}$$

#### Redutibilidade em tempo polinomial

Uma **função computável em tempo polinomial** é uma função computável cuja MT correspondente roda em tempo polinomial sobre toda entrada. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20238.png)

**Definição formal.** ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20239.png) A linguagem $A$ é **redutível em tempo polinomial** a $B$, escrito $A \leq_p B$, se existe uma função computável em tempo polinomial $f$ tal que $w \in A \iff f(w) \in B$ para toda $w$.

Uma redução de tempo polinomial converte o teste de pertinência em $A$ em um teste de pertinência em $B$ — se $A$ é redutível em tempo polinomial a uma linguagem já sabidamente solúvel em tempo polinomial, obtemos automaticamente uma solução polinomial para $A$.

**Teorema.** Se $A \leq_p B$ e $B \in P$, então $A \in P$.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20240.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20241.png)

#### 3SAT

É o caso especial do SAT em que toda fórmula está em **forma normal conjuntiva (FNC)** — uma conjunção de cláusulas, cada cláusula uma disjunção de literais:

```text
φ = (x1 ∨ ¬x2 ∨ x3) ∧ (¬x1 ∨ x2) ∧ ...
```

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20242.png)

No **3SAT**, cada cláusula tem exatamente **3 literais** (forma 3-FNC): ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20243.png)

**Teorema.** $3SAT \leq_p CLIQUE$.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20244.png) A redução transforma cada cláusula de 3 literais em um "grupo" de até 3 nós no grafo, conectando nós de grupos diferentes sempre que seus literais são *consistentes* (não são negações um do outro) — um $k$-clique no grafo resultante (com $k$ = número de cláusulas) corresponde exatamente a uma escolha consistente de um literal verdadeiro por cláusula, ou seja, a uma atribuição satisfatória.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20245.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20246.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20247.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20248.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20249.png)

#### Definição de NP-completude

Uma linguagem $B$ é **NP-completa** se $B \in NP$ **e** toda linguagem $A \in NP$ é redutível em tempo polinomial a $B$.

**Consequências imediatas:**

- Se $B$ é NP-completa e $B \in P$, então $P = NP$ (segue diretamente da definição de $\leq_p$: toda linguagem de $NP$ reduziria a $B$, e $B \in P$ propagaria essa solubilidade polinomial para toda $NP$).
- Se $B$ é NP-completa, $B \leq_p C$, e $C \in NP$, então $C$ também é NP-completa. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20250.png)

Essa segunda propriedade é o que torna a NP-completude "contagiosa": uma vez que se prova um primeiro problema NP-completo, basta reduzir qualquer outro problema de $NP$ *a partir dele* para provar que ele também é NP-completo.

#### O teorema de Cook-Levin

**Teorema (Cook-Levin).** SAT é NP-completo.

Isso significa que **qualquer** problema de $NP$ pode ser reduzido a SAT em tempo polinomial — e, em particular, $SAT \in P$ se e somente se $P = NP$. Foi este teorema que deu o pontapé inicial de toda a teoria de NP-completude.

*Ideia da prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20251.png)

*Prova.* A estratégia geral é mostrar que, para qualquer linguagem $A \in NP$ (decidida por uma MT não-determinística de tempo polinomial $N$), é possível construir, a partir da descrição de $N$ e de uma entrada $w$, uma fórmula booleana $\phi$ que é satisfazível se e somente se $N$ aceita $w$. A fórmula codifica a *tabela de computação* de $N$ sobre $w$ — uma grade onde cada linha representa uma configuração em um instante de tempo, e cada célula guarda o conteúdo da fita, a posição da cabeça e o estado naquele ponto, sendo as variáveis booleanas usadas para "marcar" qual símbolo/estado/posição ocorre em cada célula. As cláusulas da fórmula garantem que: cada célula tem exatamente um valor; a primeira linha é a configuração inicial; cada linha segue legitimamente da anterior conforme $\delta$; e alguma linha contém o estado de aceitação.

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20252.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20253.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20254.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20255.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20256.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20257.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20258.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20259.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20260.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20261.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20262.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20263.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20264.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20265.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20266.png)

**Corolário.** 3SAT também é NP-completo — restringir SAT a cláusulas de exatamente 3 literais não perde poder expressivo, pois qualquer cláusula com um número diferente de literais pode ser reescrita (com variáveis auxiliares) como um conjunto equivalente de cláusulas de 3 literais. ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20267.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20268.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20269.png)

### Problemas NP-completos adicionais

A estratégia geral para mostrar que uma linguagem é NP-completa é exibir uma redução de tempo polinomial **a partir de 3SAT** (ou de outro problema já conhecido como NP-completo). Ao construir essa redução, procura-se por estruturas — às vezes chamadas de **engrenagens** (*gadgets*) — capazes de simular variáveis e cláusulas de fórmulas booleanas dentro do problema de destino.

**CLIQUE é NP-completa.** Como já mostramos $3SAT \leq_p CLIQUE$, e 3SAT é NP-completa, CLIQUE também é (pela propriedade de propagação da NP-completude).

**COB-VERT (cobertura de vértices).** $COB\text{-}VERT = \{\langle G, k \rangle \mid G$ é um grafo não-direcionado com uma cobertura de vértices de $k$ nós$\}$ — um conjunto de $k$ nós que toca toda aresta do grafo.

**Teorema.** COB-VERT é NP-completa.

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20270.png) A redução parte de 3SAT, usando engrenagens que forçam, para cada variável, exatamente um de seus dois "nós" (literal verdadeiro/falso) a entrar na cobertura, e para cada cláusula, pelo menos um dos seus três nós de literal.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20271.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20272.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20273.png)

**CAMHAM é NP-completo.**

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20274.png) A redução, também a partir de 3SAT, constrói engrenagens elaboradas em forma de "diamante" para cada variável (permitindo percorrê-la em dois sentidos, representando verdadeiro/falso) e conectores para cada cláusula, de modo que um caminho hamiltoniano no grafo resultante corresponda a uma atribuição satisfatória.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20275.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20276.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20277.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20278.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20279.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20280.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20281.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20282.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20283.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20284.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20285.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20286.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20287.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20288.png)

**CAMHAMN é NP-completo** — a versão não-direcionada de CAMHAM (grafo não-direcionado com caminho hamiltoniano de $s$ a $t$), provada NP-completa por uma redução direta a partir de CAMHAM (substituindo cada nó do grafo direcionado por três nós encadeados no grafo não-direcionado, de forma a preservar a direcionalidade original).

![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20289.png)
![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20290.png)

**SOMA-SUBC é NP-completo.**

*Ideia.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20291.png) A redução parte de 3SAT (ou, alternativamente, de outro problema NP-completo numérico), codificando a satisfazibilidade da fórmula como uma equação de soma com dígitos cuidadosamente escolhidos, de modo que uma solução da instância de soma de subconjunto corresponda a uma atribuição satisfatória.

*Prova.* ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20292.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20293.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20294.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20295.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20296.png) ![image.png](../../assets/faculdade/periodo4/informatica-teorica/image%20297.png)

!!! tip "O quadro geral"
    Centenas de problemas práticos — escalonamento, roteamento, alocação de recursos, design de circuitos — já foram mostrados NP-completos. Na prática, isso significa que, para esses problemas, não se busca mais um algoritmo exato e eficiente para o caso geral, e sim heurísticas, aproximações, ou algoritmos exatos para casos especiais restritos.
