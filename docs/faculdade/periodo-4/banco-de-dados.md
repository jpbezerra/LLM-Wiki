# BANCO DE DADOS

---

## Conceitos Básicos

- Dado
    - É um elemento bruto sem contexto.
- Metadado
    - Dados que descrevem outros dados, dando significado
- Informação
    - É um dado com sigificado e interpretado de forma útil
- Conhecimento
    - É o uso da informação para tomar decisões
- Banco de Dados
    - É uma coleção organizada de informações estruturadas sobre um domínio específico
    - No MVC (Model-View-Controller, padrão de arquitetura de software), os dados são acessados na camada mais baixa, o Model
        - O Model é a camada que acessa o banco de dados e é onde contém toda a lógica de CRUD e fornecendo os dados para as outras camadas
- Sistema Gerenciador de Banco de Dados (SGBD)
    - É o software que gerencia e controla o banco de dados, permitindo aos usuários realizem o CRUD e outras funcionalidades
    - Motor que lê, organiza e escreve o banco de dados
    - MySQL, PostgresSQL, Oracle, etc.
    - Evolução dos SGBDs
        - Sistemas de Arquivos
            - Década de 1960
            - Utilizado antes do SGBD, na qual os usuários utilizavam os sistemas de arquivos do SO
            - Cada aplicação possuía o seu próprio arquivo e todo o controle da qualidade dos dados dependia dos programadores
            - Problemas
                - Havia muita redundâcia de dados (pois cada aplicação possuía o próprio sistema de arquivos) e de código fonte (por parte dos programadores)
                    - O mesmo dado poderia estar repetido em vários arquivos, gerando inconsistência quando o dado é atualizado em apenas um arquivo, dificultando saber em qual é o dado correto
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image.png)
                    
                - Dificuldade no acesso dos dados, pois eram todos feitos pelo programador e dependia de sua disponibilidade
                - Como os dados estão dispersos em arquivos isolados, eles podem ter formatos e valores diferentes, sendo difícil escrever programas que precisam acessar estes dados
                - Caso uma operação dependesse de várias transações, caso uma delas falhe pode gerar uma inconsistência dos dados
                    - A atomicidade garante que quando uma falha é detectada os dados voltam para o seu último estado consciente, garantir a atomicidade não era fácil de ser implementada
                - Acesso simultâneo de um mesmo dado podia gerar inconsistência dos dados
            - Para resolver estes problemas, foi criado o SGBD
        - 1ª Geração
            - Década de 1970
            - SGBD Hierárquico
                - Foram os primeiros SGBDs, garantindo um controle centralizado dos dados
                - É baseado em uma estrutura de dados do tipo árvore e baseada em ponteiros (cada pai possuía ponteiros para cada filho)
                - Permitia relações de apenas 1:N
            - SGBD em Rede
                - Reconhece a natureza não hierárquica dos dados
                - Baseado em uma estrutura de dados do tipo grafo (sem redundância, mas ainda baseada em ponteiros)
                - Permite relaçõesde M:N
                - Complexa de entender e manter, além de ter menor independência entre dados e programas
                - A manipulação de dados é feita por linguagem de baixo nível
        - 2ª Geração
            - Década de 1980
            - SGBD Relacional
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
        - 3ª Geração
            - Década de 1990
            - SGBD Orientado a Objetos
                - Modelo mais natural para expressar a realidade, tudo é objeto
                - Surgiu baseado nas tendências da época em POO e oferece suporte
                - Não existe uma linguagem padronizada
                - Não tem base teórica
                - O paradigma não foi muito bem aceito pelo mercado, surgiu o SGBD Relacional-Objeto como resposta
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%201.png)
                
            - SGBD Relacional-Objeto
                - Utiliza conceitos de OO sobre estruturas relacionais (SGBD Relacional + OO), combinando o melhor dos dois mundos
                - Suporte a tipos de dados abstratos (objetos complexos)
                - Baseado no SQL padrão mas com recursos de POO que são proprietários
                - Oracle, PostegresSQL, etc.
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%202.png)
                
        - 4ª Geração
            - Década de 2000
            - SGBD Não-Relacional
                - Voltados para atender e gerenciar grandes volumes de dados, buscando alto desempenho, disponibilidade e consistência eventual
                    - Não organiza os dados em linhas e colunas com PKs e FKs
                - O esquema de dados é semi-estruturado, admitindo replicação e ausência de itens de dados (None) sem seguir uma estrutura rígida
                    - JSON é um exemplo
                - Possui uma grande escalabilidade horizontal (múltiplos servidores), diferente dos SGBDs relacionais
                - MongoDB, Redis, Cassandra

---

## Modelo Entidade Relacionamento (MER)

- É uma linguagem diagramática usada para modelagem de banco de dados e para especificar esquemas conceituais de BD
- Componentes
    
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%203.png)
    
    - Retângulos: representam entidades
        - Entidades
            - Abstrações de um conceito concreto (cliente, livro, etc.) ou abstrato (conta, empréstimo, etc.)
            - Para se referir a uma ocorrência da entidade fala-se instância da entidade
    - Losangos: representam relacionamentos (associações entre os conceitos)
        - Relacionamentos
            - Abstração de uma associação entre instâncias de uma ou mais entidades
                - Em um relacionamento deve existir todas as instâncias
            - Para se referir a uma ocorrência de um relacionamento fala-se instância do relacionamento
                - Cada relacionamento é uma informação diferente
            - Grau de um relacionamento
                - Representa a quantidade de entidades envolvidas no relacionamento
                - Unário (auto-relacionamento), binário (duas entidades), N-ário (N entidades)
            - Papel de um relacionamento
                - Representa a função que uma dada entidade desempenhada no relacionamento
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%204.png)
                
            - Cardinalidade ou multiplicidade ou cardinalidade máxima de um relacionamento
                - Expressa o número máximo de vezes que uma instância de uma entidade, no pior caso, pode ter no relacionamento
                - Pode ser representada por qualquer número inteiro e positivo, por convenção utiliza-se 1 (um) e N (muitos)
                    - Pode ser 1:1, 1:N ou M:N
            - Participação ou obrigatoriedade ou cardinalidade mínima de um relacionamento
                - Especifica se uma instância, para ser cadastrada em uma entidade, deve estar relacionada com outra instância de alguma entidade do relacionamento
                - Quando a condição é exigida, diz-se que a participação é total ou que o relacionamento é obrigatório
                - Quando a condição não é exigida, diz-se que a participação é parcial ou que o relacionamento é opcional
                - Pode ser representada por qualquer número natural, mas por convenção usa-se os valores 0 (participação parcial) e 1 (participação total)
            - A cardinalidade e participação podem ser especificadas do lado da entidade origem (look-here) ou destino (look-across)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%205.png)
                
                - Look-Here
                    - A FK está na entidade origem da relação
                    - A entidade origem armazena a referência para a entidade destino
                    - Os dados relacionados estão na entidade origem
                    - Está relacionado com a participação
                        - “Esta entidade precisa participar do relacionamento?”
                - Look-Across
                    - Precisa olhar para a entidade destino da relação para encontrar os dados relacionados
                    - A FK está na entidade destino
                    - Está relacionado com a cardinalidade
                        - “Quantos da entidade destino se relacionam com a entidade origem?”
                - Notação de Elmasri & Navathe
                    - A participação é representada por linhas simples (participação parcial) ou duplas (participação total)
                    - É possível usar a notação (min, max) quando os valores mínimo (participação) e máximo (cardinalidade) forem diferente dos valores padrões (0 ou 1 e 1 ou N respectivamente)
                - Exemplos
                    - 1
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%206.png)
                        
                    - 2
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%207.png)
                        
                    - 3
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%208.png)
                        
                    - 4
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%209.png)
                        
            - Duas entidades podem ter mais de um relacionamento entre elas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2010.png)
                
    - Elipses: representam atributos
        - Atributos
            - Propriedades descritiva de uma entidade ou relacionamento
            - Tipos
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
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2011.png)
                
            - Entidades devem ter atributos, mas nem todo relacionamento precisa ter
                - A cardinalidade de relacionamentos afeta a inserção de atributos nos relacionamentos ou entidades
                - É comum inserir atributos em relacionamentos M:N mas não é comum inserir atributos em relacionamentos 1:1, 1:N ou N:1
                    - Em relacionamentos 1:N, é melhor colocar o atributo na entidade do lado N, ao invés no relacionamento
                - Se existe um ID, então é uma entidade, caso contrário pode ser um relacionamento
                    - Relacionamentos com atributos são tabelas, se possui muitos atributos vira uma entidade
            - Exemplos
                - 1
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2012.png)
                    
                - 2
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2013.png)
                    
                - 3
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2014.png)
                    
                - 4
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2015.png)
                    
                - 5
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2016.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2017.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2018.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2019.png)
                    
    - Linhas: ligam atributos a entidades ou entidades a relacionamentos
