# NÚMEROS COMPLEXOS

## Introdução

Os números complexos surgem de um problema simples: a equação $x^2+1=0$ não tem solução dentro dos números reais, porque nenhum real ao quadrado dá $-1$. Em vez de descartar esse tipo de equação, definimos um novo número, $i$, que resolve exatamente esse problema, e construímos um sistema numérico inteiro em torno dele — os números complexos — que contém os reais como caso particular e permite resolver qualquer equação polinomial.

!!! note "Um pouco de história"
    O nome "imaginário" é um acidente histórico, não uma descrição precisa. Raízes quadradas de negativos apareciam já no século XVI, nas fórmulas de Cardano/Tartaglia para resolver equações cúbicas — curiosamente, mesmo quando a equação tinha três raízes **reais**, a fórmula passava por um passo intermediário com $\sqrt{-1}$. Bombelli (1572) foi o primeiro a manipular essas quantidades com regras consistentes, mas só com Euler (que introduziu a notação $i$) e, depois, com a interpretação geométrica de Wessel, Argand e Gauss (fim do séc. XVIII/início do XIX) como pontos de um plano, os complexos deixaram de ser vistos como um truque de cálculo e passaram a ser um sistema numérico tão legítimo quanto os reais.

## A unidade imaginária

Define-se a **unidade imaginária** $i$ como uma raiz quadrada de $-1$:

$$i^2 = -1 \qquad \text{ou, equivalentemente,} \qquad i = \sqrt{-1}$$

### Potências de $i$

A partir disso, as potências de $i$ entram num ciclo de período 4:

$$i^0=1,\quad i^1=i,\quad i^2=-1,\quad i^3=-i,\quad i^4=1,\quad i^5=i,\ \dots$$

!!! tip "Calculando $i^n$ rapidamente"
    Para qualquer expoente $n$, divida $n$ por $4$ e olhe só o resto $r$: $i^n = i^r$. Exemplo: $i^{37}$, como $37 = 4\cdot9+1$, então $i^{37}=i^1=i$.

## Forma algébrica (ou retangular)

Um **número complexo** $z$ é escrito como:

$$z = a + bi, \qquad a,b \in \mathbb{R}$$

- $a = \text{Re}(z)$ é a **parte real**.
- $b = \text{Im}(z)$ é a **parte imaginária** (note que $b$ é um número real — "parte imaginária" é o coeficiente que multiplica $i$, não $bi$ em si).

O conjunto de todos os números complexos é denotado $\mathbb{C}$. Quando $b=0$, $z=a$ é só um número real — ou seja, $\mathbb{R}\subset\mathbb{C}$. Quando $a=0$ e $b\neq0$, $z=bi$ é chamado **imaginário puro**.

!!! example "Exemplos"
    $z_1 = 3+2i$ tem $\text{Re}(z_1)=3$ e $\text{Im}(z_1)=2$.

    $z_2 = -5i$ é imaginário puro, com $\text{Re}(z_2)=0$ e $\text{Im}(z_2)=-5$.

    $z_3 = 7$ é um real "disfarçado" de complexo, com $\text{Im}(z_3)=0$.

### Classificação

Todo $z=a+bi$ se encaixa em exatamente uma destas categorias:

| Condição | Classificação |
| --- | --- |
| $b=0$ | **número real** ($z=a$) |
| $a=0$ e $b\neq0$ | **imaginário puro** ($z=bi$) |
| $a\neq0$ e $b\neq0$ | **complexo não-real** (as duas partes contam) |
| $a=0$ e $b=0$ | **complexo nulo** ($z=0$) |

### Igualdade

Dois complexos são iguais se e somente se têm a mesma parte real **e** a mesma parte imaginária:

$$a+bi = c+di \iff a=c \text{ e } b=d$$

Isso é o que permite "separar em parte real e imaginária" ao resolver equações com complexos — cada lado tem que bater componente a componente.

## Operações básicas

Com $z_1 = a+bi$ e $z_2=c+di$:

**Soma e subtração** — some/subtraia parte real com parte real, imaginária com imaginária:

