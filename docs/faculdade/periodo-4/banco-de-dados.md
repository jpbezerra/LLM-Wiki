# BANCO DE DADOS

---
## Conceitos Básicos
<details>
<summary>Dado</summary>
	- É um elemento bruto sem contexto.
</details>
<details>
<summary>Metadado</summary>
	- Dados que descrevem outros dados, dando significado
</details>
<details>
<summary>Informação</summary>
	- É um dado com sigificado e interpretado de forma útil
</details>
<details>
<summary>Conhecimento</summary>
	- É o uso da informação para tomar decisões
</details>
<details>
<summary>Banco de Dados</summary>
	- É uma coleção organizada de informações estruturadas sobre um domínio específico
	- No MVC (Model-View-Controller, padrão de arquitetura de software), os dados são acessados na camada mais baixa, o Model
		- O Model é a camada que acessa o banco de dados e é onde contém toda a lógica de CRUD e fornecendo os dados para as outras camadas
</details>
<details>
<summary>Sistema Gerenciador de Banco de Dados (SGBD)</summary>
	- É o software que gerencia e controla o banco de dados, permitindo aos usuários realizem o CRUD e outras funcionalidades
	- Motor que lê, organiza e escreve o banco de dados
	- MySQL, PostgresSQL, Oracle, etc.
	<details>
	<summary>Evolução dos SGBDs</summary>
		<details>
		<summary>Sistemas de Arquivos</summary>
			- Década de 1960
			- Utilizado antes do SGBD, na qual os usuários utilizavam os sistemas de arquivos do SO
			- Cada aplicação possuía o seu próprio arquivo e todo o controle da qualidade dos dados dependia dos programadores
			<details>
			<summary>Problemas</summary>
				- Havia muita redundâcia de dados (pois cada aplicação possuía o próprio sistema de arquivos) e de código fonte (por parte dos programadores)
					- O mesmo dado poderia estar repetido em vários arquivos, gerando inconsistência quando o dado é atualizado em apenas um arquivo, dificultando saber em qual é o dado correto
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Dificuldade no acesso dos dados, pois eram todos feitos pelo programador e dependia de sua disponibilidade
				- Como os dados estão dispersos em arquivos isolados, eles podem ter formatos e valores diferentes, sendo difícil escrever programas que precisam acessar estes dados
				- Caso uma operação dependesse de várias transações, caso uma delas falhe pode gerar uma inconsistência dos dados
					- A atomicidade garante que quando uma falha é detectada os dados voltam para o seu último estado consciente, garantir a atomicidade não era fácil de ser implementada
				- Acesso simultâneo de um mesmo dado podia gerar inconsistência dos dados
			</details>
			- Para resolver estes problemas, foi criado o SGBD
		</details>
		<details>
		<summary>1ª Geração</summary>
			- Década de 1970
			<details>
			<summary>SGBD Hierárquico</summary>
				- Foram os primeiros SGBDs, garantindo um controle centralizado dos dados
				- É baseado em uma estrutura de dados do tipo árvore e baseada em ponteiros (cada pai possuía ponteiros para cada filho)
				- Permitia relações de apenas 1:N
			</details>
			<details>
			<summary>SGBD em Rede</summary>
				- Reconhece a natureza não hierárquica dos dados
				- Baseado em uma estrutura de dados do tipo grafo (sem redundância, mas ainda baseada em ponteiros)
				- Permite relaçõesde M:N
				- Complexa de entender e manter, além de ter menor independência entre dados e programas
				- A manipulação de dados é feita por linguagem de baixo nível
			</details>
		</details>
		<details>
		<summary>2ª Geração</summary>
			- Década de 1980
			<details>
			<summary>SGBD Relacional</summary>
				- Não é baseado em ponteiros e possui forte fundamento matemático (relações, funções, conjuntos e álgebra relacional)
				- Manipulação de dados feita por SQL
				- Dados são representados por meio de tabelas (relações), organizados em linhas e colunas com chaves primárias e estrangeiras
				- Chave primária (Primary Key, PK)
					- Identificador único para cada linha de registro de uma tabela
					- Garante que duas linhas diferentes não possuam valores iguais
					- Não pode ser nula
				- Chave estrangeira (Foreign Key, FK)
					- É um campo que faz referência a uma PK de outra tabela
					- Permite criar relações do tipo 1:N e M:N
						- Numa tabela pode-se repetir os valores de uma FK (1:N) ou serem todos diferentes (M:N)
				- SGBD mais utilizada atualmente quando é necessário garantir a integridade dos dados
				- Oracle, PostgresSQL, etc.
			</details>
		</details>
		<details>
		<summary>3ª Geração</summary>
			- Década de 1990
			<details>
			<summary>SGBD Orientado a Objetos</summary>
				- Modelo mais natural para expressar a realidade, tudo é objeto
				- Surgiu baseado nas tendências da época em POO e oferece suporte
				- Não existe uma linguagem padronizada
				- Não tem base teórica
				- O paradigma não foi muito bem aceito pelo mercado, surgiu o SGBD Relacional-Objeto como resposta
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>SGBD Relacional-Objeto</summary>
				- Utiliza conceitos de OO sobre estruturas relacionais (SGBD Relacional + OO), combinando o melhor dos dois mundos
				- Suporte a tipos de dados abstratos (objetos complexos)
				- Baseado no SQL padrão mas com recursos de POO que são proprietários
				- Oracle, PostegresSQL, etc.
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>4ª Geração</summary>
			- Década de 2000
			<details>
			<summary>SGBD Não-Relacional</summary>
				- Voltados para atender e gerenciar grandes volumes de dados, buscando alto desempenho, disponibilidade e consistência eventual
					- Não organiza os dados em linhas e colunas com PKs e FKs
				- O esquema de dados é semi-estruturado, admitindo replicação e ausência de itens de dados (None) sem seguir uma estrutura rígida
					- JSON é um exemplo
				- Possui uma grande escalabilidade horizontal (múltiplos servidores), diferente dos SGBDs relacionais
				- MongoDB, Redis, Cassandra
			</details>
		</details>
	</details>