- Relaciomento Unário
    - Relacionamento que engloba apenas 1 entidade, na qual ela assume dois papéis diferentes
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2020.png)
        
- Relacionamento Identificador
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
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2021.png)
        
    - Exemplo
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2022.png)
        
        - Nesse caso, o atributo identificador das entidades fracas é a concatenação encadeada de atributos na entidade forte
        - Identificador de Agência = (numB,numA) e da Conta = (numB,numA,numC)
- Relacionamento N-ário
    - Se todas as vezes que um relacionamento ocorrer envolver as mesmas N entidades, então é um relacionamento N-ário
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2023.png)
        
    - Como descobrir a cardinalidade de uma entidade
        - É necessário considerar o pior caso possível e ter o seguinte formato: 1 instância de X e 1 instância de Y podem se relacionar com no máximo quantas instâncias de Z (1 ou N)?
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2024.png)
            
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2025.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2026.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2027.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2028.png)
            
    - Participação
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2029.png)
        
        - No esquema 1, nenhuma das 3 entidades é obrigada a participar do relacionamento “contrata”, ou seja, o cadastro de qualquer uma das 3 independe de outra entidade
        - No esquema 2, o cadastro de produto só acontece se ele estiver relacionado com cliente e com conta
            - Produto não existe sem o relaciomento de “contrata”, pois depende de cliente e conta
        - Nos dois esquemas, quando ocorre a relação este sempre envolverá um cliente, um produto e uma conta
    - Relacionamento N-ário vs relacionamento binário
        - Se todos os clientes de uma conta sempre têm os mesmos produtos, então tem-se um relacionamento binário entre conta e produto
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2030.png)
            
            - Apesar de cliente não estar diretamente relacionamento com produto, a partir de conta é possível saber todos os produtos de um cliente (transitividade)
        - Caso em um relacionamento ternário uma entidade possuir cardinalidade 1, então provavelmente existe uma outra relação escondida, que não é ternária
            - No caso, vão ser duas relações binárias
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2031.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2032.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2033.png)
                
                - Apesar de 1 cliente com 1 conta corrente poder fazer parte de apenas 1 agência, 1 cliente pode fazer parte de N agências, causando uma contradição, enquanto que 1 conta corrente pode fazer parte de apenas 1 agência, o que está logicamente correto
                    - A relação permite que uma mesma conta esteja atrelada a mais de uma agência
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2034.png)
                        
                    - Solução
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2035.png)
                        
            - Se a partir de uma instância de entidade A é possível determinar uma instância de entidade B, então essas entidades formam um relacionamento binário e não N-ário
        - Além disso, 3 relacionamentos binários não substituem 1 relacionamento ternário
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2036.png)
            
- Entidade associativa
    - Se um relacionamento pode acontecer sem a presença de uma terceira entidade, deve-se usar a entidade associativa para representar o cenário
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2037.png)
        
    - Exemplo
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2038.png)
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2039.png)
        
    - Entidade associativa vs relacionamento n-ário
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2040.png)
        
- Herança
    - Cria uma hierarquia de entidades, onde as sub-entidades herdam todos os atributos e relacionamentos das super-entidades
        - Recomendável usar apenas se as sub-entidades possuírem atributos ou relacionamentos específicos
    - Notação
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2041.png)
        
    - Tipos
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
    - Exemplos
        - Herança PD
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2042.png)
            
        - Herança TD
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2043.png)
            
        - Herança PO
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2044.png)
            
        - Herança TO
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2045.png)
            
    - Se existe apenas uma sub-entidade, a herança é direta
        - Não pode ser disjunta/sobreposta ou total/parcial
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2046.png)
            
    - Se as sub-entidades não têm atributos ou relacionamentos específicos, usar um atributo “tipo” no lugar da herança
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2047.png)
        
- Particularidades
    - Tem poder de expressão limitado, valores válidos e pré/pós condições devem ser informadas à parte
    - Esquemas ER diferentes podem ser equivalentes
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2048.png)
        
- Dúvidas frequentes
    - Modelar um conceito como atributo ou entidade
        - Se é meramente descritivo → atributo
        - Se tem identificador explícito → entidade
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2049.png)
        
    - Modelar um conceito que tem muitas propriedades como um atributo composto/multivalorado ou entidade
        - Se é exclusivo de uma entidade → atributo
        - Se pode ser compartilhado entre várias entidades → entidade
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2050.png)
        
    - Modelar conceitos como atributos ou usar herança
        - Se pode haver inconsistência entre os conceitos → herança
        - Caso contrário → atributo
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2051.png)
        
    - Modelar um conceito como relacionamento ou entidade
        - Se tem identificador explícito → entidade
        - Caso contrário → pode ser relacionamento
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2052.png)
        
    - Modelar um conceito com relacionamento n-ário ou entidade associativa
        - Se todas as vezes que o relacionamento ocorrer, sempre envolve todas as entidades participantes → relacionamento n-ário
        - Caso contrário → entidade associativa
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2053.png)
        
