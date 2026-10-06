# AULA 1 — SISTEMAS ÚNICOS (SINGLE SYSTEMS)

Primeira lição da Unidade 1 do curso. O foco aqui é **um único sistema físico isolado** (um bit, um qubit) — nada de múltiplos sistemas, emaranhamento ou algoritmos ainda. A ideia é que entender como a informação quântica funciona para um sistema isolado é o passo natural antes de falar de múltiplos sistemas (próxima lição).

A estratégia do curso é começar pela **informação clássica**, não porque o objetivo seja explicar computação clássica, mas porque matematicamente a informação quântica é uma *extensão* da informação clássica, com diferenças pontuais e fundamentais. Entender bem a versão clássica (e a notação usada para descrevê-la) torna a versão quântica muito menos estranha.

## Duas descrições de informação quântica

Existem duas formas de descrever formalmente a informação quântica:

- **Descrição simplificada** (o assunto desta unidade): estados quânticos são representados por **vetores**, e operações são representadas por **matrizes unitárias**. É suficiente para entender a maioria dos algoritmos quânticos — não é uma simplificação "incompleta", é "a coisa de verdade", só que restrita a um caso mais simples. A limitação principal aparece quando se quer modelar **ruído** em sistemas quânticos reais.
- **Descrição geral** (coberta numa unidade posterior do curso): estados quânticos são representados por uma classe especial de matrizes chamadas **matrizes densas** (density matrices), permitindo uma classe mais geral de medições e operações, incluindo ruído. A descrição simplificada é um caso especial da geral — e a informação clássica (inclusive estados probabilísticos) também é um caso especial dela.

Este curso (e esta primeira unidade) trabalha com a descrição simplificada.

## Informação clássica

### Estados clássicos

Considere um sistema físico qualquer que armazena informação — vamos chamá-lo de $X$ (o nome é arbitrário). Assumimos que $X$ pode estar em um número **finito** de estados possíveis a cada momento. Um **estado clássico** é uma configuração do sistema que pode ser reconhecida e descrita sem ambiguidade, sem incerteza.

Chamamos de $\Sigma$ o conjunto desses estados clássicos possíveis — e $\Sigma$ é sempre um conjunto **finito e não vazio** (precisa ter pelo menos um estado, e pelo menos dois se o sistema for útil para guardar informação).

!!! example "Exemplos de conjuntos de estados clássicos"
    - Se $X$ é um bit: $\Sigma = \{0, 1\}$ (o "alfabeto binário").
    - Se $X$ é um dado de seis lados: $\Sigma = \{1, 2, 3, 4, 5, 6\}$.
    - Se $X$ é o interruptor de um ventilador: $\Sigma = \{\text{alto}, \text{médio}, \text{baixo}, \text{desligado}\}$.

### Estados probabilísticos

Em muitas situações há incerteza sobre o estado clássico atual de um sistema, de modo que cada estado possível tem uma probabilidade associada. Por exemplo, se $X$ é um bit, pode ser que

$$\Pr(X=0) = \tfrac{3}{4} \qquad \Pr(X=1) = \tfrac{1}{4}$$

Chamamos isso de **estado probabilístico** de $X$. A forma mais compacta de expressar um estado probabilístico é por um **vetor coluna**:

$$\begin{pmatrix} 3/4 \\ 1/4 \end{pmatrix}$$

onde a primeira entrada é a probabilidade do estado $0$ e a segunda, a probabilidade do estado $1$ — seguindo a ordem natural do alfabeto binário (zero primeiro, um depois).

Um vetor desse tipo é chamado **vetor de probabilidade**: todas as entradas são números reais não negativos, e a soma das entradas é igual a $1$.

### Notação de Dirac (parte 1): ket

Para descrever vetores e matrizes ao longo de todo o curso, usa-se a **notação de Dirac** — que não é específica de computação quântica, funciona igualmente bem para informação clássica (e qualquer outro contexto com vetores e matrizes).

Assuma que $\Sigma$ é um conjunto de estados clássicos com uma ordenação fixada (os elementos de $\Sigma$ em correspondência com os inteiros $1, \dots, |\Sigma|$). A ordem escolhida não importa muito — o que importa é escolher uma e **manter** essa escolha.

Denotamos por $|a\rangle$ ("ket $a$") o vetor coluna que tem um $1$ na entrada correspondente a $a \in \Sigma$ e $0$ em todas as outras.

