# COMPILADORES

[https://www.youtube.com/@LeopoldoTeixeiraCInUFPE/playlists](https://www.youtube.com/@LeopoldoTeixeiraCInUFPE/playlists)
[https://if688.github.io](https://if688.github.io/)
[https://github.com/if688/if688.github.io/tree/master](https://github.com/if688/if688.github.io/tree/master)
---
## Conceitos
<details>
<summary>Linguagem</summary>
	- É um sistema de comunicação baseado em símbolos e regras, essencial para a comunicação
	- Como expressar uma linguagem que uo computador entenda? Linguagens de programação
</details>
<details>
<summary>Compilador</summary>
	- Antes de um programa ser executado, é preciso traduzi-lo em algo que um computador possa executar
	- Essa tradução é feita através dos compiladores, que possuem a função de traduzir de uma linguagem fonte para uma linguagem alvo
		- Existem diversas linguagens que fazem explitamente o processo de compilação primeiro para depois executar o programa → linguagens compiladas
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
	- Ao ser compilado, o programa alvo vira um executável
		- Existem linguagens que abstraem a parte de compilação e executa diretamente o programa → linguagens interpretadas
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
</details>
- Existem linguagens que misturam as duas partes, utilizando um programa intermediário e uma máquina virtual para executar os programas
	- Tradutor gera código intermediário e máquina virtual executa este código
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
- Os compiladores não tentam traduzir o código inteiro de uma vez, mas aplicam o “dividir para conquistar” a fim de quebrar o código em módulos independentes
	- Por isso, os compiladores possuem duas grandes fases: análise e síntese
---
## Fases da Compilação
- O Front End simboliza a fase de análise e o Back End simboliza a fase de síntese
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
<details>
<summary>Análise</summary>
	- Serve para transformar o código fonte textual em uma IR válida, correta e livre de erros para que o compilador consiga entender e trabalhar
	<details>
	<summary>Etapas</summary>
		<details>
		<summary>Análise Léxica (Scanner)</summary>
			- Converte o texto do programa em tokens, a fim de identificar a estrutura básica do código
				- Os tokens podem conter algum valor associado
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
			<details>
			<summary>Conceitos</summary>
				- Token: par com o nome do token e atributos opcionais
					- São especificados por meio de expressões regulares
				- Lexema: sequência de caracteres que casam com o padrão de um tipo de token
				- Padrão: descrição de possíveis lexemas associados a um tipo de token
			</details>
			- O projetista do compilador caracteriza o analisador léxico por meio de expressões regulares (ERs), a geração do analisador léxico é automática a partir da definição das ERs
				<details>
				<summary>Expressão regular</summary>
					- Formalismo denotacional definida a partir de conjuntos básicos, concatenação e união
					<details>
					<summary>Operadores regulares</summary>
						<details>
						<summary>Operador .</summary>
							- . → reconhece qualquer caractere exceto “\\n”
							- a.c → abc, aac, acc, a9c, etc.
						</details>
						<details>
						<summary>Operador \*</summary>
							- r\* permite zero ou mais repetições de r
							- r\* reconhece “”, “r”, “rr”, etc.
						</details>
						<details>
						<summary>Operador +</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						<details>
						<summary>Operador ?</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						<details>
						<summary>Operador \|</summary>
							- Significa “ou”
							- r1 \| r2 → r1 ou r2
						</details>
					</details>
					<details>
					<summary>Classes de caracteres</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						- Também existe \[\^xyz\], significa qualquer caractere exceto x,y e z
						- \[\^0-9\] → qualquer caractere exceto dígito
					</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					</details>
				</details>
			- É preciso definir a microsintaxe da linguagem (os tokens e lexemas), definir critérios de separação e agregação de palavras, estabelecer palavras especiais e reservadas e implementar o analisador a partir da especificação
			<details>
			<summary>Exemplos</summary>
				<details>
				<summary>1</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>2</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
			</details>
			<details>
			<summary>Reconhecimento de tokens</summary>
				- Para reconhecer os tokens, é necessário gerar diagramas de transição e depois implementar uma máquina de estados combinando estes diagramas
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
			</details>
			- Lexer interage ditamente com o parser
				- Ajuda no reconhecimento de erros
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
		</details>
		<details>
		<summary>Análise Sintática (Parser)</summary>
			- Usa os tokens gerados na análise léxica para construir uma árvore sintática e verificar se a estrutura do código segue a gramática da linguagem
				- Cada nó interno da árvore representa uma operação e os nós filhos representam argumentos
			- Serve para detectar erros da estrutura
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
			</details>
			<details>
			<summary>Casos</summary>
				- Caso o parser ocorra perfeitamente, então a sintaxe do programa está correta e a tring de entrada está bem formatada
				- Caso contrário, há um erro de sintaxe ou violação das regras de sintaxe
				- Independente dos casos, o programa pode ainda conter erros capturados ou não pelo type checker
			</details>
			<details>
			<summary>Gramática</summary>
				- A gramática de livre contexto (GLC) caracteriza a linguagem e o parser gerado a partir de uma GLC pode ser automatizado
					- Para cada classe gramatical da GLC haverá uma estrutura de dados correspondente
				- Derivamos palavras de uma gramática G a partir do seu símbolo inicial e repetidamente substituindo não-terminais pelo corpo de uma produção
					- A linguagem gerada por G chama-se L(G) e inclui todas as strings que podemos obter através de derivações em G
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					</details>
				<details>
				<summary>Expressões regulares vs Gramáticas livres de contexto</summary>
					- Tudo que pode ser escrito por uma ER pode ser escrito com GLC, mas:
						- Regras léxicas são mais especificadas mais simplesmente com ER
						- ER geralmente são mais concisas e simples
						- Podem ser gerados analisadores léxicos mais eficientes a partir de expressões regulares
						- Estrutura/modulariza o front-end do compilador
					- ER são convenientes para especificar a estrutura de construções léxicas, como identificadores, constantes, palavras, chave e etc.
					- Usamos gramáticas para especificar estruturas aninhadas, como parênteses, begin-end, if-then-else e etc.
				</details>
				<details>
				<summary>Derivação</summary>
					- Dada uma gramática G, produz uma string s que faz parte de L(G)
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
			</details>
			<details>
			<summary>Parsing</summary>
				- Dada uma string s em L(G), produz uma árvore sintática que demonstra como obter a derivação de s
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				- Para gramáticas livres de contexto sempre é possível construir um parser com complexidade O(n³) para fazer o parsing de n tokens
					- Na prática, o parsing de linguagens de programação normalmente pode ser feito linearmente
					- Travessia linear da esquerda para a direita, olhando um token de cada vez
				- Parsers devem ler não apenas os símbolos terminas, mas também o marcador de fim de arquivo (EOF)
					- Usa-se \$ para representar o fim do arquivo
					- S’ → S\$
				<details>
				<summary>Categorias</summary>
					- Métodos de parsing universais: funcionam para qualquer gramática, mas são muito ineficientes (inviáveis para uso prático)
					<details>
					<summary>Top down</summary>
						- Constroem as parse trees a partir da raiz em direção às folhas
						<details>
						<summary>Método</summary>
							- A partir do símbolo inicial da gramática, consuma tokens da esquerda para a direita
							- Decida que produção aplicar, de acordo com o token retornado
							- Continue até que um dos casos seja verdadeiro:
								- Todas as folhas sejam símbolos terminais e não há mais tokens a serem lidos da entrada
								- Ocorra uma falta de correspondência entre a entrada e as folhas da parse tree parcialmente construída
									- Nesse, caso utiliza backtracking e restaura o estado anterior à última escolha
						</details>
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						<details>
						<summary>Backtracking</summary>
							- É interessante ter parsers que não fazem backtracking, pois causa ineficiência de código
								- Principalmente em parser top-down e leftmost
							- Como solução, o ideal é realizar um predective parsing
						</details>
						<details>
						<summary>Predective parsing</summary>
							- O token lido como primeiro terminal deve fornecer informação suficiente para decidirmos que produção aplicar
							<details>
							<summary>Situações que geram problemas para predective parsing</summary>
								<details>
								<summary>Recursão à esquerda</summary>
									- Uma gramática é recursiva à esquerda se existe um não terminal A tal que existe uma derivação de A que gera Aα, para alguma string α
									- Existem técnicas para eliminar a recursão à esquerda automaticamente
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									<details>
									<summary>Técnicas</summary>
										<details>
										<summary>Reescrever produções tornando-as recursivas à direita</summary>
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- Exemplo
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										</details>
										<details>
										<summary>Fatoração à esquerda</summary>
											- Técnica de transformação de gramática usada para produzir uma gramática adequada para predective parsing
											- Combina os casos em que há mais de uma alternativa a partir do reconhecimento de um token
											- Existem algoritmos para fazer a fatoração à esquerda
											- Exemplo
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												- Solução
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										</details>
									</details>
								</details>
								<details>
								<summary>Ambiguidade</summary>
									- Uma gramática é dita ambígua quando gera mais de uma parse-tree para a mesma string
										- Interpretação pode ser diferente de<br>acordo com estrutura derivada
										- Exemplo
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
							</details>
							<details>
							<summary>Gramática preditiva</summary>
								<details>
								<summary>Características</summary>
									- É uma gramática LL(1)
										- O parser lê a entrada da esquerda para a direita
										- Produz uma derivação mais à esquerda (leftmost derivation)
										- Usa 1 símbolo lookahead para decidir qual regra aplicar
									- É uma gramática não ambígua, cada entrada (símbolo terminal) leva a no máximo uma produção possível
									- Não é recursiva à esquerda → não pode ter produções que começam com o próprio não terminal
									- Fatorada à esquerda (left-factored) → se duas produções de um mesmo não terminal começam com o mesmo prefixo, este prefixo deve ser extraído
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
								- A construção dos parsers top-down e bottom-up é auxiliada pelos conjuntos e funções de FIRST e FOLLOW, que auxiliam o parser a decidir qual produção será aplicada com base no próximo símbolo de entrada
								- Classe rica o suficiente para cobrir a maioria das construções de linguagens de programação
								<details>
								<summary>FIRST</summary>
									- FIRST(α), onde α é qualquer string de símbolos da gramática, é o conjunto de terminais que iniciam strings derivadas a partir de α
									- Se α pode gerar ε, ε pertence a FIRST(α)
									<details>
									<summary>Exemplo</summary>
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									</details>
									<details>
									<summary>Como calcular FIRST(X)</summary>
										- Se x é um terminal FIRST(X) = \{x\};
										- Se X → ε, ε ∈ FIRST(X)
										- Se X → Y1Y2...Yk, FIRST(Y1Y2...Yk) ⊆ FIRST(X)
										- FIRST(Y1Y2...Yk) é
											- \[ε ∉ FIRST(Y1)\] FIRST(Y1); ou
											- \[ε ∈ FIRST(Y1)\] FIRST(Y1 \{ε\} ∪ FIRST(Y2...Yk)
											- Se ε ∈ FIRST(Yj) para todo j de 1 a k, ε ∈ FIRST(Y1Y2...Yk)
									</details>
								</details>
								<details>
								<summary>FOLLOW</summary>
									- FOLLOW(A), onde A é um não-terminal, é o conjunto de terminais α que pode aparecer imediatamente à direita de A numa palavra
									- Se A pode ser a última produção à direita, \$ pertence a FOLLOW(A)
									<details>
									<summary>Exemplo</summary>
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									</details>
									<details>
									<summary>Como calcular FOLLOW</summary>
										- \$ ∈ FOLLOW(S), onde S é o símbolo inicial e \$ é fim da entrada
										- Se existe uma produção A → αBβ, tudo que pertence a FIRST(β) exceto ε está em FOLLOW(B)
										- Se existe uma produção A → αB, então tudo que estiver em FOLLOW(A) estará em FOLLOW(B)
										- Se existe uma produção A → αBβ, e ε ∈ FIRST(β), tudo que estiver em FOLLOW(A) estará em FOLLOW(B)
									</details>
								</details>
							</details>
							<details>
							<summary>LL(1) table-driven parsing</summary>
								<details>
								<summary>Parsing Table</summary>
									- Mapa que diz quão ação tomar com base no estado atual e no próximo símbolo de entrada, representadas como uma matriz bidimensional
									- Construída com base nos conjuntos FIRST e FOLLOW, com uma tabela auxiliar
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									- Depois constrói a tabela M\[A, a\] onde A é um não terminal e a um símbolo terminal (incluindo \$)
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									<details>
									<summary>Algoritmo</summary>
										- Para cada produção A → α de G
											- Para todo a ∈ FIRST(α), adicione A → α em M\[A,a\]
												- Se ε ∈ FIRST(α), então, para todo b ∈ FOLLOW(A), adicione A → α em M\[A,b\]
												- A regra acima leva em conta também o símbolo \$
											- Posições em branco na tabela são error
									</details>
									<details>
									<summary>Exemplo</summary>
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									</details>
								</details>
								<details>
								<summary>Gramática LL(1)</summary>
									- G é LL(1) se, e somente se, quando A → α \| β são duas produções distintas de G e as condições abaixo são satisfeitas
										- Para nenhum terminal a, α e β geram palavras iniciadas<br>em a
										- No máximo um de α e β deriva a palavra vazia
										- Se β gera ε por meio de derivação sucessiva, α não pode<br>derivar palavras iniciadas com terminais de FOLLOW(A)
										- Se α gera ε por meio de derivação sucessiva, β não pode<br>derivar palavras iniciadas com terminais de FOLLOW(A)
									<details>
									<summary>Exemplos</summary>
										- Gramática LL(1)?
										<details>
										<summary>1</summary>
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- Não, pois a produção A→Abc é uma recursão à esquerda
											- Além disso FIRST(Abc) contém FIRST(A), que é \{b\}, significando que M\[A,b\] tentaria conter duas produções
										</details>
										<details>
										<summary>2</summary>
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- FIRST(eS) = \{e\}, logo, M\[S’, e\]=S’→eS
											- Entretanto, como FIRST(ε) = \{ε\}, precisamos olhar para o FOLLOW(S’) = \{\$, e\}
												- Para \$, M\[S’, \$\] = S’ → ε
												- Para e, M\[S’, e\] = S’ → ε
												- Porém, em M\[S’, e\] já existe S’ → eS, causando um conflito
											- Logo, não é gramática LL(1)
										</details>
									</details>
								</details>
								<details>
								<summary>Exemplo</summary>
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
							</details>
						</details>
						<details>
						<summary>Non-Recursive Predective Parsing</summary>
							- Um parser preditivo não recursivo pode ser construído mantendo uma pilha explicitamente, ao invés de implicitamente por chamadas recursivas
							- Se w é a entrada que foi casada até o momento, a pilha vai manter uma sequência de símbolos da gramática tais que S →\* wα
							<details>
							<summary>Exemplo</summary>
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
						</details>
						<details>
						<summary>Recursive-descent parsing</summary>
							- Método de análise sintática top-down em que um conjunto de procedimentos recursivos é usado para processar a entrada
								- Cada procedimento está associado a um símbolo não-terminal da gramática
								- Predective parsing é um caso especial de recursive descent parsing em que o símbolo lookahead determina sem ambiguidades o procedimento a ser chamada para cada não-terminal
						</details>
					</details>
					<details>
					<summary>Bottom up</summary>
						- Constroem as parse trees a partir das folhas, com a ideia de converter o programa de entrada para o símbolo inicial
							- O parser lê tokens até que tenha uma subpalavra w que case com o lado direito de uma produção A → B e ao chegar nesse estágio substitui B por A se isto resultar em uma derivação válida
							- Essa substituição é chamada de redução
							<details>
							<summary>Exemplo</summary>
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								<details>
								<summary>Outra visualização</summary>
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									- Derivações
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
							</details>
						- Uma redução transforma a entrada uwv em uAv se A → w é uma produção da gramática
						<details>
						<summary>Handle</summary>
							- Um handle é uma substring w e uma produção A → w tal que, reduzindo uwv → uAv permite que o símbolo inicial seja alcançado de uAv, ou seja, uma produção que podemos reduzir sem que seja gerado um problema
							<details>
							<summary>Exemplo de “falso” handle</summary>
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
							- Identificação de handles
								<details>
								<summary>Análise de shift-reduce</summary>
									- A ideia é dividir a entrada em duas partes, ilustrada pelo marcador \| ou •
										- À direita do marcador existem terminais ainda não reduzidos e à esquerda existem terminais e não-terminais
										- A parte mais a direita (ou imediatamente à esquerda) contém um potencial candidato a handle
									- Handles e reduções só ocorrem na substring da esquerda e a da direita apenas terminais
										- A cada passo da análise precisa se decidir entre shift ou reduce
										- Shift: deslocar o foco à direita → jogando um terminal para a substring da direita
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										- Reduce: aplicar uma redução a um handle
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										- Caso não consiga fazer nenhuma das duas ações, isso significa erro sintático
								</details>
								<details>
								<summary>Shift-reduce parsing</summary>
									- Toda redução é na parte mais à direita da substring da esquerda
										- Se representar esta substring como uma pilha, o shift empilha um token e o reduce desempilha símbolos da pilha e empilha o não-terminal apropriado
										- Ou seja, em reduce para A → w, desempilha \|w\| e empilha A
										- A redução ocorre quando o conteúdo da pilha for um handle
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									- Para reconhecer os handles, deve-se olhar para a pilha e o lookahead
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									- O conjunto de prefixos viáveis de uma gramática é uma linguagem regular, logo, pode-se utilizar AFD’s para determinar se o conteúdo da pilha corresponde a um prefixo viável ou não
									- Toda gramática LR(0) é analisada por um shift-reduce parsing
										<details>
										<summary>LR(0)</summary>
											<details>
											<summary>Classificação</summary>
												- L → lê a entrada da esquerda para a direita
												- R → procura a derivação mais à direita
												- (k) → número de tokens lookahead lidos, mas não consumidos
											</details>
											- O parsing pode ser feito olhando apenas o conteúdo da pilha
											- Não usa lookahead para decidir entre ações de shift e reduce
											- Classe razoavelmente fraca de gramáticas
											- Algoritmo de construção de tabelas é útil como introdução a algoritmos LR(1)...
											<details>
											<summary>Exemplos</summary>
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												<details>
												<summary>Construção do parsing table</summary>
													<details>
													<summary>Regras</summary>
														- sn → shift e vá para o estado n
														- gn → vá para o estado n
														- rk → reduza pela regra k
														- a → aceite a entrada
														- erro → entradas em branco
													</details>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
											</details>
										</details>
									<details>
									<summary>Parsing</summary>
										- Ao invés de reescanear a pilha para cada token, pode lembrar o estado alcançado para cada elemento da pilha
										- O algoritmo consiste em olhar para o estado no topo da pilha e o símbolo  de entrada para definir a ação
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										<details>
										<summary>Exemplo</summary>
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- Empilha o estado 1 inicialmente
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[1, (\] = s3, empilha o estado 3
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[3, x\] = s2, empilha o estado 2
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[2, ,\] = r2, então reduz para a regra 2 substituindo o x por S e volta para o estado 3 (1 símbolo)
												- M\[3, S\] = g7, logo empilha 7
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[7, ,\] = r3, então reduz para a regra 3 substituindo o S por L e volta para o estado 3 desempilhando 7 (1 símbolo)
												- M\[3, L\] = g5, logo empilha 5
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[5, ,\] = s8, empilha o estado 8
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[8, x\] = s2, empilha o estado 2
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[2, )\] = r2, então reduz para a regra 2 substituindo x por S e volta para o estado 8 desempilhando 2 (1 símbolo)
												- M\[8, S\] = g9, logo empilha 9
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[9, )\] = r4, então reduz para a regra 4 substituindo L,S por L e volta para o estado 8 desempilhando 9, 8 e 5 da pilha (pois são 3 símbolos) ficando 3 no topo
												- M\[3, L\] = g5, logo empilha 5
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[5, )\] = s6, empilha o estado 6
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[6, \$\] = r1, logo reduz (L) por S desempilhando 6, 5 e 3 (pois são 3 símbolos) ficando 1 no topo da pilha
												- M\[1, S\] = g4, empilha o estado 4
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											- M\[4, \$\] = a, logo aceita a entrada
										</details>
										<details>
										<summary>Problemas</summary>
											- Problemas na gramática ou limitações da técnica escolhida podem levar a conflitos
												- shift-reduce: não consegue decidir entre uma ação de shift (ou mais) ou reduce
												- reduce-reduce: não tem como decidir entre duas ou mais ações de reduce, geralmente por ambiguidade ou algum bug na gramática
												<details>
												<summary>Exemplo de shift-reduce em M\[1, +\]</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
											- Para resolver estes conflitos, realiza-se uma análise SLR
												<details>
												<summary>Análise SLR</summary>
													- Utiliza o conjunto FOLLOW para resolver conflitos
													- Intuição: só reduz se o próximo token (lookahead) estiver no conjunto FOLLOW do não-terminal associado
													- Na tabela de parsing, só inclui ação de reduce, caso o terminal esteja no conjunto FOLLOW
													- Autômatos SLR
														- Estados podem ter mais de um item de redução, caso conjuntos FOLLOW sejam distintos
														- Estados podem misturar itens de shift com itens de redução, caso os terminais associados ao shift não estejam no FOLLOW dos itens de redução
														- Isso não elimina todos os tipos de conflitos
															> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													- Para um recurso ainda mais poderoso, existem as linguagens LR(1)
												</details>
										</details>
									</details>
									<details>
									<summary>LR(1)</summary>
										- Mais poderoso que SLR
										- Suficiente para grande parte das linguagens de programação
										- A noção de item é mais sofisticada, inclui o símbolo de lookahead
										- Simulam dois processos simultaneamente
										- Compreendem o autômato LR(0) para encontrar handles
										- Um rastreador de tokens de lookahead, para determinar qual o lookahead atual
										- Remover os lookaheads de um autômato LR(1) resulta em um autômato LR(0) muito maior para a mesma gramática
										<details>
										<summary>Construção do Autômato LR(1)</summary>
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											<details>
											<summary>Exemplo</summary>
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												<details>
												<summary>Passo 1 (pode-se incrementar o conjunto dentro dos colchetes, como S → •\[\$, +\])</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 2</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 3</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 4</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 5</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 6</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 7</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 8</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Passo 9</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Autômato final</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
												<details>
												<summary>Tabela de parsing</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
											</details>
										</details>
									</details>
								</details>
						</details>
					</details>
				</details>
			</details>
		</details>
		<details>
		<summary>Análise Semântica</summary>
			- Valida o significado das expressões, detectando erros  mais profundos que não envolvem a forma do código, mas sim o sentido
				- Usa a árvore sintática e a tabela de símbolos para checar a consistência semântica com a definição da linguagem
				- A linguagem pode permitir coercions → conversão automática de tipos compatíveis
			- Uma vez encerrada, consideramos o programa de entrada válido
			- O maior desafio é rejeitar o maior número de programas incorretos e acertar o maior númeo de programas corretos
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
			</details>
			- Limitações de GLC
				- Como previne definições de classes duplicadas?
				- Como diferencia variáveis de um tipo com variáveis de outro tipo?
				- Como garante que uma dada classe implementa todos os métodos de uma interface?
			<details>
			<summary>AST (Árvores Sintáticas Abstratas)</summary>
				- Sintetizar as informações de uma parse tree, focando mas informações importantes e classificando os nós de acordo com seu papel na estrutura da linguagem
				- Representação compacta que facilita o trabalho do compilador
				- Utiliza-se as AST’s para criar estruturas de dados em código
					- Para toda AST é preferível que exista um interpretador que executa as ações que cada nó da árvore representa, sendo geralmente uma função recursiva mantendo o estado do programa
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Árvore sintática
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- AST
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Direções de Modularidade</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Visitor Design Pattern</summary>
					- Padrão de modelagem de AST’s que centraliza as funcionalidades em um objeto Visitor que encapsula as operações das AST’s e recebe a própria AST como um parâmetro das funções
					- Possui a finalidade de separar os algoritmos das estruturas de dados em que ele opera, permitindo adicionar novas operações a uma estrutura complexa sem precisar modificar as classes desses objetos
				</details>
			</details>
			<details>
			<summary>Checagem de Tipos (Type-Checking)</summary>
				- Um tipo é uma categoria de elementos de programação
				- A checagem de tipos é o primeiro passo da análise semântica
					- Consiste em duas atividades: inferência de tipos e checagem
					- A checagem pode ser feita de maneira estática ou dinâmica
				<details>
				<summary>Sistema de Tipos</summary>
					- Coleção de regras que limitam como um programa pode ser escrito
					- Garante a segurança em tempo de execução
					- A checagem de tipos verifica se as regras do sistema de tipos estão sendo respeitadas
					- Strong → sistemas que nunca permitem erros de tipo
					- Weak → podem permitir erros de tipo
					<details>
					<summary>Componentes</summary>
						- Built-in
							- Tipos pré-definidos para certos grupos de dados, como números, booleanos e caracteres
							- Variam entre as linguagens de programação
						- Tipos compostos
							- Consistem de um ou mais objetos, cada um com seu próprio tipo, como arrays, strings e enums
							- É possível criar Structures (Records) que agrupam múltiplos objetos de tipos arbitrários
							- Ponteiros são tipos especiais, pois conseguem manipular memória
							- Criação de novos tipos a partir dos existentes
						- Equivalência
							- As linguagens precisam ter regras sem ambiguidade para responder se dois tipos diferentes são equivalentes
							- Name Equivalence
								- Dois tipos são equivalentes se e somente se tem o mesmo nome
								- Se o programador escolheu nomes diferentes, a linguagem deve respeitar este ato
								- Porém. a complexidade da tarefa de gerenciar a consistência dos nomes cresce com o tempo
							- Structural equivalence
								- Dois tipos são equivalentes se tem mesma estrutura
								- Dois objetos podem ser trocados se consistem do mesmo conjunto de campos, na mesma ordem, e estes campos tem tipos equivalentes
								- Examina as propriedades essenciais que definem o tipo
						- Regras de inferência 
							- Envolve os tipos de operandos e o tipo de resultado da expressão, como em expressões aritméticas na qual os tipos do lado esquerdo e direito do operando devem ser compatíveis
							- Misturar tipos em expressões pode ser ilegal, chegando a talvez nem compilar
								- O compilador pode fazer conversões implícitas (coercions)
							- Muitas linguagens exigem declarações de variáveis antes do uso, estabelecendo tipos bem definidos
								- Algumas linguagens não exigem declaração prévia, o que pode tornar o problema de inferência de tipos mais complexo
							- Expressões e funções
								- Inferência de tipos de expressões normalmente seguem a estrutura das expressões
								- Podem depender de procedimentos e funções do programa
								- Para isto, funções normalmente definem assinaturas de tipos
					</details>
				</details>
				<details>
				<summary>Gramática de atributos</summary>
					- Formalismo para realizar análise sensível ao contexto, enriquecendo uma GLC com regras especificando computações
						- Cada regra define um atributo em termos dos valores de outros atributos
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							- Atributo type é sintetizado e atributo in é herdado (definidos em termos de nós \]dos ancestrais, irmãos, etc.)
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						<details>
						<summary>Adicionando novas regras</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						<details>
						<summary>Adicionando novas regras novamente</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
					</details>
				</details>
			</details>
			<details>
			<summary>Escopo</summary>
				- Um nome pode ter diferentes significados em um mesmo programa
					- Abstração → processo que associa um nome a um fragmento de programa
					- Binding → associação entre o nome e a funcionalidade a ser nomeada, podendo ser feitas em diferentes momentos de compilação
				- Escopo é uma região do programa na qual um binding de um nome a uma entidade é válido e visível
					- O escopo determina onde pode ver e usar uma variável ou função pelo nome
					- É possível fazer shadowing, na qual acontece quando um mesmo nome é utilizado em escopos diferentes
				- Escopo em OO
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				<details>
				<summary>Passadas</summary>
					- Conseguimos resolver análise léxica e sintática com uma única passada sobre a entrada
						- Alguns compiladores também combinam análise semântica e geração de código, chamados de single-pass compilers
						- Outros passam novamente pela entrada, chamados de multi-pass compilers
							- Ler a entrada e construir a AST (primeira passada), caminhar pela AST coletando informações sobre as classes (segunda passada), caminhar pela AST checando outras propriedades (terceira passada)…
							- Pode combinar algumas destas passadas, embora sejam logicamente distintas
							- As passadas podem ser implementadas usando a estratégia de visitors
				</details>
			</details>
			<details>
			<summary>Tabelas de Símbolos</summary>
				- Mapeamento de nomes para a entidade a que o nome se refere
					- Ao processar declarações de tipos, variáveis, e funções, associamos os identificadores com o seu significado na tabela
					- Ao processar usos de tais identificadores, fazemos o lookup na tabela
				- A implementação deve privilegiar eficiência ao acessar informações, deve ser capaz de ser expandida de forma fácil e eficiente
					- Em geral, implementadas usando hash tables, podendo ser tabelas encadeadas a depender do nível de escopo
						<details>
						<summary>Spaghetti Stacks</summary>
							- Trata a tabela de símbolos como uma lista encadeada de escopos
							- Cada escopo armazena um ponteiro para o seu ancestral mas a recíproca não é verdadeira
							- Em qualquer ponto do programa a tabela pode ser vista como uma pilha
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 2b e 2a são basicamente sibling nodes
						</details>
				<details>
				<summary>Operações</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				- Ao lidar com o escopo, a maioria das linguagens permitem declaração de nomes em múltiplos níveis de escopo
					- Nesse caso, precisa-se adaptar a tabela de símbolos para considerar os escopos
					- O compilador precisa fazer o processo de name resolution, mapeando cada nome referenciado no programa com o nível de escopo
						- A medida que o compilador sai de um escopo, a tabela encadeada é excluída
						- Para lidar com mudanças de escopo, é preciso operações adicionais
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- No nível 3, para calcular b = a + b + c + w, para cada variável o compilador pega o nome no escopo mais perto do escopo atual
						- a → nível 2b
						- b → nível 1
						- c → nível 3
						- 2 → nível 0
				</details>
			</details>
		</details>
	</details>
</details>
<details>
<summary>IR Intermediate Representation</summary>
	- É uma forma abstrata, independente de máquina do programa, que serve como ponte entre o front-end e o back-end
		- Pode ser uma árvore (AST simplificada), código de três endereços, um bytecode intermediário (LLMV, JVM), etc.
		- Durante o processo de tradução um compilador pode construir uma ou mais IRs do programa
	- A separação de fases e o uso do IR é muito útil pois traz várias vantagens práticas, teóricas e arquiteturais
		- A separação de fases melhora a modularização, tratamento de erros e reuso
		- O uso do IR melhora principalmente o quesito de portabilidade, otimização e independência tanto de linguagens quanto de máquinas, permitindo flexibilidade
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
	- Além disso, compiladores mais modernos utilizam mais de uma IR com alguns optimizers
		- Os optimizers são responsáveis por otimizar os IRs, melhorando o desempenho do programa final
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
	- O IR sempre tenta chegar mais próximo da linguagem de máquina
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
	- Ao derivar conhecimento sobre o código, é necessário transmitir esta informação entre as passadas, portanto o compilador precisa de uma representação dos fatos que deriva a partir de um programa
		- Precisa ser expressiva o suficiente para registrar fatos úteis que o compilador precisa transmitir
		- Existem vários tipos de representações intermediárias e a escolha varia de acordo com o compilador como Parse Trees, AST’s e DAG’s
			<details>
			<summary>DAG</summary>
				- É um grafo acíclico dirigido, com o objetivo de eliminar subexpressões comuns e resultar em um código mais rápido e enxuto
				- Para construir é preciso primeiro listar os nós do DAG (na qual cada nó representa um operador ou uma variável) e uma tabela de símbolos (na qual mapeia os identificadores para o nó do DAG que contém o valor mais recente daquela variável)
				- Para otimizar o código, realize apenas as operações aritméticas que estão em formato de nó
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
			</details>
			- Como alternativa a representações gráficas, existem as representações lineares
			<details>
			<summary>Representações lineares</summary>
				- Sequências de instruções que executam em ordem, impondo uma ordem clara e útil
				- Se aproximam de código assembly para uma máquina abstrata
				- Geralmente precisa codificar mecanismos de transferência de controle entre pontos do programa (jumps e conditional branches)
				<details>
				<summary>Tipos de IR Lineares</summary>
					- One-address code
						- Modela o comportamento de acumuladores e máquinas baseadas em pilha
						- Código compacto
						<details>
						<summary>Stack-Machine Code</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
					- Two-address code
						- Modela máquinas que tem operações destrutivas
						- Se tornou menos popular com a redução de restrições de memória
					- Three-address code
						- Modela máquinas em que a maioria das operações recebem dois operandos e produzem resultado (popularidade de RISC)
						- Frequentemente usado como código intermediário
							- Abstrai um assembler, onde cada instrução básica referencia no máximo 3 endereços
							- No máximo um operador no lado direito das instruções
						- Formato → x := y op z
							- Exemplo: x + y \* z é reescrito como → t1 := y \* z, t2 := x + t1
				</details>
				<details>
				<summary>Instruções</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Operadores</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Estruturas de Dados</summary>
					- A representação das instruções de três endereços pode se dar por meio de objetos e/ou registros com campos para os operadores e operandos
					- Quadruples
						- Um “quad”, contém quatro campos: op, arg1, arg2, e result
						- Instruções com operadores unários não usam arg2
						- Operadores como param, não usam arg2 ou result
						- Desvios colocam label em result
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Gerando código IR</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Com a ideia de fluxo de controle, é possível enriquecer a linguagem
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Control-Flow Graph</summary>
					- Representa o fluxo de controle do programa
						- Bastante utilizados em análises de programas para realizar otimizações, instruction scheduling e alocação global de registradores
					- Nós correspondem a blocos básicos de código e as arestas representam o controle sendo transferido
						- Blocos básicos → sequência de operações que sempre executam em conjunto, cada instrução em um bloco básico é executada após todas as instruções anteriores terem sido executadas
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- O CFG fornece uma representação gráfica dos possíveis caminhos do programa em tempo de execução
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						- Podem existir caminhos impossíveis
					<details>
					<summary>Construção</summary>
						- Podemos construir CFGs para representação intermediária de alto nível ou de baixo nível
							- No caso de ASTs, a construção se dá traduzindo cada nó a um CFG e fazendo a composição
							- No caso de representações mais baixo nível, como código de três endereços, por meio da análise de labels e instruções com desvios
						- O CGF de um Statement pode ser definido como CFG(S), um grafo de uma instrução alto nível S na qual ele é um grafo de entrada e saída simples, podendo ser definido recursivamente
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						- Condicionais
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						- Laço de repetição
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						- Este algoritmo recursivo gera um CFG com muitos blocos, gerando uma ineficiência
						- Para realizar uma construção eficiente, é preciso o mínimo de blocos possível de menor tamanho possível
							- Não devem ocorrer pares de blocos (B1, B2) tal que B2 é sucessor de B1, B1 tem uma aresta outgoing e B2 tem uma aresta incoming
							- Não devem ocorrer blocos básicos vazios
							<details>
							<summary>Exemplo</summary>
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
						<details>
						<summary>CFG’s para TAC (Three Address Code)</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
					</details>
				</details>
			</details>
</details>
<details>
<summary>Otimização</summary>
	- Realiza transformações no código com o objetivo de melhorar algum aspecto relevante, podendo ser específicas a uma arquitetura ou geral sem afetar o comportamento do programa
		- O foco da otimização é em IR’s
		- O objetivo é obter o máximo de melhoria com o mínimo de esforço
		- É preciso aplicar transformações com safety e profitability
			<details>
			<summary>Safety</summary>
				- Corretude é o critério mais importante que o compilador deve satisfazer
				- Como saber que uma transformação é segura?
				- O que é o sentido de um programa?
			</details>
			<details>
			<summary>Profitability</summary>
				- Qual a vantagem de aplicar uma transformação como loop unrolling?
					- Diminuir quantidade de iterações
					- Evitar trabalho duplicado
					- Memory bound
			</details>
	<details>
	<summary>Granularidade</summary>
		- Local → aplicada a blocos básicos isoladamente
			<details>
			<summary>Otimizações locais</summary>
				- Forma mais simples
				- Não é necessário analisar o corpo completo do procedimento/método
				<details>
				<summary>Single Assignment form</summary>
					- Representação que visa facilitar otimizações de código
					- Muitas otimizações podem ser simplificadas se cada atribuição é feita a um temporário que ainda não apareceu no bloco básico
					- Código de três endereços pode ser rescrito na forma de static single assignment (SSA)
						<details>
						<summary>SSA</summary>
							- Disciplina de nomes que muitos compiladores modernos usam para codificar informação sobre o fluxo de controle e dados de valores
								- A forma SSA foi intencionada para otimização de código
							- Na forma SSA, nomes correspondem unicamente a pontos específicos de definição no código
								- Cada nome é definido apenas uma vez
								- Como um corolário, cada uso de um nome como argumentos de operação carrega informação sobre o ponto onde o valor foi originado
							- Um programa está na forma SSA quando cada definição tem um nome distinto e todo uso se refere a uma única definição
							- Para transformar um programa em SSA, é necessário inserir funções especiais, denominadas phi, em pontos onde o fluxo de<br>controle converge
							- A propriedade de single-assignment permite ao compilador ficar alheio a muitas questões associadas ao tempo de vida de valores
								- Nomes nunca são redefinidos ou mortos, o valor está sempre disponível a partir de um caminho
							<details>
							<summary>Exemplo</summary>
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
						</details>
				</details>
				<details>
				<summary>Formas de otimizações locais</summary>
					- Simplificações algébricas
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Constant Folding
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Copy Propagation
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Copy propagation + Constant folding
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Eliminando common subexpressions
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Dead code elimination
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Exemplo de Otimização</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Simplificação algébrica
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Copy Propagation
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Constant Folding
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Common Subexpression Elimination
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Copy Propagation
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Dead Code Elimination
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				</details>
				<details>
				<summary>Como eliminar expressões redundantes</summary>
					- Assuma que queremos eliminar expressões redundantes de um bloco básico
					- Uma expressão e é redundante em p se já foi avaliada em todos os caminhos que levam a p
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- A otimização só será aplicada se não for necessário avaliar novamente (safety)
					- É interessante substituir avaliações redundantes com referências a valores computados anteriormente (profitability)
					<details>
					<summary>Local Value Numbering</summary>
						- Técnica para implementar a eliminação de um código que está em SSA
						- Faz uma travessia no bloco básico e assinala números distintos a cada valor que o bloco computa
						- Chave: Escolher números de tal forma que duas expressões ei e ej tem o mesmo valor sse os valores dos operandos são comprovadamente iguais
							- Hashing de operações, para armazenar expressões já calculadas
						- Exemplo
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					</details>
				</details>
			</details>
		- Global (intra-procedural) → aplicada a um CFG isoladamente
			<details>
			<summary>Otimizações Globais</summary>
				- Operam em um procedimento ou método inteiro (ou seja, um CFG inteiro)
					- Modificam múltiplos blocos básicos
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						- Existem situações que podem não ser otimizados
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				<details>
				<summary>Data-flow Analysis</summary>
					- Antes de aplicar uma otimização, é necessário localizar pontos onde o programa pode ser modificado para melhor
						- Para coletar esta informação, o compilador normalmente usa algum tipo de análise estática
						- Geralmente inicia-se com algum tipo de análise do fluxo de controle, para montar um CFG
						- A partir do CFG, podemos analisar como os valores fluem por meio do código (data-flow analysis)
					- É feito de forma iterativa
						- Geralmente construídas a partir de um conjunto de equações definidas a partir de conjuntos
						- Estas equações definem como dados são transferidos entre blocos básicos (funções de transferência)
						- A solução para estas equações é um algoritmo de ponto fixo, simples e robusto
				</details>
				<details>
				<summary>Corretude</summary>
					- Forma de saber que está tudo certo com a propagação de uma constante
					- Para substituir o uso de x por uma constante k, devemos garantir a seguinte condição
						- Em todos os caminhos onde há um uso de x, a última atribuição a x é x = k
						- Chamaremos esta condição de Φ
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
					- Checagem de corretude
						- Não é trivial
						- Ao quantificarmos todos os caminhos, precisamos incluir loops e branches de condicionais
						- Checar esta condição requer análise global (análise do CFG para um corpo de método)
				</details>
				- Otimizações globais dependem do conhecimento de uma propriedade P em um ponto particular da execução do programa, de modo a provar que P em qualquer ponto requer conhecimento do corpo inteiro do método
					- Existem otimizações globais indecidíveis
					- A otimização só é aplicada apenas quando se tem certeza absoluta
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				<details>
				<summary>Global constant propagation</summary>
					- Em cada ponto do programa associa-se um valor possível valor para x
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						<details>
						<summary>Exemplo</summary>
							- 1
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							- 2
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
					- Dado que temos informações globais, é fácil de realizar a otimização
						- Basta inspecionar as propriedades x = ? associadas com instruções que usam x
						- Se x for constante naquele ponto, substitua o uso de x pela constante
						- A ideia é transferir a informação de uma instrução para a próxima
							- Para cada instrução s, computamos a informação sobre o valor de x imediatamente antes e depois de s
							- Cin(x,s) = valor de x antes de s
							- Cout(x,s) = valor de x após s
					- A informação é propagada por meio de funções de transferência entre instruções, definidas por meio de regras
						<details>
						<summary>Funções de transferência</summary>
							<details>
							<summary>Regras</summary>
								- 1
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 2
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 3
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 4
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								<details>
								<summary>Regras 1 a 4</summary>
									- Relacionam o in de um statement com o out do mesmo statement
										- Propagam informação entre statements
									- Precisamos de regras relacionando o out de um statement com o in do statement seguinte para propagar informação entre nós do CFG
								</details>
								- 5
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 6
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 7
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								- 8
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
							<details>
							<summary>Algoritmo</summary>
								- Para todo nó inicial (statement) s do programa, defina Cin(x,s)=\*
								- Em todos os demais pontos do programa, defina Cin(x,s) = Cout(x,s) = #
									- O valor inicial # significa “até o momento, com o que sabemos, controle não alcança este ponto”
									- Permite que a análise alcance um ponto fixo
								- Repita o processo abaixo até que a aplicação das regras 1-8 não produza alteração
									- Dado um statement que não satisfaça 1-8, atualize usando a regra apropriada
								<details>
								<summary>Exemplo</summary>
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
								- O algoritmo termina pois o que está entre o \*, valores constantes e # é uma relação de ordem
									<details>
									<summary>Relação de ordem</summary>
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									</details>
							</details>
						</details>
				</details>
			</details>
		- Inter-procedural → aplicada entre fronteiras de métodos
	</details>
	- É feita em duas etapas: análise e transformação
		<details>
		<summary>Análise</summary>
			- Determina onde o compilador pode aplicar otimizações de forma segura e benéfica
			- Análise de fluxo de dados e aálise de dependências
		</details>
		<details>
		<summary>Transformação</summary>
			- O compilador usa os resultados da análise para reescrever o código de forma mais eficiente
			- Variam em efeito, escopo e análise necessária para habilitá-las
		</details>
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
	</details>
</details>
<details>
<summary>Síntese</summary>
	- Responsável por gerar o código alvo final, como binário ou bytecode
	<details>
	<summary>Ambiente de Execução</summary>
		- Um compilador deve implementar precisamente abstrações definidas na linguagem fonte como nomes, operadores, escopo, bindings, …
			- Isso é feito cooperando com o SO e outros softwares para dar suporte à estas abstrações
			- Para realizar esta implementação, o compilador cria um ambiente de execução no qual assume que os programas serão executados
		<details>
		<summary>Organização da memória</summary>
			- O programa tem seu próprio espaço lógico de memória, onde cada valor tem seu local
				- Memória
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
				- Gerenciamento e organização deste espaço é compartilhado entre o compilador, SO e máquina
				- O SO mapeia endereços lógicos em físicos, espalhados pela memória
					- A representação de um programa neste espaço lógico consiste de áreas de dados e programa
				- O tamanho do código gerado é fixo em tempo de compilação e pode-se colocar em uma área estática
					- O tamanho de alguns objetos de dados do programa (constantes e dados gerados pelo compilador) podem também ser alocados em áreas estáticas
					- Decisões de alocação estática são feitas apenas com base no texto do programa fonte, enquanto que decisões dinâmicas só podem ser tomadas durante a execução
			- Para maximizar o uso do espaço durante a execução, a heap e pilha mudam de tamanho dinamicamente
				- Pilha → nomes locais a um procedimento
					<details>
					<summary>Stack Allocation</summary>
						- Compiladores de linguagens que usam procedimentos, funções ou métodos como unidades de modularização gerenciam ao menos parte da memória runtime em uma pilha
						- Ao chamar um procedimento, espaço para as variáveis locais é alocado na pilha e ao término da execução, o espaço é liberado
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
						</details>
						<details>
						<summary>Ativação</summary>
							- Ativação de um procedimento = execução de um procedimento
								- Tempo de vida de uma ativação → sequência de passos do início ao fim do corpo de um procedimento p, incluindo a execução de procedimentos chamados por p
							- Se a e b são ativações de procedimentos, seus tempos de vida ou não se sobrepõem ou são aninhados
								- As alocações na pilha não seriam possíveis se as ativações não fossem aninhadas apropriadamente
							- Se a ativação de um procedimento p chama procedimento q, a ativação de q deve terminar antes que a ativação de p
								<details>
								<summary>Situações</summary>
									- Ativação de q termina normalmente
										- Controle volta para o ponto de p onde q foi<br>chamado
									- Ativação de q, ou de algum procedimento chamado por q, aborta, direta ou indiretamente
										- p encerra simultaneamente com q
									- Ativação de q termina por conta de uma exceção que q não consegue tratar
										- Procedimento p pode tratar a exceção, neste caso a ativação de q termina, enquanto a ativação de p continua, não necessariamente do ponto onde q foi chamada
										- Se p não consegue tratar a exceção, a ativação de p termina ao mesmo tempo que a de q, e presumidamente, a exceção será tratada por outro procedimento
								</details>
							<details>
							<summary>Árvores de Ativação</summary>
								- Podemos representar as ativações de procedimento feitas durante a execução de um programa com uma árvore
									- Cada nó corresponde a uma ativação
									- Os filhos de um nó p são ativações de procedimento feitas durante ativação de p
									- Ativações são ordenadas da esquerda pra direita, na ordem que foram chamadas
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
							</details>
							<details>
							<summary>Registros de Ativação</summary>
								- Cada ativação viva tem um registro (frame) na pilha de controle com a raiz da árvore de ativação no fundo
									- A sequência de registros de ativação corresponde ao caminho percorrido na árvore de ativação, onde o controle se encontra
									- Última ativação reside no topo da pilha
								<details>
								<summary>Elementos de registro</summary>
									- Valores temporários, resultantes de avaliação de expressões, etc.
									- Dados locais pertencentes ao procedimento ativo
									- Estado da máquina logo antes da chamada ao procedimento, endereço de retorno do contador de programas, por ex. conteúdo de registradores que será restaurado
									- Link de acesso para dados localizados em outros registros de ativação
									- Link de controle, registro de ativação de quem chamou procedimento
									- Valor de retorno, se houver, se possível usar registradores
									- Parâmetros reais, se possível, usar registradores
									> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
								</details>
							</details>
						</details>
					</details>
				- Heap → dados que podem existir após uma chamada de procedimento (dados que vivem indefinidamente)
					<details>
					<summary>Heap Allocation</summary>
						- Na medida que memória é utilizada e liberada, o espaço da heap é dividido entre partes livres e ocupadas de memória
							- As partes livres (holes) não residem em áreas contíguas da heap
							- A cada requisição deve-se encontrar um hole grande o suficiente para alocar os dados
								- A não ser que seja exatamente do tamanho solicitado, temos que dividir o hole ao alocar espaço, podendo gerar fragmentação (grandes quantidades de espaços livres pequenos e não contíguos)
						<details>
						<summary>Estratégias para reduzir a fragmentação</summary>
							- Controlar antes
								- Controlar a maneira de como os objetos são alocados na heap
								- first-fit vs. best-fit vs. next-fit
									- First-fit aloca o primeiro espaço livre e qye cabe
									- Best-fit divide espaços livres em bins, de tamanhos variáveis, melhorando space utilization
									- Next-fit tenta melhorar spatial locality, usando best-fit e alocando objetos próximos
							- Controlar depois
								- Ao desalocar objetos na heap, combinar (coalesce) o espaço livre com espaços livres adjacentes da heap
									- Marcar bins com um bit indicando se está ocupado ou livre
									- Se bins não forem utilizados, marcar as fronteiras dos espaços livres
						</details>
						<details>
						<summary>Manual Deallocation</summary>
							- Gerenciamento manual de memória tende a gerar erros
							- Memory leak → esquecer de deletar dados que não podem mais ser referenciados
							- Dangling reference → referenciar dados deletados
						</details>
						<details>
						<summary>Garbage Collection</summary>
							- Garbage → dados que não podem mais ser referenciados
								- Objetos se tornam garbage quando o programa não pode mais alcançar os objetos
								- É possível saber como um objeto é garbage a partir do tipo, na qual por meio disto é capaz de dizer o tamanho do objeto e quais componentes deste objeto tem referências a outros objetos 
									- Referências são sempre endereços para o início dos objetos
							- Reachability
								- Dados que podem ser acessados diretamente por um programa, sem precisar dereferenciar um ponteiro, formam o root set
									- Um programa pode alcançar qualquer membro deste conjunto a qualquer momento
									- Recursivamente, qualquer objeto cujas referências são armazenadas nos membros do root set é também alcançável
								- O conjunto de objetos alcançáveis muda durante a execução do programa, existindo operações que alteram este conjunto
									- Object allocation, reference assignments, …
								<details>
								<summary>Como encontrar objetos inalcançáveis</summary>
									- Incremental → a cada instrução realiza alguma tarefa
										<details>
										<summary>Reference Counting</summary>
											- Adicionar um contador para cada objeto alocado na heap
											- O contador rastreia o número de ponteiros para aquele objeto
											- Quando o contador alcança zero, o sistema pode liberar aquele objeto
											- Liberar um objeto pode levar a liberação de outros
											<details>
											<summary>Problemas</summary>
												> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
											</details>
										</details>
									- Batch-oriented → roda sob demanda, quando o espaço esgota
										<details>
										<summary>Batch Collectors</summary>
											- Geralmente são executados quando espaço livre está esgotado ou abaixo de um certo limiar
											- Collector pausa a execução do programa, examina memória alocada para descobrir objetos inutilizados e libera o espaço
											- Geralmente rodam em duas fases: descoberta de objetos mortos e desalocação e “reciclagem” de objetos mortos
											<details>
											<summary>Identificando objetos live (Mark-andSweep)</summary>
												- Em geral, usa-se o que é chamado de algoritmo de marking
													- O coletor usa um bit para cada objeto na heap, chamado de mark bit
													- Este bit é armazenado no cabeçalho do objeto, junto à informação para registro de localização e tamanho do objeto
													- Limpa todos os mark bits e constrói uma worklist
														- Todos os ponteiros em registradores e em variáveis acessíveis aos procedimentos
														- Caminha nesta worklist e segue quaisquer referências a partir destes ponteiros como alcançável
												- Ao término de algoritmo, objetos unmarked (objetos mortos) são inalcançáveis e podem ser liberados (sweep)
													- Realiza uma travessia nos objetos da heap liberando objetos inalcançáveis
													- Opcionalmente, já reseta o mark bit para a fase de marking evitar a travessia inicial
												<details>
												<summary>Definição do algoritmo</summary>
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
													> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
												</details>
											</details>
											- Todos os algoritmos em batch (trace-based) computam o conjunto de objetos alcançáveis e usam o seu complemento para liberar memória
											- A memória é reciclada de forma que o programa faz requisições de alocação, garbage collector descobre reachability e libera o espaço dos objetos inalcançáveis
											- Embora os algoritmos trace-based possam diferir em sua implementação, em geral são descritos de acordo com estados gerais
												- Free: espaço de memória pronto para ser alocado; não pode conter objeto alcançável
												- Unreached: espaço normalmente é denominado inalcançável, a não ser que o tracing prove o contrário
												- Unscanned: espaço alcançável, mas seus ponteiros ainda não foram escaneados
												- Scanned: todo objeto Unscanned eventualmente será observado e transiciona para este estado
											<details>
											<summary>Variações do mark-and-sweep</summary>
												- Baker’s mark-and-sweep: ao invés de examinar a heap inteira, mantém uma lista de objetos alocados
												- Mark-and-compact: move objetos na heap para eliminar fragmentação de memória, ao invés de apenas marcar como livre
												- Incremental: intercalam GC e programa, são conservadores, portanto
												- Copying collectors
													- Divide a heap em duas pools, old e new
													- Aloca memória sempre a partir  old
													- Stop and copy: quando a alocação falha, copia todos os dados live da old para new e inverte identidade, podendo usar mark-and-sweep ou incremental
											</details>
										</details>
									<details>
									<summary>Comparações</summary>
										- Com GC vs Sem GC
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										- Reference Counting vs Batch Collectors
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
										- Mark-and-sweep vs Copying Collectors
											> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
									</details>
								</details>
						</details>
					</details>
		</details>
	</details>
	<details>
	<summary>Seleção de instruções</summary>
		- Reescreve operações de IR em operações de linguagem de máquina, ainda abstraindo a quantidade de registradores simbólicos
			- Pode se beneficiar de operações especiais na máquina alvo
	</details>
	<details>
	<summary>Alocação de registradores</summary>
		- É mais eficiente realizar operações manipulando dados próximos a CPU, em registradores
		- O desafio desta etapa é conseguir associar as diversas variáveis do código em poucos registradores, com o objetivo de minimizar o spilling
			- Spilling: processo de mover variáveis da CPU para a memória RAM quando não há registradores suficientes disponíveis para armazenar todas as variáveis temporárias necessárias durante a execução de um trecho de código, afetando bastante o desempenho do código
	</details>
	<details>
	<summary>Geração do código de máquina final</summary>
		- Traduz a IR para instruções da arquitetura alvo, criando um programa executável que o processador ou VM consiga entender
		- Vários problemas complexos tendem a surgir nesta etapa e interagem entre si
			- Reordenar as instruções pode acabar aumentando o número de registradores necessários
			- Alocação de registradores pode criar falsa sensação de dependência entre valores, prejudicando a instruction scheduling
				- Instruction scheduling (escalonamento de instruções): otimização para aumentar o paralelismo em nível de instrução, reorganizando as instruções e melhorando o desempenho em máquinas com pipelines de instrução
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a4194580d794d2ccc03984b05c)*
		</details>
	</details>
</details>