- Requisitos para um bom MER
    - Ser sintaticamente correto
        - O esquema deve respeitar regras sintáticas de construção
        - Exemplos de erros sintáticos
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2054.png)
            
    - Ser semanticamente correto
        - O esquema não pode ter atributos mal especificados
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2055.png)
            
        - O esquema não pode ter relacionamentos com cardinalidades mal especificadas
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2056.png)
            
        - O esquema não pode ter relacionamentos com participações mal especificadas
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2057.png)
            
        - O esquema não pode ter relacionamentos com grau mal especificados
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2058.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2059.png)
            
        - O esquema não pode capturar mais de uma realidade
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2060.png)
            
    - Evitar ou controlar construções redundantes
        - Construções redundantes podem melhorar o desempenho mas também podem gerar dados inconsistentes
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2061.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2062.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2063.png)
            
    - Capturar o aspecto temporal
        - Guardar o histórico de um atributo
        - Exemplos
            - 1
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2064.png)
                
            - 1:1
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2065.png)
                
            - 1:N
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2066.png)
                
            - M:N
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2067.png)
                
    - Ser completo
        - É mais fácil corrigir um erro no projeto conceitual do que em qualquer outra fase do projeto do banco de dados
        - O projeto conceitual do banco de dados pode ser feito a partir de:
            - Informações existentes
                - Estratégia de engenharia reversa: feita automaticamente por uma ferramenta CASE
                - Estratégia Bottom-Up: 1º atributos → 2º Entidades → 3º Relacionamentos → 4º Herança
            - Do conhecimento de especialistas
                - Estratégia Top-Down: 1º Entidades → 2º Relacionamentos → 3º Heranças → 4º Atributos
                - Estratégica Inside-Out: igual ao Top-Down, mas começa pelas entidades mais importantes

---

## Modelo Relacional

- É um módelo lógico, não tão abstrato como o conceitual mas não considera aspectos físicos de armazenamento, acesso e desempenho
- Base sólida formal (teoria dos conjuntos) e é baseado em conceitos simples (relações com atributos, tuplas e domínios)
    - Baseado em tabelas que não podem ter subtabelas
    - Diversos conceitos do modelo conceitual não são implementados de forma tão direta no modelo relacional
- Base para o SQL
- Definições
    - Domínio
        - Conjunto de valores atômicos
    - Relação
        - Dados os conjuntos D1, …, Dn (domínios não necessariamente distintos), R é uma relação nestes n conjuntos se esta for um conjunto de tuplas <v1, …, vn> onde v1 ∈ D1, …, vn ∈ Dn, formando um subconjunto do produto cartesiano D1 x … x Dn
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2068.png)
            
        - Terminologia (Relação x Tabela)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2069.png)
            
        - Propriedades
            - Toda relação tem um valor fixo de atributos distintos
            - O valor null é usado quando um atributo não tem valor ou este pe desconhecido
            - A ordem dos atributos e das tuplas é irrelevante, não há ordenação entre tuplas e os valores podem ser associados aos atributos independentemente de uma ordem
    - Chaves
        - Conceito usado para identificar e referenciar tuplas
        - Tipos
            - Chave candidata
                - É um atributo (chave simples) ou concatenação de atributos (chave composta) cujos valores distinguem uma tupla das demais tuplas de uma relação
                    - Uma possível chave primária, deve possuir valores distintos e obrigatórios
                - Deve ser mínima
                    - Caso ela seja simples, ela já é mínima
                    - Caso contrário, deve verificar inconsistências
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2070.png)
                        
            - Chave primária
                - É uma chave candidata escolhida para identificar uma tupla
                - É frequentemente utilizada para selecionar as tuplas de uma relação
                - Não admite valor null
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2071.png)
                
            - Chave estrangeira
                - Um atributo ou concatenção de atributos que faz referência a uma chave primária
                    - A chave estrangeira é a chave primária de outra tabela, mas é a primária da tabela dela
                    - Objetivo de linkar tabelas
                - É utilizada para relacionar tuplas de relações
                - Admite valor null (participação opcional)
                    - Não precisa ser única e obrigatória
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2072.png)
                
                - Auto-relacionamento: é uma relação entre a mesma entidade, diferenciando apenas nos papéis
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2073.png)
                    
            - Chave alternativa
                - É a chave candidata que não foi escolhida como chave primária
                    - Não faz relacionamento com chave estrangeira
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2074.png)
                
- Restrições
    - Restrições de integridade
        - Regras sobre os valores armazenados nas relações
        - Têm por objetivo garantir a consistência das relações
        - Restrições de domínio
            - Todo valor de um atributo deve ser atômico (simples e monovalorado) e pertencer ao domínio do atributo
        - Restrições de chave
            - Todo valor de chave primária deve ser mínimo e único na relação
        - Integridade da entidade
            - Chaves primárias não podem ter o valor null
        - Integridade referencial
            - Especifica que os valores de uma chave estrangeira devem aparecer na chave primária da tabela referenciada
        - Exemplo
            - Inserções e atualizações
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2075.png)
                
            - Exclusões
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2076.png)
                
    - Restrições semânticas
        - São restrições para impor regras de negócio
        - Devem ser implementadas pelos programadores pois não são automaticamente garantidas
        - Exemplo: um empregado não pode ter um salário maior que seu superior imediato
- Notação simplificada
    
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2077.png)
    
- Álgebra relacional
    - Desenvolvida para descrever operações sobre um BDR, ajudando a entender SQL (linguagens de consulta estruturada)
    - Compatibilidade de domínio
        - Duas relações A(a1, …, an) e B(b1, …, bn) são ditas compatíveis em domínio se ambas têm o mesmo grau n e se Dom(ai) = Dom(bi), tal que 1 ≤ i ≤ n
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2078.png)
            
    - Operações sobre conjuntos
        - União
            - Une as tuplas das relações A e B (A U B)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2079.png)
                
        - Interseção
            - Retorna as tuplas cujos valores sejam comuns à A e B (A ⋂ B)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2080.png)
                
        - Diferença
            - Retorna as tuplas de A cujos valores não estão em B (A - B)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2081.png)
                
        - Produto cartesiano
            - Combina todas as tuplas das relações A e B (A X B)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2082.png)
                
        - União exclusiva
            - Retorna todas as tuplas de A ou B que não estão em ambas (A U| B → A U B - A ⋂ B)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2083.png)
                
    - Operações relacionais unárias
        - Produzem como resultado uma nova relação que é um subconjunto (horizontal ou vertical) da relação origem
            - Subconjunto horizontal → muda as linhas
            - Subconjunto vertical → mudam as colunas
        - Seleção
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2084.png)
            
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2085.png)
                
        - Projeção
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2086.png)
            
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2087.png)
                
        - Seleção + Projeção
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2088.png)
            
    - Operações relacionais binárias
        - Produzem como resultado uma nova relação que é um subconjunto (seleção) do produto cartesiano das relações envolvidas
        - Em geral, após um produto cartesiano, é necessário comparar um grupo de atributos (compatíveis em domínio) para selecionar as tuplas do resultado final
        - Junção
            - Retorna apenas as tuplas do produto cartesiano de seus argumentos que satisfaçam uma dada condição
            - Sintaxe
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2089.png)
                
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2090.png)
                
        - Divisão
            - Produz uma relação R(X) com as tuplas de R1(A) que estão combinadas com todas as tuplas R2(B)
            - Sintaxe
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2091.png)
                
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2092.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2093.png)
                
