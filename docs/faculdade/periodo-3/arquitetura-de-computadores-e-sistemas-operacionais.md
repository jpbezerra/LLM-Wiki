# Arquitetura de Computadores e Sistemas Operacionais

---

## Introdução, Abstração e Tecnologia do Computador

Um **computador** é formado pela combinação de **hardware** (HW) — a parte física da máquina, como chips, monitores e teclado — e **software** (SW) — os programas e dados que rodam sobre esse hardware, como sistemas operacionais, compiladores e editores de texto. Nenhum dos dois é útil isoladamente: o hardware sem software não sabe o que fazer, e o software sem hardware não tem onde executar.

### Classes de computadores

Computadores modernos se dividem, grosso modo, em três grandes classes, cada uma otimizada para um conjunto diferente de restrições:

| Classe | Características | Prioridades de projeto |
|---|---|---|
| **Desktop** | Computador pessoal de desempenho genérico. | Bom desempenho a baixo custo; flexibilidade, versatilidade e conectividade. |
| **Servidores** | Executam aplicações mais complexas, atendendo muitos usuários simultaneamente; inclui a classe dos supercomputadores. | Grande poder de armazenamento e processamento. |
| **Embarcados** | Sistemas de computação integrados a dispositivos maiores (celulares, carros, televisões) com forte integração com o hardware. | Robustez (usados em aplicações críticas); otimizados para bom desempenho com custo e energia reduzidos. |

### Arquitetura x Organização

Um ponto central para estudar computadores é distinguir dois níveis de descrição que, no dia a dia, costumam ser confundidos:

!!! note "Arquitetura"
    Refere-se aos atributos do sistema **visíveis ao programador**, que têm impacto direto na execução lógica de um programa — o conjunto de instruções (ISA), os modos de endereçamento e as estruturas de dados que o hardware suporta.

!!! note "Organização"
    Refere-se à **implementação física**: como os componentes de hardware estão estruturados e conectados para cumprir a arquitetura — a estrutura interna, os detalhes físicos (circuitos, pipeline, cache, ALU etc.) e a eficiência prática dessa implementação.

Uma consequência importante dessa distinção é que **uma arquitetura pode sobreviver por décadas**, mesmo enquanto a organização que a implementa muda completamente com a evolução da tecnologia — é o caso, por exemplo, da arquitetura x86, cuja ISA se mantém compatível há muitos anos, apesar de suas implementações internas terem mudado radicalmente.

#### Estilos de design para arquiteturas de ISA

Dentro da arquitetura, um ponto central é o estilo do **conjunto de instruções (ISA)**, que tradicionalmente se divide em duas grandes filosofias:

| | RISC (*Reduced Instruction Set Computer*) | CISC (*Complex Instruction Set Computer*) |
|---|---|---|
| **Filosofia** | Conjunto reduzido e simplificado de instruções. | Conjunto de instruções complexo, com operações elaboradas. |
| **Tamanho/duração das instruções** | Geralmente do mesmo tamanho, executadas em um único ciclo de clock. | Instruções podem variar em tamanho e duração. |
| **Hardware** | Simples; compensa com otimizações de software (compilador). | Complexo, para decodificar e executar instruções elaboradas. |
| **Exemplo** | MIPS | Intel x86 |

#### Modos de endereçamento

Os **modos de endereçamento** dizem respeito a como a CPU identifica o endereço dos dados necessários para uma instrução — são parte da arquitetura do conjunto de instruções (ISA) e determinam a lógica para localizar dados na memória ou em registradores durante a execução.

| Modo | Como funciona | Uso típico |
|---|---|---|
| **Imediato** | O operando está diretamente embutido na instrução. | Simples e rápido, mas limitado pelo tamanho do campo de operando; usado quando o dado é conhecido no momento da codificação (constantes). |
| **Direto** | O endereço efetivo é especificado diretamente na instrução. | Acessar posições de memória específicas, em sistemas com memória mapeada diretamente. |
| **Indireto** | O endereço efetivo é obtido a partir do conteúdo de um registrador ou posição de memória que contém o endereço do operando. | Acesso a matrizes ou listas encadeadas. |
| **Por registrador** | A instrução especifica diretamente o registrador que contém o dado. | Operações aritméticas/lógicas entre valores já em registradores. |
| **Base + deslocamento** | O endereço efetivo é calculado somando um offset a um registrador base. | Acessar arrays ou elementos na memória. |
| **Indexado** | O endereço do operando é calculado somando o valor de um registrador de índice a um deslocamento constante. | Acesso a elementos em arrays/matrizes, navegação em estruturas de dados. |
| **Relativo** | O endereço é calculado com base no valor atual do *program counter*. | Usado principalmente em branches (desvios condicionais: `beq`, `bne` etc.). |
| **Por pilha (stack)** | Os dados são manipulados diretamente na pilha. | Gerenciamento de variáveis locais. |
| **Implícito** | Os operandos estão implícitos, não especificados diretamente. | Operações aritméticas e de controle em arquiteturas complexas. |
| **Pseudo-direto** | Caso especial de endereçamento implícito, em que parte do endereço é fornecida diretamente e outra parte é derivada do program counter. | Instruções de salto incondicional. |

!!! example "Exemplos em Assembly (MIPS/x86)"
    **Imediato**
    ```nasm
    addi $to, $zero, 10 ; adicionando 10 em $t0
    ; o 10 é diretamente fornecido na instrução
    ```

    **Direto**
    ```nasm
    lw $t0, 0x10010000
    ; carrega o valor na memória no endereço absoluto
    ; 0x10010000 em $t0
    ```

    **Indireto**
    ```nasm
    mov eax, [ebx]
    ; o conteúdo do registrador ebx é tratado como o endereço,
    ; e o valor armazenado nesse endereço é movido para eax
    ```

    **Por registrador**
    ```nasm
    add $t0, $t1, $t2 ; $t0 = $t1 + $t2
    ; especifica os registradores $t1 e $t2
    ```

    **Base + deslocamento**
    ```nasm
    lw $t0 , 4($t1)
    ; carrega a memória a partir do endereço $t1 + 4
    ```

    **Indexado**
    ```nasm
    mov eax, [ebx + esi*4]
    ; Acessa o endereço `ebx` somado ao índice `esi`
    ; multiplicado por 4
    ; (tamanho de um elemento, no caso de um array de inteiros)
    ```

    **Relativo**
    ```nasm
    beq $t0, $t1, label
    ; se $t0 == $t1, desvia para "label"
    ```

    **Por pilha**
    ```nasm
    push eax  ; Armazena o valor de `eax` no topo da pilha
    pop ebx
    ; Recupera o valor do topo da pilha para `ebx`
    ; o valor é retirado da pilha
    ```

    **Implícito**
    ```nasm
    mul ebx
    ; Multiplica o valor em `ebx` pelo valor em `eax`
    ; o resultado é armazenado implicitamente em `eax`
    ```

    **Pseudo-direto**
    ```nasm
    j 0x00400000
    ; salta para o endereço pseudo-direto
    ; especificado
    ```

### Modelo de um computador

Independentemente da classe, todo computador segue, em essência, o mesmo modelo de componentes interconectados:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image.png)

#### CPU

A **CPU** (*Central Processing Unit*, Unidade Central de Processamento) é o "cérebro" do computador, implementado fisicamente em um chip (microprocessador). De forma contínua, a CPU realiza três operações básicas, em ciclo:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%201.png)

A CPU é composta internamente por três unidades principais:

- **Unidade de Controle (CU)** — coordena e gerencia a execução das instruções: interpreta as instruções do programa e envia sinais de controle para as demais partes da CPU e para os dispositivos do sistema. É responsável por decodificar as instruções, controlar o fluxo de dados entre registradores, ALU e memória, e coordenar a execução do programa como um todo.
- **Unidade Lógica e Aritmética (ALU)** — realiza operações aritméticas e lógicas: cálculos matemáticos e comparações lógicas.
- **Registradores** — pequenas áreas de memória de alta velocidade, usadas para armazenar dados temporários e intermediários durante a execução dos programas. Servem para armazenar resultados de cálculos da ALU, endereços de memória ou instruções em processo de execução, e se integram ao *program counter* (que mantém o endereço da próxima instrução a executar); registradores de propósito geral armazenam operandos de instruções.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%202.png)

A CPU busca programas e dados residentes na memória, e armazena dados de volta na memória, continuamente.

##### Cache

A **cache** é um tipo de memória de alta velocidade, usada para armazenar temporariamente dados e instruções que o processador acessa com frequência, com a função de reduzir o tempo necessário para acessar dados na memória principal. Funciona como uma camada intermediária entre o processador e a memória principal, armazenando dados acessados frequentemente ou recentemente. Quando a CPU precisa de um dado, ela primeiro busca na cache (**cache hit**) e, só se não o encontrar lá, busca na memória principal (**cache miss**).

A cache é organizada em níveis, cada um com um trade-off diferente entre velocidade e capacidade:

| Nível | Localização | Velocidade | Capacidade típica | Observação |
|---|---|---|---|---|
| **L1** | Dentro do núcleo da CPU | Muito rápida | 16 KB – 128 KB | Dividida em cache de dados e cache de instruções. |
| **L2** | Dentro ou próxima do núcleo | Mais lenta que L1 | 256 KB – alguns MB | Armazena dados acessados com menor frequência que os da L1. |
| **L3** | Compartilhada entre todos os núcleos | Mais lenta que L2 | Vários MB | Serve como camada de suporte para as caches L1 e L2. |

!!! note "Processadores multicore"
    São aqueles em que há mais de um núcleo (CPU) no mesmo chip, cada um podendo executar instruções de forma independente e simultânea.

#### Memória principal (RAM)

A **memória principal (RAM)** armazena os programas e dados que estão sendo usados ativamente pela CPU. É mais rápida que as memórias secundárias, porém mais volátil (perde os dados quando falta energia) e mais cara por byte armazenado.

##### SRAM x DRAM

Ambas são tipos de memória volátil (RAM) — ou seja, perdem os dados quando não há energia — mas com implementações físicas e trade-offs bem diferentes:

| | SRAM (*Static RAM*) | DRAM (*Dynamic RAM*) |
|---|---|---|
| **Armazenamento de um bit** | Um flip-flop de transistores. | Um capacitor, controlado por um transistor. |
| **Necessidade de atualização** | Não precisa ser atualizada — mantém os dados enquanto houver energia. | Precisa ser constantemente atualizada (*refresh*), pois os capacitores perdem carga com o tempo. |
| **Velocidade e custo** | Extremamente rápida; mais cara; baixo consumo de energia durante a operação. | Mais lenta; consome mais energia; mais barata. |
| **Uso típico** | Memória cache (L1, L2, L3) e registradores internos de alta performance. | Memória principal (RAM) de computadores e dispositivos móveis; buffers em placas de vídeo e sistemas embarcados. |

##### Segmentos da memória RAM

A memória RAM alocada a um programa em execução é organizada, tipicamente, em segmentos com propósitos distintos:

- **Código** — área onde estão armazenadas as instruções executáveis do programa: o código de máquina gerado pelo compilador, que será executado pela CPU. Geralmente é somente leitura, e inclui as instruções de funções e métodos do programa (uso comum em `if`, `while` e chamadas de função).
- **Pilha** — área de memória usada para armazenar dados temporários e estruturas locais, gerenciada automaticamente pelo sistema. Trabalha no estilo **LIFO**, armazenando variáveis locais, endereços de retorno de funções e parâmetros de funções; cresce e diminui conforme as funções são chamadas e retornam. É muito usada em declarações de variáveis locais e em funções recursivas (uso extensivo da pilha). Cresce **para baixo** (para endereços menores), e possui um registrador especial, o *stack pointer*, que aponta para o endereço de memória do topo da pilha.
- **Heap** — área usada para alocar dados dinâmicos durante a execução do programa, com o programador controlando explicitamente a alocação e a liberação (via `malloc`/`free` em C, ou `new`/`delete` em C++, por exemplo). O tamanho pode variar dinamicamente, mas o uso descontrolado pode levar a *memory leaks* (vazamentos de memória). Cresce **para cima** (para endereços maiores), e é tipicamente usada na criação de estruturas como listas, árvores etc.
- **Dados (Data Segment)**:
    - **Dados estáticos** — contêm variáveis globais e estáticas declaradas no programa, cujo tempo de vida é igual ao da execução do programa inteiro.
    - **Dados iniciais e não iniciais** — o **BSS** (*Block Started by Symbol*) armazena variáveis globais e estáticas **não** inicializadas; o **Data Segment** propriamente dito armazena variáveis globais e estáticas **já** inicializadas.

#### Armazenamento secundário

São os tipos de memória usados para armazenamento de **longa duração** de dados e programas — ao contrário da RAM, retêm os dados mesmo sem energia.

##### SSD x HD

| | HD (*Hard Disk Drive*) | SSD (*Solid State Drive*) |
|---|---|---|
| **Tecnologia** | Magnética: um braço mecânico com cabeça de leitura/gravação e discos girando em alta velocidade; o braço se move fisicamente para localizar os dados. | Memória flash (chips NAND); não possui partes móveis. |
| **Acesso** | Lento, pois depende de movimento mecânico. | Eletrônico, resultando em maior velocidade e confiabilidade. |
| **Capacidade e custo** | Geralmente alta capacidade e baratos. | Geralmente mais caros, com capacidade inferior ao HD pelo mesmo preço. |

##### SATA x PATA

São padrões de interface usados para conectar dispositivos de armazenamento (HDs, SSDs) à placa-mãe:

- **PATA** (*Parallel Advanced Technology Attachment*) — utiliza transmissão paralela de dados, com vários bits transferidos simultaneamente em diferentes fios. Comum em computadores mais antigos.
- **SATA** (*Serial Advanced Technology Attachment*) — utiliza transmissão serial, enviando dados bit a bit por um único canal. Substituiu o PATA, com velocidade de transferência muito superior.

#### Dispositivos de E/S e redes

Os **dispositivos de entrada/saída (E/S)** incluem mouse, teclado, monitor de vídeo, entre outros periféricos pelos quais o computador interage com o mundo externo. As **redes** permitem a comunicação e o compartilhamento de recursos entre computadores:

- **LAN** (*Local Area Network*) — rede Ethernet dentro de um prédio ou empresa.
- **WAN** (*Wide Area Network*) — redes de longa distância, como a própria internet.
- **Wireless Network** — redes sem fio, como Wi-Fi e Bluetooth.

#### Exemplos ilustrativos

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%203.png)

A memória principal (RAM) possui, tipicamente, um custo médio por GB, velocidade de acesso alta (dezenas a centenas de ns) e capacidade de armazenamento média (alguns GB). A memória secundária tem custo por GB baixo, velocidade de acesso baixa (alguns ms) e capacidade de armazenamento alta (dezenas de GB a TB). Já a memória cache tem custo por GB alto, velocidade de acesso altíssima (alguns ns) e capacidade baixíssima (KB a alguns MB) — ilustrando a clássica pirâmide de trade-off entre velocidade, custo e capacidade na hierarquia de memória.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%204.png)

A Unidade de Controle (CU) controla o fluxo de dados dentro da CPU e entre a CPU e os demais componentes, interpretando e decodificando as instruções; a Unidade Lógica e Aritmética (ALU) realiza as operações lógicas e aritméticas; e os registradores guardam informações e dados temporários durante a execução.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%205.png)

