# FÍSICA P/ COMPUTAÇÃO

---
## Eletroestática
- Ramo da física que observa o comportamento de cargas elétricas em repouso
<details>
<summary>Cargas elétricas</summary>
	Carga elementar = e = 1.6x10\^-19 Coulombs
	<details>
	<summary>Unidades de medida</summary>
		- Mili (m)
			- 10\^-3
		- Micro (µ)
			- 10\^-6
		- Nano (n)
			- 10\^-9
	</details>
	<details>
	<summary>Elétrons</summary>
		- Carga negativa
		- É uma particula elementar
		- São muito mais móveis do que prótons
		- São léptons, ou seja, não são compostos por quarks
		- Carga elétrica = -e
	</details>
	<details>
	<summary>Prótons</summary>
		- Carga positiva
		- Possui 2 quarks up e 1 down
		- Não é uma partícula elementar
		- Carga elétrica = e
			- Carga = 2x(2e/3) + -e/3 = +1.6x10\^-19
	</details>
	<details>
	<summary>Nêutrons</summary>
		- Carga neutra
		- Possui 2 quarks down e 1 up
		- Carga elétrica = 0
			- Carga = (2e/3) + 2x(-e/3) = 0
	</details>
</details>
- Materiais
	- Condutores, isolantes, semicondutores, supercondutores
<details>
<summary>Força elétrica (Lei de Coulumb)</summary>
	- É a força entre duas cargas 
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
	- Fórmula
		$$
		
F = \frac{K \cdot |q_1 \cdot q_2|}{r^2}

		$$
		$$
		K = 1 / \text{4πε}
		$$
		ε = Permissividade elétrica do meio (depende do meio)
		K = 9x10\^9 N.m²/C² (constante)
		q1 e q2 = Magnetude das cargas elétricas
		r = Distância entre os centros das cargas
		Unidade = Newton
	- A força é um vetor, que pode ser dividida em Fe x̂ e Fe ŷ; ou seja, Força elétrica na coordenada x e Força elétrica na coordenada y
		<details>
		<summary>Revisão de vetores</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		</details>
	- Atração
		- Cargas opostas se atraem
	- Repulsão
		- Cargas iguais se repelem
	<details>
	<summary>Exemplo </summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		- (Ele quer saber a quantidade de elétrons em cada carga)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
	</details>
</details>
<details>
<summary>Princípio da superposição</summary>
	- Força entre 3 ou mais cargas
	- O princípio diz que a força entre duas cargas num grupo de cargas é independente da presença das outras cargas
		- Logo, a força elétrica resultante entre essas 3 ou mais cargas é o vetor resultante das forças elétricas entre essas cargas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
	<details>
	<summary>Exemplo </summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		- Sem querer eu coloquei 0.9/4.4; mas o certo é 0.9/4.7 = 0.1914893617
			- O arctan(0.1914893617) é exatamente 10.8º
	</details>
</details>
<details>
<summary>Campo elétrico</summary>
	- É um campo vetorial provocado pela ação de cargas elétricas, que existe tanto no vácuo como em meio material
	<details>
	<summary>Tipos de campo</summary>
		- Escalares
			- Retorna um valor escalar
			- Exemplo: pressão
		- Vetoriais
			- Retorna um valor vetorial
			- Exemplo: velocidade das partícula num fluido
	</details>
	- Para caracterizar E, usamos uma carga de prova q’, onde q’ é sempre uma carga positiva (maior que zero)
		- Com essa caracterização, descobrimos como se calcular o campo elétrico:
			$$
			E = \frac{K|q|}{r^2} \hat{\imath}

			$$
			K = 9x10\^9 N.m²/C² (constante)
			q = magnetude das cargas elétricas
			r = distância da carga para a carga de prova
			î = direção do campo elétrico
			Unidade = N/C
	- Dependendo da carga, o campo elétrico é positivo ou negativo
		<details>
		<summary>Se a carga for positiva</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
			- A direção do campo elétrico é contrária aonde a carga está
		</details>
		<details>
		<summary>Se a carga for negativa</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
			- O campo elétrico é em direção aonde a carga está
		</details>
	<details>
	<summary>Linhas de fluxo</summary>
		- Fornecem a direção e o sentido do campo E local
		- A densidade da linha é proporcional à intensidade de E; que é proporcional à carga q; que é inversamente proporcional à r²
			- Ou seja, se as linhas de fluxo forem menores vão existir mais linhas; se as linhas de fluxo forem maiores vão existir menos linhas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
	</details>
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
	</details>
	- Campo gerado por várias cargas
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
</details>
<details>
<summary>Energia potencial elétrica</summary>
	- Energia potencial elétrica é uma forma de energia relacionada à posição relativa entre pares de cargas elétricas
	- Fórmula
		$$
		Ep(r) = \frac{K \cdot |q_1 \cdot q_2|}{r}
		$$
		K = 9x10\^9 N.m²/C² (constante)
		q1 e q2 = magnetude das cargas elétricas
		r = Distância entre as cargas
		Unidade = J
		- Caso queira calcular a Ep entre duas cargas deve utilizar apenas a fórmula acima
		- Caso queira calcular a Ep entre três ou mais cargas, deve se fazer um somatório dos energias
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/75e6995a02ec4548abdca3c283b6bacb)*
</details>
<details>
<summary>Potencial elétrico</summary>
	- É a capacidade que um corpo energizado tem de realizar trabalho, ou seja, atrair ou repelir outras cargas elétricas
	- Fórmula
		$$
		V(r) = \frac{Ep(r)}{q'} = \frac{Kq}{r}
		$$
		K = 9x10\^9 N.m²/C² (constante)
		q’ e q = Magnetude das cargas elétricas
		r = Distância entre as cargas
		Unidade = V (J/C)
</details>
---
