# OTIMIZAÇÃO DE JOINS (TEORIA DE BANCOS DE DADOS)

**Artigo:** *Size bounds and query plans for relational joins*, de Albert Atserias, Martin Grohe e Dániel Marx (FOCS 2008; versão completa arXiv 2017).

!!! note "O que o artigo não é"
    Não propõe uma técnica prática para acelerar joins — é um trabalho teórico que responde duas perguntas: quão grande pode ficar o resultado de uma sequência de joins, e que tipo de plano de execução basta para calculá-lo eficientemente.

## 1. Conceitos fundamentais

### Bounds (limites)

- **Upper bound** (limite superior): garante que o resultado nunca ultrapassa um certo valor, qualquer que seja o banco.
- **Lower bound** (limite inferior): mostra que existem bancos em que o resultado chega perto desse valor — ou seja, o upper bound não é exagerado.
- Quando os dois coincidem ("matching lower bound"), sabe-se exatamente o pior tamanho possível.

### Exemplo motivador: o "triângulo"

Query $R(a,b) \bowtie S(b,c) \bowtie T(c,a)$, com cada tabela tendo $N$ linhas.

- Limite ingênuo: $N \times N \times N = N^3$ (produto cartesiano).
- Melhor: ao juntar duas tabelas o resultado já está determinado → no máximo $N^2$.
- **Limite exato:** $N^{1.5} = \sqrt{N \cdot N \cdot N}$.

**Por que $N^{1.5}$ é atingível**: se cada atributo ($a$, $b$, $c$) assume $\sqrt{N}$ valores e cada tabela contém todos os pares possíveis, cada tabela tem $\sqrt{N} \times \sqrt{N} = N$ linhas, e o resultado tem $\sqrt{N} \times \sqrt{N} \times \sqrt{N} = N^{1.5}$ triplas.

**Por que não se passa de $N^{1.5}$ (argumento leve/pesado)**: um valor $v$ de $b$ é **leve** se aparece em no máximo $\sqrt{N}$ linhas de $S$ — para cada linha $(u,v)$ de $R$ com $v$ leve, há no máximo $\sqrt{N}$ valores de $w$ possíveis, logo no máximo $N\sqrt{N}$ respostas. Um valor $v$ é **pesado** se aparece em mais de $\sqrt{N}$ linhas de $S$ — existem no máximo $\sqrt{N}$ valores pesados (pois $S$ tem $N$ linhas); para cada linha $(w,u)$ de $T$ combinada com $v$ pesado, a tripla está determinada, logo no máximo $N\sqrt{N}$ respostas. Soma: no máximo $2N^{1.5}$ respostas.

### Relações, natural joins, equi-joins, theta-joins

- **Relação**: um conjunto de tuplas (sem duplicatas, sem ordem). $R(a,b)$ é o nome/esquema; $R(D)$ é o conteúdo num banco $D$ específico.
- **Theta-join** ($\theta$-join): combina linhas satisfazendo uma condição qualquer $\theta$ (`<`, `>`, `≠`, etc.): `SELECT * FROM R JOIN S ON R.x < S.y`.
- **Equi-join**: theta-join cuja condição só usa igualdades; colunas podem ter nomes diferentes: `SELECT * FROM Funcionario f JOIN Departamento d ON f.dept_id = d.dept_id`.
- **Natural join**: equi-join automático que iguala todas as colunas de mesmo nome e as funde numa só: `SELECT * FROM Funcionario NATURAL JOIN Departamento`.

O artigo trabalha com **natural joins** porque a estrutura da query depende só de quais atributos cada tabela compartilha — isso vira o **hipergrafo** da query. Resultados valem para equi-joins (basta renomear colunas), mas não para theta-joins, pois condições como `<` não representam "compartilhar atributo".

### O modelo formal

- **Query de join**: $Q = R_1 \bowtie R_2 \bowtie \dots \bowtie R_m$ (natural joins).
- **Hipergrafo da query** $H(Q)$: vértices = atributos; cada tabela = hiperaresta contendo seus atributos.
- $|D|$ = número total de tuplas no banco; $|Q|$ = soma das aridades das tabelas.
- **Join plan**: árvore que só usa joins binários (o que a maioria dos bancos reais faz).
- **Join-project plan**: árvore que também permite projeções intermediárias (descartar colunas e eliminar duplicatas no meio do caminho).