</details>
---
## Modelo Entidade Relacionamento (MER)
- É uma linguagem diagramática usada para modelagem de banco de dados e para especificar esquemas conceituais de BD
<details>
<summary>Componentes</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	- Retângulos: representam entidades
		<details>
		<summary>Entidades</summary>
			- Abstrações de um conceito concreto (cliente, livro, etc.) ou abstrato (conta, empréstimo, etc.)
			- Para se referir a uma ocorrência da entidade fala-se instância da entidade
		</details>
	- Losangos: representam relacionamentos (associações entre os conceitos)
		<details>
		<summary>Relacionamentos</summary>
			- Abstração de uma associação entre instâncias de uma ou mais entidades
				- Em um relacionamento deve existir todas as instâncias
			- Para se referir a uma ocorrência de um relacionamento fala-se instância do relacionamento
				- Cada relacionamento é uma informação diferente
			<details>
			<summary>Grau de um relacionamento</summary>
				- Representa a quantidade de entidades envolvidas no relacionamento
				- Unário (auto-relacionamento), binário (duas entidades), N-ário (N entidades)
			</details>
			<details>
			<summary>Papel de um relacionamento</summary>
				- Representa a função que uma dada entidade desempenhada no relacionamento
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Cardinalidade ou multiplicidade ou cardinalidade máxima de um relacionamento</summary>
				- Expressa o número máximo de vezes que uma instância de uma entidade, no pior caso, pode ter no relacionamento
				- Pode ser representada por qualquer número inteiro e positivo, por convenção utiliza-se 1 (um) e N (muitos)
					- Pode ser 1:1, 1:N ou M:N
			</details>
			<details>
			<summary>Participação ou obrigatoriedade ou cardinalidade mínima de um relacionamento</summary>
				- Especifica se uma instância, para ser cadastrada em uma entidade, deve estar relacionada com outra instância de alguma entidade do relacionamento
				- Quando a condição é exigida, diz-se que a participação é total ou que o relacionamento é obrigatório
				- Quando a condição não é exigida, diz-se que a participação é parcial ou que o relacionamento é opcional
				- Pode ser representada por qualquer número natural, mas por convenção usa-se os valores 0 (participação parcial) e 1 (participação total)
			</details>
			- A cardinalidade e participação podem ser especificadas do lado da entidade origem (look-here) ou destino (look-across)
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				<details>
				<summary>Look-Here</summary>
					- A FK está na entidade origem da relação
					- A entidade origem armazena a referência para a entidade destino
					- Os dados relacionados estão na entidade origem
					- Está relacionado com a participação
						- “Esta entidade precisa participar do relacionamento?”
				</details>
				<details>
				<summary>Look-Across</summary>
					- Precisa olhar para a entidade destino da relação para encontrar os dados relacionados
					- A FK está na entidade destino
					- Está relacionado com a cardinalidade
						- “Quantos da entidade destino se relacionam com a entidade origem?”
				</details>
				<details>
				<summary>Notação de Elmasri & Navathe</summary>
					- A participação é representada por linhas simples (participação parcial) ou duplas (participação total)
					- É possível usar a notação (min, max) quando os valores mínimo (participação) e máximo (cardinalidade) forem diferente dos valores padrões (0 ou 1 e 1 ou N respectivamente)
				</details>
				<details>
				<summary>Exemplos</summary>
					<details>
					<summary>1</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
					<details>
					<summary>2</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
					<details>
					<summary>3</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
					<details>
					<summary>4</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
				</details>
			- Duas entidades podem ter mais de um relacionamento entre elas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	- Elipses: representam atributos
		<details>
		<summary>Atributos</summary>
			- Propriedades descritiva de uma entidade ou relacionamento
			<details>
			<summary>Tipos</summary>
				- Simples: é indivisível
					- Ex: CPF, saldo, endereço
				- Composto: é formado por sub-atributos
					- Ex: endereço com rua, bairro e complemente
				- Monovalorado: admite apenas um valor para cada instância de entidade
					- Ex: CPF, saldo
				- Multivalorado: admite vários valores para cada instância de entidade
					- Ex: email telefone
				- Derivado: atributo calculado por meio de outros atributos
					- Ex: média de notas, saldo médio
				- Identificador: cada valor é único
					- Ex: CPF, código de matrícula
				- Discriminador: é um identificador parcial, atributos que sozinhos não identificam, mas com um atributo identificador identifica
					- Geralmente vem de outra entidade
					- Ex: data de pagamento
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			- Entidades devem ter atributos, mas nem todo relacionamento precisa ter
				- A cardinalidade de relacionamentos afeta a inserção de atributos nos relacionamentos ou entidades
				- É comum inserir atributos em relacionamentos M:N mas não é comum inserir atributos em relacionamentos 1:1, 1:N ou N:1
					- Em relacionamentos 1:N, é melhor colocar o atributo na entidade do lado N, ao invés no relacionamento
				- Se existe um ID, então é uma entidade, caso contrário pode ser um relacionamento
					- Relacionamentos com atributos são tabelas, se possui muitos atributos vira uma entidade
			<details>
			<summary>Exemplos</summary>
				<details>
				<summary>1</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>2</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>3</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>4</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>5</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
			</details>
		</details>
	- Linhas: ligam atributos a entidades ou entidades a relacionamentos
</details>
<details>
<summary>Relaciomento Unário</summary>
	- Relacionamento que engloba apenas 1 entidade, na qual ela assume dois papéis diferentes
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
</details>
<details>
<summary>Relacionamento Identificador</summary>
	- Permite usar o atributo identificador de uma entidade (entidade forte) para identificar outra entidade (entidade fraca)
		- Usado quando uma entidade não tem atributos capazes
	- Uma entidade com atributo descriminador é uma entidade fraca, pois possui do atributo identificador uma entidade forte
		- Uma entidade fraca, portanto, não possui atributo identificador
		- Toda instância de entidade fraca deve estar relacionada com no máximo uma instância de entidade forte
		- Relações 1:1 não devem possuir atributo discriminador
		- Relações 1:N devem possuir discriminador na entidade fraca
	- A cardinalidade da entidade forte é sempre 1
	- A participação da entidade fraca é sempre obrigatória (linha dupla)
		- Logo, a entidade fraca é existencialmente dependente da entidade forte
	- Não é interessante utilizar relacionamento identificador para impor participação obrigatória, mas sim participação obrigatória sem relacionamento identificado
		- Dificulta manutenção, afeta a legibilidade e aumenta o acoplamento entre entidades
	- O relacionamento identificador fica com losango duplo, a entidade fraca com retângulo duplo e o atributo identificador composto fica sublinhado
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Nesse caso, o atributo identificador das entidades fracas é a concatenação encadeada de atributos na entidade forte
		- Identificador de Agência = (numB,numA) e da Conta = (numB,numA,numC)
	</details>