!!! example "Alfabeto binário"
    $$|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \qquad |1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$$

!!! example "Naipes de um baralho"
    Para $\Sigma = \{\clubsuit, \diamondsuit, \heartsuit, \spadesuit\}$, escolhendo a ordem alfabética (em inglês: clubs, diamonds, hearts, spades):

    $$|\clubsuit\rangle = \begin{pmatrix}1\\0\\0\\0\end{pmatrix} \quad |\diamondsuit\rangle = \begin{pmatrix}0\\1\\0\\0\end{pmatrix} \quad |\heartsuit\rangle = \begin{pmatrix}0\\0\\1\\0\end{pmatrix} \quad |\spadesuit\rangle = \begin{pmatrix}0\\0\\0\\1\end{pmatrix}$$

Vetores dessa forma são chamados **vetores da base padrão** (*standard basis vectors*). Todo vetor pode ser expresso, de forma única, como combinação linear desses vetores — por exemplo, o vetor de probabilidade de antes:

$$\begin{pmatrix} 3/4 \\ 1/4 \end{pmatrix} = \tfrac{3}{4}|0\rangle + \tfrac{1}{4}|1\rangle$$

### Medindo estados probabilísticos

O que acontece quando medimos um sistema $X$ enquanto ele está em um estado probabilístico? Vemos um estado clássico, escolhido aleatoriamente de acordo com as probabilidades. Suponha que vemos o estado clássico $a \in \Sigma$ — a partir daí, não há mais incerteza: $\Pr(X=a) = 1$. Esse novo estado probabilístico (com probabilidade $1$ em $a$ e $0$ no resto) é exatamente o vetor $|a\rangle$.

!!! example "Exemplo"
    Com o bit do exemplo anterior, medir seleciona uma transição aleatória:

    $$\tfrac{3}{4}|0\rangle + \tfrac{1}{4}|1\rangle \;\longrightarrow\; \begin{cases} |0\rangle & \text{com probabilidade } 3/4 \\ |1\rangle & \text{com probabilidade } 1/4 \end{cases}$$

Pode-se pensar nisso como uma transição de conhecimento, não necessariamente física: o sistema já estava naquele estado, e só "descobrimos" qual era. De qualquer forma, o que importa aqui é como a matemática funciona — porque isso prepara o terreno para o caso quântico, que é matematicamente análogo (mas com uma interpretação bem menos trivial, como veremos adiante).

### Operações determinísticas

Toda função $f: \Sigma \to \Sigma$ descreve uma **operação determinística**, que transforma o estado $a$ em $f(a)$. O termo "determinístico" significa que o resultado depende inteiramente do estado anterior — não há aleatoriedade envolvida.

Para toda função $f$ desse tipo existe uma **única matriz** $M$ satisfazendo

$$M|a\rangle = |f(a)\rangle \quad \text{para todo } a \in \Sigma$$

Essa matriz sempre tem exatamente um $1$ em cada coluna (e $0$ nas demais entradas), definido por:

$$M(b,a) = \begin{cases} 1 & \text{se } b = f(a) \\ 0 & \text{caso contrário} \end{cases}$$

(convenção: linha $b$, coluna $a$). A ação da operação sobre um estado probabilístico é dada por multiplicação matriz-vetor: $v \mapsto Mv$.

!!! example "As quatro funções do alfabeto binário"
    Existem exatamente quatro funções $f: \{0,1\} \to \{0,1\}$:

    | | $f_1$ (constante 0) | $f_2$ (identidade) | $f_3$ (negação/bit flip) | $f_4$ (constante 1) |
    |---|---|---|---|---|
    | $f(0)$ | 0 | 0 | 1 | 1 |
    | $f(1)$ | 0 | 1 | 0 | 1 |

    E as matrizes correspondentes:

    $$M_1=\begin{pmatrix}1&1\\0&0\end{pmatrix} \quad M_2=\begin{pmatrix}1&0\\0&1\end{pmatrix} \quad M_3=\begin{pmatrix}0&1\\1&0\end{pmatrix} \quad M_4=\begin{pmatrix}0&0\\1&1\end{pmatrix}$$

    $f_3$ é a função **NOT** (negação lógica), também chamada de **bit flip**: inverte $0$ para $1$ e $1$ para $0$.

    ??? note "Como ler a matriz"
        Multiplicar uma matriz por um vetor da base padrão equivale a "jogar" o estado de entrada na coluna correspondente da matriz, e ler essa coluna como o vetor de probabilidade de saída. Por exemplo, $M_3|0\rangle$ dá a primeira coluna de $M_3$, que é $(0,1)$ — ou seja, $|1\rangle$. E $M_3|1\rangle$ dá a segunda coluna, $(1,0)$, ou seja, $|0\rangle$.

