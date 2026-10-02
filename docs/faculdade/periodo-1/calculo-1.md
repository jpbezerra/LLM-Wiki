# CÁLCULO 1

---
## Conjuntos Numéricos
<details>
<summary>Tipos de conjuntos numéricos</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
</details>
<details>
<summary>Símbolos</summary>
	```plain text
U: "união"; Ex: AUB = {0,1...,6}; {x/x∈A ou x∈B}
∩: "interseção"; Ex: A∩B = {0,2,4}; {x/x∈A e x∈B}
⊂: "contido"
⊃: "contém"
∈: "pertence"
∉: "não pertence"
Ø ou { }: conjunto vazio
	```
</details>
---
## Expressões
<details>
<summary>Numérica</summary>
	- Regras
		```plain text
1 - 1º(); 2°[]; 3º{}
2 - Potências e Raízes
3 - Multiplicação e Divisão
4 - Soma e Subtração
		```
</details>
<details>
<summary>Algébricas</summary>
	- Operações com letras
		- O melhor a se fazer é usar a Fatoração,
			```plain text
Ex: x^6+2x^4y+x²y+2y²
		x^4(x²+2y) + y(x²+2y) = (x^4+y)(x²+2y)
		
Ex: x^6+4x³y+4y²
	x^6+2x³y+2x³y+4y²
		x³(x³+2y) + 2y(x³+2y) = (x³+2y)(x³+2y)
			
Ex: x^6-3x^4y+3x²y²-y³
	x^6-x^4y-2x^4y+2x²y²+x²y²-y³
		x^4(x²-y) - 2x²y(x²-y) + y²(x²-y) = (x^4-2x²y+y²)(x²-y)
			```
	- Produtos Notáveis
		```plain text
- Quadrado da soma: (x+y)² = x²+2xy+y²
- Quadrado da diferença: (x-y)² = x²-2xy+y²
- Produto da soma pela diferença: (x+y)(x-y) = x²-y²
- Cubo da soma: (x+y)³ = x³+3x²y+3xy²+y³
- Cubo da diferença: (x-y)³ = x³-3x²y+3xy²-y³
- Soma de cubos: (x³+y³) = (x+y)(x²-xy+y²)
- Diferença de cubos: (x³-y³) = (x-y)(x²+xy+y²)
		```
	- Triângulo de Pascal
		- Tem função de auxiliar a busca pelos coeficientes de expressões algébricas utilizando os Binômios de Newton
			<details>
			<summary>Binômio de Newton</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
				-  (n¦k) = n!/(n-k)!k!
					```plain text
Ex: Determine o coeficiente de x^15y^5 em (x+2y)^20
		1^15 . 2^5 . (20¦5)
				32. 20!/15!5! = 496128
						
Ex: determine o coeficiente de x^17y³ em (3x+3y)^20
		3^17 . 3³ . (20¦3)
				3^17 . 3³ . 20!/17!3!
					```
			</details>
			<details>
			<summary>Expoentes</summary>
				```plain text
Expoente = N
N = 0; 1
N = 1; 1 1
N = 2; 1 2 1
N = 3; 1 3 3 1
N = 4; 1 4 6 4 1
N = 5; 1 5 10 10 5 1
N = 6; 1 6 15 20 15 6 1
...
				```
			</details>
	- Importante
		- Em (x-y)\^n, o *expoente ímpar* do y determina o *sinal negativo*
</details>
---
## Polinômios
<details>
<summary>Expressões algébricas formadas pela adição de monômios (expressões algébricas do tipo produto)</summary>
	- Ex: p(x) = 4x³ - x³ + 2x - 5
		- OBS: R\[x\] = \{p(x)/ p(x) é um polinômio da variável x e o conjunto dos polinômios na variável x tem coeficientes reais\}
			- Assim, p(x)∈R\[x\] ⇔ p(x) = a0x\^0 + a1x + ... + anx\^n
			- p(x) = x\^4 + x³ + 3x² + 0x + 0
				- (1,1,3,0,0) (coeficientes);
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
</details>
<details>
<summary>Grau do polinômio</summary>
	- É sempre o maior expoente
		- r(x) = -2x; grau(r(x)) = 1
		- q(x) = 2; grau(q(x)) = 0
		- p(x) = 5x\^5 + 2; grau(p(x)) = 5