- Mapeamento EER Relacional
    - O esquema EER pode gerar N esquemas Relacionais, existem várias maneiras de mapear relacionamentos e heranças
    - Prioridades no mapeamento
        1. Evitar junções → consultas mais rápidas
        2. Diminuir o número de chaves → índices menores e mais rápidos
        3. Evitar campos opcionais → menos testes de qualidade dos dados
    - Nomeação de relações e atributos
        - Usar nomes curtos
        - Eliminar espaços em branco e caracteres especiais
        - Adotar um padrão
    - Passos para fazer o mapeamento
        - Mapear as entidades regulares e seus atributos
            - Cada entidade regular é mapeada para uma relação
                - A PK da relação é o atributo identificador da entidade mapeada
            - Cada atributo multivalorado é mapeado para:
                - N atributos (desde de que N seja pequeno) ou
                - Uma relação cuja PK é o atributo multivalorado mais a PK da relação origem
                    - A PK que migrou da relação origem é FK
            - Atributos comum, composto ou derivado são mapeados para atributos da relação
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2094.png)
                
        - Mapear as entidades fracas e seus atributos
            - Cada entidade fraca é mapeada para uma relação
                - A PK que mapeia a entidade forte migra como FK
                - A PK da relação é formada pela FK mais o discriminador, caso exista
            - Atributos comum, composto, derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2095.png)
                
        - Mapear as super/subentidades e seus atributos
            - 4 alternativas
                - Uma relação para cada entidade da herança
                    - Características
                        - Características fortes
                            - Funciona bem para qualquer tipo de herança
                            - Reduz atributos opcionais
                            - Reduz testes para garantir a qualidade dos dados
                        - Características fracas
                            - Exige junções
                    - Mapeamento
                        - Cada super/subentidade é mapeada para uma relação
                            - A PK de cada relação é o atributo identificador da superentidade mapeada
                            - A PK de cada relação que mapeia uma subentidade será FK para a superentidade
                        - Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2096.png)
                        
                - Uma relação para cada subentidade da herança total
                    - Características
                        - Características fortes
                            - Reduz atributos opcionais
                            - Reduz testes para garantir a qualidade dos dados
                            - Reduz junções
                        - Características fracas
                            - Gera redudância de dados para heranças sobrepostas
                    - Mapeamento
                        - Cada subentidade é mapeada para uma relação
                            - A PK de cada relação é o atributo identificador da superentidade mapeada
                        - Os atributos e relacionamentos da superentidade migram para as relações que mapeiam as subentidades
                        - Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2097.png)
                        
                - Uma única relação para toda herança disjunta ou direta
                    - Características
                        - Características fortes
                            - Reduz junções
                        - Características fracas
                            - Só funciona com heranças definidas por um predicado/condição
                            - Exige atributos opcionais
                            - Exige testes para garantir a qualidade dos dados
                                - Testar o povoamento dos atributos e dos relacionamentos
                    - Mapeamento
                        - A superentidade e as subentidades de uma herança são mapeadas para uma única relação
                            - A PK da relação é o atributo identificador da superentidade mapeada
                        - O predicado/condição da herança torna-se um atributo da relação mapeada
                            - Seu domínio deve cobrir as subentidades
                        - Os atributos e relacionamentos das subentidades migram para a relação mapeada
                        - Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2098.png)
                        
                - Uma única relação para toda herança sobreposta
                    - Características
                        - Características fortes
                            - Reduz junções
                            - Reduz redundância de dados
                        - Características fracas
                            - Exige atributos opcionais
                                - Desaconselhada quando as subentidades têm muitos atributos ou relacionamentos
                            - Exige testes para garantir a qualidade dos dados
                                - Testar o povoamento dos atributos e dos relacionamentos
                    - Mapeamento
                        - A superentidade e as subentidades de uma herança são mapeadas para uma única relação
                            - A PK da relação é o atributo identificador da superentidade mapeada
                        - Para cada subentidade, criar na relação mapeada um atributo booleano
                        - Os atributos e relacionamentos da superentidade e das subentidades migram para a relação mapeada
                        - Atributos comum, composto derivado ou multivalorado seguem os mesmos mapeamentos das entidades regulares
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%2099.png)
                        
        - Mapear as entidades associativas
            - Cada entidade associativa é mapeada para uma relação
            - As PK das relações envolvidas migram como FK obrigatórias
            - Os atributos do relacionamento, caso existam, ficam na relação mapeada
            - A PK da relação depende do grau e da cardinalidade do relacionamento
                - Usar as mesmas regras aplicadas em relacionamentos
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20100.png)
                
        - Mapear os relacionamentos e seus atributos
            - Fusão de relações
                - Características
                    - Características fortes
                        - Reduz junções
                    - Características fracas
                        - Exige atributos opcionais
                            - Desaconselhada quando as subentidades têm muitos atributos ou relacionamentos
                        - Exige testes para garantir a qualidade dos dados
                            - Testar o povoamento dos atributos e dos relacionamentos
                - Mapeamento
                    - Melhor caso 1:1 - Total/Total
                        - Fundir as relações em uma única relação
                        - A PK da relação fundida deve ser uma das PK originais
                            - Dar preferência para a PK que poderá ser mais consultada
                        - Usar [] para definir a outra PK como chave alternativa (AK)
                        - Usar ! para definir a AK como obrigatória
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20101.png)
                            
                    - Caso alternativo 1:1 - Total/Parcial
                        - Fundir as relações em uma única relação
                        - A PK da relação fundida deve ser a PK da relação original que tem participação parcial
                            - Usar [] para definir a outra PK como AK
                        - Avaliar custo x benefício
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20102.png)
                            
            - Adição de chave estrangeira
                - Características
                    - Características fortes
                        - Reduz atributos opcionais
                        - Reduz testes para garantir a qualidade dos dados
                    - Características fracas
                        - Exige junção
                - Mapeamento
                    - Melhor caso 1:N
                        - A PK da relação do lado 1 migra como FK para a outra relação
                            - Caso o lado N seja total, usa ! para definir a FK como obrigatória
                        - Os atributos do relacionamento, caso existam, migram com a PK
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20103.png)
                            
                    - Caso alternativo 1:1
                        - Parcial/Parcial
                            - A PK de qualquer uma das relações migra como FK única e opcional (usar [] para definir a FK como única)
                        - Total/Parcial
                            - A PK da relação do lado parcial migra como FK única e obrigatória (usar [] + ! para definir a FK como única e obrigatória)
                        - Total/Total
                            - A PK de qualquer uma das relações migra como FK única e obrigatória (usar [] + ! para definir a FK como única e obrigatória)
                        - Os atributos do relacionamento, caso existam, migram com a PK
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20104.png)
                            
            - Criação de relação
                - Características
                    - Características fortes
                        - Reduz atributos opcionais
                        - Reduz testes para garantir a qualidade dos dados
                    - Características fracas
                        - Exige junção
                - Mapeamento
                    - Melhor caso M:N
                        - Cada relacionamento M:N é mapeado para uma relação
                        - As PK das relações envolvidas migram como FK
                        - As composições das FK forma a PK da relação
                        - Os atributos do relacionamento, caso existam, ficam na relação mapeada
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20105.png)
                            
                    - Caso alternativo 1:N - evitar
                        - O relacionamento 1:N é mapeado para uma relação
                        - As PK das relações envolvidas migram como FK
                        - A FK do lado N torna-se PK
                        - A outra FK torna-se obrigatória (usar ! para definir a FK como obrigatória)
                        - Os atributos do relacionamento, caso existam, ficam na relação mapeada
                    - Caso alternativo 1:1 - evitar
                        - O relacionamento 1:1 é mapeado para uma relação
                        - As PK das relações envolvidas migram como FK
                        - A PK é definida a partir das participações do relacionamento
                            - Parcial/Parcial → a PK pode ser qualquer uma das FK
                            - Total/Parcial → a PK é a FK do lado parcial
                            - Total/Total → a PK pode ser qualquer uma das FK
                        - A outra FK torna-se única (AK) e obrigatória (usar [] + ! para definir a FK como única e obrigatória)
                        - Os atributos do relacionamento, caso existam, ficam na relação mapeada
                    - Relacionamentos N-ários
                        - Cada relacionamento n-ário é mapeado para uma relação
                        - As PK das relações envolvidas migram como FK obrigatórias (usar ! para definir a FK como única e obrigatória)
                        - Os atributos do relacionamento, caso existam, ficam na relação mapeada
                        - A PK da relação depende da cardinalidade do relacionamento
                            - N:N:N → PK formada por todas as FK
                            - 1:N:N → PK dupla formada pelas FK do lado N
                            - 1:1:N → caso raro e complexo
                            - 1:1:1 → caso raro e complexo
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20106.png)
                            
    - Exemplo
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20107.png)
        
        - Mapeando entidades
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20108.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20109.png)
            
        - Mapeando herança
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20110.png)
            
        - Mapeando entidade associativa
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20111.png)
            
        - Mapeando relacionamento 1:1
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20112.png)
            
        - Mapeando relacionamento 1:N
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20113.png)
            
        - Mapeando relacionamento M:N
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20114.png)
            
        - Mapeando relacionamento N-ário
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20115.png)
            