Reforçando a classificação vista anteriormente: desktops são computadores de uso pessoal com bom custo-benefício; servidores têm alta capacidade de armazenamento e processamento; e sistemas embarcados são computadores especializados, integrados a outros dispositivos.

### Desempenho

Avaliar o desempenho de um computador exige cuidado com a métrica escolhida, já que diferentes métricas capturam aspectos diferentes do problema:

- **Tempo de resposta** — tempo necessário para completar uma tarefa.
- **Throughput** — total de trabalho realizado por unidade de tempo.

Em geral, são necessárias métricas e conjuntos de aplicações (benchmarks) diferentes para fazer comparações justas entre sistemas. Por exemplo:

- **Substituir o processador por um mais rápido** tende a melhorar o throughput, pois mais tarefas são completadas por unidade de tempo.
- **Adicionar mais processadores** não altera o tempo de execução de uma única tarefa, mas permite que mais tarefas sejam executadas simultaneamente (melhorando o throughput); se a demanda já estava muito alta, isso também pode melhorar o tempo de resposta.

#### Tempo de resposta e desempenho relativo

A noção de **desempenho** é definida como o inverso do tempo de execução:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%206.png)

Ou seja, quanto menor o tempo de resposta, melhor o desempenho.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%207.png)

Para comparar o desempenho de diferentes computadores de forma quantitativa, usamos a razão entre seus desempenhos (ou, de forma equivalente, a razão inversa entre seus tempos de execução):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%208.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%209.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2010.png)

    Para saber quantas vezes o computador A é mais rápido que o B, calculamos:

    $$
    \frac{\text{Performance}_A}{\text{Performance}_B}
    $$

    O que é equivalente a:

    $$
    \frac{\text{Execution time}_B}{\text{Execution time}_A}
    $$

    Como o tempo de execução de B é 15 s e o de A é 10 s, o resultado é 15/10 = 1,5. Logo, **A é 1,5 vezes mais rápido que B**.

!!! example "Mais exemplos"
    **1.**

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2011.png)

    Para o programa 1, o computador 2 é mais rápido: `performance_M2/performance_M1 = tempo_M1/tempo_M2 = 2/1,5 ≈ 1,33` — M2 é 1,33 vezes mais rápido que M1.

    Para o programa 2, o computador 1 é mais rápido: `performance_M1/performance_M2 = tempo_M2/tempo_M1 = 10/5 = 2` — M1 é 2 vezes mais rápido que M2.

    De forma geral (considerando o tempo total somado dos dois programas), o computador 1 é mais rápido: `performance_M1/performance_M2 = tempo_M2/tempo_M1 = 11,5/7 ≈ 1,64` — M1 é, em média, 1,64 vezes mais rápido que M2.

    **2.**

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2012.png)

    Um canal extra de rede diminui o tempo de resposta e aumenta o throughput, pois com mais rede o tempo de resposta é mais curto e mais trabalho é realizado por unidade de tempo. Já adicionar mais memória, nesse cenário, não altera nenhuma das duas variáveis, pois o dispositivo é limitado pelo desempenho da rede (o gargalo não está na memória).

    **3.**

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2013.png)

    Temos `performance_C/performance_B = 4`, logo `tempo_B/tempo_C = 4`. Como `tempo_B = 28`, então `28/tempo_C = 4`, e portanto `tempo_C = 7` segundos.

#### CPU time

O **CPU time** é o tempo gasto pela CPU processando uma determinada tarefa — não inclui o tempo de E/S nem o tempo de execução de outros programas concorrentes. Programas diferentes são afetados de forma diferente pelo desempenho da CPU e do sistema, e o CPU time pode ser dividido em:

- **User CPU Time** — tempo de CPU gasto executando o próprio programa.
- **System CPU Time** — tempo de CPU gasto pelo sistema operacional realizando tarefas em nome do programa.

Além da velocidade bruta do processador, o desempenho de uma aplicação também depende do conjunto de instruções, da escolha da linguagem de implementação e da eficiência do compilador usado.

#### Clock do sistema

As operações realizadas pelo processador são controladas por um **clock do sistema**. Normalmente, as operações começam com um pulso de clock:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2014.png)

Em nível básico, a velocidade do processador é ditada pela frequência de pulso produzida pelo clock, medida em ciclos por segundo (**Hertz**, Hz):

- **Período de clock** — tempo entre pulsos (duração de um ciclo), por exemplo 0,25 ns (picossegundos).
- **Taxa de clock (frequência de clock)** — taxa de pulso, por exemplo 1 GHz = 1 bilhão de pulsos por segundo; é o inverso do período de clock.

#### CPU time e ciclos de clock

A relação entre ciclos de clock, período de clock e CPU time é dada por:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2015.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2016.png)

Essa fórmula mostra que o desempenho pode ser melhorado tanto **reduzindo o número de ciclos de clock** necessários para o programa quanto **aumentando a frequência do clock**.

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2017.png)

    O computador B precisa que seu número de ciclos de clock seja 1,2 vezes o de A:

    - Ciclos de clock de A: `10 s (tempo de exec.) × 2 GHz (freq.) = 10 × 2 × 10⁹ = 2 × 10¹⁰`.
    - Logo, os ciclos de clock de B são `2,4 × 10¹⁰`.

    Com o tempo de execução e os ciclos de clock de B em mãos, calculamos sua frequência:

    - Frequência de clock de B: `2,4 × 10¹⁰ / 6 s = 0,4 × 10¹⁰ = 4 × 10⁹`.
    - Logo, **B precisa de uma frequência de clock de 4 GHz**.

#### Número de ciclos e número de instruções

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2018.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2019.png)

#### Desempenho de instrução (CPI)

O tempo de execução de um programa depende do número de instruções executadas, algo que a fórmula simples de ciclos de clock da CPU, por si só, não captura. A fórmula completa para o número de ciclos de clock da CPU na execução de um programa é:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2020.png)

!!! note "CPI"
    **CPI** (*Cycles Per Instruction*) é a média do número de ciclos de todas as instruções executadas em um programa, determinada pelo hardware. Permite comparar diferentes implementações da mesma ISA.

    Sendo o processador controlado por um clock com frequência constante `f`, e `I` o número de instruções de máquina executadas pelo programa, a CPI é dada por:

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2021.png)

    O número de ciclos pode variar de acordo com o tipo de instrução `i` (load, store, branch, jump etc.). A CPI também pode ser expressa como:

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2022.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2023.png)

#### Desempenho de CPU

O tempo de processador necessário para executar um dado programa é dado por:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2024.png)

Com os três fatores que impactam o desempenho do sistema — clock do sistema, CPI e número de instruções — chegamos à equação completa do CPU Time:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2025.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2026.png)

    - `Tempo_A = instr. × 2 × 250 ps = instr. × 500 ps`
    - `Tempo_B = instr. × 1,2 × 500 ps = instr. × 600 ps`

    Dados os tempos de A e B, A é mais rápido, pois seu tempo é `instr. × 500 ps`, enquanto o de B é `instr. × 600 ps`:

    - `performance_A / performance_B = n`
    - `tempo_B / tempo_A = n`
    - `instr. × 600 ps / instr. × 500 ps = 1,2`

    **A é 1,2 vezes mais rápido que B.**

!!! example "Comparando sequências de código"
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2027.png)

    A sequência de código que executa mais instruções é a sequência 2 (executa 6 instruções, contra 5 da sequência 1).

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2028.png)

    No entanto, a sequência 2 precisa de **menos ciclos** no total para completar suas instruções — ou seja, ter mais instruções não implica necessariamente ser mais lenta, pois o CPI de cada instrução pesa no resultado final.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2029.png)

#### IPS, tempo de execução e outras métricas

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2030.png)

Juntando todas essas medidas básicas de desempenho, chegamos à fórmula geral do tempo de execução:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2031.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2032.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2033.png)

##### MIPS e MFLOPS

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2034.png)

Onde `f` é a frequência de clock, `I` é o número de instruções e `T` é o tempo de execução.

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2035.png)

    Cálculo do CPI médio:

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2036.png)

    Taxa MIPS:

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2037.png)

##### Benchmarks

MIPS e MFLOPS podem ser métricas inadequadas para avaliar o desempenho de processadores, principalmente devido às diferenças entre conjuntos de instruções (RISC vs. CISC): a taxa de execução de instruções não é um critério justo para comparar arquiteturas diferentes.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2038.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2039.png)

Por isso, usam-se **programas benchmark** — programas de referência, escolhidos para representar cargas de trabalho reais, e executados de fato nos sistemas sendo comparados. As características desejadas de um bom programa benchmark são:

- Ser escrito em uma linguagem de alto nível.
- Representar um tipo particular de estilo de programação.
- Poder ser medido com facilidade.
- Ter ampla distribuição (ser representativo de muitos usos reais).

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2040.png)

    - Instruções_A = `100 × 10⁶ × 60 = 6.000` milhões.
    - Instruções_B = `75 × 10⁶ × 45 = 3.375` milhões.

    O computador A executa mais instruções que B — isso provavelmente se explica por A e B possuírem arquiteturas diferentes, que implementam instruções de modos diferentes.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2041.png)

    `(6.000 - 3.375) / 3.375 = 0,778 = 77,8%`.

#### Lei de Amdahl

Projetistas de sistemas estão constantemente procurando melhorar o desempenho, aperfeiçoando ou mudando projetos. Em todos os casos, é importante observar que o *speedup* obtido em **um** aspecto do projeto **não** resulta, necessariamente, em uma melhoria proporcional no desempenho total do sistema.

!!! warning "Armadilha comum"
    Esperar que a melhoria de um único aspecto de um computador aumente o desempenho geral por uma quantidade proporcional ao tamanho dessa melhoria.

A **Lei de Amdahl** formaliza essa intuição: a possível melhoria de desempenho obtida com uma dada otimização é limitada pelo quanto essa otimização é efetivamente utilizada.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2042.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2043.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2044.png)

    Conclusão: **não é possível** fazer melhorias suficientes para executar esse programa 5 vezes mais rápido, dada a fração do tempo que a otimização em questão consegue afetar.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2045.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2046.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2047.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2048.png)

A Lei de Amdahl ilustra bem os problemas enfrentados pela indústria no desenvolvimento de máquinas multicore com um número cada vez maior de processadores: o software que roda nessas máquinas precisa ser adaptado para um ambiente de execução altamente paralelo, caso contrário a fração sequencial do programa (que não se beneficia do paralelismo) acaba dominando o tempo de execução, limitando o ganho possível.

---

## Arquitetura de um processador

### Linguagem de máquina

Para que o hardware consiga entender e executar instruções escritas por um programador, é necessário percorrer uma série de etapas de tradução:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2049.png)

#### ISA

A **ISA** (*Instruction Set Architecture*) é a interface entre o software e o hardware, que instrui o hardware sobre como executar cada operação. Computadores diferentes podem ter ISAs diferentes — e é justamente essa interface que define a "arquitetura" no sentido discutido anteriormente.

##### ISA do MIPS

O MIPS é um exemplo clássico de arquitetura **RISC**, muito utilizada em sistemas embarcados, com as seguintes características de projeto:

- **Todas as instruções possuem 3 operandos.** A simplicidade favorece a regularidade: hardware para um número variável de operandos é mais complexo do que um hardware com número fixo de operandos.
- **Cada instrução faz apenas uma operação.**
- **Todos os registradores têm 32 bits** — 32 bits é uma **palavra** (*word*) no MIPS.
- **O número de registradores é reduzido: 32.** Isso impacta o tamanho da instrução — um número grande de registradores pode penalizar o desempenho (o ciclo de clock), já que, de forma geral, quanto menor o número de registradores, mais rápido o acesso a eles.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2050.png)

**Operações aritméticas:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2051.png)

Para melhorar o desempenho, os operandos de uma instrução aritmética devem estar em registradores, já que o acesso a eles é muito mais rápido do que o acesso à memória principal.

**Operandos na memória:**

Estruturas mais complexas podem conter mais elementos do que a quantidade de registradores disponíveis no computador — por isso, essas estruturas são mantidas na memória. Porém, operações aritméticas, por exemplo, só executam sobre dados em registradores; por isso, o MIPS possui instruções específicas de transferência de dados entre memória e registradores.

Para acessar uma palavra na memória, a instrução precisa informar o endereço de memória correspondente. A memória é tratada como um grande array unidimensional, com o endereço atuando como índice para esse array, começando em 0.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2052.png)

**Endereços de memória — Big Endian vs. Little Endian:**

O endereço de uma palavra coincide com o endereço de um dos bytes que a compõem. No MIPS, que é **Big Endian** (*big end*), o endereço da palavra é definido como o endereço do byte mais à esquerda. Já em uma arquitetura **Little Endian**, o endereço da palavra é definido como o endereço do byte mais à direita.

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2053.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2054.png)

**Operandos imediatos:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2055.png)

Os operandos desse tipo de instrução são: destino, fonte e constante. O MIPS também possui um registrador especial constante com valor 0: `$zero`.

### Base numérica

O computador utiliza a **base binária**: o bit pode assumir dois estados — 0, para nível lógico baixo, e 1, para nível lógico alto.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2056.png)

Palavras de 32 bits permitem representar `2^32` sequências de bits distintas. Números positivos, nessa representação, são chamados de **números sem sinal**.

#### Conversão de base

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2057.png)

A conversão de decimal para binário é feita por um algoritmo de **divisões sucessivas** por 2, coletando-se os restos.

!!! example
    **1.** Transformar 13 em binário: `13 / 2 = resto 1`, `6 / 2 = resto 0`, `3 / 2 = resto 1`, `1 < 2 → resto 1`. Lendo os restos da última divisão para a primeira: **13 em binário = 1101**.

    **2.** Transformar 15 em binário: `15 / 2 = resto 1`, `7 / 2 = resto 1`, `3 / 2 = resto 1`, `1 < 2 → resto 1`. **15 em binário = 1111**.

#### Representação de números negativos

Existem duas representações comuns de números negativos em base binária:

**Magnitude e sinal** — cada número tem um bit adicional para indicar o sinal (o bit mais significativo, MSB), enquanto o resto da representação permanece inalterado.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2058.png)

!!! warning "Problemas da representação de magnitude e sinal"
    Há duas representações distintas para o zero (+0 e -0), e a soma de um número com seu "inverso" nem sempre resulta em zero.

**Complemento de dois** — resolve os problemas da representação anterior. Define que o inverso de um número é aquele que, somado ao original, resulta em zero. O MSB é usado para representar o sinal do número; para uma representação com `n` bits, o bit de sinal deve ser ponderado em `-2^(n-1)`.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2059.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2060.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2061.png)

**Algoritmo para representar um número negativo em complemento de dois:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2062.png)

!!! example
    Representar o número **-34** em binário:

    1. Representar o número positivo: `34 / 2 = resto 0`, `17 / 2 = resto 1`, `8 / 2 = resto 0`, `4 / 2 = resto 0`, `2 / 2 = resto 0`. `34` em binário é `100010`; representando em complemento de dois (com bit de sinal), fica `0100010` (positivo).
    2. Inverter os bits: `1011101`.
    3. Somar 1 à palavra invertida: `1011101 + 1 = 1011110` (somando `1 + 1`, o resultado é `0` e sobe o carry para o próximo bit à esquerda).

##### Operações aritméticas com complemento de dois