$$z_1 \pm z_2 = (a\pm c) + (b\pm d)i$$

**Multiplicação** — distribui normalmente, usando $i^2=-1$:

$$z_1 \cdot z_2 = (a+bi)(c+di) = ac + adi + bci + bdi^2 = (ac-bd) + (ad+bc)i$$

!!! example "Exemplo"
    $(2+3i)(1-4i) = 2\cdot1 + 2\cdot(-4i) + 3i\cdot1 + 3i\cdot(-4i) = 2 - 8i + 3i -12i^2 = 2-5i+12 = 14-5i$

**Divisão** — multiplica-se numerador e denominador pelo **conjugado** do denominador (ver próxima seção), pra eliminar $i$ do denominador:

$$\frac{z_1}{z_2} = \frac{a+bi}{c+di} = \frac{(a+bi)(c-di)}{(c+di)(c-di)} = \frac{(ac+bd)+(bc-ad)i}{c^2+d^2}$$

!!! example "Exemplo"
    $\dfrac{1+2i}{3-i} = \dfrac{(1+2i)(3+i)}{(3-i)(3+i)} = \dfrac{3+i+6i+2i^2}{9+1} = \dfrac{1+7i}{10} = \dfrac{1}{10}+\dfrac{7}{10}i$

## Conjugado

O **conjugado** de $z=a+bi$ é $\bar z = a-bi$ (mesma parte real, parte imaginária com o sinal trocado). Geometricamente, é o reflexo de $z$ em torno do eixo real.

Propriedades úteis:

$$z \cdot \bar z = a^2+b^2 \in \mathbb{R} \qquad\qquad z+\bar z = 2a = 2\,\text{Re}(z) \qquad\qquad z-\bar z = 2bi$$

A primeira propriedade — o produto de $z$ pelo conjugado ser sempre real e não-negativo — é exatamente o que torna possível "racionalizar" denominadores complexos na divisão acima, e é a base da definição de módulo a seguir.

## Módulo

O **módulo** (ou valor absoluto) de $z=a+bi$ mede sua distância até a origem no plano complexo:

$$|z| = \sqrt{a^2+b^2} = \sqrt{z\cdot\bar z}$$

Propriedades:

$$|z_1 z_2| = |z_1||z_2| \qquad\qquad \left|\frac{z_1}{z_2}\right| = \frac{|z_1|}{|z_2|} \qquad\qquad |z_1+z_2| \le |z_1|+|z_2| \text{ (desigualdade triangular)}$$

## Plano complexo (plano de Argand-Gauss)

Como $z=a+bi$ é determinado por dois números reais, ele pode ser representado como um ponto $(a,b)$ (ou um vetor da origem até esse ponto) num plano cartesiano: o eixo horizontal é o **eixo real** e o vertical é o **eixo imaginário**.

- $\text{Re}(z)$ = coordenada $x$
- $\text{Im}(z)$ = coordenada $y$
- $|z|$ = comprimento do vetor (distância até a origem)
- $\bar z$ = reflexo de $z$ no eixo real
- $-z$ = reflexo de $z$ na origem (rotação de $180°$)

Essa representação geométrica é o que faz os números complexos serem especialmente úteis: soma de complexos é soma vetorial, e — como veremos a seguir — multiplicação tem uma interpretação geométrica igualmente limpa em termos de rotação e escala.

## Argumento

O **argumento** de $z=a+bi$ (não-nulo), denotado $\arg(z)$ ou $\theta$, é o ângulo que o vetor $z$ faz com o semieixo real positivo, medido no sentido anti-horário:

$$\theta = \arg(z) = \arctan\!\left(\frac{b}{a}\right) \;\; \text{(ajustando o quadrante)}$$

!!! warning "Cuidado com o quadrante"
    $\arctan(b/a)$ sozinho só dá o ângulo certo diretamente para $z$ no primeiro ou quarto quadrante ($a>0$). Para $a<0$, some $180°$ ($\pi$ rad) ao resultado; para $a=0$, o ângulo é $90°$ ou $270°$ dependendo do sinal de $b$. Na prática, é mais seguro desenhar o ponto $(a,b)$ e raciocinar geometricamente, ou usar a função `atan2(b,a)` de uma calculadora/linguagem de programação, que já trata os quadrantes automaticamente.