- Normalização
    - Processo matemático fundamentado na teoria dos conjuntos, aplicando uma série de regras sobre as tabelas de um BD para verificar se estas foram bem projetadas
    - Objetivos
        - Decompor uma relação até que esta fique com pouca ou nenhuma redundância de dados
        - Impedir anomalias de inserção, atualização e exclusão
        - Permitir representar eficientemente os dados no mundo real, tornando o modelo mais estável e fácil de manter
        - Pode ser usada para validar o modelo relacional gerado pelas transformações vistas anteriormente e também gerar modelos relacionais a partir de documentos da organização
    - Do ponto de vista prático e de desempenho, sua aplicação nem sempre é ideal
    - Aplicar a normalização até a 3FN ou FNBC
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20116.png)
        
    - Definições
        - Dependência Funcional (DF)
            - Quando um conjunto de atributos A1 identifica um conjunto de atributos A2, diz-se que há uma dependência funcional entre A1 e A2, onde A1 é o determinante e A2 é o dependente
            - Representação
                - A1 → A2 (lê-se: determina A2 ou A2 é dependente de A1)
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20117.png)
                
        - Dependência Funcional Parcial (DFP)
            - Ocorre quando um conjunto de atributos dependem apenas de parte de um determinado composto
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20118.png)
                
        - Dependência Funcional Total (DFT)
            - Ocorre quando um conjunto de atributos depende de todo determinado composto
        - Dependência Funcional Transitiva (DF Transitiva)
            - Dada uma relação qualquer, diz-se que existe DF Transitiva quando um conjunto de atributos A3 depende de um atributo A2, que não é PK, mas que A2 depende funcionalmente da PK A1
            - Ou seja, considerando que A1 é PK, mas A2 não é, se A1 → A2 e A2 → A3, então diz-se que A3 depende transitivamente de A1, através de A2
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20119.png)
                
    - Formas Normais
        - 1ª Forma Normal (1FN)
            - Uma relação está na 1FN quando os domínios de todos os seus atributos são atômicos
            - Ou seja, a relação não pode mapear atributos compostos ou multivalorados
            - Transformação
                - Atributo composto
                    - Decompor o atributo cmposto em atributos simples e colocá-los na mesma relação ou em uma nova relação
                    - Quando o atributo composto é monovalorado, colocar na mesma relação
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20120.png)
                        
                    - Quando o atributo composto é multivalorado, colocar em uma nova relação
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20121.png)
                        
                - Atributo multivalorado
                    - Decompor o atributo multivalorado em atributos simples e colocá-los na mesma relação ou em uma nova relação
                    - Quando a quantidade de valores é pequena e conhecida a priori, colocar na mesma relação
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20122.png)
                        
                    - Quando a multivaloração é desconhecida ou grande, colocar em uma nova relação
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20123.png)
                        
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20124.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20125.png)
                
        - 2ª Forma Normal (2FN)
            - Uma relação está na 2FN quando ela está na 1FN, a PK é composta e todas as colunas que não participam da PK são dependentes de todas as colunas que compõem a PK, isto é, não existe DFP
            - Transformação
                - Retirar os atributos com DFP da relação original
                    - A partir destes atributos retirados, cria-se uma ou mais relações compostas pela parte da PK e seus atributos dependentes
                    - A parte da PK que gerou dependência será a nova PK da tabela criada
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20126.png)
                    
            - Exemplo (DFP)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20127.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20128.png)
                
        - 3ª Forma Normal (3FN)
            - Uma relação está na 3FN quando ela está na 2FN e quando todos os atributos que não participam da PK são exclusivamente dependentes desta, isto é, a relação não contém DF Transitiva
            - Na maioria das vezes a normalização até a 3FN é suficiente, mas na literatura aparecem outras formas normais
            - Transformação
                - Retirar os atributos com DF Transitiva da relação original
                    - A partir destes atributos retirados, cria-se uma ou mais relações compostas pelo atributo determinante (como PK) mais as suas colunas dependentes
                        - Verifica-se a 2FN para cada nova tabela
                    - Além de não conter DF Transitiva, as relações 3FN não devem possuir atributos com valores calculados ou derivados
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20129.png)
                    
            - Exemplo (DF Transitiva)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20130.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20131.png)
                
        - Forma Normal BOYCE/CODD (FNBC)
            - É um refinamento da 3FN, usada em casos particulares
            - Uma relação está na FNBC quando todos os determinantes da relação devem ser chaves candidatas/alternativas
            - Transformação
                - Decompor a relação original em duas ou mais relações, separando os atributos que depende do atributo que não é chave candidata (ou seja, um atributo que é determinante da relação)
                    - O determinante que não é chave candidata/alternativa na relação original deve fazer parte da PK das novas relações
                    - Verifica-se a 3FN para cada nova relação
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20132.png)
                    
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20133.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20134.png)
                