</details>
<details>
<summary>Relacionamento N-ário</summary>
	- Se todas as vezes que um relacionamento ocorrer envolver as mesmas N entidades, então é um relacionamento N-ário
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Como descobrir a cardinalidade de uma entidade</summary>
		- É necessário considerar o pior caso possível e ter o seguinte formato: 1 instância de X e 1 instância de Y podem se relacionar com no máximo quantas instâncias de Z (1 ou N)?
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Participação</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- No esquema 1, nenhuma das 3 entidades é obrigada a participar do relacionamento “contrata”, ou seja, o cadastro de qualquer uma das 3 independe de outra entidade
		- No esquema 2, o cadastro de produto só acontece se ele estiver relacionado com cliente e com conta
			- Produto não existe sem o relaciomento de “contrata”, pois depende de cliente e conta
		- Nos dois esquemas, quando ocorre a relação este sempre envolverá um cliente, um produto e uma conta
	</details>
	<details>
	<summary>Relacionamento N-ário vs relacionamento binário</summary>
		- Se todos os clientes de uma conta sempre têm os mesmos produtos, então tem-se um relacionamento binário entre conta e produto
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Apesar de cliente não estar diretamente relacionamento com produto, a partir de conta é possível saber todos os produtos de um cliente (transitividade)
		- Caso em um relacionamento ternário uma entidade possuir cardinalidade 1, então provavelmente existe uma outra relação escondida, que não é ternária
			- No caso, vão ser duas relações binárias
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Apesar de 1 cliente com 1 conta corrente poder fazer parte de apenas 1 agência, 1 cliente pode fazer parte de N agências, causando uma contradição, enquanto que 1 conta corrente pode fazer parte de apenas 1 agência, o que está logicamente correto
					- A relação permite que uma mesma conta esteja atrelada a mais de uma agência
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Solução
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			- Se a partir de uma instância de entidade A é possível determinar uma instância de entidade B, então essas entidades formam um relacionamento binário e não N-ário
		- Além disso, 3 relacionamentos binários não substituem 1 relacionamento ternário
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
<details>
<summary>Entidade associativa</summary>
	- Se um relacionamento pode acontecer sem a presença de uma terceira entidade, deve-se usar a entidade associativa para representar o cenário
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Entidade associativa vs relacionamento n-ário</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
<details>
<summary>Herança</summary>
	- Cria uma hierarquia de entidades, onde as sub-entidades herdam todos os atributos e relacionamentos das super-entidades
		- Recomendável usar apenas se as sub-entidades possuírem atributos ou relacionamentos específicos
	<details>
	<summary>Notação</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Tipos</summary>
		- Disjunta ou sobreposta
			- Disjunta
				- Representada por um “d”
				- Cada instância da super entidade é especializada para uma instância de uma sub-entidade
			- Sobreposta
				- Representada por um “o”
				- Pelo menos uma instância da super entidade é especializada em mais de uma instância de sub-entidade
		- Total ou parcial
			- Total
				- Linha dupla
				- Toda instância da super entidade é especializada em pelo menos uma sub-entidade
			- Parcial
				- Linha simples
				- Pelo menos uma instância da super entidade não é especializada em uma sub-entidade
	</details>
	<details>
	<summary>Exemplos</summary>
		<details>
		<summary>Herança PD</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Herança TD</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Herança PO</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Herança TO</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	- Se existe apenas uma sub-entidade, a herança é direta
		- Não pode ser disjunta/sobreposta ou total/parcial
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	- Se as sub-entidades não têm atributos ou relacionamentos específicos, usar um atributo “tipo” no lugar da herança
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
</details>
<details>
<summary>Particularidades</summary>
	- Tem poder de expressão limitado, valores válidos e pré/pós condições devem ser informadas à parte
	- Esquemas ER diferentes podem ser equivalentes
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
</details>
<details>
<summary>Dúvidas frequentes</summary>
	<details>
	<summary>Modelar um conceito como atributo ou entidade</summary>
		- Se é meramente descritivo → atributo
		- Se tem identificador explícito → entidade
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Modelar um conceito que tem muitas propriedades como um atributo composto/multivalorado ou entidade</summary>
		- Se é exclusivo de uma entidade → atributo
		- Se pode ser compartilhado entre várias entidades → entidade
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Modelar conceitos como atributos ou usar herança</summary>
		- Se pode haver inconsistência entre os conceitos → herança
		- Caso contrário → atributo
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Modelar um conceito como relacionamento ou entidade</summary>
		- Se tem identificador explícito → entidade
		- Caso contrário → pode ser relacionamento
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Modelar um conceito com relacionamento n-ário ou entidade associativa</summary>
		- Se todas as vezes que o relacionamento ocorrer, sempre envolve todas as entidades participantes → relacionamento n-ário
		- Caso contrário → entidade associativa
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
<details>
<summary>Requisitos para um bom MER</summary>
	<details>
	<summary>Ser sintaticamente correto</summary>
		- O esquema deve respeitar regras sintáticas de construção
		- Exemplos de erros sintáticos
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Ser semanticamente correto</summary>
		- O esquema não pode ter atributos mal especificados
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- O esquema não pode ter relacionamentos com cardinalidades mal especificadas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- O esquema não pode ter relacionamentos com participações mal especificadas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- O esquema não pode ter relacionamentos com grau mal especificados
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- O esquema não pode capturar mais de uma realidade
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Evitar ou controlar construções redundantes</summary>
		- Construções redundantes podem melhorar o desempenho mas também podem gerar dados inconsistentes
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Capturar o aspecto temporal</summary>
		- Guardar o histórico de um atributo
		<details>
		<summary>Exemplos</summary>
			<details>
			<summary>1</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>1:1</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>1:N</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>M:N</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
	</details>
	<details>
	<summary>Ser completo</summary>
		- É mais fácil corrigir um erro no projeto conceitual do que em qualquer outra fase do projeto do banco de dados
		- O projeto conceitual do banco de dados pode ser feito a partir de:
			- Informações existentes
				- Estratégia de engenharia reversa: feita automaticamente por uma ferramenta CASE
				- Estratégia Bottom-Up: 1º atributos → 2º Entidades → 3º Relacionamentos → 4º Herança
			- Do conhecimento de especialistas
				- Estratégia Top-Down: 1º Entidades → 2º Relacionamentos → 3º Heranças → 4º Atributos
				- Estratégica Inside-Out: igual ao Top-Down, mas começa pelas entidades mais importantes
	</details>
</details>
---
## Modelo Relacional
- É um módelo lógico, não tão abstrato como o conceitual mas não considera aspectos físicos de armazenamento, acesso e desempenho
- Base sólida formal (teoria dos conjuntos) e é baseado em conceitos simples (relações com atributos, tuplas e domínios)
	- Baseado em tabelas que não podem ter subtabelas
	- Diversos conceitos do modelo conceitual não são implementados de forma tão direta no modelo relacional
- Base para o SQL
<details>
<summary>Definições</summary>
	<details>
	<summary>Domínio</summary>
		- Conjunto de valores atômicos
	</details>
	<details>
	<summary>Relação</summary>
		- Dados os conjuntos D1, …, Dn (domínios não necessariamente distintos), R é uma relação nestes n conjuntos se esta for um conjunto de tuplas \<v1, …, vn\> onde v1 ∈ D1, …, vn ∈ Dn, formando um subconjunto do produto cartesiano D1 x … x Dn
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Terminologia (Relação x Tabela)</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Propriedades</summary>
			- Toda relação tem um valor fixo de atributos distintos
			- O valor null é usado quando um atributo não tem valor ou este pe desconhecido
			- A ordem dos atributos e das tuplas é irrelevante, não há ordenação entre tuplas e os valores podem ser associados aos atributos independentemente de uma ordem
		</details>
	</details>
	<details>
	<summary>Chaves</summary>
		- Conceito usado para identificar e referenciar tuplas
		<details>
		<summary>Tipos</summary>
			<details>
			<summary>Chave candidata</summary>
				- É um atributo (chave simples) ou concatenação de atributos (chave composta) cujos valores distinguem uma tupla das demais tuplas de uma relação
					- Uma possível chave primária, deve possuir valores distintos e obrigatórios
				- Deve ser mínima
					- Caso ela seja simples, ela já é mínima
					- Caso contrário, deve verificar inconsistências
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Chave primária</summary>
				- É uma chave candidata escolhida para identificar uma tupla
				- É frequentemente utilizada para selecionar as tuplas de uma relação
				- Não admite valor null
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Chave estrangeira</summary>
				- Um atributo ou concatenção de atributos que faz referência a uma chave primária
					- A chave estrangeira é a chave primária de outra tabela, mas é a primária da tabela dela
					- Objetivo de linkar tabelas
				- É utilizada para relacionar tuplas de relações
				- Admite valor null (participação opcional)
					- Não precisa ser única e obrigatória
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Auto-relacionamento: é uma relação entre a mesma entidade, diferenciando apenas nos papéis
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Chave alternativa</summary>
				- É a chave candidata que não foi escolhida como chave primária
					- Não faz relacionamento com chave estrangeira
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
	</details>
</details>
<details>
<summary>Restrições</summary>
	<details>
	<summary>Restrições de integridade</summary>
		- Regras sobre os valores armazenados nas relações
		- Têm por objetivo garantir a consistência das relações
		<details>
		<summary>Restrições de domínio</summary>
			- Todo valor de um atributo deve ser atômico (simples e monovalorado) e pertencer ao domínio do atributo
		</details>
		<details>
		<summary>Restrições de chave</summary>
			- Todo valor de chave primária deve ser mínimo e único na relação
		</details>
		<details>
		<summary>Integridade da entidade</summary>
			- Chaves primárias não podem ter o valor null
		</details>
		<details>
		<summary>Integridade referencial</summary>
			- Especifica que os valores de uma chave estrangeira devem aparecer na chave primária da tabela referenciada
		</details>
		<details>
		<summary>Exemplo</summary>
			<details>
			<summary>Inserções e atualizações</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Exclusões</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
	</details>
	<details>
	<summary>Restrições semânticas</summary>
		- São restrições para impor regras de negócio
		- Devem ser implementadas pelos programadores pois não são automaticamente garantidas
		- Exemplo: um empregado não pode ter um salário maior que seu superior imediato
	</details>