O argumento não é único — $\theta$ e $\theta+360°k$ (para qualquer inteiro $k$) representam o mesmo ponto, já que somar uma volta completa não muda a direção. O valor de $\theta$ no intervalo $(-180°,180°]$ (ou $(-\pi,\pi]$) é chamado **argumento principal**, e é o que normalmente se usa como "o" argumento de $z$ quando não se especifica outra coisa.

## Forma polar (trigonométrica)

Em vez de descrever $z$ pelas coordenadas $(a,b)$, pode-se descrevê-lo pelo módulo $r=|z|$ e pelo argumento $\theta=\arg(z)$ definidos acima:

$$a = r\cos\theta \qquad b = r\sin\theta \qquad \Longrightarrow \qquad z = r(\cos\theta+i\sin\theta)$$

!!! example "Convertendo para forma polar"
    $z = 1+i\sqrt3$: $r = \sqrt{1^2+(\sqrt3)^2} = \sqrt{4} = 2$. Como $a=1>0$, $\theta=\arctan(\sqrt3/1) = 60° = \pi/3$.

    Logo, $z = 2(\cos 60° + i\sin 60°)$.

### Multiplicação e divisão em forma polar

A forma polar é o que torna multiplicação/divisão de complexos geometricamente intuitivas: **módulos se multiplicam/dividem, argumentos se somam/subtraem**.

$$z_1 z_2 = r_1 r_2\big(\cos(\theta_1+\theta_2) + i\sin(\theta_1+\theta_2)\big) \qquad\qquad \frac{z_1}{z_2} = \frac{r_1}{r_2}\big(\cos(\theta_1-\theta_2)+i\sin(\theta_1-\theta_2)\big)$$

Ou seja: multiplicar por $z_2$ é "esticar" por um fator $r_2$ e "girar" por um ângulo $\theta_2$. Esse é o motivo pelo qual multiplicar por $i$ (que tem $r=1,\ \theta=90°$) corresponde a girar $90°$ no plano complexo.

## Forma exponencial e fórmula de Euler

A **fórmula de Euler** conecta a exponencial complexa com seno e cosseno:

$$e^{i\theta} = \cos\theta + i\sin\theta$$

Combinando com a forma polar, qualquer complexo pode ser escrito na **forma exponencial**:

$$z = re^{i\theta}$$

Essa forma deixa multiplicação/divisão/potenciação ainda mais diretas, já que viram só álgebra de expoentes:

$$z_1 z_2 = r_1 r_2\, e^{i(\theta_1+\theta_2)} \qquad\qquad \frac{z_1}{z_2} = \frac{r_1}{r_2}\,e^{i(\theta_1-\theta_2)}$$

!!! note "Identidade de Euler"
    Um caso particular famoso: fazendo $\theta=\pi$ na fórmula de Euler, $e^{i\pi} = \cos\pi+i\sin\pi = -1+0i$, ou seja:

    $$e^{i\pi}+1=0$$

    Essa equação é frequentemente citada como uma das mais bonitas da matemática por juntar cinco constantes fundamentais ($e$, $i$, $\pi$, $1$, $0$) e as três operações básicas (soma, multiplicação, potenciação) numa única igualdade.

## Potenciação: 1ª Fórmula de De Moivre

Elevar um complexo em forma polar/exponencial a uma potência inteira $n$ é direto:

$$z^n = r^n\big(\cos(n\theta)+i\sin(n\theta)\big) = r^n e^{in\theta}$$

Essa é a **fórmula de De Moivre**: eleva o módulo à $n$-ésima potência e multiplica o argumento por $n$.

!!! example "Exemplo"
    Calcular $(1+i)^{10}$. Primeiro em forma polar: $r=\sqrt2$, $\theta=45°$. Então:

    $$(1+i)^{10} = (\sqrt2)^{10}\big(\cos(450°)+i\sin(450°)\big) = 32\big(\cos(90°)+i\sin(90°)\big) = 32(0+1i) = 32i$$

    (usei $450° = 360°+90°$, que dá o mesmo ponto que $90°$.)