### Notação de Dirac (parte 2): bra

Com a mesma ordenação de $\Sigma$, denotamos por $\langle a|$ ("bra $a$") o **vetor linha** que tem um $1$ na entrada correspondente a $a$ e $0$ nas demais (é a transposta de $|a\rangle$, sem nenhuma outra mudança neste caso clássico).

!!! example "Alfabeto binário"
    $$\langle 0| = \begin{pmatrix}1 & 0\end{pmatrix} \qquad \langle 1| = \begin{pmatrix}0 & 1\end{pmatrix}$$

Multiplicar um vetor-linha por um vetor-coluna dá um **escalar** (matriz $1\times 1$):

$$\langle a|b\rangle = \langle a||b\rangle = \begin{cases} 1 & a=b \\ 0 & a\neq b \end{cases}$$

Esse produto — "bra" encontrando "ket" para formar um "bracket" — também é chamado de **produto interno**.

Multiplicar um vetor-coluna por um vetor-linha, na ordem inversa, dá uma **matriz**:

$$|a\rangle\langle b| \;=\; \text{matriz com um 1 na entrada } (a,b) \text{ e 0 no resto}$$

!!! example "Alfabeto binário"
    $$|0\rangle\langle 0| = \begin{pmatrix}1&0\\0&0\end{pmatrix} \qquad |0\rangle\langle 1| = \begin{pmatrix}0&1\\0&0\end{pmatrix} \qquad |1\rangle\langle 0| = \begin{pmatrix}0&0\\1&0\end{pmatrix} \qquad |1\rangle\langle 1| = \begin{pmatrix}0&0\\0&1\end{pmatrix}$$

Com as duas partes da notação de Dirac (bra e ket), fica fácil reescrever a matriz $M$ de uma operação determinística inteiramente nesses termos, sem nunca escrever a matriz explicitamente como "retângulo de números":

$$M = \sum_{b\in\Sigma} |f(b)\rangle\langle b|$$

??? note "Por que essa soma funciona"
    Aplicando $M$ a $|a\rangle$:

    $$M|a\rangle = \left(\sum_{b\in\Sigma}|f(b)\rangle\langle b|\right)|a\rangle = \sum_{b\in\Sigma}|f(b)\rangle\langle b|a\rangle$$

    Como $\langle b|a\rangle$ vale $1$ quando $b=a$ e $0$ caso contrário, só sobra o termo com $b=a$: o resultado é exatamente $|f(a)\rangle$, como queríamos.

### Operações probabilísticas

Operações probabilísticas são operações que **podem** introduzir aleatoriedade/incerteza (operações determinísticas são o caso particular em que isso não acontece).

!!! example "Exemplo"
    Uma operação em um bit: se o estado é $0$, nada acontece; se o estado é $1$, o bit é invertido para $0$ com probabilidade $1/2$. A matriz correspondente é

    $$\begin{pmatrix}1 & 1/2\\ 0 & 1/2\end{pmatrix} \;=\; \tfrac{1}{2}\begin{pmatrix}1&1\\0&0\end{pmatrix} + \tfrac{1}{2}\begin{pmatrix}1&0\\0&1\end{pmatrix}$$

    — ou seja, equivalente a jogar uma moeda honesta e, com 50% de chance, aplicar a função constante-zero, e com os outros 50%, aplicar a identidade.

Essas são chamadas **matrizes estocásticas**: todas as entradas são números reais não negativos, e as entradas de **cada coluna** somam $1$ (equivalentemente: cada coluna, isolada, é um vetor de probabilidade válido). Toda matriz estocástica pode ser pensada como uma "escolha aleatória" entre operações determinísticas — basta decompor as colunas como combinação convexa de vetores da base padrão.

### Composição de operações

Se $M_1, \dots, M_n$ são matrizes estocásticas representando operações sucessivas sobre um sistema $X$, aplicar a primeira e depois a segunda a um vetor $v$ dá $M_2(M_1 v) = (M_2 M_1)v$. Como multiplicação de matrizes é associativa, a composição das duas operações é representada pelo **produto de matrizes** $M_2 M_1$ — e, de forma geral, compor $M_1, \dots, M_n$ nessa ordem é representado por