</details>
<details>
<summary>Notação simplificada</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
</details>
<details>
<summary>Álgebra relacional</summary>
	- Desenvolvida para descrever operações sobre um BDR, ajudando a entender SQL (linguagens de consulta estruturada)
	<details>
	<summary>Compatibilidade de domínio</summary>
		- Duas relações A(a1, …, an) e B(b1, …, bn) são ditas compatíveis em domínio se ambas têm o mesmo grau n e se Dom(ai) = Dom(bi), tal que 1 ≤ i ≤ n
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Operações sobre conjuntos</summary>
		<details>
		<summary>União</summary>
			- Une as tuplas das relações A e B (A U B)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Interseção</summary>
			- Retorna as tuplas cujos valores sejam comuns à A e B (A ⋂ B)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Diferença</summary>
			- Retorna as tuplas de A cujos valores não estão em B (A - B)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Produto cartesiano</summary>
			- Combina todas as tuplas das relações A e B (A X B)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>União exclusiva</summary>
			- Retorna todas as tuplas de A ou B que não estão em ambas (A U\| B → A U B - A ⋂ B)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Operações relacionais unárias</summary>
		- Produzem como resultado uma nova relação que é um subconjunto (horizontal ou vertical) da relação origem
			- Subconjunto horizontal → muda as linhas
			- Subconjunto vertical → mudam as colunas
		<details>
		<summary>Seleção</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Projeção</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Seleção + Projeção</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Operações relacionais binárias</summary>
		- Produzem como resultado uma nova relação que é um subconjunto (seleção) do produto cartesiano das relações envolvidas
		- Em geral, após um produto cartesiano, é necessário comparar um grupo de atributos (compatíveis em domínio) para selecionar as tuplas do resultado final
		<details>
		<summary>Junção</summary>
			- Retorna apenas as tuplas do produto cartesiano de seus argumentos que satisfaçam uma dada condição
			- Sintaxe
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Divisão</summary>
			- Produz uma relação R(X) com as tuplas de R1(A) que estão combinadas com todas as tuplas R2(B)
			- Sintaxe
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
</details>
<details>
<summary>Mapeamento EER Relacional</summary>
	- O esquema EER pode gerar N esquemas Relacionais, existem várias maneiras de mapear relacionamentos e heranças
	<details>
	<summary>Prioridades no mapeamento</summary>
		1. Evitar junções → consultas mais rápidas
		2. Diminuir o número de chaves → índices menores e mais rápidos
		3. Evitar campos opcionais → menos testes de qualidade dos dados
	</details>
	<details>
	<summary>Nomeação de relações e atributos</summary>
		- Usar nomes curtos
		- Eliminar espaços em branco e caracteres especiais
		- Adotar um padrão
	</details>
	<details>
	<summary>Passos para fazer o mapeamento</summary>
		<details>
		<summary>Mapear as entidades regulares e seus atributos</summary>
			- Cada entidade regular é mapeada para uma relação
				- A PK da relação é o atributo identificador da entidade mapeada
			- Cada atributo multivalorado é mapeado para:
				- N atributos (desde de que N seja pequeno) ou
				- Uma relação cuja PK é o atributo multivalorado mais a PK da relação origem
					- A PK que migrou da relação origem é FK
			- Atributos comum, composto ou derivado são mapeados para atributos da relação
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Mapear as entidades fracas e seus atributos</summary>
			- Cada entidade fraca é mapeada para uma relação
				- A PK que mapeia a entidade forte migra como FK
				- A PK da relação é formada pela FK mais o discriminador, caso exista
			- Atributos comum, composto, derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Mapear as super/subentidades e seus atributos</summary>
			- 4 alternativas
				<details>
				<summary>Uma relação para cada entidade da herança</summary>
					<details>
					<summary>Características</summary>
						- Características fortes
							- Funciona bem para qualquer tipo de herança
							- Reduz atributos opcionais
							- Reduz testes para garantir a qualidade dos dados
						- Características fracas
							- Exige junções
					</details>
					<details>
					<summary>Mapeamento</summary>
						- Cada super/subentidade é mapeada para uma relação
							- A PK de cada relação é o atributo identificador da superentidade mapeada
							- A PK de cada relação que mapeia uma subentidade será FK para a superentidade
						- Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
					</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
				</details>
				<details>
				<summary>Uma relação para cada subentidade da herança total</summary>
					<details>
					<summary>Características</summary>
						- Características fortes
							- Reduz atributos opcionais
							- Reduz testes para garantir a qualidade dos dados
							- Reduz junções
						- Características fracas
							- Gera redudância de dados para heranças sobrepostas
					</details>
					<details>
					<summary>Mapeamento</summary>
						- Cada subentidade é mapeada para uma relação
							- A PK de cada relação é o atributo identificador da superentidade mapeada
						- Os atributos e relacionamentos da superentidade migram para as relações que mapeiam as subentidades
						- Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
					</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
				</details>
				<details>
				<summary>Uma única relação para toda herança disjunta ou direta</summary>
					<details>
					<summary>Características</summary>
						- Características fortes
							- Reduz junções
						- Características fracas
							- Só funciona com heranças definidas por um predicado/condição
							- Exige atributos opcionais
							- Exige testes para garantir a qualidade dos dados
								- Testar o povoamento dos atributos e dos relacionamentos
					</details>
					<details>
					<summary>Mapeamento</summary>
						- A superentidade e as subentidades de uma herança são mapeadas para uma única relação
							- A PK da relação é o atributo identificador da superentidade mapeada
						- O predicado/condição da herança torna-se um atributo da relação mapeada
							- Seu domínio deve cobrir as subentidades
						- Os atributos e relacionamentos das subentidades migram para a relação mapeada
						- Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
					</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
				</details>
				<details>
				<summary>Uma única relação para toda herança sobreposta</summary>
					<details>
					<summary>Características</summary>
						- Características fortes
							- Reduz junções
							- Reduz redundância de dados
						- Características fracas
							- Exige atributos opcionais
								- Desaconselhada quando as subentidades têm muitos atributos ou relacionamentos
							- Exige testes para garantir a qualidade dos dados
								- Testar o povoamento dos atributos e dos relacionamentos
					</details>
					<details>
					<summary>Mapeamento</summary>
						- A superentidade e as subentidades de uma herança são mapeadas para uma única relação
							- A PK da relação é o atributo identificador da superentidade mapeada
						- Para cada subentidade, criar na relação mapeada um atributo booleano
						- Os atributos e relacionamentos da superentidade e das subentidades migram para a relação mapeada
						- Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
					</details>
					<details>
					<summary>Exemplo</summary>
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					</details>
				</details>
		</details>
		<details>
		<summary>Mapear as entidades associativas</summary>
			- Cada entidade associativa é mapeada para uma relação
			- As PK das relações envolvidas migram como FK obrigatórias
			- Os atributos do relacionamento, caso existam, ficam na relação mapeada
			- A PK da relação depende do grau e da cardinalidade do relacionamento
				- Usar as mesmas regras aplicadas em relacionamentos
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Mapear os relacionamentos e seus atributos</summary>
			<details>
			<summary>Fusão de relações</summary>
				<details>
				<summary>Características</summary>
					- Características fortes
						- Reduz junções
					- Características fracas
						- Exige atributos opcionais
							- Desaconselhada quando as subentidades têm muitos atributos ou relacionamentos
						- Exige testes para garantir a qualidade dos dados
							- Testar o povoamento dos atributos e dos relacionamentos
				</details>
				<details>
				<summary>Mapeamento</summary>
					<details>
					<summary>Melhor caso 1:1 - Total/Total</summary>
						- Fundir as relações em uma única relação
						- A PK da relação fundida deve ser uma das PK originais
							- Dar preferência para a PK que poderá ser mais consultada
						- Usar \[\] para definir a outra PK como chave alternativa (AK)
						- Usar ! para definir a AK como obrigatória
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
					<details>
					<summary>Caso alternativo 1:1 - Total/Parcial</summary>
						- Fundir as relações em uma única relação
						- A PK da relação fundida deve ser a PK da relação original que tem participação parcial
							- Usar \[\] para definir a outra PK como AK
						- Avaliar custo x benefício
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
				</details>
			</details>
			<details>
			<summary>Adição de chave estrangeira</summary>
				<details>
				<summary>Características</summary>
					- Características fortes
						- Reduz atributos opcionais
						- Reduz testes para garantir a qualidade dos dados
					- Características fracas
						- Exige junção
				</details>
				<details>
				<summary>Mapeamento</summary>
					<details>
					<summary>Melhor caso 1:N</summary>
						- A PK da relação do lado 1 migra como FK para a outra relação
							- Caso o lado N seja total, usa ! para definir a FK como obrigatória
						- Os atributos do relacionamento, caso existam, migram com a PK
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
					<details>
					<summary>Caso alternativo 1:1</summary>
						- Parcial/Parcial
							- A PK de qualquer uma das relações migra como FK única e opcional (usar \[\] para definir a FK como única)
						- Total/Parcial
							- A PK da relação do lado parcial migra como FK única e obrigatória (usar \[\] + ! para definir a FK como única e obrigatória)
						- Total/Total
							- A PK de qualquer uma das relações migra como FK única e obrigatória (usar \[\] + ! para definir a FK como única e obrigatória)
						- Os atributos do relacionamento, caso existam, migram com a PK
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
				</details>
			</details>
			<details>
			<summary>Criação de relação</summary>
				<details>
				<summary>Características</summary>
					- Características fortes
						- Reduz atributos opcionais
						- Reduz testes para garantir a qualidade dos dados
					- Características fracas
						- Exige junção
				</details>
				<details>
				<summary>Mapeamento</summary>
					<details>
					<summary>Melhor caso M:N</summary>
						- Cada relacionamento M:N é mapeado para uma relação
						- As PK das relações envolvidas migram como FK
						- As composições das FK forma a PK da relação
						- Os atributos do relacionamento, caso existam, ficam na relação mapeada
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
					<details>
					<summary>Caso alternativo 1:N - evitar</summary>
						- O relacionamento 1:N é mapeado para uma relação
						- As PK das relações envolvidas migram como FK
						- A FK do lado N torna-se PK
						- A outra FK torna-se obrigatória (usar ! para definir a FK como obrigatória)
						- Os atributos do relacionamento, caso existam, ficam na relação mapeada
					</details>
					<details>
					<summary>Caso alternativo 1:1 - evitar</summary>
						- O relacionamento 1:1 é mapeado para uma relação
						- As PK das relações envolvidas migram como FK
						- A PK é definida a partir das participações do relacionamento
							- Parcial/Parcial → a PK pode ser qualquer uma das FK
							- Total/Parcial → a PK é a FK do lado parcial
							- Total/Total → a PK pode ser qualquer uma das FK
						- A outra FK torna-se única (AK) e obrigatória (usar \[\] + ! para definir a FK como única e obrigatória)
						- Os atributos do relacionamento, caso existam, ficam na relação mapeada
					</details>
					<details>
					<summary>Relacionamentos N-ários</summary>
						- Cada relacionamento n-ário é mapeado para uma relação
						- As PK das relações envolvidas migram como FK obrigatórias (usar ! para definir a FK como única e obrigatória)
						- Os atributos do relacionamento, caso existam, ficam na relação mapeada
						- A PK da relação depende da cardinalidade do relacionamento
							- N:N:N → PK formada por todas as FK
							- 1:N:N → PK dupla formada pelas FK do lado N
							- 1:1:N → caso raro e complexo
							- 1:1:1 → caso raro e complexo
						<details>
						<summary>Exemplo</summary>
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						</details>
					</details>
				</details>
			</details>
		</details>
	</details>
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		<details>
		<summary>Mapeando entidades</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando herança</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando entidade associativa</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando relacionamento 1:1</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando relacionamento 1:N</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando relacionamento M:N</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Mapeando relacionamento N-ário</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
