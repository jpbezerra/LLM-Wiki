# APRENDIZAGEM DE MÁQUINA E CIÊNCIA DE DADOS

[Projeto Aprendizagem de Máquina](aprendizagem-de-maquina-e-ciencia-de-dados/projeto-aprendizagem-de-maquina.md)

---

- História da Inteligência Artificial
    - Fundamentos
        - **1947 – McCulloch–Pitts**: primeiro modelo matemático de um neurônio artificial, base conceitual das redes neurais.
        - **1950 – Teste de Turing**: propõe avaliar inteligência por comportamento indistinguível do humano em diálogo.
        - **1956 – Workshop de Dartmouth**: “nascimento” formal da IA como campo; define ambições e agenda de pesquisa.
        - **1957 – Perceptron**: primeiro algoritmo prático para aprender classificadores binários; inaugura o entusiasmo com redes neurais.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image.png)
        
    - Desafios e primeiro inverno
        - 1966 – ALPAC: relatório do governo dos EUA conclui resultados fracos em tradução automática → cortes de verbas.
        - 1969 – Críticas ao Perceptron (Minsky & Papert): mostram limites das redes de uma camada → esfriamento do interesse em neurais e redução de investimentos (primeiro “AI winter”).
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%201.png)
        
    - Reacensão com aprendizado em múltiplas camadas
        - **Backpropagation**: populariza o treino eficaz de redes com várias camadas, reabrindo o caminho para modelos mais expressivos.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%202.png)
        
    - Era das vitórias de sistemas especializados
        - **Deep Blue x Kasparov**: computador da IBM derrota o campeão mundial de xadrez; prova de força de IA simbólica/heurística em domínios restritos.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%203.png)
        
    - Explosão do deep learning e aplicações de consumo
        - **2011–2016 – Assistentes de voz**: Siri (2011), Alexa (2014), Google Assistant (2016) levam IA ao celular.
        - **2012 – ImageNet/AlexNet**: redes profundas superam largamente concorrentes em visão computacional, o “big bang” da era do deep learning.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%204.png)
        
    - Sistemas autônomos e percepção avançada
        - **2014–2016 – Carros autônomos**: avanços de Tesla/Waymo popularizam a ideia de veículos com percepção e decisão assistidas por IA.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%205.png)
        
    - Geração de linguagem em larga escala
        - **ChatGPT-3**: acesso massivo a modelos de linguagem capazes de produzir textos fluentes e contextuais, democratizando o uso de IA generativa.
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%206.png)
        