---

## SQL

- Ferramenta de programação usada para os bancos de dados
- Tipos de comandos
    - Data Definition Language (DDL)
        - Permite a criação, manutenção e eliminação de objetos do banco de dados, como tabelas, índices, sequências e views
        - Convenção de nomes
            - Devem começar com uma letra
            - Pode ter de 1 a 30 caracteres
            - Pode conter somente A-Z, a-z, 0-9, _, $ e #
            - Os nomes devem ser únicos por usuário
            - Não podem ser utilizadas palavras reservadas (salvo se entre aspas)
        - Chaves naturais só devem ser usadas quando forem pequenas e raramente sofrerem atualizações
            - Atualizações na PK impactam nos índices e nas FKs
            - É preferível chaves artificiais se a chave natural for grande ou passível de atualização (ex: auto incremento)
        - Tipos de Dados
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20135.png)
            
        - Restrições
            - Restrição de integridade de tabelas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20136.png)
                
            - Restrição de integridade de colunas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20137.png)
                
            - Restrições de integridade referencial
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20138.png)
                
        - Estudo de Caso
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20139.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20140.png)
            
            - Restrições
                - CONSTRAINT PK_USUARIOS PRIMARY KEY (CPF) → define CPF como a PK de PESQUISADOR
                - CONSTRAINT AK_USU_CPF UNIQUE (NOME, NASCIMENTO) → cria uma AK ou restrição única, garante que não exista duas pessoas com o mesmo nome e mesma data de nascimento cadastradas
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20141.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20142.png)
            
            - CONSTRAINT PK_ARTIGO PRIMARY KEY (MAT) → define MAT como PK de ARTIGO
            - CONSTRAINT FK_ART_EVE FOREIGN KEY (COD) REFERENCES EVENTO (COD) → define COD como uma FK, garantindo o link entre EVENTO e ARTIGO (presente na relação de publica)
            - CONSTRAINT CHK_ART_NOTA CHECK (NOTA BETWEEN 0 AND 10) → regra de checagem que força que o valor de nota esteja sempre entre 0 e 10
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20143.png)
            
            - CONSTRAINT ESCREVE_PK PRIMARY KEY (CPF, MAT) → define a PK como composta, fazendo com que a combinação entre CPF e MAT seja única
            - CONSTRAINT ESCREVEPESQUISADOR_FK FOREIGN KEY (CPF) REFERENCES PESQUISADOR ON DELETE CASCADE → cria a FK que aponta para CPF na tabela de PESQUISADOR, além disso, caso algum pesquisador for deletado na tabela de ESCREVE, ele também será deletado na tabela de PESQUISADOR
            - CONSTRAINT ESCREVEARTIGO_FK FOREIGN KEY (MAT) REFERENCES ARTIGO ON DELETE CASCADE → cria a FK que aponta para MAT na tabela de ARTIGO, além disso, caso algum pesquisador for deletado na tabela de ESCREVE, ele também será deletado na tabela de ARTIGO
        - Comandos
            - Criar tabelas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20144.png)
                
            - Alterar tabelas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20145.png)
                
            - Excluindo ou limpando uma tabela
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20146.png)
                
            - Criando e excluindo índices
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20147.png)
                
                - Criar índices quando a tabela tem muitas linhas, a coluna contém inúmeros valores distintos, a coluna é muito usada para fazer filtros e a coluna sofre pouca atualização
                - Não criar indíces quando a tabela é pequena, a coluna contém muitos valores repetidos, a coluna dificilmente é usada para fazer fazer filtros e quando sofre atualização frequente
            - Criando e excluindo sequências
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20148.png)
                
            - Criando e excluindo views
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20149.png)
                
            - Criando e excluindo papéis/usuários
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20150.png)
                
    - Data Query Language (DQL)
        - Comandos
            - SELECT: seleciona dados, * é para selecionar todos os dados de determinada tabela.
                - A seleção pode vir por meio do schema, como: SELECT * FROM public.database ao invés de SELECT * FROM database
                - Pode vir em conjunto de funções de agregação
            - FROM: especifica de qual tabela os dados serão selecionados.
            - WHERE: funciona como uma filtragem em uma consulta de tabela.
            - ORDER BY: ordena os resultados
                - ASC para ordenar de forma ascendente
                - DESC para ordenar de forma descendente
                - Pode possuir mais de uma ordenação, tem mais prioridade a ordenação mais a esquerda
                - Exemplo
                    
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
                    
            - GROUP BY: agrupar registros
                - Ao usar, precisa se certificar de que todas as colunas não agregadas na cláusula de SELECT estão no GROUP BY
            - HAVING: filtrar os resultados de grupos de linhas após a aplicação de funções de agregação
                - Difere do WHERE pois o WHERE filtra antes do agrupamento, já o HAVING filtra depois
            - PARTITION BY: divide o conjunto de resultados em partições ou grupos, peça central das Window Functions
                - Window Functions
                    - É usada para realizar cálculos em conjunto de linhas relacionadas ao registro atual dentro uma janela definida
                    - Essas funções permitem agregar, classificar ou manipular dados sem colapsar as linhas em um único valor
                    - As window functions podem ser usadas fora de cláusulas PARTITION BY
                    1. Não reduz as linhas do resultado
                    2. Definem uma janela (escopo)
                        - Definida por cláusulas como PARTITION BY e GROUP BY
                    - Sintaxe geral
                        
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
                        
                    - Funções
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
                                - Fórmula: CUME_DIST = (Número de linhas com valores <= linha atual) / (Número total de linhas)
                        - VALUE
                            - LAG(): permite acessar o valor da linha anterior dentro de um conjunto de resultados. Isso é particularmente útil para fazer comparações com a linha atual ou identificar tendências ao longo do tempo
                            - LEAD(): permite acessar o valor da próxima linha dentro de um conjunto de resultados, possibilitando comparações com a linha subsequente
                            - FIRST_VALUE(): retorna o primeiro valor de uma coluna ou expressão
                            - LAST_VALUE(): retorna o último valor de uma coluna ou expressão
                            - NTH_VALUE(): retorna o valor N de uma coluna ou expressão
            - LIMIT: limita a quantidade de linhas da query
            - OFFSET: especifica a partir de qual linha a query deve começar
        - Esqueleto
            
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
            
        - Ordem
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20151.png)
            
    - Data Manipulation Language (DML)
        - Comandos
            - Inserção
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20152.png)
                
            - Atualização
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20153.png)
                
            - Remoção
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20154.png)
                
            - Funções de manipulação de string
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20155.png)
                
            - Funções de manipulação de números
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20156.png)
                
            - Exemplos
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20157.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20158.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20159.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20160.png)
                
        - Joins
            - Servem para combinar dados de duas tabelas em uma única consulta com base em colunas comuns entre essas duas tabelas
                - Tabela de junções
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20161.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20162.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20163.png)
                    
                - Se não especificar o tipo de JOIN, o padrão vai ser o INNER
                - OUTER: serve para descrever explicitamente joins externos
                    - Esses joins externos incluem os registros de uma tabela mesmo quando não há correspondência na outra tabela, preenchendo os valores ausentes com NULL.
                - ON: definir a condição de junção
            - Tipos
                - INNER JOIN: utilizado quando você precisa de registros que têm correspondência exata em ambas as tabelas
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        INNER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
                        ```
                        
                - LEFT JOIN (ou LEFT OUTER JOIN): usado quando quer todos os registros da primeira (esquerda) tabela, com os correspondentes da segunda (direita) tabela. Se não houver correspondência, a segunda tabela terá campos NULL
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        LEFT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
                        ```
                        
                - RIGHT JOIN (ou RIGHT OUTER JOIN): é o inverso do Left Join e é menos comum. Usado quando queremos todos os registros da segunda (direita) tabela e os correspondentes da primeira (esquerda) tabela
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        RIGHT JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
                        ```
                        
                - FULL OUTER JOIN: utilizado quando queremos a união de Left Join e Right Join, mostrando todos os registros de ambas as tabelas, e preenchendo com NULL onde não há correspondência
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        FULL OUTER JOIN tabela2 ON tabela1.coluna_comum = tabela2.coluna_comum;
                        ```
                        
                - CROSS JOIN: retorna o **produto cartesiano** das tabelas, combinando cada registro da tabela à esquerda com todos os registros da tabela à direita, não precisando de uma condição ON
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        CROSS JOIN tabela2;
                        ```
                        
                - NATURAL JOIN: realiza o join automaticamente com base nas colunas de mesmo nome em ambas as tabelas, não exige especificação explícita das condições de join
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        NATURAL JOIN tabela2;
                        ```
                        
                - SELF JOIN: é um join de uma tabela com ela mesma, geralmente usado para comparar registros dentro da mesma tabela
                    - Sintaxe
                        
                        ```sql
                        SELECT a.coluna1, b.coluna2
                        FROM tabela a
                        INNER JOIN tabela b ON a.coluna_comum = b.coluna_comum;
                        ```
                        
                - LATERAL JOIN: usado para unir tabelas com subconsultas que dependem de cada linha da tabela principal. É útil quando a subconsulta precisa de informações da linha atual
                    - Sintaxe
                        
                        ```sql
                        SELECT coluna1, coluna2
                        FROM tabela1
                        JOIN LATERAL (subconsulta) AS alias ON condição;
                        ```
                        
            - Exemplos
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20164.png)
                
                - A consulta não está errada, mas não é boa prática pois mistura as tabelas sem cláusulas JOIN
                    
                    ```sql
                    SELECT A.TITULO, E.SIGLA
                    FROM ARTIGO A
                    JOIN EVENTO E ON A.TITULO = E.SIGLA;
                    ```
                    
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20165.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20166.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20167.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20168.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20169.png)
                
        - Subconsultas
            - Consiste de um comando que fica dentro de outro comando principal, facilitando a resolução de problemas mais complexos
                - Identificada pelo uso de SELECT
            - As subconsultas são categorizadas quanto a quantidade de linhas e colunas retornadas, bem como quanto a dependências entre as subconsultas
                - Quantidade de linhas e colunas retornadas
                    - Escalar → retorna um único valor (uma única linha e coluna)
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20170.png)
                        
                    - Linha → retornam várias colunas, mas apenas uma linha
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20171.png)
                        
                    - Tabela → retornam uma ou mais colunas e múltiplas linhas
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20172.png)
                        
                - Dependências entre as subconsultas
                    - Simples → a subconsulta pode ser executada de forma independente, sem precisar de um valor obtido apenas pela consulta principal
                    - Correlacionada → a subconsulta possui uma dependência com a consulta principal, precisando de algum valor obtido apenas dela
                        - SEMI JOIN → um semi join entre a tabela A e a tabela B retorna as linhas da tabela A para as quais existe pelo menos uma correspondência na tabela B
                            - Feita principalmente pelo EXISTS (mais performático, pois usa índice), mas também pode ser feito pelo IN
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20173.png)
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20174.png)
                            
                        - ANTI JOIN (ou ANTI SEMI JOIN, negação do SEMI JOIN) → oposto do semi join, retornando as linhas da tabela A para as quais não existe nenhuma correspondência na tabela B
                            - Feito através do NOT EXISTS (mais perfomático, pois usa índice), mas também pode ser feito pelo NOT IN
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20175.png)
                            
                            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20176.png)
                            
                - Exemplos
                    - Subconsulta simples e escalar no SELECT/WHERE
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20177.png)
                        
                    - Subconsulta simples e tabela no FROM
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20178.png)
                        
                    - Subconsulta simples e tabela no HAVING
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20179.png)
                        
                    - Avaliação condicional
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20180.png)
                        
        - Set Operators
            - UNION → união de dois conjuntos removendo as duplicatas
                - UNION ALL → união de dois conjuntos mantendo as duplicatas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20181.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20182.png)
                
            - INTERSECT → faz a interseção entre dois conjuntos, retornando apenas as linhas que existem em ambos os resultados das consultas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20183.png)
                
            - EXCEPT → retorna as linhas da primeira consulta que não existem na segunda consulta
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20184.png)
                
            - União Exclusiva (ou complemento) → retorna as linhas que estão na primeira ou na segunda consulta, mas não em ambas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20185.png)
                
            - Divisão relacional → dada duas tabelas, retorna uma nova relação contendo as tuplas da primeira tabela que estão associadas a tuplas da segunda tabela
                - Projetada para responder uma pergunta do tipo: Quais X estão associados a TODOS os Y de determinado conjunto
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20186.png)
                
    - Data Control Language (DCL)
        - Serve para gerenciar as permissões e o acesso dos usuários ao banco de dados
        - GRANT → conceder privilégios ou permissões a um usuário ou a um grupo de usuários
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20187.png)
            
        - REVOKE → remove os privilégios e permissões
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20188.png)
            
        - DENY (ausente no Oracle) → cria uma proibição explícita, se sobressaindo a um GRANT
    - Transaction Control Language (TCL)
        - Gerenciar transações em um banco de dados
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20189.png)
            
            - Propriedades ACID
                - Atomicidade → todas as operações de uma transação devem ser efetivadas, ou, na ocorrência de uma falha, nada deve ser efetivado
                - Consistência → transações preservam a consistência da base, garantindo que a transação leve o banco de dados de um estado válido para outro estado válido
                - Isolamento → a maneira como várias transações em paralelo interagem deve ser bem definido, garantindo que transações concorrentes não interfiram umas as outras
                - Durabilidade → uma vez consolidada a transação, suas alterações permanecem no banco até que outras transações aconteçam
        - START TRANSACTION/BEGIN TRANSACTION → marca o início de uma transação
        - COMMIT → comando para salvar permanentemente todas as alterações realizadas desde o início da transação
        - ROLLBACK → comando para descartar as alterações feitas desde o início da transação
        - SAVEPOINT → cria um marcador dentro de uma transação longa
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20190.png)
            

