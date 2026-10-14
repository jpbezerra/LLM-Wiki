# FUNDAMENTOS DE TESTES DE SOFTWARE

---

Disciplina **CIN0168 — Fundamentos de Teste de Software**, do Centro de Informática da UFPE, ministrada pela **Prof.ª Paola Accioly** (prga@cin.ufpe.br), edição 2026.2, com parte do material baseado nos slides de Marcelo d'Amorim, Breno Miranda e Leopoldo Teixeira. O conteúdo desta página segue a ordem cronológica das aulas, conforme o cronograma oficial da disciplina.

!!! note "Dados da disciplina"
    - **Avaliação**: 10% APS, 30% prova escrita, 60% projeto.
    - **Aviso em destaque dos slides**: a entrega do projeto é obrigatória para aprovação — a não entrega resulta em reprovação automática, independentemente da média nas demais avaliações.
    - **Google Classroom**: código da turma `yofr5aoo`.
    - **Bibliografia principal**:
        - ZELLER, Andreas et al. *Generating Software Tests — Breaking Software for Fun and Profit*. Disponível online em [fuzzingbook.org](https://www.fuzzingbook.org).
        - PEZZÈ, Mauro; YOUNG, Michal. *Software Testing and Analysis: Process, Principles, and Techniques*. Wiley, 2008.
        - ZELLER, Andreas. *Why Programs Fail?*. 2ª ed. Morgan Kaufmann, 2009.
        - MYERS, Glenford. *Software Testing*. 2ª ed. Wiley, 2004.
    - **Material "em destaque" apontado pela disciplina**: [fuzzingbook.org](https://www.fuzzingbook.org) (fuzzing) e [mlip-cmu.github.io/book](https://mlip-cmu.github.io/book/) (IA aplicada à engenharia de software/testes).

### Cronograma e conteúdo coberto

| Data | Tópico | Cobertura nesta página |
|---|---|---|
| 12/8 | Apresentação do curso e introdução a Teste de Software | ✅ [Introdução](#introducao-a-teste-de-software) |
| 17/8 | Falta vs. falha, Teste vs. depuração, tipos de teste | ✅ embutido na [Introdução](#conceitos-fundamentais-erro-falta-e-falha) (sem slide próprio enviado) |
| 19/8 | Técnicas funcionais/estruturais | ✅ [Técnicas de teste](#tecnicas-de-teste) |
| 24/8 | Critérios de adequação | ✅ [Critérios de adequação](#criterios-de-adequacao-de-teste) |
| 26/8 | Teste de mutação | ✅ [Teste de mutação](#teste-de-mutacao) |
| 31/8 | Teste de regressão | ✅ [Teste de regressão](#teste-de-regressao) |
| 2/9, 9/9 | APS — Framework de testes | projeto/APS, sem material de aula |
| 7/9 | Feriado (Independência do Brasil) | — |
| 14/9, 21/9 | Aula não ocorrida (ausência da professora) | — |
| 16/9 | Teste Flaky | ✅ [Testes flaky](#testes-flaky) |
| 23/9 | Lançamento do projeto | projeto, sem material de aula |
| 28/9 | Teste Combinatorial | ✅ [Teste combinatorial](#teste-combinatorial) |
| 30/9 | Fuzzing | ✅ [Fuzzing](#fuzzing) |
| 5/10 | TDD/BDD | ✅ [TDD e BDD](#tdd-e-bdd) |
| 7/10 | Teste de Sistemas Baseados em IA | ✅ [Teste de sistemas de IA](#teste-de-sistemas-baseados-em-ia) |
| 12/10 | Feriado (Nossa Senhora Aparecida) | — |
| 14/10 | IA para Testes | ✅ [IA para testes](#ia-para-testes) |

!!! warning "Sobre a numeração dos arquivos de slide"
    Os nomes dos arquivos originais (`1_-_Introduction`, `3_-_Test_techniques`, `4_-_Test_adequacy` etc.) não correspondem exatamente à ordem cronológica das aulas no calendário oficial — por isso esta página segue o cronograma, não a numeração dos arquivos. Não há material de slide enviado especificamente para o tópico de 17/8 ("Falta vs. falha, Teste vs. depuração"); os conceitos desse tópico já aparecem cobertos no material introdutório (12/8) e estão descritos na seção correspondente abaixo.

## Introdução a Teste de Software

### Por que testar?

Bugs têm causas variadas — erros de lógica, tratamento incorreto de dados, *race conditions*, integrações mal definidas, requisitos ambíguos, erros humanos (copy-paste sem adaptação), diferenças de ambiente/configuração, regressões por refatoração, dependências externas que mudam. Diante disso, três linhas de defesa são possíveis: *code review*/*peer review*, análise estática e **teste** — o foco da disciplina.

!!! quote "Citações centrais da aula de abertura"
    **Michael Feathers**: "Code without tests is bad code."

    **Edsger Dijkstra**: "Program testing can be used to show the presence of bugs, but never to show their absence!"

**Definição formal (SWEBOK 3.0, 2014)**: teste de software é a verificação **dinâmica** de que um programa fornece comportamentos **esperados** em um conjunto **finito** de casos de teste, adequadamente **selecionados** a partir do domínio de execução usualmente infinito.

Quando o software falha, o custo pode ser apenas um incômodo, pode custar tempo, dinheiro — ou vidas (os slides citam como leitura complementar o caso do Boeing 737 MAX, a explosão do foguete Ariane 5 e as *race conditions* do Therac-25). Mesmo sendo caro — tanto o esforço humano de escrever casos de teste quanto o custo computacional de executá-los —, o teste é amplamente praticado na indústria.

!!! example "Um bug real que durou 9 anos escondido em Java"
    No algoritmo de busca binária abaixo, a linha `int mid = (low + high) / 2;` pode causar *overflow* de inteiro quando `low + high` excede o limite do tipo `int`, produzindo um valor negativo que, dividido por 2, permanece negativo — um índice de array inválido.

    ```java
    public static int binarySearch(int[] a, int key) {
        int low = 0;
        int high = a.length - 1;
        while (low <= high) {
            int mid = (low + high) / 2;
            int midVal = a[mid];
            if (midVal < key) low = mid + 1;
            else if (midVal > key) high = mid - 1;
            else return mid;
        }
        return -(low + 1);
    }
    ```

    O bug ficou escondido por quase 9 anos na biblioteca padrão do Java ([fonte](https://dev.to/matheusgomes062/a-bug-was-found-in-java-after-almost-9-years-of-hiding-2d4k)) — ilustrando como a escolha dos dados de teste é determinante: só arrays suficientemente grandes revelam o problema.

### Conceitos fundamentais: erro, falta e falha

A terminologia (seguindo IEEE/SWEBOK) distingue três conceitos que frequentemente se confundem:

- **Erro (*error*/*bug*)**: um engano cometido pelo desenvolvedor — uma condição `if`/`else` errada, um cálculo mal feito, um mal-entendido de requisito.
- **Falta (*fault*)**: o ponto no código onde o erro se manifesta como uma diferença entre o que o programa faz e o que a especificação exige. Um erro pode gerar zero ou mais faults.
- **Falha (*failure*)**: um resultado observável que diverge do resultado correto especificado. Uma falta no código pode gerar zero ou mais failures, dependendo da entrada e do caminho de execução percorrido.

!!! example "Erro, falta e falha no mesmo trecho de código"
    ```python
    def sort(self, list):
        i = 0
        while i <= len(list):   # erro: deveria ser "<", não "<="
            ...list[i]...       # falta: acesso fora dos limites
    ```
    A execução com uma lista cujo tamanho expõe o índice inválido produz a falha observável `IndexError: list index out of range`.

O **modelo RIP** (*Reachability, Infection, Propagation* — Voas, "PIE: A Dynamic Failure-Based Technique", IEEE TSE, 1992) formaliza as três condições necessárias para que um teste revele uma falta:

1. **Reachability (alcance)**: o caso de teste precisa executar a linha/componente com a falta.
2. **Infection (infecção)**: a execução do código com falta precisa corromper o estado interno do programa.
3. **Propagation (propagação)**: o estado corrompido precisa se propagar até afetar a saída observável.

O **foco do teste** está em observar a *failure*; o **foco da depuração** (*debugging*) está em rastrear de volta até o *bug*/erro original — um processo que os slides descrevem como **depuração científica**: observar a falha → formular hipótese → prever comportamento → fazer experimento → observar → repetir até a hipótese ser consistente, então corrigir.

**Teste vs. depuração**, portanto, são atividades complementares mas distintas: o teste existe para **detectar** a presença de falhas (nunca prova a ausência — Dijkstra); a depuração existe para **localizar e corrigir** a falta que as causou.

### Anatomia de um caso de teste

Um caso de teste automatizado segue tipicamente o padrão **AAA** (*Arrange–Act–Assert*):

```java
@Test
public void testEmptyStack() {
    Stack<Integer> stack = new Stack<Integer>();  // Arrange (fixture)
    boolean empty = stack.isEmpty();               // Act (operation)
    assertTrue(empty);                              // Assert (oracle)
}
```

O **oráculo** (*oracle*) é o componente que compara o resultado observado com o esperado — definido pela IEEE como "um conjunto de entradas de teste, condições de execução e resultados esperados desenvolvidos para um objetivo específico". Frameworks de teste (*xUnit*) existem para praticamente toda linguagem: JUnit (Java), `unittest`/`pytest` (Python), RSpec (Ruby), Jest (JavaScript), CUnit (C), CppUnit (C++), NUnit (C#).

A automação de testes reduz o tempo de execução e melhora a reprodutibilidade, mas tem custos: o próprio código de teste precisa ser mantido, e nem todo tipo de teste se beneficia de automação (teste de usabilidade, por exemplo, costuma ser manual/exploratório).

### Caracterização do teste: alvo, visibilidade e objetivo

O teste pode ser caracterizado em três eixos independentes:

**Por alvo (granularidade)** — a pirâmide de testes clássica:

| Nível | Granularidade | Quantidade | Velocidade | Custo |
|---|---|---|---|---|
| Sistema (*system*) | Maior | Menor | Mais lentos | Maior |
| Integração | Intermediária | Intermediária | Intermediária | Intermediário |
| Unidade (*unit*) | Menor | Maior | Mais rápidos | Menor |

- **Teste de unidade**: verifica elementos de software isoladamente, tipicamente com acesso ao código e ferramentas de depuração.
- **Teste de integração**: verifica as interações entre componentes do sistema.
- **Teste de sistema**: testa o comportamento do sistema inteiro, adequado para avaliar requisitos não funcionais (segurança, desempenho, confiabilidade).

**Por visibilidade (acesso ao código)**:

- **Caixa-branca (*white-box*)**: os testes são projetados com conhecimento da estrutura interna/implementação.
- **Caixa-preta (*black-box*)**: os testes dependem apenas do comportamento observável (entrada/saída), sem olhar a implementação.

**Por objetivo** — alguns exemplos definidos nos slides:

- **Aceitação**: verifica se o sistema satisfaz os critérios de aceitação do cliente.
- **Alpha/Beta**: testes com usuários reais antes do lançamento (grupo pequeno selecionado vs. grupo maior representativo).
- **Desempenho (*performance*)**: verifica requisitos de desempenho especificados (ex.: tempo de resposta).
- **Estresse (*stress*)**: exercita o software na carga máxima de projeto e além dela, para determinar limites de comportamento.
- **Segurança**: verifica confidencialidade, integridade e disponibilidade de sistema e dados.
- **Interface**: verifica a correta troca de dados/controle entre componentes de interface.
- **Usabilidade**: avalia a facilidade de aprendizado e uso do software por usuários finais.
- **Regressão**: reteste seletivo para verificar que modificações não introduziram efeitos colaterais indesejados (ver seção dedicada [Teste de regressão](#teste-de-regressao)).

!!! tip "Qualidade interna vs. externa — e por que não existe bala de prata"
    **Qualidade interna** refere-se ao artefato de código (modularidade, coesão, acoplamento, legibilidade). **Qualidade externa** refere-se a aspectos observáveis de fora (segurança, desempenho, funcionalidade). O teste de software foca na **qualidade externa** — mas não é a única peça: qualidade interna, escolha de linguagem/ferramentas, processo de desenvolvimento e uma equipe treinada e motivada são igualmente necessários.

### Quando começar a escrever os testes?

Duas estratégias, sem uma resposta universalmente correta — a decisão varia com o projeto e a equipe:

- **Top-down**: assim que os requisitos são conhecidos (abordagem de TDD/BDD — ver [TDD e BDD](#tdd-e-bdd)); desvantagem: exige código auxiliar (mocks, stubs) antes de a implementação existir.
- **Bottom-up**: assim que o código é desenvolvido, dos testes de unidade aos de integração e sistema.

Duas observações destacadas nos slides: os testes devem refletir os requisitos (funcionais ou não) mesmo que implementados depois do código; e não é necessário esperar a última função do sistema estar pronta para começar testes de integração/sistema — bibliotecas de *mock* viabilizam isso antes.

## Técnicas de teste

Seguindo a taxonomia do **SWEBOK 3.0 (2014)**, as técnicas de teste são classificadas de acordo com a origem da geração dos casos de teste: a intuição/experiência do testador, a especificação, a estrutura do código, as faltas reais ou imaginadas a serem descobertas, ou o uso previsto do sistema.

A distinção mais básica é entre:

- **Caixa-branca**: os testes exploram informação sobre como o software foi projetado/codificado.
- **Caixa-preta**: os casos de teste dependem apenas do comportamento de entrada/saída.

### Técnicas baseadas em intuição e experiência

- **Ad hoc**: testes informais, sem roteiro estruturado, guiados pela intuição do testador (análogo ao *monkey testing* — entradas aleatórias "de macaco no teclado").
- **Teste exploratório**: aprendizado, projeto e execução dos testes ocorrem simultaneamente, guiados por quem testa — como uma investigação.

### Técnicas baseadas no domínio de entrada

**Particionamento em classes de equivalência (*equivalence partitioning*)**: divide o domínio de entrada em subconjuntos que, por hipótese, se comportam de forma similar.

!!! example "Classes de equivalência — campo idade"
    Campo que aceita idades de 18 a 56:

    | Inválido | Válido | Inválido |
    |---|---|---|
    | ≤17 | 18–56 | ≥57 |

**Análise de valor-limite (*boundary-value analysis*)**: testa valores exatamente nas fronteiras e imediatamente antes/depois delas, já que erros de programação (operadores de comparação errados, *off-by-one*) se concentram ali.

!!! example "Valor-limite — função raiz quadrada"
    Domínio válido: números reais ≥ 0.

    | Número | Resultado esperado |
    |---|---|
    | -5 | Não existe |
    | -1 | Não existe |
    | 0 | 0 |
    | 1 | 1 |
    | 4 | 2 |

**Teste de pares (*pairwise testing*)**: garante que todas as combinações de pares de valores de parâmetros sejam testadas ao menos uma vez — reduzindo drasticamente o número de casos de teste necessário (tratado em profundidade em [Teste combinatorial](#teste-combinatorial)).

!!! example "Pairwise — navegador × sistema operacional × login"
    3 navegadores × 3 sistemas operacionais × 2 métodos de login = 18 combinações possíveis, mas apenas **9 casos de teste** cobrem todos os pares:

    | Teste | Navegador | SO | Login |
    |---|---|---|---|
    | 1 | Chrome | Windows | Senha |
    | 2 | Chrome | macOS | Biometria |
    | 3 | Chrome | Linux | Senha |
    | 4 | Firefox | Windows | Biometria |
    | 5 | Firefox | macOS | Senha |
    | 6 | Firefox | Linux | Biometria |
    | 7 | Edge | Windows | Senha |
    | 8 | Edge | macOS | Biometria |
    | 9 | Edge | Linux | Senha |

**Teste aleatório (*random testing*)**: geração de entradas puramente aleatórias — citado como quarta técnica da família, aprofundado na seção de [fuzzing](#fuzzing).

### Técnicas baseadas no código

**Critérios de fluxo de controle (*control-flow-based*)**, usando o grafo de fluxo de controle de um programa (nós = blocos sequenciais, ramos = transferências de controle):

- **Cobertura de instruções (nós)**: cada instrução deve ser executada ao menos uma vez.
- **Cobertura de ramos**: cada ramo de decisão (`if`/`else`) deve ser percorrido ao menos uma vez.
- **Cobertura de condições**: cada subcondição dentro de uma expressão composta deve ser avaliada como verdadeira e falsa.

!!! example "Cobertura de instruções vs. ramos"
    ```
    1. if (x>0 and y>100)
    2.     x = x+y+1;
    3. else x = x+y-1;
    4. write x,y
    ```
    | x | y | Ramos percorridos |
    |---|---|---|
    | 1 | 101 | {(1,1A),(1A,2),(2,4)} |
    | 1 | 99 | {(1,1A),(1A,3),(2,4)} |
    | -1 | 100 | {(1,3),(3,4)} |

**Critérios de fluxo de dados (*data-flow-based*)**: rastreiam onde variáveis são **definidas** (`def`) e **usadas** (*c-use* = uso computacional, *p-use* = uso em predicado), exigindo que um teste cubra o caminho entre a definição de uma variável e seu uso. Técnicas comuns: *all-definitions*, *all-c-uses*, *all-p-uses*, *all-uses*, *all-DU-paths*.

### Técnicas baseadas em falhas (*fault-based*)

- **Error guessing**: casos de teste criados para antecipar as falhas mais plausíveis, com base no histórico de bugs de projetos anteriores e na experiência do testador.
- **Teste de mutação**: ver seção dedicada [Teste de mutação](#teste-de-mutacao).

### Técnicas baseadas no uso (*usage-based*)

**Perfil operacional (*operational profile*)**: prioriza casos de teste de acordo com a frequência real de uso de cada operação, por tipo de usuário — a percepção de confiabilidade do sistema varia conforme o perfil de quem o usa (um autor que só navega publicações pode achar o sistema perfeito, enquanto um administrador que faz backups frequentes pode perceber mais falhas).

### Técnicas baseadas em modelo

**Tabelas de decisão**: mapeiam combinações de condições para as ações correspondentes — útil para lógica de negócio com múltiplas regras combinadas (ex.: um fluxograma de diagnóstico "a impressora não imprime").

### Técnicas segundo a natureza da aplicação

Categorias de software que exigem técnicas específicas: orientado a objetos, baseado em componentes, *web*, programas concorrentes, baseado em protocolo, sistemas de tempo real, sistemas críticos de segurança (*safety-critical*), orientado a serviços, código aberto, sistemas embarcados.

!!! quote "Mensagem de encerramento do material sobre técnicas"
    "Each technique has its focus, advantages, and limitations, and it is the role of the test engineer to know how to select and combine these strategies according to the context of the project. More than memorizing definitions, what truly matters is developing critical awareness to apply the right test, at the right time, with the right purpose."

## Critérios de adequação de teste

Uma suíte com 120 testes, todos passando, com 85% de cobertura de código — isso significa que o software está bem testado? Não necessariamente: **cobertura é necessária, mas não suficiente** para garantir ausência de bugs.

!!! example "100% de cobertura de instruções não é garantia de correção"
    ```java
    y = 10 / x;
    ```
    Com `x = 5`, esse código atinge 100% de cobertura de instruções — mas `x = 0` causa um *crash* em tempo de execução que a cobertura de instruções não detecta.

**Critério de adequação de teste**: define requisitos de teste e mede quantos deles foram cobertos pela suíte — a suposição subjacente é que cobertura mais alta aumenta a chance de detectar falhas (mas não a garante). A pergunta "quando parar de testar?" não tem resposta cientificamente justificada apenas por "quando o tempo acaba" ou "quando o produto é lançado" — os critérios de adequação existem para dar uma resposta mais fundamentada.

Duas grandes famílias de critérios:

**Critérios funcionais** (baseados na especificação, independentes da estrutura interna):

- **Cobertura de requisitos**: mede quantos requisitos do sistema são exercitados pela suíte.
- **Cobertura de classes de equivalência**: entradas divididas em classes esperadas comportar-se de forma similar.
- **Cobertura de valor-limite**: valores nas fronteiras dos domínios de entrada.
- **Cobertura de cenários**: cada cenário relevante do sistema deve ser coberto por ao menos um teste.

**Critérios estruturais** (baseados na estrutura do programa, dependentes da implementação):

- **Cobertura de instruções, ramos e caminhos** — como descrito em [Técnicas baseadas no código](#tecnicas-baseadas-no-codigo).
- **Cobertura de fluxo de dados** — idem.
- **MC/DC (*Modified Condition/Decision Coverage*)**: critério mais rigoroso, exige que cada condição dentro de uma decisão composta tenha, isoladamente, afetado o resultado da decisão ao menos uma vez — usando apenas **n+1** testes em vez dos 2ⁿ necessários para testar todas as combinações de n condições booleanas.

!!! example "MC/DC — (a && (b || c)) com apenas 4 testes"
    Em vez de testar as 8 combinações possíveis de `a`, `b`, `c`, o MC/DC identifica pares de linhas que isolam o efeito de cada variável (flipando uma condição e mantendo as outras fixas), chegando a uma suíte reduzida: **Teste Suite = {2, 3, 4, 6}** — muito menor que 2ⁿ, mas ainda garantindo que cada condição influencia o resultado de forma independente.

Os critérios estruturais e funcionais se somam a um terceiro tipo — os **critérios baseados em falhas** (*fault-based*), fundamento do teste de mutação, abordado na próxima seção.

## Teste de mutação

Se todos os testes passam, isso significa que você confia 100% no seu código? Considere:

```java
boolean ehPositivo(int x) { return x > 0; }   // assertTrue(ehPositivo(10)) passa
boolean ehPositivo(int x) { return x >= 0; }  // assertTrue(ehPositivo(10)) também passa!
```

O mesmo teste passa em duas implementações sutilmente diferentes — isso mostra que **a suíte de testes pode não ser sensível o bastante** para distinguir um programa correto de uma variação dele com uma falta.

**Teste de mutação**: falhas sintáticas são inseridas no código através de **operadores de mutação** (*mutation operators*), gerando **mutantes** — clones do programa original com uma ou mais faltas inseridas propositalmente. A suíte de testes é executada contra cada mutante:

- Se **ao menos um teste falhar** no mutante, o mutante é considerado **morto** (*killed*).
- Se **todos os testes passarem**, o mutante está **vivo** (*alive*) — sinal de que a suíte não é sensível a essa mutação.

!!! example "Operador de mutação — troca de operador relacional"
    ```java
    if(a[i] < threshold){...}   // SUT original
    if(a[i] > threshold){...}   // mutante gerado pelo operador de mutação
    ```

Categorias de operadores de mutação cobertas no material: modificações de operando (troca de constante/variável/referência de array), modificações de expressão (operadores aritméticos, condicionais, relacionais, de deslocamento, de atribuição abreviada), e modificações de instrução (remoção de instrução, troca de rótulo de `case`, deslocamento de chaves de bloco).

### As duas hipóteses do teste de mutação

Para que mutantes sintéticos sejam representativos de falhas reais, duas hipóteses precisam se sustentar:

- **Hipótese do Programador Competente**: um programa com falta difere de um programa correto apenas por uma pequena alteração textual — o SUT está "próximo" de correto.
- **Hipótese do Efeito de Acoplamento (*Coupling Effect*)**: a maioria das faltas são erros sintáticos pequenos; faltas complexas são combinações de pequenas mudanças; um teste capaz de expor uma pequena mudança também tende a detectar uma mudança mais complexa.

### Medindo adequação com mutação

$$\text{Mutation Coverage} = \frac{\text{mutantes mortos}}{\text{total de mutantes}} \qquad \text{Tests Strength} = \frac{\text{mutantes executados}}{\text{total de mutantes}}$$

Na prática, o teste de mutação é **caro** — exige executar toda a suíte contra cada mutante gerado, e tipicamente muitos mutantes são gerados (um operador por mutante). Pesquisa ativa na área inclui seleção de mutantes (eliminando mutantes equivalentes e redundantes), mutantes de ordem superior, e o uso de mutação para avaliar testes gerados por IA — um achado citado nos slides é que "IA gera testes com alta cobertura, porém matando poucos mutantes", reforçando que cobertura de linha e qualidade de teste não são a mesma coisa (tema retomado em [IA para testes](#ia-para-testes)).

A ferramenta [PITest](https://pitest.org/) foi usada como demonstração prática de teste de mutação em Java.

## Teste de regressão

Toda vez que o software é modificado, surge a pergunta: as mudanças quebraram algo que já funcionava? Reexecutar toda a suíte de testes a cada modificação parece a solução óbvia — mas na prática é quase sempre inviável: estudos citam suítes de 30.000 casos de teste consumindo mais de 1.000 horas-máquina, e o Google relata que, por dia, realiza 800 mil builds e 150 milhões de execuções de teste em mais de 13 mil projetos de código.

O dilema do **teste de regressão**: reexecutar tudo é caro; não reexecutar tudo arrisca deixar passar faltas de regressão não detectadas. O desafio central é **reduzir o esforço de reteste sem comprometer sua efetividade**.

Três dimensões de técnicas se destacam:

**Redução**: elimina definitivamente testes redundantes ou desatualizados da suíte. Risco: remover testes que poderiam detectar problemas futuros, exigindo análise criteriosa para evitar lacunas de cobertura. Técnicas principais: eliminação de testes redundantes, agrupamento de testes, cobertura de testes, particionamento de equivalência, priorização de requisitos.

**Seleção**: seleciona dinamicamente, para uma execução específica, os testes que exercitam as áreas do código modificadas/impactadas, ou que historicamente revelam mais falhas. Risco: pode ser difícil rastrear com precisão o impacto de uma mudança, e testes ignorados podem deixar passar bugs não aparentes de imediato. Técnicas principais: impacto das mudanças, cobertura de código crítico, histórico de falhas, uso do software.

**Priorização**: determina a ordem ideal de execução dos casos de teste, com o objetivo de detectar falhas o mais cedo possível, minimizando custo/tempo de execução. Critérios: criticidade da funcionalidade, impacto das mudanças, probabilidade de falha (dados históricos), frequência de uso, risco ao negócio, cobertura de código, tempo de execução, e algoritmos automáticos baseados em heurísticas.

!!! example "Avaliando a priorização com APFD"
    *Average Percentage of Faults Detected* (APFD) mede quão rápido uma ordenação de testes detecta faltas. Com a mesma suíte (A, B, C, D, E) cobrindo 10 faltas:

    - Ordem **A-B-C-D-E** → **APFD = 30%**
    - Ordem **C-E-B-A-D** → **APFD = 64%**

    A mesma suíte, reordenada, detecta faltas muito mais rapidamente — ilustrando o valor da priorização.

### Problemas de pesquisa em aberto

Duas limitações práticas das técnicas propostas na literatura, segundo o material:

1. **Eficiência/escalabilidade**: "se a técnica de regressão demora muito, ela consome tempo que poderia ser destinado à execução de testes" (Henard et al., "Comparing white-box and black-box test prioritization", ICSE 2016).
2. **Contexto**: muitas técnicas assumem disponibilidade de artefatos de entrada (suíte de testes, código-fonte, *traces* de cobertura) que nem sempre existem em contextos reais de teste.

## Testes flaky

Um **teste flaky** é definido como: *"test failures not related to the latest changes but due to non-determinism in the tests"* — ou seja, a mesma versão do código, com os mesmos testes, pode produzir resultados diferentes em execuções distintas, sem relação com nenhuma mudança real no software.

### Por que são problemáticos

- **Perda de confiança**: desenvolvedores passam a ignorar builds que falham ("é só flaky mesmo").
- **Bugs escondidos**: falhas reais acabam descartadas como se fossem flakiness.
- **Tempo desperdiçado**: investigação de falhas que não são bugs reais, à espera de reexecuções.
- **Entrega bloqueada**: uma falha espúria pode bloquear *merges* e *releases*.

Flakiness também compromete pressupostos de outras técnicas: no **teste de regressão**, quebra a suposição de que "passou antes, falha agora = a mudança quebrou algo" (oráculo ruidoso), confunde `git bisect` (depuração enganosa) e prejudica a seleção/priorização de testes. No **teste de mutação**, gera "mortes falsas" de mutantes (inflando artificialmente o *mutation score*) e cobertura instável.

### Causas principais (dados empíricos — FSE 2014)

- **Async wait (45%)**: código que assume um tempo fixo de resposta, como `Thread.sleep(2000);` antes de verificar um estado — e quebra se a resposta real demorar mais.
- **Concurrency (20%)**: condições de corrida entre threads acessando memória compartilhada sem sincronização adequada, causando *lost updates*.

Dados de empresas reais citados no material: **Google** reportou 16% de seus 4,2 milhões de testes como flaky, causando 1,5% das execuções a falharem intermitentemente; **Microsoft** encontrou 4,6% de testes flaky em 5 projetos analisados; **Mozilla** estima um crescimento de mais de 100 novos testes flaky por semana em seu banco de dados de testes.

### Detecção

- **Rerun (reexecução)**: a abordagem típica — reexecutar os testes que falharam —, mas custosa e pode não capturar flakiness intermitente (um exemplo real no material mostra um teste passando em 14 de 20 execuções e falhando nas outras 6, com valores diferentes a cada falha).
- **Rerun + perturbação**: mudar ordem, coleções ou carga para expor flakiness mais cedo (ferramenta citada: [pytest-randomly](https://pypi.org/project/pytest-randomly/)).
- **No rerun**: se um teste falha mas não cobre o código alterado, ele é suspeito de ser flaky, sem precisar reexecutar (ferramenta citada: [DeFlaker](http://www.deflaker.org/)).
- **Predição**: classificar testes como propensos a flakiness usando características estáticas do código, sem executá-los (ferramenta citada: FlakeFlagger).

### Mitigação

- **Corrigir a causa raiz** (majoritariamente no código de teste — 71% das correções, segundo Lam et al., "A Study on the Lifecycle of Flaky Tests", ICSE 2020).
- **Quarentena**: isolar o teste do pipeline bloqueante, com responsável e prazo definidos.
- **Reparo automatizado**: por exemplo, ferramentas como iFixFlakies para testes dependentes de ordem.
- **Deletar**: último recurso, se o teste não agrega valor nenhum.

## Teste combinatorial

Imagine um bug que só ocorre quando um tipo específico de navegador, sistema operacional, versão de driver e idioma estão todos presentes simultaneamente — nenhum desses fatores, isoladamente, causa o erro. Essas são **falhas de interação** (*interaction failures*): disparadas apenas quando dois ou mais valores de entrada interagem para produzir um resultado incorreto.

Testar exaustivamente todas as combinações (*brute force*) costuma ser inviável pelo custo — mas e se for possível garantir que todas as interações entre pares (ou trios) de fatores sejam testadas, reduzindo milhões de casos para poucas dezenas, sem perder a capacidade de detectar esse tipo de defeito? É exatamente isso que o **teste combinatorial** faz, usando princípios de matemática combinatorial para identificar o conjunto mínimo de testes que cobre todas as interações relevantes entre parâmetros.

### O achado empírico central (NIST SP 800-142)

A referência central desta seção é o **NIST Special Publication 800-142 — "Practical Combinatorial Testing"** (Kuhn, Kacker e Lei, 2010), que investigou, a partir de 1999, quantos fatores tipicamente interagem para causar falhas reais em sistemas de diferentes domínios (dispositivos médicos, navegadores, servidores, banco de dados distribuído da NASA):

| Fatores envolvidos | Dispositivos Médicos | Navegador | Servidor | NASA |
|---|---|---|---|---|
| 1 | 66% | 29% | 42% | 68% |
| 2 (cumulativo) | 97% | 76% | 70% | 93% |
| 3 (cumulativo) | 99% | 95% | 89% | 98% |
| 4 (cumulativo) | 100% | 97% | 96% | 100% |

!!! quote "Interaction Rule (regra empírica)"
    "Most failures are induced by single factor faults or by the joint combinatorial effect (interaction) of two factors, with progressively fewer failures induced by interactions between three or more factors."

Na prática, **todas as falhas estudadas puderam ser disparadas por interações de no máximo 4-way a 6-way** — o que torna viável testar sistematicamente essas combinações em vez de todas as combinações possíveis.

### Covering arrays e pairwise testing

Um **covering array** é a estrutura central: uma matriz onde toda combinação de *t* colunas contém todos os valores possíveis dessas *t* variáveis em pelo menos uma linha. O número de testes necessário é proporcional a **v^t · log n** (para *n* parâmetros com *v* valores cada) — cresce exponencialmente com *t*, mas apenas logaritmicamente com o número de parâmetros.

!!! example "Exemplo prático de combinatória — 5 parâmetros de configuração"
    Sistema operacional (3 opções) × navegador (2) × protocolo (2) × CPU (2) × SGBD (3) = **72 combinações exaustivas**. Um covering array **pairwise (2-way)** reduz isso para apenas **10 testes**, cobrindo todos os pares possíveis de valores:

    | Teste | OS | Browser | Protocolo | CPU | SGBD |
    |---|---|---|---|---|---|
    | 1 | Windows | Chrome | IPv4 | Intel | MySQL |
    | 2 | Windows | Firefox | IPv6 | AMD | Sybase |
    | ... | ... | ... | ... | ... | ... |
    | 10 | Mac OS | Firefox | IPv6 | AMD | Oracle |

O algoritmo guloso (*greedy*) para gerar essas combinações: gerar todos os pares possíveis de valor-parâmetro, inicializar a suíte vazia, e enquanto houver pares não cobertos, montar um novo caso de teste escolhendo, para cada parâmetro, o valor que cobre o maior número de pares ainda não cobertos — repetindo até cobertura total.

### Abordagens de teste combinatorial

- **Category-partition testing**: identificação manual dos valores que caracterizam o espaço de entrada, seguida de geração automática das combinações.
- **Pairwise testing**: testa sistematicamente as interações 2-way entre atributos, com um número relativamente pequeno de casos.
- **Catalog-based testing**: agrega e sintetiza a experiência de testadores de uma organização/domínio para identificar valores significativos.

### O problema do oráculo permanece

Mesmo com a geração eficiente de covering arrays, resta determinar o resultado esperado para cada combinação. Abordagens citadas: *crash testing* (teste aleatório, verificando apenas se a combinação causa falha evidente), asserções embutidas (como JML, que podem servir de oráculo), e geração de testes baseada em modelo (usando um *model checker* para derivar entrada + saída esperada simultaneamente).

### Medindo cobertura combinatorial

Como as métricas tradicionais de cobertura de código (instrução, ramo, MC/DC) dependem de acesso ao código-fonte, e o teste combinatorial é essencialmente uma técnica de caixa-preta, usam-se métricas próprias: **cobertura simples t-way** (proporção de combinações de *t* variáveis totalmente cobertas), **cobertura (t+k)-way**, e **cobertura de configuração variável-valor** (proporção de combinações específicas de valores cobertas).

Ferramenta de demonstração citada: [CSRC/NIST — Automated Combinatorial Testing for Software](https://csrc.nist.gov/projects/automated-combinatorial-testing-for-software/downloadable-tools), que inclui o **ACTS** (gerador de covering arrays) e ferramentas de medição de cobertura combinatorial.

## Fuzzing

**Fuzzing (*fuzz testing*)**: técnica de teste automatizado que insere entradas inválidas, inesperadas ou aleatórias para encontrar falhas — muito usada em segurança de software e teste de robustez.

!!! example "Motivação — um buffer overflow clássico em C"
    ```c
    void print_name(char *input) {
        char buffer[16];        // buffer de 16 bytes
        strcpy(buffer, input);  // sem verificar o tamanho de input!
        printf("Voce digitou: %s\n", buffer);
    }
    ```
    Com uma entrada curta, o programa funciona normalmente. Com uma entrada muito maior que 16 caracteres, o `strcpy` escreve além dos limites do buffer, corrompendo a memória e causando um erro de segmentação — um **buffer overflow** que pode ser explorado para execução arbitrária de código.

### Origem histórica

O fuzzing surgiu em 1988, quando o professor **Barton Miller** (Universidade de Wisconsin-Madison), percebendo que ruídos em sua conexão telefônica corrompiam comandos UNIX e os fazia falhar de forma inesperada, criou um exercício para seus alunos testarem a robustez de utilitários UNIX com entradas aleatórias — nascendo os primeiros fuzzers. O resultado: em média, **1/3 dos programas testados quebrou**. O estudo foi publicado em 1990 ("An Empirical Study of the Reliability of UNIX Utilities", Miller, Fredriksen e So) — achando que 24% dos programas testados quebravam com entradas inválidas. Um estudo de replicação, 31 anos depois (2021, na *IEEE Transactions on Software Engineering*), mostrou que fuzzers clássicos **ainda** encontram falhas em utilitários modernos.

### Eficácia comprovada na indústria

- **Mozilla**: fuzzers já encontraram mais de 6.450 defeitos, incluindo 790 marcados como críticos de segurança.
- **Google**: em 30 dias usando **libFuzzer**, mais de 320 defeitos encontrados no Chrome; mantém o **[OSS-Fuzz](https://github.com/google/oss-fuzz)** para projetos *open source*.
- **AFL (American Fuzzy Lop)**: um dos fuzzers mais conhecidos da atualidade.

Outras empresas com fuzzing em produção: Microsoft (drivers, parsers do Windows/Office/Edge), Apple (protocolos iOS/macOS), Mozilla (Firefox, com fuzzing simbólico + cobertura), Intel (firmwares), Amazon AWS (segurança em APIs de nuvem).

### Técnicas de fuzzing

1. **Baseado em mutação**: modifica entradas válidas existentes, gerando variações inválidas — bom para testar *parsers*.
2. **Baseado em gramática**: gera entradas do zero a partir de um modelo/estrutura esperada (XML, JSON, requisições HTTP).
3. **Cego (*dumb fuzzing*)**: gera entradas totalmente aleatórias, sem considerar a estrutura esperada.
4. **Dirigido por cobertura**: usa informação de cobertura de código para guiar a geração de entradas, maximizando a exploração de novos caminhos.

### Categorias de bugs tipicamente encontrados

- **Buffer overflows** — escrita fora dos limites de um array.
- **Ausência de verificação de erros** — código que assume que tudo deu certo (ex.: abrir um arquivo sem checar se ele existe).
- **Valores numéricos fora do esperado** (*rogue numbers*) — ex.: divisão por zero não tratada.
- **Erros de acesso à memória** — ponteiros nulos ou desalocados (*use-after-free*), detectáveis com ferramentas como **AddressSanitizer**.
- **Vazamento de informação** — exposição de dados internos, como em vulnerabilidades de *format string*.

!!! example "Heartbleed (2014, OpenSSL)"
    Um exemplo real amplamente conhecido de bug de vazamento de memória encontrável por fuzzing: o servidor não verificava corretamente o tamanho da mensagem de "heartbeat" retornada, vazando conteúdo arbitrário da memória do servidor.

### Ferramentas e demonstração

O deck de aula inclui um tutorial de uso do **AFL++** — um fuzzer guiado por cobertura que gera entradas mutadas, monitora a execução e aprende quais mutações são mais eficazes:

```bash
sudo apt update && sudo apt install afl++ -y
afl-gcc -o program program.c
AFL_I_DONT_CARE_ABOUT_MISSING_CRASHES=1 afl-fuzz -i inputs -o outputs -- ./program @@
```

!!! tip "Leitura complementar destacada pela disciplina"
    O livro online **[fuzzingbook.org](https://www.fuzzingbook.org)** (Zeller, Gopinath, Böhme, Fraser e Holler) é a referência-base deste tópico e da bibliografia geral da disciplina, com implementações em Python de fuzzers desde o exemplo histórico de Barton Miller até técnicas modernas baseadas em gramática e cobertura.

## TDD e BDD

### Test-Driven Development (TDD)

TDD nasce do **Manifesto Ágil**, via Kent Beck e **XP (Extreme Programming)** — definido como Valores + Princípios + Práticas:

- **Valores**: comunicação, simplicidade, feedback, coragem, respeito, qualidade de vida (semana de 40h).
- **Princípios**: economicidade, melhorias contínuas, "falhas acontecem", *baby steps*, responsabilidade pessoal.
- **Prática central**: **escrever o teste antes do código de produção**.

O ciclo TDD segue três passos, repetidos continuamente:

1. **Red** (vermelho): escreva um teste que falha, porque a funcionalidade ainda não existe.
2. **Green** (verde): implemente o mínimo de código necessário para o teste passar.
3. **Refactor** (refatorar): melhore o código mantendo os testes passando, repetindo o ciclo com mais testes conforme necessário.

!!! example "TDD aplicado a um validador de CPF (Python)"
    **Red** — primeiro teste, falha porque `cpf_valido` não existe:
    ```python
    def test_cpf_valido_simples(self):
        self.assertTrue(cpf_valido("11144477735"))
    ```
    **Green** — implementação mínima ("burra") só para passar:
    ```python
    def cpf_valido(cpf: str) -> bool:
        return cpf == "11144477735"
    ```
    Novos testes forçam a evolução da implementação (mais **Red**), até uma versão real que valida tamanho, sequências repetidas e os dois dígitos verificadores do CPF (mais **Green**).

**Vantagens do TDD**, segundo o material: ao escrever o teste primeiro, o requisito é olhado antes do código (evitando código desnecessário); o ritmo de escrita pode ser controlado quebrando problemas complexos em partes menores; os testes derivam dos requisitos, não da implementação já existente; o código nasce testável; o feedback é rápido (problemas identificados logo após a adição de pouco código); e há *feedback* sobre o próprio design (muitos testes para uma classe pode indicar excesso de responsabilidades; muitos *mocks* pode indicar acoplamento excessivo).

**Quando usar TDD**: quando não se sabe como projetar/arquitetar uma parte do sistema, ou ao lidar com um problema complexo e pouco familiar — os *baby steps* ajudam a explorar e aprender gradualmente. **Quando não usar**: quando o problema e as decisões de design já são claras — nesse caso, não há "nada a explorar" e o TDD pode não agregar benefício significativo.

### Behavior-Driven Development (BDD)

O BDD é apresentado como uma evolução do TDD, motivada por: confusão conceitual em torno do próprio TDD, necessidade de melhorar a comunicação com *stakeholders*, foco no **comportamento** (não em métodos individuais), documentação executável, e encaixe natural com pipelines de DevOps.

A sintaxe **Gherkin** estrutura cenários de comportamento em linguagem natural estruturada:

```gherkin
Feature: Login functionality
  Given The login page is loaded
  When I input username, password and click the Login button
  Then I am on the Homepage
```

- **Given**: pré-condições ou contexto inicial.
- **When**: evento ou gatilho.
- **Then**: resultado esperado.

## Teste de sistemas baseados em IA

As técnicas clássicas de teste carregam pressupostos que deixam de valer quando o "sistema sob teste" é baseado em aprendizado de máquina — por exemplo, particionamento por classes de equivalência assume que conseguimos identificar as classes corretamente e que entradas similares produzem saídas similares; cobertura estrutural assume que a lógica do sistema está no código que conseguimos ler. Esta aula revisita quatro desafios centrais e as técnicas que ajudam a mitigá-los.

### Desafio 1 — Lógica codificada vs. lógica aprendida

!!! example "Detector de spam: regras explícitas vs. pesos de uma rede neural"
    **Código tradicional** — cada regra é legível, testável individualmente, e a cobertura de código funciona perfeitamente:
    ```python
    def is_spam(email):
        spam_score = 0
        if "GRÁTIS" in email: spam_score += 2
        if "URGENTE" in email: spam_score += 2
        # ...
        return spam_score > 5
    ```
    **Sistema de IA** — a lógica está embutida nos pesos de uma rede (`Embedding → LSTM → Dense → sigmoid`), e a função apenas chama `model.predict`. Não há "regra" para ler ou testar isoladamente.

A pergunta central: como testar algo quando não se consegue "ler" a lógica, e como garantir que o modelo aprendeu os padrões certos (e não correlações espúrias)?

**Mitigação — SHAP (SHapley Additive exPlanations)**: técnica que isola a contribuição de cada *feature* para a predição final, funcionando como uma espécie de "caixa branca" para modelos de IA. Permite: testes de regressão (comparar explicações SHAP entre versões do modelo), testes de *bias* (monitorar a contribuição de atributos sensíveis — ex.: `assert abs(shap_gender) < 0.05`), e testes de regras de negócio (verificar que atributos importantes de fato pesam na decisão — ex.: `assert shap_credit_score > 0.1`). Limitações: é uma explicação local (válida só para aquela predição específica), pode ser lenta para modelos complexos, e é uma aproximação, não 100% precisa.

!!! warning "Estudo de caso: Amazon e o recrutamento com viés de gênero (2018)"
    A Amazon desenvolveu um modelo para analisar currículos e priorizar candidatos, treinado com o próprio histórico de contratações da empresa. O modelo aprendeu a **penalizar** currículos contendo o termo "women" (ex.: "women's chess club"), refletindo o viés histórico presente nos dados de treino — não um erro de "inteligência" do modelo, mas um problema dos dados em que foi treinado. A Amazon descontinuou a ferramenta ([fonte](https://www.ml.cmu.edu/news/news-archive/2016-2020/2018/october/amazon-scraps-secret-artificial-intelligence-recruiting-engine-that-showed-biases-against-women.html)).

### Desafio 2 — Quando não temos um oráculo

Para um classificador de imagens de raio-x, qual é a saída "correta"? Cenários desafiadores citados: um modelo erra uma imagem claramente anormal (como saber se é bug de implementação ou limitação inerente do modelo?); um modelo com 95% de acerto em teste cai para 78% em produção (*overfitting*? *domain shift*?); dois especialistas humanos discordam sobre o mesmo caso (qual é a "resposta certa" a validar?).

**Mitigação — testes metamórficos**: em vez de comparar com um resultado esperado absoluto, define-se uma **relação metamórfica (MR)**: se eu transformar a entrada de uma forma específica, como a saída deveria mudar (ou se manter)?

!!! example "Relações metamórficas — classificador de imagens"
    - **MR1 (rotação)**: se classificar(foto) = "gato", então classificar(rotacionar_90°(foto)) = "gato".
    - **MR2 (espelhamento)**: se classificar(foto) = "cão", então classificar(espelhar(foto)) = "cão".
    - **MR3 (brilho)**: se classificar(foto) = "gato", então classificar(aumentar_brilho_10%(foto)) = "gato".

Vantagens: não exige oráculo absoluto (definem-se relações, não respostas); detecta inconsistências sutis de comportamento; é automatizável em larga escala; é agnóstico de domínio. Limitações: exige pensar nas relações corretas (espelhar um raio-x pode mudar o diagnóstico real — lado esquerdo/direito importa em anatomia); pode ser superficial (propriedades óbvias não capturam bugs profundos); pode gerar falsos positivos quando a violação é, na verdade, aceitável.

### Desafio 3 — Espaços de entrada de alta dimensionalidade

Em sistemas tradicionais, uma fronteira de decisão é explícita no código (`age >= 18 && income >= 50000`). Em sistemas de IA, um email de spam é transformado em um vetor de centenas de atributos — não há como visualizar ou testar "o valor-limite" de um espaço com 768 dimensões, e uma mudança mínima na entrada (trocar "!!!" por "..") pode cruzar a fronteira de decisão sem aviso.

**Mitigação — testes adversariais (*adversarial testing*)**: em vez de buscar fronteiras manualmente, usam-se algoritmos que encontram automaticamente as entradas mais propensas a "quebrar" o modelo — a famosa perturbação imperceptível que transforma a classificação de um panda (57,7% de confiança) em gibão (99,3%) é um exemplo clássico da literatura.

!!! example "Teste de robustez e invariância (Python)"
    ```python
    def test_invariancia_atributo_irrelevante():
        cliente = {"nome": "João", "idade": 35, "renda": 8000, "score": 700}
        p_original = model.predict(cliente)
        for nome in ["Maria", "Ana", "José", "Francisca"]:
            variante = {**cliente, "nome": nome}
            assert abs(model.predict(variante) - p_original) < 0.01
    ```
    Trocar apenas o nome do cliente não deveria alterar a predição do modelo de crédito — um teste de invariância a um atributo que não deveria ser relevante.

Vantagens: encontra casos que humanos jamais pensariam, automatizável em escala, matematicamente rigoroso, expõe vulnerabilidades reais. Limitações: pode ser computacionalmente caro, nem sempre transfere para o mundo real, e exige acesso ao modelo (*white-box*) ou um número alto de consultas (*black-box*).

### Desafio 4 — Comportamento não determinístico

Modelos com *temperature* (como LLMs) produzem saídas diferentes para o mesmo *prompt*; mesmo output pode ter sido alcançado por razões internas completamente diferentes. No exemplo do material, três modelos aprovam o mesmo crédito, mas um foca na profissão, outro na idade, e outro em uma correlação espúria com o nome do cliente — como testar se o sistema decidiu pelas razões "certas"?

**Mitigação — testes estatísticos**: em vez de comparar `output == expected`, testa-se se o **comportamento estatístico** do sistema está dentro do esperado, rodando múltiplas execuções.

!!! example "Teste de consistência semântica de um resumo gerado por LLM"
    ```python
    def test_content_consistency():
        summaries = [llm.summarize(article, temperature=0.7) for _ in range(50)]
        similarities = calculate_pairwise_similarity(summaries)
        assert np.mean(similarities) >= 0.75  # similares, mas não idênticos
        assert np.std(similarities) <= 0.15   # baixa variabilidade
    ```

Vantagens: funciona com sistemas não-determinísticos, detecta degradação sutil de desempenho, quantifica incerteza, compatível com *thresholds* em CI/CD. Limitações: mais lento (requer múltiplas execuções), exige definir métricas apropriadas, e os *thresholds* escolhidos podem ser arbitrários.

## IA para testes

Esta aula inverte a perspectiva da anterior: em vez de testar sistemas de IA, discute como a IA (sobretudo LLMs) pode ser usada **como ferramenta de teste** — e onde isso falha.

### O problema central: LLMs reproduzem o código, inclusive seus erros

Quando um LLM gera testes a partir apenas do código-fonte (sem mais contexto), ele tende a reproduzir o comportamento implementado, não o comportamento especificado: as classes e limites testados são os que o código implementa, e os resultados esperados são os que o código produz — não os que deveria produzir. Se o código tiver um bug, o LLM tende a "validar" esse bug como comportamento correto.

!!! example "Um LLM gerando uma asserção incorreta de limite"
    ```python
    def situacao_aluno(media: float) -> str:
        if media < 0 or media > 10: raise ValueError("Média inválida")
        if media > 7.0: return "aprovado"
        if media >= 3.0: return "final"
        return "reprovado"
    ```
    Teste gerado por um LLM (errado): `assert situacao_aluno(3.0) == "reprovado"` — mas, pela regra do código, 3.0 cai em "final". É justamente o tipo de erro de valor-limite que esta disciplina busca ensinar a evitar.

    Referência citada: Yuan et al., "Evaluating and Improving ChatGPT for Unit Test Generation", FSE 2024.

Fornecer a especificação via *docstring* ajuda parcialmente — mas persiste um limite estrutural: **LLMs alucinam**, podendo inventar regras que a especificação não contém ou esquecer limites implícitos.

### Além dos LLMs: geração baseada em busca

Abordagens alternativas ou complementares aos LLMs: **geração baseada em busca** (algoritmos genéticos evoluem testes para maximizar cobertura — ferramentas **Evosuite**, Java, e **Pynguin**, Python) e **abordagens híbridas**, como o **CodaMosa**, que chama o Pynguin e recorre a um LLM quando a busca estagna na cobertura. Desafio comum: baixa legibilidade dos testes, e ainda refletem o comportamento atual do código (um "oráculo de regressão", não um oráculo de correção).

!!! quote "Cobertura não é garantia de qualidade"
    "We found that there is a low to moderate correlation between coverage and effectiveness when the number of test cases in the suite is controlled for... coverage, while useful for identifying under-tested parts of a program, should not be used as a quality target because it is not a good indicator of test suite effectiveness." — Inozemtseva and Holmes, "Coverage Is Not Strongly Correlated with Test Suite Effectiveness", ICSE 2014.

### Avaliando testes gerados por IA: mutação como juiz

Independentemente de quem gerou os testes (humano ou IA), o **teste de mutação** (já apresentado em [Teste de mutação](#teste-de-mutacao)) serve como critério objetivo de avaliação — "testes de mutação podem atuar como juízes". Permite expor cobertura inflada (100% de cobertura de linhas com *mutation score* baixo), expor testes sem *assert* efetivo, e guiar a geração de novos testes a partir do relatório de mutação.

Pesquisa recente conecta IA e mutação de duas formas: arquiteturas multiagente, onde um agente "revisor" corrige o que um agente "gerador" produziu (ex.: *TestAgent*, Shang et al., FSE 2026, usando um grafo de conhecimento de código para reduzir alucinações e erros de compilação), e mutantes "semânticos" gerados com apoio de IA — não apenas trocas sintáticas de operador, mas falhas plausíveis de domínio.

!!! example "Mutante de domínio, gerado com apoio do Claude.ai"
    ```python
    # Original
    def pode_ver_perfil(visitante, dono):
        if visitante in dono.bloqueados:
            return False
        if dono.perfil_privado and visitante not in dono.amigos:
            return False
        return True

    # Mutante — falha plausível de domínio, não mera troca de operador
    def pode_ver_perfil(visitante, dono):
        if visitante in dono.bloqueados and visitante not in dono.amigos:  # MUTANT
            return False
        if dono.perfil_privado and visitante not in dono.amigos:
            return False
        return True
    ```
    O mutante introduz uma falha sutil: um visitante bloqueado que também seja "amigo" passaria a conseguir ver o perfil, quebrando a regra de bloqueio — bem mais próximo de um bug real do que uma simples troca de `<` por `>`.

    Referência citada: Foster et al., "Mutation-Guided LLM-based Test Generation at Meta", FSE 2025.

### Detecção de testes flaky sem reexecução

Retomando o tema de [testes flaky](#testes-flaky): em vez da detecção clássica por reexecução repetida (custosa), estudos usam o **vocabulário textual dos testes** (análise estática) para prever flakiness com classificadores de *machine learning* como Random Forest e KNN (Verdecchia et al., "Know Your Neighbor: Fast Static Prediction of Test Flakiness", IEEE Access 2021).

### IA aplicada ao fuzzing

Retomando [fuzzing](#fuzzing): o ponto fraco do fuzzing clássico é gerar entradas **estruturadas** que passem pelo parser do sistema (um JSON ou SQL válidos). LLMs ajudam criando entradas plausíveis que conseguem "ir mais fundo" no sistema testado — ferramenta citada: **[Fuzz4All](https://github.com/fuzz4all/fuzz4all)**, "Universal Fuzzing with Large Language Models". O desafio é performance/custo: um fuzzer clássico gera milhares de entradas por segundo, enquanto cada chamada a um LLM leva segundos.

!!! tip "Leitura complementar destacada pela disciplina"
    O livro **[mlip-cmu.github.io/book](https://mlip-cmu.github.io/book/)** (Machine Learning in Production, Carnegie Mellon University) é indicado como referência complementar para os temas de IA aplicada à engenharia de software e ao teste de sistemas de/com IA cobertos nesta e na aula anterior.

### Em resumo

1. A IA é ótima para gerar entradas e escrever testes — rápida, legível, incansável.
2. A IA não sabe o que o sistema *deveria* fazer — sem especificação, ela fotografa o código, bugs incluídos.
3. Os fundamentos clássicos continuam sendo os juízes: valor-limite para escolher os casos, mutação para medir a força dos testes, especificação para definir o que é correto.
4. Use a IA, mas verifique: o teste compila, roda, verifica algo, e verifica a coisa certa.