</details>
<details>
<summary>Operações com polinômios</summary>
	<details>
	<summary>Adição</summary>
		- p(x) = a0 + a1x + a2x² + ... + anx\^n
		- q(x) = b0 + b1x + b2x² + ... +bnx\^n
		- p(x) + q(x) = (a0+b0) + (a1+b1)x + (a2+b2)x² + ... + (an+bn)x\^n
	</details>
	<details>
	<summary>Multiplicação</summary>
		- Na multiplicação os expoentes somados tem que dar o expoente desejado (ou fazer chuveirinho)
			- p(x) . q(x) = (a0b0) + (a1b0 + a0b1)x + (a2b0 + a1b1 + a0b2)x² + …
				- a0b0 = 0+0 = 0; a1b0 = 1+0 = 1; a0b1 = 0+1 = 1; a2b0 = 2+0 = 2; a1b1 = 1+1 = 2; a0b2 = 0+2 = 2; …
		- Ex: p(x) = x³ + 2x; q(x) = 3x² + x + 2
			- p(x) . q(x) = 2.2x + x.2x +2.x³ + 3x².2x + x.x³ + 3x².x³ → 4x + 2x² + 2x³ + 6x³ + x\^4 + 3x\^5 → 3x\^5 + x\^4 + 8x³ + 2x² + 4x
		- OBS: grau(p(x) . q(x)) = grau(p(x)) + grau(q(x))
			- Se grau(p(x)) ≠ grau (q(x)) então:
				- grau(p(x)) + grau(q(x)) = máx grau(p(x)) . grau(q(x))
	</details>
	<details>
	<summary>Algoritmo da divisão</summary>
		- Sejam a(x) e d(x)∈R\[x\] dois polinômios com d(x) ≠ 0, então existem únicos q(x) e r(x)∈R\[x\] tais que:
			- a(x) = d(x) . q(x) + r(x); onde d(x) é o divisor, q(x) é o quociente e r(x) é o resto
		- Ex: divisão de p(x) = 2x\^4 - 3x² + x - 2 por d(x) = x² - x +1
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			q(x) = 2x² + 2x - 3; r(x) = -4x + 1
	</details>
</details>
<details>
<summary>Raízes de Polinômio</summary>
	- Definição: sejam p(x)∈R\[x\] um polinômio não nulo e a∈R\[x\] um número real; dizemos que x = a é uma raiz de p(x) se p(a) = 0
		- Ex: p(x) = x\^4 - 4x² + 2x + 1; x = 1 é uma raiz mas x = 0 não
		- Ex: dividir p(x) x\^4 - 4x² + 2x + 1 por d(x) = x - 1
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			Resposta: r(x) = 0; q(x) = x³ + x² - 3x - 1; p(x) = (x³ + x² - 3x - 1)(x - 1)
</details>
<details>
<summary>Raiz x = a versus divisão por x - a</summary>
	- De modo geral:
		- Dividindo p(x)∈R\[x\] por x - a obtemos q(x) e r(x)∈R\[x\] tais que:
			- p(x) = q(x) . (x-a) + r(x); com r(x) = 0 ou grau(r(x)) \< grau(x-a) = 1; r(x) = Constante
			- p(x) = q(x) . (x-a) + C; com p(a) = C; p(x) = q(x) . (x-a) + p(a)
			- Deste modo, p(a) = 0 ⇔ x - a divide p(x)
			- Além disso, p(a) é exatamente o resto da divisão de p(x) por x-a
			- Ex: p(x) = x\^5 - 4 = (x\^4 + x³ + x² + x + 1)(x-1) - 3; com p(1) = -3
</details>
<details>
<summary>Dispositivo de Briot-Ruffini</summary>
	- Algoritmo que possibilita a divisão entre um polinômio e um binômio de forma mais simples
	- Ex: dividir o polinômio p(x) = 3x³ + 2x² + x + 5 pelo binômio d(x) = x + 1
		- Passo a passo
			<details>
			<summary>1º - Desenhar dois segmentos de retas, um horizontal e outro vertical</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			</details>
			<details>
			<summary>2º - Colocar os coeficientes do p(x) acima do segmento horizontal e a direita do segmento vertical e repetir o primeiro coeficiente na parte de baixo; na parte esquerda do segmento vertical e embaixo do segmento horizontal devemos colocar a raiz do binômio ( para determinar a raiz basta igualar o dividendo a zero; x + 1 = 0; x = -1)</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			</details>
			<details>
			<summary>3º - agora basta multiplicar a raiz do binômio pelo primeiro coeficiente abaixo do segmento horizontal e em seguida somar o resultado pelo próximo coeficiente localizado acima do segmento horizontal e repetir o processo até o último coeficiente</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			</details>
			<details>
			<summary>Analisando o algoritmo</summary>
				- Na parte superior do segmento horizontal e à direita do segmento vertical temos os coeficientes do polinômio p(x); p(x) = 3x³ + 2x² + x + 5
				- O "-1" é a raiz do divisor, portanto o divisor é d(x) = x+1
				- Na direita do segmento vertical e abaixo do segmento horizontal se encontram o quociente e o resto, que é o último número
					- Lembrando que o grau do dividendo é 3 e o grau do divisor é 1, portanto o grau(q(x)) = grau(p(x)) - grau(d(x)) = 2; q(x) = 3x² - x + 2
					- Como r(x) é o último número, r(x) = 3
				- Utilizando o algoritmo da divisão, temos que: 
					- Dividendo = Divisor . Quociente + Resto → 3x³ + 2x² + x + 5 = (x+1)(3x² -x + 2) + 3
			</details>