## 2. Pior caso — tamanho máximo do resultado

### Fractional edge cover number ($\rho^*$)

**Edge cover**: conjunto de tabelas que, juntas, cobrem todos os atributos. **Fractional edge cover**: cada tabela $R$ recebe peso $x_R \geq 0$ tal que, para cada atributo, a soma dos pesos das tabelas que o contêm é $\geq 1$. $\rho^*(Q)$ é a menor soma de pesos possível (programa linear).

No triângulo, um edge cover inteiro precisa de 2 tabelas → $N^2$. Com pesos fracionários $\tfrac{1}{2}$ em cada tabela, o total é $3 \times \tfrac{1}{2} = \tfrac{3}{2}$ → $\rho^* = \tfrac{3}{2}$.

### Limite superior — AGM bound

Para qualquer fractional edge cover e qualquer banco $D$:

$$|Q(D)| \le \prod_R |R(D)|^{x_R} \le |D|^{\rho^*(Q)}$$

A prova usa o **Lema de Shearer** (teoria da informação): a entropia de uma tupla do resultado é limitada pela soma das entropias das "visões" de cada tabela, ponderadas pelos pesos que cobrem cada atributo. Esse limite já era conhecido (Grohe e Marx, 2006) e hoje é chamado **AGM bound** (iniciais dos autores).

### Limite inferior — contribuição nova do artigo

O limite é **justo**: para toda query existem bancos arbitrariamente grandes que o atingem. A prova usa dualidade de programação linear — o dual atribui um peso $y_a$ a cada atributo; o banco construído dá a cada atributo exatamente $N^{y_a}$ valores possíveis, colocando em cada tabela todas as combinações. No triângulo: $\sqrt{N}$ valores por atributo → cada tabela com $N$ linhas → resultado $N^{1.5}$.

### Caracterização completa

Para uma classe de queries, as afirmações abaixo são equivalentes: (1) resultados têm tamanho polinomial; (2) queries podem ser avaliadas em tempo polinomial; (3) podem ser avaliadas em tempo polinomial por um join-project plan explícito; (4) $\rho^*$ é limitado. Não é óbvio que (1) implica (2) — saber que o resultado é pequeno não garante a priori um jeito rápido de calculá-lo; o artigo prova que esse jeito existe.

## 3. Pior caso — planos de execução

### Join-project plan quase ótimo

Ordene os atributos $a_1, \dots, a_n$. O plano constrói o resultado atributo por atributo: a cada passo $i$, calcula a projeção do resultado final nos atributos $\{a_1,\dots,a_i\}$, via join do resultado anterior com as projeções de cada tabela nesses atributos. Cada intermediário é, ele próprio, resultado de uma query com $\rho^* \le \rho^*(Q)$, logo nenhum intermediário passa de $|D|^{\rho^*}$. Tempo total: $O(|Q|^2 \cdot |D|^{\rho^*+1})$ — ótimo a menos de fator polinomial, e fácil de calcular.

### Planos só com joins podem ser muito piores

Existe uma família de queries com $\rho^* \le 2$ cujo resultado final é até menor que o banco, mas **qualquer** join plan (sem projeções) tem algum intermediário de tamanho pelo menos $|D|^{(1/5)\log|Q|}$. Intuição: qualquer árvore de joins binários precisa, em algum ponto, juntar "metade" das tabelas — essa metade sozinha restringe pouco e gera explosão de tuplas, só podada depois pelas outras tabelas. A diferença é **superpolinomial**: tempo cúbico com projeções vs. $|D|^{\Omega(\log|Q|)}$ sem elas, mesmo que as projeções sejam irrelevantes para a resposta final.

### Diferença no máximo logarítmica no expoente

Sempre existe join plan com tempo $O(|Q| \cdot |D|^{2\rho^* \cdot \log|Q|})$: juntar primeiro um edge cover inteiro (tamanho $\le \sim \rho^*\log n$ pelo integrality gap). O resultado anterior é então essencialmente justo. Detalhe: **encontrar** o edge cover mínimo é NP-difícil (já o join-project plan ótimo é fácil de achar).

