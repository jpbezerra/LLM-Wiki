# Projeto Aprendizagem de Máquina

---
## Documentação do Projeto
[Base de dados e documentação do projeto (link externo)](https://www.notion.so/2ab237a4194580b3a56dfcc65b643d73)
## Bases de Dados
[https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
[https://www.unb.ca/cic/datasets/index.html](https://www.unb.ca/cic/datasets/index.html)
## Conversa com o Gemini
[Link para a conversa (externo)](https://www.notion.so/2ab237a4194580b3a56dfcc65b643d73)
## Etapas
### Etapa 1: Setup, Infraestrutura e Dados {toggle="true"}
	**O que é:** A fundação do projeto. É onde garantimos que o ambiente é reprodutível e onde transformamos dados brutos em dados prontos para o aprendizado.<br>**Por que é crítica?** Se os dados entrarem "sujos" no modelo, a saída será inútil (*Garbage In, Garbage Out*). Além disso, erros aqui (como vazamento de dados) podem invalidar todo o projeto.
	- **Setup do GitHub:** Garante que se o computador de alguém quebrar, o código está salvo. O `requirements.txt` garante que todos usem as mesmas versões de bibliotecas.
	- **EDA (Análise Exploratória):** É o momento de "conhecer o inimigo". Em detecção de fraude, você precisa saber quão raro é o evento (ex: 0.1% ou 0.01%?). Isso define qual estratégia de amostragem usar.
	- **Pré-processamento (Scaling):** Modelos de distância (como KNN e Autoencoders) falham se os dados não estiverem na mesma escala (ex: idade vai de 0-100, salário vai de 0-10000). O `StandardScaler` resolve isso.
	- **Split Estratificado:** Diferente de um split aleatório comum, o *StratifiedKFold* garante que a proporção de fraudes (ex: 0.5%) seja mantida tanto no treino quanto no teste. Sem isso, você poderia criar um teste sem nenhuma fraude por azar.
### Etapa 2: Modelagem Clássica {toggle="true"}
	**O que é:** Implementação de algoritmos tradicionais de Machine Learning para estabelecer uma "linha de base" (baseline).<br>**Por que é crítica?** Você precisa de um ponto de comparação. Se um modelo simples (Isolation Forest) funcionar bem e rápido, talvez não seja necessário gastar recursos computacionais com Deep Learning complexo.
	- **Isolation Forest (Probabilístico):** Funciona isolando observações. A lógica é: anomalias são "fáceis" de isolar (precisam de poucos cortes numa árvore de decisão), enquanto dados normais são difíceis. É o padrão ouro para esse tipo de problema.
	- **LOF / KNN (Distância/Densidade):** Baseiam-se na premissa de que anomalias estão "longe" dos vizinhos ou em áreas de baixa densidade. São ótimos para entender a geometria dos dados, mas podem ser lentos em datasets gigantes.
	- **Feature Selection:** Em anomalias, muitas colunas podem ser ruído. Remover colunas irrelevantes ajuda os modelos de distância a "enxergarem" melhor os outliers.
### Etapa 3: Deep Learning & Avançado {toggle="true"}
	**O que é:** Utilização de Redes Neurais Artificiais para aprender padrões complexos e não-lineares nos dados.<br>**Por que é crítica?** É um requisito do projeto, mas também é onde conseguimos capturar fraudes muito sofisticadas que modelos lineares não pegam.
	- **Autoencoder:** Não é um classificador comum.
		1. Ele tenta comprimir o dado (Encoder) e reconstruí-lo (Decoder).
		2. Nós o treinamos **apenas com dados normais**. Ele fica "expert" em reconstruir transações legítimas.
		3. Quando chega uma **fraude**, ele não sabe como reconstruir, gerando um **Erro de Reconstrução** alto.
		4. Esse erro é a nossa pontuação de anomalia.
	- **Threshold (Limiar):** É a linha de corte. "Se o erro for maior que X, é fraude". Definir esse X é o grande desafio desta etapa.
### Etapa 4: Avaliação e Validação Estatística {toggle="true"}
	**O que é:** A fase científica onde provamos matematicamente a qualidade dos modelos.<br>**Por que é crítica?** Em dados desbalanceados, a **Acurácia mente**. Dizer "acertei 99%" é fácil se 99% dos dados são normais. Precisamos provar que o modelo sabe achar a agulha no palheiro.
	- **Métricas de Desbalanceamento:**
		- **Recall (Revocação):** De todas as fraudes que existem, quantas eu peguei? (Vital para segurança/bancos).
		- **Precision (Precisão):** Das que eu chamei de fraude, quantas eram realmente fraude? (Evita bloquear o cartão do cliente à toa).
		- **F1-Score:** A média harmônica entre os dois acima.
		- **AUC-ROC:** Mede a capacidade de separação entre classes independente do threshold escolhido.
	- **Teste de Significância:** Se o Modelo A tem F1-Score de 0.85 e o Modelo B tem 0.84, a diferença é real ou sorte? Testes como *Wilcoxon* ou *T-test* respondem isso (obrigatório para nota máxima na academia).
### Etapa 5: Entregáveis e Documentação {toggle="true"}
	**O que é:** A tradução do código e números para linguagem humana e acadêmica.<br>**Por que é crítica?** O professor e a banca não vão rodar seu código linha por linha. Eles vão julgar seu trabalho pelo que lerem no PDF e virem nos slides.
	- **Relatório:** Deve contar uma história: "Tínhamos esse problema, tratamos os dados assim, testamos X e Y, e descobrimos que Z é melhor por causa disso". A justificativa vale mais que o código.
	- **Repositório Limpo:** Código comentado e organizado mostra profissionalismo. Um `README` explicando "Como rodar" é essencial.
	- **Slides:** Devem ser visuais. Menos texto, mais gráficos (ROC Curves, Matrizes de Confusão) e conclusões diretas sobre o impacto do modelo no negócio (ex: "Detectamos 80% das fraudes reduzindo o prejuízo em X%").