- Machine Learning
    - Transição do rule-based para data-driven/ML
        - Antigamente os sistemas eram baseado em regras feitas à mão (rule-based)
            - É fornecido o texto e um conjunto de regras e o problema devolve um rótulo
            - Problema: não escala nem generaliza, dá muito trabalho amnter, é frágil a exceções, depende de especialistas e quebra quando o domínio muda
            
            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%207.png)
            
        - Para sanar essa dor, a lógica foi invertida: agora é preciso fornecer os dados rotulados (texto + label) e o programa aprende as regras automaticamente
            - Isso é machine learning supervisionado
            - Como vantagem as regras emergem dos dados, fazendo com que o modelo se adapte melhor, generalizando novos casos e reduzindo a engenharia manual
    - Machine Learning é o campo de estudo que dá ao computador a habilidade de aprender sem ser explicitamente programado
    - Dados
        - Informações relevantes sobre determinado objeto que pode ser usado para fins de interpretação
            - São basicamente vetores de informações
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%208.png)
                
        - Tipos
            - Estruturado
                - São organizados em um esquema rígido e predefinido
                - Podem ser qualitativos ou quantitativos
                - Aplicações em ML e análise quantitativa
            - Não Estruturado
                - Imagens, texto, áudio, vídeo
                - Não possuem um esquema fixo ou formato predefinido, são flexíveis e dinâmicos
                - Mais complexos de analisar
                - Aplicações em NLP e genIA
    - Funcionamento
        - Dados de exemplo (Treinamento)
            - Entradas (X): o que o modelo vê
            - Saídas/Rótulos (y): o que queremos prever
        - Algoritmo de aprendizagem
            - Escolha de um modelo: uma forma matemática com parâmetros ajustáveis
            - Definição de uma função de perda que mede
                - Medição do erro entre a previsão e orótulo
            - Otimizador: algoritmo que ajusta os parâmetros para minimizar a perda
            - Treinamento do modelo
                1. Pré-processamento/featurização
                    - Limpar dados nulos, padronizar escalas
                    - Criação de novas features a partir das existentes
                    - Deixar os dados prontos para que um modelo de ML possa usá-los
                2. Divisão dos dados
                    - Com os dados limpos e prontos para treino, é preciso dividí-los em treino (para o modelo aprender, 70-80%), validação (escolher hiperparâmetros, 10-15%) e teste (medir desempenho final e generalização, 10-15%)
                3. Epochs
                    - O modelo vê lotes de exemplos (batches), calcula a perda, computa o gradiente (o quanto cada parâmetro contribuiu para o erro) e dá um passo que reduz a perda
                        - Quando a perda de validação para de melhorar ou após um certo número de epochs, o modelo para
            - Parâmetros vs Hiperparâmetros
                - Parâmetros → são aprendidos pelo modelo durante o treinamento
                    - Representam os conhecimentos adquiridos pelo modelo ao analisar o conjunto de dados de treinamento
                    - A qualidade dos dados de treinamento afeta diretamente os valores e a eficácia dos parâmetros
                - Hiperparâmetros → são definidos manualmente antes do início do treinamento
                    - São configurações externas que controlam o comportamento do algoritmo de aprendizado
                    - São definidos manualmente para guiar o processo de otimização
                    - A afinação dos hiperparâmetros é a busca pela melhor combinação de valores para otimizar a performance
                    - São melhorados continuamente através de múltiplos experimentos de treinamento para gerar os melhores resultados
                        - Isso é feito por meio do Hyperparameter Tuning, que utiliza o conjunto de validação para decidir qual combinação de hiperparâmetros gera o melhor modelo
        - Modelo treinado
            - Basicamente é o conhecimento e os padrões que o algoritmo conseguiu extrair dos dados
                - O modelo é avaliado por meio de métricas usando o conjunto de teste
            - Novos dados (dados que o modelo nunca viu) são coletados e analisados, realizando predições com base nos padrões que aprendeu durante o treinamento
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%209.png)
        
        - Em resumo, o processo de funcionamento do Machine Learning se inicia na coleta de dados, depois o uso de um algoritmo para aprender padrões desses dados gerando um modelo treinado para que este modelo seja usado para fazer previsões sobre novos dados
    - Machine Learning vs Deep Learning
        - A maior diferença é que o Machine Learning usurfrui de dados estruturados, enquanto que Deep Learning usurfrui de dados estruturados e não-estruturados
            - Algoritmos de Machine Learning consegue trabalhar com dados não-estruturados, mas costumam não funcionar bem pois não conseguem extrair valor deles em seu formato bruto
            - Demandam processo de Engenharia de Features
                - Engenharia de Features
                    - Processo de criar, modificar, combinar e selecionar features fazendo com que estas features sejam mais fáceis para um algoritmo entender e usá-las para fazer previsões
                    - Possui o principal objetivo de aumentar o poder preditivo do modelo
                    - Uma das formas de realizar isso é por meio da Feature Extraction, que é o processo de transfomar dados brutos e complexos em um conjunto menor e mais gerenciável de features
                        - Geralmente é feito de forma automatizada
                        - É muito comum com dados não-estruturados
                        - O objetivo do Feature Extraction é reduzir a dimensionalidade (número de variáveis) sem perder informações essenciais
        - Além disso, no Machine Learning a Feature Extraction é feita de forma manual, enquanto que no Deep Learning isso é feito via redes neurais profundas (de forma automatizada e simplificada)
            - Essas redes neurais lidam melhor com dados não estruturados e podem dispensar o processo de Engenharia de Features
                - As primeiras camadas das redes neurais extraem features automaticamente como um resultado do próprio processo de aprendizado
            - Demandam maior quantidade de dados
            
            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2010.png)
            
            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2011.png)
            
    - Taxonomias
        - Tipos de Supervisão
            - Classifica a natureza dos dados de treinamento
            - Aprendizado Supervisionado
                - É basicamente um problema de inferência indutiva, na qual com base em um conjunto finito de dados buscamos criar uma regra geral que se aplique a todos os casos possíveis (incluindo os não observados)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2012.png)
                    
                - Classificação
                    - É o problema de identificar a qual de um conjunto de categorias uma nova observação pertence com base em um treinamento realizado com dados cujas categorias de pertencimento já são conhecidas
                    - Os algoritmos de classificação tentam encontrar a fronteira de decisão, uma hipersuperfície que separa as diferentes classes no espaço de features
                        - O aprendizado consiste em ajustar a forma e a posição dessa fronteira para minimizar os erros de classificação nos dados de treinamento
                    - Classificação binária: apenas duas classes, na qual elas são frequentemente rotuladas como positiva (1) e negativa (0)
                    - Classificação Multiclasse: existem mais de duas classes e cada instância pertence a exatamente uma classe
                        - As classes são mutuamente exclusicas
                    - Classificação Multirrótulo: uma única instância pode ser associada a múltiplos rótulos simultaneamente, sem exclusividade mútua
                - Regressão
                    - Modela a relação entre um conjunto de features (variáveis independentes) e uma variável dependente contínua
                        - O objetivo é encontrar a curva que melhor se ajusta à dispersão dos pontos de dados
                    - Regressão Linear: relaciona as features e a saída de forma linear
                    - Regressão Polinomial: captura relações não-lineares, criando novas features que são potências ou interações das features originais
                    - Regressões Linearizadas com Regularização: adição de um termo de penalidade de custo do modelo linear para combater o overfitting e a multicolinearidade (features altamente correlacionadas)
                        - Regressão Ridge: adiciona uma penalidade proporcional ao quadrade da magnetude dos coeficientes, forçando-os a serem pequenos, mas não os zerando
                        - Regressão Lasso: adiciona uma penalidade proporcional ao valor absoluto dos coeficientes, podendo forçar alguns coeficientes a serem zero, funcionando como um método de seleção automática de features
                    - Modelos Baseados em Árvores
                        - Árvore de Decisão para Regressão: particiona o espaço de features recursivamente, mas em vez de buscar a pureza da classe em cada folha busca minimizar a variância dos valores de y
                            - A predição para uma nova instância é a média dos valores de y de todas as amostras de treinamento que caem naquela folha
                        - Random Forest e Gradient Boosting: combinam múltiplas árvores de decisão para criar modelos extremamente poderosos e robustos, que frequentemente representam o estado da arte para dados tabulares
            - Aprendizado Não-Supervisionado
                - O objetivo é modelar a estrutura subjacente ou a distribuição dos dados, pois não há rótulos e nem respostas corretas para treinar o modelo
                    - O objetivo é mergulhar nos dados e descobrir por conta própria a estrutura, padrões e relações ocultas que existem neles
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2013.png)
                    
                - Categorias
                    - Clustering → objetivo de agrupar dados semelhantes em clusters (grupos)
                        - Os pontos de dados dentro de um mesmo cluster devem ser muito parecidos entre si e muito diferente dos pontos de dados de outros clusters
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2014.png)
                            
                        - Avaliação
                            - Métricas Externas
                                - Usadas quando temos rótulos verdadeiros (requerem Ground Truth)
                                - Acurácia de Clusterização
                                    - Requer o mapeamento dos clusters encontrados para as classes reais (via matriz de confusão) para maximizar a correspondência
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2015.png)
                                        
                                - Pureza
                                    - Para cada cluster, identifica-se a classe mais frequente
                                    - A pureza é a média ponderada dessas frequências
                                    - Tende a aumentar com o número de clusters (pureza é 1 se cada ponto for seu próprio cluster)
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2016.png)
                                        
                                - Informação Mútua Normalizada (NMI)
                                    - Baseada em entropia
                                    - Mede a informação compartilhada entre as atribuições de clusters e os rótulos reais, normalizada para estar entre 0 e 1
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2017.png)
                                        
                                    - Penaliza subdivisões excessivas que não adicionam informação
                            - Métricas Internas
                                - Usadas na prática quando não há rótulos
                                - Coeficiente de Silhueta (Silhouette)
                                    - Combina coesão e separação
                                    - Para cada ponto i, calcula-se
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2018.png)
                                        
                                - O valor do coeficiente varia de -1 a +1
                                    - Valores próximos a +1 indicam que o ponto está bem agrupado e longe dos clusters vizinhos
                                    - Valores próximos a 0 indicam fronteiras sobrepostas
                                    - Valores negativos indicam atribuição errada
                    - Redução de Dimensionalidade → objetivo de reduzir o número de features, preservando o máximo de informação relevante possível
                        - Grandes quantidade de dimensões (features) pode tornar o treinamento de modelos lento, ineficiente e suscetível à maldição da dimensionalidade (dados se tornam muito esparsos)
                - A maior dificuldade do aprendizado não-supervisionado é avaliar o resultado do modelo, por causa da falta de rótulos
            - Aprendizado Semi-Supervisionado
                - É uma abordagem híbrida que busca combinar o melhor do aprendizado supervisionado e não-supervisionado
                - A essência é o modelo utilizar um grande volume de dados não rotulados para melhorar a performance de um modelo que foi treinado com um pequeno volume de dados rotulados
                    - Extrai o máximo de valor de dados baratos e não rotulados (já que dados rotulados são caros e difíceis de obter)
                - Funciona com base em suposições
                    - Suposição de continuidade (Smoothness Assumption) → pontos que estão próximos no espaço de features têm alta probabilidade de ter o mesmo rótulo, portanto, a informação do rótulo pode ser suavizada através das vizinhanças dos dados
                    - Suposição de Cluster (Cluster Assumption) → os dados tendem a formar clusters distintos, logo, pontos dentro do mesmo cluster têm alta probabilidade de ter o mesmo rótulo
                        - Logo, a fronteira de decisão entre as classes deve passar por regiões de baixa densidade
                    - Suposição de Manifold (Manifold Assumption) → embora os dados possam viver em um espaço de alta dimensão, eles na verdade residem em uma estrutura de dimensão muito menor (um manifold)
                        - O algoritmo pode explorar essa estrutura para fazer generalizações melhores
                - Técnicas
                    - Self-Training → consiste no treino de um modelo (com um pequeno conjunto de dados rotulados) na qual depois ele é usado para fazer previsões em dados não rotulados e pega as previsões em que o modelo está mais confiante e adiciona ao conjunto de treinamento (adiciona o par dado e pseudo-rótulo), realizando um retreinamento
                    - Modelos Generativos → tentam aprender a estrutura subjacente dos dados, usando todos os dados (rotulados e não rotulados) e em seguida usam os poucos dados rotulados para associar essa estrutura aos rótulos
                        - É basicamente primeiro aprender o mapa do território dos dados e depois usar os poucos pontos rotulados como legendas para esse mapa
                        - Modelam p(x) ou p(x, y)
                    - Graph-Based Methods → representam todo o conjunto de dados como um grafo, onde os nós são os pontos de dados (rotulados e não rotulados) e as arestas conectam pontos semelhantes
                        - Label Propagation →
            - Aprendizado Auto-Supervisionado (SSL)
                - Técnica que permitiu à IA aprender com a escala massiva de dados brutos no mundo, movendo o campo de modelos específicos para modelos generalistas com uma compreensão profunda e flexível de seus domínios
                - É uma abordagem na qual o aprendizado não supervisionado finge ser supervisionado, resolvendo o gargalo da rotulagem de forma com que os dados forneçam sua própria supervisão
                    - O gabarito dos rótulos vem da propria estrutura dos dados
                - Mecanismo
                    - Tarefa Pretexto (Pretext Task) → etapa de auto-supervisão, na qual um enorme volumes de dados não rotulados é coletado e é inventado uma tarefa artificial onde a resposta já está contida nos próprios dados
                        - O objetivo é que ao tentar resolver a tarefa o modelo aprenda representações ricas e úteis sobre os dados, e não se tornar bom em resolver a tarefa pretexto em si
                    - Tarefa Fim (Downstream Task) → depois que o modelo foi pré-treinado na tarefa pretexto com bilhões de exemplos não rotulados, ele desenvolveu um entendimento profundo da linguagem ou imagens
                        - Agora, pegamos esse modelo pré-treinado e o adaptamos para uma tarefa real com um pequeno conjunto de dados rotulados (Fine-Tuning, Ajuste Fino)
                - Quebra a dependência de dados rotulados por humanos, se tornando infinitamente escalável e permitindo a criação de modelos gigantes e de propósito geral
            - Aprendizado Por Reforço
                - Aprender através da experiência e da interação com um ambiente, sendo a forma mais próximo de como os humanos aprendem a tomar decisões no mundo real (tentativa e erro)
                - Componentes
                    - Agente (Agent) → a entidade que aprende e toma decisões
                    - Ambiente (Environment) → o mundo com o qual o agente interage
                    - Estado (S) → uma fotografia do ambiente em um determinado momento
                    - Ação (A) → uma das possíveis jogadas ou movimentos que o agente pode realizar em um estado
                    - Recompensa (R) → o feedback numérico que o agente recebe do ambiente após tomar uma ação
                - Funcionamento
                    - Observação → o agente observa o estado atual do ambiente
                    - Ação → com base no estado, o agente decide tomar uma ação
                    - Feedback → o ambiente reage à ação do agente, transitando para um novo estado e fornecendo um sinal de feedback ao agente, podendo ser de 3 tipos
                        - Recompensa (número positivo) → se a ação foi boa e o aproximou de seu objetivo
                        - Punição (número negativo) → se a ação foi ruim
                        - Neutro (zero) → se a ação não teve consequências imediatas
                    - Objetivo não é obter a maior recompensa imediata, mas sim maximizar a recompensa cumulativa total ao longo do tempo, pois isso força a pensar estrategicamente e a tomar ações que podem não ser boas no curto prazo, mas que levam a um resultado muito melhor no futuro
                - Abordagens
                    - Explotação → o agente decide tomar a ação que ele já sabe que lhe dará uma boa recompensa, com base em sua experiência passada
                    - Exploração → o agente decide tentar uma ação nova, que ele nunca tentou antes, para ver o que acontece
                        - A recompensa é incerta, mas pode descobrir uma estratégia ainda melhor
                    - Um bom agente de RL precisa equilibrar de forma inteligente a exploração (para descobrir novas e melhores estratégias) com a explotação (para usar o conhecimento que já adquiriu e garantir boas recompensas)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2019.png)
                
        - Tarefa
            - O tipo do problema a se resolver
        - Paradigma
            - Estratégia de aprendizado do modelo
            - Update → momento em que o modelo ajusta seus parâmetros internos (seu "conhecimento") com base em novas informações para melhorar seu desempenho
                - A forma como essa atualização acontece é o que diferencia fundamentalmente os paradigmas
            - Batch Learning (Offline)
                - Treinamento em todo conjunto de dados de uma vez
                - Update requer retreinamento completo
                - Estável
                - Não se adapta a novos dados
            - Online Learning
                - Treinamento com uma instância por vez
                - Update contínuo e incremental
                - Adapta rapidamente a novos dados (evita concept drift)
                - Menos estável, risco de treinamento com dados classificados incorretamente
            - Transfer Learning
                - Reutiliza aprendizado de tarefa relacionada
                - O conhecimento adquirido ao resolver uma tarefa pode ser útil para resolver outras, então ao invés de treinar um modelo do zero para resolver uma tarefa X, reutilizamos um modelo que já foi treinado na tarefa Y
            - Few-Shot Learning
                - Lida com poucos exemplos por classe, na qual o objetivo é treinar um modelo para reconhecer novas classes com apenas um punhado de exemplos
                    - Caso extremo de Transfer Learning
                - Envolve treinar um modelo em uma grande variedade de classes para que ele aprenda a aprender
                    - O objetivo é que ele aprenda a extrair as características mais discriminatórias de uma classe para que, ao ver um novo exemplo, ele possa generalizar rapidamente
            - Multi-Task Learning
                - Lida com múltiplas tarefas simultaneamente
                - O modelo geralmente tem uma "espinha dorsal" (shared layers) que aprende representações úteis para todas as tarefas, e depois "cabeças" específicas (task-specific layers) para cada tarefa
                    - Ao aprender as tarefas em conjunto, o modelo pode usar o sinal de aprendizado de uma tarefa para ajudar na generalização das outras
            - Eager Learning
                - Aprendizado durante fase de treinamento
                - Resulta em um modelo explícito
                - Predição rápida usando o modelo já treinado
                - Requer retreinamento
            - Lazy Learning
                - Aprendizado durante a predição
                - Não há modelo treinado, mas instâcias de treinamento que precisam ser armazenadas
                - Predição lenta
                - Facilmente adaptável para novos dados
            - Instance-based Learning
                - Este é um paradigma de aprendizado de máquina onde as predições são feitas com base na similaridade com instâncias armazenadas do conjunto de treinamento
                - Lazy Learning (Aprendizado Preguiçoso): Não constrói um modelo explícito durante a fase de treinamento
                - Memory-Based (Baseado em Memória): Armazena todas (ou parte) das instâncias de treinamento
                - Local Learning (Aprendizado Local): As decisões são tomadas com base em informações locais, ou seja, a vizinhança da nova consulta
                - Non-parametric (Não-paramétrico): Não assume uma forma específica para a função objetivo
                - Hipótese Central: A premissa é que "instâncias próximas no espaço de características tendem a ter rótulos similares"
        - Estratégia Temporal
            - Quando ocorre o aprendizado
        - Estratégia de Modelagem
            - Modelos Discriminativos
                - Aprendem fronteiras de decisão ou funções de mapeamento
                - Discriminam entre diferentes classes
                - Aprendem a modelar a probabilidade da variável de saída y (rótulo) condicionada pela variável de entrada x (features)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2020.png)
                    
            - Modelos Generativos
                - Aprendem distribuições conjuntas de probabilidade a fim de poderem gerar novos dados similares aos dados de treinamento
                - Modelam a probabilidade da variável de entrada x condicionada pela variável de saída y
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2021.png)
                    
        - Métricas de Avaliação
            - Matriz de Confusão
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2022.png)
                
                - Positivos: TP + FN
                - Negativos: TN + FP
            - Acurácia
                - Mede a performance geral do modelo, vendo a proporção de previsões corretas em relação ao total de previsões feitas
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2023.png)
                    
                - É útil quando as classes do seu dataset são bem balanceadas
            - Precisão
                - Mede o quão confiável é o modelo ao dizer sim, analisando a proporção entre as vezes em que acertou uma classe positiva em relação ao total de previsões para a classe positiva
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2024.png)
                    
                - Útil quando o custo de um falto positivo é alto
            - Recall
                - Mede quantos dos casos existentes são encontrados pelo modelo, ou seja, a proporção do quanto que o modelo acertou que algo é positivo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2025.png)
                    
                - Útil quando o custo do falso negativo é muito alto
            - F1-Score
                - Média harmônica entre precision e recall balanceia confiança e cobertura, ideal quando é preciso de um bom desempenho tanto em evitar alarmes falsos quanto em encontrar todos os casos positivos
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2026.png)
                    
            - Curva ROC (Receiver Operating Characteristic)
                - Gráfico que ilustra o desempenho de classificação em todos os limiares de classificação possíveis, mostrando o quão bom o modelo é em distinguir entre as classes positiva e negativa
                - Eixo X: taxa de falsos positivos (FPR)
                    - De todos os casos que eram realmente negativos, quantos o modelo conseguiu identificar corretamente
                    - FPR = FP / (FP + TN)
                    - Quanto mais próximo de 0, melhor
                - Eixo Y: taxa de verdadeiros positivos (TPR)
                    - É o recall, na qual quanto mais próximo de 1, melhor
                - Gráfico
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2027.png)
                    
                - AUC (Area Under the Curve)
                    - Métrica que mede a área sob a curva ROC, medindo a probabilidade de que o modelo classifique um exemplo positivo aleatório com uma pontuação mais alta do que um exemplo negativo aleatória
                    - Mede o quão bem o modelo consegue separar as duas classes
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2028.png)
                    
                - Threshold Choice
                    - É a escolha do ponto de corte que é usado para converter a saída de probabilidade do modelo em uma decisão final de sim ou não
                    - Ou seja, se o Threshold for de 0.5, então se a probabilidade for maior que 0.5 é sim, caso contrário, é não
                    - Estratégias para escolher o limiar
                        - Younden’s Index → ponto na curva ROC que está mais distante verticalmente da linha diagonal, encontrar o limiar que maximiza a diferença TPR - FPR (ótima escolha de forma geral, pois busca o ponto de maior poder discriminatório do modelo)
                        - Equal Error Rate (EER) → ponto na curva onde a taxa de falsos positivos é igual à taxa de falsos negativos (FPR = 1 - TPR), encontrando o limiar onde a chance de cometer um "alarme falso" é a mesma de "deixar um caso passar” (útil em problemas onde os dois tipos de erro têm custos semelhantes)
        - Overffiting vs Underfitting
            - Underfitting → quando modelos aprendem de menos
            - Overfitting → quando os modelos se especializam demais e perdem capacidade de generalização
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2029.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2030.png)
                
    - CRISP-DM
        - Framework estruturado para projetos de ciências de dados que é relevante em empresas tradicionais e indústrias reguladas, mas menos usados em tech companies e startups
        - Fases
            1. Business Understanding (Entendimento do Negócio)
                - Traduzir o problema de negócio para um problema técnico de ML
                - Estabelecer as métricas de sucesso (ex: reduzir churn usando classificação binária com F1-score > 0.8)
                - Identificar stakeholders e restrições (constraints)
            2. Data Understanding (Entendimento dos Dados)
                - Realizar a coleta inicial e descrição dos dados
                - Analisar a qualidade e a completude dos dados
                - Identificar padrões preliminares
                - Entregáveis incluem dicionário de dados e relatório de qualidade
            3. Data Preparation (Preparação dos Dados)
                - Esta é a fase que mais consome tempo, estimada entre 60-80% do total do projeto
                - Inclui Limpeza (tratar missing values, outliers, inconsistências), Transformação (normalização, encoding), Feature Engineering (criação de variáveis) e Integração de múltiplas fontes
            4. Modeling (Modelagem)
                - Seleção dos algoritmos apropriados
                - Tuning (ajuste) de hiperparâmetros
                - Uso de validação cruzada para garantir robustez
                - Comparação sistemática entre os modelos testados
            5. Evaluation (Avaliação):
                - Avaliar a performance com métricas técnicas
                - Medir o impacto real no negócio (business value)
                - Verificar a robustez em cenários adversos
                - Analisar a interpretabilidade e fairness (ausência de bias)
            6. Deployment (Implantação)
                - Definir a infraestrutura de produção
                - Implementar monitoramento (para drift e degradação)
                - Estabelecer um processo de manutenção e retreinamento
                - Ter estratégias de contingência (rollback)
    - EDA
        - Processo de investigar, visualizar e compreender os dados sistematicamente antes de aplicar algoritmos de ML
            - Seus princípios incluem deixar as hipóteses emergirem dos dados, usar a visualização extensivamente e manter um ceticismo saudável
        - Divisão
            - Análise Estrutural: Entender a "anatomia" dos dados, como dimensionalidade (observações e variáveis), tipos de dados, missing values e duplicatas
            - Análise Distribucional: Como os dados se comportam, incluindo distribuições univariadas, assimetria (skewed), outliers e variabilidade
            - Análise Relacional: Como as variáveis se conectam, através de correlações, dependências, interações e clusters
            - Detecção de Anomalias: Identificar o que está "estranho", como outliers (erros vs. valores legítimos) e inconsistências
        - Técnicas
            - Univariada (uma variável)
                - Quantitativas (Numéricas): Medidas de tendência central (média, mediana, moda) , dispersão (variância, desvio padrão) e forma (assimetria, curtose). Visualizações: Histograma, Box Plot, Density Plot
                - Qualitativas (Categóricas): Análise de frequência (absoluta, relativa, acumulada). Visualizações: Gráfico de barras, Gráfico de pizza, Gráfico de Pareto
            - Bivariada (duas variáveis)
                - Quantitativa vs. Quantitativa: Correlação (Pearson, Spearman). Visualização: Scatter Plot (gráfico de dispersão), Heatmap de Correlação
                - Categórica vs. Quantitativa: Testes como ANOVA. Visualização: Box Plot por Grupo, Violin Plot
                - Categórica vs. Categórica: Tabela de Contingência , Teste Qui-quadrado. Visualização: Heatmap de Contingência, Stacked Bar Chart
            - Multivariada: Uso de Matriz de Correlação para identificar relações entre múltiplas variáveis, frequentemente visualizada com um heatmap com dendrograma
    - Pré-processamento de dados
        - O pré-processamento transforma dados brutos em um formato adequado para ML , seguindo o princípio de "Garbage in, garbage out"
        - Tratamento de Missing Values
            - Algoritmos podem falhar com valores NaN, e o tratamento inadequado pode introduzir bias
                - O tratamento depende do mecanismo de ausência
            - MCAR (Missing Completely At Random): A ausência é totalmente aleatória (ex: falha de computador)
                - Não introduz bias
                - Pode-se deletar ou imputar (ex: média)
            - MAR (Missing At Random): A ausência depende de outras variáveis observadas (ex: homens respondem menos sobre peso, mas sabemos quem é homem)
                - Introduz bias se tratado de forma simples
                - Deletar valores introduz bias; a imputação deve considerar as outras variáveis (ex: imputação por regressão)
            - MNAR (Missing Not At Random): A ausência depende do próprio valor faltante (ex: pessoas com alta renda não revelam o salário)
                - Causa bias severo e é o problema mais complexo
                - Imputação simples ou deleção geram bias severo; a única saída é modelar o próprio mecanismo de ausência
        - Tratamento de Outliers
            - São obsevações significativamente diferentes do restante
            - Tipos
                - Statistical Outliers (Estatísticos): Valores extremos, mas válidos e legítimos (ex: salário do CEO, altura de um jogador de basquete)
                    - Não devem ser deletados
                    - O tratamento envolve transformações (log) ou o uso de modelos robustos
                - Domain-Specific Outliers (De Domínio): Valores que violam regras de negócio ou lógicas (ex: idade de 150 anos, desconto de 120%)
                    - Devem ser investigados, corrigidos se possível, ou deletados se comprovadamente impossíveis
                - Data Errors (Erros de Dados): Valores incorretos devido a falhas de coleta ou entrada (ex: valores padrão como 999, encodings errados como "S?o Paulo")
                    - Devem ser corrigidos na fonte ou deletados.
        - Tratamento de Duplicatas
            - Registros que representam a mesma entidade
                - Podem causar overfitting e bias na avaliação
            - Exact Duplicates (Exatas): Linhas idênticas
                - Tratamento: Remover, mantendo apenas a primeira ocorrência
            - Near Duplicates (Aproximadas): Mesma entidade com pequenas diferenças (ex: "João Silva" vs "Joao Silva")
                - Tratamento: Padronização (ex: lowercase) e uso de similaridade de strings (ex: Levenshtein distance)
            - Entity Resolution (Resolução de Entidades): Registros diferentes que representam a mesma entidade (ex: Cliente A com um endereço e Cliente B com endereço abreviado)
                - Requer técnicas sofisticadas de matching (probabilístico, ML)
        - Feature Scaling
            - Necessário porque atributos em escalas muito diferentes (ex: Salário vs. Idade) podem dominar algoritmos baseados em distância (como KNN) ou gradiente
            - Standardization (Z-score): Transforma os dados para terem média 0 e desvio padrão 1, usando a fórmula z = (x-mean) / std
                - Preserva a forma da distribuição
            - Min-Max Scaling: Reescala os dados para um range fixo, geralmente [0, 1], usando a fórmula z = (x - min) / (max - min)
            - Ponto Crítico: Os valores usados para o escalonamento (média, desvio padrão, min, max) devem ser calculados apenas no conjunto de treino e depois aplicados para transformar os conjuntos de validação e teste
        - Encoding de Variáveis Categóricas
            - Algoritmos de ML exigem números, não texto
                - A técnica depende do tipo de variável: nominais, ordinais e alta cardinalidade
            - Técnicas de Encoding
                - Label Encoding: Mapeia categorias para inteiros (ex: P=0, M=1, G=2)
                    - Adequado apenas para variáveis ordinais
                - One-Hot Encoding: Cria k colunas binárias (0/1) para k categorias
                    - Não introduz ordem artificial, mas pode criar muitas dimensões (maldição da dimensionalidade)
                - Dummy Encoding: Similar ao One-Hot, mas usa k-1 colunas, removendo a multicolinearidade
                    - A categoria removida torna-se a referência
                - Target Encoding: Substitui a categoria por uma estatística da variável-alvo (ex: a média do alvo para aquela categoria)
                    - É bom para alta cardinalidade e captura a relação com o alvo
                - Frequency Encoding: Substitui a categoria por sua frequência (popularidade) no dataset
                - Binary Encoding: Converte os labels (números inteiros) para representação binária e divide os bits em colunas
                    - Reduz a dimensionalidade para log2(k) colunas
                - Hash Encoding: Usa uma função hash para mapear categorias para um número fixo de dimensões
                    - Não depende do número de categorias, mas pode causar colisões (categorias diferentes mapeadas para a mesma coluna)
        - Redução de Dimensionalidade
            - Etapa crucial no pré-processamento
            - A alta dimensionalidade interfere no custo de aprendizado e na qualidade das respostas
                - À medida que a dimensionalidade aumenta, o volume do espaço cresce exponencialmente, tornando os dados esparsos
                - Para manter a mesma densidade de dados necessária para um aprendizado estatístico confiável, a quantidade de dados de treinamento necessária cresceria exponencialmente com a dimensão
                - Além disso, em métodos baseados em instância, a presença de muitos atributos irrelevantes pode dominar a métrica de distância, tornando-a perigosa
            - Abordagens da Redução de Atributos
                - Feature Extraction
                    - Criação de novos atributos a partir da combinação dos originais
                        - Envolve projetar os dados originais em um novo espaço de features, muitas vezes de menor dimensão, retendo a maior parte da informação relevante
                    - Uma forma de fazer isso é usando a técnica PCA
                        - PCA (Principal Component Analysis)
                            - O PCA realiza uma projeção ortogonal dos dados em um espaço linear de menor dimensão, tal que a variância dos dados projetados seja maximizada
                            - Cada nova dimensão (componente principal) é uma combinação linear das variáveis originais
                                - Os componentes são ordenados de forma decrescente pela quantidade de variância dos dados que eles explicam
                            - Matematicamente, o PCA envolve a decomposição em autovalores (eigendecomposition) da matriz de covariância dos dados
                                - Os autovetores definem as direções de maior variância (os componentes principais) e os autovalores indicam a magnitude dessa variância
                            - É uma técnica de aprendizado não supervisionado (não usa os rótulos das classes para encontrar as projeções)
                                - Também é conhecido como transformada de Karhunen-Loève
                - Feature Selection
                    - Diferente da extração, a seleção mantém os atributos originais, descartando os irrelevantes ou redundantes
                    - Técnicas
                        - Filters
                            - Os filtros avaliam os atributos com base em propriedades gerais dos dados, independentemente do algoritmo de aprendizado que será usado posteriormente
                            - Os atributos são ordenados (ranqueados) com base em métricas estatísticas de relevância e redundância, na qual um número K de atributos mais bem ranqueados é selecionado
                            - Métricas
                                - InfoGain
                                    - Ganho de Informação
                                    - Mede a redução da entropia causada pelo particionamento dos dados de acordo com um atributo
                                - GainRatio
                                    - Usados em árvores de decisão
                                - Correlação
                                    - Entre o atributo e a classe alvo
                            - São computacionalmente leves e rápidos
                            - Porém, possuem dificuldades práticas
                                - É necessário definir o limiar de corte (quantos atributos descartar) por tentativa e erro
                                - Ignoram a interação dos atributos com o viés do algoritmo de aprendizado específico
                        - Wrappers
                            - Os Wrappers realizam uma busca no espaço de subconjuntos de atributos, utilizando o próprio algoritmo de aprendizado para avaliar a qualidade de cada subconjunto
                            - Consideram o viés indutivo do algoritmo específico, tendendo a encontrar subconjuntos que maximizam a performance daquele modelo
                            - Como testar todos os subconjuntos é inviável (2^K), usam-se buscas gulosas
                                - Forward Selection
                                    - Começa com um conjunto vazio e adiciona atributos um a um, escolhendo aquele que mais melhora a performance do modelo, até que não haja melhora significativa
                                    - Tende a produzir conjuntos menores e elimina bem a redundância
                                - Backward Elimination
                                    - Começa com todos os atributos e remove um a um o que menos prejudica (ou mais melhora) a performance
                                    - Geralmente produz melhores resultados de precisão, pois captura melhor as interações entre atributos, mas é computacionalmente muito mais pesado
                        - Ambas as estratégias podem ficar presas em mínimos locais (não encontram a solução ótima global) e têm alto custo computacional, pois treinam o modelo repetidas vezes
                            - RankSearch
                                - Forma de lidar com o alto custo computacional dos Wrappers
                                - Abordagem híbrida para minimizar o problema de custo
                                - Usa-se uma métrica de filtro (como o InfoGain) para ordenar os atributos inicialmente
                                - O algoritmo avalia subconjuntos inserindo gradualmente os atributos na ordem gerada pelo filtro, mas avaliando com o classificador (como um Wrapper simplificado)
                                    - Isso evita a busca combinatória completa de 2^K
        - Divisão dos Dados
            - É crucial dividir os dados para evitar uma ilusão de performance
                - O objetvo é medir a capacidade de generalização do modelo para dados nunca vistos
            - A divisão deve ocorrer antes das etapas de pré-processamento (como scaling e imputação)
            - Treino: onde o modelo aprende os padrões (60-80%)
            - Validação: usado para tuning de hiperparâmetros e seleção de modelos (10-20%)
            - Teste: usado uma vez no final, para uma avaliação final e não-enviesada (10-20%)
                - Fornece a estimativa honesta da performance em produção
            - Estratégias
                - Random Split (Aleatória): Pode criar conjuntos desbalanceados ou não representativos
                - Stratified Split (Estratificada): Garante que a mesma proporção de classes do dataset original seja mantida em todos os conjuntos (treino, validação e teste)
                    - É a abordagem preferida para problemas de classificação
                - Time Series Split (Séries Temporais): Os dados devem ser ordenados por data
                    - Nunca se deve usar dados futuros para prever o passado
                    - O treino é feito com os dados mais antigos (ex: primeiros 80%) e o teste com os dados mais recentes (ex: últimos 20%)
        - K Fold Cross-Validation
            - Técnica usada para avaliar o desempenho de um modelo de ML, sendo particularmente útil em conjuntos de dados pequenos onde a criação de um conjunto de validação fixo poderia “desperdiçar” dados valiosos
            - O dataset de treino é dividido em k partes (folds)
                - O modelo é treinado k vezes
                - Em cada vez, k-1 partes são usadas para treino e 1 parte é usada para validação
                - A performance final é a média das k avaliações, fornecendo uma estimativa mais robusta
                - O Stratified K-Fold garante que as proporções de classe sejam mantidas em cada fold
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2031.png)
                    
    - Tunagem de Hiperparâmetros
        - Hiperparâmetros são configurações do algoritmo definidas antes do processo de aprendizado
            - Eles têm um impacto crítico na performance e as configurações ideais variam para cada conjunto de dados
        - Metodologia
            - Preparação dos dados → dividir os dados, pré-processamento após divisão para evitar data leakage
            - Definição do espaço de busca → identificar os hiperparâmetros críticos, estabelecer os ranges de variação para testar
            - Escolha da estratégia de busca
                - Manual Tuning → testar valores manualmente, um por vez
                - Grid Search → testa todas as combinações possíveis de hiperparâmetros definidos no range
                - Random Search → amostra aleatoriamente combinações do espaço de hiperparâmetros
    - Modelos
        - Regressão Linear
            - Problema da Regressão
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2032.png)
                
            - Uma técnica estatística que modela o relacionamento entre uma variável dependente e uma ou mais variáveis independentes
                - Assume que o relacionamento é aproximadamente linear
                - Usado para predição e para entender a influência dos preditores
                - Motivação
                    - Simples & Interpretável: Fácil de entender e explicar (coeficientes refletem a importância dos preditores)
                    - Rápido & Eficiente: Rápido de treinar, mesmo para conjuntos de dados grandes
                    - Bom Baseline: Ponto de partida para comparação de modelos mais complexos
                    - Extensível: Podem incluir termos polinomiais, interações e e regularização
                    - Inferência Estatística : Suporta a construção de intervalos de confiança e outras análises
            - Definição do modelo
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2033.png)
                
            - Setup
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2034.png)
                
                - X → matriz de preditores
            - Objetivo
                - Encontra o vetor β que minimiza a soma dos resíduos (residual sum of squares - RSS), medida estatística para medir a diferença entre os valores reais (observados) e os valores previstos por um modelo de regressão
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2035.png)
                    
                - Métodos
                    - OLS (Ordinary Least Square)
                        - O objetivo do OLS é encontrar o vetor β que minimiza a Soma dos Resíduos Quadrados (RSS)
                            - Possui uma solução analítica, evitando iterações e é eficiente para conjuntos de dados pequenos a médios
                            - É sensível a outliers, requer a inversõ da matriz X^TX, que é custosa e pode ser instável (especialmente com atributos correlacionados), e não é escalável para big data
                        - Fórmula
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2036.png)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2037.png)
                            
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2038.png)
                            
                        - Regularização
                            - Ridge Regression (L2 Regularization)
                                - O OLS pode apresentar desempenho insatisfatório quando os preditores são altamente correlacionados (multicolinearidade), o número de variáveis p é próximo ou maior que o número de observações n e quando ocorre overfitting em contextos de alta dimensionalidade
                                    - Para lidar com estes problemas, a Regressão Ridge adiciona uma penalidade L2 à função de perda, reduzindo os coeficientes para melhorar a capacidade de generalização
                                    - Indicada quando há multicolinearidade ou quando se espera que todas as variáveis tenham alguma influência
                                    - Melhora a estabilidade, introduz viés para reduzir a variância, mas não reduz coeficientes exatamente a zero
                                - Função objetivo
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2039.png)
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2040.png)
                                    
                            - Lasso Regression (L1 Regularization)
                                - Adiciona uma penalidade L1 à função de perda, podendo reduzir alguns coeficientes exatamente à zero (diferença para o L2), atuando como um método de seleção de variáveis
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2041.png)
                                    
                            - Elastic Net (L1 + L2)
                                - Combina ambos os métodos, útil quando os preditores são altamente correlacionados
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2042.png)
                                    
                    - GD (Gradient Descent)
                        - É um método iterativo usado para encontrar os parâmetros que minimizam o erro de predição, sendo útil para conjuntos de alta dimensão
                            - Não requer inversão de matrizes, flexível e estável para regularização de parâmetros
                                - Quando a matriz começa a crescer, computacionalmente fica inviável a utilização do OLS
                            - Requer definição ou ajuste de taxa de aprendizagem n, convergência pode ser lenta e pode ficar preso em mínimos locais
                            - Na prática, o GD vai ajustar os parâmetros por meio de derivadas sucessivas, de modo a se aproximar ao máximo de 0 (ou seja, ponto de inflexão, chegando ao ponto mais baixo da função de erro, aonde queremos chegar)
                        - Função objetivo
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2043.png)
                            
                            - Regra de ajuste
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2044.png)
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2045.png)
                                
                        - Variantes
                            - Batch Gradient Descent → usa todos os n exemplos em cada passo de ajuste
                            - Stochastic Gradient Descent → ajusta os parâmetros usando um exemplo por vez
                            - Mini-batch Gradient Descent → usa uma amostra de exemplos por ajuste
                        - Comparação
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2046.png)
                            
        - Regressão Logística
            - É um modelo linear projetado para problemas de classificação binária, embora possa ser estendido para multiclasse
                - Ela modela a probabilidade de que uma dada entrada pertença a uma classe usando a função logística (sigmoide), que mapeia qualquer entrada de valor real para uma saída entre 0 e 1
                - A saída é interpretada como uma probabilidade, e a classificação é feita aplicando-se um limiar (limiar de corte)
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2047.png)
                    
            - Problema de Classificação
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2048.png)
                
            - A regressão logística modela a probabilidade de que uma entrada xi ∈ R^p pertença à classe yi ∈ {0, 1} usando a função sigmoide, denotada por σ (sigma)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2049.png)
                
                - A função sigmoide mapeia a saída linear w^Tx para uma probabilidade no intervalo (0, 1)
                    - Formalização
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2050.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2051.png)
                        
                - Para encontrar os parâmetros w ideais, minimizamos a função log-loss (entropia cruzada) sobre o conjunto de dados, na qual é uma função derivada da Log-Verossimilhança dos dados
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2052.png)
                    
                    - Formalização
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2053.png)
                        
                    - Problema da Minimização
                        - Não existe uma solução em forma fechada para minimizar a função de perda logarítmica → utilizam-se métodos de otimização numérica
                        - A solução deve ser encontrada usando métodos de otimização numérica, que requerem o cálculo do gradiente da função de perda
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2054.png)
                            
                        - Métodos comuns
                            - Gradiente Descendente
                                - Atualiza os pesos iterativamente usando o gradiente de todos os dados
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2055.png)
                                
                            - Gradiente Descendente Estocástico (SGD)
                                - Atualiza os pesos usando apenas uma ou poucas amostras a cada passo
            - Regressão Logística Multiclasse
                - Uma regressão logística para problemas com K classes na qual K > 2
                - O modelo utiliza um vetor de pesos wk, separado para cada classe k
                - A função sigmoide é substituída pela Função Softmax para calcular a probabilidade para cada classe
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2056.png)
                    
                - A função de perda utilizada é a Entropia Cruzada generalizada
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2057.png)
                    
                - Gradiente em wk
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2058.png)
                    
            - Vantagens e desvantagens
                - Vantagens
                    - Simples e Interpretável: É fácil de implementar e os coeficientes w podem ser interpretados em termos do seu efeito nas log-odds (razão de chances logarítmica)
                    - Eficiente: É computacionalmente eficiente e converge rapidamente, mesmo em grandes conjuntos de dados
                    - Saída Probabilística: Fornece probabilidades reais de pertencimento à classe, o que é útil para avaliação de risco e tomada de decisão
                    - Bem Estabelecida: Possui fundamentos estatísticos sólidos e é amplamente confiável
                - Desvantagens
                    - Suposição de Linearidade: Assume que a relação entre as variáveis de entrada x e as log-odds é linear, o que pode não ser verdade
                    - Expressividade Limitada: Não é adequada para capturar relações complexas e não lineares por conta própria
                    - Dependência de Engenharia de Atributos: O desempenho do modelo depende muito de uma boa seleção e pré-processamento das features (características)
            - Regularização na Regressão Logística
                - A regularização adiciona um termo de penalização à função de perda logística (log-loss) para evitar overfitting e melhorar a generalização
                - Ridge (L2)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2059.png)
                    
                - Lasso (L1)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2060.png)
                    
                - Elastic Net (L1 + L2)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2061.png)
                    
        - K-Nearest Neighbor (KNN)
            - É o principal exemplo de aprendizagem por instâncias
                - Ele armazena os dados de treinamento e, para cada novo padrão de consulta, constrói uma aproximação da função objetivo agregando os K vizinhos mais próximos
            - KNN para classificação
                - Processo para classificar um novo dado
                    - Calcular a distância entre o novo dado e todos os dados de treinamento
                    - Atribuir o novo dado à classe majoritária entre os K vizinhos mais próximos
                    - Isso pode ser feito de duas formas
                        - Voto simples: cada um dos K vizinhos tem um voto
                        - Voto ponderado por distância: vizinhos mais próximos têm um peso maior no voto
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2062.png)
                        
            - KNN para regressão
                - Processo para prever o valor de um novo dado
                    - Calcular a distância entre o novo dado e todos os dados de treinamento
                    - Atribuir como rótulo do novo dado um valor baseado nos K vizinhos mais próximos
                    - Isso pode ser feito de duas formas
                        - Média simples: o valor é a média dos rótulos dos K vizinhos
                        - Média ponderada por distância: a média dos rótulos dos K vizinhos, onde vizinhos mais próximos têm maior peso
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2063.png)
                        
            - Hiperparâmetros do KNN
                - O KNN possui 2 hiperparâmetros que precisam ser definidos
                    - Quantidade de vizinhos (K)
                        - K = 1 → o modelo fica muito sujeito a ruídos nos dados
                        - K muito grande → o modelo pode perder o significado de proximidade e simplesmente classificar pela classe majoritária de todo o conjunto de dados
                    - Métrica de distância
                        - Distância Euclidiana (L2) → métrica mais comumente adotada, funciona bem com features contínuas, principal desvantagem é ser sensível a outliers e a diferenças de escala entre as features
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2064.png)
                            
                        - Distância Manhattan (L1) → robusta a outliers, boa para features em escalas diferentes
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2065.png)
                            
                        - Ao usar medidas de distância, a escala dos atributos é crucial
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2066.png)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2067.png)
                            
            - Fácil de implementar, não requer etapa de treinamento, ideal para conjuntos de dados pequenos ou médios
            - Sensível a presença de atributos irrelevantes e/ou redundantes, custo computacional e armazenamento em alguns contextos é impraticável
        - Classificadores Bayesianos
            - Modelos de classificação probabilística que aplicam o teorema de Bayes para estimar a probabilidade de cada classe dado os atributos observados
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2068.png)
                
                - P(ck|x) → probabilidade a posteriori, probabilidade da classe ck dado que vimos x
                - P(x|ck) é a verossimilhança (likelihood), a probabilidade de ver x se a classe for ck
                - P(ck) → a probabilidade a priori (prior),a probabilidade da classe ck em geral
                - P(x) → a evidência (a probabilidade de ver x)
                - O objetivo é atribuir a classe que tiver a maior probabilidade a posteriori
                - Tipos comuns incluem Naïve Bayes, Semi-naïve e Redes Bayesianas completas
            - Exemplo da Regra de Bayes
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2069.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2070.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2071.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2072.png)
                
            - Naïve Bayes
                - O Naïve Bayes é uma aplicação direta do Teorema de Bayes para classificação
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2073.png)
                    
                - Suposição ingênua (Naïve Assumption)
                    - Os atributos são condicionalmente independentes dada a classe, pois calcular P(x | y = ck) (probabilidade de uma combinação específica de atributos) é complexo
                    - Isso permite que a verossimilhança P(x | y = ck) seja dividida em um produto de probabilidades individuais:
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2074.png)
                        
                - Regra de classificação final
                    - A classe prevista ŷ é aquela que maximiza o produto da prior com as likelihoods individuais
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2075.png)
                        
                - Estimação de parâmetros
                    - Para usar o Naïve Bayes, o modelo primeiro "aprende" as probabilidades a partir dos dados de treinamento
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2076.png)
                        
                - Simples, rápido para treinar e prever, funciona bem com dados de alta dimensionalidade e lida bem com atributos contínuos e categóricos
                - A suposição de independência frequentemente não é realista, a acurácia pode cair se os atributos forem altamente correlacionados e requer boas estimativas de probabilidade para eventos raros
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2077.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2078.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2079.png)
                    
                - Suavização de Laplace
                    - Essa técnica adiciona um pequeno valor α (geralmente α = 1) a *cada* contagem, para evitar probabilidades zero
                        - Útil em casos de um valor atributo nunca aparecer para uma determinada classe nos dados de treinamento
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2080.png)
                        
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2081.png)
                        
        - Árvores de Decisão
            - Algoritmo de aprendizado supervisionado que cria um modelo em forma de árvore para fazer predições
                - Imitam o processo de decisão humana, fazendo uma série de perguntas para chegar a uma conclusão
                - Podem ser usadas para classificação e regressão
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2082.png)
                    
            - Componentes
                - Root Node
                    - Ponto de partida da árvore
                    - Contém todo o dataset
                    - Primeira pergunta/decisão
                - Decision Nodes
                    - Representam testes/condições sobre características, dividem os dados em subconjuntos
                    - Cada nó tem um ou mais filhos
                - Leaf Nodes
                    - Pontos finais da árvore, contém as predições finais e não tem mais divisões
                - Branches
                    - Conectam os nós, representam os resultados dos testes
                    - Caminho da raiz até a folha = regra de decisão
            - Construção da árvore
                - Calcular a impureza inicial (Entropia ou Gini) do dataset
                    - Entropia → medindo bagunça
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2083.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2084.png)
                        
                    - Gini → probabilidade de erro
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2085.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2086.png)
                        
                - Para cada feature disponível, calcular o ganho de informação (Information Gain) que ela proporcionaria se fosse usada para dividir os dados
                    - Se categórica → testar cada vaor
                    - Se contínua → encontrar melhor threshold
                    - Fórmula de ganho
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2087.png)
                        
                - Escolher feature com maior ganho
                - Dividir dados baseado na feature escolhida
                - Para cada subconjunto verificar critérios de parada
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2088.png)
                    
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2089.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2090.png)
                    
                    - Passo 1
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2091.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2092.png)
                        
                    - Passo 2
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2093.png)
                        
                    - Passo 3
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2094.png)
                        
                    - Passo 4
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2095.png)
                        
                    - Passo 5
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2096.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2097.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2098.png)
                        
                    - Árvore final
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%2099.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20100.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20101.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20102.png)
                        
            - Árvores de Decisão para Regressão
                - A estrutura é a mesma (nós de decisão)
                - As folhas contêm um valor numérico (ex: a média dos valores naquele subconjunto)
                - O critério de divisão não é a pureza, mas a redução do erro de predição, usando métricas como Erro Quadrático Médio (MSE) ou Erro Absoluto Médio (MAE)
            - Facilmente implementada com ifs e elses ou até em hardware com portas lógicas, processo sistemático e interpretável que quando bem executado produz modelos compreensíveis e eficazes para uma ampla gama de problemas de classificação
            - Possui alta instabilidade e variância, pois pequenas mudanças podem mudar a árvore toda, mudança no topo afeta toda a estrutura abaixo, tem tendência ao overfitting e possui generalização limitada
                - Para sanar algumas dessas desvantagens, faz-se o pruning
                    - Pruning
                        - Processo de remoção de ramos/subárvores de uma árvore de decisão
                        - Objetivo de reduzir o overfitting e melhorar generalização
                        - Trade-off: simplicidade vs precisão no treino
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20103.png)
                            
                        - Tipos
                            - Pre-Prunning (Early Stopping)
                                - Durante a construção da árvore
                                - Para o crescimento antes que comece overfitting
                                - Critérios
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20104.png)
                                    
                                - Overview
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20105.png)
                                    
                            - Post-Prunning
                                - Após construir uma árvore completa
                                - Remove ramos que não melhoram performance
                                - Métodos
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20106.png)
                                    
                                - Overview
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20107.png)
                                    
        - Métodos Ensemble
            - Ensemble Learning é um paradigma de ML que consiste em combinar múltiplos modelos (classificadores ou regressores) para resolver um único problema computacional
            - A premissa central é que um comitê de especialistas geralmente toma decisões superiores às de um único especialista, visando reduzir a variância (overfitting), o viés (underfitting) e aumentar a robustez do sistema preditivo
            - Classificação
                - Ensemble Heterogêneos
                    - Combinam modelos gerados por diferentes algoritmos de aprendizado (exemplo: árvore de decisão + SVM)
                    - Objetivo de explorar a diversidade algorítmica para capturar diferentes padrões nos dados
                    - Estratégias de combinação
                        - Votação (Voting) → maioria simples ou ponderada
                        - Stacking (Empilhamento) → treina-se um “meta-modelo” (segundo nível) que aprende a combinar as previsões dos modelos base (primeiro nível)
                            - Funcionamento
                                - Os modelos bases fazem suas previsões
                                - Essas previsões tornam-se "novas features" de entrada para um meta-modelo
                                - O meta-modelo aprende qual modelo base confiar em quais situações
                - Ensemble Homogêneos
                    - Utilizam o mesmo algoritmo base mas induzem diversidade alterando os dados de treinamento, a inicialização ou os parâmetros internos
                    - Permite a especialização e correção de erros sistemáticos do algoritmo escolhido
                    - Bagging (Bootstrap Agreggating)
                        - Técnica projetada para melhorar a estabilidade e precisão, focando principalmente na redução da variância
                        - Funcionamento
                            - O processo inteiro ocorre em paralelo e independe da execução anterior
                            - Amostragem (Bootstrap)
                                - A partir do conjunto de dados original, geram-se novos conjuntos de dados
                                - Cada conjunto é criado por amostragem com reposição, mantendo o tamanho original, logo, alguns exemplos podem aparecer repetidos enquanto outros são omitidos
                            - Treinamento
                                - Um modelo base é treinado independentemente em cada amostra criada
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20108.png)
                                    
                            - Agregação
                                - Classificação → votação majoritária (rótulo mais frequente vence)
                                - Regressão → média das previsões individuais
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20109.png)
                                
                            - Se os erros dos modelos individuais fossem não correlacionados, a média do erro seria reduzida por um fator de M
                                - Na prática, como os modelos treinados são treinados em dados similares, os erros são correlacionados, mas a redução da variância ainda é significativa
                        - Random Forest
                            - É um método Ensemble que combina múltiplas árvores de decisão para obter uma predição final mais robusta
                                - Os erros individuais das árvores se cancelam
                            - Etapas
                                - Bootstrap sampling (Bagging)
                                    - Cada árvore é treinada em uma amostra de bootstrap (amostragem aleatória com reposição) dos dados originais
                                    - Isso significa que cada árvore vê uma versão ligeiramente diferente dos dados
                                - Random Feature Selection
                                    - Em cada nó de cada árvore, ao decidir a melhor divisão, o algoritmo não considera todas as features, mas apenas um subconjunto aleatório delas
                                - Construção individual
                                    - Cada árvore é construída até profundidade máxima ou critério de parada
                                    - Geralmente não há poda e o overfitting é compensado pela agregação
                                - Agregação final
                                    - Classificação → voto majoritário das árvores
                                    - Regressão → média aritmética das predições
                            - Hiperparâmetros
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20110.png)
                                
                    - Boosting
                        - Treina modelos de forma sequencial, a ideia é combinar weak learners para formar um strong learner
                        - Funcionamento
                            - O foco está na redução do viés e, secundariamente, da variância
                            - Primeira treina-se um modelo inicial
                            - Depois, identificam-se os erros cometidos por esse modelo
                                - Isso se faz calculando o erro considerando os pesos das amostras
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20111.png)
                                    
                            - Por fim, o próximo modelo é treinado focando em corrigir esses erros, fazendo o ajuste de pesos e normalização, realizando um processo sequencial de reponderação
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20112.png)
                                
                            - Com isso, treina-se um novo modelo focando nas amostrar difíceis, e o processo se repete até atingir o número desejado de modelos
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20113.png)
                                
                            - Agregação
                                - Classificação → votação majoritária (rótulo mais frequente vence)
                                - Regressão → média das previsões individuais
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20114.png)
                                    
                        - Gradient Boosting
                            - O GB foca nos resíduos (diferença entre o valor real e o predito)
                            - Em vez de prever o rótulo y diretamente, cada nova árvore tenta prever o erro (y - ŷ) da árvore anterior
                            - Com isso, a predição final Fm(x) é a soma do modelo inicial mais as correções ponderadas pela taxa de aprendizado (η)
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20115.png)
                                
                                - Na qual hm(x) é a árvore treinada para prever o resíduo do passo anterior
                            - Processo Sequencial do GB
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20116.png)
                                
                - Mixture os Experts
                    - Forma sofisticada de Ensemble
                    - A combinação é dinâmica
                        - Uma Gating Network (rede de portão) decide, com base no input atual, qual especialista (modelo) é mais adequado para aquela região específica do espaço de dados
                        - É uma estratégia dividir para conquistar
            - Trade-off Viés-Variância
                - Ensembles reduzem Variância
                    - Ao fazer a média de modelos (como no Bagging), suavizam-se as idiossincrasias (características particulares) de modelos individuais que se ajustaram demais ao ruído (overfitting)
                - Ensembles reduzem Viés
                    - Ao combinar modelos simples em sequência (como no Boosting), aumenta-se a complexidade da fronteira de decisão, permitindo que o modelo aprenda padrões complexos que um modelo fraco sozinho não conseguiria (underfitting)
            - Considerações Finais
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20117.png)
                
        - Support Vector Machine (SVM)
            - É um classificador que em sua forma mais básica encontra um hiperplano para separar dados em duas classes com a maior margem possível
                - Hiperplano: “superfície plana” que divide o espaço, em um espaço 2D é uma reta, em 3D é um plano
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20118.png)
                    
            - Vetores de Suporte → são os pontos que estão tocando a margem
                - São os únicos pontos que definem a posição do hiperplano ótimo, todos os outros pontos poderiam ser removidos sem alterar o modelo
            - Para um conjunto de dados linearmente separável, existem infinitos hiperplanos que podem dividir as classes
                - O SVM busca encontrar o hiperplano ótimo, aquele que maximiza a margem de separação entre as duas classes
                    - Ele deve ser equidistante de ambas as classes
                    - A margem é uma zona de separação entre as classes, definida por dois hiperplanos paralelos ao hiperplano de decisão, na qual é dada por d = 2 / ||W||
                    - Cálculo
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20119.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20120.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20121.png)
                        
            - Problema Primal
                - O treinamento do SVM é um problema de otimização onde queremos maximizar a margem d
                    - Matematicamente isso equivale minimizar ||W||, ou seja, (1/2)||W||²
                    - Está sujeito a restrições de que todos os pontos devem ser classificados corretamente fora da margem → yi(w • xi + b) ≥ 1
                - Para resolver um problema de otimização com restrições de desigualdade, pode-se usar a técnica dos Multiplicadores de Lagrange para transformá-lo sem restrições
                    - Permite usar técnicas de cálculo diferencial
                    - Revela a dualidade do problema
                    - Facilita a introdução do kernel trick
                    - Multiplicadores de Lagrange
                        - Técnica que transforma o problema primal em dual
                        - Lagrangiano → função que introduz os multiplicadores de Lagrange (αi) que combina a função objetivo original com as restrições
                            - Lagrangiano do SVM
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20122.png)
                                
                            - Como chegar à fórmula
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20123.png)
                                
                        - Karush-Kuhn-Tucker
                            - São requisitos necessários para encontrar a solução ótima no problema de otimização de SVM, garantindo que os valores encontrados para os pesos, viés e multiplicadores de Lagrange sejam de fato a melhor solução possível para separar as classes
                            - Condições
                                - Gradientes nulos
                                    - O gradiente do Langrangiano (L) em relação às variáveis primais (w e b) deve ser zero
                                        - Em relação à w
                                            
                                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20124.png)
                                            
                                            - Isso implica que o vetor de pesos w é uma combinação linear dos vetores de treinamento
                                                
                                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20125.png)
                                                
                                            - Essa condição revela que apenas os pontoscom ai > 0 contribuem para a formação de w, esses pontos são os chamados vetores de suporte
                                        - Em relação à b
                                            
                                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20126.png)
                                            
                                            - Isso indica que a solução é balanceada entre as classes, não havendo viés sistemático para uma classe específica apenas pela soma dos multiplicadores
                                - Restrições primais satisfeitas
                                    - A solução deve respeitar as restrições originais do problema primal, garantindo que todos os pontos sejam classificados corretamente fora da margem ou sobre ela
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20127.png)
                                        
                                - Multiplicadores não-negativos
                                    - Os multiplicadores de Lagrange (α) introduzidos no problema de otimização não podem ser negativos
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20128.png)
                                        
                                - Condições de complementaridade
                                    - O produto entre o multiplicador e a restrição devem ser 0
                                        
                                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20129.png)
                                        
                                    - Essa condição define a esparsidade do modelo (o fato de depender apenas de alguns pontos)
                                    - Para que o produto seja 0, existem duas situações
                                        - αi = 0
                                            - Isso significa que o ponto não é um vetor de suporte, nesse caso a restrição pode ser diferente de zero (o ponto pode estar longe da margem)
                                        - Restrição = 0
                                            - Isso significa que o ponto está exatamente sobre a margem, nesse caso αi pode ser positivo (αi >0), esses são os vetores de suporte
                    - Problema Dual Final
                        - Substituindo as equações derivadas no Langrariano, chegamos ao problema que o algoritmo resolve na prática
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20130.png)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20131.png)
                            
                        - Resolvendo o sistema, obtemos os valores de α, que determinam os vetores de suporte
                            - A partir deles encontramos W e b
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20132.png)
                                
                - Processo completo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20133.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20134.png)
                    
            - SVM Não-Linear
                - Nem sempre os dados são linearmente separáveis
                    - Uma solução possível para isso é aumentando a dimensionalidade dos dados, a fim de encontrar um hiperplano separador (baseado no Teorema de Cover)
                    - Funções de Kernel podem transformar os dados do espaço original para um espaço de maior dimensão onde eles se tornem linearmente separáveis, são funções que ajudam a organizar dados e melhorar sua classificação
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20135.png)
                        
                - Mapear explicitamente para dimensões altas é custoso
                - O Kernel Trick permite calcular o produto escalar nesse espaço de alta dimensão sem fazer o mapeamento explicitamente
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20136.png)
                    
                - Tipos de Kernels
                    - Linear
                        - Equivalente ao SVM clássico, bom para muitas features e separabilidade linear
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20137.png)
                            
                        - Mais rápido e interpretável
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20138.png)
                            
                    - Polinomial
                        - Útil quando há interação entre as features
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20139.png)
                            
                            - Geralmente usa-se grau baixo (2-3)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20140.png)
                            
                    - RBF (Radial Basis Function)
                        - Mapeia para espaço infinito-dimensional
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20141.png)
                            
                        - Funciona bem na maioria dos casos
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20142.png)
                            
                    - Sigmóide
                        - Similar a redes neurais com uma camada oculta
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20143.png)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20144.png)
                            
            - Classificação Multi-Classe
                - O SVM é binário por natureza, com um única hiperplano separador
                - Para problemas multiclasse, precisa-se de estratégias especiais
                    - One-vs-Rest (OvR) / One-vs-All (OvA)
                        - Treina k classificadores e escolhe o de maior confiança
                            - f(x) = argmax{f1(x), f2(x), …, fn(x)}
                        - É mais rápido, mas sofre com classes desbanlanceadas
                    - One-vs-One (OvO)
                        - Para k classes, treina k(k-1) / 2 classificadores (cada par de classes)
                        - A decisão é por votação majoritária, sendo mais robusta e performática, mas mais lento(O(k²))
            - Support Vector Regression
                - A ideia é encontrar um hiperplano que se ajuste aos dados de forma que o máximo número de pontos esteja dentro de uma “faixa de erro” (ϵ-insensitive tube) ao redor do hiperplano, enquanto que os pontos fora dessa faixa são penalizados
                - É a análoga da SVM
            - Vantagens
                - Efetivo em Alta Dimensão
                    - Funciona bem mesmo quando o número de features >
                    número de amostras
                - Memória Eficiente
                    - Usa apenas os support vectors para predição, resultando em um
                    modelo final compacto
                - Versatilidade com Kernels
                - Fundamentação Matemática Sólida
            - Desvantagens
                - Não Fornece Probabilidades
                    - Saída é apenas classificação/valor
                - Sensível à Escala dos Dados
                    - Normalização/padronização obrigatória
                - Seleção Complexa de Hiperparâmetros
                - Performance Ruim em Datasets Grandes
                    - Lento para treinar com milhões de
                    amostras
                - Sensível a Ruído e Outliers
                    - Outliers podem afetar significativamente a margem
            - Usos
                - Use SVM quando
                    - Dados têm muitas features
                    - Dataset é pequeno/médio
                    - Precisão é mais importante que interpretabilidade
                    - Relações não-lineares complexas
                    - Problema bem definido (classificação/regressão)
                - Evite SVM quando
                    - Dataset é muito grande (>100k samples)
                    - Precisa de probabilidades nativas
                    - Interpretabilidade é crucial
                    - Dados têm muito ruído
                    - Recursos computacionais limitados
        - K-Means
            - O K-Means é um dos algoritmos de clustering mais populares devido à sua simplicidade e eficiência computacional
            - O objetivo é particionar o conjunto de dados em K grupos, onde K é um parâmetro pré-definido
                - O algoritmo busca minimizar uma função de custo, frequentemente chamada de medida de distorção J, que é a soma dos quadrados das distâncias de cada ponto de dados ao seu centróide atribuído
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20145.png)
                    
            - Passos
                - Inicialização
                    - Escolha K centróides iniciais μk aleatoriamente ou usando uma subamostra dos dados
                - Iterar até a convergência
                    - Fase de Associação (Passo E)
                        - Atribua cada ponto de dados xn ao cluster cujo centróide (ponto médio de dados os dados pertencentes a um cluster, representando seu centro) μk é o mais próximo (geralmente usando distância euclidiana)
                        - Matematicamente, define-se variáveis indicadoras binárias rnk ∈ {0, 1}
                    - Fase de Atualização (Passo M)
                        - Recalcule os centróides μk como a média de todos os pontos de dados atualmente atribuídos ao cluster k
            - Propriedades e Limitações
                - Convergência
                    - O algoritmo garante a convergência para um mínimo local da função de distorção J em um número finito de iterações, pois cada passo reduz o valor de J
                - Limitações Críticas
                    - Escolha de K
                        - O número de clusters deve ser definido a priori
                    - Mínimos Locais
                        - A solução final depende fortemente da inicialização
                        - É comum rodar o algoritmo várias vezes com inicializações diferentes e escolher o resultado com o menor erro
                    - Sensibilidade a Outliers
                        - Como utiliza a média quadrática, outliers podem deslocar significativamente os centróides
                        - O algoritmo K-Medoids é uma alternativa mais robusta que usa pontos de dados reais (medóides) como centros em vez da média
                    - Forma dos Clusters
                        - O K-Means, ao usar distância Euclidiana, pressupõe implicitamente que os clusters são esféricos e têm tamanhos similares
                        - Ele falha em detectar clusters alongados ou com formas complexas
        - Gaussian Mixture Models (GMM)
            - Enquanto o K-Means faz uma "atribuição rígida" (um ponto pertence a apenas um cluster), os modelos probabilísticos permitem "atribuições suaves" (probabilidades de pertencimento)
            - O GMM é um modelo que assume que os dados são gerados por uma combinação linear de K distribuições gaussianas
                - A densidade probabilística é dada pela fórmula abaixo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20146.png)
                    
                    - πk são coeficientes de mistura (probabilidades a priori)
                    - μk são as médias
                    - Σk são as matrizes de covariância de cada componente
            - Algoritmo Expectation-Maximization
                - Para treinar um GMM, utilizamos o algoritmo EM para encontrar os parâmetros que maximizam a verossimilhança dos dados
                    - Ela generaliza a lógica do K-Means
                - Passos
                    - Passo E (Expectativa)
                        - Calcula a responsabilidade γ(znk), que é a probabilidade posterior de que o componente k gerou o ponto n, usando os prâmetros atuais
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20147.png)
                            
                    - Passo M (Maximização)
                        - Reestima os parâmetros (μk, Σk, πk) usando as responsabilidades calculadas
                        - Por exemplo, a nova média μk é a média ponderada de todos os dados, onde o peso é a responsabilidade do cluster k para aquele ponto
            - Relação com K-Means
                - O K-Means é um caso limite do GMM
                - Se considerarmos um GMM onde todas as matrizes de covariância são proporcionais à identidade (ϵI) e fizermos a variância ϵ → 0, as responsabilidades tornam-se binárias (0 ou 1), resultando na atribuição rígida do K-Means
        - Mapas Auto-Organizáveis (SOM - Konohen Maps)
            - O SOM são redes neurais inspiradas na organização topológica do córtex cerebral
                - Diferente do K-Means e GMM, o SOM foca na preservação da topologia e visualização de dados
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20148.png)
                    
            - A rede aprende a mapear dados de entrada de alta dimensão em um grid (reticulado) de neurônios, geralmente 2D, preservando as relações de vizinhança
            - Competição
                - Os neurônios competem para ser ativados por um padrão de entrada
                - Apenas um (o vencedor ou Best Matching Unit - BMU) "ganha"
            - Cooperação
                - O vencedor ativa seus vizinhos no reticulado através de conexões laterais. A magnitude da cooperação é definida por uma função de vizinhança topológica hj,i (geralmente uma Gaussiana centrada no vencedor)
            - Adaptação
                - Os pesos sinápticos do vencedor e de seus vizinhos são ajustados para ficarem mais parecidos com o vetor de entrada
            - Algoritmo
                - Inicialização
                    - Pesos sinápticos wj são inicializados com valores pequenos aleatórios
                - Amostragem
                    - Um vetor de entrada x é escolhido do conjunto de dados
                - Correspondência (Matching)
                    - Encontrar o neurônio vencedor i(x) cujo vetor de pesos é mais próximo de x (menor distância Euclidiana)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20149.png)
                        
                - Atualização
                    - Ajustar os pesos de todos os neurônios j usando a regra de atualização
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20150.png)
                        
                        - Onde η(n) é a taxa de aprendizado e hj,i(x) é a função de vizinhança, ambas decaindo com o tempo (n)
                - Continuação
                    - Repetir até a convergência
            - Fases do aprendizado
                - O aprendizado ocorre em duas fases distintas
                    - Fase de Ordenação
                        - A taxa de aprendizado e a vizinhança são grandes
                        - Ocorre a ordenação topológica global dos vetores de peso
                    - Fase de Convergência
                        - A taxa de aprendizado e a vizinhança são pequenas
                        - Ocorre o ajuste fino dos pesos para melhor representação da densidade dos dados (quantização vetorial)
