# Assembly

!!! note
    Esta página cobre o assembly MIPS, que é o dialeto usado em maior detalhe nas anotações originais (por ser didaticamente mais simples e muito usado em disciplinas de arquitetura de computadores), além de uma nota breve sobre NASM e GAS, os dois dialetos de assembly x86 mais comuns.

## MIPS

MIPS é uma arquitetura RISC (*Reduced Instruction Set Computer*), caracterizada por um conjunto de instruções pequeno e regular, em que cada instrução é simples e, em geral, executa em um único ciclo de clock.

### Instruções

As instruções em MIPS aceitam, no máximo, até 3 operandos (registradores) — por exemplo, uma instrução de soma recebe dois registradores de origem e um registrador de destino.

### Registradores

O MIPS possui 32 registradores de 32 bits cada, e cada registrador é referenciado com o símbolo `$` antecedendo o seu nome (por exemplo, `$s0`, `$t1`, `$a0`).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%201.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%202.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%203.png)

### Instruções de movimentação de dados

**Load (`lw`)** — instrução de movimentação de dados **da memória para o registrador**; é uma operação de leitura da memória, usada para o tipo `.word`.

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%204.png)

**Store (`sw`)** — instrução de movimentação de dados **do registrador para a memória**; é uma operação de escrita na memória.

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%205.png)

**Move (`move`)** — instrução para passar o conteúdo de um registrador para outro registrador; a memória RAM não é envolvida nessa operação.

**`li`** — atribui um número imediato (literal) a um registrador.

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%206.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%207.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%208.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%209.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2010.png)

Para armazenar valores do tipo `float` e `double`, usamos os registradores `$fX`. É importante observar que os valores do tipo `double` devem ser armazenados nos registradores de índice **par** (já que um `double` ocupa 64 bits, o equivalente a dois registradores de ponto flutuante consecutivos).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2011.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2012.png)

**`la`** — copia o **endereço** de um *label* (rótulo) na memória para o registrador dado; é usado para os tipos `.byte` ou `.asciiz`.

### Instruções aritméticas

| Instrução | Significado |
|---|---|
| `add` | Soma — usa dois registradores como operandos. |
| `addi` | Soma — usa um registrador e um valor inteiro imediato. |
| `sub` | Subtração. |
| `subi` | Subtração — usa um registrador e um valor inteiro imediato. |
| `mul` | Multiplicação. |
| `div` | Divisão inteira. |

!!! example "`div`"
    ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2013.png)

Após uma operação de `div`, o quociente é armazenado no registrador especial `lo`, e o resto no registrador especial `hi`:

- **`mflo`** — move o conteúdo do registrador `lo` (o quociente da divisão) para um registrador comum.

    ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2014.png)

- **`mfhi`** — move o conteúdo do registrador `hi` (o resto da divisão) para um registrador comum.

    ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2015.png)

### Deslocamento de bits (shifts)

**`sll`** (*shift left logical*) — desloca os bits para a esquerda, o que equivale a multiplicar por potências de dois.

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2016.png)

Por exemplo, se fizermos `sll $s3, $s2 (= 10), 10`, estaremos multiplicando $10$ por $2^{10} = 1024$, resultando em $10240$.

**`srl`** (*shift right logical*) — desloca os bits para a direita, o que equivale a dividir por potências de dois (capturando apenas a parte inteira do resultado). Por exemplo, `srl $s0, $s4 (= 10240), 5` equivale a $10240 / 2^5 = 320$.

### Diretivas e estrutura de um programa

- **`.data`** — seção de especificação de variáveis; lida com os dados que residem na memória principal. Para criar uma variável do tipo string, usamos a diretiva `.asciiz` (que adiciona um terminador nulo); se for apenas um caractere, usamos `.ascii`.
- **`.text`** — seção que contém as instruções propriamente ditas do programa.
- **Impressão de saída** — a sequência típica é carregar o código da operação desejada em `$v0` e o valor a imprimir em `$a0`, seguido da instrução `syscall`, que executa a chamada de sistema (imprimindo o que está dentro do registrador `$a0`, no caso de uma impressão de inteiro).

### Condicionais

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2017.png)

