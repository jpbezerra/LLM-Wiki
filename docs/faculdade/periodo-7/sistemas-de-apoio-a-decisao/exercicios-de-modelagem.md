# Exercícios de modelagem (estilo da prova)

Exercícios no mesmo formato dos estudos de caso da disciplina (campanha de publicidade, VVC, refinaria):
um enunciado em texto corrido, uma tabela de dados e o pedido de **formular o modelo analítico** e
**discutir outras restrições e fatores**.

!!! warning "O que o professor cobra"
    O foco da avaliação é o **caminho**: definir bem as **variáveis de decisão**, escrever a **função
    objetivo** e traduzir cada regra do enunciado em uma **restrição**. O número final sai do Solver. Por
    isso, cada resposta abaixo mostra primeiro a formulação completa; o resultado numérico aparece só no
    fim, como conferência para quem rodar no Solver.

## Roteiro de 5 passos para qualquer enunciado

**1. Ache a pergunta.** Procure o verbo da decisão: "quanto produzir", "onde investir", "quantas
veiculações", "quanto transportar". O "quanto de quê" vira a variável de decisão.

**2. Defina as variáveis por escrito, com unidade.** Ex.: "$x_1$ = número de veiculações na TV em horário
normal". Se houver dois índices (origem e destino, produto e mês), use $x_{ij}$ e diga o que é cada índice.
Uma variável mal definida derruba o modelo inteiro.

**3. Escreva a função objetivo.** "Maximizar lucro, clientes, retorno" ou "minimizar custo, distância,
tempo". É sempre $\sum (\text{contribuição unitária}) \times (\text{variável})$.

**4. Transforme cada frase com número em restrição.** Leia o enunciado frase por frase e risque cada
limite usado. Use o dicionário abaixo.

**5. Feche com o domínio.** Não-negatividade ($x \ge 0$), limites como $0 \le x \le 1$ (frações) e, se fizer
sentido, integralidade ("$x$ inteiro").

### Dicionário: do português para a restrição

| Frase no enunciado | Restrição |
|---|---|
| "não pode gastar mais de 800 mil", "no máximo", "até", "não exceder", "disponível" | $\ldots \le 800.000$ |
| "no mínimo", "pelo menos", "não menos que", "atender a demanda" | $\ldots \ge b$ |
| "exatamente", "toda a produção", "deve ser igual" | $\ldots = b$ |
| "entre 5 e 10" | **duas** restrições: $x \ge 5$ e $x \le 10$ |
| "gastar no máximo R\$ 500 mil com TV" | só as variáveis de TV: $40.000x_1 + 75.000x_2 \le 500.000$ |
| "comum deve ser no mínimo 16 vezes a verde" | $x_c \ge 16x_v$, ou $x_c - 16x_v \ge 0$ |
| "no máximo 40% do total em ações" | $x_a \le 0{,}4(x_a + x_b + \dots)$, ou seja, $0{,}6x_a - 0{,}4x_b - \dots \le 0$ |
| "o produto A deve ser pelo menos o dobro de B" | $x_A \ge 2x_B$ |
| "a participação deve ser a mesma em todos os anos" | **uma** variável (a fração) multiplica o desembolso de cada ano |
| "pode ser fracionado", "participação" | $0 \le x \le 1$ (fração) |
| "número de veiculações, peças, pessoas" | $x$ inteiro (se arredondar distorcer) |
| "estoque do mês passa para o mês seguinte" | balanço: $I_t = I_{t-1} + \text{produção}_t - \text{demanda}_t$ |
| "o que entra em um depósito é o que sai" (transbordo) | $\sum \text{entradas} = \sum \text{saídas}$ |

!!! tip "Armadilha das porcentagens"
    "No máximo 40% do total" **não** é $x_a \le 0{,}4$. É $x_a \le 0{,}4 \times (\text{soma de todas as
    variáveis})$. Passando tudo para a esquerda, fica linear: $0{,}6x_a - 0{,}4(x_b+x_c+x_d) \le 0$. Só vira
    $x_a \le 0{,}4 \cdot T$ quando o total $T$ é um número fixo (por exemplo, "investir exatamente 1 milhão").

### Checklist para "discuta outras restrições e fatores"

Quase toda prova termina pedindo isso. Em vez de decorar respostas, passe pelas categorias:

- **Incerteza nos dados**: demanda, preço ou audiência são previsões. Saída: análise de sensibilidade,
  cenários ou restrições de chance (Arenales, Seção 2.2.3).
- **Não linearidades**: saturação/retornos decrescentes (a 10ª veiculação rende menos que a 1ª), descontos
  por volume, custos fixos (preparar máquina, contratar).
- **Integralidade**: veiculações, pessoas e máquinas são inteiros, o que vira programação inteira.
- **Interação entre variáveis**: sobreposição de público, produtos que competem pelo mesmo mercado,
  projetos dependentes ("só faço D se fizer E").
