# Exercícios de teoria da decisão

Exercícios para praticar o conteúdo da página [Teoria da Decisão](teoria-da-decisao.md), do mais simples
ao mais completo. Tente resolver antes de abrir a resposta.

## D1. Critérios sob incerteza e sob risco (resolvido como modelo)

Uma pessoa vai aplicar R\$ 10 mil por um ano em **ações**, **imóvel (fundo)** ou **poupança**. O ganho
(R\$ mil) depende da economia:

| | Recessão | Estável | Crescimento |
|---|---|---|---|
| Ações | −2,0 | 1,0 | 4,0 |
| Imóvel | −0,5 | 0,8 | 2,0 |
| Poupança | 0,6 | 0,6 | 0,6 |

a) Qual ação cada critério recomenda: maximax, maximin, Laplace, Hurwicz com $\alpha=0{,}3$ e Savage?

b) Com $P(\text{recessão})=0{,}2$, $P(\text{estável})=0{,}5$ e $P(\text{crescimento})=0{,}3$, qual é a decisão
pelo VME? Quanto vale, no máximo, uma previsão perfeita da economia?

??? success "Resposta D1"
    **a)**

    | | Melhor | Pior | Média | Hurwicz $0{,}3\cdot\max + 0{,}7\cdot\min$ |
    |---|---|---|---|---|
    | Ações | 4,0 | −2,0 | 1,0 | $1{,}2 - 1{,}4 = -0{,}2$ |
    | Imóvel | 2,0 | −0,5 | 0,767 | $0{,}6 - 0{,}35 = 0{,}25$ |
    | Poupança | 0,6 | 0,6 | 0,6 | $0{,}6$ |

    Maximax: **Ações** (4,0). Maximin: **Poupança** (0,6). Laplace: **Ações** (1,0). Hurwicz
    ($\alpha=0{,}3$, bem pessimista): **Poupança** (0,6).

    Savage: os máximos das colunas são 0,6; 1,0; 4,0.

    | Arrependimento | Recessão | Estável | Crescimento | Máximo |
    |---|---|---|---|---|
    | Ações | 2,6 | 0 | 0 | 2,6 |
    | Imóvel | 1,1 | 0,2 | 2,0 | **2,0** |
    | Poupança | 0 | 0,4 | 3,4 | 3,4 |

    Savage: **Imóvel**. Cinco critérios, três respostas diferentes.

    **b)**

    $$VME(\text{Ações}) = 0{,}2(-2) + 0{,}5(1) + 0{,}3(4) = -0{,}4 + 0{,}5 + 1{,}2 = 1{,}3$$

    $$VME(\text{Imóvel}) = 0{,}2(-0{,}5) + 0{,}5(0{,}8) + 0{,}3(2) = -0{,}1 + 0{,}4 + 0{,}6 = 0{,}9$$

    $$VME(\text{Poupança}) = 0{,}6$$

    Decisão: **Ações** (R\$ 1,3 mil). Com informação perfeita, escolhe-se a melhor de cada coluna:

    $$VE_{\text{info perfeita}} = 0{,}2(0{,}6) + 0{,}5(1{,}0) + 0{,}3(4{,}0) = 1{,}82$$

    $$VEIP = 1{,}82 - 1{,}3 = 0{,}52$$

    Uma previsão perfeita vale no máximo R\$ 520.

## D2. Matriz de perdas

Uma gráfica decide quantas apostilas imprimir (100, 200 ou 300) para um curso cuja procura é incerta: 100,
200 ou 300 alunos, com probabilidades 0,3, 0,5 e 0,2. Cada apostila custa R\$ 10 e é vendida por R\$ 25;
a que sobra vai para reciclagem sem valor. Monte a matriz de lucros, ache a decisão pelo VME e o VEIP.