!!! example
    **1.** `7 - 5`:

    - 7 em binário: `7 / 2 = resto 1`, `3 / 2 = resto 1`, `1 < 2 → resto 1` → com o MSB, fica `0111`.
    - 5 em binário: `5 / 2 = resto 1`, `2 / 2 = resto 0`, denominador 1 → com o MSB, fica `0101`.
    - Transformar 5 em -5: `0101 → 1010 → 1010 + 1 = 1011`.
    - `7 + (-5)`: `0111 + 1011 = 0010 = 2`.

    **2.** `13 - 45` → `0001101 - 0101101`:

    - Transformar 45 em -45: `1010011`.
    - `13 + (-45) = 0001101 + 1010011 = 1100000 = -32`.

### Extensão de sinal

**Extensão de sinal** é o processo de mudar o número de bits de uma representação, acrescentando posições de bits à esquerda (repetindo o bit de sinal).

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2063.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2064.png)

    Primeiro invertem-se os bits: `0000...0111 + 1 → 0000...1000 = 8`; como o número original era negativo, o resultado final é **-8**.

### Formatos das instruções

As instruções são mantidas no computador como uma série de sinais eletrônicos, que podem ser representados como números — cada parte da instrução pode ser considerada um número individual. Cada registrador é mapeado e possui um número específico (de 0 a 31):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2065.png)

O MIPS define cinco formatos principais de instrução:

**Instruções tipo R** (registrador):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2066.png)

| Campo | Significado |
|---|---|
| `op` | *Opcode* (código da operação); pode ser `000000` para operações aritméticas. |
| `rs` | Registrador que contém o 1º operando fonte (*register source 1*). |
| `rt` | Registrador que contém o 2º operando fonte (*register target*, *register source 2*). |
| `rd` | Registrador destino, que recebe o resultado (*register destination*). |
| `shamt` | Campo usado em operações de deslocamento de bits, como `sll` e `srl` (*shift amount*). |
| `funct` | Especifica a operação exata a ser realizada, usado em conjunto com o `opcode` (*function code*). |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2067.png)

**Instruções tipo I** (imediato):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2068.png)

| Campo | Significado |
|---|---|
| `op` | *Opcode* da operação. |
| `rs` | Registrador que contém o 1º operando fonte. |
| `rt` | Registrador que contém o 2º operando — aqui, o registrador de destino (*register target*, *register destination*). |
| `constant`/`immediate` | Valor numérico literal embutido diretamente na instrução, usado como operando. |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2069.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2070.png)

**Instruções tipo J** (jump):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2071.png)

| Campo | Significado |
|---|---|
| `op` | *Opcode* da operação. |
| `pseudo-address`/`address` | Endereço relativo ao destino de uma instrução de salto. |

**Instruções tipo FR e FI** — análogas às instruções tipo R e I, respectivamente, mas voltadas para operações de ponto flutuante:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2072.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2073.png)

!!! note
    Todos os formatos de instrução do MIPS possuem a **mesma quantidade total de bits** (32 bits), apenas organizados de formas diferentes nos campos internos — o que, como visto na seção de pipeline, simplifica bastante o hardware de busca e decodificação.

### Operações lógicas

As operações lógicas permitem a manipulação bit a bit dos dados:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2074.png)

**Operações de deslocamento (shifts)** afetam a localização dos bits em um dado, permitindo deslocá-los para a direita ou para a esquerda:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2075.png)

- Deslocar `i` bits para a **esquerda** é equivalente a multiplicar o valor por `2^i`.
- Deslocar `i` bits para a **direita** é equivalente a dividir o valor por `2^i`.

**Outras operações lógicas** incluem `and`, `andi`, `or`, `ori`, `nor`, `xor`, `xori`. Para simplificar o conjunto de instruções, o MIPS não implementa um `not` dedicado — basta fazer `A nor $zero`, que produz o mesmo resultado.

### Controle de fluxo

- **Condicionais** (`beq`, `bne`, `bgt`, `bge`) — são instruções do tipo I, em que a constante é um endereço de deslocamento. Esse deslocamento é aplicado ao program counter: se a condição é verdadeira, o PC passa a guardar o endereço do deslocamento × 4, somado ao próprio valor atual do PC.
- **Loop** (`j`) — acompanhado de um endereço de destino, permite realizar loops ou saltos para outras labels.
- **Comparativos** (`slt`, *set less than*) — testa se um valor é menor que outro, retornando 0 ou 1.
- **Controle de procedimentos** (`jr` e `jal`):
    - **`jal`** (*jump and link*) — usado para chamadas de função (procedimento/sub-rotina). Salta para um endereço específico e salva o endereço de retorno (o endereço imediatamente após a instrução `jal`) no registrador `$ra` (*return address*). Há uma convenção de que os registradores `$a0`–`$a3` são usados como parâmetros, e os registradores `$v0` e `$v1` são usados como valores de retorno. Como os argumentos disponíveis em registradores são limitados, argumentos adicionais precisam ser armazenados na pilha, usando `$sp`:

        ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2076.png)

        !!! example
            ```nasm
            exemplo: #label do procedimento
            	addi $sp, $sp, –12 ; ajusta o sp para empilhar 3 palavras
            	sw $t1, 8($sp) ; salva o reg. $t1 na pilha
            	sw $t0, 4($sp) ; salva o reg. $t0 na pilha
            	sw $s0, 0($sp) ; salva o reg. $s0 na pilha

            	; corpo do procedimento
            	add $t0,$a0,$a1 ; register $t0 contém g + h
            	add $t1,$a2,$a3 ; register $t1 contém i + j
            	sub $s0,$t0,$t1 ; f = $t0 – $t1, (g + h)–(i + j)

            	; coloca o valor de retorno do proc. no reg. $v0
            	add $v0,$s0,$zero ; returns f ($v0 = $s0 + 0)

            	; restaurar os valores dos registradores salvos na pilha
            	lw $s0, 0($sp) ; restaura o $s0
            	lw $t0, 4($sp) ; restaura o $t0
            	lw $s1, 8($sp) ; restaura o $s1
            	add $sp,$sp,12 ; atualiza o sp (pop três palavras)

            	; retorna
            	jr $ra
            ```

    - **`jr`** (*jump register*) — realiza um salto baseado no valor contido em um registrador. Normalmente usada para retornar de chamadas de funções e para simular `switch`-`case` (funcionalidade de controle de fluxo).

        !!! example "Simulando switch-case com jr"
            ```nasm
            .data
            	jTable: .word L0,L1,L2,L3 ; tabela de Labels

            .text
            	la $t4, jTable ; $t4 = endereço base da tabela de desvios
            	; Definindo as variáveis
            	li $s1, 15 ; g = $s1 = 15
            	li $s2, 20 ; h = $s2 = 20
            	li $s3, 10 ; i = $s3 = 10
            	li $s4, 5 ; j = $s4 = 5
            	li $s5, 2 ; k = $s5 = 2 supondo que k é igual a 2

            	;testa se o valor de k está entre 0 e 3.
            	slt $t3,$s5,$zero ; teste se k < 0
            	bne $t3,$zero,Exit ; se k < 0 vá para Exit
            	slti $st3, $s5, 4 ; teste se k < 4
            	beq $t3,$zero,Exit ; se k>3 vá para Exit

            	; Calculando o endereço correto do Label
            	sll $t1, $s5, 2 ; calcula o shift (em bytes) p/ o end. base da tabela de end.
            	add $t1, $t1, $t4 ; $t1 será o endereço do label 2 na jTable
            	lw $t0, 0($t1) ; $t0 é onde está o label desejado $t0 = tabela[k]
            	jr $t0 ; desvia com base no conteúdo de $t0 (selecao do label)

            	L0: add $s0, $s3, $s4 ; Se K = 0 então f = i + j
            	j EXIT ; fim deste case, desvia para EXIT
            	L1: add $s0, $s1, $s2 ; Se K = 1 então f = g + h
            	j EXIT ; fim deste case, desvia para EXIT
            	L2: sub $s0, $s1, $s2 ; Se K = 2 então f = g - h
            	j EXIT ; fim deste case, desvia para EXIT
            	L3: sub $s0, $s3, $s4 ; Se K = 3 então f = i – j
            	EXIT: ; sai do switch
            ```

#### Suporte a procedimentos

Existe um problema chamado ***register spilling***, que ocorre quando o número de registradores de um processador é insuficiente para armazenar todas as variáveis de um programa em execução. Quando isso acontece, algumas variáveis precisam ser armazenadas na memória (normalmente na pilha), o que é muito mais lento do que acessar registradores.

Para evitar esse problema, usa-se a convenção de que os **registradores temporários** `$t0`–`$t9` guardam valores temporários e podem ser usados livremente, enquanto os **registradores salvos** `$s0`–`$s7` devem guardar constantes ou valores importantes que precisam ser preservados ao longo de um procedimento. Também é fundamental reutilizar sempre que possível os registradores temporários; os registradores salvos podem ser mantidos na pilha, ou simplesmente não alterados.

Nesse contexto, existe o conceito de ***program working set* (PW)**: o subconjunto de dados e variáveis que estão sendo ativamente utilizados por um programa em um dado momento. O PW é essencial porque um PW pequeno significa que menos registradores estão sendo utilizados simultaneamente; além disso, manter um PW estável e previsível ajuda o compilador a antecipar melhor o uso de registradores.

#### Procedimentos aninhados

É preciso ter cuidado com a sobrescrita de valores de registradores — especialmente o `$ra` — quando um procedimento chama outro. Para isso, é necessário colocar na pilha os valores de todos os registradores importantes, de forma que, ao retornar de um procedimento secundário, os valores corretos possam ser recuperados.

!!! example "Fatorial recursivo"
    ```nasm
    fatorial:

    	; Primeiro salva $ra e $a0 na pilha
    	addi $sp, $sp, –8 ; ajusta a pilha para 2 itens
    	sw $ra, 4($sp) ; save o end. retorno na pilha
    	sw $a0, 0($sp) ; salva o argmento n ($a0) na pilha

    	; testa caso básico (n<1)
    	slti $t0,$a0,1 ; testa se n < 1
    	beq $t0,$zero,L1 ; se n >= 1, desvia para L1

    	; se n<1, fatorial coloca 1 em $v0 , atualiza a pilha e retorna
    	addi $v0,$zero,1 ; retorna 1
    	addi $sp,$sp,8 ; retira 2 itens da pilha
    	jr $ra ; return para quem chamou

    	; quando n>=1
    	L1: addi $a0,$a0,–1 ; n >= 1: argument gets (n – 1)
    	jal fatorial ; chama fatorial com (n –1)

    	; Fatorial retorna: restaurar os antigos valores de $a0 e $ra
    	lw $a0, 0($sp) ; restaura o argumento n ($a0)
    	lw $ra, 4($sp) ; restaura o end. retorno $ra
    	addi $sp, $sp, 8 ; ajusta o sp (retirada de 2 itens)

    	; novo valor de $v0 = $a0 * $v0
    	mul $v0,$a0,$v0 ; retorna * fact (n – 1)

    	; return a quem chamou o procedimento
    	jr $ra
    ```

### Sincronização

É preciso que dois ou mais processadores estejam sincronizados a fim de evitar **condições de corrida** e garantir que apenas um processador acesse uma região da memória por vez. Condições de corrida ocorrem quando dois processadores (ou threads) tentam acessar e modificar a mesma região de memória sem coordenação — por exemplo, P1 escreve na memória enquanto P2 tenta ler o mesmo endereço simultaneamente. Para garantir a sincronização, é preciso implementar e usar **operações atômicas**, que não podem ser interrompidas por outros processadores.

O MIPS oferece as instruções `ll` (*load linked*) e `sc` (*store conditional*) para esse fim:

- **`ll rt, offset(rs)`** — lê o valor da memória no endereço `offset + rs` e indica que será feita uma operação atômica com esse valor, marcando o endereço como monitorado.
- **`sc rt, offset(rs)`** — tenta armazenar um valor em um endereço monitorado anteriormente por um `ll`. O armazenamento só é bem-sucedido se nenhum outro processador tiver modificado o endereço monitorado desde o `ll`; retorna 1 se a operação foi bem-sucedida, e 0 caso tenha falhado (outro processador já acessou/modificou o endereço).

!!! example
    Se fizermos `ll $s0, 0($t1)`, outro processador modificar o endereço monitorado, e então tentarmos `sc $s1, 0($t1)`, a operação retornará `0`. Se nada tiver modificado o endereço, dependendo de como o monitoramento de hardware é gerenciado, pode retornar 0 ou 1.

Utilizando essas instruções, é possível implementar o **swap atômico** — uma operação muito utilizada em sistemas de multiprocessamento para trocar o conteúdo de um endereço de memória compartilhada por um valor em um registrador, de forma atômica. Essa operação é importante para evitar condições de corrida: basicamente, uma troca de valores entre memória e registrador, sem interrupções, de forma que nenhum outro processador ou thread possa interferir entre as etapas de carregar, verificar e armazenar.

!!! example "Swap atômico"
    ```nasm
    try:
        add $t0, $zero, $s4   ; Coloca o valor a ser escrito em $t0
        ll $t1, 0($s1)        ; Load Linked: carrega Mem[$s1] em $t1
        sc $t0, 0($s1)        ; Store Conditional: tenta armazenar $t0 em Mem[$s1]
        beq $t0, $zero, try   ; Se falhou (sc retorna 0), tenta novamente
        add $s4, $zero, $t1   ; Move o valor antigo de Mem[$s1] para $s4
    ```

### Tradução e inicialização

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2077.png)

### Processador

#### Datapath

O **datapath** é a representação funcional que mostra como os dados fluem e são processados dentro da CPU, de acordo com cada instrução. É composto por dois tipos de elementos:

- **Elementos combinacionais** — como portas AND, somadores, a ALU, multiplexadores etc. Processam dados sem armazenar informação entre ciclos de clock.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2078.png)

- **Elementos sequenciais/de estado** — como registradores, memória, o PC etc. Armazenam valores entre ciclos de clock.

O clock define quando o sinal pode ser lido e escrito.

##### Datapath completo (ciclo único)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2079.png)

O datapath possui memórias de instrução e de dados **separadas**, pois o processador opera em um único ciclo e não pode usar uma memória de porta única para dois acessos simultâneos dentro do mesmo ciclo. O bloco *shift left 2* serve para multiplicar um valor por 4, necessário para calcular endereços de branch corretamente (`beq`, `bne`). O bloco *registers* é usado para armazenar e recuperar valores necessários para cálculos e manipulação de dados — ou seja, para instruções R e I, que usam registradores e valores imediatos/controle de fluxo.

##### Controle da ALU

A ALU lida com as instruções `lw`, `sw`, `beq`, `add`, `sub`, `and`, `or`, `nor`, `slt` e `j` (o `j` é visto em mais detalhe depois; o restante desta seção vale sobretudo para as demais). Dependendo da classe da instrução, a ALU é usada para operações diferentes:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2080.png)

A ALU recebe como entrada um sinal de 4 bits chamado **ALUControl**, que indica qual operação será executada. Esse sinal é gerado por uma pequena unidade de controle (a **ALU Control Unit**, ou **ALU Decoder**), que recebe como entradas o campo `funct` da instrução e o **ALUOp** (um campo de controle de 2 bits, produzido pela unidade de controle principal, cujo valor depende do tipo de instrução recebida):

| ALUOp | Instrução | Operação |
|---|---|---|
| `00` | `lw`, `sw` | add |
| `01` | `beq` | sub |
| `10` | Instrução tipo R | Depende do `funct` |
| `11` | Operação personalizada | Depende da arquitetura |

A saída dessa unidade de controle (o ALU Decoder) é justamente o **ALUControl**:

| ALUControl | Instrução |
|---|---|
| `0000` | and |
| `0001` | or |
| `0010` | add |
| `0110` | sub |
| `0111` | slt |
| `1100` | nor |

A tabela completa dos sinais relevantes é:

| Instrução | ALUOp | funct | Ação desejada da ALU | ALUControl |
|---|---|---|---|---|
| `lw` | 00 | XXXXXX | add | 0010 |
| `sw` | 00 | XXXXXX | add | 0010 |
| `beq` | 01 | XXXXXX | sub | 0110 |
| `add` | 10 | 100000 | add | 0010 |
| `sub` | 10 | 100010 | sub | 0110 |
| `and` | 10 | 100100 | and | 0000 |
| `or` | 10 | 100101 | or | 0001 |
| `slt` | 10 | 101010 | slt | 0111 |
| `nor` | 10 | 100111 | nor | 1100 |

O caminho completo de sinais até a ALU é:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2081.png)

##### Unidade de Controle

A **Unidade de Controle** gera todos os sinais necessários com base no `opcode` da instrução. Esses sinais controlam os fluxos de dados e as operações do processador. Os principais sinais são:

**RegDst** — controla o MUX que seleciona qual registrador será escrito no banco de registradores.

| RegDst | Campo utilizado | Bits | Tipo de instrução |
|---|---|---|---|
| 0 | `rt` | [20:16] | I |
| 1 | `rd` | [15:11] | R |

**Branch** — indica se a instrução é de branch e controla o MUX do PC, determinando se a próxima instrução virá de forma sequencial ou "saltada".

| Branch | Descrição |
|---|---|
| 0 | O PC não é alterado para o endereço de branch. |
| 1 | O PC é alterado para o endereço de branch se o resultado da ALU for Zero. |

!!! note
    O PC só é atualizado quando `ALUResult` é Zero, porque, no `beq`, se `rs` e `rt` forem iguais, então `rs - rd = 0`, já que a ALU implementa o `beq` como uma subtração.

**MemRead** — habilita a leitura de dados da memória de dados.

| MemRead | Tipo de instrução | Descrição |
|---|---|---|
| 0 | Todas, exceto load | Nenhuma leitura na memória é realizada. |
| 1 | Instruções de load | Habilita a leitura da memória de dados. |

**MemtoReg** — controla o MUX que seleciona o valor a ser escrito no banco de registradores.

| MemtoReg | Tipo de instrução | Descrição |
|---|---|---|
| 0 | Tipo R e I (exceto load) | O dado a ser escrito vem da saída da ALU. |
| 1 | Apenas load | O dado a ser escrito vem da memória de dados. |

!!! note
    Instruções tipo J não são consideradas aqui, pois não gravam no banco de registradores valores vindos da memória ou da ALU.

**ALUOp** — define a operação geral da ALU (tabela já vista acima).

**MemWrite** — habilita a escrita de dados na memória de dados.

| MemWrite | Tipo de instrução | Descrição |
|---|---|---|
| 0 | Todas, exceto store | Nenhuma escrita na memória é realizada. |
| 1 | Instruções de store | Habilita a escrita na memória de dados. |

**ALUSrc** — controla o MUX que seleciona a segunda entrada da ALU.

| ALUSrc | Tipo de instrução | Descrição |
|---|---|---|
| 0 | Tipo R e Tipo I (branch) | O segundo operando vem do banco de registradores (campo `rt`). |
| 1 | Tipo I (load/store, imediato) | O segundo operando vem do valor imediato (com extensão de sinal). |

**RegWrite** — habilita a escrita no banco de registradores.

| RegWrite | Tipo de instrução | Descrição | Motivo |
|---|---|---|---|
| 0 | Tipo I (store) | Nenhum registrador é escrito. | Apenas escreve na memória, sem alterar registradores. |
| 0 | Tipo I (branch) | Nenhum registrador é escrito. | Apenas altera o PC, não escreve em registradores. |
| 0 | Tipo J (jump) | Nenhum registrador é escrito. | Apenas altera o PC, não escreve em registradores. |
| 1 | Tipo R | Habilita a escrita no registrador de destino. | O resultado da ALU é gravado no registrador destino. |
| 1 | Tipo I (imediato) | Habilita a escrita no registrador de destino. | O resultado da ALU é gravado no registrador destino. |
| 1 | Tipo I (load) | Habilita a escrita no registrador de destino. | O valor da memória é gravado no registrador destino. |
| 1 | Tipo J (Jump and Link) | Habilita a escrita no registrador de destino. | Escreve o endereço de retorno no registrador `$ra`. |

**Jump** — indica se a instrução é de salto incondicional (`j`) e controla o valor do PC diretamente.

| Jump | Descrição |
|---|---|
| 0 | O PC segue o fluxo normal (somado a 4, ou atualizado por branch). |
| 1 | O PC é alterado para o endereço especificado na instrução `j`. |

Até aqui, estamos considerando que todas as instruções executam em um único ciclo de clock, de tamanho fixo. Isso é ineficiente, pois há instruções bem rápidas que acabam tendo de ser executadas de forma mais lenta, já que o ciclo de clock precisa acomodar as instruções mais demoradas. Essa ineficiência é resolvida pela técnica de **pipeline**.

### Pipeline

**Pipeline** é a técnica em que múltiplas instruções têm sua execução sobreposta no tempo.

!!! example "Sem pipeline x com pipeline"
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2082.png)

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2083.png)

Essa técnica é baseada em **5 estágios**, chamados de ciclos de instrução:

1. **IF** (*Instruction Fetch*) — buscar a instrução na memória.
2. **ID** (*Instruction Decode*) — decodificar a instrução e ler os registradores.
3. **EX** (*Execution*) — executar a operação (na ALU) ou calcular um endereço.
4. **MEM** (*Memory Access*) — acessar o operando na memória, buscando (`lw`) ou armazenando (`sw`).
5. **WB** (*Write Back*) — escrever o resultado de volta no registrador.

#### Desempenho do pipeline

Comparação entre a versão com pipeline e a versão de ciclo único (*single-cycle*):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2084.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2085.png)

Além disso, a própria ISA do MIPS foi **projetada tendo o pipeline em mente**:

- Todas as instruções têm o mesmo tamanho, facilitando o IF e o ID.
- Poucos e regulares formatos de instrução, permitindo decodificar a instrução e ler registradores em um único passo.
- Acesso à memória apenas em operações de load e store, permitindo calcular o endereço no EX e acessar a memória no MEM.
- Alinhamento dos operandos em memória, de forma que o acesso à memória gaste apenas um ciclo.

#### Hazards

**Hazards** são conflitos que impedem o início da próxima instrução no próximo ciclo de clock. Existem três tipos principais.

##### Hazards estruturais

Ocorrem quando duas ou mais instruções já no pipeline precisam do mesmo recurso simultaneamente, gerando uma competição por esse recurso. Para resolver esse problema, é preciso que as memórias de instruções e de dados estejam separadas, permitindo que os estágios de IF e de MEM ocorram ao mesmo tempo. Refere-se, fundamentalmente, a uma limitação do hardware, que não pode buscar instruções ao mesmo tempo que acessa dados na memória — a não ser que existam unidades de memória separadas para cada finalidade.

##### Hazards de dados

Ocorrem quando há um conflito no acesso a um operando, na memória ou em um registrador. Existem três tipos de conflito:

- **Read After Write (RAW)** — ocorre quando uma instrução precisa ler um valor que ainda não foi escrito pela instrução anterior; é uma dependência verdadeira, pois a instrução seguinte tenta ler um registrador antes de o valor correto ter sido escrito. Exemplo: guardar o resultado de um `add` em `$t1` (`add $t1, $t2, $t3`) e precisar dele logo em seguida em um `sub` (`sub $t4, $t1, $t2`).
- **Write After Write (WAW)** — ocorre quando duas instruções tentam escrever no mesmo registrador, e a segunda pode sobrescrever o valor antes que a primeira tenha concluído sua escrita; é uma dependência de escrita, um conflito na ordem de escrita de um registrador. Exemplo: um `mul` seguido de um `add` usando o mesmo registrador de destino (`mul $t1, $t4, $t5; add $t1, $t2, $t3`).
- **Write After Read (WAR)** — ocorre quando uma instrução tenta escrever em um registrador antes que outra instrução termine de lê-lo; é uma dependência de anti-fluxo, um conflito entre leitura e escrita em um registrador. Exemplo: em um `sub` seguido de um `add`, o `add` pode acabar lendo o valor já atualizado pelo `sub` (`sub $t2, $t5, $t6; add $t1, $t2, $t3`).

**Soluções para hazards de dados:**

- **Forwarding (Bypassing)** — em vez de esperar que o dado seja gravado no banco de registradores (no estágio WB), o resultado é encaminhado diretamente da saída da ALU (ou de outro estágio) para onde ele é necessário. Assim, o resultado gerado no estágio EX pela instrução anterior é passado diretamente para o estágio EX da instrução atual. Minimiza *stalls* (atrasos) no pipeline, mas exige conexões extras na unidade de processamento.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2086.png)

- **Stalling (Pipeline Bubble)** — o pipeline é pausado até que o dado necessário esteja disponível, causando um *stall* proposital; uma "bolha" (instrução vazia) é inserida no pipeline para evitar conflitos. Como causa stalls propositais, reduz o throughput (eficiência do pipeline).
- **Reordenação de instruções** — o compilador (ou o próprio processador) rearranja as instruções para evitar dependências diretas entre instruções consecutivas.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2087.png)

    Instruções independentes podem ser executadas entre a instrução produtora e a instrução consumidora do dado. Reduz stalls sem necessidade de hardware adicional.

- **Especulação e execução out-of-order** — em arquiteturas avançadas, o processador pode executar instruções fora de ordem, desde que as dependências sejam respeitadas. Os resultados são armazenados em buffers temporários até poderem ser escritos no registrador de destino. Exige, porém, hardware complexo para controle e *reorder buffers*.

##### Hazards de controle

Ocorrem quando há uma alteração no fluxo de controle do programa, como em instruções de branch ou jump, fazendo com que o processador não saiba qual é o próximo endereço correto do PC até que o branch (ou salto) seja resolvido. Isso ocorre mais especificamente na fase de IF: nesse estágio, o processador busca a próxima instrução com base no valor atual do PC, e, caso a instrução seja de branch ou jump, pode acabar buscando instruções incorretas antes que o branch/jump seja resolvido nos estágios EX ou MEM.

**Soluções para hazards de controle:**

- **Pipeline Stall** — o pipeline é pausado até que o destino do branch seja resolvido. Simples de implementar, mas reduz o desempenho.
- **Branch prediction** — o processador faz uma previsão sobre se o branch será tomado ou não, e continua executando com base nessa previsão. Se a previsão estiver correta, o pipeline continua normalmente; se estiver errada, as instruções incorretas já buscadas são descartadas (*flush*). Existem duas grandes abordagens:
    - **Previsão estática** — aplica uma regra predefinida para decidir se o branch será tomado:
        - **Not taken** — prevê que o desvio não vai acontecer; ocorre stall no pipeline se a predição for incorreta.

            ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2088.png)

        - **Taken** — prevê que o desvio sempre vai acontecer; ocorre stall se a predição for incorreta.
        - **Baseada no tipo de branch** — aplica regras específicas dependendo do tipo: branches "para a frente" têm previsão padrão de não tomado; branches "para trás" têm previsão padrão de tomado — essa regra se justifica por causa de loops, já que branches que apontam para trás geralmente indicam loops, executados várias vezes antes de sair.
    - **Previsão dinâmica** — o processador usa um histórico de execuções anteriores para prever se o branch será tomado; mais eficiente, mas requer hardware adicional.
- **Delay slots** — o compilador insere uma instrução independente imediatamente após o branch, chamada de *delay slot*, que é sempre executada, independentemente de o branch ter sido tomado ou não. Utiliza melhor o pipeline, mas depende de o compilador encontrar instruções úteis para ocupar o *delay slot*.
- **Early branch resolution** — o destino e a condição do branch são calculados mais cedo no pipeline (no estágio ID, em vez do EX), reduzindo o impacto do hazard, mas exigindo mudanças no datapath para calcular o branch já no ID.
- **Predication** — em vez de usar instruções de branch, o processador executa ambas as alternativas (tomado e não tomado) e descarta a incorreta depois que a condição é avaliada. Elimina totalmente o hazard de controle, mas consome mais recursos do processador.

#### Unidade de processamento do MIPS (com pipeline)

Com 5 estágios, até 5 instruções podem estar em execução simultaneamente, durante um único ciclo de clock. Em geral, instruções e dados se movem da esquerda para a direita no datapath — com exceções na fase de WB e na atualização do PC.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2089.png)

Para que essas instruções sejam processadas simultaneamente, é necessária a presença de **registradores de pipeline** entre os estágios, para armazenar informações produzidas no ciclo anterior, de modo a não perdê-las.

**Registradores no pipeline — operações de load e store:**

| Estágio | Load | Store |
|---|---|---|
| IF | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2090.png) | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2090.png) |
| ID | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2091.png) | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2091.png) |
| EX | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2092.png) | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2096.png) |
| MEM | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2093.png) | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2097.png) |
| WB | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2094.png) | ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2098.png) |

Unidade de processamento corrigida para load:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2095.png)

##### Controle do pipeline

É preciso adicionar controle à unidade de processamento com pipeline, configurando os valores de controle em cada estágio:

- **IF e ID** — sinal para leitura do PC e busca de instrução, sempre ativo.
- **EX** — sinais `RegDst`, `ALUOp` e `ALUSrc`.
- **MEM** — sinais `Branch`, `MemRead`, `MemWrite`.
- **WB** — sinais `MemtoReg`, `RegWrite`.

Datapath com controle do pipeline:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%2099.png)

#### Exercícios resolvidos

!!! example "Exercício 1"
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20100.png)

    1. O tempo de ciclo de clock de uma versão sem pipeline é de 1010 ps (soma de todos os estágios), e de uma versão com pipeline é de 400 ps (latência do maior estágio).
    2. A latência total de uma instrução de load, sem pipeline, é de 1010 ps (igual ao tempo de ciclo de clock); com pipeline, é de 2000 ps (400 × 5 estágios).
    3. O estágio a ser dividido seria o de MEM (o de maior latência), passando a ter dois estágios de MEM de 200 ps cada; o novo tempo de ciclo de clock seria de 1200 ps.

!!! example "Exercício 2"
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20101.png)

    1. Dependências: instruções 1 e 3 por `$t1`; 2 e 3 por `$t2`; 3 e 4 por `$t3`; 5 e 6 por `$t4`; 6 e 7 por `$t5`. A instrução 3 depende das instruções 1 e 2; a instrução 4 depende da 3; a instrução 6 depende das 4 e 5; a instrução 7 depende da 6.
    2. Ocorre um stall entre as instruções 1/3 e 2/3, para garantir que os valores de `$t1` e `$t2` estejam corretos (já que a instrução 3 depende dos valores gerados por elas); ocorre um stall entre 3/4, pois a instrução 4 depende do valor da 3; e ocorre um stall entre 5/6, pois a instrução 6 depende do valor da 5.
    3. Reordenando as instruções para evitar os stalls:

        ```nasm
        lw $t1, 0($t0)
        lw $t2, 4($t0)
        lw $t4, 12($t0)
        add $t3, $t1, $t2
        sw $t3, 8($t0)
        add $t5, $t3, $t4
        sw $t5, 16($t0)
        ```

#### Detalhando hazards de dados