- **Tempo**: sazonalidade, vários períodos, estoque e caixa passando de um período para outro.
- **Recursos esquecidos**: mão de obra, armazenagem, transporte, capital de giro.
- **Políticas e regras**: diversificação mínima, limites legais e ambientais, contratos mínimos.
- **Outros objetivos**: risco, imagem, qualidade, que levam a multicritério ou a uma restrição do tipo
  "risco $\le$ limite".

---

## M1. Marcenaria (mix de produção)

A Marcenaria Pau-Brasil fabrica **mesas**, **cadeiras** e **estantes**. Por semana, há 200 m² de madeira,
240 h de carpintaria e 150 h de acabamento. Uma mesa usa 3 m² de madeira, 4 h de carpintaria e 2 h de
acabamento, e dá lucro de R\$ 120. Uma cadeira usa 1 m², 1,5 h e 0,5 h, com lucro de R\$ 30. Uma estante
usa 4 m², 3 h e 3 h, com lucro de R\$ 150. O mercado absorve no máximo 20 estantes por semana, e como as
mesas são vendidas em conjunto, deve-se fabricar **pelo menos 4 cadeiras para cada mesa**.

Formule o modelo que maximize o lucro semanal. Discuta outras restrições e fatores.

??? success "Resolução M1"
    **Variáveis**: $x_1$ = mesas, $x_2$ = cadeiras, $x_3$ = estantes produzidas por semana.

    **Função objetivo**:

    $$\text{max } Z = 120x_1 + 30x_2 + 150x_3$$

    **Restrições**:

    $$
    \begin{aligned}
    3x_1 + x_2 + 4x_3 &\le 200 \quad \text{(madeira)}\\
    4x_1 + 1{,}5x_2 + 3x_3 &\le 240 \quad \text{(carpintaria)}\\
    2x_1 + 0{,}5x_2 + 3x_3 &\le 150 \quad \text{(acabamento)}\\
    x_3 &\le 20 \quad \text{(mercado de estantes)}\\
    x_2 &\ge 4x_1 \quad \text{(4 cadeiras por mesa)}\\
    x_1, x_2, x_3 &\ge 0 \text{ e inteiros}
    \end{aligned}
    $$

    A regra "4 cadeiras por mesa" é a que mais gente erra: é $x_2 \ge 4x_1$ (cadeiras são 4 vezes as mesas),
    e **não** $4x_2 \ge x_1$. Teste com números: 5 mesas exigem pelo menos 20 cadeiras, e
    $20 \ge 4 \cdot 5$ confere.

    **Outros fatores**: estoque de produtos acabados, prazo de secagem do verniz, demanda máxima de mesas e
    cadeiras, perdas de madeira no corte, horas extras.

    **Conferência (Solver)**: contínuo, $x \approx (17{,}1;\ 68{,}6;\ 20)$ e $Z \approx$ R\$ 7.114. Inteiro,
    $x=(17;\ 69;\ 20)$ e $Z=$ R\$ 7.110. Madeira e estantes ficam no limite.

## M2. Dieta hospitalar (mistura, minimizar custo)

A nutricionista de um hospital monta o cardápio diário de um paciente com **arroz**, **feijão**,
**frango** e **leite**, medidos em porções. A dieta precisa ter pelo menos 70 g de proteína, pelo menos
14 mg de ferro e entre 2.000 e 2.600 kcal. Por restrições clínicas, o paciente não pode tomar mais de 3
porções de leite, comer mais de 6 de arroz nem mais de 4 de feijão.

| Por porção | Arroz | Feijão | Frango | Leite |
|---|---|---|---|---|
| Proteína (g) | 3 | 8 | 25 | 8 |
| Ferro (mg) | 1 | 2 | 2,5 | 1,5 |
| Energia (kcal) | 130 | 140 | 200 | 120 |
| Custo (R\$) | 0,40 | 0,60 | 2,50 | 1,20 |

Formule o modelo de menor custo. Discuta outras restrições e fatores.

??? success "Resolução M2"
    **Variáveis**: $x_A, x_F, x_G, x_L$ = porções diárias de arroz, feijão, frango e leite.

    $$\text{min } Z = 0{,}40x_A + 0{,}60x_F + 2{,}50x_G + 1{,}20x_L$$

    $$
    \begin{aligned}
    3x_A + 8x_F + 25x_G + 8x_L &\ge 70 \quad \text{(proteína)}\\
    x_A + 2x_F + 2{,}5x_G + 1{,}5x_L &\ge 14 \quad \text{(ferro)}\\
    130x_A + 140x_F + 200x_G + 120x_L &\ge 2.000 \quad \text{(energia mínima)}\\
    130x_A + 140x_F + 200x_G + 120x_L &\le 2.600 \quad \text{(energia máxima)}\\
    x_L \le 3, \quad x_A &\le 6, \quad x_F \le 4\\
    x_A, x_F, x_G, x_L &\ge 0
    \end{aligned}
    $$

    "Entre 2.000 e 2.600 kcal" gera **duas** restrições com o mesmo lado esquerdo.

    **Outros fatores**: palatabilidade e variedade (o Solver tende a repetir sempre a mesma combinação),
    outros nutrientes (sódio, gordura, fibras), porções inteiras ou meias porções, preferências do paciente.

    **Conferência**: $(6;\ 4;\ 1{,}5;\ 3)$, custo R\$ 12,15 por dia. A energia fica exatamente em 2.000
    kcal (restrição ativa) e a proteína sobra (111,5 g).