- Deep Learning
    - É um tipo de Machine Learning que usa redes neurais artificiais com muitas camadas (profundas) para imitar o cérebro humano, aprendendo padrões complexos diretamente de grandes volumes de dados sem precisar de programação explícita para cada tarefa, permitindo que máquinas identifiquem, classifiquem e prevejam informações de forma autônoma e precisa
    - Redes Neurais
        - Representam um paradigma projetado para emular a capacidade do cérebro humano de adquirir e armazenar conhecimento experimental
            - Biologicamente, o cérebro opera através de componentes estruturais lentos, mas compensa com uma interconectividade densa e processamento paralelo
        - Anatomia Computacional
            - A modelagem matemática abstrai a complexidade bioquímica em componentes funcionais diretos
            - Sinapses e Pesos (wkj)
                - No sistema biológico, a sinapse é a junção onde o sinal é transmitido
                - No modelo artificial, cada conexão de entrada xj para um neurônio k é multiplicado por um peso wkj
                - O valor do peso determina a intensidade e o sinal (excitatório se positivo, inibitório se negativo) da conexão
            - Soma (Agregador Linear)
                - O corpo celular (soma) biológico integra os sinais
                - Matematicamente, isso é a soma ponderada das entradas mais um termo de viés (bias)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20151.png)
                    
            - Bias (bk)
                - Age como um peso conectado a uma entrada fixa de +1, permitindo que o hiperplano de decisão seja deslocado da origem, aumentando a flexibilidade do modelo
            - Função de Ativação (φ(⋅))
                - Define a saída do neurônio em resposta ao campo local induzido vk
                - Introduz a não-linearidade essencial para que a rede possa resolver problemas complexos
        - Evolução dos Modelos de Neurônio
            - Modelo McCulloth-Pitts
                - Foi o primeiro passo formal
                - É um modelo de limiar binário (”tudo ou nada”), se a soma ponderada excede um limiar T (threshold do neurônio), a saída é 1, caso contrário, é 0
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20152.png)
                    
                - Limitação → ele não possui mecanismo de aprendizado intríseco, os pesos precisavam ser calculados analiticamente para realizar funções lógicas (AND, OR, NOT)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20153.png)
                    
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20154.png)
                    
            - Perceptron de Rosenblatt
                - Introduziu a regra de aprendizado
                - O Perceptron é construído sobre o modelo de McCulloch-Pitts, mas com pesos ajustáveis via treinamento supervisionado
                    - Define um hiperplano de decisão no espaço m-dimensional
                    - O neurônio calcula a soma ponderada das entradas mais o viés, produzindo uma saída 1 (campo induzido é positivo) ou -1 (campo induzido negativo), com o objetivo de classificar os estímulos em duas classes
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20155.png)
                        
                    - Existe também um viés que tem o efeito de deslocar a fronteira de decisão para longe da origem
                        - Matematicamente, o bias pode ser tratado como um peso sináptico w0 conectado a uma entrada fixa com valor +1
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20156.png)
                        
                - Interpretação Geométrica
                    - O perceptron define uma região de decisão separada por um hiperplano, definida pela equação wx + b = 0
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20157.png)
                        
                    - A fronteira de decisão é o conjunto de pontos onde o perceptron está “indeciso”, logo, wx + b = 0
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20158.png)
                        
                    - O vetor de pesos é perpendicular à reta de decisão
                    - O bias controla a distância da reta até a origem
                    - O lado da reta determina a classe que cada região representa
                - Perceptron Learning Rule
                    - Para que o perceptron classifique corretamente exemplos x como pertencentes à C1 ou C2, é necessário encontrar os pesos sinápticos w e b em um processo interativo através de uma regra de correção de erros chamada Perceptron Learning Rule ou Perceptron Convergence Algorithm
                        - No entanto, esse procedimento e o próprio perceptron só funcionam corretamente se as classes C1 e C2 forem linearmente separáveis
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20159.png)
                            
                        - Assim, dados dois conjuntos de vetores de entrada para treinamento H1 e H2 tais que H1 é o subespaço de vetores de treinamento que pertencem à classe C1 e H2 à C2, treina-se o perceptron iterativamente ajustando-se os pesos w e b com o Perceptron Learning Rule de modo que os pesos w e b convergem e formem um hiperplano de separação, tal que w^Tx ≥ 0 para cada vetor de entrada x pertencente à C1 e w^Tx < 0 para cada vetor de entrada x pertencente à C2
                        - Se os dados forem linearmente separáveis, o algoritmo converge em número finito de iterações, caso contrário, oscila indefinidamente
                    - Algoritmo
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20160.png)
                        
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20161.png)
                            
                    - Outras regras
                        - Hebbian Learning Rule
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20162.png)
                            
                        - Delta Learning Rule
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20163.png)
                            
                        - Widrow-Hoff Learning Rule (LMS (Least Mean Square) Learning Rule)
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20164.png)
                            
                            - Foca na minimização do MSE e opera sobre a saída linear antes da função de ativação degrau
                            - A regra define uma superfície de erro parabólica no espaço de pesos, na qual o ajuste é feito na direção oposta ao gradiente do erro(∇E), descendo a encosta da superfície de erro em direção ao mínimo global
                        - Correlation Learning Rule
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20165.png)
                            
                        - Winner-Take-All Learning Rule
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20166.png)
                            
            - Problema XOR
                - O perceptron simples (Single Layer Perceptron) foi provado matematicamente que não consegue resolver problemas que não sejam linearmente separáveis, como o exemplo clássico da função XOR
                    - A função XOR requer duas retas de decisão para separar as classes, o que é impossível para um único neurônio linear
                    - Isso desanimou a pesquisa em redes neurais por anos e contribuiu para o primeiro inverno da IA
                - Para resolver esse problema, a solução reside na adição de camadas intermediárias, criando o Multilayer Perceptron (MLP)
            - MLP (Multi-Layer Perceptron)
                - Arquitetura e Capacidades
                    - Camadas Ocultas
                        - Neurônios entre a entrada e saída que não tem contato direto com o ambiente externo
                        - Extraem features de ordem superior e constroem representações internas dos dados
                    - Não-Linearidade
                        - Se os neurônios ocultos fossem lineares, a rede interna colapsaria matematicamente em um único Perceptron Linear
                        - As funções de ativação não-lineares permitem que a rede modele fronteiras de decisão complexas e arbitrárias
                    - Aproximador Universal
                        - Uma MLP com apenas uma camada oculta (com um número suficiente de neurônios) e funções de ativação sigmoidais pode aproximar qualquer função contínua com precisão arbitrária
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20167.png)
                        
                - Backpropagation
                    - É o método (ou algoritmo) padrão para treinar MLPs, pois resolve o problema de como ajustar os pesos das camadas ocultas
                    - O treinamento ocorre em duas fases distintas para cada exemplo de treino
                        - Fase Forward (Propagação)
                            - Nessa fase, os pesos sinápticos são fixos
                                - O sinal de entrada entra na rede e se propaga camada por camada até a saída
                            - Cada neurônio calcula seu campo local induzido (soma ponderada das entradas mais o viés), aplicando-se logo em seguida a função de ativação não-linear
                                - O sinal resultante serve de entrada para a próxima camada
                            - Nenhuma alteração nos pesos ocorre aqui, apenas os estados de ativação são calculados
                        - Back Forward (Retropropagação)
                            - É onde o aprendizado ocorre
                            - Primeiro, ocorre o cálculo do erro
                                - Um sinal de erro é produzido comparando a saída da rede com a resposta desejada
                            - Depois, propaga-se o erro
                                - Esse erro é propragado de trás para frente (da saída para a entrada)
                                - O algoritmo calcula o gradiente local para cada neurônio
                            - Por fim, ocorre o ajuste nos pesos para minimizar o erro
                                - O cálculo para a camada de saída é direto, mas para as camadas ocultas é mais complexo, pois o erro deve ser distribuído recursivamente com base nos pesos e na derivada da função de ativação
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20168.png)
                        
                - Modos de aprendizado
                    - A forma como apresentamos os dados e atualizamos os pesos afeta significativamente a convergência e a qualidade da solução
                    - Batch Learning
                        - Os ajustes nos pesos são realizados apenas após a apresentação de todos os N exemplos de treinamento (1 epoch)
                        - Função de custo: minimiza o erro médio quadrático sobre toda a época (Eav)
                        - Estimativa precisa do vetor gradiente (garante convergência para um mínimo local em condições simples) e permite paralelização do processamento
                        - Requer muito armazenamento e pode ser lento se o conjunto de dados for muito grande e redundante
                    - Online Learning
                        - Os pesos são ajustados após a apresentação de **cada** exemplo individual
                        - Função de Custo: Minimiza o erro instantâneo (E(n))
                        - O caráter estocástico (aleatório) da busca torna menos provável que a rede fique presa em mínimos locais. Requer menos memória
                        - O caminho em direção ao mínimo é ruidoso (ziguezagueante) e difícil de paralelizar
                - Funções de Ativação
                    - Para que o gradiente seja calculado e o backpropagation funcione, a função de ativação deve ser diferenciável em todos os pontos
                    - Tipos
                        - Sigmoide (Logística
                            - Mapeia a entrada para o intervalo (0, 1)
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20169.png)
                                
                            - Foi a mais usada historicamente, interpretada como uma taxa de disparo neuronal
                        - Tangente Hiperbólica
                            - Mapeia para (-1, 1)
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20170.png)
                                
                            - Permite valores negativos, o que pode acelerar a convergência em comparação à sigmoide
                        - ReLU (Rectified Linear Unit)
                            - É computacionalmente eficiente e evita o problema do desaparecimento do gradiente para valores positivos
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20171.png)
                                
                        - Leaky ReLU
                            - Permite um pequeno gradiente mesmo quando a unidade não está ativa, evitando neurônios mortos
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20172.png)
                                
                        - Linear
                            - Mapeia a entrada para a saída sem nenhuma transformação não linear
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20173.png)
                                
                            - Frequentemente usada na camada de saída de redes neurais quando o objetivo é resolver problemas de regressão, onde a saída precisa assumir qualquer valor real contínuo
                        - Softmax
                            - Usada na camada de saída para classificação multiclasse
                            - Transforma as saídas em uma distribuição de probabilidade onde a soma de todas as saídas é igual a 1
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20174.png)
                                
                        - ELU (Exponential Linear Unit)
                            - Uma variação da ReLU que resolve o problema dos neurônios mortos
                            - Para valores negativos, usa uma função exponencial que pode melhorar a performance, embora seja computacionalmente mais custosa
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20175.png)
                                
                                - Enquanto que para valores positivos possui o mesmo comportamento da ReLU
                                - Permite valores negativos, introduzindo robustez ao ruído
                        - Maxout
                            - Generalização das funções ReLU e Leaky ReLU
                            - Em vez de aplicar uma função não-linear sobre uma soma ponderada, calcula o máximo entre múltiplas funções lineares diferentes
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20176.png)
                                
                            - É uma função linear por partes, que aprende a própria função de ativação dependendo dos pesos
                    - Comparação
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20177.png)
                        
                - Taxa de Aprendizado e Momentum
                    - O algoritmo Backpropagation é uma aplicação do método de descida do gradiente (Gradient Descent)
                        - A eficiência depende de como navegamos na superfície de erro
                    - Taxa de Aprendizado
                        - Determina o tamanho do passo que damos na direção oposta ao gradiente
                        - Pequena demais: A convergência é suave, mas extremamente lenta
                        - Grande demais: A rede aprende rápido, mas pode se tornar instável, oscilando em torno do mínimo ou até divergindo
                    - Momentum (α)
                        - Para evitar oscilações e acelerar o aprendizado em regiões planas da superficíe de erro, modifica-se a regra de atualização adicionando uma fração de alteração de peso anterior
                            - Age como um objeto com masse descendo uma colina, ganhando inércia
                        - Fórmula
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20178.png)
                            
                            - α é geralmente um número positivo, a constante de momento, suavizando a trajetória no espaço de pesos
                - Generalização
                    - O objetivo final não é zerar erro de treinamento, mas sim ter bom desempenho em dados nunca vistos (generalização)
                    - Overfitting
                        - Se treinar a rede por tempo demais, ela começará a memorizar o ruído dos dados de treinamento
                        - O erro de treino continua caindo, mas o erro em um conjunto de validação começa a subir
                        - Early Stopping
                            - É a técnica de monitorar o erro em um conjunto de validação separado durante o treinamento e parar o processo assim que esse erro começar a aumentar, mesmo que o erro de treinamento continue diminuindo
                            - Evita o Overfitting
                - Critérios de Parada
                    - Usa-se uma combinação, pois não há uma regra única
                        - O erro médio quadrático cair abaixo de um limiar pequeno
                        - A norma do vetor gradiente ser suficientemente pequena (indicando um mínimo)
                        - A taxa de mudança do erro ser muito pequena (estagnação)
    - Preparação dos dados
        - Dados Estruturados
            - MLPs tradicionais funcionam bem com dados tabulares
            - É crucial reescalar os atributos para uma escala padrão para evitar as variáveis com magnetudes grandes dominem a função de custo em relação a variáveis pequenas
            - Técnicas comum incluem a normalização Minmax e Z-Score
        - Dados Não-Estruturados
            - Para entradas como pixels de imagens ou sequências de texto, as MLPs falham pois não capturam a estrutura espacial ou temporal
            - Deep Learning introduz arquiteturas específicas para essas modalidades
    - Redes Neurais Convolucionais (CNNs)
        - São especializadas no processamento de dados com topologia de grade (como imagens), explorando correlações espaciais locais
        - Operação de Convolução
            - Em vez de pesos fixoa para cada entrada, a CNN aprende filtros (ou kernels) que deslizam sobre a imagem
            - Uma convolução é um filtro espacial que opera sobre uma vizinhança S ao redor de um ponto para gerar um valor de saída
                - Matematicamente, para uma imagem I e um kernel g, J(i) = (I * g)(i)
            - Propriedades que tornam as CNNs robustas
                - Campos Receptivos Locais
                    - Cada neurônio se conecta apenas a uma pequena região da entrada, capturando características locais
                - Compartilhamento de Pesos
                    - O mesmo filtro é aplicado em toda a imagem
                    - Se um filtro aprende a detectar uma borda vertical, ele a detectará em qualquer parte da imagem
                    - Isso reduz drasticamente o número de parâmetros livres
                - Subamostragem (Pooling)
                    - Reduz a dimensionalidade e introduz invariância a pequenas translações
        - Hiperparâmetros e Arquitetura
            - Uma camada convolucional transforma um volume de entrada (Wi x Hi x Di) em um volume de saída baseando-se em 4 características
                - Filtros (K), que representa o número de mapaz de características a aprender
                - Tamanho do Kernel (F), dimensão espacial do filtro
                - Stride (S), o passo do deslizamento do filtro na qual passos maiores reduzem a dimensão espacial da saída
                - Padding (P), adição de bordas para manter as dimensões espaciais
        - Pooling (Subamostragem)
            - Geralmente inserido após convoluções para reduzir o custo computacional e controlar overfitting
            - Max Pooling → Seleciona o valor máximo em uma janela (ex: 2×2)
                - É o mais comum pois preserva as características mais salientes
            - Average Pooling → Calcula a média dos valores na janela
        - Arquitetura Típica
            
            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20179.png)
            
    - Modelos de Sequência
        - Redes Neurais Recorrentes (RNNs)
            - Processam informações sequencialmente, mantendo um estado oculto (a^<t>) que funciona como memória do contexto anterior
                - O estado atual depende da entrada atual x^<t> e do estado anterior a^<t-1>
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20180.png)
                    
            - Backpropagation Through Time
                - O treinamento envolve desenrolar a rede no tempo e propagar o erro do final da sequência até o início
                - Isso é equivalente a treinar uma rede muito profunda com pesos compartilhados em cada passo de tempo
            - RNNs sofrem com o problema do desaparecimento de gradiente (vanishing gradient), tornando difícil aprender dependências de longo prazo
        - Arquiteturas Avançadas
            - LSTM (Long Short-Term Memory
                - Introduz "portões" (gates) que regulam o fluxo de informação, permitindo que a rede aprenda o que esquecer e o que manter na memória por longos períodos
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20181.png)
                    
            - Transformers e Atenção
                - A arquitetura moderna dominante (base do BERT/GPT)
                - Utiliza mecanismos de autoatenção para permitir que cada elemento da entrada interaja com todos os outros, ponderando a importância relativa de cada parte do contexto, independentemente da distância sequencial
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20182.png)
                    
    - Otimização e Regularização Avançada
        - Redes profundas têm milhões de parâmetros, o que as torna propensas ao overfitting (alta variância)
        - Técnicas de Regularização
            - Dados
                - Aumentar o dataset é a melhor regularização
                - O Data Augmentation cria novos exemplos artificiais aplicando transformações (rotação, corte, cor) nas imagens originais, ensinando invariâncias à rede
                - Isso pode ser visto como uma técnica para encorajar a invariância a transformações conhecidas
            - Dropout
                - Durante o treinamento, desativa aleatoriamente uma porcentagem de neurônios (ex: 50%)
                - Isso força a rede a não depender de neurônios específicos e cria um efeito de "ensemble" de muitas sub-redes, melhorando a generalização
            - Early Stopping
                - Monitora o erro em um conjunto de validação e para o treinamento quando esse erro começa a subir, prevenindo que a rede "decore" o ruído dos dados de treino
            - Regularização L1/L2 (Weight Decay)
                - Adiciona uma penalidade à função de custo proporcional à magnitude dos pesos, forçando a rede a manter pesos pequenos e modelos mais simples
    - Ataques Adversariais
        - As Redes Adversariais (Ataques Adversariais) representam uma área crucial na segurança de sistemas de Aprendizado de Máquina (ML)
            - Esses ataques exploram vulnerabilidades nos modelos ao criar entradas levemente perturbadas que levam a classificações incorretas, seguindo um roteiro bem definido que se baseia em explorar as fronteiras de decisão dos modelos
        - O cerne dos ataques adversariais é a não-robustez dos modelos de ML, especialmente Redes Neurais, em relação a pequenas perturbações nos dados de entrada
        - Um ataque bem sucedido envolve a criação de uma amostra adversarial x’ adicionando uma pequena perturbação δ a uma amostra original e legítima x
            - x’ = x + δ
            - O objetivo é que o modelo f classifique incorretamente x’, ou seja, f(xadv) ≠ f(x), enquanto x’ permanece visualmente idêntica a x para um observador humano
            - O problema é formalmente estabelecido como um desafio de otimização que busca a perturbação mínima (δ) que garanta a misclassificação
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20183.png)
                
            - A vulnerabilidade reside no fato de que, embora as redes neurais formem fronteiras de decisão complexas e não-lineares, a alta dimensionalidade do espaço de entrada (como em imagens) torna essas fronteiras muito próximas aos dados de treinamento
                - Uma minúscula modificação (o δ) pode ser suficiente para mover o ponto de entrada através da superfície de decisão e induzir um erro
        - O conjunto de técnicas para encontrar pertubações adversariais e construir amostras adversariais são chamadas de Ataques Adversariais
        - Taxonomia
            - Os ataques são categorizados de acordo com três dimensões principais
            - Propósito do Ataque
                - Determina a intenção final do adversário
                - Evasão (Evasion)
                    - Criar uma amostra adversarial (x′) que o modelo misclassifique durante a inferência (tempo de teste)
                    - É a forma mais comum de ataque.
                - Envenenamento (Poisoning)
                    - Inserir amostras maliciosas no conjunto de treinamento para corromper o modelo final, explorando a fase de aprendizado
                - Trojan/Backdoor
                    - Inserir funcionalidade oculta que é ativada por um "gatilho" específico
                - Inferência de modelo (Model Inference)
                    - Tentar roubar a arquitetura ou os parâmetros do modelo original
                - Inferência de pertencimento de dados (Membership Inference)
                    - Determinar se um determinado ponto de dados foi incluído no conjunto de treinamento (uma preocupação de privacidade)
            - Alvo do Ataque
                - Define o resultado desejado da misclassificação
                - Com Alvo (Targeted)
                    - Forçar o modelo a classificar x′ como uma classe alvo específica escolhida pelo atacante (ex: fazer um "gato" ser classificado como "cachorro")
                - Sem Alvo (Untargeted)
                    - Simplesmente fazer o modelo misclassificar x′ para qualquer classe incorreta
            - Conhecimento do Atacante
                - Refere-se ao nível de informação que o atacante possui sobre o modelo alvo
                - White-box (Caixa Branca)
                    - O atacante tem conhecimento completo do modelo, incluindo sua arquitetura, todos os seus parâmetros (pesos) e a função de perda (loss function) usada no treinamento
                    - Os ataques de caixa branca aproveitam a diferenciabilidade dos modelos, especialmente das Redes Neurais Convolucionais (CNN), utilizando métodos baseados em gradiente para calcular a perturbação δ na direção que maximiza o erro (ou seja, descida do gradiente no espaço de perda do modelo, mas subida do gradiente no espaço de entrada x)
                    - Métodos
                        - Fast Gradient Signed Method (FGSM)
                            - Este é um dos métodos não-iterativos mais simples e eficientes, na qual a perturbação é calculada a partir do gradiente da função de perda J em relação à entrada x
                            - Fórmula
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20184.png)
                                
                                - sign(⋅) é o operador que usa apenas o sinal do gradiente
                                - ∇xJ(θ, x, l) é o gradiente da função de perda J em relação à entrada x (mantendo os parâmetros θ fixos)
                                - ϵ é o tamanho da perturbação (norma máxima de restrição)
                            - Algoritmo
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20185.png)
                                
                        - Ataques Iterativos (Iterative White-Box Attacks)
                            - Refinam a perturbação ao longo de múltiplos passos, resultando em perturbações mais fortes e menores
                            - Basic Iterative Method (BIM)
                                - Aplica o FGSM em pequenos passos (β) por um número N de iterações, garantindo que a perturbação acumulada total não exceda o limite ϵ
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20186.png)
                                    
                            - Projected Gradient Descent (PGD)
                                - Uma variação poderosa que, em cada passo, projeta a perturbação de volta para um limite (tipicamente uma L∞-norma) se exceder ϵ
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20187.png)
                                    
                            - Momentum Iterative Method (MIM)
                                - Incorpora o conceito de Momentum, tipicamente usado para acelerar e estabilizar o treinamento, na direção do ataque
                                - O gradiente acumulado (vetor de velocidade) é usado para guiar a perturbação, o que ajuda a escapar de mínimos locais na superfície de erro e resulta em ataques mais transferíveis
                                    
                                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20188.png)
                                    
                - Black-box (Caixa Preta)
                    - O atacante tem conhecimento limitado, tendo acesso apenas às entradas e saídas (previsões) do modelo
                    - Nestes cenários, o atacante deve tentar inferir informações do modelo sem acesso direto ao gradiente
                        - Isso é feito tipicamente através de consultas (queries)
                    - Cenários de Ataque
                        - Os ataques de caixa preta são frequentemente categorizados pela natureza do acesso do atacante
                        - Query-limited
                            - O atacante é restrito ao número de vezes que pode consultar o modelo
                        - Partial-information
                            - O atacante pode obter as pontuações de confiança (scores) ou as probabilidades de classe
                        - Decision-based
                            - O atacante recebe apenas a classificação final (a decisão)
                    - Algoritmos Black-Box por Busca
                        - Square Attack
                            - Um método eficiente que utiliza busca aleatória para modificar blocos quadrados na imagem de entrada
                            - A perturbação é feita iterativamente, e a cada passo, a função de perda L do classificador é avaliada para guiar a busca por um minimizador aproximado
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20189.png)
                                
                        - SimBA (Simple Black-box Adversarial Attack)
                            - Um ataque simples que usa pesquisa de pixel-a-pixel
                            - Ele escolhe aleatoriamente uma direção ortogonal no espaço de entrada e testa se a adição ou subtração de uma perturbação α naquela direção reduz a probabilidade da classe correta
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20190.png)
                                
        - Estratégias de Defesa e Robustez
            - A defesa contra ataques adversariais visa tornar os modelos mais **robustos** e suas fronteiras de decisão mais suaves, dificultando que pequenas perturbações causem misclassificações
            - Mecanismos de Defesa
                - Knowledge and Access Protection (Proteção de Acesso)
                    - Medidas de segurança para dificultar a obtenção de informações para um ataque de caixa branca, como ocultar a arquitetura e limitar o número de solicitações (queries) ao modelo
                - Detecting and Removing Adversarial Perturbations (Detecção e Remoção)
                    - Inclui sistemas que tentam identificar se a entrada foi adulterada ou usar modelos denoising (remoção de ruído) para tentar restaurar a entrada original
                - Smoothing Decision Boundaries (Suavização de Fronteiras)
                    - Gaussian Noise Augmentation (GNA)
                        - Aumenta a regularidade das funções de mapeamento, o que ajuda a prevenir o overfitting e a suavizar as fronteiras
                    - Label Smoothing (LS)
                        - Em vez de usar rótulos "rígidos", como 1 para a classe correta e 0 para as outras, o label smoothing modifica os rótulos para uma distribuição mais "suave"
                        - Por exemplo, em vez de 1 e 0, o modelo pode ser treinado para prever cerca de 1 − ϵ para a classe correta e distribuir uma pequena porção ϵ uniformemente entre as outras classes
                - Enhancing Models (Aprimoramento do Modelo)
                    - Adversarial Training (Treinamento Adversarial)
                        - É considerada uma das defesas mais eficazes
                        - Consiste em treinar o modelo em um conjunto de dados que inclui amostras adversariais geradas durante o treinamento
                        - Isso injeta no modelo conhecimento sobre as direções de ataque, levando à aprendizagem de fronteiras de decisão mais robustas
                - Multiple Models (Modelos Múltiplos)
                    - Utiliza técnicas como Ensembles (comitês) onde a previsão final é determinada pelo voto majoritário de vários modelos independentes
                    - Isso é eficaz porque o erro de um comitê é menor se os erros dos modelos individuais não forem correlacionados, o que adiciona uma camada de resistência às perturbações
    - Autoencoders (AE)
        - São redes neurais projetadas para aprender representações codificadas dos dados de entrada, de forma não supervisionada
            
            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20191.png)
            
        - Arquitetura
            - É composto por duas funções principais
                - Encoder (z = f(x)) → comprime a entrada x em uma representação latente z (código)
                - Decoder (X̂ = g(z)) → reconstrói a entrada a partir do código latente z, gerando uma aproximação X̂
            - A rede é treinada minimizando uma função de perda de reconstrução, tipicamente o MSE
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20192.png)
                
            - Se o encoder e o decoder forem lineares e a função de perda for o MSE, o AE aprende o mesmo subespaço que o PCA
                - No entanto, ao introduzir não-linearidades (camadas ocultas com ativações como sigmoide ou ReLU) o AE pode aprender variedades não-lineares complexas, superando o PCA
        - Bottleneck
            - Para que o aprendizado seja útil, impões-se um gargalo na rede
                - Sem isso, a rede poderia simplesmente aprender a função identidade sem extrair características significativas
                - Autoencoders Sobcompletos → a dimensão do espaço latente z é menor que a entrada x
                    - Isso força a rede a capturar as características mais salientes dos dados
                - Autoencoders Sobrecompletos → a dimensão latente é maior que a entrada
                    - Para evitar que a rede apenas copie os dados (overfitting), é necessário o uso de regularização
                    - Regularização L1/L2 → adição de termos de penalidade na função de custo (Weight Decay), o que incentiva pesos pequenos e modelos mais simples
        - Tipos
            - Denoising Autoencoders (DAE)
                - O modelo é treinado para reconstruir a entrada original x a partir de uma versão corrompida x̃
                - Isso força o modelo a aprender a estrutura robusta dos dados e a projetar as entradas de volta para a variedade correta dos dados
            - Convolutional Autoencoder
                - Este tipo de autoencoder substitui as camadas totalmente conectadas (densas) por camadas de convolução, sendo ideal para processamento de imagens
                - O encoder utiliza camadas convolucionais para extrair características espaciais da imagem de entrada, reduzindo sua dimensionalidade (downsampling) até chegar ao gargalo (bottleneck)
                    - O decoder utiliza camadas de convolução transposta (frequentemente chamadas de DeConv) para fazer o processo inverso (upsampling), reconstruindo a imagem original a partir do código latente
                - São excelentes para preservar a estrutura espacial dos dados e são amplamente utilizados em tarefas de visão computacional, como remoção de ruído em imagens e compressão
            - Multilayer Autoencoder
                - Também conhecido como Deep Autoencoder, este modelo estende a arquitetura básica adicionando mais camadas ocultas tanto no codificador quanto no decodificador
                - Enquanto um autoencoder com apenas uma camada oculta linear se comporta de forma semelhante à Análise de Componentes Principais (PCA), a adição de camadas extras com funções de ativação não-lineares (como sigmoide ou ReLU) permite que a rede aprenda relações muito mais complexas
                - Essa arquitetura permite realizar uma redução de dimensionalidade não-linear
                    - A rede pode ser vista como dois mapeamentos funcionais sucessivos: o primeiro projeta os dados em um subespaço (possivelmente não-linear) e o segundo mapeia de volta para o espaço original
            - Regularized Autoencoder
                - Este tipo de autoencoder utiliza técnicas de regularização na função de custo (loss function) para evitar o overfitting (sobreajuste) e forçar o modelo a aprender características úteis, em vez de apenas copiar a entrada para a saída
                - O modelo ideal deve obter uma boa representação dos dados sem simplesmente "decorar" a entrada
                    - A regularização ajuda a balancear o erro de reconstrução com a complexidade do modelo
                - Técnicas comuns incluem a adição de penalidades à função de custo, como a Regularização L1 ou L2 (penalizando a magnitude dos pesos) ou a Divergência de Kullback-Leibler (KL) (usada para forçar a distribuição do espaço latente a se assemelhar a uma distribuição específica, fundamental em Variational Autoencoders)
            - Sparse Autoencoder
                - O Sparse Autoencoder é uma variante que impõe uma restrição de esparsidade nas unidades da camada oculta (espaço latente)
                - A ideia é fazer com que a maioria dos neurônios na camada oculta esteja inativa (com saída zero ou próxima de zero) para qualquer dada entrada
                    - Apenas um pequeno número de neurônios deve ser ativado para representar uma amostra específica
                - Geralmente, autoencoders tentam comprimir dados usando um gargalo menor que a entrada (Undercomplete)
                    - No entanto, o Sparse Autoencoder permite o uso de um espaço latente maior que a entrada (Overcomplete)
                    - Sem a restrição de esparsidade, um autoencoder sobrecompleto apenas copiaria a entrada
                    - A esparsidade força a rede a aprender características únicas e estruturas latentes interessantes nos dados, mesmo com uma grande dimensão no gargalo
            - Variational Autoencoder (VAE)
                - Os Autoencoders tradicionais geram um espaço latente descontínuo, o que dificulta a geração de novos dados via interpolação
                    - Os VAEs resolvem isso introduzindo uma abordagem probabilística
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20193.png)
                        
                - Em vez de mapear a entrada para um ponto fixo no espaço latente, o VAE mapeia a entrada para uma distribuição de probabilidade (geralmente Gaussiana)
                    - Encoder Probabilístico (p0(x | z)) → reconstrói x a partir da amostra z
                - Função de Custo (ELBO)
                    - O treinamento maximiza o Evidence Lower Bound (ELBO), que consiste em dois termos conflitantes
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20194.png)
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20195.png)
                        
                    - Erro de reconstrução → maximiza a verossimilhança dos dados, fazendo X̂ ≈ X
                    - Divergência de Kullback-Leibler (DKL)
                        - Regulariza o espaço latente, forçando a distribuição aprendida q(z | x) a ser próxima de uma distribuição a priori p(z) (geralmente uma gaussiana normal padrão N(0, 1))
                        - Isso garante que o espaço latente seja contínuo e suave, permitindo a geração de dados válidos ao amostrar de p(z)
                - Reparametrização
                    - Para permitir o treinamento via backpropagation através do processo de amostragem aleatória (que não é diferenciável), utiliza-se o truque da reparametrização
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20196.png)
                        
                    - Isso move a estocasticidade para a variável auxiliar ϵ, permitindo calcular gradientes em relação a μ e σ
                - Limitações
                    - Suavização excessiva dos dados gerados
                    - Ajusta o espaço latente à distribuição gaussiana multivariada
    - Generative Adversarial Networks (GANs)
        - Enquanto VAEs usam densidade explícita / aproximada, as GANs utilizam uma abordagem de densidade implícita baseada em teoria dos jogos para gerar dados de altíssima qualidade
        - Jogo adversarial
            - O sistema é composto por duas redes neurais que competem entre si
            - Gerador (G)
                - Tenta criar dados falsos (G(z)) a partir de um ruído aleatório z que sejam indistinguíveis dos dados reais
                - Seu objetivo é "enganar" o discriminador
            - Discriminador (D)
                - Um classificador binário que recebe tanto dados reais (x) quanto dados falsos (G(z)) e tenta distinguir qual é qual
        - Função Objetivo Minmax
            - O treinamento é formulado como um jogo de soma zero minimax com a seguinte função valor V(D,G)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20197.png)
                
            - O Discriminador quer maximizar essa função: D(x) ≈ 1 (para reais) e D(G(z)) ≈ 0 (para falsos)
            - O Gerador quer minimizar essa função: quer que D(G(z)) ≈ 1 (enganar o discriminador)
        - Processo de Treinamento
            - O treinamento ocorre de forma alternada
            - Fixa-se G e treina-se D para classificar corretamente reais vs. falsos (Gradiente Ascendente)
            - Fixa-se D e treina-se G
                - Na prática, em vez de minimizar log(1−D(G(z))), maximiza-se log(D(G(z))) para evitar gradientes saturados (muito pequenos) no início do treino, quando o gerador é ruim e o discriminador vence facilmente
            - O equilíbrio ideal (Equilíbrio de Nash) ocorre quando o gerador produz dados perfeitos e o discriminador não consegue mais distinguir, resultando em D(x) = 0.5 para qualquer entrada