## 4. Com tamanhos de tabela conhecidos

Na prática, o otimizador conhece o tamanho $N_R$ de cada tabela. O programa linear passa a minimizar $\sum x_R \log N_R$.

- O limite superior $\prod N_R^{x_R}$ continua válido; o inferior só é garantido a menos de fator $2^{-n}$ ($n$ = número de atributos).
- Existe família de queries em que o limite superior dá $\sim 2^n$ mas o resultado real nunca passa de $2^{\varepsilon n}$ (via dimensão VC e Lema de Sauer).
- **Inaproximabilidade**: nenhum algoritmo polinomial estima o tamanho máximo com erro melhor que $2^{n^{1-\varepsilon}}$, a menos que NP = ZPP (redução do problema do conjunto independente máximo em grafos).

!!! tip "Mensagem central"
    Estimar cardinalidade de joins é intrinsecamente difícil — não é falha do método de fractional covers, é dificuldade do próprio problema.

## 5. Caso médio — bancos aleatórios

Modelo: cada tupla possível entra em cada tabela $R$ com probabilidade $p_R$, independentemente, sobre domínio de $N$ valores (análogo ao grafo aleatório de Erdős–Rényi).

$$\mathbb{E}[X] = N^n \cdot \prod_R p_R$$

Cada tabela recebe peso $w_R = \log(1/p_R)$ ("quanto a tabela restringe"). A **densidade** de uma query é $\delta = \tfrac{1}{n}\sum_R w_R$ (média por atributo), e a **densidade máxima** $\bar\delta$ é a maior $\delta$ entre todas as subqueries induzidas.

- $\bar\delta$ bem abaixo de $\log N$: o resultado se concentra em torno do valor esperado (via desigualdade polinomial de Kim–Vu, com probabilidade $1 - N^{-d}$).
- $\bar\delta$ bem acima de $\log N$: existe subquery com menos de uma solução esperada → resultado vazio quase certamente (desigualdade de Markov).
- A densidade máxima pode ser calculada em tempo polinomial via fluxo máximo / corte mínimo.

## 6. Caso médio — planos de execução

**Resultado técnico principal**: no modelo aleatório, **todo** join-project plan pode ser transformado num join plan (sem projeções) em que o tamanho esperado de cada subplano aumenta no máximo por um fator constante, independente do tamanho do banco. A vantagem das projeções que aparece no pior caso **desaparece** no caso médio.

A transformação remove uma projeção por vez (a mais baixa da árvore), escolhendo $A^* \supseteq A$ que minimiza uma função submodular — pela submodularidade existe um minimizador único e máximo. Dois passos: remover tabelas cujos atributos não cabem em $A^*$ (adiciona poucas tuplas), e trocar a projeção antiga por $A^*$, tornando-a redundante (cada tupla tem poucas extensões em média). Ferramentas usadas: desigualdade FKG, posto de funções indicadoras, comparações de probabilidades condicionais.

## 7. Conclusões do artigo

- **Pior caso**: $\rho^*$ caracteriza exatamente o tamanho do resultado; planos com projeções podem ser superpolinomialmente melhores que planos só com joins.
- **Caso médio**: a densidade máxima governa o comportamento; planos só com joins são quase tão bons quanto os com projeções.
- **Questões em aberto**: incorporar dependências funcionais de forma completa; provar uma versão do resultado do caso médio válida com alta probabilidade (não só em esperança).

## 8. Insights práticos para engenharia de dados

### Fan-out: o problema nº 1

Juntar duas tabelas por chave não-única em nenhum dos lados — nenhuma tabela "cobre" o atributo com peso 1 sozinha — significa que o resultado pode chegar ao produto das multiplicidades. O efeito mais traiçoeiro é o **resultado errado** (somas/contagens infladas por duplicação), não só performance.

Prática: conhecer o grão de cada tabela antes do join; teste de unicidade (dbt):

```yaml
columns:
  - name: customer_id
    tests: [unique, not_null]
```

Em join fato → dimensão por FK (caso $\rho^* = 1$), o número de linhas deve igualar o da tabela fato.

### Calcular o tamanho do join antes de executar