## M3. Campanha de marketing digital

Uma loja on-line tem R\$ 100 mil para uma campanha em **Instagram**, **YouTube**, **Google Ads** e
**outdoor**. Quer atingir o maior número possível de pessoas, com pelo menos 500 mil jovens (18–24 anos).
Por política de diversificação, no máximo 40% da verba pode ir para o Instagram e no máximo 20% para o
Google Ads. Já existe um contrato de outdoor que obriga a gastar pelo menos R\$ 10 mil nesse meio.

| Para cada R\$ 1 mil investido | Instagram | YouTube | Google Ads | Outdoor |
|---|---|---|---|---|
| Pessoas atingidas (mil) | 12 | 9 | 7 | 4 |
| Jovens atingidos (mil) | 9 | 6 | 3 | 1 |

Formule o modelo. Discuta outras restrições e fatores.

??? success "Resolução M3"
    Aqui a variável natural é **quanto dinheiro** vai para cada meio (e não quantas veiculações, como no
    estudo de caso da sala), porque os dados vêm "por R\$ 1 mil investido".

    **Variáveis**: $x_I, x_Y, x_G, x_O$ = valor investido (em R\$ mil) em cada meio.

    $$\text{max } Z = 12x_I + 9x_Y + 7x_G + 4x_O \quad \text{(mil pessoas)}$$

    $$
    \begin{aligned}
    x_I + x_Y + x_G + x_O &\le 100 \quad \text{(verba)}\\
    9x_I + 6x_Y + 3x_G + x_O &\ge 500 \quad \text{(jovens)}\\
    x_I &\le 0{,}4(x_I + x_Y + x_G + x_O) \quad \text{(Instagram} \le 40\%)\\
    x_G &\le 0{,}2(x_I + x_Y + x_G + x_O) \quad \text{(Google} \le 20\%)\\
    x_O &\ge 10 \quad \text{(contrato)}\\
    x_I, x_Y, x_G, x_O &\ge 0
    \end{aligned}
    $$

    Linearizando as porcentagens: $0{,}6x_I - 0{,}4x_Y - 0{,}4x_G - 0{,}4x_O \le 0$ e
    $-0{,}2x_I - 0{,}2x_Y + 0{,}8x_G - 0{,}2x_O \le 0$.

    **Outros fatores**: a mesma pessoa vista em vários meios (alcance duplicado), saturação, custo de criar
    os anúncios, conversão em vendas (atingir não é vender), sazonalidade.

    **Conferência**: $x_I=40$, $x_Y=50$, $x_G=0$, $x_O=10$, alcance de 970 mil pessoas. O limite de 40% do
    Instagram e o contrato de outdoor ficam ativos.

## M4. Carteira de investimentos

Um investidor vai aplicar **exatamente R\$ 1 milhão** em **ações**, **CDB**, **Tesouro Direto** e
**fundos imobiliários (FII)**, buscando o maior retorno anual esperado. O assessor impõe: no máximo 40% em
ações; pelo menos 30% em Tesouro; renda fixa (CDB + Tesouro) somando pelo menos 40%; o valor em FII não
pode passar do valor em ações; e o **risco médio ponderado** da carteira deve ser no máximo 1,6.

| | Ações | CDB | Tesouro | FII |
|---|---|---|---|---|
| Retorno esperado ao ano | 14% | 11% | 10% | 12% |
| Índice de risco | 3,0 | 1,0 | 0,5 | 2,0 |