$$M_n \cdots M_2 M_1$$

Note a **ordem invertida**: a primeira operação aplicada fica mais à direita no produto, a última fica mais à esquerda — porque é a matriz da direita que multiplica o vetor primeiro.

!!! warning "A ordem importa"
    Multiplicação de matrizes **não é comutativa**. Com $M_1$ = constante-zero e $M_2$ = NOT (bit flip):

    $$M_2 M_1 = \begin{pmatrix}0&0\\1&1\end{pmatrix} \qquad M_1 M_2 = \begin{pmatrix}1&1\\0&0\end{pmatrix}$$

    Fazer $M_1$ depois $M_2$ (zerar e depois inverter) dá a função constante-um; fazer $M_2$ depois $M_1$ (inverter e depois zerar) dá a função constante-zero. São operações diferentes — assim como acender um fósforo e depois soprar é diferente de soprar e depois acender.

As matrizes estocásticas são **fechadas sob multiplicação**: o produto de matrizes estocásticas é sempre uma matriz estocástica.

## Informação quântica

Matematicamente, informação quântica funciona de um jeito bem parecido com informação clássica — com algumas diferenças-chave. A primeira e mais fundamental é **como se define um estado**.

### Definindo um estado quântico

Um estado quântico de um sistema é representado por um **vetor coluna** cujos índices correspondem aos estados clássicos daquele sistema, com duas condições:

- as entradas são **números complexos** (em vez de reais não negativos, como no caso probabilístico);
- a soma dos **valores absolutos ao quadrado** das entradas deve ser igual a $1$ (em vez da soma simples ser $1$).

Os números complexos que aparecem num vetor de estado quântico são chamados de **amplitudes**. Elas desempenham um papel parecido com o de probabilidades, mas **não são** probabilidades e não têm a mesma interpretação direta.

!!! note "Por que definir assim?"
    Não existe uma justificativa a priori — essa é simplesmente a definição que a física descobriu ser a correta para modelar sistemas quânticos reais. Escolhe-se essa definição porque ela **funciona** (reproduz o que se observa experimentalmente), não por alguma necessidade lógica prévia. Boa parte do estudo de computação e informação quântica é, nesse sentido, uma exploração das consequências dessa única escolha de definição.

### Norma euclidiana

Para um vetor coluna $v$ com entradas complexas $\alpha_1,\dots,\alpha_n$, a **norma euclidiana** é definida como

$$\|v\| = \sqrt{\sum_{k=1}^{n} |\alpha_k|^2}$$

Um vetor de estado quântico é, portanto, um **vetor unitário** (norma $1$) com respeito a essa norma — e essa é uma definição equivalente à anterior (soma dos valores absolutos ao quadrado igual a $1$).

!!! note "Outras normas existem"
    A notação com barras duplas $\|\cdot\|$ não significa sempre norma euclidiana em todo contexto matemático — por exemplo, a soma simples dos valores absolutos (sem elevar ao quadrado nem tirar raiz) é outra norma, chamada **norma um** (*one-norm*). Neste curso, porém, sempre que aparecer essa notação aplicada a um vetor coluna, significa norma euclidiana.

### Exemplos de estados de qubit

**Qubit** é a abreviação de *quantum bit* — um bit que pode estar em um estado quântico, isto é, um sistema cujos estados clássicos são $\{0,1\}$.

!!! example "Estados da base padrão"
    $|0\rangle$ e $|1\rangle$ são estados quânticos válidos (entradas reais — logo também complexas — com soma dos quadrados igual a $1$).

!!! example "Estados mais e menos (plus/minus)"
    $$|+\rangle = \tfrac{1}{\sqrt2}|0\rangle + \tfrac{1}{\sqrt2}|1\rangle \qquad |-\rangle = \tfrac{1}{\sqrt2}|0\rangle - \tfrac{1}{\sqrt2}|1\rangle$$

    Em ambos os casos, $\left(\tfrac{1}{\sqrt2}\right)^2 + \left(\tfrac{1}{\sqrt2}\right)^2 = \tfrac12+\tfrac12 = 1$. O sinal de mais/menos dentro do ket não corresponde a nenhum estado clássico do sistema — é só um nome escolhido para o vetor, assim como qualquer outro símbolo poderia ser.