</details>
<details>
<summary>Normalização</summary>
	- Processo matemático fundamentado na teoria dos conjuntos, aplicando uma série de regras sobre as tabelas de um BD para verificar se estas foram bem projetadas
	<details>
	<summary>Objetivos</summary>
		- Decompor uma relação até que esta fique com pouca ou nenhuma redundância de dados
		- Impedir anomalias de inserção, atualização e exclusão
		- Permitir representar eficientemente os dados no mundo real, tornando o modelo mais estável e fácil de manter
		- Pode ser usada para validar o modelo relacional gerado pelas transformações vistas anteriormente e também gerar modelos relacionais a partir de documentos da organização
	</details>
	- Do ponto de vista prático e de desempenho, sua aplicação nem sempre é ideal
	- Aplicar a normalização até a 3FN ou FNBC
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Definições</summary>
		<details>
		<summary>Dependência Funcional (DF)</summary>
			- Quando um conjunto de atributos A1 identifica um conjunto de atributos A2, diz-se que há uma dependência funcional entre A1 e A2, onde A1 é o determinante e A2 é o dependente
			- Representação
				- A1 → A2 (lê-se: determina A2 ou A2 é dependente de A1)
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Dependência Funcional Parcial (DFP)</summary>
			- Ocorre quando um conjunto de atributos dependem apenas de parte de um determinado composto
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Dependência Funcional Total (DFT)</summary>
			- Ocorre quando um conjunto de atributos depende de todo determinado composto
		</details>
		<details>
		<summary>Dependência Funcional Transitiva (DF Transitiva)</summary>
			- Dada uma relação qualquer, diz-se que existe DF Transitiva quando um conjunto de atributos A3 depende de um atributo A2, que não é PK, mas que A2 depende funcionalmente da PK A1
			- Ou seja, considerando que A1 é PK, mas A2 não é, se A1 → A2 e A2 → A3, então diz-se que A3 depende transitivamente de A1, através de A2
			- Exemplo
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Formas Normais</summary>
		<details>
		<summary>1ª Forma Normal (1FN)</summary>
			- Uma relação está na 1FN quando os domínios de todos os seus atributos são atômicos
			- Ou seja, a relação não pode mapear atributos compostos ou multivalorados
			<details>
			<summary>Transformação</summary>
				<details>
				<summary>Atributo composto</summary>
					- Decompor o atributo cmposto em atributos simples e colocá-los na mesma relação ou em uma nova relação
					- Quando o atributo composto é monovalorado, colocar na mesma relação
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Quando o atributo composto é multivalorado, colocar em uma nova relação
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>Atributo multivalorado</summary>
					- Decompor o atributo multivalorado em atributos simples e colocá-los na mesma relação ou em uma nova relação
					- Quando a quantidade de valores é pequena e conhecida a priori, colocar na mesma relação
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Quando a multivaloração é desconhecida ou grande, colocar em uma nova relação
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
			</details>
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>2ª Forma Normal (2FN)</summary>
			- Uma relação está na 2FN quando ela está na 1FN, a PK é composta e todas as colunas que não participam da PK são dependentes de todas as colunas que compõem a PK, isto é, não existe DFP
			<details>
			<summary>Transformação</summary>
				- Retirar os atributos com DFP da relação original
					- A partir destes atributos retirados, cria-se uma ou mais relações compostas pela parte da PK e seus atributos dependentes
					- A parte da PK que gerou dependência será a nova PK da tabela criada
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Exemplo (DFP)</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>3ª Forma Normal (3FN)</summary>
			- Uma relação está na 3FN quando ela está na 2FN e quando todos os atributos que não participam da PK são exclusivamente dependentes desta, isto é, a relação não contém DF Transitiva
			- Na maioria das vezes a normalização até a 3FN é suficiente, mas na literatura aparecem outras formas normais
			<details>
			<summary>Transformação</summary>
				- Retirar os atributos com DF Transitiva da relação original
					- A partir destes atributos retirados, cria-se uma ou mais relações compostas pelo atributo determinante (como PK) mais as suas colunas dependentes
						- Verifica-se a 2FN para cada nova tabela
					- Além de não conter DF Transitiva, as relações 3FN não devem possuir atributos com valores calculados ou derivados
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Exemplo (DF Transitiva)</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Forma Normal BOYCE/CODD (FNBC)</summary>
			- É um refinamento da 3FN, usada em casos particulares
			- Uma relação está na FNBC quando todos os determinantes da relação devem ser chaves candidatas/alternativas
			<details>
			<summary>Transformação</summary>
				- Decompor a relação original em duas ou mais relações, separando os atributos que depende do atributo que não é chave candidata (ou seja, um atributo que é determinante da relação)
					- O determinante que não é chave candidata/alternativa na relação original deve fazer parte da PK das novas relações
					- Verifica-se a 3FN para cada nova relação
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
	</details>