??? success "Resolução M4"
    **Variáveis**: $x_A, x_C, x_T, x_F$ = valor aplicado (R\$ mil) em cada opção.

    $$\text{max } Z = 0{,}14x_A + 0{,}11x_C + 0{,}10x_T + 0{,}12x_F$$

    $$
    \begin{aligned}
    x_A + x_C + x_T + x_F &= 1.000 \quad \text{(aplicar tudo)}\\
    x_A &\le 0{,}4 \cdot 1.000 = 400\\
    x_T &\ge 0{,}3 \cdot 1.000 = 300\\
    x_C + x_T &\ge 400 \quad \text{(renda fixa)}\\
    x_F &\le x_A\\
    \frac{3x_A + x_C + 0{,}5x_T + 2x_F}{1.000} &\le 1{,}6 \;\Rightarrow\; 3x_A + x_C + 0{,}5x_T + 2x_F \le 1.600\\
    x_A, x_C, x_T, x_F &\ge 0
    \end{aligned}
    $$

    Como o total é fixo (1.000), as porcentagens viram números diretamente. Se o enunciado dissesse "até
    1 milhão", seria preciso usar a forma geral $x_A \le 0{,}4(x_A+x_C+x_T+x_F)$. O risco médio é uma
    média ponderada; multiplicando pelo total, fica linear.

    **Outros fatores**: liquidez (resgate antes do prazo), impostos e taxas, correlação entre os ativos (o
    risco de uma carteira não é só a média dos riscos), horizonte de investimento, perfil do investidor.

    **Conferência**: ações 375, CDB 325, Tesouro 300, FII 0; retorno de R\$ 118,25 mil (11,8%). O risco
    (exatamente 1,6) e o piso do Tesouro ficam ativos.

## M5. Fundo de capital semente (estilo VVC)

O fundo Semente Nordeste tem R\$ 80 milhões para aportes neste ano e R\$ 70 milhões no próximo. Pode
comprar participações **fracionadas** em cinco startups; se comprar uma fração neste ano, precisa aportar
a mesma fração da parcela do ano seguinte. Por um acordo de parceria, a participação na startup D não pode
ser maior que a participação na startup E.

| Startup | Aporte ano 1 | Aporte ano 2 | Lucro esperado |
|---|---|---|---|
| A | 20 | 25 | 30 |
| B | 40 | 15 | 45 |
| C | 10 | 20 | 20 |
| D | 30 | 10 | 35 |
| E | 15 | 30 | 25 |

(valores em R\$ milhões)

??? success "Resolução M5"
    **Variáveis**: $x_A, \dots, x_E$ = fração (de 0 a 1) da rodada de cada startup comprada pelo fundo. Uma
    única variável por startup garante a regra "mesma participação nos dois anos".

    $$\text{max } Z = 30x_A + 45x_B + 20x_C + 35x_D + 25x_E$$

    $$
    \begin{aligned}
    20x_A + 40x_B + 10x_C + 30x_D + 15x_E &\le 80 \quad \text{(orçamento ano 1)}\\
    25x_A + 15x_B + 20x_C + 10x_D + 30x_E &\le 70 \quad \text{(orçamento ano 2)}\\
    x_D &\le x_E \quad \text{(parceria)}\\
    0 \le x_i &\le 1
    \end{aligned}
    $$

    **Outros fatores**: sobra de um ano não usada no outro (poderia virar variável de caixa), risco de
    cada startup, participação mínima para ter assento no conselho, valor do dinheiro no tempo (lucros
    em anos diferentes).

    **Conferência**: $x_A=1$, $x_B \approx 0{,}946$, $x_C=1$, $x_D=x_E\approx 0{,}270$; lucro $\approx$
    R\$ 108,8 milhões. Os dois orçamentos e a parceria ficam ativos.

## M6. Mistura de sucos

Uma indústria quer produzir **1.000 litros** de um suco misto a partir de concentrados de **laranja**,
**maçã** e **uva**, com o menor custo. O teor de açúcar do produto final deve ficar entre 11% e 13%, a
vitamina C deve ser de pelo menos 25 mg por litro e, para poder estampar "sabor laranja" no rótulo, a
laranja deve ser pelo menos 40% da mistura.

| | Laranja | Maçã | Uva |
|---|---|---|---|
| Custo (R\$/L) | 2,00 | 1,20 | 1,60 |
| Açúcar | 10% | 12% | 16% |
| Vitamina C (mg/L) | 50 | 5 | 10 |

??? success "Resolução M6"
    **Variáveis**: $x_L, x_M, x_U$ = litros de cada concentrado na mistura de 1.000 L.

    $$\text{min } Z = 2{,}0x_L + 1{,}2x_M + 1{,}6x_U$$

    $$
    \begin{aligned}
    x_L + x_M + x_U &= 1.000 \quad \text{(volume)}\\
    0{,}10x_L + 0{,}12x_M + 0{,}16x_U &\ge 0{,}11 \cdot 1.000 = 110 \quad \text{(açúcar mín.)}\\
    0{,}10x_L + 0{,}12x_M + 0{,}16x_U &\le 0{,}13 \cdot 1.000 = 130 \quad \text{(açúcar máx.)}\\
    50x_L + 5x_M + 10x_U &\ge 25 \cdot 1.000 = 25.000 \quad \text{(vitamina C)}\\
    x_L &\ge 0{,}4 \cdot 1.000 = 400 \quad \text{(rótulo)}\\
    x_L, x_M, x_U &\ge 0
    \end{aligned}
    $$

    É o mesmo esquema do problema da ração do livro (Exemplo 2.1): "quantidade do componente $i$ na
    mistura $= \sum_j a_{ij}x_j$", comparada com a exigência. Supõe **aditividade** (o açúcar da mistura é a
    soma dos açúcares), uma das três hipóteses de linearidade.

    **Outros fatores**: disponibilidade de cada concentrado, sabor (testes sensoriais), validade, custo de
    água/embalagem, variação do teor de açúcar entre safras.

    **Conferência**: laranja $\approx 444$ L, maçã $\approx 556$ L, uva 0; custo $\approx$ R\$ 1.555,56. A
    vitamina C fica ativa.