!!! example "Um estado sem nome especial"
    $$\tfrac{1+2i}{3}|0\rangle - \tfrac{2}{3}|1\rangle$$

    Os valores absolutos ao quadrado das entradas são $5/9$ e $4/9$, que somam $1$.

!!! example "Estado de um sistema com quatro estados clássicos (naipes)"
    $$\tfrac12|\clubsuit\rangle - \tfrac{i}{2}|\diamondsuit\rangle + 0\,|\heartsuit\rangle + \tfrac{1}{\sqrt2}|\spadesuit\rangle$$

    Os quadrados dos valores absolutos são $1/4$, $1/4$, $0$ e $1/2$ — soma $1$.

### Notação de Dirac (parte 3): vetores arbitrários

A notação de Dirac pode ser usada para **qualquer** vetor, não só vetores da base padrão correspondentes a estados clássicos — qualquer nome pode ir dentro de um ket. É comum usar a letra grega $\psi$ ("psi") para nomear um vetor arbitrário, como em $|\psi\rangle$.

A regra importante: se $|\psi\rangle$ é um vetor coluna, então $\langle\psi|$ é entendido como o **conjugado transposto** de $|\psi\rangle$, denotado $|\psi\rangle^\dagger$. Conjugado transposto significa duas operações (que comutam entre si, podem ser feitas em qualquer ordem): transpor o vetor (virar coluna em linha) e tomar o conjugado complexo de cada entrada.

!!! example "Exemplo"
    Para $|\psi\rangle = \dfrac{1+2i}{3}|0\rangle - \dfrac{2}{3}|1\rangle$:

    $$\langle\psi| = \dfrac{1-2i}{3}\langle 0| - \dfrac{2}{3}\langle 1|$$

    Note que o sinal da parte imaginária inverte ($1+2i \to 1-2i$) por causa do conjugado complexo — a parte real ($-2/3$) não muda porque já é um número real.

Essa regra é consistente com a notação para estados clássicos: lá, as entradas são só $0$s e $1$, então tomar o conjugado complexo não faz diferença nenhuma.

### Medindo estados quânticos

Medições fornecem o mecanismo para extrair informação **clássica** de sistemas **quânticos**: quando olhamos para um sistema em estado quântico, não vemos o estado quântico em si — vemos um estado clássico. Por ora, o curso trata apenas da versão mais simples de medição, chamada **medição na base padrão** (*standard basis measurement*); versões mais gerais (medições projetivas, e depois POVMs) aparecem em lições posteriores.

Numa medição na base padrão, os possíveis resultados são exatamente os estados clássicos do sistema. A probabilidade de cada estado clássico ser o resultado é o **valor absoluto ao quadrado** da entrada correspondente no vetor de estado quântico imediatamente antes da medição.

!!! example "Medindo o estado mais ($|+\rangle$)"
    $$\Pr(\text{resultado}=0) = \left|\tfrac{1}{\sqrt2}\right|^2 = \tfrac12 \qquad \Pr(\text{resultado}=1) = \left|\tfrac{1}{\sqrt2}\right|^2 = \tfrac12$$

    Um bit uniformemente aleatório.

!!! example "Medindo o estado menos ($|-\rangle$)"
    Mesma coisa: $1/2$ para cada resultado — o sinal de menos some ao tomar o valor absoluto.

!!! example "Medindo $\frac{1+2i}{3}|0\rangle - \frac23|1\rangle$"
    $$\Pr(\text{resultado}=0) = \left|\tfrac{1+2i}{3}\right|^2 = \tfrac59 \qquad \Pr(\text{resultado}=1) = \left|-\tfrac23\right|^2 = \tfrac49$$

!!! example "Medindo os estados da base padrão"
    Medir $|0\rangle$ dá o resultado $0$ com certeza; medir $|1\rangle$ dá o resultado $1$ com certeza (valor absoluto de $1$ ao quadrado é $1$) — consistente com associar esses vetores diretamente aos respectivos estados clássicos.

Assim como no caso probabilístico, medir um sistema **muda** seu estado: se o resultado obtido é o estado clássico $a$, o novo estado quântico do sistema passa a ser $|a\rangle$. Esse fenômeno é por vezes chamado de **colapso** do estado quântico — e é o tipo de coisa que tira o sono de quem estuda os fundamentos da mecânica quântica, mesmo sendo, do ponto de vista puramente matemático, bem análogo ao caso probabilístico. Uma consequência direta: medir o mesmo sistema uma segunda vez (sem nenhuma operação no meio) sempre dá o mesmo resultado da primeira — há um limite de quanta informação clássica pode ser extraída de um estado quântico.