</details>
---
## SQL
- Ferramenta de programação usada para os bancos de dados
<details>
<summary>Tipos de comandos</summary>
	<details>
	<summary>Data Definition Language (DDL)</summary>
		- Permite a criação, manutenção e eliminação de objetos do banco de dados, como tabelas, índices, sequências e views
		- Convenção de nomes
			- Devem começar com uma letra
			- Pode ter de 1 a 30 caracteres
			- Pode conter somente A-Z, a-z, 0-9, _, \$ e #
			- Os nomes devem ser únicos por usuário
			- Não podem ser utilizadas palavras reservadas (salvo se entre aspas)
		- Chaves naturais só devem ser usadas quando forem pequenas e raramente sofrerem atualizações
			- Atualizações na PK impactam nos índices e nas FKs
			- É preferível chaves artificiais se a chave natural for grande ou passível de atualização (ex: auto incremento)
		<details>
		<summary>Tipos de Dados</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Restrições</summary>
			<details>
			<summary>Restrição de integridade de tabelas</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Restrição de integridade de colunas</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Restrições de integridade referencial</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Estudo de Caso</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Restrições
				- CONSTRAINT PK_USUARIOS PRIMARY KEY (CPF) → define CPF como a PK de PESQUISADOR
				- CONSTRAINT AK_USU_CPF UNIQUE (NOME, NASCIMENTO) → cria uma AK ou restrição única, garante que não exista duas pessoas com o mesmo nome e mesma data de nascimento cadastradas
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- CONSTRAINT PK_ARTIGO PRIMARY KEY (MAT) → define MAT como PK de ARTIGO
			- CONSTRAINT FK_ART_EVE FOREIGN KEY (COD) REFERENCES EVENTO (COD) → define COD como uma FK, garantindo o link entre EVENTO e ARTIGO (presente na relação de publica)
			- CONSTRAINT CHK_ART_NOTA CHECK (NOTA BETWEEN 0 AND 10) → regra de checagem que força que o valor de nota esteja sempre entre 0 e 10
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- CONSTRAINT ESCREVE_PK PRIMARY KEY (CPF, MAT) → define a PK como composta, fazendo com que a combinação entre CPF e MAT seja única
			- CONSTRAINT ESCREVEPESQUISADOR_FK FOREIGN KEY (CPF) REFERENCES PESQUISADOR ON DELETE CASCADE → cria a FK que aponta para CPF na tabela de PESQUISADOR, além disso, caso algum pesquisador for deletado na tabela de ESCREVE, ele também será deletado na tabela de PESQUISADOR
			- CONSTRAINT ESCREVEARTIGO_FK FOREIGN KEY (MAT) REFERENCES ARTIGO ON DELETE CASCADE → cria a FK que aponta para MAT na tabela de ARTIGO, além disso, caso algum pesquisador for deletado na tabela de ESCREVE, ele também será deletado na tabela de ARTIGO
		</details>
		<details>
		<summary>Comandos</summary>
			- Criar tabelas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Alterar tabelas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Excluindo ou limpando uma tabela
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Criando e excluindo índices
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Criar índices quando a tabela tem muitas linhas, a coluna contém inúmeros valores distintos, a coluna é muito usada para fazer filtros e a coluna sofre pouca atualização
				- Não criar indíces quando a tabela é pequena, a coluna contém muitos valores repetidos, a coluna dificilmente é usada para fazer fazer filtros e quando sofre atualização frequente
			- Criando e excluindo sequências
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Criando e excluindo views
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Criando e excluindo papéis/usuários
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Data Query Language (DQL)</summary>
		<details>
		<summary>Comandos</summary>
			- SELECT: seleciona dados, \* é para selecionar todos os dados de determinada tabela.
				- A seleção pode vir por meio do schema, como: SELECT \* FROM public.database ao invés de SELECT \* FROM database
				- Pode vir em conjunto de funções de agregação
			- FROM: especifica de qual tabela os dados serão selecionados.
			- WHERE: funciona como uma filtragem em uma consulta de tabela.
			- ORDER BY: ordena os resultados
				- ASC para ordenar de forma ascendente
				- DESC para ordenar de forma descendente
				- Pode possuir mais de uma ordenação, tem mais prioridade a ordenação mais a esquerda
				<details>
				<summary>Exemplo</summary>
					```sql
-- Ordena clientes pelo país
SELECT * FROM customers ORDER BY country;
-- Ordena por país em ordem descendente
SELECT * FROM customers ORDER BY country DESC;
-- Ordena por país e nome do contato
SELECT * FROM customers ORDER BY country, contact_name;
-- Ordena por país em ordem ascendente e nome em ordem descendente
SELECT * FROM customers ORDER BY country ASC, contact_name DESC;
					```
				</details>
			- GROUP BY: agrupar registros
				- Ao usar, precisa se certificar de que todas as colunas não agregadas na cláusula de SELECT estão no GROUP BY
			- HAVING: filtrar os resultados de grupos de linhas após a aplicação de funções de agregação
				- Difere do WHERE pois o WHERE filtra antes do agrupamento, já o HAVING filtra depois
			- PARTITION BY: divide o conjunto de resultados em partições ou grupos, peça central das Window Functions
				<details>
				<summary>Window Functions</summary>
					- É usada para realizar cálculos em conjunto de linhas relacionadas ao registro atual dentro uma janela definida
					- Essas funções permitem agregar, classificar ou manipular dados sem colapsar as linhas em um único valor
					- As window functions podem ser usadas fora de cláusulas PARTITION BY
					1. Não reduz as linhas do resultado
					2. Definem uma janela (escopo)
						- Definida por cláusulas como PARTITION BY e GROUP BY
					<details>
					<summary>Sintaxe geral</summary>
						```sql
SELECT
	.
	.
	window_function_name(arg1, arg2, ...) OVER (
	  [PARTITION BY partition_expression, ...]
	  [ORDER BY sort_expression [ASC | DESC], ...]
	) AS column_name
FROM
	tabela t;
						```
					</details>
					<details>
					<summary>Funções</summary>
						- OVER: usada em conjunto com window functions para definir a janela sobre a qual a função será apliada
						- AGREGATE
							- COUNT(): conta as ocorrências
								- Em conjunto com o GROUP BY, é possível contar em quantas vezes cada ocorrência de uma coluna ocorreu
							- MIN(): valor mínimo
							- MAX(): valor máximo
							- AVG(): média, ter cuidado com floats
							- SUM(): soma, ter cuidado com floats
						- RANKING
							- NTILE(): divde um conjunto de dados ordeado em um número especificado de grupos aproximadamente iguais
							- RANK(): atribui um rank único a cada linha, deixando lacunas em caso de empates
							- DENSE_RANK(): atribui um rank único a cada linha, com ranks contínuos para linhas empatadas
							- ROW_NUMBER(): atribui um número sequencial único a cada linha dentro de uma partição ou conjunto de resultado
							- PERCENT_RANK(): calcula o rank relativo de uma linha específica dentro do conjunto de resultados como uma porcentagem
								- Fórmula: PERCENT_RANK = (RANK - 1) / (N - 1)
									- N → número total de linhas no conjunto de dados
									- RANK → rank da linha dentro do conjunto de dados
							- CUME_DIST(): calcula a distribuição acumulada de um valor no conjunto de resultados. Representa a proporção de linhas que são menores ou iguais à linha atual
								- Fórmula: CUME_DIST = (Número de linhas com valores \<= linha atual) / (Número total de linhas)
						- VALUE
							- LAG(): permite acessar o valor da linha anterior dentro de um conjunto de resultados. Isso é particularmente útil para fazer comparações com a linha atual ou identificar tendências ao longo do tempo
							- LEAD(): permite acessar o valor da próxima linha dentro de um conjunto de resultados, possibilitando comparações com a linha subsequente
							- FIRST_VALUE(): retorna o primeiro valor de uma coluna ou expressão
							- LAST_VALUE(): retorna o último valor de uma coluna ou expressão
							- NTH_VALUE(): retorna o valor N de uma coluna ou expressão
					</details>
				</details>
			- LIMIT: limita a quantidade de linhas da query
			- OFFSET: especifica a partir de qual linha a query deve começar
		</details>
		<details>
		<summary>Esqueleto</summary>
			```sql
SELECT -- Quais colunas você quer ver?
    coluna1, coluna2, COUNT(*)
    window_function_name(arg1, arg2, ...) OVER (
		  [PARTITION BY partition_expression, ...]
		  [ORDER BY sort_expression [ASC | DESC], ...]
		)
FROM -- De qual tabela principal?
    tabela_principal
JOIN -- Quer combinar com qual outra tabela?
    outra_tabela ON tabela_principal.id = outra_tabela.id_principal
WHERE -- Quais filtros você quer aplicar nas linhas?
    coluna1 > 100
GROUP BY -- Quer agrupar as linhas por algum critério?
    coluna2
HAVING -- Quer filtrar os grupos que você criou?
    COUNT(*) > 5
ORDER BY -- Como você quer ordenar o resultado final?
    coluna1 DESC
LIMIT -- Quantas linhas você quer como resultado?
    10
OFFSET -- A partir de qual linha você quer começar?
    20;
			```
		</details>
		<details>
		<summary>Ordem</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Data Manipulation Language (DML)</summary>
		<details>
		<summary>Comandos</summary>
			- Inserção
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Atualização
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Remoção
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Funções de manipulação de string
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Funções de manipulação de números
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			<details>
			<summary>Exemplos</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Joins</summary>
			- Servem para combinar dados de duas tabelas em uma única consulta com base em colunas comuns entre essas duas tabelas
				<details>
				<summary>Tabela de junções</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				- Se não especificar o tipo de JOIN, o padrão vai ser o INNER
				- OUTER: serve para descrever explicitamente joins externos
					- Esses joins externos incluem os registros de uma tabela mesmo quando não há correspondência na outra tabela, preenchendo os valores ausentes com NULL.
				- ON: definir a condição de junção
			<details>
			<summary>Tipos</summary>
				- INNER JOIN: utilizado quando você precisa de registros que têm correspondência exata em ambas as tabelas
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
INNER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
						```
					</details>
				- LEFT JOIN (ou LEFT OUTER JOIN): usado quando quer todos os registros da primeira (esquerda) tabela, com os correspondentes da segunda (direita) tabela. Se não houver correspondência, a segunda tabela terá campos NULL
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
LEFT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
						```
					</details>
				- RIGHT JOIN (ou RIGHT OUTER JOIN): é o inverso do Left Join e é menos comum. Usado quando queremos todos os registros da segunda (direita) tabela e os correspondentes da primeira (esquerda) tabela
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
RIGHT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
						```
					</details>
				- FULL OUTER JOIN: utilizado quando queremos a união de Left Join e Right Join, mostrando todos os registros de ambas as tabelas, e preenchendo com NULL onde não há correspondência
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
FULL OUTER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
						```
					</details>
				- CROSS JOIN: retorna o **produto cartesiano** das tabelas, combinando cada registro da tabela à esquerda com todos os registros da tabela à direita, não precisando de uma condição ON
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
CROSS JOIN tabela2;
						```
					</details>
				- NATURAL JOIN: realiza o join automaticamente com base nas colunas de mesmo nome em ambas as tabelas, não exige especificação explícita das condições de join
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
NATURAL JOIN tabela2;
						```
					</details>
				- SELF JOIN: é um join de uma tabela com ela mesma, geralmente usado para comparar registros dentro da mesma tabela
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT a.coluna1, b.coluna2
FROM tabela a
INNER JOIN tabela b ON a.coluna_comum = b.coluna_comum;
						```
					</details>
				- LATERAL JOIN: usado para unir tabelas com subconsultas que dependem de cada linha da tabela principal. É útil quando a subconsulta precisa de informações da linha atual
					<details>
					<summary>Sintaxe</summary>
						```sql
