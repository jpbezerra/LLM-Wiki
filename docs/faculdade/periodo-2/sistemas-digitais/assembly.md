# Assembly

<details>
<summary>MIPS</summary>
	<details>
	<summary>Instruções</summary>
		- Instruções com até 3 operandos (registradores) 
	</details>
	<details>
	<summary>Registradores</summary>
		- Há 32 registradores de 32 bits cada
		- Possui o \$ antecendendo o seu nome
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Load (lw)</summary>
		- Instrução de movimentação de dados da memória para o registrador
		- Operação de leitura da memória
		- Usa para o tipo .word
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Store (sw)</summary>
		- Instrução de movimentação de dados do registrador para a memória
		- Operação de escrita na memória
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Move (move)</summary>
		- Intrução para passar o conteúdo de um registrador para outro registrador
		- Memória RAM nã é envolvida
	</details>
	<details>
	<summary>li</summary>
		- Atribuir um número ao registrador
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		- Para armazenar floats e doubles usamos os registradores \$fx
			- Devemos armazenar os doubles nos registradores pares
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>la</summary>
		- Copia o endereço do label na memória para o registrador dado
		- Usa para o tipo .byte ou .asciiz
	</details>
	- add (adicionar): usa dois registradores
	- addi: usa um operando e um inteiro
	- sub (subtrair)
	- subi: usa um operando e um inteiro
	- mul: multiplicar
	- div(divisão inteira)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	- mflo: move o conteúdo de lo
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	- mfhi: move o conteúdo de hi
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	- sll (multiplicar por potências de dois)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		- Basicamente, se fizermos sll \$s3, \$s2 ( = 10), 10; estaremos multiplicando 10 por 2\^10 = 10240
	- srl (dividir por potências de dois)
		- Exemplo, srl \$s0, \$s4 (= 10240), 5; estaremos fazendo 10240 / (2 \^ 5) = 320 
		- Só é capaz de pegar a parte inteira
	- .data: especificação de algumas variáveis, lida com os dados na memória principal
		- Criando uma variável que é uma string, usamos o .asciiz (se for char usar .ascii)
	- .text: intruções em si
	- Ordem de impressão: syscall (imprime o que está dentro do registrador \$a0)
	<details>
	<summary>Condicionais</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		- Não existe else, apenas if’s
	</details>
	<details>
	<summary>Laços de repetição</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Funções</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		- jal: chamar a função
		- jr: voltar para quem chamou a função
		- \$ra: registrador específico para o enderço de retorno de funções
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Arrays (vetores)</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
	</details>
	<details>
	<summary>Manipulação de arquivos de texto</summary>
		<details>
		<summary>Abrir</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			- Não existe modo de leitura e escrita simultâneo
		</details>
		<details>
		<summary>Ler</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			- li \$v0, 13 indica o modo leitura; la \$a0, file no \$a0 tem que passar o endereço do arquivo; li \$a1, 0 é a flag de abertura de arquivo (0 - leitura, 1 - escrita)
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			-  li \$v0, 14 indica que vamos ler o arquivo; ao invés de la \$a2, tamanhoBuffer é li \$a2, tamanhoBuffer
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		</details>
		<details>
		<summary>Escrever</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/d5b5d6cba485460d90d416df7188cbd9)*
		</details>
	</details>
</details>
<details>
<summary>NASM</summary>
</details>
<details>
<summary>GAS</summary>
</details>