### Operações unitárias

Assim como estados quânticos são diferentes de estados probabilísticos, o conjunto de operações permitidas também é diferente: operações sobre estados probabilísticos são matrizes **estocásticas**; operações sobre estados quânticos são matrizes **unitárias**.

Uma matriz quadrada $U$ com entradas complexas é **unitária** se satisfaz

$$U^\dagger U = \mathbb{1} = UU^\dagger$$

onde $U^\dagger$ é o conjugado transposto de $U$ e $\mathbb{1}$ é a matriz identidade. As duas igualdades são equivalentes entre si (ter uma implica a outra) e equivalem a dizer que $U$ é invertível com $U^{-1}=U^\dagger$ — o que só vale para matrizes quadradas.

Equivalentemente: $U$ é unitária se e somente se ela **nunca muda a norma euclidiana** de nenhum vetor — $\|Uv\| = \|v\|$ para todo vetor coluna complexo $v$. Como consequência direta: se $v$ é um estado quântico (norma $1$), então $Uv$ também é um estado quântico. De fato, as matrizes unitárias são **precisamente** as matrizes que sempre transformam estados quânticos em estados quânticos — o análogo exato do que as matrizes estocásticas são para vetores de probabilidade.

#### Operações de Pauli

As **operações de Pauli** correspondem às matrizes de Pauli:

$$\mathbb{1} = \begin{pmatrix}1&0\\0&1\end{pmatrix} \quad \sigma_x = \begin{pmatrix}0&1\\1&0\end{pmatrix} \quad \sigma_y = \begin{pmatrix}0&-i\\i&0\end{pmatrix} \quad \sigma_z = \begin{pmatrix}1&0\\0&-1\end{pmatrix}$$

Também chamadas simplesmente de $X$, $Y$ e $Z$ (cuidado: essas letras também são usadas para outras coisas em computação quântica, mas são nomes bem padronizados para essas matrizes específicas).

Todas são unitárias — e, nesse caso particular, todas são também **hermitianas** (iguais ao próprio conjugado transposto), então verificar que são unitárias é só elevar cada uma ao quadrado e checar que dá a identidade.

$\sigma_x$ é chamada de **bit flip** (ou operação NOT) — é a mesma operação NOT que já apareceu no contexto clássico:

$$\sigma_x|0\rangle = |1\rangle \qquad \sigma_x|1\rangle = |0\rangle$$

$\sigma_z$ é chamada de **phase flip** (inversão de fase):

$$\sigma_z|0\rangle = |0\rangle \qquad \sigma_z|1\rangle = -|1\rangle$$

(o significado mais profundo de "inverter a fase" — por que colocar um sinal de menos na frente de $|1\rangle$ e não de $|0\rangle$ é chamado assim — fica mais claro em lições futuras.)

#### Operação de Hadamard

A **operação de Hadamard**, quase sempre chamada apenas de $H$:

$$H = \begin{pmatrix} \tfrac{1}{\sqrt2} & \tfrac{1}{\sqrt2} \\ \tfrac{1}{\sqrt2} & -\tfrac{1}{\sqrt2} \end{pmatrix}$$

$H$ também é sua própria conjugada transposta, então verificar que é unitária é só multiplicá-la por si mesma e checar que dá a identidade:

$$H^\dagger H = H H = \begin{pmatrix}\tfrac12+\tfrac12 & \tfrac12-\tfrac12\\ \tfrac12-\tfrac12 & \tfrac12+\tfrac12\end{pmatrix} = \begin{pmatrix}1&0\\0&1\end{pmatrix}$$

#### Operações de fase

Uma **operação de fase** é qualquer matriz da forma

$$P_\theta = \begin{pmatrix}1 & 0 \\ 0 & e^{i\theta}\end{pmatrix}$$

para qualquer número real $\theta$ — a entrada $e^{i\theta}$ está sempre sobre o círculo unitário, então matrizes desse formato são sempre unitárias (a transposição não faz nada a essa matriz; o conjugado complexo troca $e^{i\theta}$ por $e^{-i\theta}$, e o produto dá $e^{i\theta}e^{-i\theta}=1$). Quando $\theta \in \{0,\pi\}$, essa operação coincide com a identidade ou com $\sigma_z$, respectivamente.