??? success "Resposta D2"
    Lucro $=25 \cdot \min(\text{impresso}, \text{procura}) - 10 \cdot \text{impresso}$.

    | Imprimir \ Procura | 100 | 200 | 300 | VME |
    |---|---|---|---|---|
    | 100 | 1.500 | 1.500 | 1.500 | 1.500 |
    | 200 | 500 | 3.000 | 3.000 | $0{,}3(500)+0{,}5(3.000)+0{,}2(3.000) = \mathbf{2.250}$ |
    | 300 | −500 | 2.000 | 4.500 | $-150+1.000+900 = 1.750$ |

    Decisão: imprimir **200** (VME de R\$ 2.250).

    $$VE_{\text{info perfeita}} = 0{,}3(1.500) + 0{,}5(3.000) + 0{,}2(4.500) = 450 + 1.500 + 900 = 2.850$$

    $$VEIP = 2.850 - 2.250 = 600$$

    Como montar a matriz é parte da prova: cada célula é uma conta, não um dado pronto. Ex.: imprimir 300 e
    vender 100 dá $25(100) - 10(300) = -500$.

## D3. Construção de utilidade com duas escalas

Uma pessoa vai escolher um destino de viagem e tem a ordem de preferência
$\text{Paris} \succ \text{Roma} \succ \text{Lisboa} \succ \text{Buenos Aires} \succ \text{Santiago}$.

- 1ª rodada (escala com Roma $=1$, Buenos Aires $=0$): ela fica indiferente entre Lisboa certa e 60% de Roma
  / 40% de Buenos Aires.
- 2ª rodada (escala com Paris $=1$, Santiago $=0$): Roma certa $\sim$ 90% de Paris; Buenos Aires certa
  $\sim$ 30% de Paris.

a) Coloque as cinco utilidades na escala da 1ª rodada.

b) Ela prefere Lisboa certa ou um sorteio 50% Paris / 50% Santiago?

c) Para que $\lambda$ ela fica indiferente entre Roma certa e $\lambda\,\text{Paris} + (1-\lambda)\,\text{Lisboa}$?

??? success "Resposta D3"
    **Utilidades lidas das perguntas**: 1ª rodada, $u(\text{Lisboa}) = 0{,}6$; 2ª rodada,
    $v(\text{Roma}) = 0{,}9$ e $v(\text{BA}) = 0{,}3$.

    **a)** Itens-ponte (conhecidos nas duas escalas): Roma e Buenos Aires. Com $u^* = a\,v + b$:

    $$a(0{,}3) + b = 0 \qquad a(0{,}9) + b = 1 \;\Rightarrow\; a = \frac{1}{0{,}6}, \quad b = -\frac{0{,}3}{0{,}6}$$

    $$u^*(D) = \frac{v(D) - 0{,}3}{0{,}6}$$

    | Destino | $v$ (2ª rodada) | $u^*$ |
    |---|---|---|
    | Paris | 1 | $0{,}7/0{,}6 = 7/6 \approx 1{,}167$ |
    | Roma | 0,9 | 1 |
    | Lisboa | — | 0,6 (já estava nesta escala) |
    | Buenos Aires | 0,3 | 0 |
    | Santiago | 0 | $-0{,}3/0{,}6 = -0{,}5$ |

    **b)** $u(\text{sorteio}) = 0{,}5(7/6) + 0{,}5(-0{,}5) = 0{,}583 - 0{,}25 \approx 0{,}333 < 0{,}6$.
    Prefere **Lisboa certa**.

    **c)**

    $$\lambda\cdot\frac{7}{6} + (1-\lambda)\cdot 0{,}6 = 1 \;\Rightarrow\; \lambda\left(\frac{7}{6} - \frac{3}{5}\right) = 0{,}4 \;\Rightarrow\; \lambda\cdot\frac{17}{30} = \frac{12}{30} \;\Rightarrow\; \lambda = \frac{12}{17} \approx 0{,}71$$

    **Variação**: dava para fazer o caminho contrário, levando a 1ª rodada para a escala Paris–Santiago
    com $v = 0{,}3 + 0{,}6\,u$. Lisboa ficaria $0{,}3 + 0{,}6(0{,}6) = 0{,}66$. As respostas de b e c
    não mudam, porque a escala é arbitrária (Lema 5).

## D4. Utilidade para dinheiro por faixas

Um empresário responde:

- na escala R\$ 0 a R\$ 10 mil: R\$ 1.000 certos $\sim$ 20% de chance de R\$ 10 mil;
- na escala R\$ 0 a R\$ 100 mil: R\$ 10 mil certos $\sim$ 60% de chance de R\$ 100 mil;
- na escala R\$ 0 a R\$ 1 milhão: R\$ 100 mil certos $\sim$ 85% de chance de R\$ 1 milhão.