## M7. Transporte de grãos

Três fazendas (F1, F2, F3) produzem 200, 300 e 250 toneladas de milho. Três cooperativas (C1, C2, C3)
precisam de 250, 200 e 300 toneladas. O frete por tonelada (R\$) está abaixo. Formule o modelo de menor
custo.

| | C1 | C2 | C3 |
|---|---|---|---|
| F1 | 8 | 6 | 10 |
| F2 | 9 | 12 | 13 |
| F3 | 14 | 9 | 16 |

??? success "Resolução M7"
    **Variáveis**: $x_{ij}$ = toneladas enviadas da fazenda $i$ à cooperativa $j$ ($i,j = 1,2,3$), nove
    variáveis.

    $$\text{min } Z = 8x_{11} + 6x_{12} + 10x_{13} + 9x_{21} + 12x_{22} + 13x_{23} + 14x_{31} + 9x_{32} + 16x_{33}$$

    $$
    \begin{aligned}
    x_{11} + x_{12} + x_{13} &\le 200 \quad \text{(oferta F1)}\\
    x_{21} + x_{22} + x_{23} &\le 300 \quad \text{(oferta F2)}\\
    x_{31} + x_{32} + x_{33} &\le 250 \quad \text{(oferta F3)}\\
    x_{11} + x_{21} + x_{31} &= 250 \quad \text{(demanda C1)}\\
    x_{12} + x_{22} + x_{32} &= 200 \quad \text{(demanda C2)}\\
    x_{13} + x_{23} + x_{33} &= 300 \quad \text{(demanda C3)}\\
    x_{ij} &\ge 0
    \end{aligned}
    $$

    Regra de bolso: **linhas da tabela = restrições de oferta** (soma na horizontal), **colunas =
    restrições de demanda** (soma na vertical). Aqui a oferta total (750) é igual à demanda total (750),
    então o problema é **balanceado** e as ofertas também serão usadas por inteiro.

    **Outros fatores**: capacidade dos caminhões, estradas interditadas na chuva, custo fixo por viagem,
    prazos de entrega, perdas no transporte.

    **Conferência**: F1→C3: 200; F2→C1: 250; F2→C3: 50; F3→C2: 200; F3→C3: 50. Custo R\$ 7.500.

## M8. Designação de tarefas

Uma software house tem 4 programadores e 4 tarefas urgentes. Cada programador fica com exatamente uma
tarefa e cada tarefa com exatamente um programador. A tabela mostra o tempo estimado (horas). Minimize o
tempo total.

| | T1 | T2 | T3 | T4 |
|---|---|---|---|---|
| Ana | 14 | 5 | 8 | 7 |
| Bruno | 2 | 12 | 6 | 5 |
| Carla | 7 | 8 | 3 | 9 |
| Davi | 2 | 4 | 6 | 10 |

??? success "Resolução M8"
    **Variáveis**: $x_{ij} = 1$ se o programador $i$ fica com a tarefa $j$, e $0$ caso contrário
    (variável **binária**).

    $$\text{min } Z = \sum_{i}\sum_{j} t_{ij}\,x_{ij}$$

    $$
    \begin{aligned}
    \sum_j x_{ij} &= 1 \quad \text{para cada programador } i \quad \text{(uma tarefa por pessoa)}\\
    \sum_i x_{ij} &= 1 \quad \text{para cada tarefa } j \quad \text{(uma pessoa por tarefa)}\\
    x_{ij} &\in \{0, 1\}
    \end{aligned}
    $$

    É o **problema de designação** do livro (Seção 2.2.2): um caso especial do transporte com ofertas e
    demandas iguais a 1. O livro observa que, mesmo trocando $x_{ij} \in \{0,1\}$ por $x_{ij} \ge 0$, a
    solução ótima sai inteira.

    **Conferência**: Ana→T2 (5), Bruno→T4 (5), Carla→T3 (3), Davi→T1 (2); total de 15 h.

## M9. Escala de atendentes (cobertura)

Um call center 24 h divide o dia em 6 faixas de 4 horas. Cada atendente trabalha um turno de **8 horas
seguidas**, que pode começar no início de qualquer faixa. O número mínimo de atendentes em cada faixa é:

| Faixa | 0–4h | 4–8h | 8–12h | 12–16h | 16–20h | 20–24h |
|---|---|---|---|---|---|---|
| Mínimo | 4 | 8 | 14 | 12 | 10 | 6 |