- Modelos de Linguagem e NLP
    - Um modelo de linguagem é uma distribuição de probabilidade sobre sequências de palavras
    - A tarefa fundamental é estimar a probabilidade de um próximo termo (wt) dado o histórico de termos anteriores (w1, …, wt-1)
        - Ou seja, P(wt | w1, …, wt-1)
        - O modelo aprende padrões de coocorrência
            - Exemplo: se a frase é "O gato subiu no", o modelo atribui uma alta probabilidade à palavra "telhado" e baixa a "carro", baseando-se em estatísticas de corpus textuais
        - Dados sequenciais (como linguagem) violam a suposição i.i.d (independente e indeticamente distribuído) comum em modelos simples, portanto, modelos de linguagem devem capturar correlações entre observações próximas e distantes na sequência
    - Estratégias de Treinamento
        - Para treinar modelos robustos utilizam-se tarefas que forçam o modelo a aprender contexto semântico e sintático sem a necessidade de dados rotulados manualmente (aprendizado auto-supervisionado)
        - Masked Languagem Modeling (MLM)
            - Diferente da modelagem tradicional que prevê a próxima palavra (unidirecional), o MLM permite aprendizado bidirecional.
            - Oculta-se uma palavra da frase com um token especial [MASK]
                - O objetivo é prever a palavra original observando todo o contexto (à esquerda e à direita) simultaneamente
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20198.png)
                    
            - O modelo utiliza informações de "O gato" e "no telhado" para inferir a ação, criando uma representação mais rica do que apenas olhar para o passado
        - Next Sentence Prediction (NSP)
            - Esta tarefa ensina o modelo a entender relacionamentos de longo prazo e coerência entre sentenças, essencial para tarefas como "Perguntas e Respostas"
            - O modelo recebe par de frases (A, B) e deve classificar a relação em IsNext (B segue logicamente A) ou NotNext (B é uma frase aleatória sem conexão com A)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20199.png)
                
    - Evolução das Arquiteturas Neurais para Texto
        - Redes Recorrentes (RNNs/LSTMs)
            - Processam palavras sequencialmente
            - RNNs utilizam feedback para manter um "estado interno" (memória), mas sofrem com o problema do desaparecimento do gradiente em sequências longas
        - CNNs para Texto
            - Exploram janelas locais de palavras, capturando padrões semelhantes a n-gramas
        - Transformers
            - A arquitetura atual de ponta (base do BERT e GPT)
            - Utilizam mecanismos de atenção para modelar relações globais entre todas as palavras de uma vez, permitindo paralelização massiva e captura de dependências de longo alcance
    - Word Embeddings (Representações Vetoriais)
        - A base para o funcionamento dessas redes é transformar palavras (símbolos discretos) em vetores contínuos (v ∈ R^d)
        - Word2Vec
            - Técnica pioneira que aprende embeddings baseando-se na hipótese distribucional, palavras que aparecem em contextos similares possuem significados similares
            - As palavras são mapeadas em um espaço vetorial onde a proximidade geométrica reflete proximidade semântica
                - Operações algébricas vetoriais revelam analogias
            - Arquitetura
                - É uma rede neural rasa (shallow)
                - Componentes
                    - Camada de Entrada
                        - Representação one-hot da palavra (vetor esparso)
                    - Camada Oculta (Linear)
                        - Não possui função de ativação não-linear (como sigmoide ou ReLU)
                        - A matriz de pesos W ∈ R^V x N desta camada contém os próprios embeddings que queremos aprender
                    - Camada de Saída (Softmax)
                        - Produz uma distribuição de probabilidade sobre o vocabulário
                        - Função
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20200.png)
                            
            - Variantes de Treinamento
                - Existem duas formas principais de treinar o Word2Vec
                - CBOW (Continuous Bag of Words)
                    - Tenta prever a palavra central baseada nas palavras de contexto (vizinhas)
                - Skip-gram
                    - Faz o inverso da CBOW
                    - Dada a palavra central, tenta prever as palavras do contexto
                    - Tende a funcionar melhor para palavras raras
        - BERT
            - O Word2Vec á uma grande limitação, pois ele gera embeddings estáticos
                - Exemplo: a palavra “banco” terá o mesmo vetor na frase “sentei no banco” e fui ao “banco sacar dinheiro”
                - Modelos de linguagem modernos como o BERT geram embeddings contextuais, onde a representação vetorial de “banco” muda dinamicamente dependendo das palavras ao seu redor
                - Com isso, o BERT é baseado na arquitetura Transformer
            - Mecanismo de Self-Attention
                - É o coração do BERT e do Transformer
                - Permite que cada palavra pondere a importância de todas as outras palavras na frase para construir sua própria representação
                - Para cada palavra xi, o modelo aprende três projeções lineares (matrizes de pesos) que geram 3 vetores
                    - Query (Q) → O que a palavra está procurando
                    - Key (K) → O que a palavra oferece como conteúdo
                    - Value (V) → o conteúdo informacional da palavra
                - Cálculo da Atenção
                    - A atenção é calculada comparando a Query de uma palavra com as Keys de todas as outras
                    - Similaridade
                        - Calcula-se o produto escalar entre Qi e Kj
                        - Um valor alto indica alta relevância (atenção) entre as palavras i e j
                    - Escalonamento e Normalização
                        - O produto é dividido por √dk para estabilidade dos gradientes e depois passa por uma função Softmax para gerar pesos que somam 1
                    - Soma ponderada
                        - O vetor de saída é a soma dos vetores Value (Vj) ponderados pelos pesos de atenção calculados (αij)]
                    - Fórmula final
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20201.png)
                        
                        - Softmax expandido
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20202.png)
                            
                    - Exemplo
                        - Na frase “O cliente foi ao banco sacar dinheiro”, ao processar “banco”, o mecanismo de atenção atribuirá um peso α alt para as palavras “sacar” e “dinheiro”, injetando o contexto financeiro na representação final de “banco”