SELECT coluna1, coluna2
FROM tabela1
JOIN LATERAL (subconsulta) AS alias ON condição;
						```
					</details>
			</details>
			<details>
			<summary>Exemplos</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- A consulta não está errada, mas não é boa prática pois mistura as tabelas sem cláusulas JOIN
					```sql
SELECT A.TITULO, E.SIGLA
FROM ARTIGO A
JOIN EVENTO E ON A.TITULO = E.SIGLA;
					```
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
		<details>
		<summary>Subconsultas</summary>
			- Consiste de um comando que fica dentro de outro comando principal, facilitando a resolução de problemas mais complexos
				- Identificada pelo uso de SELECT
			- As subconsultas são categorizadas quanto a quantidade de linhas e colunas retornadas, bem como quanto a dependências entre as subconsultas
				<details>
				<summary>Quantidade de linhas e colunas retornadas</summary>
					- Escalar → retorna um único valor (uma única linha e coluna)
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Linha → retornam várias colunas, mas apenas uma linha
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Tabela → retornam uma ou mais colunas e múltiplas linhas
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>Dependências entre as subconsultas</summary>
					- Simples → a subconsulta pode ser executada de forma independente, sem precisar de um valor obtido apenas pela consulta principal
					- Correlacionada → a subconsulta possui uma dependência com a consulta principal, precisando de algum valor obtido apenas dela
						- SEMI JOIN → um semi join entre a tabela A e a tabela B retorna as linhas da tabela A para as quais existe pelo menos uma correspondência na tabela B
							- Feita principalmente pelo EXISTS (mais performático, pois usa índice), mas também pode ser feito pelo IN
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
						- ANTI JOIN (ou ANTI SEMI JOIN, negação do SEMI JOIN) → oposto do semi join, retornando as linhas da tabela A para as quais não existe nenhuma correspondência na tabela B
							- Feito através do NOT EXISTS (mais perfomático, pois usa índice), mas também pode ser feito pelo NOT IN
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
							> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>Exemplos</summary>
					- Subconsulta simples e escalar no SELECT/WHERE
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Subconsulta simples e tabela no FROM
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Subconsulta simples e tabela no HAVING
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Avaliação condicional
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
		</details>
		<details>
		<summary>Set Operators</summary>
			- UNION → união de dois conjuntos removendo as duplicatas
				- UNION ALL → união de dois conjuntos mantendo as duplicatas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- INTERSECT → faz a interseção entre dois conjuntos, retornando apenas as linhas que existem em ambos os resultados das consultas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- EXCEPT → retorna as linhas da primeira consulta que não existem na segunda consulta
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- União Exclusiva (ou complemento) → retorna as linhas que estão na primeira ou na segunda consulta, mas não em ambas
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Divisão relacional → dada duas tabelas, retorna uma nova relação contendo as tuplas da primeira tabela que estão associadas a tuplas da segunda tabela
				- Projetada para responder uma pergunta do tipo: Quais X estão associados a TODOS os Y de determinado conjunto
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Data Control Language (DCL)</summary>
		- Serve para gerenciar as permissões e o acesso dos usuários ao banco de dados
		- GRANT → conceder privilégios ou permissões a um usuário ou a um grupo de usuários
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- REVOKE → remove os privilégios e permissões
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- DENY (ausente no Oracle) → cria uma proibição explícita, se sobressaindo a um GRANT
	</details>
	<details>
	<summary>Transaction Control Language (TCL)</summary>
		- Gerenciar transações em um banco de dados
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			<details>
			<summary>Propriedades ACID</summary>
				- Atomicidade → todas as operações de uma transação devem ser efetivadas, ou, na ocorrência de uma falha, nada deve ser efetivado
				- Consistência → transações preservam a consistência da base, garantindo que a transação leve o banco de dados de um estado válido para outro estado válido
				- Isolamento → a maneira como várias transações em paralelo interagem deve ser bem definido, garantindo que transações concorrentes não interfiram umas as outras
				- Durabilidade → uma vez consolidada a transação, suas alterações permanecem no banco até que outras transações aconteçam
			</details>
		- START TRANSACTION/BEGIN TRANSACTION → marca o início de uma transação
		- COMMIT → comando para salvar permanentemente todas as alterações realizadas desde o início da transação
		- ROLLBACK → comando para descartar as alterações feitas desde o início da transação
		- SAVEPOINT → cria um marcador dentro de uma transação longa
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
</details>
---
## PL/SQL
- É uma linguagem procedural da Oracle, estendendo a SQL-DML com comandos que permitem a criação de blocos de procedimentos de programação
	- Não aceita SQL-DDL 
<details>
<summary>Estrutura básica</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Tipo de bloco</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Tipos de identificadores</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		<details>
		<summary>Tipo Primitivo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Exemplos
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Tipo Registro</summary>
			- Semelhante a uma estrutura de dados
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Tipo Tabela</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Manipulando uma coleção do tipo tabela
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Operadores</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
<details>
<summary>Estrutura de aninhamento</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
</details>
<details>
<summary>Consultas</summary>
	<details>
	<summary>SELECT</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>INSERT</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>UPDATE</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>DELETE</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
<details>
<summary>Fluxos</summary>
	<details>
	<summary>IF</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Exemplo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Não esquecer de inicializar as variáveis no DECLARE
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>CASE</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Exemplo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>LOOP</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Exemplo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>WHILE</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Exemplo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>FOR</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Exemplo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>CURSOR</summary>
		- Semelhante a um ponteiro para manipular linhas de uma tabela temporária
		- Tipos
			- Implícito: declarado e gerenciado pelo servidor Oracle para todo comando DML e PL/SQL SELECT
			- Explícito: declarado e gerenciado pelo programador, gerado apenas pelo SELECT
		<details>
		<summary>Fluxo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Sintaxe</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			<details>
			<summary>Abrindo um cursor</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Lendo um cursor</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				<details>
				<summary>Usando LOOP/EXIT</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
				<details>
				<summary>Usando WHILE</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
			</details>
			<details>
			<summary>Fechando um cursor</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Tipo registro</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Cursor com laços FOR</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Cursor com laços FOR sem declaração
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Cursor com parâmetros</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
		</details>
	</details>
	<details>
	<summary>Exceções</summary>
		- Fluxo
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		- Tratamento
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			<details>
			<summary>Exceções predefinidas</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Exemplo
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
			<details>
			<summary>Exceções criadas</summary>
				- Criação
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Exemplo
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
	</details>
</details>
<details>
<summary>Subprogramas</summary>
	- Bloco de código nomeado (não usar DECLARE), podendo ser PROCEDURE (por padrão não retornam valor) ou FUNCTION (por padrão, necessariamente, retornam valor)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	<details>
	<summary>Sintaxe</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		<details>
		<summary>Exemplo procedimento</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Exemplo função</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Chamando subprogramas</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Subprogramas parametrizados</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		<details>
		<summary>Modos de passagem de parâmetro</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
	<details>
	<summary>Excluindo subprogramas</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Organizando subprogramas</summary>
		- Pacote: estrutura que agrupa logicamente subprogramas, tipos de dados, variáveis e etc. encapsulando-os em um único objeto do banco de dados
		- Os subprogramas devem ser especificados de forma que um subprograma ao ser “chamado” já tenha sido especificado antes
		- Formado pela Especificação (público) e Corpo (Privado)
		<details>
		<summary>Sintaxe</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Chamando pacotes</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		<details>
		<summary>Removendo pacotes</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
	</details>
</details>
<details>
<summary>Triggers</summary>
	- São códigos de PL/SQL armazenados no SGBD, associados a um objeto do BD
	- São executados implicitamente pelo SGBD na ocorrência de um determinado evento ou combinação deles
	- Podem ser usados para registrar modificações, garantir regras de negócio, gerar valor de coluna e manter tabelas duplicadas
	- Recomenda-se não ultrapassar 60 linhas, caso contrário chamar subprogramas
	- Não tem como definir a ordem de execução entre triggers
	- Não usar para refazer ações pré-existentes no SGBD
	<details>
	<summary>Sintaxe</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
	<details>
	<summary>Componentes</summary>
		- Momento
			- Corresponde ao tempo (BEFORE, AFTER ou INSTEAD OF) em que o trigger deve ser executado
		- Evento
			- DBA (Database Administrator): CREATE, ALTER, DROP, SERVERERROR, LOGON, LOGOFF, STARTUP, SHUTDOWN, GRANT e REVOKE
			- DML (INSERT, DELETE e UPDATE)
		<details>
		<summary>Exemplos</summary>
			- Momento/Evento - DML
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Evento - DML
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			- Momento/Evento - VIEW (INSTEAD OF)
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Evento - VIEW
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
		</details>
		- Tipo
			- Só aplicável a eventos DML
			- Comando
				- Acionado antes ou depois de um comando, independente deste atualizar ou não uma ou mais linhas
				- Não permite acesso as linhas atualizadas
				- Sintaticamente, basta não usar “FOR EACH ROW”
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
			- Linha
				- Adicionado para cada linha afetada
				- UPDATE requer a definição do campo (UDATE OF campo)
				<details>
				<summary>Exemplo</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
					- Com cláusula WHEN
						> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				</details>
		- Ação
			- Bloco PL/SQL associado ao evento
			- Requer a definição de predicados lógicos quando o trigger tem mais de um evento DML
				- INSERTING: quando o trigger foi disparado por um INSERT
				- UPDATING: quando o trigger foi disparado por um UPDATE
				- DELETING: quando o trigger foi disparado por um DELETE
			<details>
			<summary>Exemplo</summary>
				> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
				- Impedindo um comando DML
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
			</details>
	</details>
	<details>
	<summary>Remoção de triggers</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/1ea237a41945803ebc70c8b7c9545326)*
	</details>
</details>
