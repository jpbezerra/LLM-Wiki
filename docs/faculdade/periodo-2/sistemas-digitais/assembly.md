# Assembly

- MIPS
    - Instruções
        - Instruções com até 3 operandos (registradores)
    - Registradores
        - Há 32 registradores de 32 bits cada
        - Possui o $ antecendendo o seu nome
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%201.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%202.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%203.png)
        
    - Load (lw)
        - Instrução de movimentação de dados da memória para o registrador
        - Operação de leitura da memória
        - Usa para o tipo .word
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%204.png)
        
    - Store (sw)
        - Instrução de movimentação de dados do registrador para a memória
        - Operação de escrita na memória
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%205.png)
        
    - Move (move)
        - Intrução para passar o conteúdo de um registrador para outro registrador
        - Memória RAM nã é envolvida
    - li
        - Atribuir um número ao registrador
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%206.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%207.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%208.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%209.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2010.png)
        
        - Para armazenar floats e doubles usamos os registradores $fx
            - Devemos armazenar os doubles nos registradores pares
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2011.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2012.png)
        
    - la
        - Copia o endereço do label na memória para o registrador dado
        - Usa para o tipo .byte ou .asciiz
    - add (adicionar): usa dois registradores
    - addi: usa um operando e um inteiro
    - sub (subtrair)
    - subi: usa um operando e um inteiro
    - mul: multiplicar
    - div(divisão inteira)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2013.png)
        
    - mflo: move o conteúdo de lo
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2014.png)
        
    - mfhi: move o conteúdo de hi
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2015.png)
        
    - sll (multiplicar por potências de dois)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2016.png)
        
        - Basicamente, se fizermos sll $s3, $s2 ( = 10), 10; estaremos multiplicando 10 por 2^10 = 10240
    - srl (dividir por potências de dois)
        - Exemplo, srl $s0, $s4 (= 10240), 5; estaremos fazendo 10240 / (2 ^ 5) = 320
        - Só é capaz de pegar a parte inteira
    - .data: especificação de algumas variáveis, lida com os dados na memória principal
        - Criando uma variável que é uma string, usamos o .asciiz (se for char usar .ascii)
    - .text: intruções em si
    - Ordem de impressão: syscall (imprime o que está dentro do registrador $a0)
    - Condicionais
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2017.png)
        
        - Não existe else, apenas if’s
    - Laços de repetição
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2018.png)
        
    - Funções
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2019.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2020.png)
        
        - jal: chamar a função
        - jr: voltar para quem chamou a função
        - $ra: registrador específico para o enderço de retorno de funções
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2021.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2022.png)
        
    - Arrays (vetores)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2023.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2024.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2025.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2026.png)
        
    - Manipulação de arquivos de texto
        - Abrir
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2027.png)
            
            - Não existe modo de leitura e escrita simultâneo
        - Ler
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2028.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2029.png)
            
            - li $v0, 13 indica o modo leitura; la $a0, file no $a0 tem que passar o endereço do arquivo; li $a1, 0 é a flag de abertura de arquivo (0 - leitura, 1 - escrita)
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2030.png)
            
            - li $v0, 14 indica que vamos ler o arquivo; ao invés de la $a2, tamanhoBuffer é li $a2, tamanhoBuffer
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2031.png)
            
        - Escrever
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2032.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2033.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2034.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/sistemas-digitais/assembly/Untitled%2035.png)
            
- NASM
- GAS