- Explicabilidade de Modelos (xAI)
    - A explicabilidade (ou interpretabilidade) tornou-se um requisito não funcional crítico no desenvolvimento de sistemas de IA
        - Em domínios onde decisões automatizadas afetam a vida humana (como crédito, justiça criminal e diagnósticos médicos), leis como o GDPR na Europa exigem o "direito à explicação"
        - Modelos complexos ("caixas-pretas") precisam ser auditados para garantir que não estão discriminando grupos minoritários ou operando com base em correlações espúrias
        - Para que especialistas (ex: médicos) adotem uma ferramenta de IA, eles precisam confiar que o raciocínio do modelo é sólido e alinhado com o conhecimento do domínio
    - Taxonomias dos Métodos de Interpretabilidade
        - Quanto ao Momento de Aplicação
            - Métodos Intrísecos (Ante-hoc)
                - A interpretabilidade é obtida restringindo a complexidade do modelo antes do treinamento
                - Exemplos
                - Regressão Linear (os pesos indicam a relação direta)
                - Árvores de Decisão (o caminho da raiz à folha é a explicação)
                - Sistemas Baseados em Regras
                - Trade-off
                    - embora árvores de decisão sejam legíveis por humanos, elas podem sofrer de overfitting se crescerem demais
                    - Frequentemente, há uma perda de acurácia preditiva ao se optar por modelos intrinsecamente simples em vez de modelos complexos como redes neurais profundas
            - Métodos Post-hoc
                - Aplicam-se técnicas de análise *após* o treinamento de um modelo complexo
                - O objetivo é manter a alta performance do modelo "caixa-preta" (como uma rede neural profunda ou um ensemble) e extrair explicações sobre seu comportamento
        - Quanto à Dependência do Modelo
            - Agnósticos (Model-Agnostic)
                - Podem ser aplicados a qualquer algoritmo de ML
                - Tratam o modelo como uma função f(x) desconhecida, analisando apenas a relação entre entradas e saídas
                - Isso é vantajoso pois separa a explicação da implementação do modelo
            - Não-Agnósticos (Model-Specific)
                - Exploram estruturas internas específicas, como os pesos em uma Regressão Linear, a impureza de Gini em Árvores de Decisão ou os gradientes e ativações de filtros em Redes Neurais Convolucionais (CNNs)
        - Quanto ao Escopo
            - Global
                - Tenta explicar o comportamento do modelo como um todo
                    - Responde à pergunta: "Como o modelo toma decisões em média?"
                - Exemplos incluem a importância global de atributos
                - O desafio aqui é que, para modelos não-lineares com muitas variáveis, uma explicação global pode ser uma simplificação excessiva da realidade
            - Local
                - Foca em explicar uma previsão específica para uma única instância
                    - Responde: "Por que o modelo negou crédito para o cliente X?"
                - Em muitos casos, o comportamento local de uma função complexa pode ser aproximado linearmente, tornando a explicação local mais fiel do que a global
                - Existe também a interpretação para Grupos de Instâncias, focada em fairness (justiça) e comportamento do modelo em subpopulações (ex: gênero ou raça)
    - Métodos Agnósticos Globais
        - Estes métodos tentam entender a importância geral das variáveis no modelo
        - Permutation Feature Importance
            - Este método mede o aumento no erro de predição do modelo após permutar (embaralhar) os valores de um atributo
            - Calcula-se o erro original do modelo no conjunto de dados
            - Para cada atributo j gera-se uma nova matriz de dados onde a coluna j é permutada aleatoriamente (quebrando a relação entre o atributo e o alvo)
            - Calcula-se o erro na base permutada
            - A importância é a diferença (ou razão) entre o erro permutado e o erro original
            - Se o erro aumentar muito, o atributo era importante, caso contrário, o atributo era irrelevante
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20203.png)
                
        - Partial Dependence Plots (PDP)
            - O PDP mostra o efeito marginal de um ou dois atributos no resultado previsto pelo modelo
            - Para calcular a dependência parcial de um atributo xs, marginaliza-se sobre os valores de todos os outros atributos xc
            - Na prática, fixa-se um valor para xs e calcula-se a média das previsões do modelo para todos os exemplos do dataset, mantendo os outros atributos inalterados
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20204.png)
                
    - Métodos Agnósticos Locais
        - Individual Conditional Expectation (ICE)
            - É o equivalente “local” do PDP
                - Enquanto o PDP mostra a média das predições, o ICE plota uma linha para cada instância do dataset
            - Revela interações heterogêneas que o PDP pode esconder
                - Por exemplo, se um atributo aumenta a predição para metade dos dados e diminui para a outra metade, o PDP mostraria uma linha reta (efeito médio zero), enquanto o ICE mostraria o comportamento divergente das curvas individuais
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20205.png)
                    
        - Local Surrogate (LIME)
            - O Local Interpretable Model-agnostic Explanations (LIME) baseia-se na premissa de que modelos complexos são linearmente separáveis em uma vizinhança local muito pequena
            - Procedimento
                - Escolhe-se a instância de interesse x que se deseja explicar
                - Gera-se um novo conjunto de dados artificial perturbando x (amostrando pontos ao redor de x)
                - Obtêm-se as predições do modelo "caixa-preta" para esses pontos artificiais
                - Ponderam-se os pontos artificiais pela sua proximidade com x (pontos mais próximos têm peso maior)
                - Treina-se um modelo simples e interpretável (como Regressão Linear ou Árvore de Decisão) com esses dados ponderados
            - Os pesos do modelo simples servem como explicação para a decisão do modelo complexo naquela instância específica (ex: a palavra "channel" teve peso alto para classificar um comentário como spam)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20206.png)
                
        - Shapley Values (SHAP)
            - Baseado na Teoria dos Jogos, este método atribui a cada atributo um valor de "payout" (contribuição) para a predição final
            - O valor de Shapley de um atributo é a média da contribuição marginal desse atributo através de todas as combinações (coalizões) possíveis de atributos
            - É o único método de atribuição que satisfaz propriedades matemáticas de eficiência, simetria e aditividade
                - Ele explica a diferença entre a predição atual e a predição média do modelo
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20207.png)
                    
    - Explicações Baseadas em Exemplos
        - Em vez de usar pesos ou gráficos, esses métodos explicam o modelo selecionando instâncias de dados
        - Contrafactuais: Descrevem a menor mudança necessária na entrada para alterar a predição (ex: "Se você aumentasse sua renda em R$ 500, seu empréstimo seria aprovado")
        - Exemplos Adversariais: Entradas criadas intencionalmente para enganar o modelo, revelando fragilidades na fronteira de decisão
        - Protótipos: Seleção de instâncias representativas de uma classe para justificar a classificação de um novo exemplo
        - Instâncias Influentes: Identifica quais exemplos de treinamento mais impactaram a decisão do modelo ou a criação dos parâmetros
    - Propriedades de uma Boa Explicação
        - Para avaliar a qualidade das explicações geradas, consideram-se diversas métricas qualitativas e quantitativas
            - Acurácia: Quão bem a explicação prevê dados não vistos
            - Fidelidade: Quão bem a explicação aproxima o comportamento do modelo "caixa-preta"
                - Uma explicação pode ter alta fidelidade local mas baixa fidelidade global
            - Consistência: Modelos diferentes com performance similar devem gerar explicações similares
            - Estabilidade: Pequenas mudanças na entrada não devem causar mudanças drásticas na explicação
            - Inteligibilidade: O grau em que a explicação é compreensível para um humano (ex: uma árvore de decisão com 5 nós é mais inteligível que uma com 500)
            - Certeza: A explicação deve refletir a incerteza do modelo
            - Grau de Importância: A explicação deve refletir a real importância das variáveis
            - Novidade: Capacidade de indicar se a instância é um outlier ou está longe da distribuição de treinamento
            - Representatividade: Quantas instâncias a explicação cobre