## Radiciação: 2ª Fórmula de De Moivre (raízes $n$-ésimas)

Diferente dos reais, todo número complexo não-nulo tem exatamente $n$ raízes $n$-ésimas distintas. Se $z=r(\cos\theta+i\sin\theta)$, suas $n$ raízes $n$-ésimas são:

$$w_k = \sqrt[n]{r}\left(\cos\frac{\theta+360°k}{n} + i\sin\frac{\theta+360°k}{n}\right), \qquad k=0,1,2,\dots,n-1$$

Geometricamente, essas $n$ raízes estão todas sobre um círculo de raio $\sqrt[n]{r}$, igualmente espaçadas por um ângulo de $360°/n$ entre si — formam os vértices de um polígono regular de $n$ lados.

!!! example "Raízes cúbicas de $8$"
    $z=8=8(\cos0°+i\sin0°)$, $r=8$, $\theta=0°$, $n=3$. $\sqrt[3]{8}=2$.

    $$w_0 = 2(\cos0°+i\sin0°) = 2$$
    $$w_1 = 2(\cos120°+i\sin120°) = 2\left(-\tfrac12+i\tfrac{\sqrt3}{2}\right) = -1+i\sqrt3$$
    $$w_2 = 2(\cos240°+i\sin240°) = 2\left(-\tfrac12-i\tfrac{\sqrt3}{2}\right) = -1-i\sqrt3$$

    Só $w_0=2$ é uma raiz "real" — as outras duas são genuinamente complexas, mas todas as três, elevadas ao cubo, dão $8$. Note que formam um triângulo equilátero no plano complexo.

## Por que isso importa: Teorema Fundamental da Álgebra

O motivo histórico/estrutural pelo qual os complexos são tão importantes: o **Teorema Fundamental da Álgebra** garante que todo polinômio de grau $n \ge 1$ com coeficientes complexos (em particular, reais) tem exatamente $n$ raízes em $\mathbb{C}$, contando multiplicidade. Nos reais isso é falso ($x^2+1$ não tem raiz real), mas nos complexos é sempre verdade — é nesse sentido que $\mathbb{C}$ "completa" os reais algebricamente.

Uma consequência prática: polinômios reais com raízes complexas sempre têm essas raízes em **pares conjugados**. Se $z=a+bi$ é raiz de um polinômio com coeficientes reais, $\bar z = a-bi$ também é.

!!! example "Exemplo"
    $x^2-2x+5=0$: usando Bhaskara, $x = \dfrac{2\pm\sqrt{4-20}}{2} = \dfrac{2\pm\sqrt{-16}}{2} = \dfrac{2\pm4i}{2} = 1\pm2i$.

    As duas raízes, $1+2i$ e $1-2i$, são conjugadas uma da outra — como esperado, já que os coeficientes do polinômio são reais.

## Aplicações

Números complexos não são só um exercício abstrato — aparecem em vários lugares por causa exatamente da propriedade de "rotação + escala" vista na forma polar:

- **Engenharia elétrica**: em circuitos de corrente alternada, resistências, capacitores e indutores são combinados usando uma grandeza complexa chamada **impedância** ($Z=R+jX$, onde engenheiros costumam usar $j$ no lugar de $i$ para não confundir com corrente). Isso transforma equações diferenciais de circuitos em álgebra complexa simples.
- **Processamento de sinais**: a Transformada de Fourier, usada para decompor um sinal (áudio, imagem, etc.) em frequências, é definida inteiramente em termos de $e^{i\theta}$ — a forma exponencial é o que faz essa decomposição funcionar de forma compacta.
- **Computação gráfica e rotações 2D**: como visto na seção de forma polar, multiplicar por $e^{i\theta}$ gira um ponto do plano por $\theta$ — uma forma elegante de representar rotações 2D, análoga ao papel que os quaternions têm para rotações 3D.
- **Fractais**: o conjunto de Mandelbrot é definido por uma iteração puramente em $\mathbb{C}$: $z_{n+1}=z_n^2+c$, testando para quais valores de $c\in\mathbb{C}$ essa sequência permanece limitada.
- **Mecânica quântica**: a função de onda que descreve o estado de um sistema quântico é, por definição, uma função de valores complexos — não é só uma conveniência de cálculo, é parte da própria formulação da teoria.