```sql
WITH a AS (SELECT k, COUNT(*) AS na FROM tabela_a GROUP BY k),
     b AS (SELECT k, COUNT(*) AS nb FROM tabela_b GROUP BY k)
SELECT SUM(na * nb) AS linhas_do_join,
       MAX(na * nb) AS maior_chave
FROM a JOIN b USING (k);
```

Para 3+ tabelas com ciclo, usar o AGM bound como teto (ex.: $\sqrt{|R|\cdot|S|\cdot|T|}$ no triângulo) para dimensionar cluster ou decidir reestruturar a query.

### Reduzir cedo — análogo das projeções intermediárias

Explica por que um stage do Spark pode ter bilhões de linhas de saída mesmo com resultado final pequeno. Remédio: eliminar colunas e **deduplicar/agregar** antes do próximo join (selecionar menos colunas sozinho não reduz linhas).

```sql
WITH eventos_por_usuario AS (
  SELECT user_id, COUNT(*) AS n_eventos
  FROM eventos
  GROUP BY user_id
)
SELECT ...
FROM eventos_por_usuario e
JOIN assinaturas s USING (user_id);
```

Para filtrar sem trazer colunas, usar semi-join: `SELECT * FROM pedidos p WHERE EXISTS (SELECT 1 FROM clientes_ativos c WHERE c.id = p.cliente_id)`, ou no Spark `df.join(outro, "chave", "left_semi")` (nunca multiplica linhas). Sinal de alerta na Spark UI/plano de execução: nó intermediário muito maior que a saída final.

### Data skew = argumento "leve/pesado" do paper

- `spark.sql.adaptive.skewJoin.enabled=true` (Spark AQE).
- Separar chaves pesadas (identificadas pela query acima) e processá-las separadamente (ex.: broadcast), unindo depois com o caminho das leves.
- **Salting**: sufixo aleatório na chave pesada para espalhar entre partições.
- Filtrar nulos/defaults antes do join (causa clássica de skew acidental).

### Não confiar nas estimativas do otimizador

A inaproximabilidade prova que estimar tamanho de joins é intrinsecamente difícil, mesmo sabendo o tamanho de cada tabela. Quebrar queries gigantes em modelos intermediários materializados; manter AQE ativo; comparar estimado vs. real (`EXPLAIN ANALYZE`, BigQuery execution details, Snowflake Query Profile).

### Declarar chaves (mesmo não impostas)

Restrições (chaves, dependências funcionais) reduzem o pior caso teórico. Em warehouses (BigQuery, Snowflake), PK/FK geralmente não são impostas mas podem ser declaradas e usadas pelo otimizador — garantir com testes (dbt `unique`/`relationships`, contracts, Great Expectations).

### Onde aparecem joins cíclicos em engenharia de dados

Identity resolution / entity matching (usuários, dispositivos, e-mails, IPs); detecção de fraude (anéis de contas compartilhando cartão/endereço/dispositivo); recomendações "quem comprou X também comprou Y" (self-joins muitos-para-muitos). Estratégias: filtrar agressivamente antes; limitar grau de cada nó (ignorar hubs); ferramentas de grafo (GraphFrames, bancos de grafo).

### Checklist para revisar um pipeline com joins

1. Qual o grão de cada tabela e a chave é única em pelo menos um lado?
2. Existe teste garantindo essa unicidade?
3. O número de linhas pós-join bate com o esperado?
4. Há stage intermediário muito maior que a saída final? Dá para agregar/deduplicar antes?
5. Algum join só serve para filtrar? Trocar por semi-join.
6. Qual a distribuição das chaves (máximo de linhas por chave)? Nulos/defaults concentrando linhas?
7. Os joins formam ciclo? Se sim, calcular o AGM bound antes de produção.

## 9. Conexão com sistemas reais

O AGM bound motivou os chamados **worst-case optimal join algorithms** (NPRR, Leapfrog Triejoin, Generic Join), que processam a query atributo por atributo (mesma ideia do plano ótimo) em vez de tabela por tabela. Usados em sistemas como LogicBlox/RelationalAI, no banco de grafos Kùzu, e de forma adaptativa no Umbra — relevante para quem lida com consultas em grafos ou muitos joins cíclicos.