- Resolução de problemas de busca
    - A resolução de problemas em IA é o processo de encontrar uma sequência de ações que leve de um estado inicial a um estado objetivo desejado
        - A formulação precisa é o primeiro passo crítico
    - Componentes de um Problema de Busca
        - Um problema é formalmente definido por quatro componentes essenciais
        - Espaço de Estados
            - Conjunto de todos os estados alcançáveis a partir di estado inicial através de qualquer sequência de ações
            - Pode ser visualizado como um grafo onde os nós são estados e as arestas são ações
        - Estado Inicial
            - O estado em que o agente se encontra antes de realizar qualquer ação
        - Ações (Operadores)
            - O conjunto de operações disponíveis para o agente que causam uma transição de estado
        - Teste de Término (Objetivo)
            - Uma condição que determina se um determinado estado é o estado objetivo
            - O objetivo pode ser específico ou uma propriedade abstrata
    - Custo e Solução
        - Custo do Caminho
            - Uma função numérica que atribui um custo a cada caminho
            - Geralmente é a soma dos custos das ações individuais ao longo do caminho
            - Funções de custo diferentes podem levar a soluções ótimas diferentes
        - Solução
            - É uma sequência de ações (caminho) que leva do estado inicial a um estado que satisfaz o teste de término
        - Custo Total
            - Envolve o Custo de Busca (tempo e memória gastos para encontrar a solução) somado ao Custo do Caminho (custo para executar a solução)
            - Existe um trade-off entre encontrar a solução ótima e o esforço computacional gasto para achá-la
    - Processo de Busca
        - É o processo computacional que explora o espaço de estados para encontrar a solução
        - Algoritmo Geral de Busca
            - Ocorre através da construção de uma árvore de busca sobreposta ao espaço de estados
            - A distinção crucial é entre nós explorados e a Fronteira (lista de nós a serem expandidos)
                - Inicialmente a fronteira contém apenas o estado inicial do problema
            - Algoritmo de Geração e Teste
                - Selecionar o primeiro nó (estado) da fronteira do espaço de estados
                    - Se a fronteira está vazia, o algoritmo termina com falha
                - Testar se o nó selecionado é um estado final (objetivo)
                    - Se “sim”, então retornar nó (a busca termina com sucesso)
                - Gerar um novo conjunto de estados aplicando ações ao estado selecionado
                - Inserir os nós gerados na fronteira, de acordo com a estratégia de busca usada, e voltar para o passo (1)
            - Implementação do Algoritmo
                - Espaço de Estado
                    - Pode ser representado como uma árvore onde os estados são nós e as operações são arcos
                - Os nós da estrutura de dados da busca contém mais informações que o estado, possuindo 3 componentes
                    - Estado → configuração correspondente ao nó
                    - Lista de estados daquele caminho
                    - Custo do nó desde a raiz g(n)
                - Função-Insere
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20208.png)
                    
    - Métodos de Busca
        - Critérios de Avaliação
            - Completude → a estratégia sempre encontra uma solução quando existe alguma?
            - Qualidade (Otimalidade) → a estratégia encontra a melhor solução quando existem soluções?
                - Solução de menor custo de caminho
            - Custo do Tempo → quanto tempo gasta para encontrar a 1ª solução?
            - Custo de Memória → quanta memória é necessária para realizar a busca?
        - Busca Exaustiva (Cega, Não Informada)
            - Não possui informação sobre o quão próximo um estado está do objetivo, eles apenas sabem gerar sucessores e testar o objetivo
            - BFS
                - Expande o nó mais raso da fronteira
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20209.png)
                    
                - A fronteira é implementada como uma fila (FIFO)
                - Ordem: Raiz → Nível 1 → Nível 2
                - Completude → sim, encontra a solução se ela existir (e o fator de ramificação for finito)
                - Otimalidade → é ótima apenas se todos os custos das ações forem iguais
                    - Garante encontrar a solução com o menor número de passos (mais rasa)
            - Busca de Custo Uniforme
                - Expande o nó com o menor custo de caminho acumulado g(n) na fronteira
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20210.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20211.png)
                    
                - Ao contrário da busca em largura, ela leva me conta custos de arestas variados
                - Otimalidade
                    - É ótima desde que os custos das ações sejam não-negativos (g nunca decresce ao longo de um caminho)
                    - Se houvesse custos negativos, o algoritmo precisaria explorar exaustivamente para garantir que um caminho longo não se tornasse barato subitamente
            - DFS
                - Expande o nó no nível mais profundo da árvore atual
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20212.png)
                    
                - A fronteira é uma pilha (LIFO)
                - Memória muito eficiente (O(b⋅m)), pois armazena apenas o caminho atual e os irmãos dos nós no caminho
                - Completude e Otimalidade
                    - Não é completa, pois pode entrar em loops infinitos ou descer caminhos infinitos sem solução
                    - Não é ótima, pois pode encontrar uma solução longa antes de uma curta
        - Busca Heurística (Informada)
            - Utiliza conhecimento específico do problema para estimar qual nó é mais promissor, tornando a busca mais eficientes
            - Função Heurística
                - A base da busca informada é a função heurística h(n), que estima o custo do caminho mais barato do nó n até o objetivo
                - Uma heurística é admissível se nunca se superestima o custo real para atingir o objetivo
            - Busca Gulosa
                - Expande o nó que parece estar mais próximo do objetivo, ou seja, minimiza h(n)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20213.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20214.png)
                    
                - Semelhante ao DFS no sentido de seguir um único caminho promissor
                - Não é ótima, pois pode cair em mínimos locais ou escolher caminhos que parecem curtos mas não longos no total
                - Não é completa, pois é sujeita a loops
                - Custo de tempo e memória é O(b^d), pois guarda todos os nós expandidos na memória
            - Algoritmo A* (A-Star)
                - O A* é o algoritmo de busca mais popular, combinando a robustez da busca de custo uniforme (g) com a eficiência da busca gulosa (h)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20213.png)
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20215.png)
                    
                - Função de avaliação: f(n) = g(n) + h(n)
                    - g(n) → custo real do início até n
                    - h(n) → custo estimado de n até o objetivo
                    - f(n) → custo total estimado da solução passando por n
                - Se h(n) for admissível, o A* é ótimo e completo, pois f(n) é admissível também
                    - f nunca irá superestimar o custo real da melhor solução através de n, pois g guarda o valor exato do caminho já percorrido
                - Expande o menor número de nós necessário entre os algoritmos que usam a mesma heurística, expandindo apenas nós onde f(n) ≤ C* (custo da solução ótima)
            - Construção e Aprendizado de Heurísticas
                - A eficiência do A* depende da qualidade da heurística h(n), se for muito próxima do custo real, a busca é quase direta
                    - Para encontrar a solução ótima, a heurística escolhida não pode superestiamr o custo real para chegar ao objetivo
                    - Uma heurística é admissível se 0 ≤ h(n) ≤ h*(n), onde h*(n) é o custo real do caminho ótimo de n até o objetivo
                        - Se h(n) superestimar o custo, o algoritmo pode achar que um caminho promissor é muito caro e acabar escolhendo um caminho pior, perdendo a otimalidade
                    - Se h(n) = 0, o A* vira uma Busca de Custo Uniforme
                    - Dominância → se tivermos duas heurísticas, h1 e h2, e para todo nó n do grafo vale que h2(n) ≥ h1(n), dizemos que h2 domina h1
                    - Impacto → o A* usando h2 (a heurística dominante) expandirá menos nós do que usando h1
                        - Isso ocorre porque h2 guia a busca de forma mais estreita em direção ao objetivo, descartando caminhos inúteis mais cedo
                        - O limite perfeito é quando h(n) é exatamente igual ao custo real, nesse caso a busca vai direto ao objetivo sem erros
                - Estratégias para criar heurísticas
                    - Relaxamento do Problema
                        - Uma forma de inventar heurísticas admissíveis é relaxar as restrições do problema original
                            - O custo da solução exata para um problema relaxado é uma boa heurística para o problema original
                            - Exemplo
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20216.png)
                                
                                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20217.png)
                                
                    - Heurística Composta (Maximização)
                        - Se você tem várias heurísticas admissíveis e nenhuma delas domina as outras em todos os estados, você pode criar uma super-heurística escolhendo o valor máximo entre elas a cada passo
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20218.png)
                            
                        - Como todas são admissíveis, o máximo entre elas também será admissível e dominará todas as individuais
                    - Aprendizagem de Máquina para Heurísticas
                        - Quando não é possível definir h(n) analiticamente, podemos usar métodos de aprendizado indutivo
                        - Geração de dados → resolve-se muitos problemas de exemplo (talvez usando busca cega ou reversa) para coletar pares (estado, custo real)
                        - Aprendizado → um algoritmo de aprendizado supervisionado treina com esses dados para aprender uma função ĥ(n) que prevê o custo
                        - Conexão com Redes Neurais → o objetivo do aprendizado supervisionado é aproximar uma função desconhecida a partir de exemplos
                            - Nesse caso, a rede neural seria treinada para aproximar a função de custo real h*(n)
                            - As características do estado (features) seriam as entradas da rede e o custo real seria a saída desejada
    - Busca Adversarial
        - Trata de ambientes com múltiplos agentes competindo entre si (jogos)
            - Agentes Autônomos
                - Um agente deve ser capaz de tomar decisões para alcançar um objetivo em um ambiente
                - Em problemas de busca simples, o agente sabe o efeito exato de suas ações
                    - Se ele planeja ir do estado Si para Sf, ele assume que chegará lá
                - A busca adversarial introduz um elemento crítico de incerteza, o oponente
                    - O agente não tem controle sobre as ações do outro agente
                    - Portanto, o planejamento não é uma sequência fixa de ações, mas uma estratégia que especifica qual ação tomar em resposta a qualquer movimento posível do oponente
            - Jogos
                - São abstrações de situações de conflito
                - A IA clássica foca em um subconjunto específico de jogos para manter a tratabilidade computacional
                - Tipos de Jogos
                    - Two-Player → geralmente chamados de MAX (nós) e MIN (oponentes)
                    - Turn-taking → os jogadores jogam alternadamente
                    - Zero-one → o ganho de um é exatamente a perda do outro
                    - Informação perfeita → o ambiente é totalmente observável
                - A complexidade dos jogos é imensa, no xadrez, por exemplo, o número de estados possíveis pode ser astronômico, tornando impossível a busca exaustiva até o fim do jogo na maioria dos casos
        - Um problema de busca adversarial é formalmente definido com alguns componentes
            - Estado Inicial → configuração inicial do tabuleiro e a indicação de quem joga primeiro
            - Operadores → as jogadas legais disponíveis em um determinado estado
            - Estado Final → condições que determinam o fim do jogo
            - Função de Utilidade (Payoff) → valor numérico atribuído aos estados terminais
            - O objetivo do agente pode ser formalizado como o aprendizado de uma função alvo V: Board → ℜ, que mapeia qualquer estado do tabuleiro para um valor real
                - O objetivo é encontrar uma função V tal que, se o estado b for final e vitorioso, V(b) = 100, se for derrota, V(b) = -100
                - Para estados intermediários, V(b) deve refletir a probabilidade de vitória assumindo um jogo ótimo de ambos os lados
        - Algoritmo Minmax
            - É a base da tomada de decisão em jogos de soma-zero
            - A premissa central é: “Eu jogo para maximizar minha pontuação, assumindo que meu oponente jogará para minimizá-la”
            - Funcionamento
                - O algoritmo realiza uma busca em profundidade na árvore de jogo
                - Gera a árvore de jogo até os estados terminais (ou até um limite de profundidade)
                - Aplica a função de utilidade nas folhas
                - Propaga os valores para cima (backtracking)
                    - Se o nível é de MAX (minha vez), o valor do nó é o máximo dos valores dos filhos
                    - Se o nível é de MIN (vez do oponente), o valor do nó é o mínimo dos valores dos filhos
            - O valor Minmax de um nó é definido recursivamente
                - Minmax-Value(n) = Utility(n) se n é um terminal
                - Minmax-Value(n) = max_sucessores se n é um nó Max
                - Minmax-Value(n) = min_sucessores se n é um nó Min
            - O algoritmo é ótimo (encontra a melhor estratégia, assumindo que o oponente também joga otimamente) e completo (encotra a solução se ela existir)
                - No entanto, sua complexidade é O(b^m), onde b é o fator de ramificação e m a profundidade máxima da árvore
                - Para jogos reais como xadrez, isso é impraticável
            - Otimizações
                - Como a busca completa é impossível em jogos complexos, utilizam-se duas técnicas principais para tornar o problema tratável
                - Alpha-Beta Pruning
                    - Esta técnica melhora a eficiência do Minimax sem alterar o resultado final
                        - A ideia é parar de avaliar um ramo da árvore assim que se prova que ele é pior do que uma opção já examinada anteriormente
                    - Alfa (α): O valor da melhor escolha (o valor mais alto) que o jogador MAX já encontrou ao longo do caminho ou acima dele
                    - Beta (β): O valor da melhor escolha (o valor mais baixo) que o jogador MIN já encontrou
                    - Corte: Se em algum ponto α ≥ β, o jogador atual não precisa considerar mais aquele ramo, pois já existe uma garantia de que aquela linha de jogo não será escolhida (ou pelo próprio jogador ou pelo oponente)
                - Função de Avaliação Heurística
                    - Em vez de buscar até o fim do jogo, a busca é cortada em uma profundidade *d* limitada
                        - Como não temos a utilidade real (vitória/derrota) nesses nós intermediários, usamos uma **Função de Avaliação** (ou Heurística) para estimar a "bondade" do estado
                    - É basicamente uma função V̂(b) que aproxima a função real V(b)
                        - Uma forma comum é a combinação linear de características (features) do tabuleiro
                            
                            ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20219.png)
                            
                        - xi são características e wi são pesos que indicam a importância de cada feature
                    - Aprendizado dos pesos
                        - Os pesos wi podem ser aprendidos automaticamente
                        - Pode se usar o algoritmo LMS (Least Mean Squares) para ajustar esses pesos jogando partidas contra si mesmo e minimizando o erro entre a avaliação estimada e o resultado real do jogo