Quantos atendentes devem começar em cada faixa para usar o menor número total de pessoas?

??? success "Resolução M9"
    **Variáveis**: $x_k$ = número de atendentes que **começam** o turno no início da faixa $k$
    ($k=1,\dots,6$).

    O ponto-chave: quem está trabalhando na faixa $k$ é quem começou na faixa $k$ **ou** na anterior
    (porque o turno dura duas faixas).

    $$\text{min } Z = x_1 + x_2 + x_3 + x_4 + x_5 + x_6$$

    $$
    \begin{aligned}
    x_6 + x_1 &\ge 4 \quad \text{(0–4h: quem começou às 20h ainda está lá)}\\
    x_1 + x_2 &\ge 8\\
    x_2 + x_3 &\ge 14\\
    x_3 + x_4 &\ge 12\\
    x_4 + x_5 &\ge 10\\
    x_5 + x_6 &\ge 6\\
    x_k &\ge 0 \text{ e inteiros}
    \end{aligned}
    $$

    O erro mais comum é escrever $x_k \ge \text{mínimo}_k$, esquecendo que um turno cobre duas faixas.

    **Outros fatores**: intervalos de almoço, limite de turnos noturnos por pessoa, folgas semanais, custo
    diferente para turno da madrugada, absenteísmo.

    **Conferência**: mínimo de **28** atendentes (por exemplo, $x = (4, 4, 10, 2, 8, 0)$). Há outras
    escalas com o mesmo total.

## M10. Produção em três meses (planejamento com estoque)

Uma fábrica de chocolates precisa atender a demanda de 1.000, 1.500 e 2.000 caixas em outubro, novembro e
dezembro. Em cada mês, pode produzir até 1.200 caixas em horário normal (R\$ 10 por caixa) e até mais 400
em hora extra (R\$ 14 por caixa). Caixas produzidas antes podem ficar em estoque, ao custo de R\$ 2 por
caixa por mês (cobrado sobre o estoque no fim de cada mês). Há 100 caixas em estoque no início de
outubro.

??? success "Resolução M10"
    **Variáveis** (para $t = 1, 2, 3$): $x_t$ = caixas em horário normal no mês $t$; $h_t$ = caixas em hora
    extra; $I_t$ = estoque no fim do mês $t$.

    $$\text{min } Z = 10(x_1+x_2+x_3) + 14(h_1+h_2+h_3) + 2(I_1+I_2+I_3)$$

    $$
    \begin{aligned}
    I_1 &= 100 + x_1 + h_1 - 1.000 \quad \text{(balanço outubro)}\\
    I_2 &= I_1 + x_2 + h_2 - 1.500 \quad \text{(balanço novembro)}\\
    I_3 &= I_2 + x_3 + h_3 - 2.000 \quad \text{(balanço dezembro)}\\
    x_t &\le 1.200, \quad h_t \le 400\\
    x_t, h_t, I_t &\ge 0
    \end{aligned}
    $$

    É o modelo de **dimensionamento de lotes** do livro (Seção 2.2.3): "estoque de hoje = estoque de ontem
    + produção − demanda". Exigir $I_t \ge 0$ é o que garante que a demanda é atendida sem atraso.

    **Outros fatores**: capacidade do depósito, validade do chocolate, custo de contratar/demitir,
    atraso permitido com multa (estoque negativo, *backlogging*).

    **Conferência**: produção normal no máximo todo mês, hora extra de 400 em novembro e dezembro;
    estoques de 300 e 400 caixas; custo de R\$ 48.600. Compensa antecipar em outubro (custo 10 + 2 de
    estoque = 12) em vez de fazer hora extra (14).

## M11. Planejamento agrícola

Um produtor tem 100 hectares para plantar **soja**, **milho** e **feijão**. Ele dispõe de 650 mil m³ de
água e 1.000 dias-homem de trabalho na safra. Por contrato com uma granja, o milho deve ocupar pelo menos
20% da área plantada, e o feijão não pode passar de 30 ha (limite de armazenagem).

| Por hectare | Soja | Milho | Feijão |
|---|---|---|---|
| Lucro (R\$) | 1.800 | 1.500 | 2.200 |
| Água (mil m³) | 6 | 8 | 5 |
| Mão de obra (dias) | 10 | 6 | 15 |