---

## PL/SQL

- É uma linguagem procedural da Oracle, estendendo a SQL-DML com comandos que permitem a criação de blocos de procedimentos de programação
    - Não aceita SQL-DDL
- Estrutura básica
    
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20191.png)
    
    - Tipo de bloco
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20192.png)
        
    - Tipos de identificadores
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20193.png)
        
        - Tipo Primitivo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20194.png)
            
            - Exemplos
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20195.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20196.png)
                
        - Tipo Registro
            - Semelhante a uma estrutura de dados
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20197.png)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20198.png)
                
        - Tipo Tabela
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20199.png)
            
            - Manipulando uma coleção do tipo tabela
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20200.png)
                
    - Operadores
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20201.png)
        
- Estrutura de aninhamento
    
    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20202.png)
    
- Consultas
    - SELECT
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20203.png)
        
    - INSERT
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20204.png)
        
    - UPDATE
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20205.png)
        
    - DELETE
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20206.png)
        
- Fluxos
    - IF
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20207.png)
        
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20208.png)
            
            - Não esquecer de inicializar as variáveis no DECLARE
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20209.png)
                
    - CASE
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20210.png)
        
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20211.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20212.png)
            
    - LOOP
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20213.png)
        
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20214.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20215.png)
            
    - WHILE
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20216.png)
        
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20217.png)
            
    - FOR
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20218.png)
        
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20219.png)
            
    - CURSOR
        - Semelhante a um ponteiro para manipular linhas de uma tabela temporária
        - Tipos
            - Implícito: declarado e gerenciado pelo servidor Oracle para todo comando DML e PL/SQL SELECT
            - Explícito: declarado e gerenciado pelo programador, gerado apenas pelo SELECT
        - Fluxo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20220.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20221.png)
            
        - Sintaxe
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20222.png)
            
            - Abrindo um cursor
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20223.png)
                
            - Lendo um cursor
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20224.png)
                
                - Usando LOOP/EXIT
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20225.png)
                    
                - Usando WHILE
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20226.png)
                    
            - Fechando um cursor
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20227.png)
                
            - Tipo registro
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20228.png)
                
            - Cursor com laços FOR
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20229.png)
                
                - Cursor com laços FOR sem declaração
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20230.png)
                    
            - Cursor com parâmetros
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20231.png)
                
    - Exceções
        - Fluxo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20232.png)
            
        - Tratamento
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20233.png)
            
            - Exceções predefinidas
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20234.png)
                
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20235.png)
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20236.png)
                    
            - Exceções criadas
                - Criação
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20237.png)
                    
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20238.png)
                    