</details>
---
## Funções
<details>
<summary>Associações de elementos entre dois conjuntos, por exemplo uma função de A em B significa associar cada elemento de A a um único elemento de B</summary>
	- Em uma função A→B, o A é chamado de Domínio e o B de Contradomínio
		- Um elemento de B relacionado a um elemento de A recebe o nome de Imagem, agrupando todas as imagens de B temos um conjunto imagem que é um subconjunto do contradomínio
			- No gráfico, o f(x) simboliza o eixo y
</details>
<details>
<summary>Ex: A = \{1,2,3,4\}; B = \{1,2,3,4,5,6,7,8\}; f: A→B é x→2x, então f(x) = 2x</summary>
	- Domínio = \{1,2,3,4\}; Contradomínio = \{1,2,3,4,5,6,7,8\} e Imagem = \{2,4,6,8\}
</details>
<details>
<summary>Tipos</summary>
	<details>
	<summary>Função composta: Duas funções f e g podem ser representadas como função composta por f◦g ou g◦f</summary>
		- f◦g (x) = f(g(x)) e g◦f (x) = g(f(x))
	</details>
	<details>
	<summary>Função constante</summary>
		- f(x) = C, onde C∈R 
		<details>
		<summary>Gráfico</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
		</details>
	</details>
	<details>
	<summary>Função do 1° grau (Função afim)</summary>
		- f(x) = ax + b; a,b∈R com a diferente de 0
		<details>
		<summary>Gráficos</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			- O coeficiente a é a inclinação da reta (ou o coeficiente angular)<br>a = tg(θ), onde θ é o ângulo formado entre a reta e o eixo x
		</details>
	</details>
	<details>
	<summary>Função do 2° grau (Função quadrática)</summary>
		- f(x) = ax² + bx + c, para achar a raiz se usa bháskara
		<details>
		<summary>Gráficos (Parábola)</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			- a\>0 = concavidade pra cima
			- a\<0 = concavidade pra baixo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
			- Δ é o discriminante da equação do 2° grau, é a interseção com o eixo x
		</details>
		<details>
		<summary>Interseção com os eixos</summary>
			- Eixo y: x = 0; y = c
			- Eixo x: y = 0; Fórmula de Bháskara
		</details>
		<details>
		<summary>Para calcular o x do vértice (ponto que fica no centro da parábola)</summary>
			xv = -b/2a = x1+x1/2 (x1 e x2 são as raízes)
		</details>
		<details>
		<summary>Para calcular o y do vértice (ponto mais baixo da parábola)</summary>
			yv = f(xv) = -Δ/4a
		</details>
		<details>
		<summary>Ex: f(x) = x² - 4x + 3</summary>
			a\>0; c = 3; raízes = (x1 = 1) e (x2 = 3); xv = 2; yv = -1
		</details>
	</details>
	<details>
	<summary>Função exponencial</summary>
		- f(x) = a\^x; quando o valor de x aumenta, a imagem também aumenta
	</details>
	<details>
	<summary>Função logarítmica</summary>
		- f(x) = log de x na base a; com a sendo real, positivo e diferente de 1
		- A função logarítmica é o inverso da função exponencial
			<details>
			<summary>Funções invertíveis</summary>
				- Uma função f: A→B é invertível se existe uma função g: B→A, ou seja, g = f\^-1
					- Nesse caso, o domínio A em f vira contradomínio em g e o contradomínio B em f vira o domínio em g
			</details>
	</details>
</details>
<details>
<summary>Operações com funções</summary>
	- (f+g)(x) = f(x) + g(x)
	- (f-g)(x) = f(x) - g(x)
	- (Kf)(x) = K . f(x)
	- (f.g)(x) = f(x) . g(x)
	- Com D = D(f)∩D(g):
		- (f/g)(x) = f(x)/g(x)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
</details>
<details>
<summary>Composição de funções</summary>
	- Dadas duas funções f e g, a composição de f com g é denotada como f◦g tal que f◦g(x) = f(g(x))
</details>
---
## Limites
---
## O problema da reta tangente (Derivada)
---
## Trigonometria
---
## Teorema do Valor Intermediário (ou Teorema de Bolzano)
- Propriedade das funções contínuas
> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
- Toda função polinomial é contínua
- Para provar que tal função possui raiz, basta achar um f(x) positivo e outro f(x) negativo
<details>
<summary>Exemplo</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/b4b75b2378ac4f74b821e7fd09c3afc8)*
</details>
---
## Teorema do Valor Extremo (ou Teorema de Weierstrass)
---
## Teorema do Valor Médio
---
## Sinal da 1ª derivada
---
## Sinal da 2ª derivada
---
## Problemas de otimização
---
## Regra de L'Hôspital
---
## Assíntotas
---
## Integral
---
[Cálculo 1](calculo-1/calculo-1.md)

## Conteúdo

- [Cálculo 1](calculo-1/calculo-1.md)