a) Coloque R\$ 1 mil, R\$ 10 mil e R\$ 100 mil na escala de R\$ 0 a R\$ 1 milhão.

b) Ele prefere R\$ 10 mil certos ou 50% de R\$ 100 mil e 50% de R\$ 0?

c) Estime o equivalente certo desse jogo (interpole linearmente entre os pontos conhecidos) e o prêmio de
risco. Ele é avesso, neutro ou propenso ao risco nessa faixa?

??? success "Resposta D4"
    **a)** Em cada extensão, os pontos-ponte são R\$ 0 (vale 0 nas duas escalas) e o topo da escala menor.
    Por isso $b=0$ e $a$ = utilidade do topo antigo na escala nova:

    $$v_{0,10^6}(100\text{ mil}) = 0{,}85$$

    $$v_{0,10^6}(10\text{ mil}) = 0{,}85 \times 0{,}6 = 0{,}51$$

    $$v_{0,10^6}(1\text{ mil}) = 0{,}51 \times 0{,}2 = 0{,}102$$

    **b)** $u(\text{jogo}) = 0{,}5(0{,}85) + 0{,}5(0) = 0{,}425 < 0{,}51 = u(10\text{ mil})$. Prefere os
    **R\$ 10 mil certos**, embora o jogo tenha VE de R\$ 50 mil.

    **c)** $u(EC) = 0{,}425$, entre R\$ 1 mil (0,102) e R\$ 10 mil (0,51):

    $$EC \approx 1.000 + \frac{0{,}425 - 0{,}102}{0{,}51 - 0{,}102} \times 9.000 \approx 8.125$$

    $$PR = VE - EC \approx 50.000 - 8.125 = 41.875$$

    Prêmio de risco positivo e grande: **fortemente avesso ao risco** nessa faixa.

## D5. Escolha com função utilidade dada

A utilidade de uma pessoa é $u(x) = \ln\left(1 + \dfrac{x}{1.000}\right)$, com $x$ em reais. Ela pode
escolher:

- **A**: R\$ 2.000 certos;
- **B**: 80% de R\$ 3.000 e 20% de nada;
- **C**: 50% de R\$ 8.000 e 50% de nada.

Qual ela escolhe? Calcule o equivalente certo e o prêmio de risco de B.

??? success "Resposta D5"
    $$u(A) = \ln 3 \approx 1{,}0986$$

    $$u(B) = 0{,}8\ln 4 + 0{,}2\ln 1 = 0{,}8(1{,}3863) \approx 1{,}1090$$

    $$u(C) = 0{,}5\ln 9 + 0{,}5\ln 1 = 0{,}5(2{,}1972) \approx 1{,}0986$$

    Escolhe **B**. Curiosidade: A e C empatam, pois $0{,}5\ln 9 = \ln 3$.

    Equivalente certo de B: $\ln(1 + EC/1.000) = 1{,}1090$, então
    $EC = 1.000(e^{1{,}1090} - 1) \approx$ R\$ 2.031. Como $VE(B) = 0{,}8 \times 3.000 = 2.400$, o prêmio de
    risco é $\approx$ R\$ 369. A função $\ln$ é côncava, então a pessoa é avessa ao risco.

## D6. Atitude diante do risco

Para cada função utilidade, calcule o equivalente certo do jogo "50% de R\$ 0 e 50% de R\$ 100" e
classifique a atitude: (a) $u(x) = \sqrt{x}$; (b) $u(x) = x$; (c) $u(x) = x^2$.

??? success "Resposta D6"
    VE do jogo = R\$ 50 nos três casos.

    **(a)** $E[u] = 0{,}5\sqrt{100} = 5$, então $EC = 5^2 = 25 < 50$: **avesso** ($PR = 25$).

    **(b)** $E[u] = 50$, então $EC = 50 = VE$: **neutro** ($PR = 0$).

    **(c)** $E[u] = 0{,}5(100^2) = 5.000$, então $EC = \sqrt{5.000} \approx 70{,}7 > 50$: **propenso**
    ($PR \approx -20{,}7$, ou seja, pagaria mais que o valor esperado para jogar).

    Regra: côncava → avesso; linear → neutro; convexa → propenso. Na curva em "S" do handout, as três
    situações aparecem em faixas diferentes de dinheiro.

## D7. Árvore com pesquisa de mercado (valor da informação)