Utilizando a técnica de *forwarding*, surge a pergunta: como detectar quando é necessário adiantar dados, em instruções que usam a ALU? A ALU é responsável por produzir resultados no estágio EX.

**Classificando as dependências:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20102.png)

Deve-se adiantar dados apenas das instruções que irão de fato escrever em um registrador — examinando se o sinal `RegWrite` está ativo:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20103.png)

Além disso, só se deve adiantar o dado se o `rd` da instrução anterior não for `$zero`. Para implementar o adiantamento, é necessário um MUX e sinais de controle que selecionem entre os valores do banco de registradores e os valores já adiantados.

**Especificando os sinais de controle:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20104.png)

**Condições:**

- **Hazard em EX:**

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20105.png)

- **Hazard em MEM:**

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20106.png)

**Hazard duplo:** é importante notar que há situações em que os dois hazards (EX e MEM) acontecem ao mesmo tempo:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20107.png)

Por causa disso, a condição do hazard em MEM precisa ser alterada.

**Condições atualizadas:**

- Hazard em EX (inalterado):

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20105.png)

- Hazard em MEM (atualizado):

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20108.png)

**Datapath — sem e com adiantamento:**

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20109.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20110.png)

Unidade de processamento completa, com forwarding:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20111.png)

##### Hazard load-use

Nem sempre o *forwarding* resolve todos os hazards:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20112.png)

Um caso em que o forwarding **não** resolve é o **hazard load-use**, que ocorre quando uma instrução tenta usar imediatamente o dado que está sendo carregado da memória por um `lw` anterior (ou seja, um `lw` seguido imediatamente de uma instrução que usa o registrador carregado):

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20113.png)

Para resolver esse hazard, é preciso criar uma **unidade de detecção de hazard**, que verifica se o tipo do hazard é load-use — caso seja, insere um stall (uma bolha) entre o load e a instrução que o usa.

**Stall no pipeline:** para realizar o stall, primeiro é preciso identificá-lo no estágio de ID. Caso positivo, forçam-se os valores do sinal de controle no registrador ID/EX para zero — com isso, os estágios de EX, MEM e WB executam uma instrução `nop` (*no-operation*), e os sinais se propagam para os demais registradores de pipeline, efetivando o stall. Apesar de reduzir o desempenho, stalls são necessários para garantir resultados corretos.

Unidade de processamento completa, com forwarding e detecção de hazard:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20114.png)

#### Detalhando hazards de controle

Entre as estratégias para solucionar hazards de controle, a menos custosa e mais eficiente no pior caso é a de *branch prediction* usando previsão **dinâmica**. Para implementá-la, é preciso de um **buffer de predição de desvio**: uma pequena área de memória indexada pela porção baixa do endereço da instrução de branch, contendo um bit que indica se o desvio ocorreu recentemente. Se a predição estiver incorreta, as instruções preditas são descartadas (*flush*) e os bits do buffer são atualizados.

**Preditor de 1 bit** — histórico curto; pode errar a predição duas vezes consecutivas em certos cenários (por exemplo: o preditor tem o bit em 0, apostando que o desvio não será tomado na última iteração de um loop — o que não acontece, atualizando o bit para 1; na próxima vez que o loop é executado, o preditor erra novamente, de forma simétrica, em sua primeira e última iteração).

**Preditor de 2 bits** — só muda a previsão quando ocorrem 2 erros consecutivos, sendo mais resiliente a esse tipo de oscilação:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20115.png)

!!! example "Exercício"
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20116.png)

    Para o primeiro desvio, o ideal é seguir a abordagem *branch not taken*, pois com ela só se erra em 5% dos casos. Para o segundo desvio, o ideal é a abordagem *branch taken*, também errando apenas 5% dos casos. Para o último desvio, o ideal é a predição dinâmica, errando apenas 10% dos casos — enquanto *branch not taken* erraria 70% e *branch taken* erraria 30%.

#### Exceções

**Exceções** são eventos inesperados que exigem uma mudança no fluxo de execução das instruções — e são tratadas como mais uma forma de hazard de controle. Podem ser internas (opcode inválido, overflow, `syscall` etc.) ou externas — as **interrupções**, originadas por um dispositivo de E/S externo.

**Manipulação de exceções sem afetar o desempenho.** Quando uma exceção ocorre, é preciso:

1. Salvar o endereço da instrução que gerou a exceção no registrador **Exception Program Counter (EPC)**.
2. Salvar a indicação do problema no **registrador de causa** (*cause register*) — por exemplo, 10 para opcode inválido, 12 para overflow etc.
3. Pular para a rotina de tratamento (*handler*, que diagnostica, trata e resolve o problema) no endereço `0x80000180`. Esse endereço específico é pré-definido como ponto de entrada para o tratamento de exceções em **modo kernel**.

!!! note "Modo kernel"
    É um dos modos de operação de um processador, que oferece acesso completo e irrestrito aos recursos do hardware que podem afetar a integridade do sistema. É usado para realizar tarefas críticas, como gerenciar dispositivos de hardware, memória e outros recursos essenciais. Na arquitetura do processador, existe um bit de modo em um registrador especial que controla esse comportamento: valor 0 para modo kernel e valor 1 para modo usuário.

Como alternativa a um único endereço fixo, pode-se usar um **vetor de interrupções** — uma tabela de endereços que indica onde estão localizadas as rotinas de tratamento para diferentes interrupções ou exceções:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20117.png)

Para realizar o *flush* ao tratar exceções, são adotados novos sinais de controle:

- **`IF.flush`** — limpa as instruções no estágio IF.
- **`ID.flush`** — limpa as instruções no estágio ID (ou integra-se com a unidade de detecção de hazard).
- **`EX.flush`** — limpa as instruções no estágio EX, prevenindo que a instrução ali presente escreva seu resultado no estágio WB (via uma entrada no MUX que zera os sinais de controle).

Além disso, é preciso salvar os valores do registrador de causa e do EPC, e transferir o controle para a rotina de tratamento por meio de um novo MUX no PC, com uma das entradas sendo `0x80000180`.

Datapath com suporte a exceções:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20118.png)

#### Paralelismo a nível de instrução (ILP)

**ILP** é a capacidade do processador de executar múltiplas instruções ao mesmo tempo, aproveitando a sobreposição de tarefas do pipeline. Existem duas formas principais de aumentar o ILP:

1. **Pipeline mais profundo** — mais estágios, com menos trabalho por estágio e, consequentemente, menor ciclo de clock.
2. **Múltipla emissão (*Multiple Issue*)** — o processador é projetado para emitir várias instruções por ciclo de clock (em vez de apenas uma), por meio da replicação de componentes internos (várias ALUs, unidades de memória etc.), permitindo que várias instruções sejam iniciadas simultaneamente.

Nessa segunda abordagem, surge a métrica **IPC** (*Instructions Per Cycle*), que mede a eficiência média de instruções por ciclo de clock — o inverso do CPI. Por exemplo, `CPI = 0,25` significa `IPC = 4`.

Existem duas formas de múltipla emissão:

- **Múltipla emissão estática** — o compilador agrupa instruções para serem emitidas juntas, empacotando-as em "lotes" de emissão, e já detecta e evita hazards em tempo de compilação.
- **Múltipla emissão dinâmica (superescalar)** — a própria CPU examina o fluxo de instruções em tempo de execução e escolhe quais emitir em cada ciclo; o compilador ainda pode ajudar reorganizando as instruções, mas a CPU resolve os hazards com técnicas avançadas em tempo de execução.

---

## Hierarquia da memória

### Motivação

Idealmente, gostaríamos de uma memória **ilimitada e extremamente rápida**, capaz de armazenar todos os dados e programas necessários e de fornecê-los à CPU na mesma velocidade com que ela os processa. Na prática, essa memória ideal não existe: memórias rápidas (como SRAM) são caras e pequenas, enquanto memórias grandes e baratas (como discos) são lentas. Essa diferença de desempenho entre a CPU e a memória principal só tende a aumentar, já que a velocidade dos processadores cresce mais rápido do que a velocidade de acesso à memória.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20119.png)

A solução adotada é organizar a memória em uma **hierarquia**: níveis sucessivos de memória, cada um menor, mais rápido e mais caro por byte do que o nível abaixo dele, e maior, mais lento e mais barato do que o nível acima. O objetivo é apresentar ao usuário a maior quantidade de memória possível ao custo da tecnologia mais barata, operando na velocidade oferecida pela tecnologia mais rápida.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20120.png)

### Princípio da localidade

Essa hierarquia só funciona bem na prática por causa do **princípio da localidade**: programas, na maioria do tempo, acessam uma porção relativamente pequena do seu espaço de endereçamento. Existem dois tipos de localidade:

- **Localidade temporal** — se um item de dado é referenciado, é provável que ele seja referenciado novamente em breve (por exemplo, dados usados em um loop).
- **Localidade espacial** — se um item de dado é referenciado, é provável que itens cujos endereços estejam próximos a ele também sejam referenciados em breve (por exemplo, elementos sucessivos de um array).

Graças a esse princípio, é possível manter os dados mais usados recentemente (e os dados vizinhos a eles) nos níveis mais rápidos e menores da hierarquia, mantendo o restante nos níveis mais lentos e maiores — sem perder desempenho na maior parte do tempo.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20121.png)

### Cache

**Cache** é o termo genérico usado para o primeiro nível da hierarquia de memória visto pela CPU, aproveitando o princípio da localidade.

#### Acessando a cache

Quando ocorre um acesso à memória, a cache é consultada primeiro:

- **Hit (acerto)** — o dado solicitado está presente na cache.
- **Miss (falta)** — o dado solicitado não está na cache, e precisa ser buscado em um nível inferior da hierarquia (memória principal, por exemplo), o que causa um atraso (*stall*) no pipeline enquanto o dado é buscado.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20122.png)

A forma mais simples de organizar uma cache é o **mapeamento direto**, em que cada endereço de memória é mapeado para exatamente uma posição (linha) da cache, calculada como `(endereço do bloco) mod (número de linhas da cache)`.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20123.png)

Como vários endereços de memória podem ser mapeados para a mesma linha da cache, é preciso de alguma forma identificar **qual** bloco de memória está armazenado em cada linha. Isso é feito por meio de uma **tag** (etiqueta), que registra a porção do endereço que não é usada para indexar a linha, junto de um bit de **válido** (*valid bit*), que indica se aquela linha contém ou não um dado válido (inicialmente todas as linhas são inválidas).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20124.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20125.png)

#### Tratando misses de cache

Quando ocorre um miss, o controle da CPU precisa:

1. Detectar o miss.
2. Buscar o bloco correspondente na memória principal (ou no próximo nível da hierarquia).
3. Armazenar o bloco na cache, atualizando os bits de tag e válido.
4. Reiniciar a instrução que causou o miss, que agora irá encontrar o dado como um hit.

#### Tratando escritas (write)

Quando a CPU precisa escrever um dado, existem duas políticas principais:

- **Write-through** — a escrita é feita simultaneamente na cache e na memória principal. É mais simples de implementar e mantém a consistência entre cache e memória, mas é mais lenta, pois toda escrita exige acesso à memória principal.
- **Write-back** — a escrita é feita apenas na cache, e o dado só é propagado para a memória principal quando o bloco correspondente é substituído (removido da cache). É mais rápida, mas exige um bit extra, chamado **dirty bit** (bit de sujeira), que indica se o bloco foi modificado desde que foi carregado — apenas blocos "sujos" precisam ser escritos de volta na memória ao serem substituídos.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20126.png)

### Desempenho da cache

O desempenho da cache é medido, principalmente, pelo **tempo médio de acesso à memória**, conhecido como **AMAT** (*Average Memory Access Time*):

$$AMAT = \text{Tempo de acerto} + \text{Taxa de falta} \times \text{Penalidade de falta}$$

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20127.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20128.png)

Para reduzir o AMAT, pode-se reduzir o tempo de acerto, reduzir a taxa de falta ou reduzir a penalidade de falta. Um dos fatores que afeta diretamente a taxa de falta é o **tamanho do bloco** da cache: blocos maiores aproveitam melhor a localidade espacial e reduzem a taxa de falta, até certo ponto — blocos excessivamente grandes aumentam a penalidade de falta (já que mais dados precisam ser transferidos da memória) e podem até aumentar a taxa de falta, por reduzirem o número total de blocos que cabem na cache.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20129.png)

### Mapeamento associativo

Além do mapeamento direto, existem outras formas de organizar uma cache, que reduzem a taxa de falta ao custo de maior complexidade de hardware:

- **Totalmente associativa** — qualquer bloco de memória pode ser armazenado em qualquer linha da cache. Reduz bastante a taxa de falta, mas exige comparar a tag de todas as linhas simultaneamente, o que é caro em hardware (geralmente inviável para caches grandes).
- **Associativa por conjuntos (*set-associative*)** — um meio-termo entre o mapeamento direto e o totalmente associativo: a cache é dividida em conjuntos, e cada bloco de memória pode ser armazenado em qualquer linha dentro de um conjunto específico (determinado por `(endereço do bloco) mod (número de conjuntos)`). Uma cache com `n` linhas por conjunto é chamada de **n-way set-associative**.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20130.png)

| Associatividade | Taxa de falta | Complexidade de hardware | Tempo de acerto |
|---|---|---|---|
| Mapeamento direto (1-way) | Maior | Menor | Menor |
| *n*-way set-associative | Intermediária | Intermediária | Intermediária |
| Totalmente associativa | Menor | Maior | Maior |

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20131.png)

#### Políticas de substituição

Quando uma cache associativa (seja por conjuntos ou totalmente associativa) precisa substituir um bloco e todas as linhas disponíveis já estão ocupadas, uma política de substituição decide qual bloco será removido. A mais comum é a **LRU** (*Least Recently Used*), que remove o bloco que não foi acessado há mais tempo, aproveitando a localidade temporal.

### Caches multinível

Como qualquer melhora em desempenho tem um custo associado, é comum utilizar uma hierarquia de **múltiplos níveis de cache** (L1, L2, L3), em vez de apenas um — buscando um equilíbrio entre velocidade (caches L1 pequenas e rápidas, muito próximas da CPU) e capacidade (caches L2/L3 maiores, um pouco mais lentas, que reduzem a penalidade de ir direto à memória principal em caso de miss na L1).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20132.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20133.png)

### Memória virtual

**Memória virtual** é uma técnica que permite a múltiplos programas compartilharem a memória principal de forma segura, dando a cada processo a ilusão de possuir seu próprio espaço de endereçamento contíguo e privado — mesmo que, na prática, a memória física seja compartilhada e fragmentada entre vários processos. Além disso, permite que programas usem mais memória do que a quantidade de RAM efetivamente disponível, utilizando o disco como extensão.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20134.png)

#### Paginação

A técnica mais comum de implementar memória virtual é a **paginação**: o espaço de endereçamento virtual de cada processo é dividido em blocos de tamanho fixo chamados **páginas**, e a memória física é dividida em blocos do mesmo tamanho chamados **frames** (ou molduras). Uma **tabela de páginas** mantém o mapeamento de cada página virtual para seu frame físico correspondente (ou indica que a página não está presente na memória física, apenas no disco).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20135.png)

Quando um processo tenta acessar uma página que não está na memória física, ocorre uma **falta de página** (*page fault*), e o sistema operacional precisa buscar essa página no disco, possivelmente removendo outra página da memória física para abrir espaço (usando políticas de substituição semelhantes às de cache, como LRU).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20136.png)