- Decisões Sequenciais
    - Diferente dos problemas de aprendizado supervisionado ou classificação estática, problemas de decisões sequenciais envolvem um agente que deve tomar uma série de decisões ao longo do tempo para atingir um objetivo
    - O ambiente não é determinístico
        - Quando um agente executa uma ação, o resultado não é garantido
        - Portanto, o agente deve ponderar a utilidade (o quão bom é um estado) e a incerteza (a probabilidade de alcançar esse estado)
    - Enquanto algoritmos de busca clássicos (como A*) procuram um caminho fixo do início ao fim, em ambientes estocásticos (incertos), um plano fixo falha
        - Se o agente tentar ir para o "Norte" mas escorregar para o "Leste", o plano original quebra
        - Por isso, a solução para problemas sequenciais é uma política (uma função universal de reação), não um caminho simples
    - Princípio da Maximização da Utilidade Esperada
        - A busca racional para a tomada de decisão é a Utilidade Esperada (EU - Expected Utility)
        - Seja A uma ação e E a evidência (conhecimento atual) do agente
            - Resulti(A) são os possíveis estados resultantes da ação
            - A utilidade esperada é a soma das utilidades de todos os resultados possíveis, ponderada pela probabilidade de eles ocorrerem
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20220.png)
                
                - O agente racional deve sempre escolher a ação que maximiza essa soma
                - E resume a evidência que o agente possui do mundo
                - Do(A) indica que a ação A foi executada no estado atual
    - Exemplo
        
        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20221.png)
        
    - Recompensas
        - Para avaliar se uma sequência de estados é boa ou não, atribuímos recompensas a cada estado visitado
        - Formas de somar recompensas
            - Recompensas Aditivas
                - A utilidade é a soma simples de todas as recompensas
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20222.png)
                    
                - Se o horizonte for infinito, a soma pode divergir para o infinito, tornando impossível comparar duas sequências infinitas
            - Recompensas Descontadas
                - Aplica-se um fator de desconto γ na qual 0 ≤ γ ≤ 1, na qual se γ é próximo a 0 o agente se importa apenas com recompensas imediatas e se γ é próximo a 1 o agente valoriza recompensas futuras quase tanto quanto as atuais
                - Matematicamente o fator de desconto garante que a série geométrica convirja para um valor finito, mesmo em horizontes infinitos, permitindo a comparação matemática de políticas
    - Política
        - Em ambientes incertos, não buscamos uma sequência de ações, mas sim uma Política (π)
        - Uma política é um mapeamento π(s) que diz ao agente qual é a melhor ação a tomar para qualquer estado s em que ele se encontre
        - Política Ótima (π*)
            - É a política que, se seguida, resulta na maior utilidade esperada acumulada ao longo do tempo
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20223.png)
                
    - Processos de Decisão de Markov (MDP)
        - São a estrutura matemática fundamental utilizada para modelar e resolver problemas de decisão sequencial sob incerteza
        - Componentes
            - Estados (S) → conjunto de estados possíveis
            - Ações (A) → conjunto de ações disponíveis em cada estado
            - Modelo de Transição (T ou P) → T(s, a, s’) é a probabilidade de chegar ao estado s’ dado que a ação a foi executada no estado s
            - Função de Recompensa (R) → R(s) ou R(s, a) é o valor imediato recebido ao entrar no estado
        - Propriedade de Markov
            - A característica central é que o futuro depende apenas do estado atual e não da história de como o agente chegou lá
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20224.png)
                
        - Algoritmo de Value Iteration (Iteração de Valor)
            - Algoritmo central para resolver MDPs quando o modelo de transição T e as recompensas R são conhecidos
                - O objetivo é calcular a Utilidade Real U(s) (ou função de valor) de cada estado
            - A utilidade de um estado não é apenas a sua recompensa imediata, mas a recompensa imediata mais a utilidade descontada do próximo estado para onde você vai, assumindo que você agirá de forma ótima a partir daí
            - Equação de Bellman
                - A relação fundamental que permite resolver o MDP é a Equação de Bellman para utilidades
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20225.png)
                    
                - R(s)**:** Recompensa imediata
                - γ**:** Fator de desconto
                - maxa**:** O agente escolhe a melhor ação possível
                - ∑s′T(...)U(s′)**:** A média ponderada (esperança) da utilidade dos possíveis estados futuros (s′)
            - Algoritmo
                - Como as utilidades dos estados são interdependentes (a utilidade de *A* depende de *B*, e *B* pode depender de *A*), usamos uma abordagem iterativa de programação dinâmica
                - Inicialização
                    - Comece com utilidades arbitrárias (geralmente zero) para todos os estados, ou seja, U0(s) = 0
                - Iteração
                    - Atualize a utilidade de todos os estados simultaneamente com base nas utilidades da iteração anterior, usando a regra de atualização de Bellman
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20226.png)
                        
                - Convergência
                    - Repita até que a mudança nas utilidades entre iterações seja muito pequena (menor que um limiar ϵ)
                    - Este processo converge para os valores ótimos únicos devido à propriedade de contração do fator de desconto
                - Extração da Política
                    - Uma vez que temos os valores finais U(s), a política ótima π*(s) é simplesmente escolher a ação que maximiza o somatório de transição
                        
                        ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20227.png)
                        
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20228.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20229.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20230.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20231.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20232.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20233.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20234.png)
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20235.png)
                