Uma empresa decide se lança um app. Se lançar: sucesso (probabilidade 0,4) dá lucro de R\$ 500 mil;
fracasso (0,6) dá prejuízo de R\$ 200 mil. Não lançar dá zero. Antes, pode encomendar uma pesquisa de
R\$ 20 mil, que dá "favorável" ou "desfavorável". Pelo histórico: quando o app faz sucesso, a pesquisa saiu
favorável 80% das vezes; quando fracassa, saiu favorável 30% das vezes.

a) Sem pesquisa, qual é a decisão e o VME?

b) Vale a pena fazer a pesquisa? Desenhe a árvore e faça o fold back.

c) Quanto vale a informação perfeita?

??? success "Resposta D7"
    **a)** $VME(\text{lançar}) = 0{,}4(500) + 0{,}6(-200) = 200 - 120 = 80$ > 0: lançar, com VME de
    R\$ 80 mil.

    **b)** Primeiro, as probabilidades com Bayes:

    $$P(\text{Fav}) = P(\text{Fav}\mid S)P(S) + P(\text{Fav}\mid F)P(F) = 0{,}8(0{,}4) + 0{,}3(0{,}6) = 0{,}32 + 0{,}18 = 0{,}5$$

    $$P(S \mid \text{Fav}) = \frac{0{,}32}{0{,}5} = 0{,}64 \qquad P(S \mid \text{Desf}) = \frac{0{,}4 \times 0{,}2}{0{,}5} = \frac{0{,}08}{0{,}5} = 0{,}16$$

    ```mermaid
    flowchart LR
        D0{{"Pesquisar?"}} -->|"sim (−20)"| R((Resultado))
        D0 -->|não| L0{{"Lançar?"}}
        R -->|"Fav 0,5"| D1{{"Lançar?"}}
        R -->|"Desf 0,5"| D2{{"Lançar?"}}
        D1 -->|lançar| E1(("S 0,64 / F 0,36"))
        D1 -->|não| Z1["0"]
        D2 -->|lançar| E2(("S 0,16 / F 0,84"))
        D2 -->|não| Z2["0"]
        L0 -->|lançar| E0(("S 0,4 / F 0,6"))
        L0 -->|não| Z0["0"]
    ```

    Fold back:

    - Favorável e lançar: $0{,}64(500) + 0{,}36(-200) = 320 - 72 = 248$ > 0: **lança**.
    - Desfavorável e lançar: $0{,}16(500) + 0{,}84(-200) = 80 - 168 = -88$ < 0: **não lança** (0).
    - Nó do resultado: $0{,}5(248) + 0{,}5(0) = 124$.

    $$VEIA = 124 - 80 = 44 > 20 \text{ (custo)}$$

    **Vale pesquisar**: VME com pesquisa $= 124 - 20 = 104 > 80$. Política ótima: pesquisar; lançar só se
    der favorável.

    **c)** Com informação perfeita: lança só quando vai dar sucesso.

    $$VE = 0{,}4(500) + 0{,}6(0) = 200 \qquad VEIP = 200 - 80 = 120$$

    Confere $VEIA (44) \le VEIP (120)$: uma pesquisa imperfeita vale menos que a informação perfeita.

## D8. Árvore sequencial (estilo medicamento, sem desconto)

Uma empresa de biotecnologia decide se testa um produto. O **teste 1** custa R\$ 10 milhões e tem 60% de
sucesso. Se passar, decide se faz o **teste 2**, que custa R\$ 30 milhões e tem 50% de sucesso. Se passar
no teste 2, recebe R\$ 200 milhões. Monte a árvore, calcule os valores nos nós de fim e faça o fold back.

??? success "Resposta D8"
    **Nós de fim** (somando tudo no caminho):

    | Caminho | Valor |
    |---|---|
    | Teste 1 falha | −10 |
    | Teste 1 passa → não faz teste 2 | −10 |
    | Teste 1 passa → teste 2 falha | $-10 - 30 = -40$ |
    | Teste 1 passa → teste 2 passa | $-10 - 30 + 200 = 160$ |
    | Não testar | 0 |

    **Fold back**:

    1. Evento do teste 2: $0{,}5(160) + 0{,}5(-40) = 60$.
    2. Decisão após o teste 1: $\max(60;\,-10) = 60$ → **faz o teste 2**.
    3. Evento do teste 1: $0{,}6(60) + 0{,}4(-10) = 36 - 4 = 32$.
    4. Raiz: $\max(32;\,0)$ → **testar**, com VME de R\$ 32 milhões.

    A faixa de resultados vai de −40 a +160: é o risco que a árvore mostra junto com o VME.