## Exercícios Resolvidos

### Potências de $i$

!!! example "Exercício 1"
    Calcule $i^{58}$.

    **Solução.** $58 = 4\cdot14+2$, resto $2$. Logo $i^{58}=i^2=-1$.

!!! example "Exercício 2"
    Calcule $i^{15}+i^{20}$.

    **Solução.** $15=4\cdot3+3 \Rightarrow i^{15}=i^3=-i$. $20=4\cdot5+0 \Rightarrow i^{20}=i^0=1$. Soma: $-i+1=1-i$.

### Forma algébrica, classificação e igualdade

!!! example "Exercício 3"
    Classifique $z_1=4-7i$, $z_2=9i$, $z_3=\sqrt2$ e $z_4=0$ quanto ao tipo (real, imaginário puro, complexo não-real ou nulo).

    **Solução.** $z_1$: $a=4\neq0,\ b=-7\neq0$ → complexo não-real. $z_2$: $a=0,\ b=9\neq0$ → imaginário puro. $z_3$: $b=0$ → real. $z_4$: $a=b=0$ → complexo nulo.

!!! example "Exercício 4"
    Determine $x$ e $y$ reais tais que $(2x-1)+3i = 5+(y+1)i$.

    **Solução.** Pela igualdade de complexos, parte real com parte real e imaginária com imaginária: $2x-1=5 \Rightarrow x=3$; e $3=y+1 \Rightarrow y=2$.

### Operações na forma algébrica

!!! example "Exercício 5"
    Calcule $(5-2i)+(3+6i)-(1-i)$.

    **Solução.** Separando partes reais e imaginárias: $(5+3-1)+(-2+6+1)i = 7+5i$.

!!! example "Exercício 6"
    Calcule $(3-2i)(4+5i)$.

    **Solução.** $3\cdot4 + 3\cdot5i -2i\cdot4 -2i\cdot5i = 12+15i-8i-10i^2 = 12+7i+10 = 22+7i$.

### Divisão na forma algébrica

!!! example "Exercício 7"
    Calcule $\dfrac{5+i}{2-3i}$.

    **Solução.** Multiplica numerador e denominador pelo conjugado do denominador, $2+3i$:

    $$\frac{(5+i)(2+3i)}{(2-3i)(2+3i)} = \frac{10+15i+2i+3i^2}{4+9} = \frac{7+17i}{13} = \frac{7}{13}+\frac{17}{13}i$$

!!! example "Exercício 8"
    Simplifique $\dfrac{1}{i}$.

    **Solução.** Multiplica por $\dfrac{-i}{-i}$ (ou pelo conjugado de $i$, que é $-i$): $\dfrac{1}{i}\cdot\dfrac{-i}{-i} = \dfrac{-i}{-i^2} = \dfrac{-i}{1} = -i$.

### Interpretação geométrica e módulo

!!! example "Exercício 9"
    Calcule o módulo de $z=-6+8i$ e localize-o no plano complexo (indique o quadrante).

    **Solução.** $|z|=\sqrt{(-6)^2+8^2}=\sqrt{36+64}=\sqrt{100}=10$. Como $a=-6<0$ e $b=8>0$, $z$ está no 2º quadrante.

!!! example "Exercício 10"
    Sabendo que $|z|=5$, que curva no plano complexo é formada por todos os $z$ que satisfazem essa condição?

    **Solução.** $|z|=5$ significa que a distância de $z$ até a origem é sempre $5$ — ou seja, é a equação de uma **circunferência de raio $5$ centrada na origem**.

### Argumento