??? success "Resolução M11"
    **Variáveis**: $x_S, x_M, x_F$ = hectares plantados de cada cultura.

    $$\text{max } Z = 1.800x_S + 1.500x_M + 2.200x_F$$

    $$
    \begin{aligned}
    x_S + x_M + x_F &\le 100 \quad \text{(terra)}\\
    6x_S + 8x_M + 5x_F &\le 650 \quad \text{(água)}\\
    10x_S + 6x_M + 15x_F &\le 1.000 \quad \text{(mão de obra)}\\
    x_M &\ge 0{,}2(x_S + x_M + x_F) \quad \text{(contrato do milho)}\\
    x_F &\le 30\\
    x_S, x_M, x_F &\ge 0
    \end{aligned}
    $$

    Note que a regra fala em "área **plantada**", que pode ser menor que 100 ha. Por isso a porcentagem
    usa a soma das variáveis, e não o número 100. Linearizada: $-0{,}2x_S + 0{,}8x_M - 0{,}2x_F \ge 0$.

    **Outros fatores**: rotação de culturas, risco climático (cenários de chuva), preço futuro das
    commodities, custo de sementes e adubo, crédito rural.

    **Conferência**: soja 32,5 ha, milho 37,5 ha, feijão 30 ha; lucro de R\$ 180.750. Terra, mão de obra e
    o limite de feijão ficam ativos.

## M12. Aplicação de caixa em dois anos (gestão financeira)

Uma empresa tem R\$ 100 mil hoje (ano 0) e quer ter o máximo de dinheiro no fim do ano 2. Opções:

- **A**: aplicar no ano 0 e receber 30% a mais no fim do ano 2 (no máximo R\$ 60 mil);
- **B**: aplicação de 1 ano que rende 15%, disponível no ano 0 e no ano 1;
- **C**: aplicar no ano 1 e receber 25% a mais no fim do ano 2 (no máximo R\$ 50 mil).

Dinheiro não aplicado fica parado no caixa, sem render.

??? success "Resolução M12"
    **Variáveis**: $A_0$, $B_0$, $B_1$, $C_1$ = valores aplicados em cada opção (o índice é o ano da
    aplicação); $S_0, S_1$ = caixa parado no ano 0 e no ano 1.

    $$\text{max } Z = 1{,}30A_0 + 1{,}15B_1 + 1{,}25C_1 + S_1 \quad \text{(dinheiro no fim do ano 2)}$$

    $$
    \begin{aligned}
    A_0 + B_0 + S_0 &= 100 \quad \text{(balanço do ano 0: o que tenho = o que aplico + o que guardo)}\\
    B_1 + C_1 + S_1 &= 1{,}15B_0 + S_0 \quad \text{(balanço do ano 1: o que volta é reaplicado)}\\
    A_0 &\le 60, \quad C_1 \le 50\\
    \text{todas} &\ge 0
    \end{aligned}
    $$

    É uma versão pequena do modelo de **fluxo de caixa** do livro (Seção 2.2.5): em cada período,
    entradas = saídas.

    **Outros fatores**: impostos e taxas de resgate, risco de cada aplicação, necessidade de caixa mínimo
    para despesas (restrição $S_t \ge$ reserva), retiradas ao longo do caminho.

    **Conferência**: $B_0=100$, $B_1=65$, $C_1=50$ (nada em A); total de R\$ 137,25 mil. Contraintuitivo:
    A rende 30%, mas prende o dinheiro por 2 anos; B + C rende $1{,}15 \times 1{,}25 \approx 1{,}44$.

---

## Exemplos do livro (Arenales) para treinar só a formulação

Os enunciados abaixo são do capítulo indicado pelo professor. Tente escrever variáveis, objetivo e
restrições antes de abrir a resposta.

**L1. Ração (Exemplo 2.1).** A ração é feita de farinha de osso, soja e peixe, e precisa ter pelo menos 30%
de proteína e 50% de cálcio. Osso: 20% proteína, 60% cálcio, \$0,56/kg. Soja: 50%, 40%, \$0,81/kg. Peixe:
40%, 40%, \$0,46/kg.

??? success "Resposta L1"
    $x_j$ = kg do ingrediente $j$ em 1 kg de ração.

    $$
    \begin{aligned}
    \text{min } & 0{,}56x_o + 0{,}81x_s + 0{,}46x_p\\
    \text{s.a. } & 0{,}2x_o + 0{,}5x_s + 0{,}4x_p \ge 0{,}3 \quad \text{(proteína)}\\
    & 0{,}6x_o + 0{,}4x_s + 0{,}4x_p \ge 0{,}5 \quad \text{(cálcio)}\\
    & x_o + x_s + x_p = 1\\
    & x_o, x_s, x_p \ge 0
    \end{aligned}
    $$

    Ótimo do livro: 50% osso e 50% peixe, custo \$0,51/kg.

**L2. Bebidas (Exemplo 2.3).** Araraquara tem 800 unidades e São José dos Campos 1.000. São Paulo,
Belo Horizonte e Rio precisam de 500, 400 e 900. Custos: de Araraquara 4, 2, 5; de S. J. Campos 11, 7, 4.

??? success "Resposta L2"
    $$
    \begin{aligned}
    \text{min } & 4x_{11} + 2x_{12} + 5x_{13} + 11x_{21} + 7x_{22} + 4x_{23}\\
    \text{s.a. } & x_{11}+x_{12}+x_{13} \le 800, \quad x_{21}+x_{22}+x_{23} \le 1.000\\
    & x_{11}+x_{21} = 500, \quad x_{12}+x_{22} = 400, \quad x_{13}+x_{23} = 900\\
    & x_{ij} \ge 0
    \end{aligned}
    $$

    Conferência no Solver: custo 6.900 (Araraquara manda 500 a SP e 300 a BH; S. J. Campos manda 100 a BH
    e 900 ao Rio).