!!! warning
    Em MIPS não existe uma instrução de `else`: a linguagem oferece apenas instruções de desvio condicional (`beq`, `bne`, `blt`, `bgt`, etc.), e toda estrutura condicional — incluindo um `if/else` — precisa ser construída manualmente a partir de desvios (*branches*) e rótulos (*labels*).

### Laços de repetição

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2018.png)

Da mesma forma que os condicionais, os laços de repetição (`for`, `while`) são implementados combinando rótulos com instruções de desvio condicional e incondicional (`j`), que saltam de volta para o início do laço ou para fora dele, conforme a condição de parada é avaliada.

### Funções

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2019.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2020.png)

- **`jal`** (*jump and link*) — usada para **chamar** a função: salta para o endereço da função e salva o endereço de retorno.
- **`jr`** (*jump register*) — usada para **retornar** a quem chamou a função.
- **`$ra`** — registrador específico que armazena o endereço de retorno de funções (é automaticamente preenchido por `jal`, e usado por `jr $ra` para voltar).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2021.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2022.png)

### Arrays (vetores)

Vetores em MIPS são tratados como blocos contíguos de memória, acessados por meio de um registrador que guarda o endereço base do vetor, somado a um deslocamento (*offset*) calculado a partir do índice e do tamanho de cada elemento (por exemplo, 4 bytes por elemento, no caso de inteiros do tipo `.word`).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2023.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2024.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2025.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2026.png)

### Manipulação de arquivos de texto

**Abrir um arquivo**

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2027.png)

!!! warning
    Em MIPS, não existe um modo de abertura que permita leitura e escrita simultâneas no mesmo arquivo — é necessário escolher um ou outro modo ao abrir.

**Ler um arquivo**

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2028.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2029.png)

Nessa sequência: `li $v0, 13` indica o modo de abertura de arquivo; `la $a0, file` precisa passar, em `$a0`, o endereço do nome do arquivo; e `li $a1, 0` é a *flag* do modo de abertura (0 para leitura, 1 para escrita).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2030.png)

Em seguida, `li $v0, 14` indica que a operação será de leitura do arquivo; e, diferentemente do que se poderia esperar, o tamanho do buffer é passado com `li $a2, tamanhoBuffer` (carregando o valor imediato), e não com `la $a2, tamanhoBuffer` (que carregaria um endereço).

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2031.png)

**Escrever em um arquivo**

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2032.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2033.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2034.png)

![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2035.png)

## NASM e GAS

O material original apenas listava esses dois nomes, sem detalhá-los; a seguir, um resumo mínimo de propósito geral sobre cada um, para contextualizar sua diferença em relação ao MIPS visto acima:

- **NASM** (*Netwide Assembler*) — é um dos montadores (*assemblers*) mais populares para a arquitetura x86/x86-64, utilizando a sintaxe **Intel**, em que o destino da operação vem antes da origem (por exemplo, `mov eax, ebx` move o conteúdo de `ebx` para `eax`). É amplamente usado em projetos de sistemas operacionais, bootloaders e código de baixo nível que roda diretamente sobre hardware x86, justamente por gerar binários simples e por sua sintaxe ser considerada mais legível por muitos programadores.
- **GAS** (*GNU Assembler*) — é o montador padrão do projeto GNU (parte do *binutils*, usado por padrão pelo GCC), e tradicionalmente utiliza a sintaxe **AT&T**, em que a ordem dos operandos é invertida em relação à sintaxe Intel (o destino vem depois da origem — por exemplo, `movl %ebx, %eax` move o conteúdo de `ebx` para `eax`), além de usar prefixos como `%` para registradores e `$` para valores imediatos. É o montador mais comumente encontrado "por debaixo dos panos" em sistemas Linux, já que é o utilizado pelo GCC para gerar código objeto a partir de código assembly embutido (*inline assembly*) ou gerado pelo compilador.

Em ambos os casos, o princípio fundamental é o mesmo observado no MIPS: um pequeno conjunto de instruções que manipulam registradores e memória diretamente, sem as abstrações (variáveis nomeadas, tipos, estruturas de controle de alto nível) presentes em linguagens como C — a diferença está na arquitetura de hardware-alvo (x86/x86-64, ao invés de MIPS) e na sintaxe de escrita das instruções.
