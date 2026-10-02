# Assunções da regressão linear

---
Para que a regressão linear produza resultados confiáveis, algumas assunções devem ser atendidas:
<details>
<summary>**Linearidade:** A relação entre a variável dependente e a variável independente deve ser linear.</summary>
	- Variável dependente - no contexto de regressão linear é representada por Y e é a variável  que está sendo medida ou observada
	- Variável independente - no contexto de regressão linear é representada por X e é manipulada ou controlada pelo pesquisador
	- Exemplo: Analisando os efeitos do tempo de estudo (variável independente) no desempenho acadêmico (variável dependente)
	- Ou seja, para cada unidade de mudança da variável independente, espera-se que a mudança na variável dependente seja constante
</details>
<details>
<summary>**Independência das observações:** As observações devem ser independentes umas das outras.</summary>
	- A independência das observações é essencial para garantir a validade estatística dos testes de hipóteses e intervalos de confiança associados aos coeficientes de regressão. Se as observações não forem independentes umas das outras, os testes estatísticos podem produzir resultados distorcidos e não confiáveis.
	- A independência das observações é necessária para obter estimativas precisas e não tendenciosas dos parâmetros do modelo de regressão. Se as observações estiverem correlacionadas ou dependentes umas das outras, as estimativas dos coeficientes de regressão podem ser enviesadas e imprecisas.
	-  A independência das observações permite que os resultados obtidos a partir do modelo de regressão sejam generalizados para a população de interesse. Se as observações não forem independentes, os resultados podem se aplicar apenas ao conjunto específico de observações e não podem ser generalizados para a população mais ampla.
	- Em resumo, a independência das observações é uma suposição crítica da regressão linear porque afeta a validade estatística, a precisão da estimativa dos parâmetros e a generalização dos resultados. Assumir a independência das observações permite que os resultados da regressão sejam confiáveis e aplicáveis a uma ampla gama de situações.
</details>
<details>
<summary>**Homoscedasticidade:** A variância dos resíduos (erros) deve ser constante em todos os níveis das variáveis independentes.</summary>
	- A homocedasticidade é essencial para garantir a validade dos testes estatísticos associados aos coeficientes de regressão. Se os erros do modelo não tiverem variância constante em todos os níveis da variável independente, os testes de significância podem produzir resultados distorcidos e não confiáveis.
	- A homocedasticidade é necessária para garantir que as previsões e intervalos de confiança gerados pelo modelo de regressão sejam válidos. Se os erros do modelo variarem de forma não constante, as previsões e intervalos de confiança podem ser imprecisos e não confiáveis.
	- Em resumo, a homocedasticidade é uma suposição crítica da regressão linear porque afeta a validade dos testes estatísticos, a precisão das estimativas dos parâmetros do modelo, a interpretabilidade dos coeficientes de regressão e a validade das previsões e intervalos de confiança. Assumir a homocedasticidade permite que os resultados da regressão sejam confiáveis e interpretáveis.
</details>
<details>
<summary>**Normalidade dos Resíduos:** Os resíduos devem seguir uma distribuição normal.</summary>
	- A normalidade dos resíduos é essencial para garantir a validade dos testes de hipóteses e intervalos de confiança associados aos coeficientes de regressão. Muitos testes estatísticos pressupõem que os erros do modelo têm uma distribuição normal. Se os resíduos não forem normalmente distribuídos, os testes de significância podem produzir resultados distorcidos e não confiáveis.
	- A normalidade dos resíduos é importante para garantir que as previsões e intervalos de confiança gerados pelo modelo de regressão sejam válidos. Se os resíduos não seguirem uma distribuição normal, as previsões e intervalos de confiança podem ser imprecisos e não confiáveis.
	- Em resumo, a normalidade dos resíduos é uma suposição crítica da regressão linear porque afeta a validade dos testes estatísticos, a eficiência dos estimadores, a validade das previsões e intervalos de confiança e as propriedades dos métodos de estimação. Assumir a normalidade dos resíduos permite que os resultados da regressão sejam confiáveis e interpretáveis.
