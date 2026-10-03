# Projeto Aprendizagem de Máquina

---

## Documentação do Projeto

[[https://docs.google.com/document/d/1-aDrRsSokbBwam7-Af1D9OKU7SacZxWBpkZyhEP_2os/edit?usp=sharing](https://docs.google.com/document/d/1-aDrRsSokbBwam7-Af1D9OKU7SacZxWBpkZyhEP_2os/edit?usp=sharing)](https://docs.google.com/document/d/1-aDrRsSokbBwam7-Af1D9OKU7SacZxWBpkZyhEP_2os/preview?usp=sharing)

[Google Colab](https://colab.research.google.com/github/CesarC15/projetoML/blob/main/src/deteccao_anomalias.ipynb)

## Bases de Dados

[https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

[https://www.unb.ca/cic/datasets/index.html](https://www.unb.ca/cic/datasets/index.html)

## Conversa com o Gemini

[‎Gemini - direct access to Google AI](https://gemini.google.com/share/1944994aa1b8)

## Contexto do projeto

O projeto é um sistema de **detecção de anomalias/fraudes** em transações, combinando modelos clássicos de ML (Isolation Forest, KNN/LOF) com um Autoencoder, e validado estatisticamente contra o problema de classes extremamente desbalanceadas típico desse domínio. As etapas abaixo documentam o raciocínio por trás de cada fase do trabalho — não só o que foi feito, mas por que era necessário.

## Etapas

### Etapa 1 — Setup, Infraestrutura e Dados

É a fundação do projeto: garantir que o ambiente seja reprodutível, e transformar dados brutos em dados prontos para o aprendizado.

!!! warning "Por que esta etapa é crítica"
    Se os dados entrarem "sujos" no modelo, a saída será inútil (*Garbage In, Garbage Out*). Além disso, erros aqui — como vazamento de dados (*data leakage*) — podem invalidar todo o restante do projeto.

- **Setup do GitHub**: garante que, se o computador de alguém quebrar, o código continua salvo. O `requirements.txt` garante que todos usem as mesmas versões de bibliotecas.
- **EDA (Análise Exploratória)**: o momento de "conhecer o inimigo". Em detecção de fraude, é preciso saber quão raro é o evento (0.1%? 0.01%?) — isso é o que define qual estratégia de amostragem usar depois.
- **Pré-processamento (Scaling)**: modelos baseados em distância (como KNN e Autoencoders) falham se os dados não estiverem na mesma escala (ex: idade varia de 0–100, salário de 0–10000). O `StandardScaler` resolve isso.
- **Split estratificado**: diferente de um split aleatório comum, o `StratifiedKFold` garante que a proporção de fraudes (ex: 0.5%) seja mantida tanto no treino quanto no teste. Sem isso, seria possível, por azar, criar um conjunto de teste sem nenhuma fraude.

### Etapa 2 — Modelagem Clássica

Implementação de algoritmos tradicionais de Machine Learning para estabelecer uma linha de base (*baseline*).

!!! warning "Por que esta etapa é crítica"
    É preciso ter um ponto de comparação. Se um modelo simples (Isolation Forest) já funcionar bem e rápido, talvez não seja necessário gastar recursos computacionais com Deep Learning complexo.

- **Isolation Forest (probabilístico)**: funciona isolando observações — a lógica é que anomalias são "fáceis" de isolar (precisam de poucos cortes em uma árvore de decisão), enquanto dados normais são difíceis de isolar. É considerado o padrão-ouro para esse tipo de problema.
- **LOF / KNN (distância/densidade)**: baseiam-se na premissa de que anomalias estão "longe" dos vizinhos, ou em áreas de baixa densidade. São ótimos para entender a geometria dos dados, mas podem ser lentos em datasets gigantes.
- **Feature Selection**: em problemas de anomalia, muitas colunas podem ser apenas ruído. Remover colunas irrelevantes ajuda os modelos de distância a "enxergarem" melhor os outliers reais.

### Etapa 3 — Deep Learning e Avançado

Utilização de redes neurais artificiais para aprender padrões complexos e não lineares nos dados.

!!! warning "Por que esta etapa é crítica"
    É um requisito do projeto, mas também é onde se consegue capturar fraudes muito sofisticadas, que modelos lineares não pegam.

**Autoencoder**: não é um classificador comum — funciona de forma indireta.

1. Ele tenta comprimir o dado (encoder) e reconstruí-lo (decoder).
2. É treinado **apenas com dados normais**, tornando-se "especialista" em reconstruir transações legítimas.
3. Quando chega uma **fraude**, ele não sabe reconstruí-la bem, gerando um **erro de reconstrução** alto.
4. Esse erro de reconstrução é a própria pontuação de anomalia do modelo.

**Threshold (limiar)**: é a linha de corte — "se o erro for maior que X, é fraude". Definir esse $X$ é o grande desafio desta etapa.

### Etapa 4 — Avaliação e Validação Estatística

A fase científica onde se prova matematicamente a qualidade dos modelos treinados.

!!! warning "Por que esta etapa é crítica"
    Em dados desbalanceados, a **acurácia mente**. Dizer "acertei 99%" é fácil se 99% dos dados já são normais por natureza — é preciso provar que o modelo de fato sabe achar a agulha no palheiro.

| Métrica | O que mede | Por que importa aqui |
|---|---|---|
| **Recall (Revocação)** | De todas as fraudes que existem, quantas eu peguei? | Vital para segurança/bancos — uma fraude não detectada é um prejuízo direto |
| **Precision (Precisão)** | Das que eu chamei de fraude, quantas eram realmente fraude? | Evita bloquear o cartão do cliente à toa |
| **F1-Score** | Média harmônica entre Recall e Precision | Balanceia os dois trade-offs acima |
| **AUC-ROC** | Capacidade de separação entre classes, independente do threshold escolhido | Permite comparar modelos sem travar numa escolha específica de corte |

**Teste de significância**: se o Modelo A tem F1-Score de 0.85 e o Modelo B tem 0.84, essa diferença é real ou pode ser só sorte da divisão dos dados? Testes como *Wilcoxon* ou *t-test* respondem a essa pergunta — e são exigidos para nota máxima na avaliação acadêmica.

### Etapa 5 — Entregáveis e Documentação

A tradução do código e dos números para linguagem humana e acadêmica.

!!! warning "Por que esta etapa é crítica"
    O professor e a banca não vão rodar o código linha por linha — vão julgar o trabalho pelo que lerem no PDF e virem nos slides.

- **Relatório**: deve contar uma história — "tínhamos esse problema, tratamos os dados assim, testamos X e Y, e descobrimos que Z é melhor por causa disso". A justificativa vale mais do que o código em si.
- **Repositório limpo**: código comentado e organizado demonstra profissionalismo. Um `README` explicando "como rodar" é essencial.
- **Slides**: devem ser visuais — menos texto, mais gráficos (curvas ROC, matrizes de confusão) e conclusões diretas sobre o impacto do modelo no negócio (ex: "detectamos 80% das fraudes, reduzindo o prejuízo em X%").

[Kanban](../../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/projeto-aprendizagem-de-maquina/Kanban%202ab237a419458087a8e0d7c3f7d754b9.csv)