#### TLB (Translation Lookaside Buffer)

Como a tradução de endereços virtuais para físicos, via tabela de páginas, ocorre a cada acesso à memória, ela se tornaria um gargalo de desempenho caso precisasse consultar a tabela de páginas (que fica na própria memória) a cada acesso. Para evitar isso, utiliza-se a **TLB**, uma cache especializada que armazena as traduções de endereço mais usadas recentemente, acelerando bastante o processo de tradução na maioria dos acessos.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20137.png)

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20138.png)

### Resumo da hierarquia de memória

A hierarquia de memória completa, do nível mais rápido/menor ao mais lento/maior, costuma ser: registradores → cache L1 → cache L2/L3 → memória principal (RAM) → memória virtual/disco. Cada nível funciona como uma "cache" do nível seguinte, aproveitando o princípio da localidade para manter o desempenho percebido próximo ao do nível mais rápido, com o custo e a capacidade do nível mais barato.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20139.png)

---

## Processadores Paralelos

### Motivação

Por muitos anos, o aumento de desempenho dos processadores veio principalmente do aumento da frequência de clock e de técnicas de paralelismo a nível de instrução (ILP, vistas na seção de pipeline). Porém, esse caminho encontrou limites físicos — sobretudo relacionados à dissipação de calor e ao consumo de energia (a potência cresce proporcionalmente ao cubo da frequência, aproximadamente). A resposta da indústria foi migrar para o **paralelismo em nível de processos/threads**, colocando múltiplos núcleos de processamento (*cores*) dentro do mesmo chip, dando origem aos processadores **multicore**.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20140.png)

Esse tipo de paralelismo é bem diferente do paralelismo de instrução: ele exige que o próprio software seja escrito (ou adaptado) para se beneficiar de múltiplos fluxos de execução simultâneos, dividindo o trabalho entre eles.

### Taxonomia de Flynn

A **Taxonomia de Flynn** classifica arquiteturas de computadores paralelos de acordo com o número de fluxos de instruções e de dados que podem ser processados simultaneamente:

| Categoria | Significado | Descrição | Exemplo |
|---|---|---|---|
| **SISD** | *Single Instruction, Single Data* | Arquitetura sequencial tradicional, sem paralelismo explícito. | Processador uniprocessado clássico. |
| **SIMD** | *Single Instruction, Multiple Data* | Uma mesma instrução é aplicada simultaneamente a múltiplos dados. | Unidades vetoriais, GPUs. |
| **MISD** | *Multiple Instruction, Single Data* | Múltiplas instruções processam o mesmo fluxo de dados. Pouco usada na prática. | Sistemas tolerantes a falhas (redundância). |
| **MIMD** | *Multiple Instruction, Multiple Data* | Múltiplos processadores executam instruções diferentes sobre dados diferentes, de forma independente. | Multiprocessadores, multicomputadores, clusters. |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20141.png)

A categoria **MIMD** é a mais flexível e a mais usada atualmente nos processadores multicore e em sistemas distribuídos, já que cada núcleo pode executar um programa (ou parte de um programa) completamente diferente dos demais.

### Multiprocessadores com memória compartilhada (SMP)

Um **multiprocessador simétrico (SMP)** é composto por múltiplos processadores que compartilham um único espaço de endereçamento de memória física, acessível por todos eles igualmente.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20142.png)

Essa organização simplifica a programação (todos os núcleos "veem" os mesmos dados), mas cria um problema importante: a **coerência de cache**.

#### Coerência de cache

Como cada processador possui sua própria cache privada (ou conjunto de caches), é possível que diferentes processadores tenham, em um dado momento, cópias **diferentes** do mesmo endereço de memória em suas respectivas caches — gerando inconsistências se um processador modificar seu valor local sem que os demais sejam avisados.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20143.png)

!!! warning "Problema da coerência de cache"
    Sem um mecanismo de coerência, um processador pode continuar lendo um valor "antigo" (obsoleto) de sua cache local, mesmo depois que outro processador já tenha atualizado o valor correspondente na memória principal.

Um protocolo de coerência de cache precisa garantir, essencialmente, duas propriedades:

- **Propagação de escrita** — mudanças feitas por um processador precisam eventualmente ser visíveis aos demais.
- **Serialização de escritas** — todos os processadores devem ver as escritas na mesma ordem (um valor não pode "retroceder" para um processador e "avançar" para outro).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20144.png)

**Abordagens para manter a coerência:**

- **Protocolos de espionagem (*snooping*)** — cada cache "escuta" o barramento compartilhado, monitorando as transações de memória realizadas pelas demais caches, de forma a invalidar ou atualizar suas próprias cópias quando necessário. Funciona bem para sistemas com um número pequeno/moderado de processadores conectados por um barramento compartilhado.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20145.png)

- **Protocolos baseados em diretório** — um diretório centralizado (ou distribuído) mantém o estado de cada bloco de memória e sabe exatamente quais caches possuem cópias dele, evitando a necessidade de transmitir (*broadcast*) todas as transações para todos os processadores. Escala melhor para sistemas com muitos processadores.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20146.png)

##### Protocolo MESI

Um dos protocolos de coerência mais usados é o **MESI**, baseado em espionagem, que atribui a cada linha de cache um dos quatro estados:

| Estado | Significado |
|---|---|
| **M**odified | O bloco foi modificado nesta cache e está desatualizado na memória principal e nas demais caches; esta cache é a única com a cópia válida. |
| **E**xclusive | O bloco está presente apenas nesta cache (nenhuma outra cache possui uma cópia), e está atualizado em relação à memória principal. |
| **S**hared | O bloco pode estar presente em múltiplas caches simultaneamente, e todas as cópias estão atualizadas em relação à memória principal. |
| **I**nvalid | O bloco não contém dados válidos nesta cache (precisa ser buscado de outro nível). |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20147.png)

### Multiprocessadores com memória distribuída

Em vez de compartilhar um único espaço de memória física, cada processador (ou grupo de processadores) possui sua própria memória local, e a comunicação entre eles ocorre por meio de troca explícita de mensagens pela rede.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20148.png)

**NUMA** (*Non-Uniform Memory Access*) é uma organização intermediária, em que a memória é fisicamente distribuída entre os processadores, mas logicamente compartilhada — ou seja, qualquer processador pode acessar qualquer região de memória, mas o tempo de acesso varia dependendo de quão "próxima" (fisicamente) aquela região está do processador que faz a requisição (acessar a memória local é mais rápido do que acessar a memória de outro nó).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20149.png)

### Clusters e Warehouse-Scale Computers (WSC)

Um **cluster** é um conjunto de computadores completos (cada um com seu próprio processador, memória e armazenamento), interconectados por uma rede, trabalhando de forma coordenada em tarefas — muito usados para processamento de grandes volumes de dados e aplicações de alta disponibilidade.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20150.png)

Um **WSC** (*Warehouse-Scale Computer*) é uma evolução dos clusters, em escala muito maior — um datacenter completo, com milhares de servidores, projetado e operado como se fosse um único e gigantesco computador, otimizado para custo, energia e confiabilidade.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20151.png)

### Multithreading em hardware

**Multithreading em hardware** é uma técnica que permite que múltiplas threads compartilhem as unidades funcionais de um único núcleo de processador, aumentando a utilização desse núcleo mesmo quando uma thread está parada esperando por um recurso (como um acesso à memória).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20152.png)

Existem duas abordagens principais:

- **Multithreading de granularidade fina (*fine-grained*)** — o processador alterna entre as threads a cada ciclo de clock, pulando as threads que estiverem bloqueadas (esperando algum recurso). Melhora a utilização do processador, mas pode reduzir o desempenho individual de uma thread isolada, já que o tempo de execução dela é intercalado com o das demais.
- **Multithreading simultâneo (SMT — *Simultaneous Multithreading*)** — instruções de múltiplas threads são emitidas no **mesmo** ciclo de clock, aproveitando as unidades funcionais ociosas do processador superescalar. É o modelo usado, por exemplo, na tecnologia Hyper-Threading da Intel.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20153.png)

### GPUs (Graphics Processing Units)

As **GPUs** são processadores altamente paralelos, originalmente projetados para processamento gráfico, mas hoje amplamente usados para computação de propósito geral (**GPGPU**), especialmente em cargas de trabalho que se beneficiam de paralelismo massivo de dados, como treinamento de modelos de aprendizado de máquina.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20154.png)

Diferente de uma CPU tradicional — projetada para minimizar a latência de poucos fluxos de execução complexos — uma GPU é projetada para **maximizar o throughput**, executando milhares de threads simples simultaneamente, seguindo um modelo próximo ao SIMD (todas as threads de um grupo executam a mesma instrução sobre dados diferentes).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20155.png)

!!! note
    Esse modelo é muito eficiente para operações regulares sobre grandes volumes de dados (como multiplicação de matrizes, processamento de imagens e treinamento de redes neurais), mas é menos eficiente para código com muitos desvios condicionais e dependências complexas entre dados — tarefas para as quais uma CPU tradicional continua sendo mais adequada.

### Comparação entre as abordagens de paralelismo

| Abordagem | Granularidade | Comunicação | Exemplo típico |
|---|---|---|---|
| ILP (pipeline, múltipla emissão) | Instrução | Implícita (hardware) | Processador superescalar único |
| SMT (multithreading simultâneo) | Thread | Compartilhamento de unidades funcionais | Hyper-Threading |
| SMP (multiprocessador simétrico) | Processo/thread | Memória compartilhada | Servidor multicore |
| NUMA | Processo/thread | Memória distribuída, logicamente compartilhada | Servidores de grande porte |
| Cluster/WSC | Aplicação/tarefa | Troca de mensagens pela rede | Datacenters |
| SIMD/GPU | Dado | Instrução única, múltiplos dados | GPUs, unidades vetoriais |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20156.png)

Como visto na seção de Desempenho, a Lei de Amdahl continua sendo a principal limitação teórica de qualquer uma dessas abordagens: o ganho de desempenho obtido pela paralelização é sempre limitado pela fração do programa que permanece sequencial, por mais processadores que sejam adicionados ao sistema.

---

## Introdução aos Sistemas Operacionais

### O que é um sistema operacional

Um **Sistema Operacional (SO)** é um software que atua como intermediário entre o hardware do computador e os programas de aplicação (e seus usuários), com dois objetivos principais:

- **Gerenciar os recursos do computador** — CPU, memória, dispositivos de E/S e armazenamento — de forma eficiente e justa entre os diversos programas em execução.
- **Fornecer uma máquina estendida (abstração)** — oferecendo aos programas uma interface mais simples e conveniente do que a interação direta com o hardware bruto, escondendo a complexidade e as particularidades de cada dispositivo físico.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20157.png)

### Modos de operação: kernel e usuário

Para proteger a integridade do sistema, a maioria dos processadores modernos oferece pelo menos dois modos de operação:

- **Modo kernel (ou modo supervisor)** — permite acesso irrestrito a todo o hardware e a todas as instruções do processador, incluindo instruções privilegiadas (como manipular registradores de controle de memória ou desabilitar interrupções). É nesse modo que o núcleo do sistema operacional é executado.
- **Modo usuário** — restringe o acesso direto ao hardware; programas de aplicação são executados nesse modo, e qualquer necessidade de acesso a um recurso protegido precisa ser solicitada ao sistema operacional por meio de uma **chamada de sistema** (*system call*).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20158.png)

!!! note "Chamadas de sistema (system calls)"
    São o mecanismo pelo qual um programa em modo usuário solicita um serviço do sistema operacional — por exemplo, abrir um arquivo, alocar memória ou criar um novo processo. A chamada de sistema causa uma **troca de modo**, temporariamente elevando o privilégio de execução para modo kernel, de forma controlada, para que o SO possa atender à solicitação em segurança e depois devolver o controle ao programa em modo usuário.

O **POSIX** (*Portable Operating System Interface*) é um conjunto de padrões que define uma interface de chamadas de sistema comum, visando garantir portabilidade de programas entre diferentes sistemas operacionais do tipo Unix (Linux, macOS, BSD, entre outros).

### Arquiteturas de kernel

Existem diferentes formas de organizar internamente o núcleo (*kernel*) de um sistema operacional:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20159.png)

| Arquitetura | Características | Exemplos |
|---|---|---|
| **Monolítica** | Todo o SO (gerenciamento de processos, memória, sistema de arquivos, drivers) executa em um único espaço de endereçamento, em modo kernel. Mais rápida (menos trocas de contexto), porém menos modular e mais vulnerável — uma falha em qualquer componente pode comprometer todo o sistema. | Linux, versões antigas do Unix. |
| **Microkernel** | Apenas as funcionalidades essenciais (comunicação entre processos, escalonamento básico, gerenciamento mínimo de memória) executam em modo kernel; serviços como sistema de arquivos e drivers executam como processos separados em modo usuário, comunicando-se por troca de mensagens. Mais robusta e modular, porém com maior overhead de comunicação. | Minix, QNX, L4. |
| **Híbrida** | Combina elementos das duas abordagens: um núcleo relativamente pequeno, mas que ainda executa alguns serviços adicionais em modo kernel por razões de desempenho. | Windows NT, macOS (XNU). |
| **Exokernel** | Leva a modularidade a um extremo: o núcleo fornece apenas um conjunto mínimo de abstrações de baixo nível (alocação segura de recursos físicos), delegando praticamente toda a lógica de gerenciamento (de memória, de processos etc.) para bibliotecas executadas em nível de usuário, específicas de cada aplicação. | Projetos de pesquisa acadêmica (ex.: MIT Exokernel). |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20160.png)

!!! tip "Trade-off fundamental"
    Em geral, quanto mais modular é a arquitetura do kernel (microkernel, exokernel), mais robusto e seguro tende a ser o sistema — já que falhas em um componente não derrubam o sistema inteiro — mas ao custo de desempenho, por causa da comunicação adicional entre processos. Arquiteturas monolíticas sacrificam parte dessa robustez em troca de desempenho.

### Principais funções do sistema operacional

De forma resumida, um sistema operacional moderno é responsável por:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20161.png)

- **Gerência de processos** — criação, escalonamento, sincronização e encerramento de processos e threads (detalhado nas próximas seções).
- **Gerência de memória** — alocação e liberação de memória física e virtual para os processos, incluindo paginação e proteção entre processos.
- **Gerência de armazenamento (sistema de arquivos)** — organização de arquivos e diretórios em dispositivos de armazenamento persistente, controlando permissões de acesso.
- **Gerência de dispositivos de E/S** — abstração do acesso a dispositivos físicos variados (discos, teclados, placas de rede) por meio de drivers e interfaces padronizadas.
- **Segurança e proteção** — controle de acesso a recursos, autenticação de usuários e isolamento entre processos.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20162.png)

### Evolução histórica dos sistemas operacionais

Os sistemas operacionais evoluíram significativamente ao longo das décadas, acompanhando a evolução do hardware:

- **Processamento em lote (*batch*)** — os primeiros sistemas não tinham interação direta com o usuário; programas (jobs) eram submetidos em lote e processados sequencialmente, sem multiprogramação.
- **Multiprogramação** — vários programas são mantidos na memória simultaneamente, e a CPU alterna entre eles sempre que um programa fica bloqueado esperando por E/S, aumentando a utilização da CPU.
- **Tempo compartilhado (*time-sharing*)** — a CPU é dividida em pequenos intervalos de tempo (*time slices*), alternando rapidamente entre vários programas, dando a ilusão de execução simultânea e permitindo interação direta de múltiplos usuários com o sistema.
- **Sistemas pessoais e multitarefa** — com a popularização de computadores pessoais, surgiram sistemas operacionais voltados para um único usuário, mas ainda capazes de executar múltiplos programas (multitarefa), como Windows, macOS e Linux.
- **Sistemas distribuídos e em nuvem** — sistemas operacionais modernos precisam lidar com recursos distribuídos por múltiplas máquinas, redes e datacenters, incluindo virtualização e orquestração de contêineres.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20163.png)