## D9. Axiomas: identifique o problema

Para cada caso, diga qual axioma da teoria de von Neumann-Morgenstern está sendo violado.

a) Uma pessoa diz que prefere café a chá, chá a suco e suco a café.

b) Um gestor diz que não consegue comparar dois projetos: "nem prefiro um, nem sou indiferente".

c) Alguém prefere R\$ 100 certos a R\$ 50 certos, mas prefere "10% de R\$ 50 e 90% de uma viagem" a "10% de
R\$ 100 e 90% da mesma viagem".

d) Alguém diz que prefere R\$ 1 milhão a R\$ 10 mil e R\$ 10 mil a R\$ 0, mas que nenhuma loteria entre
R\$ 1 milhão e R\$ 0, com qualquer probabilidade, é equivalente a R\$ 10 mil.

??? success "Resposta D9"
    a) **Transitividade** (Axioma 2): forma um ciclo; a pessoa poderia ser explorada indefinidamente
    trocando um pelo outro.

    b) **Completeza** (Axioma 1): ou prefere um, ou o outro, ou é indiferente.

    c) **Dominância/independência** (Axioma 3): misturar a mesma coisa (90% da viagem) dos dois lados não
    deveria inverter a preferência.

    d) **Arquimediano** (Axioma 4): se $P \succ Q \succ R$, deve existir um $\lambda$ de indiferença.

## D10. Conceitos (questões curtas)

a) Classifique como decisão sob certeza, risco ou incerteza: (i) escolher a rota mais curta num mapa;
(ii) uma seguradora precificando seguro de carro com base em estatísticas de acidentes; (iii) lançar um
produto totalmente inédito, sem nenhum histórico de mercado.

b) Um gestor recusou um projeto com VME positivo e, um ano depois, o mercado mostrou que o projeto teria
dado muito lucro. Ele tomou uma má decisão?

c) Por que, numa árvore de decisão, se usa **média ponderada** nos círculos e **máximo** nos quadrados?

??? success "Resposta D10"
    a) (i) **Certeza**. (ii) **Risco**: há probabilidades estimadas a partir de dados. (iii) **Incerteza**:
    não há base para estimar probabilidades (usaria critérios como maximin ou Hurwicz, ou buscaria
    informação para passar a risco).

    b) Não necessariamente. Decisão e consequência são coisas diferentes. Se, com o que se sabia na época,
    o gestor tinha razões para recusar (por exemplo, aversão ao risco, com a utilidade esperada menor que a
    de não investir), a decisão pode ter sido boa e a consequência, azar. Avalia-se o **processo**.

    c) No círculo, quem escolhe é a natureza: não se controla o ramo, então o melhor que se pode dizer é o
    valor **esperado**. No quadrado, quem escolhe é o decisor: ele vai pegar o ramo **melhor**.

## D11. Exercício do handout com outra pergunta (João)

Usando $u(p) = 0{,}62\log_{10}(4 \times 10^{-6}p + 1)$ do Exercício 03, João prefere R\$ 40.000 certos ou um
jogo com 50% de R\$ 0 e 50% de R\$ 100.000?

??? success "Resposta D11"
    $$u(40.000) = 0{,}62\log_{10}(1{,}16) \approx 0{,}62(0{,}0645) \approx 0{,}0400$$

    $$u(\text{jogo}) = 0{,}5\,u(0) + 0{,}5 \times 0{,}62\log_{10}(1{,}4) \approx 0{,}5(0{,}62)(0{,}1461) \approx 0{,}0453$$

    Prefere o **jogo**. O equivalente certo do jogo é a solução de $u(EC) = 0{,}0453$. Dividindo por 0,62,
    $\log_{10}(4 \times 10^{-6}EC + 1) \approx 0{,}0731$; então:

    $$EC = \frac{10^{0{,}0731} - 1}{4 \times 10^{-6}} \approx 45.800$$

    Fica abaixo do VE de R\$ 50.000 (João é levemente avesso ao risco), mas acima dos R\$ 40.000.