- Subprogramas
    - Bloco de código nomeado (não usar DECLARE), podendo ser PROCEDURE (por padrão não retornam valor) ou FUNCTION (por padrão, necessariamente, retornam valor)
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20239.png)
        
    - Sintaxe
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20240.png)
        
        - Exemplo procedimento
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20241.png)
            
        - Exemplo função
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20242.png)
            
    - Chamando subprogramas
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20243.png)
        
    - Subprogramas parametrizados
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20244.png)
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20245.png)
        
        - Modos de passagem de parâmetro
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20246.png)
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20247.png)
            
    - Excluindo subprogramas
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20248.png)
        
    - Organizando subprogramas
        - Pacote: estrutura que agrupa logicamente subprogramas, tipos de dados, variáveis e etc. encapsulando-os em um único objeto do banco de dados
        - Os subprogramas devem ser especificados de forma que um subprograma ao ser “chamado” já tenha sido especificado antes
        - Formado pela Especificação (público) e Corpo (Privado)
        - Sintaxe
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20249.png)
            
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20250.png)
            
        - Chamando pacotes
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20251.png)
            
        - Removendo pacotes
            
            ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20252.png)
            
- Triggers
    - São códigos de PL/SQL armazenados no SGBD, associados a um objeto do BD
    - São executados implicitamente pelo SGBD na ocorrência de um determinado evento ou combinação deles
    - Podem ser usados para registrar modificações, garantir regras de negócio, gerar valor de coluna e manter tabelas duplicadas
    - Recomenda-se não ultrapassar 60 linhas, caso contrário chamar subprogramas
    - Não tem como definir a ordem de execução entre triggers
    - Não usar para refazer ações pré-existentes no SGBD
    - Sintaxe
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20253.png)
        
    - Componentes
        - Momento
            - Corresponde ao tempo (BEFORE, AFTER ou INSTEAD OF) em que o trigger deve ser executado
        - Evento
            - DBA (Database Administrator): CREATE, ALTER, DROP, SERVERERROR, LOGON, LOGOFF, STARTUP, SHUTDOWN, GRANT e REVOKE
            - DML (INSERT, DELETE e UPDATE)
        - Exemplos
            - Momento/Evento - DML
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20254.png)
                
                - Evento - DML
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20255.png)
                    
            - Momento/Evento - VIEW (INSTEAD OF)
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20256.png)
                
                - Evento - VIEW
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20257.png)
                    
        - Tipo
            - Só aplicável a eventos DML
            - Comando
                - Acionado antes ou depois de um comando, independente deste atualizar ou não uma ou mais linhas
                - Não permite acesso as linhas atualizadas
                - Sintaticamente, basta não usar “FOR EACH ROW”
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20258.png)
                    
            - Linha
                - Adicionado para cada linha afetada
                - UPDATE requer a definição do campo (UDATE OF campo)
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20259.png)
                    
                    - Com cláusula WHEN
                        
                        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20260.png)
                        
        - Ação
            - Bloco PL/SQL associado ao evento
            - Requer a definição de predicados lógicos quando o trigger tem mais de um evento DML
                - INSERTING: quando o trigger foi disparado por um INSERT
                - UPDATING: quando o trigger foi disparado por um UPDATE
                - DELETING: quando o trigger foi disparado por um DELETE
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20261.png)
                
                - Impedindo um comando DML
                    
                    ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20262.png)
                    
    - Remoção de triggers
        
        ![image.png](../../assets/faculdade/periodo4/banco-de-dados/image%20263.png)