### Virtualização

**Virtualização** é a técnica de criar uma versão virtual de um recurso computacional (como um processador, memória ou um sistema operacional completo), permitindo que múltiplos ambientes isolados compartilhem o mesmo hardware físico. Uma **máquina virtual (VM)** executa seu próprio sistema operacional completo, de forma isolada, sobre um **hipervisor**, que gerencia o acesso dessas VMs ao hardware real subjacente.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20164.png)

!!! note "Virtualização vs. containers"
    Diferente de uma VM completa, um **contêiner** (como Docker) não virtualiza um sistema operacional completo — ele compartilha o kernel do sistema operacional hospedeiro, isolando apenas o espaço de usuário (bibliotecas, dependências e processos da aplicação). Isso torna os contêineres muito mais leves e rápidos de inicializar do que VMs tradicionais, embora ofereçam um nível de isolamento ligeiramente menor.

---

## Processos e Threads

### O conceito de processo

Um **processo** é a abstração fundamental de um programa em execução. Enquanto um *programa* é um conjunto estático de instruções armazenado em disco, um *processo* é a instância dinâmica desse programa, incluindo seu código, seus dados, seu estado atual (valores de registradores, PC) e os recursos que ele está utilizando (memória alocada, arquivos abertos, etc.).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20165.png)

#### Bloco de controle de processo (PCB)

Para gerenciar os processos, o sistema operacional mantém, para cada um deles, uma estrutura de dados chamada **Bloco de Controle de Processo (PCB — *Process Control Block*)**, que armazena todas as informações necessárias para suspender e retomar a execução de um processo a qualquer momento. Entre as informações contidas no PCB, estão:

- Identificador do processo (**PID**).
- Estado atual do processo.
- Valor do *program counter* (PC) e dos demais registradores da CPU.
- Informações de escalonamento (prioridade, ponteiros para filas de escalonamento).
- Informações de gerência de memória (tabelas de página, limites de memória alocada).
- Informações de contabilização (tempo de CPU usado, limites de tempo).
- Informações de E/S (dispositivos alocados, lista de arquivos abertos).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20166.png)

#### Estados de um processo

Durante sua execução, um processo transita entre diferentes **estados**:

| Estado | Descrição |
|---|---|
| **Novo** | O processo está sendo criado. |
| **Pronto (*ready*)** | O processo está na memória, apto a executar, mas aguardando que a CPU seja alocada a ele pelo escalonador. |
| **Em execução (*running*)** | O processo está de fato sendo executado pela CPU. |
| **Bloqueado/em espera (*waiting*)** | O processo está esperando a ocorrência de algum evento (ex.: término de uma operação de E/S), e não pode continuar até que esse evento ocorra. |
| **Terminado** | O processo concluiu sua execução (ou foi encerrado), liberando os recursos que utilizava. |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20167.png)

A transição entre os estados "em execução" e "pronto", bem como entre "pronto" e "bloqueado", é controlada pelo **escalonador** do sistema operacional, detalhado mais adiante na seção de Gerência de Processador.

### Troca de contexto

Sempre que o sistema operacional decide suspender a execução de um processo (para executar outro, ou por causa de um bloqueio) e depois retomá-la, é necessário realizar uma **troca de contexto (*context switch*)**: salvar o estado completo do processo atual (registradores, PC, etc.) no seu PCB, e carregar o estado salvo do próximo processo a ser executado.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20168.png)

!!! warning "Custo da troca de contexto"
    A troca de contexto é uma operação de **puro overhead** — ou seja, não realiza trabalho útil para nenhum processo, apenas transfere o controle da CPU. Seu custo depende da complexidade do sistema operacional e das características do hardware (como a presença de suporte dedicado para troca rápida de contexto). Minimizar a frequência e o custo das trocas de contexto é uma das preocupações centrais no projeto de escalonadores eficientes.

### Criação e término de processos

Um processo pode criar novos processos, chamados de **processos filhos**, formando uma hierarquia (uma árvore de processos). No modelo Unix/Linux, a chamada de sistema `fork()` cria um processo filho que é uma cópia quase idêntica do processo pai (mesmo código, dados e estado), e a chamada `exec()` é usada para substituir a imagem de memória do processo filho por um novo programa.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20169.png)

Um processo pode terminar de forma normal (concluindo sua execução e chamando `exit()`) ou de forma anormal (por um erro fatal, ou por ser encerrado por outro processo — por exemplo, via `kill()`). Quando um processo termina, seus recursos (memória, arquivos abertos) são liberados pelo sistema operacional.

### Threads

Uma **thread** é um fluxo de execução dentro de um processo. Um processo pode conter uma ou mais threads, e todas as threads de um mesmo processo compartilham o mesmo espaço de endereçamento (código, dados globais, arquivos abertos), mas cada thread mantém seu próprio contexto de execução individual: seu próprio conjunto de registradores, seu próprio *program counter* e sua própria pilha.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20170.png)

| Característica | Processo | Thread |
|---|---|---|
| Espaço de endereçamento | Próprio e isolado | Compartilhado com as demais threads do processo |
| Comunicação entre entidades | Mais custosa (IPC) | Mais simples e rápida (memória compartilhada) |
| Criação/troca de contexto | Mais custosa | Mais leve e rápida |
| Isolamento/robustez | Alto (falha em um processo não afeta outros) | Baixo (falha em uma thread pode comprometer todo o processo) |

A principal vantagem de usar threads, em vez de múltiplos processos, é o menor custo de criação, troca de contexto e comunicação entre elas, já que compartilham o mesmo espaço de memória.

#### Modelos de threading: ULT vs. KLT

Existem duas abordagens principais para implementar threads:

- **ULT (*User-Level Threads*)** — as threads são gerenciadas inteiramente por uma biblioteca em nível de usuário, sem que o kernel saiba de sua existência (o kernel só "vê" o processo como um todo). A troca de contexto entre threads é muito rápida, pois não exige uma chamada de sistema. A desvantagem é que, se uma thread faz uma chamada de sistema bloqueante, **todo o processo** (e todas as suas threads) é bloqueado, já que o kernel não distingue entre as threads individuais.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20171.png)

- **KLT (*Kernel-Level Threads*)** — o próprio kernel conhece e gerencia cada thread individualmente, escalonando-as de forma independente. Isso resolve o problema do bloqueio total, permitindo que outras threads do mesmo processo continuem executando mesmo que uma delas esteja bloqueada — mas tem um custo maior de criação e troca de contexto, já que cada operação exige uma chamada de sistema.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20172.png)

- **Modelo híbrido (*many-to-many*)** — combina as duas abordagens, mapeando um número de threads de usuário para um número (geralmente menor) de threads de kernel, buscando um equilíbrio entre a leveza do modelo ULT e a concorrência real do modelo KLT.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20173.png)

| Modelo | Mapeamento | Vantagem | Desvantagem |
|---|---|---|---|
| **ULT** (many-to-one) | N threads de usuário → 1 thread de kernel | Troca de contexto muito rápida | Bloqueio de uma thread bloqueia o processo inteiro; não aproveita múltiplos núcleos |
| **KLT** (one-to-one) | 1 thread de usuário → 1 thread de kernel | Paralelismo real, aproveitamento de múltiplos núcleos | Criação e troca de contexto mais custosas |
| **Híbrido** (many-to-many) | N threads de usuário → M threads de kernel (M ≤ N) | Equilíbrio entre os dois modelos | Maior complexidade de implementação |

### Processos vs. threads: multiprocessamento e multithreading

Em um sistema com múltiplos núcleos, tanto múltiplos processos quanto múltiplas threads de um mesmo processo podem ser executados verdadeiramente em paralelo, cada um em um núcleo diferente — e não apenas de forma intercalada (como aconteceria em um único núcleo, por meio de *time-sharing*).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20174.png)

Aplicações modernas costumam combinar as duas abordagens: múltiplos processos para isolar componentes críticos ou não confiáveis entre si (por exemplo, abas distintas de um navegador), e múltiplas threads dentro de cada processo para paralelizar tarefas que compartilham dados de forma intensa (por exemplo, renderização e interface gráfica de uma mesma aba).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20175.png)

---

## Sincronização e Comunicação Interprocessos

### Condições de corrida

Quando múltiplos processos ou threads acessam e manipulam dados compartilhados concorrentemente, e o resultado final dessa manipulação depende da ordem (não determinística) em que as operações ocorrem, diz-se que existe uma **condição de corrida (*race condition*)**.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20176.png)

!!! example
    Dois processos incrementam uma variável compartilhada `contador`, cujo valor inicial é 5. Cada incremento é, na verdade, composto por três operações de baixo nível: ler o valor atual de `contador`, somar 1, e escrever o novo valor de volta. Se os dois processos executarem essas três operações de forma intercalada — por exemplo, ambos lerem o valor 5 antes que qualquer um escreva o resultado — o valor final de `contador` pode acabar sendo 6, em vez do 7 esperado, porque uma das atualizações foi "perdida".

### Região crítica e exclusão mútua

O trecho de código em que um processo acessa recursos compartilhados é chamado de **região crítica** (*critical section*). Para evitar condições de corrida, é necessário garantir a **exclusão mútua**: apenas um processo (ou thread) pode executar dentro da sua região crítica referente a um dado recurso compartilhado por vez.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20177.png)

Uma solução para o problema da região crítica deve satisfazer três propriedades:

1. **Exclusão mútua** — se um processo está executando em sua região crítica, nenhum outro processo pode executar na correspondente região crítica simultaneamente.
2. **Progresso** — se nenhum processo está em sua região crítica e existem processos que desejam entrar, a decisão de qual processo entrará não pode ser postergada indefinidamente.
3. **Espera limitada** — deve existir um limite para o número de vezes que outros processos podem entrar em suas regiões críticas depois que um processo solicitou entrada e antes que essa solicitação seja atendida (evitando *starvation*).

### Espera ocupada (busy waiting)

Uma abordagem simples (mas ineficiente) para sincronização é a **espera ocupada**, em que um processo fica repetidamente verificando, em um loop, se uma condição se tornou verdadeira (como uma variável de bloqueio tendo sido liberada), consumindo ciclos de CPU sem realizar trabalho útil enquanto espera.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20178.png)

!!! warning "Desvantagem da espera ocupada"
    Além de desperdiçar CPU, a espera ocupada pode causar o problema da **inversão de prioridade**: se um processo de alta prioridade espera ocupadamente por um recurso detido por um processo de baixa prioridade, e o escalonador não dá tempo de CPU suficiente a esse processo de baixa prioridade para que ele libere o recurso, o processo de alta prioridade pode acabar impedido de progredir por um tempo desproporcional.

### Solução por hardware: TSL

Uma forma de implementar exclusão mútua com apoio de hardware é a instrução **TSL** (*Test-and-Set Lock*), uma instrução atômica (indivisível) que lê o valor de uma variável de bloqueio e, simultaneamente, define seu novo valor — garantindo que nenhum outro processador possa intervir entre a leitura e a escrita.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20179.png)

```c
// Pseudocódigo da instrução TSL, atômica por construção
int TSL(int *lock) {
    int old_value = *lock;
    *lock = 1;
    return old_value;
}

// Uso da TSL para exclusão mútua (com espera ocupada)
void entrar_regiao_critica(int *lock) {
    while (TSL(lock) == 1) {
        // espera ocupada: continua tentando até conseguir o lock
    }
}

void sair_regiao_critica(int *lock) {
    *lock = 0;
}
```

### Solução por software: algoritmo de Peterson

O **Algoritmo de Peterson** é uma solução puramente em software (sem necessidade de instruções especiais de hardware) para o problema da exclusão mútua entre dois processos, usando duas variáveis compartilhadas: um array `flag`, que indica se cada processo quer entrar na região crítica, e uma variável `turn`, que indica de quem é a vez.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20180.png)

```c
// Algoritmo de Peterson para 2 processos (0 e 1)
int flag[2] = {0, 0};
int turn;

void entrar_regiao_critica(int i) { // i é o id do processo (0 ou 1)
    int j = 1 - i; // id do outro processo
    flag[i] = 1;   // "eu quero entrar"
    turn = j;      // cede a vez ao outro, caso ele também queira entrar
    while (flag[j] == 1 && turn == j) {
        // espera ocupada
    }
}

void sair_regiao_critica(int i) {
    flag[i] = 0; // "eu não quero mais entrar"
}
```

!!! note
    O algoritmo de Peterson satisfaz as três propriedades desejadas (exclusão mútua, progresso e espera limitada) para dois processos, mas, na prática, processadores modernos com múltiplos núcleos e reordenação de instruções podem exigir barreiras de memória adicionais para que ele funcione corretamente — por isso, raramente é usado diretamente em sistemas reais, servindo principalmente como exercício didático.

### Semáforos

Como as soluções baseadas em espera ocupada são ineficientes, Dijkstra propôs os **semáforos**: uma variável inteira, manipulada apenas por duas operações atômicas, tradicionalmente chamadas de `P` (ou `wait`/`down`) e `V` (ou `signal`/`up`).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20181.png)

```c
// Semântica das operações de um semáforo S
void P(Semaforo *S) { // wait / down
    S->valor--;
    if (S->valor < 0) {
        // o processo é bloqueado e colocado em uma fila de espera
        bloquear_processo();
    }
}

void V(Semaforo *S) { // signal / up
    S->valor++;
    if (S->valor <= 0) {
        // acorda um dos processos bloqueados na fila de espera
        acordar_processo();
    }
}
```

Diferente da espera ocupada, quando um processo não pode decrementar o semáforo (porque seu valor já é 0 ou negativo), ele é **bloqueado** pelo sistema operacional e colocado em uma fila de espera, liberando a CPU para outros processos — e só é "acordado" quando outro processo executa a operação `V`.

Existem dois tipos de semáforos:

- **Semáforo binário (mutex)** — assume apenas os valores 0 ou 1, funcionando como um cadeado simples que garante exclusão mútua para um único recurso.
- **Semáforo contador (ou geral)** — pode assumir qualquer valor inteiro, usado para controlar o acesso a um *pool* de múltiplas instâncias de um mesmo tipo de recurso (por exemplo, um conjunto de N conexões disponíveis em um banco de dados).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20182.png)

### O problema do produtor-consumidor

O **problema do produtor-consumidor** (também chamado de *bounded buffer problem*) é um problema clássico de sincronização, em que um ou mais processos **produtores** geram itens e os colocam em um *buffer* compartilhado de tamanho fixo, enquanto um ou mais processos **consumidores** retiram itens desse buffer para processá-los.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20183.png)

Esse problema exige coordenação em duas frentes: o produtor não pode inserir itens se o buffer estiver cheio, e o consumidor não pode retirar itens se o buffer estiver vazio. A solução clássica usa **três semáforos**:

- `cheio` — conta o número de posições ocupadas do buffer (inicialmente 0).
- `vazio` — conta o número de posições livres do buffer (inicialmente igual à capacidade N do buffer).
- `mutex` — semáforo binário que garante exclusão mútua ao acessar o buffer (evitando que produtor e consumidor manipulem a estrutura do buffer simultaneamente).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20184.png)