</details>
<details>
<summary> **Ausência de multicolinearidade**: Se houver várias variáveis independentes no modelo, elas não devem estar altamente correlacionadas entre si. Multicolinearidade pode levar a estimativas imprecisas dos coeficientes de regressão.</summary>
	- Quando existe multicolinearidade entre as variáveis independentes, ou seja, quando duas ou mais variáveis independentes estão altamente correlacionadas entre si, pode ser difícil determinar com precisão o efeito de cada variável independente sobre a variável dependente. Isso pode levar a estimativas imprecisas ou instáveis dos coeficientes de regressão.
	- A multicolinearidade pode obscurecer a importância relativa das variáveis independentes no modelo. Isso dificulta a identificação das variáveis que são verdadeiramente importantes para explicar as variações na variável dependente.
	- Em resumo, a ausência de multicolinearidade é uma suposição crítica na regressão linear porque afeta a precisão das estimativas dos coeficientes, a interpretação do modelo, a identificação de variáveis importantes e a estabilidade das estimativas. Assumir a ausência de multicolinearidade permite que os resultados da regressão sejam mais confiáveis e interpretações mais precisas.
	</details>
# Minha fala
---
- Me introduzo e tal
- Vou falar sobre as assunções da regressão linear
	- Primeiro, falando sobre o que uma assunção
		- Assunção basicamente refere-se à uma condição que deve ser aceita como verdadeira para que, nesse contexto, aconteça a validação estatística; então podemos entender como as premissas da regressão linear
- No total existem 5 assunções, a primeira delas é a linearidade
	- A linearidade diz que a relação entre a variável dependente a independente deve ser linear
		- Variável dependente: é a do eixo Y e remete à variável que está sendo medida/observada
		- Variável independete: é a do eixo X e remete à variável que está sendo manipulada ou controlada pelo pesquisador
	- Dando o exemplo: vamos observar a variável dependente preço e independente metros quadrados, à medida que eu manipulo o metro quadrado os preços são alterados
	- No entanto, é importante notar que, embora a regressão linear exija uma relação linear entre as variáveis, isso não significa que todas as relações reais precisam ser estritamente lineares
- Normalidade dos Resíduos
	- Resíduos são basicamente as diferenças entre os valores observados (reais) e os valores preditos (estimados)
	- Muitos testes estatísticos pressupõem que os erros do modelo têm uma distribuição normal. Se os resíduos não forem normalmente distribuídos, os testes de significância podem produzir resultados distorcidos e não confiáveis
	- Assumir a normalidade dos resíduos permite que os resultados da regressão sejam confiáveis e interpretáveis
- Homoscedasticidade
	- Homoscedasticidade - propriedade de apresentar a mesma variação ou dispersão estatística
	- Se os resíduos do modelo não tiverem variância constante em todos os níveis da variável independente, os testes de significância podem produzir resultados distorcidos e não confiáveis.
	- Se os resíduos do modelo variarem de forma não constante, as previsões e intervalos de confiança podem ser imprecisos e não confiáveis.
- O próximo é a independencia das observações
	- As observações devem ser independentes umas das outras
	- permite que os resultados obtidos a partir do modelo de regressão sejam generalizados para a população de interesse. Se as observações não forem independentes, os resultados podem se aplicar apenas ao conjunto específico de observações e não podem ser generalizados para a população mais ampla
	- Se as observações não são independentes, os erros (resíduos) podem estar correlacionados. Isso pode levar a estimativas viesadas e imprecisas dos coeficientes de regressão
- Ausência de multicolinearidade
	- multicolinearidade basicamente significa uma alta correlação entre duas variáveis independentes, o que dificulta determinar com precisão o efeito de cada variavel independente possui sobre a variavel independente; levando a estimativas imprecisas ou instaveis
	- Assumir a ausência de multicolinearidade permite que os resultados da regressão sejam mais confiáveis e interpretações mais precisas.
