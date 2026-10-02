# Cálculo 1

**Cálculo 1**
Conjuntos Numéricos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Símbolos
U: "união"; Ex: AUB = \{0,1...,6\}; \{x/x∈A ou x∈B\}
∩: "interseção"; Ex: A∩B = \{0,2,4\}; \{x/x∈A e x∈B\}
⊂: "contido"
⊃: "contém"
∈: "pertence"
∉: "não pertence"
Ø ou \{ \}: conjunto vazio
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Expressões Numéricas
Regra
1 - 1º(); 2°\[\]; 3º\{\}
2 - Potências e Raízes
3 - Multiplicação e Divisão
4 - Soma e Subtração
Expressões Algébricas
Operações com letras
O melhor a se fazer é usar a Fatoração
Ex: x\^6+2x\^4y+x²y+2y²
x\^4(x²+2y) + y(x²+2y) = (x\^4+y)(x²+2y)
Ex: x\^6+4x³y+4y²
x\^6+2x³y+2x³y+4y²
x³(x³+2y) + 2y(x³+2y) = (x³+2y)(x³+2y)
Ex: x\^6-3x\^4y+3x²y²-y³
x\^6-x\^4y-2x\^4y+2x²y²+x²y²-y³
x\^4(x²-y) - 2x²y(x²-y) + y²(x²-y) = (x\^4-2x²y+y²)(x²-y) Produtos Notáveis
Quadrado da soma: (x+y)² = x²+2xy+y²
Quadrado da diferença: (x-y)² = x²-2xy+y²
Produto da soma pela diferença: (x+y)(x-y) = x²-y²
Cubo da soma: (x+y)³ = x³+3x²y+3xy²+y³
Cubo da diferença: (x-y)³ = x³-3x²y+3xy²-y³
Soma de cubos: (x³+y³) = (x+y)(x²-xy+y²)
Diferença de cubos: (x³-y³) = (x-y)(x²+xy+y²)
Triângulo de Pascal
Tem função de auxiliar a busca pelos coeficientes de expressões algébricas utilizando os Binômios de Newton
Binômio de Newton
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(n¦k) = n!/(n-k)!k!
Ex: Determine o coeficiente de x\^15y\^5 em (x+2y)\^20 1\^15 . 2\^5 . (20¦5)
32. 20!/15!5! = 496128
Ex: determine o coeficiente de x\^17y³ em (3x+3y)\^20 3\^17 . 3³ . (20¦3)
3\^17 . 3³ . 20!/17!3!
Expoente = N
N = 0; 1
N = 1; 1 1
N = 2; 1 2 1
N = 3; 1 3 3 1
N = 4; 1 4 6 4 1
N = 5; 1 5 10 10 5 1
N = 6; 1 6 15 20 15 6 1
...
Importante
Em (x-y)\^n, o *expoente ímpar* do y determina o *sinal negativo*
Polinômios
Expressões algébricas formadas pela adição de monômios (expressões algébricas do tipo produto) Ex: p(x) = 4x³ - x³ + 2x - 5
OBS: R\[x\] = \{p(x)/ p(x) é um polinômio da variável x e o conjunto dos polinômios na variável x tem coeficientes reais\}
Assim, p(x)∈R\[x\] ⇔ p(x) = a0x\^0 + a1x + ... + anx\^n
p(x) = x\^4 + x³ + 3x² + 0x + 0
(1,1,3,0,0) (coeficientes);
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Grau do polinômio
É sempre o maior expoente
r(x) = -2x; grau(r(x)) = 1
q(x) = 2; grau(q(x)) = 0
p(x) = 5x\^5 + 2; grau(p(x)) = 5
Operações com polinômios
Adição
p(x) = a0 + a1x + a2x² + ... + anx\^n
q(x) = b0 + b1x + b2x² + ... +bnx\^n
p(x) + q(x) = (a0+b0) + (a1+b1)x + (a2+b2)x² + ... + (an+bn)x\^n
Multiplicação
Na multiplicação os expoentes somados tem que dar o expoente desejado (ou fazer chuveirinho) p(x) . q(x) = (a0b0) + (a1b0 + a0b1)x + (a2b0 + a1b1 + a0b2)x² + ...
a0b0 = 0+0 = 0; a1b0 = 1+0 = 1; a0b1 = 0+1 = 1; a2b0 = 2+0 = 2; a1b1 = 1+1 = 2; a0b2 = 0+2 = 2; ...
Ex: p(x) = x³ + 2x; q(x) = 3x² + x + 2
p(x) . q(x) = 2.2x + x.2x +2.x³ + 3x².2x + x.x³ + 3x².x³ → 4x + 2x² + 2x³ + 6x³ + x\^4 + 3x\^5 → 3x\^5 + x\^4 + 8x³ + 2x² + 4x
OBS: grau(p(x) . q(x)) = grau(p(x)) + grau(q(x))
se grau(p(x)) ≠ grau (q(x)) então:
grau(p(x)) + grau(q(x)) = máx grau(p(x)) . grau(q(x))
Algoritmo da Divisão
Sejam a(x) e d(x)∈R\[x\] dois polinômios com d(x) ≠ 0, então existem únicos q(x) e r(x)∈R\[x\] tais que: a(x) = d(x) . q(x) + r(x); onde d(x) é o divisor, q(x) é o quociente e r(x) é o resto
r(x) = 0 ou grau(r(x)) \< grau(d(x))
Ex: divisão de p(x) = 2x\^4 - 3x² + x - 2 por d(x) = x² - x +1
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
q(x) = 2x² + 2x - 3; r(x) = -4x + 1
Raízes de Polinômio
Definição: sejam p(x)∈R\[x\] um polinômio não nulo e a∈R\[x\] um número real; dizemos que x = a é uma raiz de p(x) se p(a) = 0
Ex: p(x) = x\^4 - 4x² + 2x + 1; x = 1 é uma raiz mas x = 0 não
Ex: dividir p(x) x\^4 - 4x² + 2x + 1 por d(x) = x - 1
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Resposta: r(x) = 0; q(x) = x³ + x² - 3x - 1; p(x) = (x³ + x² - 3x - 1)(x - 1)
Então x - 1 é uma raiz de p(x)
Raiz x = a versus divisão por x - a
De modo geral:
Dividindo p(x)∈R\[x\] por x - a obtemos q(x) e r(x)∈R\[x\] tais que:
p(x) = q(x) . (x-a) + r(x); com r(x) = 0 ou grau(r(x)) \< grau(x-a) = 1; r(x) = Constante p(x) = q(x) . (x-a) + C; com p(a) = C; p(x) = q(x) . (x-a) + p(a)
Deste modo, p(a) = 0 ⇔ x - a divide p(x)
Além disso, p(a) é exatamente o resto da divisão de p(x) por x-a
Ex: p(x) = x\^5 - 4 = (x\^4 + x³ + x² + x + 1)(x-1) - 3; com p(1) = -3
Dispositivo de Briot-Ruffini
Algoritmo que possibilita a divisão entre um polinômio e um binômio de forma mais simples Ex: dividir o polinômio p(x) = 3x³ + 2x² + x + 5 pelo binômio d(x) = x + 1
Passo a passo
1º - Desenhar dois segmentos de retas, um horizontal e outro vertical
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
2º - Colocar os coeficientes do p(x) acima do segmento horizontal e a direita do segmento vertical e repetir o primeiro coeficiente na parte de baixo; na parte esquerda do segmento vertical e embaixo do segmento horizontal devemos colocar a raiz do binômio ( para determinar a raiz basta igualar o dividendo a zero; x + 1 = 0; x = -1)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
3º - agora basta multiplicar a raiz do binômio pelo primeiro coeficiente abaixo do segmento horizontal e em seguida somar o resultado pelo próximo coeficiente localizado acima do segmento horizontal e repetir o processo até o último coeficiente
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Analisando o algoritmo
Na parte superior do segmento horizontal e à direita do segmento vertical temos os coeficientes do polinômio p(x); p(x) = 3x³ + 2x² + x + 5
O "-1" é a raiz do divisor, portanto o divisor é d(x) = x+1
Na direita do segmento vertical e abaixo do segmento horizontal se encontram o quociente e o resto, que é o último número
Lembrando que o grau do dividendo é 3 e o grau do divisor é 1, portanto o grau(q(x)) = grau(p(x)) -grau(d(x)) = 2; q(x) = 3x² - x + 2
Como r(x) é o último número, r(x) = 3
Utilizando o algoritmo da divisão, temos que:
Dividendo = Divisor . Quociente + Resto → 3x³ + 2x² + x + 5 = (x+1)(3x² -x + 2) + 3
Funções
Associações de elementos entre dois conjuntos, por exemplo uma função de A em B significa associar cada elemento de A a um único elemento de B
Em uma função A→B, o A é chamado de Domínio e o B de Contradomínio
Um elemento de B relacionado a um elemento de A recebe o nome de Imagem, agrupando todas as imagens de B temos um conjunto imagem que é um subconjunto do contradomínio
No gráfico, o f(x) simboliza o eixo y
Ex: A = \{1,2,3,4\}; B = \{1,2,3,4,5,6,7,8\}; f: A→B é x→2x, então f(x) = 2x
Domínio = \{1,2,3,4\}; Contradomínio = \{1,2,3,4,5,6,7,8\} e Imagem = \{2,4,6,8\}
Tipos
Função composta: Duas funções f e g podem ser representadas como função composta por f◦g ou g◦f f◦g (x) = f(g(x)) e g◦f (x) = g(f(x))
Função constante
f(x) = C, onde C∈R
Gráfico:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Função do 1° grau (Função afim)
f(x) = ax + b; a,b∈R com a diferente de 0
Gráficos:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
O coeficiente a é a inclinação da reta (ou o coeficiente angular)
a = tg(θ), onde θ é o ângulo formado entre a reta e o eixo x
Interseções com os eixos
y: x = 0; y = b
x: y = 0; ax + b = 0; ax = -b (raiz ou zero da função)
Caso especial: função linear, nesse caso f(x) = ax e quando a = 1 a função linear é uma função identidade
Função do 2° grau (Função quadrática)
f(x) = ax² + bx + c, para achar a raiz se usa bháskara
Gráficos (Parábola):
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
a\>0 = concavidade pra cima
a\<0 = concavidade pra baixo
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Δ é o discriminante da equação do 2° grau, é a interseção com o eixo x
Interseção com os eixos
Eixo y: x = 0; y = c
Eixo x: y = 0; Fórmula de Bháskara
Para calcular o x do vértice (ponto que fica no centro da parábola)
xv = -b/2a = x1+x1/2 (x1 e x2 são as raízes)
Para calcular o y do vértice (ponto mais baixo da parábola)
yv = f(xv) = -Δ/4a
Ex: f(x) = x² - 4x + 3
a\>0; c = 3; raízes = (x1 = 1) e (x2 = 3); xv = 2; yv = -1
Função exponencial
f(x) = a\^x; quando o valor de x aumenta, a imagem também aumenta
Função logarítmica
f(x) = log de x na base a; com a sendo real, positivo e diferente de 1
A função logarítmica é o inverso da função exponencial
Funções invertíveis
Uma função f: A→B é invertível se existe uma função g: B→A, ou seja, g = f\^-1
Nesse caso, o domínio A em f vira contradomínio em g e o contradomínio B em f vira o domínio em g Operações com funções
(f+g)(x) = f(x) + g(x)
(f-g)(x) = f(x) - g(x)
(Kf)(x) = K . f(x)
(f.g)(x) = f(x) . g(x)
Com D = D(f)∩D(g):
(f/g)(x) = f(x)/g(x)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Composição de funções
Dadas duas funções f e g, a composição de f com g é denotada como f◦g tal que f◦g(x) = f(g(x))
Limites
O limite tem o objetivo de determinar o comportamento de determinada função f(x) a medida de que ela se aproxima de alguns valores
Ex: f(x) = x+1
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
À medida que x se aproxima de 1, o valor de f(x) se aproxima de 2 Ex: f(x) = x³ - 1
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
À medida que x se aproxima de 1, o valor de f(x) se aproxima de 3 Definição intuitiva:
seja f(x) uma função definida no ponto a∈R, mas não necessariamente no ponto a
Escrevemos que L∈R é o limite de f quando x tende à a, se tornando x suficientemente próximo de a mas não igual à a; teremos valores de f(x) tão próximos de L quanto quisermos
O limite de f quando x tende a a não depende do valor de f no ponto a
Notação
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Propriedades dos limites
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Limites laterais
Limite lateral pela esquerda
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Limite lateral pela direita
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Portanto, uma função f possui limite quando o limite lateral pela esquerda de f é igual ao limite lateral pela direita de f
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Limites contínuos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Na letra c, os limites laterais são diferentes, logo não há limite; para isso, vamos manipular de modo a existir um limite contínuo
Propriedades
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Limites no infinito
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Propriedades
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
O problema da reta tangente
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
A reta tangente ao gráfico de uma função
Ex: obtenha a equação da reta tangente ao gráfico de f(x) = 4x - x² no ponto de abscissa x = 1 O ponto em que a reta é tangente ao gráfico é P = (1, f(1)); f(1) = 4 - 1 = 3
Logo, P = (1,3)
A equação da reta é dada por: y-yo = m(x-xo)
xo = 1; yo = 3
Logo, a equação da reta do ponto P é y = m(x-1) + 3
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se delta = 0 a reta tangente só toca em um ponto, que é o que queremos
Ex: determine a equação da reta tangente ao gráfico f(x) = x³ no ponto P = (1,1)
Equação da reta do ponto P(1,1): y = m(x-1) + 1
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Outra forma de fazer:
Equação da reta: y-yo = m(x-xo)
m = y-yo/(x-xo )
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: determine a equação da reta tangente ao gráfico f(x) = x² - 3x no ponto P = (1, -2)
Equação da reta no ponto P(1, -2): y + 2 = m(x-1)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
A reta tangente com limite de retas secantes
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: determine a equação na reta tangente ao gráfico de f(x) = x³ no ponto P = (1,1)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: encontre a equação da reta tangente ao gráfico de f(x) = x³ - 4x no ponto P = (1, -2)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivada
Definição
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
OBS: utilizando o conceito de derivada da direita; h sempre tende à 0
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Basicamente, derivada é igual ao coeficiente m; porém, a derivada se escreve como f'(xo) Ex: Obtenha a derivada no ponto xo = 0 na função f(x) = x²
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: Obtenha a derivada no ponto xo = 1 na função f(x) = x\^4 - 3x + 5
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Função derivada
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
OBS: utilizando esse conceito de derivada; h sempre tende à 0
Com isso, é a função derivada que produz a inclinação da reta tangente ao gráfico de f
Derivadas de funções elementares
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: item b)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: item f)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Regra de derivação
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(Regra do tombo)
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Outras regras
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Regra da cadeia (ou Regra da função composta)
Vamos considerar o problema de derivar a função y = (x³+2)\^4
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Para isso, primeiramente vamos atribuir a função u = x³ + 2 Com isso, y = u\^4
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(derivada externa em relação à derivada da função interna = dy/du) . (derivada interna em relação àvariável = du/dx) = (derivada externa em relação à variável = dy/dx)
Outra forma de expressar a fórmula: y' = f'(u).u'
OBS: sempre que possível, transformar a raiz em uma potência
Ex: obtenha a função derivada de f(x) = 4x³ - 2x + 5
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: obtenha a função derivada de f(x) = (2x - 3)/(1 - x)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: obtenha a derivada da função f (x) = (x²+1)\^5/(x³+x+1)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: obtenha a derivada da função f (x) = (x³ + 2)\^100
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: obtenha P e Q que pertencem à função g(x) = 2x³ - 3x² - 3x onde suas retas tangentes sejam paralelas à y = 3x - 2
Se as retas tangentes de g(x) são paralelas à y e o coeficiente angular (ou derivada) de y é 3 Logo, é válido dizer que \[g(x)\]' é igual à \[y\]'; logo, \[g(x)\]' = 3
\[g(x)\]' = 3.2x² - 2.3x¹ - 1.3.x\^0 = 6x² - 6x - 3
6x² - 6x - 3 = 3; x² - x - 1 = 0
Resolvendo por Bháskara, encontramos:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Portanto, os pontos P e Q são:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Trigonometria
Relações métricas no triângulo retângulo
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Relações trigonométricas no triângulo retângulo
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arcos notáveis
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Aplicações
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Círculo trigonométrico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(1° quadrante é o superior direito e o 4° quadrante é o inferior direito) Funções trigonométricas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráficos
Função seno
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Função cosseno
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Função tangente
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Identidades trigonométricas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema do confronto
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Limite trigonométrico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
É outro limite trigonométrico fundamental
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
É outro limite trigonométrico fundamental
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivadas de funções trigonométricas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Tabela para decorar
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Outras derivadas
Derivada da função e\^x
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
se x é uma função derivável, então \[e\^x\]' = x' . (e\^x) Derivada da função ln(x) ou logaritmo natural de x
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
se x é uma função derivável, então \[ln(x)\]' = x' . 1/x
OBS: ln(x) ou logaritmo natural de x
ln(x) pode ser escrito como log de x na base "e"
por exemplo, ln(1) = log de 1 na base; ou seja existe um x tal que e\^x = 1(x = 0) Derivada de uma constante (a) elevado à outro número real ou função (x)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Exemplos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
se x é uma função derivável, então \[a\^x\]' = x' . a\^x . ln(a)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivada de uma função elevada à outra função
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivada de log
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Exemplos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: z = sen(x²)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivada da função inversa
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivada das funções trigonométricas inversas
Arcsen (inversa do seno)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráfico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arccos (inverso do cosseno)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráfico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arctg (inverso da tangente)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráfico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arccot
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arcsec (inverso da secante)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Demonstração
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Arccosec (inverso da cossecante)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Derivação implícita
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
OBS: quando usar a regra da cadeia não prestar atenção apenas nas fórmulas mas também na lógica
Para a lógica, separar as derivadas em funções e em coeficientes, já que a regra da cadeia é a derivada da de fora e a de dentro
Por isso, a derivada de uma função sempre é a derivada da função em si vezes a derivada do coeficiente da função
OBS: uma função é duas vezes diferenciável se tanto a derivada da função quanto a derivada da sua derivada são diferenciáveis
Se uma função é diferenciável, então a derivada existe para todos os pontos do limite da função
OBS: conjugação de raiz cúbica (a lógica é a mesma para as de outras raízes)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema do Valor Intermediário (ou Teorema de Bolzano)
Propriedade das funções contínuas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Toda função polinomial é contínua
Para provar que tal função possui raiz, basta achar um f(x) positivo e outro f(x) negativo
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema do Valor Extremo (ou Teorema de Weierstrass)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
O mínimo e máximo absolutos são respectivamente o menor e maior valor que a função atinge em todo o seu domínio
Dada uma função f(x), f(c) é o valor máximo absoluto se f(c) ≥ f(x) para todo x no domínio da função (intervalo aberto)
Dada uma função f(x), f(c) é o valor mínimo absoluto se f(c) ≤ f(x) para todo x no domínio da função (intervalo aberto)
O mínimo e máximo locais são respectivamente o menor e maior valor que a função atinge em um intervalo fechado
Dada uma função f(x), f(c) é o valor máximo absoluto se f(c) ≥ f(x) para todo x no domínio dentro do intervalo fechado
Dada uma função f(x), f(c) é o valor máximo absoluto se f(c) ≤ f(x) para todo x no domínio dentro do intervalo fechado
Todo máximo e mínimo absolutos são um máximo e mínimo locais, mas nem todo máximo e mínimo locais são um máximo e mínimo absoluto
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ponto crítico - é um ponto x no domínio de uma função em que f'(x) = 0 ou f'(x) não existe; o ponto crítico é um extremo absoluto
Quando f'(x) = 0, isso caracteriza um ponto de inflexão (ponto sobre uma curva na qual a curvatura troca o sinal, podendo mudar de concavidade para cima, ou positivo, para concavidade para baixo, ou negativo; e vice-versa)
Quando f'(x) não existir, isso indica um sinal de descontinuidade, logo, uma função que não écontínua
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Logo, para x = 3/2 temos o valor mínimo de 1 e para x = 1 e x = 2 temos o valor máximo de 2 Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema do Valor Médio
Teorema de Rolle
Utilizado para demonstrar o Teorema do Valor Médio
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Representação do Teorema
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Consequências
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Como f(x) é uma função polinomial, logo é contínua; além disso, f(x) é uma função derivável no intervalo \[1,3\]
Com isso, as condições do Teorema do Valor Médio estão atendidas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Sinal da 1ª derivada
Condições
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex: Encontre onde a função f(x) = 3x\^4 - 4x³ - 12x² + 5 é crescente e onde ela é decrescente
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráfico
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Pelo gráfico, fica fácil perceber que f(x) possui pontos críticos, configurando máximos ou mínimos da função; ou seja, existe mais de um "c" na função
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Em outras palavras
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Gráficos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Sinal da 2ª derivada
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Os pontos em que ocorrem as mudanças de concavidade são chamados de pontos de inflexão (pontos em que f''(x) = 0)
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Neste gráfico, há um ponto de inflexão pois a curva no intervalo (0, 12) é côncava para cima e a partir do intervalo (12, 18) é côncava para baixo
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(Diferentemente do teste da primeira derivada, a derivada no ponto c está definida)
Ex: Determine os máximos e mínimos relativos de f(x) = -4x³ + 3x² + 15
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Problemas de otimização
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
V = (50 - 2x)(30 - 2x).x = 4x³ - 160x² + 1500x
V' = 12x² - 320x + 1500
12x² - 320x + 1500 = 0
3x² - 80x + 375 = 0
x1 = (40+5√19)/3 (ponto crítico)
Este valor não é possível no nosso problema, pois x1 ≅ 20 e 2x \< 30, logo é um absurdo
x2 = (40-5√19)/3 (ponto crítico)
Valor que vamos usar, x2 ≅ 6,07
Domínio de V(x) = \]0, 15\[
Limite de x tende a 0 = 0
Limite de x tende a 15 = 0
Quando x tende aos extremos do domínio o volume tende a x V(6,07) ≅ 4104 cm³
Ponto máximo da função, portanto, x ≅ 6,07
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Regra de L'Hôspital
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se a forma indeterminada persistir, temos que derivar quantas vezes forem necessárias Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Assíntotas
Verticais
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se o denominador do limite for igual a 0, temos uma assíntota vertical Possui foco no "x"
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Horizontais
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Possui foco no "y"
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Oblíquas
Funções racionais
Para calcular a assíntota oblíqua, basta realizar a divisão de polinômio até chegar na forma irredutível, o quociente é a assíntota oblíqua
Existem assíntotas oblíquas se o grau do polinômio de cima for unidade maior que o grau do polinômio de baixo; além disso, ela servirá tanto para +∞ quanto -∞
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Funções não racionais
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Precisamos fazer o cálculo para mais e menos infinito Se m for igual a 0, a assíntota é horizontal
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Logo, y = 1/2 é uma assíntota horizontal
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Logo, y = -2x - (1/2) é uma assíntota oblíqua
Integral
A integral definida
Problema da área
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ou seja, calcular a integral é calcular a área
Notação
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
∫ - símbolo da integral
a - limite inferior da integração
b - limite superior da integração
\[a,b\] - intervalo fechado da função que vamos calcular a área
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
f(x) - função a integrar
dx - diferencial de x (variável independente)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
limite de n tendendo à infinito do somatório de i = 1 até n de f(xi*) (é o f(x) da extremidade direita do xi* (xi *= \[x(i-1), xi\]), ou seja, o valor de y do ponto xi; entre outras palavras é a altura) vezes Δx ((xi - x(i -1))/n); ou seja, é o valor da base)*
*Portanto a integral do intervalo de \[a,b\] de f(x) é o limite de n tendendo à infinito do somatório de todas as pequenas áreas (diferenciais de x ou pouquinhos de x) do intervalo \[a,b\] na qual a área de*
*cada pouquinho se dá pela multiplicação da base (Δx) pela altura (f(xi*)) Ex: Calcule
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(isso tudo sobre n) OBS: segundo a fórmula de Faulhaber:
Seja n, p∈Z\*+ (conjunto dos inteiros positivos com exceção do zero)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
É igual a: 1\^p + 2\^p + ... + n\^p
p - potência na qual os números estão elevados
n\^(p+1-i) é o último número natural
Bi = é o i-ésimo número de Bernoulli
OBS: Números de Bernoulli
Sequências de números racionais com conexões na teoria dos números Formas de calcular:
Fórmula de recorrência
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se n é impar e maior que 1, Bn = 0
Fórmula utilizando a função zeta de Riemann
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
ζ(n) é a função zeta de Riemann
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Sequência
*(tabela/banco de dados do Notion não migrado — [ver original no Notion](https://www.notion.so/68cb3b681efe49a997cd8060eb01e40a))*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
o que estava sobre n pode ser cortado, não interferindo no resultado
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Teorema fundamental do cálculo
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Outra forma de fazer
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
f(p(x)) é substituir o p(x) no t e f(q(x)) é substituir o q(x) no t
Primitiva
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Como achar a primitiva do tipo x\^n:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Propriedades
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Primeira forma
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Segunda forma
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Áreas de regiões entre gráficos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Tabela de integrais definidas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Técnicas de integração
Integração por substituição
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Integração por partes
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Integrais trigonométricas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(regra da potência do cosseno ímpar)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(regra da potência do seno e cosseno pares)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(regra da potência do seno ímpar)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
(regra da potência do seno e cosseno pares)
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Quando aparecer apenas tg(x) ou cotg(x), utilizar essa fórmula trigonométrica Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Quando aparecer apenas sec(x) ou cossec(x), utilizar esse macete Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Técnica para calcular integral de tg(x)sec(x), pode usar para calcular cossec(x)cotg(x) também Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Substituição trigonométrica
Tabela de substituições trigonométricas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Primeira forma
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Segunda forma
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Área da elipse
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Frações parciais
Técnica usada para integrar funções racionais do tipo:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se apenas o denominador for uma função
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Se o numerador e o denominador for uma função:
Caso o grau do numerador seja maior ou igual que o grau do denominador, devemos realizar a divisão do numerador pelo denominador
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
P(x) é o dividendo S(x) é o quociente, Q(x) é o divisor e R(x) é resto
Depois, se possível, devemos fatorar completamente o denominador Q(x) Por fim decompomos em frações parciais encontrando os coeficientes escolhidos
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
Ex:
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b774737d6d2a4bd693ab75bd5620851e)*
