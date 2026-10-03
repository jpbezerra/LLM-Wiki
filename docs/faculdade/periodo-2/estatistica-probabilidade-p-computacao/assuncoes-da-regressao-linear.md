# Assunções da regressão linear

Uma **assunção** (ou pressuposto) refere-se a uma condição que deve ser aceita como verdadeira para que, em determinado contexto, a validação estatística do modelo seja legítima. No caso da regressão linear, essas assunções são as premissas que sustentam a confiabilidade dos coeficientes estimados, dos testes de significância e dos intervalos de confiança construídos a partir do modelo. São, no total, cinco assunções principais: linearidade, independência das observações, homocedasticidade, normalidade dos resíduos e ausência de multicolinearidade.

## Linearidade

A relação entre a variável dependente e a variável independente deve ser **linear**.

- **Variável dependente** — no contexto da regressão linear, é representada por $Y$, e é a variável que está sendo medida ou observada (fica no eixo Y).
- **Variável independente** — representada por $X$, é manipulada ou controlada pelo pesquisador (fica no eixo X).

!!! example
    Analisando os efeitos do tempo de estudo (variável independente) no desempenho acadêmico (variável dependente); ou, de forma equivalente, observando a variável dependente "preço" e a variável independente "metros quadrados" — à medida que o metro quadrado é manipulado, os preços se alteram.

Em outras palavras, para cada unidade de mudança na variável independente, espera-se que a mudança na variável dependente seja constante. É importante notar que, embora a regressão linear exija uma relação linear entre as variáveis, isso não significa que todas as relações reais precisem ser estritamente lineares — apenas que o modelo linear é uma aproximação razoável dentro do intervalo de dados estudado.

## Independência das observações

As observações devem ser **independentes** umas das outras.

Essa independência é essencial por diversos motivos:

- Garante a validade estatística dos testes de hipóteses e dos intervalos de confiança associados aos coeficientes de regressão. Se as observações não forem independentes, os testes estatísticos podem produzir resultados distorcidos e não confiáveis.
- É necessária para obter estimativas precisas e não tendenciosas dos parâmetros do modelo. Se as observações estiverem correlacionadas ou dependentes entre si, as estimativas dos coeficientes podem ser enviesadas e imprecisas — os erros (resíduos) podem estar correlacionados, o que leva a estimativas viesadas e imprecisas dos coeficientes de regressão.
- Permite que os resultados obtidos a partir do modelo sejam generalizados para a população de interesse. Se as observações não forem independentes, os resultados podem se aplicar apenas ao conjunto específico observado, sem poder ser generalizados para a população mais ampla.

Em resumo, a independência das observações é uma suposição crítica porque afeta a validade estatística, a precisão da estimativa dos parâmetros e a generalização dos resultados. Assumi-la permite que os resultados da regressão sejam confiáveis e aplicáveis a uma ampla gama de situações.

## Homocedasticidade

A **homocedasticidade** é a propriedade de apresentar a mesma variação ou dispersão estatística: a variância dos resíduos (erros) deve ser constante em todos os níveis das variáveis independentes.

- É essencial para garantir a validade dos testes estatísticos associados aos coeficientes de regressão. Se os erros do modelo não tiverem variância constante em todos os níveis da variável independente, os testes de significância podem produzir resultados distorcidos e não confiáveis.
- É necessária para garantir que as previsões e intervalos de confiança gerados pelo modelo sejam válidos. Se os erros variarem de forma não constante (fenômeno chamado de **heterocedasticidade**), as previsões e intervalos de confiança podem ser imprecisos e não confiáveis.

Em resumo, a homocedasticidade afeta a validade dos testes estatísticos, a precisão das estimativas dos parâmetros do modelo, a interpretabilidade dos coeficientes de regressão e a validade das previsões e intervalos de confiança. Assumi-la permite que os resultados da regressão sejam confiáveis e interpretáveis.

## Normalidade dos resíduos

Os **resíduos** — basicamente, as diferenças entre os valores observados (reais) e os valores preditos (estimados) pelo modelo — devem seguir uma **distribuição normal**.

- Muitos testes estatísticos pressupõem que os erros do modelo têm distribuição normal. Se os resíduos não forem normalmente distribuídos, os testes de significância podem produzir resultados distorcidos e não confiáveis.
- É importante para garantir que as previsões e intervalos de confiança gerados pelo modelo sejam válidos. Se os resíduos não seguirem uma distribuição normal, as previsões e intervalos de confiança podem ser imprecisos e não confiáveis.

Em resumo, a normalidade dos resíduos é uma suposição crítica da regressão linear porque afeta a validade dos testes estatísticos, a eficiência dos estimadores, a validade das previsões e intervalos de confiança, e as propriedades dos métodos de estimação. Assumi-la permite que os resultados da regressão sejam confiáveis e interpretáveis.

## Ausência de multicolinearidade

Quando há várias variáveis independentes no modelo, elas não devem estar altamente correlacionadas entre si. A **multicolinearidade** — alta correlação entre duas ou mais variáveis independentes — pode levar a estimativas imprecisas ou instáveis dos coeficientes de regressão.

- Quando existe multicolinearidade, torna-se difícil determinar com precisão o efeito de cada variável independente sobre a variável dependente, o que leva a estimativas imprecisas ou instáveis dos coeficientes.
- A multicolinearidade pode obscurecer a importância relativa das variáveis independentes no modelo, dificultando a identificação das variáveis que são verdadeiramente importantes para explicar as variações na variável dependente.

Em resumo, a ausência de multicolinearidade é uma suposição crítica porque afeta a precisão das estimativas dos coeficientes, a interpretação do modelo, a identificação de variáveis importantes e a estabilidade das estimativas. Assumi-la permite que os resultados da regressão sejam mais confiáveis e as interpretações, mais precisas.

!!! note "Origem do conteúdo"
    Este material também serviu de roteiro para uma apresentação oral sobre o tema (introdução ao conceito de assunção, seguida da explicação de cada uma das cinco premissas acima, nessa mesma ordem de conteúdo). O texto acima já incorpora e unifica tanto as anotações de estudo quanto o roteiro da fala, sem perda de conteúdo.