Dois casos particulares, muito usados, têm nome próprio:

$$S = P_{\pi/2} = \begin{pmatrix}1&0\\0&i\end{pmatrix} \qquad T = P_{\pi/4} = \begin{pmatrix}1&0\\0&\tfrac{1+i}{\sqrt2}\end{pmatrix}$$

$S$ e $T$ são chamadas de **portas** (*gates*) $S$ e $T$ quando se fala em circuitos — assunto de uma lição futura.

#### Exemplos de ação dessas operações

!!! example "Hadamard em $|0\rangle$, $|1\rangle$, $|+\rangle$, $|-\rangle$"
    $$H|0\rangle = |+\rangle \qquad H|1\rangle = |-\rangle \qquad H|+\rangle = |0\rangle \qquad H|-\rangle = |1\rangle$$

    Ou seja: $H$ alterna entre o estado zero e o estado mais, e entre o estado um e o estado menos. Isso também dá um jeito simples de **distinguir** $|+\rangle$ de $|-\rangle$: medir qualquer um dos dois diretamente na base padrão dá um bit uniformemente aleatório nos dois casos (não ajuda a diferenciá-los) — mas aplicar $H$ e **depois** medir dá $0$ com certeza se o estado original era $|+\rangle$, e $1$ com certeza se era $|-\rangle$.

!!! example "Hadamard no estado sem nome especial"
    $$H\left(\tfrac{1+2i}{3}|0\rangle - \tfrac23|1\rangle\right) = \tfrac{-1+2i}{3\sqrt2}|0\rangle + \tfrac{3+2i}{3\sqrt2}|1\rangle$$

    ??? note "Passo a passo"
        Na forma de vetor coluna:

        $$H\begin{pmatrix}\frac{1+2i}{3}\\[2pt]-\frac23\end{pmatrix} = \begin{pmatrix}\frac{1}{\sqrt2} & \frac{1}{\sqrt2}\\[2pt]\frac{1}{\sqrt2} & -\frac{1}{\sqrt2}\end{pmatrix}\begin{pmatrix}\frac{1+2i}{3}\\[2pt]-\frac23\end{pmatrix} = \begin{pmatrix}\frac{-1+2i}{3\sqrt2}\\[4pt]\frac{3+2i}{3\sqrt2}\end{pmatrix}$$

        É simplesmente multiplicação matriz-vetor padrão, com os números complexos somados/subtraídos entrada por entrada.

!!! example "Operação T em $|+\rangle$, usando a notação de Dirac direto (sem converter para matriz)"
    $T|0\rangle=|0\rangle$ e $T|1\rangle=\dfrac{1+i}{\sqrt2}|1\rangle$ (ação da matriz $T$ sobre a base padrão). Expandindo $|+\rangle$ e usando linearidade:

    $$T|+\rangle = T\left(\tfrac{1}{\sqrt2}|0\rangle+\tfrac{1}{\sqrt2}|1\rangle\right) = \tfrac{1}{\sqrt2}T|0\rangle + \tfrac{1}{\sqrt2}T|1\rangle = \tfrac{1}{\sqrt2}|0\rangle + \tfrac{1+i}{2}|1\rangle$$

    E se depois quisermos aplicar Hadamard ao resultado, repetimos o mesmo truque — expandir, usar linearidade, substituir a ação de $H$ sobre $|0\rangle$ e $|1\rangle$ (que já conhecemos: $|+\rangle$ e $|-\rangle$), e por fim simplificar:

    $$HT|+\rangle = \tfrac{1}{\sqrt2}H|0\rangle + \tfrac{1+i}{2}H|1\rangle = \tfrac{1}{\sqrt2}|+\rangle + \tfrac{1+i}{2}|-\rangle = \left(\tfrac12+\tfrac{1+i}{2\sqrt2}\right)|0\rangle + \left(\tfrac12-\tfrac{1+i}{2\sqrt2}\right)|1\rangle$$

    Essa é uma forma alternativa (e equivalente) de calcular a ação de uma operação, sem nunca escrever a matriz explicitamente como "retângulo de números" — útil quando é mais conveniente trabalhar direto na notação de Dirac.

#### Composição de operações unitárias