!!! example "Exercício 11"
    Determine o argumento principal de $z=-1-i$.

    **Solução.** $a=-1,\ b=-1$, ambos negativos → 3º quadrante. $\arctan(b/a)=\arctan(1)=45°$, mas como estamos no 3º quadrante, somamos $180°$: $\theta=45°+180°=225°$. Como argumento principal fica em $(-180°,180°]$, equivalentemente $\theta=225°-360°=-135°$.

### Forma polar

!!! example "Exercício 12"
    Escreva $z=-4$ na forma polar.

    **Solução.** $r=|-4|=4$. Como $z$ está sobre o eixo real negativo, $\theta=180°$. Logo $z=4(\cos180°+i\sin180°)$.

!!! example "Exercício 13"
    Converta $z=3(\cos210°+i\sin210°)$ de volta para a forma algébrica.

    **Solução.** $\cos210°=-\frac{\sqrt3}{2}$, $\sin210°=-\frac12$. $z = 3\left(-\frac{\sqrt3}{2}-\frac12 i\right) = -\frac{3\sqrt3}{2}-\frac32 i$.

### Multiplicação e divisão na forma polar

!!! example "Exercício 14"
    Com $z_1=2(\cos40°+i\sin40°)$ e $z_2=5(\cos20°+i\sin20°)$, calcule $z_1z_2$ e $z_1/z_2$.

    **Solução.** Multiplicação: módulos multiplicam, argumentos somam: $z_1z_2=2\cdot5\big(\cos(40°+20°)+i\sin(40°+20°)\big)=10(\cos60°+i\sin60°)$.

    Divisão: módulos dividem, argumentos subtraem: $z_1/z_2=\frac{2}{5}\big(\cos(40°-20°)+i\sin(40°-20°)\big)=0{,}4(\cos20°+i\sin20°)$.

### 1ª Fórmula de De Moivre (potenciação)

!!! example "Exercício 15"
    Calcule $\left(\sqrt3+i\right)^6$.

    **Solução.** Forma polar: $r=\sqrt{3+1}=2$, $\theta=\arctan(1/\sqrt3)=30°$. Pela 1ª fórmula de De Moivre:

    $$z^6 = 2^6\big(\cos(6\cdot30°)+i\sin(6\cdot30°)\big) = 64(\cos180°+i\sin180°) = 64(-1+0i) = -64$$

### 2ª Fórmula de De Moivre (radiciação)

!!! example "Exercício 16"
    Determine as raízes quartas de $z=16$.

    **Solução.** $z=16(\cos0°+i\sin0°)$, $r=16$, $n=4$. $\sqrt[4]{16}=2$.

    $$w_k = 2\left(\cos\frac{0°+360°k}{4}+i\sin\frac{0°+360°k}{4}\right),\quad k=0,1,2,3$$

    $$w_0=2(\cos0°+i\sin0°)=2 \qquad w_1=2(\cos90°+i\sin90°)=2i$$
    $$w_2=2(\cos180°+i\sin180°)=-2 \qquad w_3=2(\cos270°+i\sin270°)=-2i$$

    As quatro raízes ($2,\ 2i,\ -2,\ -2i$) formam um quadrado no plano complexo, como esperado — todas elevadas à quarta dão $16$.

## Resumo de fórmulas

| Conceito | Fórmula |
| --- | --- |
| Unidade imaginária | $i^2=-1$ |
| Forma algébrica | $z=a+bi$ |
| Conjugado | $\bar z = a-bi$ |
| Módulo | $\vert z\vert=\sqrt{a^2+b^2}=\sqrt{z\bar z}$ |
| Forma polar | $z=r(\cos\theta+i\sin\theta)$ |
| Forma exponencial | $z=re^{i\theta}$ |
| Fórmula de Euler | $e^{i\theta}=\cos\theta+i\sin\theta$ |
| De Moivre (potência) | $z^n=r^n(\cos n\theta+i\sin n\theta)$ |
| Raízes $n$-ésimas | $w_k=\sqrt[n]{r}\left(\cos\frac{\theta+360°k}{n}+i\sin\frac{\theta+360°k}{n}\right)$ |