```c
// Problema do produtor-consumidor com semáforos
Semaforo vazio = N; // N posições livres inicialmente
Semaforo cheio = 0; // nenhuma posição ocupada inicialmente
Semaforo mutex = 1; // exclusão mútua no acesso ao buffer

void produtor() {
    while (true) {
        item = produzir_item();
        P(&vazio);  // espera por uma posição livre
        P(&mutex);  // entra na região crítica
        inserir_no_buffer(item);
        V(&mutex);  // sai da região crítica
        V(&cheio);  // sinaliza que há mais um item disponível
    }
}

void consumidor() {
    while (true) {
        P(&cheio);  // espera por um item disponível
        P(&mutex);  // entra na região crítica
        item = retirar_do_buffer();
        V(&mutex);  // sai da região crítica
        V(&vazio);  // sinaliza que há mais uma posição livre
        consumir_item(item);
    }
}
```

!!! warning "Ordem das operações P"
    É fundamental que as operações `P(&vazio)`/`P(&cheio)` sejam feitas **antes** de `P(&mutex)`, e nunca depois — caso contrário, pode ocorrer um **deadlock**: por exemplo, se o produtor adquirisse primeiro o `mutex` e depois tentasse `P(&vazio)` com o buffer cheio, ele ficaria bloqueado segurando o `mutex`, impedindo que o consumidor jamais conseguisse esvaziar o buffer (já que o consumidor também precisa do `mutex` para retirar itens).

### Monitores

Um **monitor** é uma construção de sincronização de mais alto nível do que semáforos, geralmente oferecida diretamente por linguagens de programação (como Java, com blocos `synchronized`). Um monitor agrupa, em uma única estrutura, os dados compartilhados e os procedimentos que os manipulam, garantindo automaticamente que apenas um processo (ou thread) possa estar executando qualquer um desses procedimentos por vez — a exclusão mútua é imposta pelo próprio compilador/runtime, e não precisa ser gerenciada manualmente pelo programador.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20185.png)

Monitores também oferecem **variáveis de condição**, que permitem que um processo seja bloqueado dentro do monitor até que uma determinada condição se torne verdadeira, e sejam "acordados" por outro processo quando essa condição é satisfeita — de forma análoga ao papel dos semáforos no problema produtor-consumidor, mas com a exclusão mútua do acesso aos dados compartilhados garantida automaticamente pela linguagem.

!!! tip "Semáforos vs. monitores"
    Semáforos são um mecanismo de sincronização de baixo nível, flexível, mas propenso a erros (como esquecer de liberar um semáforo, ou inverter a ordem das operações `P`/`V`). Monitores reduzem esses erros ao encapsular a exclusão mútua na própria estrutura da linguagem, facilitando a escrita de código concorrente correto, ainda que com um pouco menos de flexibilidade.

### Comunicação entre processos (IPC)

Além de sincronizar o acesso a recursos compartilhados, processos frequentemente precisam **trocar dados** entre si — o que é chamado de **Comunicação Interprocessos (IPC — *Interprocess Communication*)**. Como, em geral, processos não compartilham memória (diferente de threads), são necessários mecanismos específicos para essa comunicação:

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20186.png)

- **Pipes** — um canal de comunicação unidirecional entre dois processos relacionados (geralmente processo pai e filho), em que a saída de um processo é usada como entrada do outro (como o operador `|` no terminal Unix).

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20187.png)

- **Memória compartilhada** — uma região de memória física é mapeada no espaço de endereçamento de múltiplos processos, permitindo que eles leiam e escrevam diretamente nos mesmos dados. É o mecanismo de IPC mais rápido, mas exige sincronização explícita (via semáforos ou outras primitivas) para evitar condições de corrida, já que o sistema operacional não garante nenhuma coordenação automática sobre o conteúdo dessa memória.

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20188.png)

- **Troca de mensagens (*message passing*)** — processos se comunicam enviando e recebendo mensagens explícitas, por meio de chamadas de sistema como `send()` e `receive()`, sem a necessidade de compartilhar memória diretamente. É mais lenta do que a memória compartilhada (envolve cópias de dados e, geralmente, chamadas de sistema), mas mais simples de usar corretamente e mais adequada para processos em máquinas distintas (comunicação em rede).

    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20189.png)

- **Sockets** — uma abstração de comunicação bidirecional, amplamente usada para comunicação em rede entre processos (potencialmente em máquinas diferentes), seguindo o modelo cliente-servidor.

| Mecanismo | Velocidade | Complexidade de uso | Escopo típico |
|---|---|---|---|
| Pipes | Média | Baixa | Processos relacionados, na mesma máquina |
| Memória compartilhada | Alta | Alta (exige sincronização manual) | Processos na mesma máquina |
| Troca de mensagens | Baixa/Média | Baixa | Processos na mesma máquina ou em rede |
| Sockets | Baixa/Média | Média | Processos em rede |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20190.png)

---

## Gerência de Processador

### O escalonador

O **escalonador (*scheduler*)** é o componente do sistema operacional responsável por decidir **qual processo (ou thread), entre os que estão no estado "pronto", receberá a CPU a seguir**, e por quanto tempo. Essa decisão é crítica para o desempenho percebido do sistema como um todo.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20191.png)

### Critérios de escalonamento

Diferentes algoritmos de escalonamento buscam otimizar diferentes métricas, que muitas vezes competem entre si:

| Critério | Descrição |
|---|---|
| **Utilização da CPU** | Percentual de tempo em que a CPU está ocupada executando processos (idealmente próximo de 100%). |
| **Throughput** | Número de processos concluídos por unidade de tempo. |
| **Tempo de turnaround** | Tempo total desde a submissão até a conclusão de um processo (espera + execução + E/S). |
| **Tempo de espera** | Tempo total que um processo passa na fila de "pronto", aguardando a CPU. |
| **Tempo de resposta** | Tempo entre a submissão de uma requisição e a produção da primeira resposta (importante em sistemas interativos). |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20192.png)

!!! note
    Em geral, algoritmos que minimizam o tempo médio de espera não são necessariamente os melhores para o tempo de resposta (sistemas interativos), e vice-versa — por isso, a escolha do algoritmo de escalonamento depende muito do perfil de uso do sistema (um servidor de processamento em lote valoriza throughput; um sistema desktop valoriza tempo de resposta).

### Escalonamento não preemptivo vs. preemptivo

- **Não preemptivo (*non-preemptive*)** — uma vez que a CPU é concedida a um processo, ele a mantém até terminar sua execução ou bloquear voluntariamente (por exemplo, esperando por E/S). Mais simples de implementar, mas pode causar longos tempos de espera para processos curtos presos atrás de processos longos.
- **Preemptivo (*preemptive*)** — o sistema operacional pode interromper um processo em execução (preempção) e devolvê-lo à fila de "pronto", mesmo que ele não tenha terminado nem bloqueado, geralmente para conceder a CPU a outro processo de maior prioridade ou após o esgotamento de uma quota de tempo. Permite melhor tempo de resposta e evita que um único processo monopolize a CPU, mas exige controle mais cuidadoso sobre acesso a recursos compartilhados.

### Algoritmos de escalonamento

#### FCFS (First-Come, First-Served)

O algoritmo mais simples: os processos são atendidos na ordem exata em que chegam à fila de "pronto", sem preempção.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20193.png)

!!! warning "Efeito comboio (convoy effect)"
    O FCFS sofre do **efeito comboio**: se um processo com tempo de execução muito longo é o primeiro a chegar, todos os processos seguintes — mesmo que muito curtos — precisam esperar que ele termine, aumentando bastante o tempo médio de espera do sistema como um todo.

#### SJF (Shortest Job First)

Associa a cada processo o tempo estimado da sua próxima execução, e escolhe sempre o processo com o **menor tempo de execução estimado** para executar a seguir. É um algoritmo não preemptivo (na sua forma básica) e é **comprovadamente ótimo** em relação ao tempo médio de espera, entre os algoritmos não preemptivos — desde que as estimativas de tempo de execução sejam precisas.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20194.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20195.png)

!!! warning "Limitação do SJF"
    Na prática, o tempo exato de execução de um processo raramente é conhecido de antemão — por isso, o SJF normalmente depende de **estimativas** (baseadas, por exemplo, em uma média exponencial dos tempos de execução anteriores do mesmo processo), o que reduz sua aplicabilidade direta em sistemas reais. Além disso, processos longos podem sofrer *starvation* caso processos curtos continuem chegando.

#### SRTF (Shortest Remaining Time First)

É a versão **preemptiva** do SJF: sempre que um novo processo chega à fila de "pronto", seu tempo de execução estimado é comparado com o tempo **restante** do processo atualmente em execução — se o novo processo tiver um tempo menor, ocorre uma preempção, e o processo em execução volta para a fila de "pronto".

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20196.png)

#### HRRN (Highest Response Ratio Next)

Busca equilibrar os benefícios do SJF com a necessidade de evitar *starvation* de processos longos, calculando uma **razão de resposta** para cada processo na fila:

$$\text{Razão de resposta} = \frac{\text{tempo de espera} + \text{tempo de execução estimado}}{\text{tempo de execução estimado}}$$

O processo com a **maior razão de resposta** é escolhido para executar a seguir. Note que, quanto mais tempo um processo espera, maior fica sua razão de resposta — garantindo que, eventualmente, mesmo processos mais longos sejam escolhidos, evitando a *starvation* presente no SJF puro.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20197.png)

#### Round Robin (RR)

Cada processo recebe uma pequena unidade de tempo fixa, chamada **quantum** (ou *time slice*), para executar. Se o processo não terminar dentro desse quantum, é preemptado e devolvido ao **final** da fila de "pronto" (que é organizada como uma fila circular), dando a vez ao próximo processo.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20198.png)

!!! example
    ![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20199.png)

!!! tip "Escolha do quantum"
    A escolha do tamanho do quantum é um trade-off importante: um quantum **muito pequeno** aumenta excessivamente o número de trocas de contexto (cujo overhead passa a dominar o tempo total), enquanto um quantum **muito grande** faz o Round Robin se comportar, na prática, como o FCFS, perdendo os benefícios de um bom tempo de resposta para sistemas interativos. Um valor típico razoável é um quantum entre 10 e 100 milissegundos.

#### Escalonamento por prioridade

Cada processo recebe uma prioridade (numérica), e a CPU é sempre concedida ao processo de **maior prioridade** entre os que estão prontos (podendo ser preemptivo ou não). Prioridades podem ser definidas estaticamente (fixas, atribuídas na criação do processo) ou dinamicamente (ajustadas durante a execução, por exemplo, para evitar starvation).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20200.png)

!!! warning "Starvation e envelhecimento (aging)"
    Processos de baixa prioridade podem nunca chegar a executar, caso processos de prioridade mais alta continuem chegando (*starvation*). Uma solução comum é o **envelhecimento (*aging*)**: a prioridade de um processo é gradualmente aumentada conforme ele espera na fila de "pronto", garantindo que, eventualmente, mesmo processos de baixa prioridade acabem sendo executados.

#### Filas multinível com retroalimentação (MFQ)

O **MFQ** (*Multilevel Feedback Queue*) combina diversos algoritmos de escalonamento, organizando os processos em várias filas, cada uma com uma prioridade e um quantum diferentes — normalmente, filas de maior prioridade possuem quanta menores (mais adequados para processos curtos e interativos), enquanto filas de menor prioridade possuem quanta maiores (mais adequados para processos de longa duração, ligados à CPU).

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20201.png)

Um processo pode se mover entre as filas com base em seu comportamento observado: se ele utiliza todo o seu quantum em uma fila de alta prioridade (sugerindo que é um processo mais "pesado"), é movido para uma fila de prioridade mais baixa; se ele libera a CPU antes do fim do quantum (por exemplo, esperando por E/S, sugerindo um processo interativo), permanece na mesma fila ou é promovido a uma fila de prioridade mais alta. Esse mecanismo permite que o escalonador se adapte dinamicamente ao comportamento de cada processo, sem exigir conhecimento prévio do seu tempo de execução.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20202.png)

#### Escalonamento por loteria (Lottery Scheduling)

Cada processo recebe um certo número de "bilhetes de loteria", proporcional à prioridade ou à fração de CPU que deve receber. A cada decisão de escalonamento, um bilhete é sorteado aleatoriamente entre todos os bilhetes distribuídos, e o processo correspondente ao bilhete sorteado recebe a CPU.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20203.png)

!!! note
    Esse algoritmo é probabilisticamente justo: em média, um processo com o dobro de bilhetes de outro receberá, em média, o dobro da fração de tempo de CPU. Além disso, resolve de forma elegante o problema da starvation, já que todo processo com pelo menos um bilhete tem sempre uma chance (ainda que pequena) de ser escolhido a cada rodada.

### Comparação entre os algoritmos de escalonamento

| Algoritmo | Preemptivo? | Critério otimizado | Risco de starvation |
|---|---|---|---|
| FCFS | Não | Simplicidade | Baixo (mas sofre efeito comboio) |
| SJF | Não | Tempo médio de espera | Alto (processos longos) |
| SRTF | Sim | Tempo médio de espera | Alto (processos longos) |
| HRRN | Não | Equilíbrio espera/execução | Baixo (compensado pela razão de resposta) |
| Round Robin | Sim | Tempo de resposta | Nenhum |
| Prioridade | Ambos | Flexibilidade/importância | Alto (sem aging) |
| MFQ | Sim | Adaptação ao comportamento do processo | Baixo (com promoção entre filas) |
| Loteria | Sim | Justiça proporcional | Nenhum |

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20204.png)

### Escalonamento em sistemas multiprocessados

Em sistemas com múltiplos núcleos ou processadores, o escalonamento se torna mais complexo, pois é preciso decidir não apenas **quando**, mas também **em qual núcleo** cada processo (ou thread) deve ser executado.

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20205.png)

- **Escalonamento assimétrico** — apenas um núcleo (o "mestre") toma todas as decisões de escalonamento, distribuindo processos para os demais núcleos (os "escravos"), que apenas os executam. É mais simples de implementar, mas o núcleo mestre pode se tornar um gargalo.
- **Escalonamento simétrico (SMP)** — todos os núcleos participam igualmente do processo de escalonamento, geralmente compartilhando (ou replicando, de forma sincronizada) a fila de processos prontos. É mais escalável, mas exige sincronização cuidadosa ao acessar as estruturas de dados de escalonamento compartilhadas entre os núcleos.
- **Afinidade de processador** — sempre que possível, o escalonador tenta manter um processo (ou thread) executando repetidamente no **mesmo** núcleo em que já executou antes, aproveitando os dados que esse processo já deixou "aquecidos" nas caches locais daquele núcleo (afinidade de cache), em vez de migrá-lo para outro núcleo a cada nova execução, o que exigiria recarregar esses dados em uma cache "fria".

![image.png](../../assets/faculdade/periodo3/arquitetura-de-computadores-e-sistemas-operacionais/image%20206.png)

!!! tip "Balanceamento de carga"
    Em sistemas multiprocessados, é importante balancear a carga de trabalho entre os núcleos, evitando que alguns fiquem sobrecarregados enquanto outros ficam ociosos. Isso pode ser feito de forma ativa (um processo migra periodicamente processos de núcleos mais ocupados para núcleos mais livres, chamado *push migration*) ou de forma passiva (um núcleo ocioso "rouba" trabalho de outro núcleo sobrecarregado, chamado *pull migration* ou *work stealing*).