**L3. Transbordo (Exemplo 2.5).** Mesmo problema, mas os mercados só recebem dos depósitos Campinas (3) e
Barra Mansa (4). Custos fábrica→depósito: Araraquara 1 e 3; S. J. Campos 1 e 2. Depósito→mercado: Campinas
1, 3, 3; Barra Mansa 3, 4, 1.

??? success "Resposta L3"
    Além de oferta e demanda, cada depósito ganha uma restrição de **conservação de fluxo** (tudo que
    entra, sai):

    $$
    \begin{aligned}
    \text{min } & x_{13} + 3x_{14} + x_{23} + 2x_{24} + x_{35} + 3x_{36} + 3x_{37} + 3x_{45} + 4x_{46} + x_{47}\\
    \text{s.a. } & x_{13}+x_{14} \le 800, \quad x_{23}+x_{24} \le 1.000\\
    & x_{35}+x_{45} = 500, \quad x_{36}+x_{46} = 400, \quad x_{37}+x_{47} = 900\\
    & x_{13}+x_{23} = x_{35}+x_{36}+x_{37} \quad \text{(Campinas)}\\
    & x_{14}+x_{24} = x_{45}+x_{46}+x_{47} \quad \text{(Barra Mansa)}\\
    & x_{ij} \ge 0
    \end{aligned}
    $$

**L4. Salada (texto da Seção 2.2.1).** Salada com maionese, salsa, maçã e batata ($x_1$ a $x_4$, em
gramas), com 100 g a 200 g no total e composição de 4–6% de maionese, 4–6% de salsa, 30–40% de maçã e
50–60% de batata.

??? success "Resposta L4"
    $$
    \begin{aligned}
    0{,}04(x_1+x_2+x_3+x_4) \le x_1 &\le 0{,}06(x_1+x_2+x_3+x_4)\\
    0{,}04(x_1+x_2+x_3+x_4) \le x_2 &\le 0{,}06(x_1+x_2+x_3+x_4)\\
    0{,}30(x_1+x_2+x_3+x_4) \le x_3 &\le 0{,}40(x_1+x_2+x_3+x_4)\\
    0{,}50(x_1+x_2+x_3+x_4) \le x_4 &\le 0{,}60(x_1+x_2+x_3+x_4)\\
    100 \le x_1+x_2+x_3+x_4 &\le 200
    \end{aligned}
    $$

    É o exemplo do livro de porcentagem sobre um total **variável**, a mesma armadilha da M3 e da M11.

**L5. Vigas pré-moldadas (Exemplo 2.7).** Dois tipos de viga, 3 semanas, demanda (item 1: 100, 90, 120;
item 2: 40, 50, 80), 40 h por semana (item 1 gasta 15 min e item 2 gasta 20 min), custos de produção
20, 20, 30 para os dois itens e custos de estoque 2 e 3 (item 1) e 2,5 e 3,5 (item 2). Estoques inicial e
final nulos.

??? success "Resposta L5"
    $x_{it}$ = vigas do tipo $i$ produzidas na semana $t$; $I_{it}$ = estoque no fim da semana $t$.

    $$
    \begin{aligned}
    \text{min } & 20x_{11}+20x_{12}+30x_{13}+20x_{21}+20x_{22}+30x_{23}+2I_{11}+3I_{12}+2{,}5I_{21}+3{,}5I_{22}\\
    \text{s.a. } & x_{11} - I_{11} = 100, \quad x_{12} + I_{11} - I_{12} = 90, \quad x_{13} + I_{12} = 120\\
    & x_{21} - I_{21} = 40, \quad x_{22} + I_{21} - I_{22} = 50, \quad x_{23} + I_{22} = 80\\
    & \tfrac{1}{4}x_{1t} + \tfrac{1}{3}x_{2t} \le 40 \quad (t = 1,2,3)\\
    & x_{it}, I_{it} \ge 0
    \end{aligned}
    $$

    Os minutos foram passados para horas (15 min = 1/4 h; 20 min = 1/3 h), para ficarem na mesma unidade
    das 40 h. Atenção a uma inconsistência do livro: a Tabela 2.6 traz demanda 50 para o item 2 na
    semana 2, mas as equações do livro usam 70. Aqui foi usado o valor da tabela.

    Ao rodar no Solver com os dados da tabela, o problema dá **infactível**: a demanda total pede
    $310 \cdot \tfrac14 + 170 \cdot \tfrac13 \approx 134$ h, e só há $3 \times 40 = 120$ h. Bom exemplo de
    por que conferir os totais antes de confiar no modelo.
