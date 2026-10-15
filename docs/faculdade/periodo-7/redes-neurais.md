# REDES NEURAIS

---

Disciplina **Redes Neurais**, do Centro de Informática da UFPE, ministrada pelo **Prof. Germano Crispim Vasconcelos** (gcv@cin.ufpe.br, ramal 2126-8430 r. 4310). Parte do material é datada (©2006) e revisada ao longo dos anos; outra parte é mais recente, incluindo material complementar enviado por e-mail aos alunos. Esta página cobre a ementa completa da disciplina, do **Conteúdo 1 ao 27**: dos fundamentos (Perceptrons, MLP, Backpropagation) até CNNs, RBFs, Autoencoders, GANs, Kohonen, Redes Recorrentes/LSTM/GRU, KANs, Transformers e o projeto final de classificação de dados tabulares (Churn).

!!! note "Dados da disciplina"
    - **Site**: [www.cin.ufpe.br/~gcv/web_lci/intro.html](http://www.cin.ufpe.br/~gcv/web_lci/intro.html)
    - **Avaliação**: 2 mini-projetos (apresentação em sala, sorteio de 3-4 grupos de 4 pessoas, 20 min) + 1 projeto de larga escala em classificação de dados tabulares (4 pessoas, todos apresentam).
    - **Entregas**: sempre PPT/PDF + notebook Jupyter com os experimentos, no Classroom, até o prazo — sem atraso.
    - **Faltas**: abonadas por doença com atestado enviado pelo Classroom. Exame final exige entrega de todo o projeto da fase final.
    - **Bibliografia indicada pelo professor**:
        - NG, Andrew. *Machine Learning Yearning*. Disponível em [info.deeplearning.ai/machine-learning-yearning-book](https://info.deeplearning.ai/machine-learning-yearning-book).
        - NIELSEN, Michael. *Neural Networks and Deep Learning* (2017). Disponível em [neuralnetworksanddeeplearning.com](http://neuralnetworksanddeeplearning.com/).
        - ZHANG, LIPTON, LI, SMOLA. *Dive into Deep Learning*. Disponível em [d2l.ai](https://d2l.ai/).
        - MANASWI, Navin Kumar. *Deep Learning with Applications Using Python*.
        - FLEURET, François. *The Little Book of Deep Learning*.
        - RUSSELL, Stuart; NORVIG, Peter. *Artificial Intelligence: A Modern Approach*, 4ª ed.
        - STARMER, Josh. *The StatQuest Illustrated Guide to Neural Networks and AI* (Jan. 2025).
        - BEALE, R.; JACKSON, T. *Neural Computing: An Introduction* (1990).
        - Canais/autores recomendados em vídeo: Josh Starmer (StatQuest), Luis Serrano (Serrano Academy), Andrej Karpathy, Jay Alammar, Andrew Ng.

### Conteúdo coberto nesta página

| Conteúdo | Tópico | Cobertura |
|---|---|---|
| 1 | Introdução à disciplina e a Redes Neurais | ✅ [Introdução](#introducao-a-redes-neurais) |
| 2 | Conceitos Fundamentais (funções de ativação, topologias, tipos de aprendizagem) | ✅ [Conceitos fundamentais](#conceitos-fundamentais) |
| 3 | Perceptrons e Adaline | ✅ [Perceptrons e Adaline](#perceptrons-e-adaline) |
| 4 | Multilayer Perceptrons (MLP) | ✅ [Multilayer Perceptrons](#multilayer-perceptrons-mlp) |
| 5 | Backpropagation — derivação e exemplo numérico | ✅ [Backpropagation](#backpropagation-regra-delta-generalizada) |
| 6 | Mini-projeto 1 (parte MLP) | ✅ [Mini-projeto 1](#mini-projeto-1-cifar-10-com-mlp-e-cnn) |
| 7 | Redes Convolucionais (CNNs) | ✅ [CNNs](#redes-convolucionais-cnns) |
| 8 | Mini-projeto 1 (parte CNN) | ✅ embutido no [Mini-projeto 1](#mini-projeto-1-cifar-10-com-mlp-e-cnn) |
| 9 | Redes de Funções de Base Radial (RBFs) | ✅ [RBFs](#redes-de-funcoes-de-base-radial-rbfs) |
| 10 | Autoencoders e Variational Autoencoders | ✅ [Autoencoders](#autocodificadores-autoencoders) |
| 11 | Generative Adversarial Networks (GANs) | ✅ [GANs](#generative-adversarial-networks-gans) |
| 12 | Apresentação do Mini-projeto 1 | sem material de aula (data de apresentação) |
| 13 | Redes de Kohonen (SOMs) | ✅ [Kohonen](#redes-de-kohonen-self-organizing-maps) |
| 14 | BPTT, LSTMs e GRUs | ✅ [Recorrentes/LSTM/GRU](#redes-recorrentes-lstms-e-grus) |
| 15 | Mini-projeto 2 (LSTMs) | ✅ [Mini-projeto 2](#mini-projeto-2-previsao-do-preco-do-bitcoin-com-lstm) |
| 16 | Kolmogorov-Arnold Networks (KANs) | ✅ [KANs](#kolmogorov-arnold-networks-kans) |
| 17 | Aprendizagem por Reforço | ⚠️ sem slide próprio — [nota conceitual](#aprendizagem-por-reforco-reinforcement-learning) |
| 18–19 | Transformers (1 e 2) | ✅ [Transformers](#transformers) |
| 20–21 | Large Language Models (LLMs) | ✅ embutido em [Transformers](#transformers-decoder-only-e-llms) |
| 22 | Transformers para dados tabulares (FT-Transformer, STab) | ✅ [Transformers tabulares](#transformers-para-dados-tabulares-ft-transformer-e-stab) |
| 23 | PatchTST (Transformers para séries temporais) | ✅ [PatchTST](#patchtst-transformers-para-series-temporais) |
| 24 | Pré-processamento de dados | ✅ [Pré-processamento](#pre-processamento-de-dados) |
| 25–27 | Projeto final: Classificação de Dados Tabulares (Churn) | ✅ [Projeto Churn](#projeto-final-previsao-de-churn) |

!!! warning "Sobre a numeração dos arquivos de slide"
    Os nomes dos arquivos originais não seguem necessariamente a ordem de apresentação do cronograma de aulas — por exemplo, o arquivo de Perceptrons cobre dois conteúdos (Perceptrons/Adaline **e** MLP), e o material do mini-projeto 1 cobre tanto a parte de MLP quanto a de CNN. Esta página segue a ordem pedagógica do material, agrupando por tema.

## Introdução a Redes Neurais

### Sobre a disciplina

A disciplina é apresentada como tendo uma abordagem conceitos-teoria, com dois mini-projetos de experimentação em problemas de aprendizagem de máquina e um projeto final em uma aplicação de larga escala de classificação de dados.

!!! note "Cronograma oficial (2025.2)"
    | Data | Tópico |
    |---|---|
    | 12/09 | Introdução e Perceptrons |
    | 15/09 | Multilayer Perceptrons e 1º Miniprojeto |
    | 19/09 | Derivação do Backpropagation e Simulador |
    | 22/09 | CNNs e Complemento do 1º Miniprojeto |
    | 26/09 | Autoencoders e Autoencoders Variacionais |
    | 29/09 | Redes de Funções de Base Radial (RBFs) |
    | 03/10 | Redes de Kohonen (SOMs) |
    | 06/10 | Generative Adversarial Networks (GANs) |
    | 10/10 | Apresentação (PPT) do 1º Miniprojeto |
    | 13/10 | BPTT, LSTMs, GRUs e 2º Miniprojeto |
    | 17/10 | Kolmogorov Arnold Networks (KANs) |
    | 20/10, 24/10 | Transformers (1 e 2) |
    | 31/10 | Large Language Models (LLMs) |
    | 03/11 | Apresentação (PPT) do 2º Miniprojeto |
    | 07/11 em diante | Projeto de Classificação de Dados Tabulares (pré/pós-processamento, divisão dos dados, plano de experimentação, Aprendizagem por Reforço, checkpoints, apresentação final) |

### O que são Redes Neurais?

Redes Neurais são apresentadas como uma abordagem alternativa à forma algorítmica de resolver problemas — a partir de **exemplos** do problema, em vez de regras explícitas —, sendo particularmente úteis onde não há como definir regras, como ocorre em boa parte dos problemas do mundo real.

**Definição central**: são **sistemas paralelos distribuídos** compostos por unidades de processamento simples interligadas entre si e com o ambiente por um número de conexões. As conexões estão associadas a **pesos**, que armazenam o conhecimento da rede (relação **Conhecimento → Aprendizagem**). São inspiradas na estrutura paralela do cérebro e buscam reter algumas de suas propriedades: capacidade de aprender por exemplos e se adaptar ao ambiente, e habilidade de lidar com problemas complexos, imprecisos e ruidosos.

O ciclo conceitual de funcionamento tem duas fases: **Aprendizagem** (um Professor/Crítico/mecanismo não-supervisionado fornece Dados de Treinamento → Conhecimento representado nos pesos da rede → Comparador avalia e realimenta o ajuste) e **Uso** (Usuário fornece Dados → passam pelos Pesos já treinados → produzem Dados de saída para o Usuário).

### O neurônio biológico e o neurônio de McCulloch-Pitts

O neurônio biológico tem **dendritos** (recebem o sinal), **corpo/soma** (soma os sinais), **axônio** (transmite o sinal) e **sinapse** (conexão com outro neurônio). O modelo matemático clássico — o **neurônio de McCulloch & Pitts (1943)** — formaliza esse comportamento: entradas $x_0, x_1, ..., x_n$ ponderadas por pesos $w_0, w_1, ..., w_n$, somadas e passadas por uma função de ativação $f_h$ com limiar $\theta$:

$$y = f_h\left[\sum_{i=1}^{n} w_i x_i - \theta\right]$$

O termo $\sum w_i x_i - \theta$ é chamado de **net** (ou $net_{pj}$), e a cadeia de dependência $W \rightarrow net_{pj} \rightarrow O_j \rightarrow E$ (pesos determinam o net, que determina a saída, que determina o erro) é a base da regra da cadeia usada depois no Backpropagation.

### Visão matemática: o neurônio como hiperplano separador

Interpretando o neurônio como classificador linear:

$$f(x) = \sum w_i x_i - \theta = |W||X|\cos\varphi - \theta$$

No ponto de fronteira de decisão ($f(x)=0$), para duas dimensões:

$$w_1 x_1 + w_2 x_2 - \theta = 0 \;\Rightarrow\; x_2 = -\frac{w_1}{w_2}x_1 + \frac{\theta}{w_2}$$

— equivalente à equação de uma reta ($y = mx + c$), com o vetor de pesos $W$ ortogonal à reta/hiperplano separador. Essa visão é ilustrada classicamente com um exemplo de análise de crédito (eixos *Estado Civil* × *Renda*, classes *Compra*/*Não compra*) e generalizada a hiperplanos em espaços de maior dimensão.

!!! example "Como funciona uma rede neural — exemplo de análise de crédito"
    Entradas como *Sexo, Idade, Renda, ...* conectadas através de camadas intermediárias a saídas *Adimplente / Inadimplente*. A solução é baseada na estatística dos dados e tem a capacidade de relacionar grande quantidade de variáveis — sem que um especialista precise escrever regras explícitas.

### Trabalhos fundadores

- **McCulloch & Pitts (1943)** — modelo matemático do neurônio artificial.
- **Donald Hebb (1949)** — regra de aprendizagem (hebbiana).
- **Frank Rosenblatt (1958–1962)** — Perceptron, primeira topologia de rede treinável.

Motivos para a popularidade mais recente da área: novos paradigmas (Deep Learning), análise fundamentada em métodos científicos, avanço tecnológico dos computadores, sucesso em aplicações reais e grandes players do mercado (Google, Facebook, Nvidia, Apple etc.).

### Aplicações (panorama)

O material ilustra um panorama amplo de aplicações históricas e atuais de redes neurais: animação facial e vida artificial, organismos evolutivos (perseguição/fuga), robótica (ASIMO, AIBO, RoboCup Soccer), leitura labial e conversão som→imagem, estimação de trajetórias para vigilância, realidade virtual, jogos (*The Sims*, FIFA), busca de informação na web, previsão financeira, detecção de intrusão/spam, sistemas de controle (freios ABS, foco de câmera, máquina de lavar), recomendação de produtos, análise de mercado e crédito, reconhecimento facial e de impressão digital, processamento de sinais e voz, detecção de fraudes, diagnose médica e interfaces humano-máquina.

## Conceitos fundamentais

Esta seção cobre o material de "Conceitos Fundamentais" (slide deck de 2006, ainda usado como referência), que complementa a introdução com formalizações sobre interdisciplinaridade, funções de ativação, topologias e tipos de aprendizagem.

### Área interdisciplinar

Redes Neurais envolve Neurofisiologia, Psicologia Cognitiva, Matemática, Física, Medicina, Percepção Humana, Engenharias e Ciência da Computação. Características que tornam as redes neurais semelhantes ao cérebro: elementos básicos (neurônios), rede de processadores interconectados, conhecimento armazenado em conexões, conhecimento adquirido por aprendizagem, estrutura inerentemente paralela e representações distribuídas.

### Elementos de um modelo de rede neural

Todo modelo possui: (1) a **função** das unidades de processamento, (2) a **topologia** da rede e (3) a **estratégia/algoritmo** de aprendizagem. A unidade (neurônio artificial) é caracterizada por um conjunto de conexões de entrada, um estado de ativação e um valor de saída; seu comportamento segue três passos — estímulo de entrada, computação do estado de ativação e resposta. A definição da unidade se caracteriza por uma **regra de propagação** (determina o estado de ativação) e uma **função de ativação** (determina a resposta).

### Funções de ativação

| Função | Fórmula |
|---|---|
| Limiar (*threshold*) | $y = 1$ se $v \geq 0$; $y=0$ se $v<0$ |
| Sinal (*sign*) | $y=+1$ se $v\geq0$; $y=-1$ se $v<0$ |
| Rampa | $y=0$ se $v<0$; $y=v$ se $0\leq v<1$; $y=1$ se $v>1$ |
| Linear | $y = v$ |
| Logística (sigmoide) | $y = \dfrac{1}{1+e^{-v}}$ |
| Tangente hiperbólica | $y = \tanh(v)$ |
| ReLU | $f(x) = \max(0,x)$ |
| Gaussiana | $e^{-x^2/2\sigma^2}$ |

### Topologias de redes

- **Feedforward rasa (*shallow*)**: entrada → camada(s) intermediária(s) → saída, totalmente conectadas, sem realimentação.
- **Feedforward profunda (*deep*)**: múltiplos blocos de camadas intermediárias seguidos de classificador — camadas podem aprender características específicas (ex.: "nó de linha diagonal", "nó de rosto", "nó de gato", em uma CNN).
- **Recorrente**: possui conexões de *feedback* (realimentação), com unidades de atraso ($Z^{-1}$); um estado interno $S(t)$ é realimentado via retardo, gerando $S(t+1)$.
- **Construtiva**: cresce dinamicamente, adicionando unidades escondidas conforme necessário (ex.: algoritmo *Cascade Correlation*, usando uma medida de correlação $C = \sum_o |\sum_p (y_{po}-y_o)(e_{po}-e_o)|$ para decidir qual unidade adicionar).

### Tipos de aprendizagem (pelo grau de feedback)

| Tipo | Descrição | Convergência |
|---|---|---|
| **Supervisionada** | Um "professor" informa o quanto a resposta se aproxima da desejada (ex.: nota de prova). Conjunto: $s=\{(x_1,f(x_1)),...\}$ | Rápida |
| **Por reforço** | Um "crítico" informa apenas certo/errado (ex.: punição/recompensa). Conjunto: $s=\{(x_1,\text{sgn}[f(x_1)]),...\}$ | Média |
| **Não-supervisionada** | O sistema se auto-organiza pelas similaridades entre exemplos (ex.: córtex visual estriado). Conjunto: $s=\{(x_1),...\}$, sem rótulo | Lenta |

### Formalização da aprendizagem

- **Learnability vs. Computability**: *computability* é o poder computacional de um sistema em termos do universo de funções que ele consegue computar (ex.: MLP, RBF, pRAM); *learnability* é o poder que os algoritmos de aprendizagem conseguem fazer o sistema efetivamente computar.
- **Caso específico**: aprendizagem é o processo de modificar o estado da máquina $M$ com base nos exemplos, para classificar exemplos não vistos do mesmo problema.
- **Caso geral**: aprendizagem é o processo de escolha de $h \in H$ (espaço de hipóteses) que melhor aproxime $c \in C$ (espaço de conceitos), a partir dos exemplos de treinamento.
- **Algoritmo de aprendizagem**: função $L$ que, a partir da amostra $s$, seleciona $h \in H$ para aproximar $c \in C$. Critérios de avaliação: **consistência** ($h(x_i)=f(x_i)$ para todo exemplo de treino) e **convergência** (melhoria da aproximação com mais exemplos).

### Complexidade das superfícies de decisão

Usando o clássico exemplo de análise de crédito (débito × renda, crédito concedido/recusado), os slides catalogam tipos de superfície de decisão e os modelos associados:

| Superfície | Modelos associados |
|---|---|
| Hiperplano paralelo (regra tipo "se renda < t...") | árvores de decisão, indução de regras |
| Hiperplano oblíquo | Perceptron, regressão linear |
| Superfícies lineares por partes | raciocínio baseado em casos, MLP com saída sigmoide, regressão linear por partes |
| Superfície não linear | MLP, Cascade Correlation, k-vizinhos mais próximos, regressão não-linear |
| Superfícies elípticas | RBF (Radial Basis Functions) |
| Agrupamento (sem rótulo) | Kohonen/vector quantization, ART (Adaptive Resonance Theory) |

## Perceptrons e Adaline

### O Perceptron de Rosenblatt (1958–1962)

O **Perceptron** introduz uma unidade de decisão alimentada por uma camada de unidades sensoriais/associativas. É ilustrado classicamente com um problema de reconhecimento de padrões bidimensional (eixos *Estado Civil* × *Renda*, classes *Compra*/*Não compra*), separáveis por uma reta.

### Regra de aprendizagem do Perceptron

Se um padrão $X$ é **corretamente** classificado, os pesos não mudam. Se é **incorretamente** classificado:

$$
W(t+1) = \begin{cases}
W(t) - \eta X & \text{se } \sum w_i x_i - \theta \geq 0 \text{ e } X \in C_2 \\
W(t) + \eta X & \text{se } \sum w_i x_i - \theta < 0 \text{ e } X \in C_1
\end{cases}
$$

onde $\eta$ é a taxa de aprendizagem. O Perceptron tem **operação simples** e **convergência garantida**, mas resolve **apenas** problemas linearmente separáveis.

### Adaline (Adaptive Linear Neuron) — Bernard Widrow, 1960

Estrutura semelhante ao MCP, com saída passando por uma função degrau ($\pm 1$). Define-se o erro $e_i = (d_i - y_i)$ e a função de custo (**Erro Médio Quadrático**, MSE):

$$C = \frac{1}{2}\sum_p (d_p - y_p)^2$$

Regra de atualização — **Regra de Widrow-Hoff** ou **Regra Delta**:

$$W_i(t+1) = W_i(t) + \eta \, e_i \, X(t)$$

O Adaline compartilha as mesmas três características do Perceptron: operação simples, convergência garantida, e limitação a problemas linearmente separáveis.

### Classificadores lineares combinados

Com duas retas de decisão $d_1$ e $d_2$ dividindo o plano $X_1 \times X_2$ em quatro regiões, é possível combinar sinais para formar regiões de decisão mais complexas do que uma única reta:

| Classificação | $d_1$ | $d_2$ |
|---|---|---|
| Classe 1 | + | + |
| Classe 2 | + | − |
| Classe 2 | − | + |
| Classe 2 | − | − |

### O problema do XOR e a necessidade de multicamadas

!!! danger "A limitação central do Perceptron/Adaline: o XOR"
    Os quatro padrões do problema **OU-exclusivo (XOR)** não podem ser separados por uma única reta — nenhuma das tentativas de reta consegue dividir corretamente as duas classes. Isso demonstra que o XOR **não é linearmente separável**: um único Perceptron ou Adaline não consegue resolvê-lo.

    **A solução**: usar **duas camadas de neurônios** — duas unidades intermediárias, cada uma implementando uma reta de separação diferente, combinadas por uma unidade de saída, produzindo uma fronteira de decisão não linear capaz de resolver o XOR. Essa é a ponte conceitual direta para os **Multilayer Perceptrons**.

## Multilayer Perceptrons (MLP)

### Arquitetura e funcionamento

Um MLP é composto por camada de entrada, uma ou mais camadas intermediárias e camada de saída, todas as camadas adjacentes totalmente conectadas. O treinamento, via **Backpropagation (Regra Delta Generalizada)**, ocorre em duas fases:

- **Fase forward** (passo para frente): a entrada se propaga da camada de entrada em direção à saída — cada camada calcula seus sinais de saída e os propaga à camada seguinte.
- **Fase backward** (passo para trás): o erro calculado na saída se propaga de volta, da saída em direção à entrada, ajustando os pesos.

Formalmente, dado um conjunto de pares $(X_p, Y_p)$, o objetivo é construir um mapeamento $F(W; X_p) \Rightarrow Y_p$.

### Características do MLP

- **Aproximador universal de funções**: uma única camada intermediária é capaz de aproximar qualquer função contínua definida em um hipercubo.
- Alta capacidade de generalização.
- Convergência para mínimo global **não garantida**.
- Em alguns casos, lento na aprendizagem.

### Complexidade funcional × número de camadas

Tabela clássica (Lippmann, *IEEE ASSP*, abril de 1987) relacionando número de camadas com a capacidade de separação de regiões:

| Camadas | Capacidade |
|---|---|
| 1 (Perceptron simples) | Um único hiperplano — só resolve problemas linearmente separáveis (incapaz de resolver XOR) |
| 2 | Regiões convexas (resolve XOR) |
| 3 | Regiões arbitrárias (qualquer forma) |

### Overfitting, viés-variância e regularização

A complexidade funcional de uma rede está diretamente ligada ao **dilema viés-variância** (*bias-variance*): redes muito simples sofrem de alto viés (*underfitting*); redes muito complexas sofrem de alta variância (*overfitting*). O erro total é a soma de $\text{Bias}^2$ + *Variance*, minimizado em um ponto de complexidade ótima.

Uma forma de controlar isso é a **validação cruzada**: o erro de treinamento decresce monotonicamente, mas o erro de validação decresce e depois volta a subir — o ponto de parada ideal corresponde ao mínimo do erro de validação (early stopping).

**Regularização** adiciona um termo de penalização sobre os pesos à função de custo:

$$C = \frac{1}{2n}\sum_x \|y - a^L\|^2 + \frac{\lambda}{2n}\sum_w w^2$$

Quanto maior o fator $\lambda$, mais suave (menos irregular/overfit) fica a fronteira de decisão aprendida — um compromisso entre reduzir o erro e manter pesos pequenos. Outra técnica de regularização é o **Dropout**: durante o treinamento, unidades são aleatoriamente "desligadas", forçando a rede a não depender excessivamente de nenhuma unidade específica.

!!! tip "Demo interativa"
    O material indica a demonstração prática em [playground.tensorflow.org](http://playground.tensorflow.org/).

### Outra função de erro: entropia cruzada

Como alternativa ao erro quadrático médio, usa-se a **entropia cruzada (cross-entropy)**:

$$C = -\frac{1}{n}\sum_x\left[y\ln(a) + (1-y)\ln(1-a)\right]$$

### MLP aplicado à previsão de séries temporais

Dado um conjunto de valores $y(t_1), ..., y(t_n)$, o objetivo é prever $y(t_{n+1})$. Três decisões de projeto são fundamentais: a **janela de entrada**, o **horizonte de previsão** e **outras variáveis explicativas**. Uma arquitetura típica usa uma janela deslizante com atrasos:

$$y(n) = \sum_{i=0}^{10} w_i\, x(n-i)$$

Na previsão **recursiva** (multi-passo), as entradas da rede passam a incluir valores **previstos pela própria rede** (e não mais apenas histórico real), permitindo prever vários passos à frente em sequência — ao custo de divergência progressiva da série real.

### Reconhecimento de padrões: verificação vs. classificação

- **Verificação**: dado $X_p$, verificar se pertence a uma classe específica $C_i$.
- **Classificação**: dado $X_p$, decidir entre múltiplas classes $C_1, ..., C_n$.

Fórmula geral: $Y_k = Y_k(X_p; W)$, $k=1,...,n$. Quando as saídas $Y_k$ são variáveis contínuas, trata-se de um problema de **regressão**/aproximação de funções.

## Backpropagation (Regra Delta Generalizada)

### Derivação matemática completa

O erro na camada de saída, para o padrão $p$:

$$E_p = \frac{1}{2}\sum_{j=1}^{n}(t_{pj}-o_{pj})^2$$

Para minimizar o erro via gradiente descendente: $\Delta_p W_{ji} \propto -\dfrac{\partial E_p}{\partial W_{ji}}$. Expandindo via regra da cadeia (usando $net_{pj} = \sum_k W_{jk}O_{pk}$ e $\delta_{pj} = -\partial E_p/\partial net_{pj}$):

$$\Delta_p W_{ji} = \eta \, \delta_{pj} \, O_{pi}$$

O cálculo de $\delta_{pj}$ depende de dois casos:

**Caso 1 — unidade de saída:**

$$\delta_{pj} = (t_{pj}-o_{pj}) \cdot f'_j(net_{pj})$$

**Caso 2 — unidade intermediária (escondida):**

$$\delta_{pj} = f'_j(net_{pj}) \cdot \sum_k \delta_{pk} \, W_{jk}$$

ou seja, o erro de uma unidade escondida é a soma ponderada (pelos pesos de saída daquela unidade) dos deltas das unidades da camada seguinte — o erro "retropropagado" de todas as unidades a jusante contribui para o $\delta$ da unidade $j$.

Para a função de ativação **sigmoide**, $o_{pj}=f(net_{pj})=\frac{1}{1+e^{-net_{pj}}}$, com a propriedade notável:

$$f'(net_{pj}) = o_{pj}(1-o_{pj})$$

— a derivada é expressa em função da própria saída já calculada, o que torna o cálculo de $\delta$ eficiente.

### Exemplo numérico completo (Matt Mazur)

!!! example "Um passo de Backpropagation calculado à mão"
    Rede com 2 entradas ($i_1=0{,}05$, $i_2=0{,}10$), 1 camada escondida com 2 neurônios ($h_1, h_2$, bias $b_1=0{,}35$), 2 saídas ($o_1, o_2$, bias $b_2=0{,}60$), pesos iniciais $w_1..w_4$ (entrada→escondida) e $w_5..w_8$ (escondida→saída), alvo $(0{,}01;\ 0{,}99)$, taxa de aprendizagem $\eta=0{,}5$.

    **Forward pass**: $net_{h1}=w_1 i_1+w_2 i_2+b_1=0{,}3775 \Rightarrow out_{h1}=0{,}59327$; analogamente $out_{h2}=0{,}59688$. $net_{o1}=w_5\,out_{h1}+w_6\,out_{h2}+b_2=1{,}10591 \Rightarrow out_{o1}=0{,}75137$; $out_{o2}=0{,}77293$.

    **Erro total**: $E_{total}=\tfrac12(0{,}01-0{,}75137)^2+\tfrac12(0{,}99-0{,}77293)^2=0{,}29837$.

    **Backward pass (camada de saída)**: pela regra da cadeia, $\partial E_{total}/\partial w_5 = 0{,}74137 \times 0{,}18682 \times 0{,}59327 = 0{,}08217$, levando aos pesos atualizados $w_6^+=0{,}40867$, $w_7^+=0{,}51130$, $w_8^+=0{,}56137$.

    **Backward pass (camada escondida)**: como cada neurônio escondido afeta *ambas* as saídas, $\partial E_{total}/\partial out_{h1} = \partial E_{o1}/\partial out_{h1} + \partial E_{o2}/\partial out_{h1} = 0{,}03635$. Propagando até $w_1$: $\partial E_{total}/\partial w_1 = 0{,}00044 \Rightarrow w_1^+ = 0{,}14978$ (e analogamente $w_2^+=0{,}19956$, $w_3^+=0{,}24975$, $w_4^+=0{,}29950$).

    Após 10.000 iterações repetindo esse processo, o erro cai para ~0,0000351 e as saídas da rede ficam bem próximas dos alvos.

    *Crédito: Matt Mazur, ["A Step by Step Backpropagation Example"](https://mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example/amp/).*

### Material complementar: por que o ReLU é não linear?

Apesar de ser formada por dois segmentos de reta, o ReLU ($\max(0,x)$) é considerado uma função de ativação **não linear**. A saída de um neurônio com ReLU pode ser vista como $\text{ReLU}(x-h)$ (um ReLU deslocado $h$ unidades). A saída de toda a última camada escondida é uma **soma ponderada de ReLUs diferentemente deslocados**:

$$\hat{y} = \sum_k w_k \cdot \text{ReLU}(x - b_k)$$

Somar progressivamente mais termos ReLU deslocados cria "dobras" (*bends*) adicionais na curva resultante — com poucos termos, a aproximação é grosseira (poucos segmentos lineares visíveis); com muitos termos (demonstrado com uma aproximação de $\sin(x)$ usando 2 a 100 unidades ReLU), a curva aparenta ser inteiramente não linear. Conclusão central do artigo: *"o ReLU NUNCA adiciona não linearidade perfeita a uma rede neural — é a linearidade por partes (piecewise linearity) do ReLU que nos dá a percepção de uma curva não linear"*; a força do ReLU está em "todo um exército de ReLUs embutidos na rede". *(Fonte: Avi Chawla, "An Intuitive Guide to Non-Linearity of ReLU", newsletter* Daily Dose of Data Science*, 5 jun. 2024.)*

## Mini-projeto 1: CIFAR-10 com MLP e CNN

!!! note "Regras gerais do mini-projeto"
    - Grupos de 3–4 pessoas (nunca mais que 4).
    - Entrega: **PPT (em PDF)** + **notebook Jupyter**, por 1 integrante, mas com o nome de todos no início do PPT.
    - 4 grupos sorteados no início da aula apresentam os resultados; todos do grupo precisam participar.
    - **Avaliação pelo PPT** — a apresentação é formativa, não é o critério de nota em si, mas a ausência implica ficar sem nota.
    - Entrega no Classroom até meia-noite da data agendada.
    - Prazo: 2 semanas para a entrega do MLP; 4 semanas no total (MLP + CNN).

### Fase 1 — MLP

A base de dados usada é o **CIFAR-10**, subconjunto rotulado do dataset *80 million tiny images*, criado por **Alex Krizhevsky, Vinod Nair e Geoffrey Hinton**: 60.000 imagens coloridas de 32×32 pixels, em 10 classes (*airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck*), com 6.000 imagens por classe — 50.000 de treino e 10.000 de teste, divididas em 5 *training batches* e 1 *test batch* de 10.000 imagens cada.

O que entregar: PPT + notebook relatando hiperparâmetros investigados (número de camadas, número de neurônios, taxa de aprendizagem, função de ativação, regularização, algoritmo de aprendizagem, drop-out), taxas de acerto por classe e totais (acurácia, precision, recall), buscando ganhos de desempenho.

### Fase 2 — CNN

Repetir o experimento do CIFAR-10 com uma rede **CNN**, como continuidade do trabalho do MLP (material de referência indicado: capítulo 6 de [neuralnetworksanddeeplearning.com](http://neuralnetworksanddeeplearning.com/chap6.html)). Parâmetros a variar: tamanho da rede, tamanho da janela de convolução (filtro), *stride*, *padding*, drop-out, janela de pooling, taxa de aprendizagem. Entrega complementar ao PPT do MLP (continuidade), com apresentação de 15 minutos para os grupos sorteados.

## Redes Convolucionais (CNNs)

### Motivação biológica e ideia central

A inspiração histórica vem de **Hubel & Wiesel (1959)**, sobre o córtex visual. A limitação da rede totalmente conectada motiva as CNNs: um "detector de padrões" (ex.: detector de bico de pássaro) aplicado em diferentes posições da imagem pode ser comprimido para os **mesmos parâmetros** — a ideia central de **compartilhamento de pesos (weight sharing)**.

- **CNN**: rede neural com camadas convolucionais e outras camadas.
- **Camada convolucional**: filtros que fazem a operação de convolução; cada filtro detecta um pequeno padrão local.

### A operação de convolução (exemplo numérico)

Com uma imagem binária 6×6 e filtros 3×3, calcula-se o produto escalar entre o filtro e cada submatriz 3×3 da imagem, deslizando com um determinado *stride*. Com *stride*=1, obtém-se um **mapa de características (feature map)** 4×4; repetindo para $k$ filtros, obtém-se um tensor $k \times 4 \times 4$ (profundidade = número de filtros). Em imagens coloridas (3 canais RGB), cada filtro opera simultaneamente sobre todos os canais de entrada.

### Convolução vs. totalmente conectada

Comparando a mesma imagem 6×6 tratada como (a) convolução com filtro 3×3 ou (b) camada *fully-connected* com 36 entradas: a saída de um neurônio convolucional depende de apenas **9 entradas** (a janela do filtro), não das 36 — **menos parâmetros**. E ao aplicar o mesmo filtro em outra posição, os pesos usados são os mesmos — **pesos compartilhados**. Esses dois pilares — **conectividade local** e **compartilhamento de parâmetros** — são o que distingue a convolução da camada totalmente conectada.

### Max pooling e arquitetura completa

**Max pooling** reduz os *feature maps* subamostrando — "subsampling não muda o objeto" (um pássaro subamostrado continua reconhecível como pássaro), reduzindo parâmetros e custo computacional. A arquitetura completa encadeia **Convolução → Max Pooling → Convolução → Max Pooling → ... → Achatamento (Flattening) → Rede Feedforward Totalmente Conectada** para a classificação final. O número de canais da saída corresponde ao número de filtros aplicados.

CNNs também se aplicam a domínios não-visuais: em **texto/NLP**, calculam-se vetores para n-gramas e agrupam-se depois; em **reconhecimento de fala**, um espectrograma (frequência × tempo) é tratado como "imagem" de entrada, com filtros se movendo na direção da frequência.

### LeNet-5 e a história do Deep Learning

A **LeNet-5** (Yann LeCun) é o marco histórico clássico: INPUT 32×32 → C1 (6@28×28, convolução) → S2 (6@14×14, subsampling) → C3 (16@10×10) → S4 (16@5×5) → C5 (120, *full connection*) → F6 (84) → OUTPUT (10). Com 82 erros em dígitos manuscritos, comparável (mas superior) ao desempenho humano estimado (20–30 erros).

A competição **ILSVRC-2012** (ImageNet, 1,2 milhões de imagens, 1000 classes) foi um ponto de virada: a rede de **Alex Krizhevsky (NIPS 2012)** — a **AlexNet** — obteve 16,4% de erro de classificação (top-5), contra 26–29% dos competidores tradicionais baseados em *features* manuais (SIFT, HoG). AlexNet: 5 camadas convolucionais + 3 totalmente conectadas + soft-max, 650K neurônios, 60 milhões de pesos. O resultado foi manchete do *MIT Technology Review* ("10 Breakthrough Technologies 2013"), levou à contratação de Yann LeCun pelo Facebook (2013) para liderar seu laboratório de IA, e culminou no **Prêmio Turing de 2018/2019** concedido a **Yann LeCun, Geoffrey Hinton e Yoshua Bengio** pelo trabalho fundacional em redes neurais.

### Como se treina uma CNN — backpropagation para convolução

Transformar uma camada totalmente conectada em convolucional ocorre em duas operações: **corte de conexões** (de todos-com-todos para conexões locais) e **compartilhamento de pesos** (os mesmos pesos reutilizados em diferentes posições).

Para uma entrada $X$ (3×3) e filtro $W$ (2×2) produzindo saída $h$ (2×2), o forward é:

$$h_{11} = W_{11}X_{11}+W_{12}X_{12}+W_{21}X_{21}+W_{22}X_{22} \quad (\text{e análogo para } h_{12}, h_{21}, h_{22})$$

O gradiente a ser propagado para a camada anterior é obtido pela **convolução completa entre o filtro rotacionado 180°** ($\text{ROT180}(w)$) e o mapa de gradientes da camada seguinte — a rotação dos pesos resulta diretamente da derivação do erro delta em uma CNN. O algoritmo de backpropagation para CNN resume-se a 5 passos: (1) definir ativação de entrada; (2) *feedforward* calculando $z^l=w^l * \sigma(z^{l-1})+b^l$; (3) calcular o erro de saída $\delta^L$; (4) retropropagar $\delta^l = \delta^{l+1} * \text{ROT180}(w^{l+1})\,\sigma'(z^l)$; (5) obter o gradiente $\partial C/\partial w^l_{a,b} = \delta^l_{a,b} * \sigma(\text{ROT180}(z^{l-1}_{a,b}))$.

### Efeito visual de diferentes filtros

| Tipo de filtro | Efeito |
|---|---|
| Identity | imagem inalterada |
| Edge detection (3 variantes) | realça bordas/contornos |
| Sharpen | realça nitidez |
| Box blur | borra uniformemente |
| Gaussian blur | borra com pesos gaussianos |

ReLU zera valores negativos do *feature map* ("Rectified Feature Map"); max pooling e sum pooling produzem resultados visuais distintos sobre o mesmo mapa.

### Aplicações

CNNs são aplicadas em: reconhecimento facial (landmarks + Transformer para análise detalhada), carros autônomos (detecção de veículos/pedestres/placas), monitoramento de vídeo (CNN + LSTM para reconhecimento de ações), detecção de objetos múltiplos, segmentação semântica de cenas (indoor RGBD), diagnóstico médico por imagem (detecção de anomalias em raios-X, ex.: pneumonia) e análise facial comercial (cosméticos).

!!! tip "Mini-projeto de consolidação"
    O material sugere repetir o experimento clássico do **MNIST com CNNs**, com base no capítulo 6 de Michael Nielsen, *Neural Networks and Deep Learning*: [neuralnetworksanddeeplearning.com/chap6.html](http://neuralnetworksanddeeplearning.com/chap6.html).

## Redes de Funções de Base Radial (RBFs)

### Estrutura

Uma RBF é definida do ponto de vista de um problema de **aproximação de funções**: uma superfície $F$ é uma combinação linear de funções de base radial. Arquitetura em três camadas:

- **Entrada**: apenas propaga os dados $x_1, ..., x_n$.
- **Intermediária**: neurônios que computam funções de base radial $\varphi_j$, cada um associado a um centro $C_j$, calculando $\varphi_j(|X-C_j|)$.
- **Saída**: combina linearmente as saídas intermediárias com pesos $w_j$ + bias $w_0$:

$$F(X) = \sum_j w_j \cdot \varphi_j(|X-C_j|)$$

RBFs são **aproximadores universais de funções**, estimam a probabilidade *a posteriori* (visão bayesiana), mas têm requerimento de memória tipicamente maior que MLPs. A regra de propagação típica é a distância euclidiana ($net_j = |X-C|$) e a função de ativação típica é a gaussiana ($o_j = \exp(-net_j^2/d_j^2)$). Trabalhos de referência: Broomhead & Lowe (1988), Moody & Darken (1989), Poggio & Girosi (1990), Niranjan & Fallside (1990).

### Treinamento

Envolve estimar três conjuntos de parâmetros: as **larguras** $d$, os **centros** $C_j$ e os **pesos** $W_{ji}$ de saída.

- **Larguras**: definidas *a priori*, por gradiente descendente, ou pela heurística dos **K-vizinhos mais próximos**: $\sigma_i = \sqrt{\frac{1}{K}\sum_k \|\vec{c}_k - \vec{c}_i\|^2}$.
- **Centros**: distribuição uniforme/aleatória, amostra do treino, **clustering não-supervisionado** (K-médias) ou gradiente descendente.
- **Pesos de saída**: otimização linear com solução de mínimo global, via esquema de correção de erros (LMS, Newton-like) ou via manipulação direta de matrizes: $W = (G^TG+\lambda G_0)^{-1}G^TY$ (com $\lambda$ o termo de regularização).

Um pipeline prático combina as três técnicas: $x_p \rightarrow$ K-means (gera $c_i$) + KNN (gera $\sigma_i$ usando os $c_i$) $\rightarrow$ cálculo das funções de base (matriz $A$) $\rightarrow$ regressão linear (pesos $w$).

### RBFs construtivas — algoritmo DDA

O algoritmo **DDA (Dynamic Decay Adjustment)**, de Berthold & Diamond (1995, NIPS'7), cria dinamicamente novos protótipos (RBFs) para cada classe conforme novos padrões de treinamento são apresentados, e "encolhe" o raio de ativação de RBFs de outras classes quando necessário para evitar sobreposição incorreta entre classes.

### Aplicações

Reconhecimento de voz, diagnose médica, reconhecimento de caracteres, mineração de dados e textos, reconhecimento de alvos, classificação de fonemas, análise de crédito, previsão e controle.

## Autocodificadores (Autoencoders)

### Aprendizagem não-supervisionada e PCA

O objetivo é aprender a estrutura de dados **X sem rótulos**. O **PCA** (Pearson, 1901) é a abordagem estatística clássica para compressão/visualização, mas limitada a componentes lineares — diferentemente de um autoencoder, que introduz **não-linearidade** (sem funções de ativação, um AE tem capacidade equivalente a PCA).

### Formalização

Dado $x$ (sem rótulos), aprende-se $f$ (**encoder**) e $g$ (**decoder**):

$$f(x) = s(wx+b) = z \qquad g(z) = s(w'z+b') = \hat{x}$$

onde $z$ é a representação latente/código e $h(x)=g(f(x))=\hat{x}$ aproxima a função identidade. A função de perda a minimizar é o **erro de reconstrução**:

$$L(X) = \sum_{x^{(i)}\in X} \ell\big(x^{(i)}, r(h(x^{(i)}))\big)$$

### Subcompleto vs. sobrecompleto

Se a dimensão latente $K < D$ (dimensão de entrada), o AE é **subcompleto** (*undercomplete*) — comprime a entrada, aprendendo boas características para a distribuição de treino, mas potencialmente ruins para outras entradas. Se $K > D$, é **sobrecompleto** (*overcomplete*) — sem compressão, risco de simplesmente aprender a função identidade (cópia), a menos que se imponha alguma restrição.

!!! example "Compressão extrema: 2000 → 30 → 2000"
    Um exemplo clássico ("Reducing the Dimensionality of Data with Neural Networks", *Science*, 2006) usa a arquitetura simétrica 2000→1000→500→30 (*code layer*)→500→1000→2000 aplicada a imagens de rostos, demonstrando compressão efetiva por meio da camada *bottleneck* central de 30 unidades.

### Variantes de autoencoders

- **Convolutional AE**: encoder com camadas convolucionais + max pooling (reduzindo dimensão espacial), decoder com convoluções + upsampling (ex.: 28×28×1 → ... → *hidden code* 4×4×8 → ... → 28×28×1 reconstruído).
- **Denoising AE**: aprende representações **robustas a ruído** — corrompe-se a entrada (zerando componentes com probabilidade $p$, ou com ruído gaussiano aditivo) antes de apresentá-la à rede, e compara-se a reconstrução com a versão **não-ruidosa**. Força a rede a aprender correlações entre *features*, não a confiar em cada *feature* isoladamente. *(Fonte: "Representation Learning - A Review and New Perspectives", 2013.)*
- **Contractive AE**: adiciona à função de perda um termo de penalização pela norma do jacobiano do encoder, para que o encoder não seja sensível a variações fora do manifold de treino mas seja sensível a variações ao longo do manifold. Fórmula: $-\sum_k [x_k\log z_k + (1-x_k)\log(1-z_k)] + \|\partial h(x)/\partial x\|^2$. *(Fonte: "Contractive Auto-Encoders: Explicit Invariance during Feature Extraction", 2011.)*
- **Sparse AE**: força apenas uma pequena quantidade de unidades ocultas a ativar por padrão de entrada (motivação biológica: córtex visual V1).
- **Stacked AE (SAE)**: treina cada camada AE sequencialmente (camada a camada), depois acopla um classificador (MLP/SVM/RBF/SGB) ao final, aproveitando o treino não-supervisionado para um treinamento supervisionado mais "inteligente".

!!! example "Aprendizado de conceitos em escala — Google/YouTube"
    Um experimento com 10 milhões de vídeos do YouTube (1 frame por vídeo, 200×200) treinou um autoencoder esparso localmente conectado de 9 camadas com *pooling*, por 3 dias em um cluster de 1000 máquinas (16.000 núcleos) — a rede aprendeu, de forma não supervisionada, conceitos de **face humana** e **face de gato**. *(Le et al., "Building high-level features using large-scale unsupervised learning", 2012.)*

### Autoencoder Variacional (VAE)

Diferente de um AE simples (que aprende uma codificação pontual $z=e(x)$), o **VAE** aprende uma **distribuição latente** $p(z|x)$: o encoder produz $\mu_x$ e $\sigma_x$, amostra-se $z \sim \mathcal{N}(\mu_x,\sigma_x)$, e o decoder reconstrói $\hat{x}=d(z)$. A função de perda combina erro de reconstrução com divergência KL contra uma normal padrão:

$$\text{loss} = \|x-\hat{x}\|^2 + KL\big[\mathcal{N}(\mu_x,\sigma_x),\ \mathcal{N}(0,I)\big]$$

O **reparametrization trick** permite backpropagation através da amostragem estocástica: $z = \sigma_x \cdot \zeta + \mu_x$, com $\zeta \sim \mathcal{N}(0,I)$. A regularização (via KL) é o que faz o espaço latente formar regiões contínuas e bem distribuídas (sem "buracos" sem sentido entre classes) — condição necessária para que o VAE seja usado como modelo *generativo*.

## Generative Adversarial Networks (GANs)

### Arquitetura e treinamento adversarial

Uma GAN tem dois componentes diferenciáveis: o **Generator (G)**, que recebe ruído latente $z$ (gaussiano/uniforme) e produz $G(z)$; e o **Discriminator (D)**, que recebe tanto amostras reais $x$ quanto geradas $G(z)$ e tenta distinguir *Real* de *Fake*.

O treinamento alterna entre duas fases: **treinar o Discriminador** (pesos do Generator congelados; backprop só atualiza D) e **treinar o Generator** (pesos do Discriminator congelados; backprop flui da *loss*, através de D, até G, atualizando só G).

### Formulação matemática — jogo min-max

$$\min_G \max_D V(D,G) = \mathbb{E}_{x\sim p(x)}[\log D(x)] + \mathbb{E}_{z\sim q(z)}[\log(1-D(G(z)))]$$

O discriminador tenta **maximizar** sua recompensa (reduzir seu erro); o gerador tenta **minimizar** a recompensa do discriminador (maximizar a perda do discriminador). Algoritmo de treinamento (Goodfellow et al.): a cada iteração, atualiza-se D por $k$ passos (gradiente ascendente sobre $\frac{1}{m}\sum[\log D(x^{(i)}) + \log(1-D(G(z^{(i)})))]$), depois atualiza-se G uma vez (gradiente descendente sobre $\frac{1}{m}\sum\log(1-D(G(z^{(i)})))$).

### Log Loss / entropia cruzada binária

A base da formulação é a **Log Loss**:

$$\text{log loss} = -\frac{1}{N}\sum_{i=1}^N \log(P_i) \qquad \text{BCE} = -\frac{1}{N}\sum_i\big[y_i\log(p(y_i)) + (1-y_i)\log(1-p(y_i))\big]$$

Como bibliotecas de otimização só fazem gradiente *descendente*, na prática o código usa o sinal negativo (minimizando $-\log D(x) - \log(1-D(G(z)))$ para o discriminador, matematicamente equivalente a maximizar via gradiente ascendente). Para o gerador, o **non-saturating loss trick** inverte os alvos (fingindo que o dado falso é real), passando a minimizar $-\log D(G(z))$ — o que fornece gradientes mais fortes no início do treinamento.

### DCGAN e aritmética no espaço latente

A **DCGAN** (Radford, Metz & Chintala, 2015) substitui camadas totalmente conectadas por convoluções (convoluções transpostas/*fractionally-strided* no Generator), usa Batch Normalization após cada camada, ReLU nas camadas ocultas do gerador e Tanh na saída. Um resultado célebre demonstra **aritmética vetorial no espaço latente**:

$$\text{"man with glasses"} - \text{"man without glasses"} + \text{"woman without glasses"} = \text{"woman with glasses"}$$

— evidenciando que direções no espaço latente correspondem a atributos semânticos consistentes.

!!! tip "Material complementar"
    Vídeo recomendado: Luis Serrano (Serrano.Academy), ["A Friendly Introduction to GANs"](https://www.youtube.com/watch?v=8L11aMN5KY8).

## Redes de Kohonen (Self-Organizing Maps)

### Fundamentos

As **Redes de Kohonen (SOM)**, desenvolvidas por **Kohonen em 1982**, baseiam-se em **aprendizagem não-supervisionada** e **aprendizagem competitiva**, com forte inspiração neurofisiológica (mapas topográficos no córtex visual, tátil e auditivo; processo *Winner Takes All*).

Características gerais: inspiração biológica, aprendizagem não-supervisionada por *clustering* (a rede identifica características comuns no domínio dos padrões de entrada), memória associativa, e **mapa topográfico de características** — quantização vetorial, relações de vizinhança preservadas, representação de espaços N-dimensionais em 2D.

### Arquitetura e aprendizagem competitiva

Camada de saída plana (grade 2D), com camadas de entrada e saída totalmente conectadas, mas *feedback* na saída apenas numa vizinhança de cada neurônio (excitação/inibição lateral — a função clássica "chapéu mexicano", onde o **óxido nítrico** liberado pelas células ativas é uma das substâncias responsáveis por esse papel). Neurônios competem; apenas um fica ativo por vez (o "vencedor"), que se especializa em agrupamentos de padrões similares.

Formalização: espaço de entrada de dimensão $d$, vetor de entrada $x=[x_1,...,x_d]$; camada de Kohonen com $N$ neurônios $A=\{c_1,...,c_N\}$, cada um com vetor peso $w_j=[\omega_{j1},...,\omega_{jd}]$ representando sua posição no espaço de entrada. Grades podem ser **hexagonais** (6 vizinhos diretos) ou **retangulares** (4 vizinhos diretos).

### Algoritmo de aprendizagem

1. Inicializa pesos (aleatórios em $[0,1]$), raio de vizinhança, taxa de aprendizagem e taxa de redução.
2. Apresenta padrão de entrada.
3. Calcula distância euclidiana do vetor de entrada a cada neurônio de saída.
4. Seleciona o neurônio $n_{j^*}$ de menor distância.
5. Adapta pesos do vencedor e sua vizinhança: $w_{ij}(t+1)=w_{ij}(t)+\eta(t)[x_i(t)-w_{ij}(t)]\cdot\Lambda_{i,i^*}$.
6. Repete enquanto existirem padrões.
7. Reduz vizinhança e taxa de aprendizagem (convergência).
8. Repete até o total de iterações.

A função de vizinhança $\Lambda$ é tipicamente gaussiana: $\Lambda_{i,i^*}(n)=\exp(-d_{i,i^*}^2/2\sigma^2(n))$, com variância que decresce ao longo do treinamento (de cobrir todo o mapa a apenas o vencedor). O treinamento tem **duas fases**: **ordenação topológica** dos pesos (taxa de aprendizagem alta, > 0,1) e **convergência** (ajuste fino, taxa baixa, ≈ 0,01, vizinhança mínima).

### Aplicações

Reconstrução de superfícies 3D a partir de nuvens de pontos, segmentação de imagens, reconhecimento de fala (máquina de escrever fonética de Kohonen, com "mapa fonotópico"), reconhecimento de caracteres manuscritos, organização de países por indicadores de pobreza, mineração de textos (agrupamento de artigos por similaridade semântica), identificação de perfis de jogadores (World of Warcraft, Lopes & Mustaro, 2009) e — em um estudo de caso brasileiro — **identificação de padrões de comportamento em dados de internação do SUS** (Pernambuco, 2008–2014, ~41 mil registros/mês, mapa SOM 15×15 segmentado em 15 clusters via índice de Davies-Bouldin), revelando discrepâncias em taxas de mortalidade, cesáreas e valores de gastos por cluster — discrepâncias que sinalizam pontos para investigação, não necessariamente irregularidades.

## Redes Recorrentes, LSTMs e GRUs

### Por que redes recorrentes?

Redes **feedforward** não têm noção de tempo ou memória de estados anteriores — a informação flui apenas para frente. Redes **recorrentes** têm nós que se conectam de volta a outros nós e a si mesmos, criando memórias de curto prazo. Três categorias clássicas de tarefas temporais: **reconhecimento de sequências** (ex.: voz), **reprodução de sequências** (ex.: previsão de séries temporais) e **associação temporal** (ex.: geração de fala/texto).

Os cinco padrões arquiteturais clássicos: *one-to-one* (redes vanilla), *one-to-many* (legendagem de imagens), *many-to-one* (classificação de sentimento), *many-to-many* sincronizado (tradução automática) e *many-to-many* com saída a cada passo (classificação de vídeo por frame).

### Redes de Elman e de Jordan

A **Rede de Elman** (1990, 1993, 1999) é uma Rede Recorrente Simples (SRN) com **unidades de contexto**, que no tempo $t$ guardam uma cópia das ativações das unidades escondidas em $t-1$:

$$h_k(t) = f\left(w_k^x x(t) + \sum_j w_{kj}^c h_j(t-1)\right), \quad y = \sum_k w_k^2 h_k(t)$$

A **Rede de Jordan** é semelhante, mas as unidades de contexto guardam memória das **unidades de saída** (não das escondidas) — Elman e Jordan podem produzir desempenhos diferentes dependendo da aplicação.

### Backpropagation Through Time (BPTT)

A generalização da ideia de Elman: copiar ativações de entrada e escondidas por vários passos no tempo (quanto mais "camadas de contexto"/*copy layers*, mais história é incluída explicitamente no gradiente). A rede recorrente é "desenrolada" (*unfolded*) no tempo em uma cadeia de cópias com **pesos idênticos** entre níveis, e tratada como uma "grande" rede feedforward para o cálculo do gradiente — que é acumulado (somado ou tirado a média) entre as cópias.

$$E_{total}(t_0,t_n) = \frac{1}{2}\sum_{t=t_0}^{t_n}\sum_{j\in A} e_j^2(t)$$

**Principal desvantagem do BPTT**: alto custo de armazenamento (história inteira), processamento (gradiente para todas as camadas) e dados (muitos exemplos necessários).

### O problema do gradiente que desaparece

!!! warning "Vanishing gradient problem"
    Na teoria, uma RNN clássica deveria conseguir aprender dependências temporais arbitrariamente longas. **Na prática**, o gradiente tende a desaparecer (*vanishing gradient*) ao ser propagado por muitos passos no tempo, tornando difícil que uma unidade distante no tempo aprenda a partir de entradas muito anteriores.

### LSTM (Long Short-Term Memory)

A LSTM resolve esse problema com uma **célula de memória (cell state)** $C_t$ que atravessa a cadeia temporal quase sem modificação direta, sofrendo apenas interações lineares pontuais controladas por três *gates* — uma "esteira transportadora" onde a informação é esquecida, alterada ou mantida por filtros:

- **Forget gate**: $f_t = \sigma(W_f\cdot[h_{t-1},x_t]+b_f)$ — decide o que esquecer do estado anterior.
- **Input gate** + candidato: $i_t = \sigma(W_i\cdot[h_{t-1},x_t]+b_i)$, $\tilde{C}_t = \tanh(W_C\cdot[h_{t-1},x_t]+b_C)$ — decide o que incorporar.
- **Atualização do cell state**: $C_t = f_t * C_{t-1} + i_t * \tilde{C}_t$.
- **Output gate**: $o_t = \sigma(W_o[h_{t-1},x_t]+b_o)$, $h_t = o_t * \tanh(C_t)$ — decide o que expor como saída.

!!! example "Intuição dos gates"
    *Forget gate*: "Bob is a nice person. Dan on the other hand is evil." — ao encontrar um novo sujeito, a rede precisa esquecer o gênero/identidade do sujeito anterior.

    *Input gate*: "Bob knows swimming. He told me over the phone that he had served the navy for 4 long years." — a rede decide incorporar a nova informação relevante.

    *Output gate*: "Bob fought single handedly with the enemy and died for his country. For his contributions brave ______." — a rede expõe, na saída, a informação de contexto retida necessária para prever a próxima palavra.

### GRU (Gated Recurrent Unit)

Uma simplificação da LSTM, com apenas dois *gates* (*reset* e *update*), fundindo o estado oculto e o *cell state* em um único vetor:

$$\tilde{c}^{\langle t\rangle} = \tanh(W_c[\Gamma_r * c^{\langle t-1\rangle}, x^{\langle t\rangle}]+b_c) \qquad \Gamma_u = \sigma(W_u[c^{\langle t-1\rangle},x^{\langle t\rangle}]+b_u)$$
$$\Gamma_r = \sigma(W_r[c^{\langle t-1\rangle},x^{\langle t\rangle}]+b_r) \qquad c^{\langle t\rangle} = \Gamma_u * \tilde{c}^{\langle t\rangle} + (1-\Gamma_u) * c^{\langle t-1\rangle}$$

!!! example "Dependências de longo alcance com a GRU"
    "The cat, which already ate ..., was full." — o *update gate* $\Gamma_u$ pode permanecer memorizando a informação de concordância verbal (sujeito singular "cat") ao longo de toda a frase, mesmo quando $\Gamma_u \approx 0$ (quase constante), demonstrando como o gate de atualização resolve o problema do gradiente que desaparece em dependências longas. *(Cho et al., 2014; Chung et al., 2014; material no estilo do curso de Deep Learning Specialization de Andrew Ng.)*

### Codificação de dados textuais

Para alimentar RNNs/LSTMs/GRUs com texto, a opção mais simples é o **one-hot encoding**: cada palavra única do vocabulário recebe um vetor binário com um único 1 na posição correspondente.

## Mini-projeto 2: previsão do preço do Bitcoin com LSTM

!!! note "O que consta no material"
    O slide desse mini-projeto é enxuto (6 páginas) e **não especifica** prazos de entrega, formato de entrega, composição de grupos, arquitetura detalhada da rede, hiperparâmetros a variar ou critérios de avaliação — apenas o objetivo, a regra de divisão dos dados e os links de referência, reproduzidos fielmente abaixo.

**Objetivo**: empregar uma LSTM para prever o preço do Bitcoin no período de dezembro de 2014 a maio de 2018, usando os primeiros 80% dos registros para treino e os 20% finais para teste (dados plotados ao longo de ~1.280 dias, com o corte de treino/teste por volta do dia 1000).

O material de referência indicado é o projeto de **Brian Mwangi**, repositório GitHub `predicting-bitcoin-prices-using-LSTM` (arquivo de dados `btc.csv`, notebook `btc.ipynb` em Google Colab), e o guia [*"A Beginner's Guide to Implementing Long Short-Term Memory Networks (LSTM)"*](https://heartbeat.fritz.ai/a-beginners-guide-to-implementing-long-short-term-memory-networks-lstm-eb7a2ff09a27). As bibliotecas sugeridas no trecho de código do slide são `tensorflow` (implementação da LSTM), `numpy` (álgebra matricial), `pandas` (estruturas de dados), `matplotlib` (visualização) e `scikit-learn` — `StandardScaler` (normalização dos dados).

!!! tip "Fora do escopo do mini-projeto"
    O slide também aponta, como aplicação adicional **não obrigatória**, a geração de textos com LSTMs (tarefa de previsão de sequências), com o link [*"Fundamentals of Deep Learning – Introduction to LSTM"*](https://www.analyticsvidhya.com/blog/2017/12/fundamentals-of-deep-learning-introduction-to-lstm/).

## Kolmogorov-Arnold Networks (KANs)

### MLP vs. KAN: a mudança de paradigma

O **Teorema da Representação de Kolmogorov-Arnold** é a base teórica alternativa ao Teorema da Aproximação Universal (base dos MLPs):

| | MLP | KAN |
|---|---|---|
| Teorema | Teorema da Aproximação Universal | Teorema da Representação de Kolmogorov-Arnold |
| Fórmula (rasa) | $f(x) \approx \sum_{i=1}^{N} a_i \sigma(w_i \cdot x + b_i)$ | $f(x) = \sum_{q=1}^{2n+1} \Phi_q\left(\sum_{p=1}^{n}\varphi_{q,p}(x_p)\right)$ |
| Onde fica o "aprendível" | Funções de ativação **fixas** nos nós; **pesos aprendíveis** nas arestas | Funções de ativação **aprendíveis** nas arestas; operação de **soma** nos nós |
| Fórmula (profunda) | $\text{MLP}(x) = (W_3 \circ \sigma_2 \circ W_2 \circ \sigma_1 \circ W_1)(x)$ | $\text{KAN}(x) = (\Phi_3 \circ \Phi_2 \circ \Phi_1)(x)$ |

Ou seja: uma KAN **inverte** a lógica do MLP — em vez de pesos escalares fixos combinados com uma não-linearidade fixa, cada "aresta" da rede é, ela mesma, uma função 1D aprendível (tipicamente parametrizada como uma *B-spline*), e os nós apenas somam as saídas dessas funções.

### Camada KAN e empilhamento

Uma camada KAN com $n_{in}$ entradas e $n_{out}$ saídas é definida como uma matriz de funções 1D $\Phi = \{\varphi_{q,p}\}$, $p=1,...,n_{in}$, $q=1,...,n_{out}$, cada $\varphi_{q,p}$ com parâmetros treináveis. No teorema de Kolmogorov-Arnold, as funções internas formam uma camada KAN com $n_{in}=n$, $n_{out}=2n+1$, e as funções externas formam uma segunda camada com $n_{in}=2n+1$, $n_{out}=1$ — a representação completa é a composição de duas camadas KAN. **Empilhar mais camadas KAN** é o que permite redes KAN profundas, exatamente como MLPs profundos empilham camadas lineares + não-linearidade.

Para obter a saída de uma camada, o vetor de entrada passa pela matriz de funções:

$$z^1 = \Phi^1 \cdot X, \qquad \Phi^1 = \begin{bmatrix}\varphi_{11}(\cdot) & \varphi_{12}(\cdot) & \cdots \\ \varphi_{21}(\cdot) & \varphi_{22}(\cdot) & \cdots \\ \vdots & & \ddots\end{bmatrix}$$

!!! example "Interpretabilidade: regressão simbólica com KAN"
    Um exemplo do material mostra uma KAN aprendendo a função $e^{\sin(\pi x) + y^2}$ a partir de dados, em 6 passos: (1) treino com esparsificação; (2) *pruning* da rede; (3) identificação simbólica de cada ramo (seno, quadrado, exponencial); (4) ajuste fino dos parâmetros afins; (5) fórmula simbólica obtida por precisão numérica: $1{,}0\,e^{1{,}0y^2+1{,}0\sin(3{,}14x)}$; (6) simplificação/arredondamento final: $e^{y^2+\sin(\pi x)}$ — demonstrando como uma KAN treinada pode ser lida de volta como uma expressão matemática interpretável, algo não trivial em um MLP.

### Variantes de KANs

| Variante | Ideia |
|---|---|
| **Conv-KANs** | Integra ativações spline aprendíveis em camadas convolucionais, com eficiência de parâmetros melhorada em visão computacional. |
| **T-KANs / MT-KANs** | Para séries temporais; incorporam mecanismos recorrentes e de *gating* para dependências temporais longas, superando RNNs tradicionais em alguns casos. |
| **GKANs / KA-GNNs** | Para dados em grafo; substituem operações fixas de GCNs por funções univariadas aprendíveis. |
| **Wav-KANs** | Usam funções *wavelet* como base, capturando padrões de baixa e alta frequência (ex.: monitoramento ambiental, imagens hiperespectrais). |
| **QKANs / VQKANs** | Integração com computação quântica (circuitos quânticos parametrizados). |
| **MonoKAN** | *Splines* de Hermite cúbicas com restrição de monotonicidade — mais explicável, útil em diagnóstico médico. |
| **CoxKAN** | Combina KAN com o Modelo de Riscos Proporcionais de Cox para análise de sobrevivência interpretável. |
| **KAN-XGBoost / U-KAN** | Modelos híbridos — detecção de intrusão e segmentação de imagens médicas (U-Net + KAN), respectivamente. |

!!! tip "Papers e vídeos citados no material"
    - GAO et al. "TabKANet: Tabular Data Modeling with Kolmogorov-Arnold Network and Transformer" (2024), Tsinghua University.
    - YANG, X.; WANG, X. "Kolmogorov–Arnold Transformer" (2024), National University of Singapore.
    - JI, T.; HOU, Y.; ZHANG, D. "A Comprehensive Survey on Kolmogorov Arnold Networks (KAN)" (jan. 2025), Xi'an Jiaotong-Liverpool University.
    - Vídeos: ["Kolmogorov Arnold Networks (KAN) Paper Explained"](https://www.youtube.com/watch?v=7zpz_AlFW2w); Luis Serrano, [explicação do paper](https://www.youtube.com/watch?v=myFtp5zMv8U) e [matemática do teorema](https://www.youtube.com/watch?v=nS2hnm0JRBk).

## Aprendizagem por Reforço (Reinforcement Learning)

!!! warning "Nota sobre esta seção"
    A disciplina **não enviou slide próprio** sobre Aprendizagem por Reforço (RL) para este conteúdo. Diferentemente do restante desta página — que reproduz fielmente apenas o que está nos slides da disciplina —, o resumo abaixo é uma síntese conceitual de conhecimento geral sobre o tema, incluída a pedido do usuário ("sobre reinforcement learning, não tem slide próprio, faça como achar melhor"). Trate-a como contexto introdutório, não como conteúdo oficial da disciplina.

**Aprendizagem por Reforço** é o terceiro grande paradigma de aprendizagem de máquina (ao lado do supervisionado e do não-supervisionado), em que um **agente** aprende a tomar decisões ao interagir com um **ambiente**, recebendo **recompensas** (ou punições) em resposta às suas **ações**, com o objetivo de maximizar a recompensa acumulada ao longo do tempo — e não a partir de exemplos rotulados fornecidos de antemão.

Conceitos centrais:

- **Estado ($s$)**: a situação atual do ambiente, do ponto de vista do agente.
- **Ação ($a$)**: o que o agente pode fazer em cada estado.
- **Política ($\pi$)**: a estratégia do agente — um mapeamento de estados para ações (determinística ou probabilística).
- **Recompensa ($r$)**: o sinal de feedback numérico recebido após uma ação.
- **Função de valor ($V$) e função Q ($Q$)**: estimam o retorno esperado a partir de um estado (ou de um par estado-ação), usadas para avaliar quão boa é uma política.
- **Trade-off exploração vs. explotação**: o agente precisa balancear tentar ações novas (exploração) com repetir ações já conhecidas como boas (explotação).

Algoritmos clássicos incluem **Q-Learning** e **SARSA** (baseados em tabelas de valor), e, na era do Deep Learning, o **Deep Q-Network (DQN)** — que usa uma rede neural para aproximar a função $Q(s,a)$ em espaços de estado muito grandes (ex.: pixels de um jogo de Atari) — além de métodos de **gradiente de política** (*policy gradient*, ex.: REINFORCE, PPO) e métodos **ator-crítico** (*actor-critic*), que combinam uma rede que aprende a política com outra que aprende a função de valor. RL teve destaque público com sistemas como o AlphaGo/AlphaZero (DeepMind) e é também a técnica usada no **RLHF** (*Reinforcement Learning from Human Feedback*), etapa de alinhamento usada no treinamento de LLMs como o ChatGPT.

## Transformers

### Arquitetura geral

O slide da disciplina reproduz o diagrama clássico encoder-decoder do Transformer, com créditos ao vídeo *"Illustrated Guide to Transformers Neural Network"* (canal The AI Hacker):

- **Encoder**: `Inputs → Input Embedding (+ codificação posicional)` → bloco repetido de `Multi-Headed Attention → Add & Norm → Feed Forward → Add & Norm`.
- **Decoder**: `Outputs (shifted right) → Output Embedding (+ codificação posicional)` → bloco repetido de `Multi-Headed Attention (mascarada) → Add & Norm → Multi-Headed Attention (atenção encoder-decoder) → Add & Norm → Feed Forward → Add & Norm` → `Linear → Softmax → Output Probabilities`.

O slide descreve textualmente o funcionamento: *"the encoder output is a continuous vector representation of the inputs"*; e o decoder opera de forma autoregressiva, realimentando suas próprias saídas até gerar um token especial de fim de sentença (`<end>`): *"Feed previous outputs into the decoder recurrently until an 'end of sentence' token is generated."* Um diagrama de arcos sobre uma frase de exemplo ("As aliens entered our planet and began to colonize earth a certain group of extraterrestrials...") ilustra como o self-attention conecta palavras semanticamente relacionadas mesmo quando distantes na sequência — diferente de uma RNN, que processa a sequência estritamente em ordem.

!!! note "Sobre a fonte deste material"
    O slide da disciplina não traz fórmulas matemáticas escritas — ele é essencialmente um roteiro visual que **delega a explicação matemática detalhada** a uma lista de vídeos externos (créditos explícitos no próprio slide). A formalização abaixo (scaled dot-product attention e multi-head attention) foi complementada a partir de um desses recursos linkados pelo slide — o vídeo ["The math behind Attention: Keys, Queries, and Values matrices"](https://www.youtube.com/watch?v=UPtG_38Oq8o), de Luis Serrano — e está equivalente à formulação do paper "Attention Is All You Need" (Vaswani et al., 2017), que não é citado diretamente nos slides.

### Self-attention: a formalização matemática

Cada palavra de entrada é representada por um vetor de embedding; empilhando esses vetores forma-se a matriz $X$ (nº de palavras × dimensão do embedding). Três matrizes de pesos **aprendidas no treinamento** — $W_Q$, $W_K$, $W_V$ — projetam $X$ em três papéis:

$$Q = X W_Q \qquad K = X W_K \qquad V = X W_V$$

A atenção é calculada por:

$$\text{Attention}(Q,K,V) = \text{softmax}\left(\frac{QK^\top}{\sqrt{d_k}}\right)V$$

- **Scores** ($QK^\top$): a entrada $(i,j)$ mede o quanto a *query* da palavra $i$ combina com a *key* da palavra $j$.
- **Escala** ($\sqrt{d_k}$): evita que o softmax produza valores extremos (saturação), suavizando a distribuição sem mudar qual palavra recebe maior peso.
- **Softmax**: normaliza cada linha para pesos positivos que somam 1.
- **Saída**: combinação ponderada dos vetores *Value* de todas as palavras da sequência.

!!! example "Exemplo numérico (Luis Serrano)"
    Para a palavra "I" em uma frase curta, com $d_k=3$, os *scores* brutos eram aproximadamente $[1, 5, 3]$. Divididos por $\sqrt{3}\approx 1{,}732$: $[0{,}577;\ 2{,}887;\ 1{,}732]$. Após softmax: pesos de atenção $\approx [0{,}070;\ 0{,}707;\ 0{,}223]$ — a palavra "I" atende principalmente a "love" (peso ≈ 0,707), resultando no vetor de saída $\approx [1{,}000;\ 1{,}637;\ 0{,}070]$.

**Multi-head attention**: o mesmo cálculo de $Q,K,V$ é executado em paralelo por várias "cabeças", cada uma com seus próprios pesos aprendidos, permitindo capturar diferentes tipos de relação entre palavras simultaneamente; os resultados são concatenados e passam por uma transformação linear final.

### Transformers decoder-only e LLMs

O material da disciplina não traz slide próprio detalhando LLMs — em vez disso, aponta uma lista de vídeos complementares sobre o tema (ver abaixo). Em linhas gerais (conhecimento complementar, na mesma linha dos recursos linkados pelo slide): os **LLMs modernos baseados em GPT** usam apenas a parte **decoder** do Transformer original (arquitetura *decoder-only*, com atenção mascarada/causal — cada token só pode atender a tokens anteriores, nunca ao futuro), treinados primeiro por **pré-treinamento auto-supervisionado** (prever o próximo token em grandes corpora de texto) e depois ajustados por **fine-tuning** supervisionado e por **RLHF** (*Reinforcement Learning from Human Feedback* — ver seção de Aprendizagem por Reforço acima) para seguir instruções de forma alinhada e segura.

!!! tip "Vídeos indicados pelo slide da disciplina"
    **Passo a passo**: ["Illustrated Guide to Transformers Neural Network"](https://www.youtube.com/watch?v=4Bdc55j80l8) (The AI Hacker) · ["Word Embedding e Word2Vec, claramente explicados"](https://www.youtube.com/watch?v=viZrOnJclY0) (Josh Starmer) · ["All The Math You Need For Attention In 15 Minutes"](https://www.youtube.com/watch?v=wU9CZIFkO6U) · ["Rede neural transformer, a fundação do ChatGPT, explicada"](https://www.youtube.com/watch?v=zxQyTK8quyY) (Josh Starmer) · ["Deep Dive into LLMs like ChatGPT"](https://www.youtube.com/watch?v=7xTGNNLPyMI) (Andrej Karpathy).

    **Complementares**: ["Let's build GPT: from scratch, in code, spelled out"](https://www.youtube.com/watch?v=kCc8FmEb1nY) (Karpathy) · ["A matemática matricial por trás dos transformers"](https://www.youtube.com/watch?v=KphmOJnLAdI) (Josh Starmer) · ["The Attention Mechanism in Large Language Models"](https://www.youtube.com/watch?v=OxCpWwDCDFQ) (Luis Serrano) · ["The math behind Attention: Keys, Queries, and Values matrices"](https://www.youtube.com/watch?v=UPtG_38Oq8o) (Luis Serrano) · ["What are Transformer Models and how do they work?"](https://www.youtube.com/watch?v=qaWMOYf4ri8) (Luis Serrano).

## Transformers para dados tabulares: FT-Transformer e STab

A disciplina também estuda arquiteturas Transformer adaptadas a **dados tabulares** (como o problema de churn do projeto final), comparando dois modelos em um estudo de caso de um cliente de telecom (Cliente C0001).

### Semelhanças entre os dois modelos

Ambos tokenizam cada **coluna/atributo** da tabela separadamente (não concatenam a linha inteira em um único vetor de entrada), aplicam **self-attention multi-cabeça** entre as colunas (permitindo, por exemplo, que o modelo aprenda como `tipo_contrato` amplifica ou atenua o peso de `atrasos_6m`), injetam uma codificação posicional/espacial fixa por coluna, e em ambos os casos o material fixa o mesmo protocolo experimental (70% treino / 30% teste, *oversampling* no treino, limiar de decisão 0,30, semente aleatória fixa).

### FT-Transformer (Feature Tokenizer Transformer)

Cada variável (numérica ou categórica) é projetada em um vetor de dimensão fixa $d_{model}$ (projeção linear para numéricas, *embedding lookup* para categóricas), e um **token especial [CLS]**, inicializado como vetor treinável, é adicionado ao início da sequência. Após a camada de self-attention, o [CLS] agrega informação de todas as variáveis via seus pesos de atenção; uma FFN padrão é aplicada **token a token, de forma independente** (sem troca de informação entre colunas nessa etapa); ao final, **todos os tokens de variáveis são descartados** e apenas o vetor do [CLS] alimenta a MLP de classificação final.

!!! example "Por que usar [CLS] em vez de concatenar tudo?"
    O material apresenta três justificativas: **(1)** regularização estrutural — concatenar tudo dá liberdade excessiva à camada final para "decorar" combinações específicas de treino (overfitting), enquanto o [CLS] força o modelo a aprender padrões gerais de interação via atenção; **(2)** a agregação via [CLS] é **dinâmica por amostra** (os pesos de atenção mudam cliente a cliente), enquanto a concatenação + FFN usa pesos estáticos fixos após o treino; **(3)** interpretabilidade "de graça" — basta ler os pesos de atenção do [CLS] para saber exatamente qual variável pesou mais na decisão, sem precisar de técnicas pós-hoc como SHAP ou LIME.

### STab (Spatial-Tabular Transformer)

Não usa token [CLS]: a sequência mantém exatamente um token por atributo. Em vez da FFN padrão, usa um **Modulador Espacial de Canais** (*Spatial Channel Modulator*), que trata o conjunto de todas as variáveis como um "campo espacial" e re-escala ativamente a amplitude de cada canal de cada variável, antes de concatenar todos os tokens atualizados em um único vetor denso (*spatial flattening*) que alimenta a MLP final — nenhuma variável é descartada.

A fórmula central do modulador:

$$y_i = s_i(Z_{\text{todas}}) \odot H_{\text{proj}}(x_i) + x_i$$

onde $H_{\text{proj}}(x_i) = W_2 \cdot \text{GELU}(W_1 x_i + b_1) + b_2$ é uma sugestão de ajuste local (MLP de 2 camadas), $s_i(Z_{\text{todas}}) = \sigma(W_s \cdot \text{Pooling}(Z_{\text{todas}}) + b_s)$ é um "controle de volume" (0 a 1) calculado a partir de um resumo global de **todas** as variáveis da linha, $\odot$ é o produto de Hadamard (elemento a elemento, não produto escalar), e a soma final com $x_i$ é uma conexão residual que preserva o dado original.

!!! example "Analogia da mesa de som"
    O FFN comum do FT-Transformer é como "músicos em cabines isoladas", cada um ajustando seu próprio equalizador sem saber o volume dos outros. O Modulador Espacial do STab é o "engenheiro de som mestre": escuta a banda inteira tocando junto e, com um fader por canal, pode subir o volume do "atraso de pagamento" e baixar variáveis secundárias, deixando o sinal de alerta de churn mais evidente para o classificador final.

### Comparação de resultados

No estudo de caso de churn, o **FT-Transformer** obteve o maior AUROC (0,8052) no conjunto de teste; o **STab** obteve o maior Recall (94,02%) e a maior estatística KS (0,4680) — ou seja, cada arquitetura se destacou em uma métrica diferente, sem um "vencedor" absoluto nos slides.

## PatchTST: Transformers para séries temporais

Baseado no paper **NIE, Y.; NGUYEN, N. H.; SINTHONG, P.; KALAGNANAM, J. "A Time Series is Worth 64 Words: Long-term Forecasting with Transformers"** (ICLR 2023, Princeton University e IBM Research), aplicado no material a um estudo de caso com a série histórica do Bitcoin (2017–2023).

### Patching e independência de canais

O problema que o PatchTST resolve: um Transformer clássico, processando a série ponto a ponto (dia a dia), fica excessivamente sensível ao ruído de alta frequência e tende a cair em falsos sinais (*bull traps*). A solução:

- **Patching**: agrupar dias consecutivos em *patches* (ex.: 7 dias = 1 semana), convertendo cada patch em um único token via projeção linear — o número de patches é $N = \lfloor (L-P)/S \rfloor + 1$, onde $L$ é o tamanho da janela, $P$ o tamanho do patch e $S$ o *stride*. Isso reduz a complexidade da atenção de $O(L^2)$ para $O((L/P)^2)$ — no exemplo do material, ~49× mais rápido.
- **Channel independence (CI)**: cada variável (preço, volume, indicadores) é tratada como uma série univariada isolada, processada pela mesma rede/pesos compartilhados, evitando contaminação de escala entre variáveis heterogêneas.

!!! note "Atenção bidirecional no Encoder (não causal)"
    O PatchTST usa apenas o **Encoder** do Transformer (como o BERT), não o Decoder (como o GPT) — por isso a atenção **não é mascarada**: um patch mais antigo (ex.: Semana 1) pode legitimamente atribuir peso alto a um patch mais recente (Semana 2), porque toda a janela de histórico já é conhecida de uma vez. O objetivo do encoder é construir a representação mais rica possível de todo o passado antes de prever o futuro real — diferente de um decoder causal, que nunca pode "olhar para frente".

### Resultados no estudo de caso (Bitcoin, teste 2022–2023)

| Modo | Métrica | Resultado |
|---|---|---|
| Residual (preço em USD, $P_{pred} = SMA_7 + \hat\Delta_{PatchTST}$) | RMSE | \$1.084,22 (−36,8% vs. SMA-7 pura) |
| Residual | MAPE / R² | 2,45% / 98,84% |
| Classificação (convicção ≥ 70% compra / ≤ 30% venda) | Acurácia direcional (POCID) | 63,48% (+7,09 p.p. vs. SMA-7) |

## Pré-processamento de dados

Passos de tratamento da base de dados antes da modelagem (ex.: para o projeto final de churn):

- **Análise exploratória**: histogramas, *box plots* e estatísticas descritivas (mínimo, máximo, mediana, média, quartis).
- **Dados ausentes e outliers**: identificação e tratamento.
- **Codificação de variáveis categóricas**:
    - **Integer encoding** — quando há ordem natural entre as categorias.
    - **One-hot encoding** — para variáveis com poucos valores possíveis (ex.: 3 a 5 categorias).
    - **Binary encoding** — para variáveis com muitos valores possíveis.
- **Normalização** de variáveis numéricas.
- **Binning** — agrupamento de valores contínuos em faixas.
- **Análise de correlação** — entre variáveis independentes, e de cada uma com a variável dependente (alvo).
- **Seleção e combinação de variáveis** (ex.: soma, divisão entre colunas, gerando novas variáveis agregadas).

!!! tip "Recursos citados no material"
    [Tutorial completo de ciência de dados em Python](https://www.analyticsvidhya.com/blog/2016/01/complete-tutorial-learn-data-science-python-scratch-2/) · [Entendendo distribuições populacionais via estatística](https://www.analyticsvidhya.com/blog/2014/07/statistics/) · [100 Days of ML Code](https://github.com/Avik-Jain/100-Days-Of-ML-Code) · [Histogramas e Binning (Python Data Science Handbook)](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.05-Histograms-and-Binnings.ipynb).

## Projeto final: previsão de Churn

### O problema

Prever se um cliente de telecomunicações vai **abandonar (churn)** a empresa — classificação binária — usando a base pública do Kaggle [*"Customers Churned in Telecom Services"*](https://www.kaggle.com/datasets/kapturovalexander/customers-churned-in-telecom-services/data): ~7.000 registros, 19 variáveis independentes (gênero, se é idoso, se tem parceiro/dependentes, tempo como cliente, tipo de serviço de internet/telefone, tipo de contrato, método de pagamento, faturamento sem papel, etc.) e a variável alvo **Churn** (27% dos clientes da base migraram, 73% permaneceram).

### Objetivo pedagógico

Dar uma visão prática do uso de redes neurais na solução de um problema real, consolidar os conhecimentos teóricos da disciplina e permitir contato com ferramentas como GitHub, Keras e Scikit-learn em Python.

### Modelos a investigar

MLP, modelo baseado em Transformer (STab), TabPFN v2 Transformer, KAN (versão mais recente), TabKAN, Mitra (Amazon) e Gradient Boosting/XGBoost como baseline de comparação. Recomendação de ordem: começar por MLP e XGBoost, só então experimentar os modelos mais complexos (STab, TabPFNv2).

### Preparação dos dados

Divisão em conjuntos de **Treinamento, Validação e Teste**, estatisticamente representativos e **sem sobreposição** (nenhuma informação do teste pode influenciar normalização/ajuste feitos no treino — vazamento de dados). O particionamento é feito por classe (separando Classe 1 e Classe 2), depois cada classe é subdividida (50%/25%/25%), e os blocos finais são recombinados e aleatorizados para formar treino/validação/teste mantendo a proporção de classes.

### Métricas de avaliação

- **Estatística de Kolmogorov-Smirnov (KS)** — métrica **principal** do projeto.
- MSE (erro médio quadrático) ou entropia cruzada (comparados entre si como parâmetros a variar).
- Matriz de confusão, curva ROC, Precision, Recall, F-measure e Acurácia.

!!! example "Lendo o KS Statistic"
    O material mostra três faixas de referência: KS ≈ 0,247 → "desempenho ainda ruim"; KS ≈ 0,278 → "desempenho bom"; KS ≈ 0,302 → "desempenho muito bom".

### Lições práticas repassadas pelo professor

- Comece com uma rede **pequena** (1 camada, 10 unidades) — a melhor rede costuma ser a menor que resolve bem o problema (navalha de Occam).
- Defina um número máximo de épocas alto (10.000) e use critério de parada por paciência (*patience*, *max fail* = 20).
- Taxas de aprendizagem menores custam mais tempo, mas tendem a gerar melhores resultados.
- Faça backup automático dos experimentos, documente o processo e registre o desempenho de forma evolutiva a cada etapa — e **não elimine variáveis** no primeiro modelo (exceto identificadores).
- Comece o projeto com antecedência — deixar para a última semana não funciona.
- Considere o **Optuna** para busca de hiperparâmetros (ou *grid search*, como alternativa).

### Entrega

Apresentação final com todos os integrantes do grupo, cobrindo a estrutura experimental e a interpretação dos resultados, com entrega de PPT e código ao final do semestre. Repositório de apoio da disciplina: [github.com/RomeroBarata/IF702-redes-neurais](https://github.com/RomeroBarata/IF702-redes-neurais).