- Aprendizagem por Reforço (Reinforcement Learning - RL)
    - Aborda o problema de como um agente autônomo, agindo em um ambiente, pode aprender a escolher ações ótimas para atingir seus objetivos
        - O problema fundamental do RL é que o agente não conhece o modelo de transição nem a função de recompensa a priori, ele deve aprender interagindo com o ambiente
        - O agente está no estado st, executa uma ação at, o ambiente devolde uma recompensa rt e o novo estado st+1
        - No MDP o agente planeja mentalmente, no RL o agente precisa explorar o mundo real para descobrir quais ações levam a recompensas
    - Q-Learning
        - O Q-Learning é um método "model-free" (livre de modelo), o que significa que o agente pode aprender a política ótima sem nunca aprender as probabilidades de transição T ou as recompensas R explicitamente
        - Função Q
            - Em vez de aprender a utilidade do estado U(s), o agente aprende a utilidade de tomar uma ação específica num estado
            - Definimos Q(s, a) como o valor de realizar a ação a no estado s e, a partir daí, agir otimamente
            - Relação entre utilidade do estado e Q-Function
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20236.png)
                
            - Isso é vantajoso porque, se o agente conhece os valores de Q, ele pode escolher a melhor ação simplesmente olhando qual a maximiza Q(s, a), sem precisar saber as probabilidades de transição para calcular o futuro esperado
        - Q-Table
            - Para ambientes com estados e ações finitos, o conhecimento é armazenado em uma tabela de dimensão N X M (Estados X Ações)
                - Inicialmente, essa tabela pode ser preenchida com valores aleatórios ou zeros
        - Algoritmo de Atualização
            - O agente explora o ambiente e atualiza a Tabela Q iterativamente
            - A regra de atualização baseia-se na diferença temporal (Temporal Difference - TD) entre o que o agente esperava receber e o que ele realmente conseguiu
                
                ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20237.png)
                
                - Erro de Previsão (TD Error) → o termo entre colchetes representa a surpresa do agente, se for positivo, a ação foi melhor do que o esperado, se negativo, foi pior
            - Procedimento
                - Primeira inicializa-se arbitrariamente os valores Q(s, a) para todos os pares estado-ação
                - Dado um estado inicial, xecuta uma trajetória de aprendizagem
                    - Escolhe e executa uma ação at
                    - Registra a recompensa rt recebida
                    - Observa o novo estado st+1
                    - Atualiza o valor de Q(st, at) de acordo com a equação de aprendizagem
                - Repete o processo até a convergência dos valores da Q-Table
        - Políticas de Escolha de Ação
            - O agente enfrenta um dilema entre explorar (tentar ações novas para descobrir recompensas desconhecidas) e explotar (usar o conhecimento atual para maximizar a recompensa imediata)
            - Política ϵ-Greedy (Guloso)
                - É a estratégia mais simples e popular
                - Com probabilidade 1−ϵ escolhe a melhor ação conhecida (Exploitation) → argmaxaQ(s,a)
                - Com probabilidade ϵ escolhe uma ação aleatória (Exploration)
                - O valor de ϵ pode começar alto (muita exploração) e diminuir ao longo do tempo (foco na otimização)
            - Política Softmax (Exploração de Boltzmann)
                - A ϵ-Greedy tem um defeito de que quando explora, ela trata a pior ação e a segunda melhor ação com a mesma probabilidade
                    - A Softmax escolhe ações probabilisticamente com base em seus valores Q de cada ação
                    - Ações melhores têm maior chance de serem escolhidas, mas as piores não são impossíveis
                - Probabilidade de escolher a ação a no estado s
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20238.png)
                    
                    - τ é a temperatura, se τ é alto, a escolha é quase aleatória (exploration), se τ é baixo, o comportamento é mais determinístico (exploitation)
            - Política UCB (Upper Confidence Bound)
                - Esta política favorece explicitamente ações que o agente conhece pouco
                - Ela adiciona um bônus de exploração baseado em quantas vezes a ação foi testada
                    
                    ![image.png](../../assets/faculdade/periodo5/aprendizagem-de-maquina-e-ciencia-de-dados/image%20239.png)
                    
                    - N(s) é o número de visitas ao estado
                    - N(s, a) é o número de vezes que a ação foi tomada
                    - c controla o peso da exploração
                    - Se uma ação foi pouco testada (N(s ,a) baixo), o termo da raiz quadrada aumenta, incentivando o agente a testá-la