Assim como no caso probabilístico, compor operações unitárias é representado por **multiplicação de matrizes** (na mesma ordem invertida: a primeira operação aplicada fica à direita no produto). As matrizes unitárias também são **fechadas sob multiplicação** — compor operações unitárias sempre dá outra operação unitária.

!!! example "A operação 'raiz quadrada de NOT'"
    Aplicar Hadamard, depois $S$, depois Hadamard de novo:

    $$HSH = \begin{pmatrix}\tfrac{1}{\sqrt2}&\tfrac{1}{\sqrt2}\\\tfrac{1}{\sqrt2}&-\tfrac{1}{\sqrt2}\end{pmatrix}\begin{pmatrix}1&0\\0&i\end{pmatrix}\begin{pmatrix}\tfrac{1}{\sqrt2}&\tfrac{1}{\sqrt2}\\\tfrac{1}{\sqrt2}&-\tfrac{1}{\sqrt2}\end{pmatrix} = \begin{pmatrix}\tfrac{1+i}{2} & \tfrac{1-i}{2}\\[2pt]\tfrac{1-i}{2} & \tfrac{1+i}{2}\end{pmatrix}$$

    Por que esse nome? Porque aplicar essa operação **duas vezes** (elevar a matriz ao quadrado) dá exatamente a operação NOT ($\sigma_x$):

    $$(HSH)^2 = \begin{pmatrix}0&1\\1&0\end{pmatrix} = \sigma_x$$

    Isso é peculiar — não existe nenhuma operação **clássica** (representada por matriz estocástica) tal que aplicá-la duas vezes dê um NOT. É um primeiro sinal concreto de que operações quânticas permitem coisas que operações clássicas simplesmente não conseguem replicar.

---

## Anotações e observações pessoais

!!! warning "Conteúdo não-oficial"
    Esta seção reúne minhas próprias anotações, dúvidas e observações feitas durante/depois da aula — não é conteúdo do curso, e pode conter entendimentos equivocados ou opiniões pessoais. Tratar como complementar, não como referência.

- A analogia clássico → quântico ficou bem clara estruturalmente (vetor de probabilidade → vetor de estado quântico; matriz estocástica → matriz unitária; "ver um estado ao medir" em ambos os casos), mas a pergunta que ficou em aberto é sempre a mesma: **por que** a definição de estado quântico é "essa" especificamente (números complexos, soma dos módulos ao quadrado igual a 1)? A aula é explícita que não há uma razão a priori — só "é assim que a física funciona e essa definição é a que reproduz os experimentos" — mas queria entender melhor esse ponto no futuro (talvez fique mais claro nas lições sobre medição geral/POVM ou na unidade de descrição geral).
- Queria revisar com mais calma, passo a passo, a parte de **transposição + conjugado complexo** (notação de Dirac parte 3) — entendi o mecanismo (transpor + conjugar cada entrada), mas quero me sentir mais confortável fazendo isso "no automático" para vetores com números complexos mais complicados.
- Idem para os exemplos de **medição de estados quânticos**: entendi a regra (prob. = módulo ao quadrado da amplitude), mas quero revisar o passo a passo de cada exemplo (principalmente os com números complexos) até estar 100% automático.
- Fiquei na dúvida se "operações unitárias" se refere sempre a **matrizes quadradas** — a aula confirma isso (a própria definição de unitária, com $U^\dagger U = UU^\dagger = \mathbb{1}$, só faz sentido/é bem definida para matrizes quadradas).
- Queria entender melhor a **origem/motivação** das matrizes de Pauli, Hadamard e de fase — de onde "vieram" essas matrizes específicas, não só que elas são unitárias. Acho que isso deve aparecer melhor com mais contexto físico (spin, interferômetros, etc.) em lições futuras, ou lendo um pouco mais no Qiskit Textbook em paralelo.
- Achei a notação de "estados sem nome" (ex.: $\tfrac{1+2i}{3}|0\rangle-\tfrac23|1\rangle$) meio contraintuitiva no começo — ainda bom revisitar por que faz sentido usar números complexos "genéricos" assim, e não só casos com significado físico claro (base padrão, plus/minus).
- Quero voltar e reorganizar mentalmente os exemplos de "qubit unitary operations" e "composing unitary operations" de forma mais estratificada/visual — a aula passa eles em sequência meio corrida, achei que ajudaria ter cada operação (Pauli, Hadamard, fase) com seu próprio bloco bem isolado antes de ir para composição (o que tentei refletir na organização desta página, usando os dropdowns para os passos de cálculo).
