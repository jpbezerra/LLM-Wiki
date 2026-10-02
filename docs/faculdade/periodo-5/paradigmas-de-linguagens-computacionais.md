# PARADIGMAS DE LINGUAGENS COMPUTACIONAIS

- Monitoria: [drive.google.com](https://drive.google.com/drive/folders/1V8XFhhf1mPC0qanE1Hi8BMLjIPIbsj5L?usp=sharing)
---
<details>
<summary>Paradigmas</summary>
	- Paradigma significa um exemplo geral ou modelo que serve de base para compreender, observar e orientar a resolução de problemas
	- Um paradigma de programação fornece e determina a visão que o programador possui sobre a estruturação e a execução do programa
		- Programação orientada a objetos → programadores podem abstrair um programa como uma coleção de objetos que interagem entre si
		- Programação lógica → programadores abstraem o programa como um conjunto de predicados que estabelecem relações entre objetos (axiomas), e uma meta (teorema) a ser provada a ser usando os predicados
	- Algumas linguagens foram desenvolvidas para suportar um paradigma específico, mas existem linguagens multiparadigma (Lisp, Python, Perl, C++, etc.)
	- Os paradigmas são diferenciados pelas técnicas de programação que permitem ou proíbem
		- Exemplo: programação estruturada não permite o uso de goto
	<details>
	<summary>Programação imperativa</summary>
		- Descreve a computação como ações, enunciados ou comandos que mudam o estado de um programa, enfatizando como resolver um problema
		- Imperativo → o programador diz ao computador faça isso, depois isso e etc.
		- Paradigmas procedimental (C, Pascal) e orientado a objetos (Java, Smalltalk)
	</details>
	<details>
	<summary>Programação declarativa</summary>
		- Descreve o que o programa faz e não como os seus procedimentos funcionam
			- Ênfase nos resultados
		- Paradigmas funcional (Haskell, OCaml, Lisp) e lógico (Prolog)
			- Programação funcional é um paradigma de programação que descreve uma computação como uma expressão a ser avaliada
				- A principal forma de estruturar o programa é pela definição e aplicação de funções
				- Baseia-se na ideia de calcular
				- Não utiliza a definição de computador pelas Máquinas de Turing, mas sim a definição por meio de Cálculo Lambda
				- Todos os subprogramas são vistos como funções, recebendo argumentos e retornando soluções simples na qual a solução depende apenas da entrada e o tempo em que uma função é chamada é irrelevante (funções sem efeitos colaterais)
				<details>
				<summary>Vantagens e desvantagens</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
				</details>
		- Linguagens declarativas permitem que programas sejam escritos de forma clara, concisa e com um alto nível de abstração, permitem prototipagem rápida, fornecem poderosas ferramentas de resolução de problemas e suportam componentes de software reutilizáveis
			- Isso pode ser útil na abordagem de dificuldades encontradas no desenvolvimento de software (tamanho e compelxidade de computadores modernos, tempo e custo de desenvolvimento de programas e confiança de que os problemas concluídos funcionam corretamente)
	</details>
</details>
<details>
<summary>Haskell</summary>
	- Linguagem declarativa funcional, tipagem estática, tipos e funções recursivas, sistemas de tipos poderosos, programas concisos, avaliação lazy, maior facilidade de raciocínio sobre programas
	- Haskell é uma linguagem de programação pura avançada
		- É um produto de código aberto que permite o desenvolvimento rápido de software robusto, conciso e concreto
		- Possui bom suporte para integração com outras linguagens, concorrência e paralelismo integrados, depuradores, ricas bibliotecas, produz software flexível, de alta qualidade e de fácil manutenção
		- Programação baseada em definições
	- Códigos organizados em módulos (conjunto de definições como tipos, variáveis, funções e etc.)
		- Para que as definições de um módulo possam ser usadas o módulo deve ser importado, na qual uma coleção destes módulos relacionados formam uma biblioteca
	- Transparência referencial → uma expressão pode ser substituída pelo seu valor resultante sem alterar o comportamento do programa
		- Ou seja, pode-se provar propriedades matemáticas com funções pois a ordem dos fatores não altera o resultado, pois variáveis globais não mudam
		- Por isso Haskell permite raciocinar código como se fosse matemática pura
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			- A ordem dos fatores altera o resultado, pois altera a variável b
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			- Aqui independente da ordem dos fatores, o valor de b segue imutável, que nem na matemática pura
		</details>
	<details>
	<summary>Definição de funções</summary>
		- Os parâmetros das funções são separados apenas por espaço e o nome deve começar em minúsculo
		```haskell
-- | square :: Int -> Int
-- Define a função 'square' que recebe um valor do tipo Int (inteiro) e retorna um valor do tipo Int.
square :: Int -> Int

-- | square x = x * x
-- A função 'square' recebe um argumento chamado 'x'
-- e o seu resultado é a multiplicação de 'x' por ele mesmo (o quadrado).
square x = x * x
		```
		```haskell
-- | allEqual :: Int -> Int -> Int -> Bool
-- Define a função 'allEqual' que recebe três valores do tipo Int
-- e retorna um valor do tipo Bool (booleano), ou seja, 'True' ou 'False'.
allEqual :: Int -> Int -> Int -> Bool

-- | allEqual n m p = (n == m) && (m == p)
-- A função 'allEqual' compara os três argumentos (n, m, p).
-- (n == m): Verifica se 'n' é igual a 'm'.
-- (m == p): Verifica se 'm' é igual a 'p'.
-- &&: É o operador lógico "e". A expressão só será verdadeira (True)
-- se ambas as comparações (n == m E m == p) forem verdadeiras.
allEqual n m p = (n == m) && (m == p)
		```
		```haskell
-- | maxi :: Int -> Int -> Int
-- Define a função 'maxi' que recebe dois valores do tipo Int e retorna um Int.
maxi :: Int -> Int -> Int

-- | maxi n m | n >= m = n
-- Usa uma "guarda" para definir o comportamento.
-- Se a condição (n >= m) for verdadeira, a função retorna o valor de 'n'.
maxi n m | n >= m = n

-- |            | otherwise = m
-- O "otherwise" atua como um "senão".
-- Se a condição acima for falsa (ou seja, se 'm' for maior que 'n'),
-- a função retorna o valor de 'm'.
				 | otherwise = m
		```
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		<details>
		<summary>Recursão</summary>
			- Precisa definir caso base e definir o valor usando a própria função
			```haskell
vendas :: Int -> Int
vendas _ = 10 -- toda semana vende 10

totalVendas :: Int -> Int
totalVendas n
	| n == 0    = vendas 0
	| otherwise = totalVendas (n-1) + vendas n
			```
			```haskell
maxVendas :: Int -> Int
maxVendas n
	| n == 0    = vendas 0
	| otherwise = maxi (maxVendas (n-1)) (vendas n)
			```
		</details>
		<details>
		<summary>Casamento de padrões</summary>
			- Permite usar padrões no lugar de variáveis, na definição de funções
				- São realmente os casos de uma função matemática, por exemplo
			```haskell
maxVendas :: Int -> Int
maxVendas 0 = vendas 0
maxVendas n = maxi(maxVendas(n-1)) (vendas n)

totalVendas :: Int -> Int
totalVendas 0 = vendas 0
totalVendas n = totalVendas (n-1) + vendas n
			```
			```haskell
myNot :: Bool -> Bool
myNot True = False
myNot False = True

myOr:: Bool -> Bool
myOr True  x = True
myOr False x = x

myAnd :: Bool -> Bool
myAnd False x = False
myAnd True  x = x
			```
			- Regras para padrões
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
				- Os casos devem ser exaustivo, mas não é obrigatório → funções parciais
		</details>
	</details>
	<details>
	<summary>Notação</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Duas formas de usar funções binárias
		<details>
		<summary>Erros comuns</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
	</details>
	<details>
	<summary>Definições locais</summary>
		- where aparece no final de uma equação/guard, definindo nomes visíveis apenas naquela equação
		- O let aparece antes da expressão que usa as variáveis, podendo usar em qualquer lugar apenas não em definições de funções
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>Tipos básicos</summary>
		- Integer → precisão arbitrária
		- Int → precisão fixa (bounded
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Bool
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Char
		- String
		- Float → 8 números decimais
		- Double → 16 números decimais
	</details>
	<details>
	<summary>Listas</summary>
		- Coleções de objetos de um mesmo tipo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Construtor de listas
			- (:) :: a (head with type ‘a’) → \[a\] (tail with type ‘a’) → \[a\] (list with type ‘a’)
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Declaração de listas com range
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Funções sobre listas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		- Compreensões de listas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>case</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>Tuplas</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>Tipos</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>Polimorfismo</summary>
		- Função que possui um tipo genérico, usando variáveis de tipos
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			- Usado quando os tipos dos elementos não importam
		- Overloading
			- Mesmo nome de função mas definições distintos para cada tipo → polimorfismo de sobrecarga
			- Classe → coleção de tipos para os quais uma função está definida
			- O conjunto de tipos para os quais == está definida é a classe igualdade, Eq (tipo de typeclass), existe Ord, Show, Num, Read, entre outros
				- Para realizar o polimorfismo, basta utilizar as classes
					```haskell
exemplo :: Eq t -> t -> Bool
					```
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
				</details>
			- Instâncias → membros de uma classe
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
	</details>
	<details>
	<summary>Funções de Alta Ordem</summary>
		- Função que recebe uma função como argumento e/ou retorna uma função como resultado
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			</details>
			- O argumento em função é o que aparece entre parênteses, na qual esta função é normalmente uma função de transformação (pega um valor e retorna outro valo transformado)
		- Facilitam o entendimento da funções, facilitando modificações (mudança na função de transformação)
			- Aumentam o reuso de código
			- Utiliza o Currying → técnica que transforma uma função de múltiplos argumentos numa sequência de funções, cada uma com um única argumento
		<details>
		<summary>map</summary>
			- Aplica uma função a cada elemento da lista
			```haskell
map :: (a -> b) -> [a] -> [b]

-- Exemplo

map (*2) [1,2,3,4]
-- [2,4,6,8]
			```
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>fold</summary>
			- Reduz uma lista a um único valor, aplicando uma função binária recursivamente
			- Pode ser tanto foldr (acumula da esquerda para a direita) ou foldl (acumula da direita para a esquerda)
			```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b
foldl :: (b -> a -> b) -> b -> [a] -> b

-- Exemplo

foldr (+) 0 [1,2,3,4]
-- 10

foldl (+) 0 [1,2,3,4]
-- 10
			```
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>filter</summary>
			- Mantém apenas os elementos que satisfazem um predicado (função que retorna um bool)
			```haskell
filter :: (a -> Bool) -> [a] -> [a]

-- Exemplo
filter even [1,2,3,4,5,6]
-- [2,4,6]
			```
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>all</summary>
			- Recebe um predicado e uma lista, retornando True se a função vale para todos os elementos
			```haskell
all :: (a -> Bool) -> [a] -> Bool
			```
		</details>
		<details>
		<summary>curry</summary>
			- Transforma uma função que recebe um par em uma função que recebe dois argumentos separados
			```haskell
curry :: ((a, b) -> c) -> a -> b -> c

f :: (Int, Int) -> Int
f (x,y) = x + y

g :: Int -> Int -> Int
g = curry f

-- Agora:
f (3,4)   -- 7
g 3 4     -- 7
			```
		</details>
		<details>
		<summary>uncurry</summary>
			- Transforma uma função que recebe dois argumentos separados em uma função que recebe um par
			```haskell
uncurry :: (a -> b -> c) -> (a, b) -> c

h :: Int -> Int -> Int
h x y = x * y

k :: (Int, Int) -> Int
k = uncurry h

-- Agora:
h 3 4       -- 12
k (3,4)     -- 12

			```
		</details>
	</details>
	<details>
	<summary>Função de Composição</summary>
		- (.) é o operador de composição de funções em Haskell
			- (f . g) significa “aplica g primeiro, depois aplica f”
			```haskell
(.) :: (u -> v) -> (t -> u) -> (t -> v)

-- Exemplo
negate . abs $ (-5)
-- Primeiro abs (-5) = 5
-- Depois negate 5 = -5
			```
		- Estruturar programas compondo funções
			```haskell
fill :: String -> [Line]
fill s = splitLines (splitWords s)

-- pode ser reescrito como:
fill = splitLines . splitWords

--
twice :: (t -> t) -> (t -> t)
twice f = f . f

--
iter :: Int -> (t -> t) -> (t -> t)
iter 0 f = id
iter n f = (iter (n-1) f) . f
			```
		- Notação Lambda
			- É uma forma de definir funções anônimas
			```haskell
addNum :: Int -> (Int -> Int)
addNum n = \m -> n + m
			```
			</details>
	<details>
	<summary>Aplicações parciais</summary>
		- Em Haskell toda função é curried (recebe um argumento e retorna outra função se ainda faltam argumentos)
			- Por causa disso, isto permite a aplicação parcial, ou seja, passar só parte dos argumentos
		- Exemplo
			```haskell
multiply :: Int -> Int -> Int
multiply a b = a * b

-- O tipo real é:
multiply :: Int -> (Int -> Int)

-- Aplicações
multiply 2      -- função que multiplica por 2
(multiply 2) 5  -- 10

-- multiply 2 é uma função que multiplica por 2
-- , passada para o map
doubleList :: [Int] -> [Int]
doubleList = map (multiply 2)

doubleList [1,2,3]   -- [2,4,6]

			```
	</details>
	<details>
	<summary>Associatividade</summary>
		- Aplicação de função é à esquerda
			```haskell
-- Definição simples
add :: Int -> Int -> Int
add x y = x + y

main = do
    print (add 2 3)   -- 5
    print ((add 2) 3) -- 5 (mesma coisa, aplicação é à esquerda)

			```
		- Símbolo de função ‘→’ é associativo à direita
			- Funções que sempre retornam funções até consumir todos os parâmetros
			```haskell
-- Observe os tipos:
-- Int -> Int -> Int
-- é o mesmo que Int -> (Int -> Int)

mul :: Int -> Int -> Int
mul x y = x * y

main = do
    let f = mul 4   -- f :: Int -> Int
    print (f 5)     -- 20
			```
		- A associatividade explica as curried functions → uma função de 2 argumentos é na verdade uma função que recebe 1 argumento e retorna outra função
		- Exemplo
			```haskell
g :: (Int -> Int) -> Int
g h = h 0 + h 1

-- h é uma função de Int -> Int
-- As funções são passadas como argumentos,
-- não só valores
			```
	</details>
	<details>
	<summary>Tipos Algébricos</summary>
		- Semelhante à enums
			```haskell
data Estacao = Inverno   | Verao
							 Primavera | Outono
							 
data Temp = Frio | Quente

clima :: Estacao -> Temp
clima Inverno = Frio
clima _ = Quente
			```
		<details>
		<summary>Tuplas vs Tipos Algébricos</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>Construtores com argumentos</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>Forma geral</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>Tipos Polimórficos</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
	</details>
	<details>
	<summary>Laziness</summary>
		- Estratégia de avaliação a qual uma expressão só é calculada no momento exato em que seu resultado é necessário (call-by-need)
			- Ao atribuir uma expressão a uma variável, Haskell não a executa imediatamente, cria uma “promessa” de cálculo (chamada de thunk)
			- O thunk contém a expressão e tudo o que é necessário para calculá-la
				- A expressão é avaliada apenas quando outra parte do porgrama realmente preciso do valor da variável, na qual o thunk é forçado, a expressão avaliada, o resultado é armazenado para uso futuro e o thunk é substituído
				- Se o valor for necessário novamente, o resultado já calculado é utilizado, evitando recálculos desnecessários
		<details>
		<summary>Vantagens</summary>
			- Com Laziness, é possível definir e manipular listas e outras estruturas de dados que são teoricamente infinitas
				```haskell
-- Uma lista infinita de todos os números inteiros a partir de n
infinitosAPartirDe n = n : infinitosAPartirDe (n + 1)

-- Pega os 5 primeiros elementos da lista infinita a partir de 1
primeirosCinco = take 5 (infinitosAPartirDe 1)
-- Resultado: [1,2,3,4,5]
-- O restante da lista infinita nunca é calculado.
				```
			- Permite que os programadores separem a lógica de geração de dados da lógica de consumo
			- Evita cálculos desnecessário, se um valor nunca for usado ele nunca será calculado, levando a ganhos significativos de eficiência
		</details>
		<details>
		<summary>Desafios</summary>
			- Space Leaks → se um programa acumular um grande número de thunks sem avaliá-los, pode consumir uma quantidade significativa de memória
			- Previsibilidade de performance → o desempenho pode se tornar menos previsível, já que o momento exato em que um cálculo ocorre pode ser difícil de determinar apenas lendo o código
			- Para mitigar esses desafios, o Haskell oferece diversos mecanismos para cntrolar a avaliação e forçar o cálculo de expressões quando necessário
				- seq → força a avaliação de uma expressão até certo ponto antes de prosseguir
					```haskell
-- Versão preguiçosa que pode acumular thunks
somaPreguicosa :: [Int] -> Int
somaPreguicosa xs = foldl (\acc x -> acc + x) 0 xs

-- Forçando a avaliação do acumulador com seq
somaComSeq :: [Int] -> Int
somaComSeq xs = foldl f 0 xs
  where
    f acc x = let novoAcc = acc + x
              in novoAcc `seq` novoAcc
					```
				- \$! → aplica uma função a um argumento, garantindo que o argumento seja avaliado antes da função ser chamada
					```haskell
-- Versão preguiçosa que pode acumular thunks
somaPreguicosa :: [Int] -> Int
somaPreguicosa xs = foldl (\acc x -> acc + x) 0 xs

-- Usando aplicação estrita para forçar a avaliação
somaComOpEstrito :: [Int] -> Int
somaComOpEstrito xs = foldl f 0 xs
  where
    f acc x = (acc +) $! x
					```
					- A expressão (acc +) \$! parece aplicar a função (acc +) ao argumento x, no entanto, \$! não força o argumento x (que já é o valor), mas sim o resultado da função
					- Uma forma mais clara de usar \$! nesse contexto é forçar o acumulador na própria recursão
						```haskell
import Data.List (foldl') -- A forma correta de fazer isso é usar a função pronta

-- Implementando uma versão estrita de foldl nós mesmos com $!
meuFoldlEstrito :: (b -> a -> b) -> b -> [a] -> b
meuFoldlEstrito _ z [] = z
meuFoldlEstrito f z (x:xs) =
    let z' = f z x
    in meuFoldlEstrito f $! z' $ xs -- Força a avaliação de z' antes da chamada recursiva

somaComMeuFoldlEstrito :: [Int] -> Int
somaComMeuFoldlEstrito = meuFoldlEstrito (\acc x -> acc + x) 0
						```
				- Anotações de estrita → permitem que os desenvolvedores marquem campos em tipos de dados como estritos, garantindo que seus valores sejam calculados assim que a estrutura de dados for criada
		</details>
	</details>
	<details>
	<summary>Mônadas</summary>
		- Em Haskell, Monad é uma ferramenta poderosa para gerenciar contextos como o de falha, permitindo que o programador encadeie operações de forma limpa e segura, abstraindo a lógica repetitiva de tratamento de contexto
			- O principal objetivo é facilitar a composição de funções onde o resultado de uma é a entrada da próxima, especialmente quando essas funções podem falhar ou ter efeitos colaterais
			- Mônadas abstraem o padrão de verificar e continuar, para que o programador não precise fazer isso manualmente
		- Componentes
			- Construtor de Tipo → um tipo que encapsula o valor em um contexto
			- Função de Ligação (\>\>=, bind) → operador principal para encadear operações monádicas, extraindo o valor do contexto (caso exista) e o passando para a próxima função
			- Função Unidade → uma função que pega um valor puro e coloca no contexto monádico mínimo
		<details>
		<summary>Maybe</summary>
			- Mônada para lidar com computações que podem falhar ou não retornar um valor
			- Construtor de tipo
				- data Maybe t = Just t \| Nothing
			- Função Unidade: return x = Just x
				- Simplesmente envolve o valor com o construtor Just
			- Função de Ligação
				- Caso de sucesso (Just): se o valor da esquerda do operador for um Just x, a função f à direita é aplicada ao valor x que estava dentro do Just, logo, (\>\>=) Just x f = f x
				- Caso de falha (Nothing): se o valor à esquerda for Nothing, a função f é completamente ignorada e o resultado da operação é simplesmente Nothing, logo, (\>\>=) Nothing _ = Nothing
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/268237a4194580d994e1d2e62ea9aa3e)*
		</details>
		<details>
		<summary>Notação do</summary>
			- Torna o código monádico ainda mais legível, parecendo uma sequência de instruções imperativas
				```haskell
safeTail Nothing = Nothing
safeTail (Just l)
	| l /= [] = Just (tail l)
	| otherwise = Nothing

do
  x <- return 33
  y <- safeDiv 10000 x
  z <- return $ show y
  safeTail z
				```
		</details>
	</details>
</details>
<details>
<summary>Java</summary>
	- Características Gerais
		- Tipagem Estática: Java exige a declaração explícita dos tipos das variáveis, diferentemente de linguagens dinâmicas como Python
		- Compilação e Execução: Todo programa Java deve ter pelo menos uma classe
			- O método main é estático e serve como ponto de partida para a execução da aplicação
		- Gerenciamento de Memória: A linguagem possui um Garbage Collector (Coletor de Lixo) que gerencia a memória automaticamente, liberando o espaço de objetos não utilizados
	- Tipos
		- Tipos Primitivos: Armazenam valores diretamente e possuem tamanho fixo
			- Exemplos: int, double, boolean, char
		- Tipos de Referência: Armazenam referências (endereços de memória) para objetos
			- Exemplos: String, Arrays e classes criadas pelo usuário (como Conta, Livro)
			- O valor padrão para referências não inicializadas é null, indicando a ausência de objeto
	- Pacotes (Packages)
		- Java utiliza pacotes (ex: java.util, java.lang) para organizar classes e evitar conflitos de nomes
		- O comando import é usado para trazer classes de outros pacotes
	<details>
	<summary>POO</summary>
		- A POO foca nos dados (objetos) e não apenas nas funções, estruturando o programa de forma mais próxima às atividades do mundo real
		- Classe vs Objeto
			- Objeto: É uma instância concreta da classe criada em memória
				- Um objeto possui identidade única, estado (valores atuais dos atributos) e comportamento
				<details>
				<summary>Criação e inicialização</summary>
					- Operador new
						- Um objeto é criado (instanciado) usando o operador new, que aloca memória para o objeto e retorna uma referência para ele
					- Construtores
						- São métodos especiais responsáveis por inicializar os atributos do objeto no momento da criação
						- Sintaxe: Possuem o mesmo nome da classe e não têm tipo de retorno (nem mesmo void)
						- Construtor Default
							- Se nenhum construtor for definido, o Java fornece um construtor implícito sem parâmetros que inicializa atributos com valores padrão (0 para números, false para boolean, null para referências)
						- Construtores Personalizados
							- É possível definir construtores que recebem parâmetros para obrigar a inicialização de dados essenciais (ex: obrigar o número da conta ao criá-la)
							- Ao definir um construtor explícito, o padrão implícito deixa de existir
					- Palavra-chave this
						- Representa uma referência para o próprio objeto em execução
						- É usada frequentemente nos construtores e métodos "Set" para distinguir entre os atributos da classe e os parâmetros do método quando eles têm o mesmo nome
					- Sobrecarga (Overloading)
						- É a capacidade de ter múltiplos construtores ou métodos com o mesmo nome, mas com listas de argumentos diferentes (assinaturas diferentes)
						- Exemplo: Um construtor que recebe apenas o número da conta e outro que recebe número e saldo inicial
						- Um construtor pode chamar outro da mesma classe usando this(parametros)
				</details>
			- Classe: É o modelo, a "forma" ou o conceito
				- Descreve as propriedades (atributos) e comportamentos (métodos) que os objetos terão
				- É uma estrutura estática de definição
				- Classes começam com Maiúscula (CamelCase), métodos e atributos com minúscula
				<details>
				<summary>Estrutura de uma classe</summary>
					- O corpo de uma classe pode conter atributos, métodos e construtores
					- Atributos (Estado)
						- Variáveis que caracterizam as propriedades do objeto
						- Exemplo: Uma classe Conta possui numero (String) e saldo (double)
					- Métodos (Comportamento)
						- Operações que realizam ações e podem modificar os atributos do objeto
						- Exemplo: creditar (double valor) altera o saldo da conta
						- Métodos podem retornar valores (usando return) ou serem void (sem retorno)
						- Métodos devem ser o menos dependente possível uns dos outros (baixo acoplamento)
						- Um método deve ter um propósito único e bem definido (alta coesão)
				</details>
				<details>
				<summary>Membros Estáticos (static)</summary>
					- Variáveis e métodos podem ser declarados como static
						- Isso significa que eles pertencem à classe e não a uma instância específica
					- Variáveis Estáticas
						- Todos os objetos compartilham a mesma variável
						- Se um objeto a altera, muda para todos
						- Útil para contadores globais ou constantes
					- Métodos Estáticos
						- São chamados através do nome da classe (ex: Conta.getProximo()) e só podem acessar outras variáveis ou métodos estáticos
						- Eles não podem acessar atributos de instância (this não existe num contexto estático)
				</details>
				<details>
				<summary>Encapsulamento (Information Hiding)</summary>
					- Recomenda-se fortemente o uso do modificador private nos atributos para que eles só sejam acessados ou modificados pelos métodos da própria classe
					- Isso protege a integridade dos dados e facilita a manutenção e extensibilidade do código
						- O acesso externo é feito através de métodos públicos (Getters e Setters)
				</details>
				<details>
				<summary>Classe String</summary>
					- Em Java, Strings são objetos (tipo referência), não tipos primitivos
					- Imutabilidade → Uma vez criado, o objeto String não é alterado; operações de concatenação geram novos objetos
					- Comparação
						- ==: compara se as variáveis referenciam o mesmo objeto na memória
						- .equals(): compara o conteúdo do texto (o valor semântico)
					- Métodos Úteis:
						- length(): Retorna o tamanho da string
						- substring(inicio, fim): Extrai uma parte da string
						- +: Operador de concatenação
				</details>
			- Exemplo: "Conta Bancária" é a classe; a conta específica "123-X com saldo 354,78" é o objeto
		<details>
		<summary>Herança</summary>
			- Mecanismo fundamental para estender funcionalidades de classes existentes e promover o reuso de código, permitindo criar uma hierarquia onde uma subclasse herda atributos e métodos de uma superclasse
				- Em Java, utiliza-se extends para realizar a herança
				- Java suporta somente herança simples, logo, só uma classe pode herdar diretamente de uma única superclasse direta
			- Construtores na herança
				- Os construtores da superclasse não são herdados
				- A subclasse deve definir seus próprios construtores e deve invocar o construtor da superclasse para garantir a inicialização correta dos atributos herdados
					- Essa inicialização da superclasse é feito por meio da keyword super()
					- Se o construtor da superclasse não tiver parâmetros, o Java faz a chamada implícita, se tiver parâmetros, a chamada deve ser explícita no código da subclasse
			- Acesso e viabilidade
				- Embora a subclasse herde atributos privados (private), ela não pode acessá-los diretamente
					- O acesso deve ser feito através de métodos públicos ou protegidos (como getters/setters ou métodos de negócio)
			<details>
			<summary>Override</summary>
				- Muitas vezes, o comportamento herdado não é adequado para a subclasse, por isso, o Override permite alterar esse comportamento
				- Regras de Redefinição:
					- Invariância de Assinatura: O nome do método, a lista de argumentos e o tipo de retorno devem ser idênticos aos da superclasse
					- Semântica e Visibilidade: A visibilidade não pode ser mais restritiva e a semântica (o que o método faz conceitualmente) deve ser preservada
				- Uso do super: Dentro de um método redefinido, é possível chamar a implementação original da superclasse usando super.nomeDoMetodo().
					- Exemplo
						```java
// Classe Pai
class Animal {
    public void fazerSom() {
        System.out.println("Som genérico de animal");
    }
}

// Classe Filha
class Cachorro extends Animal {
    @Override // Indica que o método está sendo sobrescrito
    public void fazerSom() {
        System.out.println("Latido!");
    }
}

						```
			</details>
			- Princípio da Substituição
				- Um objeto da subclasse deve se comportar como o objeto da superclasse)
		</details>
		<details>
		<summary>Polimorfismo</summary>
			- Capacidade do objeto assumir várias formas ou de responder a uma mesma mensagem de diferentes maneiras
			- Objetos de uma subclasse podem ser usados em qualquer lugar onde um objeto da superclasse é esperado
				- Isso permite tratar objetos de tipos diferentes de forma uniforme
				- Exemplo: Um método que aceita Conta (superclasse) como parâmetro funcionará perfeitamente se receber uma Poupanca ou ContaEspecial
			<details>
			<summary>Dynamic Binding</summary>
				- Mecanismo que faz o polimorfismo funcionar em tempo de execução
				- Quando um método é chamado em uma variável do tipo Conta, o Java decide qual código executar (o da Conta ou da Poupanca) baseando-se no tipo real do objeto na memória, e não no tipo da variável
				- Métodos e atributos marcados com final não podem ser sobrescritos (impede o Override) e possuem ligação estática, na qual o Java decide qual código executar baseado em tempo de compilação
					```java
public class FinalVariableExample {
    public static void main(String[] args) {
        final int MAX_VALUE = 100;
        System.out.println("MAX_VALUE: " + MAX_VALUE);

        // MAX_VALUE = 200; // Isso causaria um erro de compilação.
    }
}

// Neste exemplo, MAX_VALUE é uma variável final. 
// Uma vez inicializada, seu valor não pode ser alterado; 
// qualquer tentativa de reatribuí-lo 
// resultará em um erro de compilação. 
					```
			</details>
		</details>
		<details>
		<summary>Verificação de Tipos e Casting</summary>
			- Às vezes é necessário recuperar o tipo específico de um objeto que está em uma variável genérica
			- Casting (Conversão Explícita)
				- Para usar métodos exclusivos de uma subclasse (ex: renderJuros da Poupanca) quando se tem uma referência de Conta, é necessário fazer um cast: ((Poupanca) conta).renderJuros(...) 
				- Fazer um cast para o tipo errado gera um erro em tempo de execução (ClassCastException)
					- Para evitar erros, usa-se o instanceof para verificar se o objeto é realmente daquele tipo antes de fazer o cast
				- Exemplo
					```java
class Animal {
    void comer() {
        System.out.println("O animal está comendo.");
    }
}

class Cachorro extends Animal {
    void latir() {
        System.out.println("Au au!");
    }
}

// Código principal
Animal meuAnimal = new Cachorro(); // Upcasting (implícito, automático)
// meuAnimal.latir(); // Isto não compila, pois o compilador não reconhece o método latir() na classe Animal

Cachorro meuCachorro = (Cachorro) meuAnimal; // Downcasting (explícito, manual)
meuCachorro.latir(); // Agora podemos chamar o método latir()
// Saída: Au au!

					```
		</details>
		<details>
		<summary>Referências e Passagem de Parâmetros</summary>
			- Em Java, uma variável de classe não guarda o objeto, mas sim uma referência (endereço) para ele
			- Aliasing
				- Duas variáveis podem apontar para o mesmo objeto
				- Alterações feitas através de uma variável (ex: b.creditar) afetam a visão da outra variável (a), pois o objeto subjacente é o mesmo
			- Em Java, a passagem de parâmetros é sempre por valor
				- Para tipos primitivos, copia-se o valor (ex: 10, true)
				- Para objetos, copia-se o valor da referência
					- O método recebe uma cópia do endereço, se o método alterar o estado do objeto (ex: mudar o saldo), a alteração persiste fora
					- Mas se o método apontar a variável local para um new Conta(), a variável original fora do método não é alterada 
		</details>
		<details>
		<summary>Classe Abstrata</summary>
			- Uma classe abstrata é um tipo de classe que não pode ser instanciada diretamente (new ContaAbstrata() não é permitido), ela serve como um modelo incompleto para herdar código e definir uma interface comum
			- Para declarar, utiliza-se a keyword abstract
			- Pode conter atributos e métodos concretos que são comuns a todas as subclasses
			- Contém métodos declarados com a keyword abstract que não possuem implementação, servem somente de assinatura (base comum)
				- Um método abstrato permite que se programe chamando o método da classe abstrata
				- Força todas as subclasses concretas a fornecerem uma implementação desse método, ou seja, além de herdar código herdam a obrigação da implementação
				```java
abstract class Animal {
    // Método abstrato (sem implementação)
    abstract void fazerBarulho();

    // Método concreto (com implementação)
    void dormir() {
        System.out.println("Zzzzz...");
    }
}

class Cachorro extends Animal {
    // Implementação obrigatória do método abstrato
    @Override
    void fazerBarulho() {
        System.out.println("Au au!");
    }
}

public class Main {
    public static void main(String[] args) {
        Cachorro meuCachorro = new Cachorro();
        meuCachorro.fazerBarulho(); // Executa a implementação da classe Cachorro
        meuCachorro.dormir(); // Executa a implementação da classe Animal
    }
}
				```
		</details>
		<details>
		<summary>Interfaces</summary>
			- Uma interface define um contrato ou um padrão de serviços
				- Ela lista os métodos disponíveis e suas assinaturas, sem se preocupar com a implementação
			- O foco é no o quê a classe pode fazer, e não como ela faz
				- Para isso, utiliza-se a keyword interface na superclasse e na subclasse utiliza a keyword implements
				- Por padrão, todos os métodos são públicos ou abstratos
			- A principal vantagem é que uma classe pode implementar múltiplas interfaces de uma só vez (ex: class Aviao implements Voador, TransportadorDePessoas)
				- Isso supera a limitação de herança simples de classes em Java
			- Além disso, há um polimorfismo de interface, na qual um objeto de uma superclasse pode referenciar qualquer objeto de uma subclasse, onde o método correto é determinado dinamicamente
				```java
// Arquivo: Pagavel.java
public interface Pagavel {
    // Todo meio de pagamento precisa conseguir processar um valor
    void processarPagamento(double valor);
    
    // Todo meio de pagamento precisa emitir um comprovante
    String getComprovante();
}

// Arquivo: Pix.java
public class Pix implements Pagavel {
    @Override
    public void processarPagamento(double valor) {
        System.out.println("Gerando QR Code para valor de R$ " + valor);
        System.out.println("Conectando ao Banco Central... Pagamento Instantâneo realizado!");
    }

    @Override
    public String getComprovante() {
        return "COMPROVANTE-PIX-12345";
    }
}

// Arquivo: CartaoCredito.java
public class CartaoCredito implements Pagavel {
    @Override
    public void processarPagamento(double valor) {
        System.out.println("Validando limite do cartão...");
        System.out.println("Cobrando taxa da operadora...");
        System.out.println("Pagamento de R$ " + valor + " aprovado no crédito.");
    }

    @Override
    public String getComprovante() {
        return "COMPROVANTE-VISA-99887";
    }
}

// Arquivo: SistemaLoja.java
public class SistemaLoja {
    public static void main(String[] args) {
        // Podemos criar uma lista de pagamentos variados
        // Note que o tipo da variável é a INTERFACE 'Pagavel'
        Pagavel compra1 = new Pix();
        Pagavel compra2 = new CartaoCredito();

        // Vamos processar tudo num loop
        Pagavel[] compras = {compra1, compra2};

        System.out.println("--- Iniciando Fechamento de Caixa ---");
        
        for (Pagavel p : compras) {
            // AQUI É O POLIMORFISMO:
            // O Java decide qual 'processarPagamento' chamar baseando-se no objeto real
            p.processarPagamento(100.00);
            System.out.println("Recibo: " + p.getComprovante());
            System.out.println("--------------------------------");
        }
    }
}
				```
		</details>
		<details>
		<summary>Classe Abstrata vs Interfaces</summary>
			- Implementação
				- Classe abstrata → implementações compartilhadas nas subclasses
				- Interface → implementações diferentes nas subclasses
			- Estrutura
				- Classe abstrata → pode ter atributos, construtores e métodos concretos
				- Interface → não define atributos (apenas constantes finais) nem construtores
			- Herança
				- Classe abstrata → herança simples de código (só pode ter uma superclasse)
				- Interface → herança múltipla de assinaturas (mais de uma superclasse)
			- Uso ideal
				- Classe abstrata → Agrupar classes intimamente relacionadas que compartilham estado e comportamento base
				- Interface → Definir um comportamento ou capacidade (o que o objeto faz), independentemente de sua classe
		</details>
	</details>
	<details>
	<summary>Exceções</summary>
		- Em Java, Exceções são objetos derivados da superclasse Exception
			- O objetivo disso é desenvolver sistemas robustos, separando o código de tratamento de erro do código da lógica normal
		- Sintaxe
			- Levantar o erro
				- Usar a palavra-chave throw seguida do objeto da exceção.
				- Ex: throw new SIException(saldo, numero);.
				- Isso interrompe o fluxo normal e passa o controle para quem chamou o método.
			- Declarar o erro
				- Na assinatura do método, usar throws.
				- Ex: public void debitar(...) throws SIException
	</details>
	<details>
	<summary>Programação Concorrente</summary>
		- Quando dois ou mais comandos/tarefas progridem “ao mesmo tempo”, útil para permitir múltiplos usuários simultâneos e aumentar a eficiência do sistema
			- Ocorre via paralelismo ou divisão de tempo
		- Um dos maiores desafios da concorrência é que comandos que parecem simples em linguagens de alto nível (como Java) não são atômicos
			- Uma simples instrução é composta por mais de uma etapa, que envolve leitura na memória, lógica do comando e escrita na memória
		- Race Condition
			- Em um ambiente concorrente, se duas threads tentarem atualizar a mesma variável ao mesmo tempo sem controle, elas podem "atrapalhar" uma à outra
				- Isso ocorre porque a execução pode ser interrompida no meio das etapas acima
				- Exemplo: Duas threads leem o valor 1, ambas somam 1, ambas escrevem 2, o resultado deveria ser 3, mas dados foram perdidos
			- Não Determinismo
				- Devido a essa interferência arbitrária, a execução de um programa concorrente pode gerar resultados diferentes a cada execução, tornando o debug difícil
		<details>
		<summary>Threads</summary>
			- Java não possui um operador nativo de concorrência, mas utiliza o conceito de Threads (fios de execução)
			- Criação de Threads
				- Existem duas formas principais
				- Estender a classe Thread, criando uma subclasse de java.lang.Thread e redefinindo o método run()
				- Implementando a interface Runnable, sendo mais flexível quando a classe já herda de outra classe (pois Java não suporta herança múltipla de classes)
			- Ciclo de vida básico
				- start(): Inicia a execução da thread (chama o run internamente em um novo contexto de execução)
				- join(): Faz com que a thread atual espere até que a thread chamada termine sua execução
			- Sincronização e Exclusão Mútua
				- Para evitar interferências e condições de corrida, é necessário controlar o acesso a recursos compartilhados (como atributos de um objeto)
					- Isso é feito através da Exclusão Mútua, por meio de monitores
				<details>
				<summary>Monitores</summary>
					- Em Java, todo objeto possui um monitor associado que funciona como uma trava (lock)
					- Mecanismos de sincronização que garantem que apenas uma thread por vez acesse uma determinada seção de código ou objeto compartilhado
					- Eles funcionam encapsulando estruturas de dados compartilhadas e as operações que as manipulam, com a característica principal de **exclusão mútua** (apenas um thread por vez) e, opcionalmente, cooperação entre threads através de espera e notificação, usando métodos como wait() e notify()
					- Em Java, qualquer objeto pode ser um monitor, para isso basta usar a keyword synchronized
						- Métodos sincronizados
							- Ao declarar um método como synchronized, a thread deve adquirir o monitor do objeto (this) antes de executá-lo
							- Nenhuma outra thread pode executar qualquer método sincronizado desse mesmo objeto simultaneamente
						- Blocos sincronizados
							- Permitem travar apenas um trecho crítico do código ou usar um objeto específico como trava (synchronized(objeto) \{ ... \})
							- Isso reduz o custo de performance e aumenta a granularidade da concorrência
						- Região crítica
							- É o trecho de código onde ocorrem acessos a recursos compartilhados que podem gerar inconsistência
							- O uso de synchronized torna essa região atômica
				</details>
			- Coordenação entre Threads (wait e notify)
				- Além da exclusão mútua, às vezes as threads precisam cooperar ou esperar por uma condição específica (ex: não debitar se o saldo for insuficiente)
				- wait()
					- Deve ser chamado dentro de um bloco sincronizado
					- A thread libera o monitor (lock) e entra em estado de espera até ser notificada, isso é usado quando uma pré-condição não é atendida
					- O wait() deve ser usado dentro de um loop while (e não if) para garantir que a condição seja retestada quando a thread acordar
				- notify() / notifyAll()
					- Acorda threads que estão esperando no monitor do objeto
					- notifyAll acorda todas (mais seguro para garantir que a thread correta prossiga), enquanto notify acorda apenas uma arbitrária
		</details>
	</details>
</details>
