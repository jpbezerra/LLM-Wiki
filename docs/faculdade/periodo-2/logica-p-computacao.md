# LÓGICA P/ COMPUTAÇÃO

---

## Lógica Aristotélica

- O que é lógica?
    - É o estudo do raciocínio
    - Comportamento lógico
        - Sair num dia de chuva com o guarda-chuva aberto
    - Comportamento ilógico
        - Sair num dia de chuva segurando um guarda-chuva fechado
    - Explicação lógica
        - Luiza parou no restaurante porque estava com fome
    - Explicação ilógica
        - Luiza parou no restaurante porque estava doente
    - Silogismo
        - Inferência onde uma proposição (conclusão) segue de duas outras (premissas)
        - Exemplos
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%201.png)
            
        - Sentenças
            - São proposições ou enunciados que podem ser verdadeiras ou falsas, por isso perguntas, ordens e exclamações não são proposições já que não assumem valores de verdadeiro ou falso
            - Tipos
                - Objetos a categorias
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%202.png)
                    
                - Categorias a categorias
                    - Universal
                        - Positiva
                            - Todo P é Q
                        - Negativa
                            - Nenhum P é Q
                    - Existencial
                        - Positiva
                            - Algum P é Q
                        - Negativa
                            - Algum P não é Q
        - Contradição
            
            Quando combinações de sentenças declarativas levam à um absurdo ou impossibilidade lógica
            
            - Tipo 1
                - São triviais
                - Exemplo
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%203.png)
                    
            - Tipo 2
                - Para identificar as situações contraditórias do tipo 2, utilizamos o quadrado de oposições
                - Quadrado de oposições
                    - A - Todo A é B
                    - E - Nenhum A é B
                    - I - Algum A é B
                    - O - Algum A não é B
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%204.png)
                    
                    - Situações
                        - Contraditórias
                            - Quando uma é V a outra é F
                            - Exemplo
                                - Todo homem é Vegano
                                - Algum homem não é Vegano
                        - Contrárias
                            - Podem ser ambas falsas, mas não ambas verdadeiras
                            - Exemplo
                                - Todo homem é atleta
                                - Nenhum homem é atleta
                        - Subcontrárias
                            - Podem ser ambas verdadeiras, mas não ambas falsas
                            - Exemplo
                                - Algum homem é atleta
                                - Algum homem não é atleta
                        - Subalternas
                            - Uma afirmação universal implica em uma particular
                            - Exemplo
                                - Todo homem é mortal
                                - Algum homem é mortal
                                
                                - Nenhum homem é mortal
                                - Algum homem não é mortal
        - Ato de inferência (Figura de inferência)
            - O ato de tirar uma conclusão a partir de um conjunto de sentenças (premissas)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%205.png)
                
            - Validade do ato de inferência
                - Válido (Logicamente seguro)
                    - Quando para todas as situações na qual as premissas são verdadeiras, a conclusão é obrigatoriamente verdadeira
                    - Se um ato de inferência possui premissas falsas ou contraditórias, é dito que o ato de inferência é válido por vacuidade
                    - Um ato de inferência válido é chamado de silogismo
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%206.png)
                        
                        - O ato de inferência é válido e a conclusão é verdadeira
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%207.png)
                        
                        - O ato de inferência é válido mas possui conclusão não verdadeira (está logicamente certa mas não é verdade no mundo não-lógico)
                - Inválido
                    - Quando existe uma situação na qual as premissas são verdadeiras mas a conclusão é falsa
                    - Exemplo
                        - Todo homem é mortal (premissa 1)
                        - Sócrates é mortal (premissa 2)
                        - Logo, Sócrates é homem (conclusão)
                        - O ato de inferência acima é inválido pois Sócrates pode não ser necessariamente um homem, mas pode ser um cachorro por exemplo
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%208.png)
                        
                        - Ato de inferência inválido pois não é porque eu não possuo todo o ouro do mundo que eu não sou rico, conclusão falsa
                - Quando as premissas não são ou não podem ser todas verdadeiras é dito que o ato de inferência é válido por vacuidade
        - Argumento
            - É uma coleção de atos de inferência
            - Validade dos argumentos
                - Válido
                    - Um argumento é válido se todos os seus atos também são válidos
                    - Se um ato de inferência de um argumento é válido por vacuidade, é dito que o argumento também é válido por vacuidade
                - Inválido
                    - Um argumento é inválido se algum dos seus atos é inválido
        - O uso de Diagrama de Venn para analisar os enunciados e atos de inferência
            - Exemplos
                - 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%209.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/cb623669-c75b-4d1c-8699-b85946f84419.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/cbc75a60-98a0-4814-add1-94cca88d9f4d.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/ce407048-6eae-4565-9912-764d1712e3f2.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/bfcd1549-a0a9-43b1-ad85-22b08267ec55.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/785399aa-ad17-4e14-b0a1-20ea3e578f04.png)
                    
                    - Vemos que o ato de inferência é válido
                - 2
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2010.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/14818dc2-9b16-4cb7-b6d9-67dec568cf94.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/204a6ca2-f315-4459-b1c0-f1a95ed26a8d.png)
                    
                    - Como existe um caso em que as premissas são verdadeiras mas a conclusão não é, então este ato de inferência não é válido
                - 3
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2011.png)
                    
                    - O ato de inferência é válido
                - 4
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2012.png)
                    
                    - O ato de inferência não é válido
        - Conjunto inconsistente de sistemas
            - Seja C um conjunto de sentenças (ato de inferência), dizemos que C é inconsistente se é possível inferir de modo seguro (válido) uma sentença S de algum subconjunto de C e uma sentença contraditória a S (¬S) de um outro subconjunto de C
                - Caso contrário, C é consistente (não possui contradições. ou seja, que existe pelo menos uma situação em que é verdade)
            - Nesse caso, dizemos que C contem uma contradição implícita
                - Exemplos
                    - 1
                        - C = {”Todo humano é mortal”, “Nenhum anjo é mortal”, “Gabriel é um anjo”, “Gabriel é humano”}; contradição implícita
                    - 2
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2013.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2014.png)
                        
                    - 3
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2015.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2016.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2017.png)
                        
                        - Logo, a inferência é inválida
                - C também é inconsistente se houver uma contradição explícita
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2018.png)
                        
            - Exemplo
                - Determine e justifique se o seguinte conjunto de sentenças é consistente
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2019.png)
                
                - O conjunto de sentenças é consistente pois existe um caso em que x é B, logo, que é verdade:
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2020.png)
                    
        - Paradoxos
            - Paradoxo do Barbeiro
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2021.png)
                
                - Se o barbeiro for barbeado por ele mesmo, há uma contradição pois o barbeiro só barbeia os homens que não se barbeiam
                - Se o barbeiro for barbeado pelo barbeiro (que passa a ser ele mesmo) então quer dizer que ele não se barbeia; mas se ele não se barbeia então ele deve se barbear
            - Paradoxo de Russel
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2022.png)
                

---

## Lógica Simbólica de Boole e Frege

- Álgebra booleana
    - Representação de sentenças através de números 0 (False) e 1 (True)
    - Operadores lógicos (and, nand, or, nor, xor, xnor, not, if then)
    - Operações de teoria de conjuntos (produto, soma e complemento)
- Lógica simbólica de Frege
    - Método preciso de representação e manipulação simbólica de sentenças da álgebra booleana
    - Exemplo
        
        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2023.png)
        
        - Conjunto
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2024.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2025.png)
            
            - Vai ser consistente se cada argumento for 1
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2026.png)
                
                - Podemos ver que há um caso em que as três são 1, logo é um conjunto consistente
    - Sintaxe
        - As regras sintáticas da lógica
        - Alfabeto
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2027.png)
            
            - ∑* representa o conjunto de todas as expressões construídas a partir do alfabeto ∑ (incluindo o vazio)
        - Conjunto ∑*
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2028.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2029.png)
            
            - Há muitas expressões que não são lógicas mas que pertencem à ∑*
            - Definição dos operadores
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2030.png)
                
        - Conjuntos indutivos
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2031.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2032.png)
            
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2033.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2034.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2035.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2036.png)
                
        - Expressões legítimas
            - É um conjunto indutivo que contém expressões construídas a partir do alfabeto ∑ que possuem significado lógico (no caso da lógica simbólica e álgebra booleana)
            - Esse conjunto de expressões legítimas é chamado de <expr> ou  prop
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2037.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2038.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2039.png)
            
            - <expr> é o fecho indutivo de X sobre F
            - Definindo <expr>
                - De cima para baixo
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2040.png)
                    
                - De baixo para cima
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2041.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2042.png)
                    
                - Relacionado as duas definições
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2043.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2044.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2045.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2046.png)
                    
        - Conjuntos livremente gerados
            - Seja A um conjunto qualquer e X um subconjunto de A, suponha que F seja um conjunto de funções sobre A cada uma com sua aridade (A é uma analogia à PROP)
            - O fecho indutivo X+v sob F será um conjunto livremente gerado se:
                - As funções de F forem injetoras quando restritas a entradas de X+v
                    - Como saber se as funções são injetoras
                        - Fazer uma prova por indução
                            - Se f(x) = f(y); x = y
                            - Ou, se x ≠ y; f(x) ≠ f(y)
                - Quaisquer duas funções distintas de F possuem conjunto imagem sob X+v diferentes
                - Nenhum elemento da base X está no conjunto imagem de uma f∈F sob X+v
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2047.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2048.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2049.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2050.png)
                
                - Não, pois o elemento a é representado por *(b, c) e por *(c, b); logo * não é uma função injetora
            - PROP é livremente gerado
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2051.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2052.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2053.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2054.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2055.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2056.png)
                
                - Com isso, é provado que PROP é livremente gerado
        - Funções recursivas sobre PROP
            - Como PROP é um conjunto livremente gerado podemos definir funções recursivamente sobre PROP
            - Funções
                - Calcular o número de símbolos de uma expressão
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image.png)
                    
                - Calcular o número de parênteses à esquerda
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%201.png)
                    
                - Calcular o número de parênteses à direita
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%202.png)
                    
                - Calcular o número de parênteses
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%203.png)
                    
                - Calcular o número de operadores
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%204.png)
                    
                - Determinar as subexpressões de uma expressão
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%205.png)
                    
                - Calcular o posto de uma expressão
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%206.png)
                    
            - Uma vez que definimos funções recursivas sobre os elementos de PROP, podemos provar propriedades desses elementos, usando indução matemática
            - Provando propriedades sobre PROP
                - Para toda proposição φ∈PROP o número de parênteses de φ é par
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%207.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%208.png)
                    
                - Para toda proposição φ∈PROP o número total de símbolos de φ é no mínimo igual ao número de operadores de φ
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%209.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2010.png)
                    
                - Para toda fórmula φ∈PROP, o número de parênteses à esquerda de φ é igual ao número de parênteses à direita de φ
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2011.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2012.png)
                    
                - Para toda fórmula φ∈PROP, o número de subfórmulas de φ é no máximo, duas vezes o número de operadores de φ mais 1
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2013.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2014.png)
                    
                - Para toda fórmula φ∈PROP, o posto (altura da árvore sintática) de φ é no máximo igual ao número total de símbolos de φ
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2015.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2016.png)
                    
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2017.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2018.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2019.png)
                
    - Semântica
        - Está relacionada ao valor matemático
        - Dado que PROP é livremente gerado, sabemos que podemos definir funções recursivamente sobre PROP pois o resultado está seguro (do ponto de vista matemático)
            - Queremos fazer uma função que retorna um valor matemático de forma recursiva
        - Definição formal desse processo
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2057.png)
            
            - A função valor traz a valoração para cada elemento de uma expressão que percente à X+v (0 ou 1)
                - Valor é uma função recursiva
                - Quando Valor(e) sendo e atômica, então usamos a função v() que dá de fato o valor booleano à expressão
            - A função d é uma função que mostra as operações
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2058.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2059.png)
                
        - Teorema da extensão homomórfica única
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2060.png)
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2061.png)
            
            - A = PROP
        - Valoração
            - Uma valoração é um função v: X→Z de forma que existe uma função v̂: X+v→Z tal que:
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2062.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2063.png)
                
                - Lembrando que, a → b ≡ ¬a V b
            - Definição da função
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2064.png)
                
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2065.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2066.png)
                
        - Satisfabilidade
            - Seja φ uma proposição, φ é dita satisfatível se existe pelo menos uma valoração w que a satisfaz (ŵ(φ) = 1)
            - φ é chamada de tautologia se toda valoração a satisfaz
            - Seja φ uma proposição, φ é dita refutável se existe pelo menos uma valoração w que não a satisfaz (ŵ(φ) = 0)
            - φ é chamada de insatisfatível se nenhuma valoração a satisfaz
            
            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2067.png)
            
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2068.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2069.png)
                
                - Como há pelo menos um caso em que ŵ(φ) = 1, então φ é satisfazível
        - Conjunto satisfatível
            - Suponha que S seja um conjunto de proposições, dizemos que S é satisfatível se existe pelo menos uma valoração que satisfaz todas as proposições de S
                - S será insatisfatível quando não for satisfatível
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2070.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2071.png)
                
                - Como existe um caso em que as 3 proposições de S são 1, logo S é satisfatível
        - Consequência lógica
            - Dizemos que uma proposição φ é uma consequência lógica do conjunto S se toda valoração que satisfaz S também satisfaz φ
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2072.png)
                
                - Nesse caso é verdade
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2073.png)
                
                - Nesse caso não é verdade
            - Seja Γ um conjunto de sentenças lógicas e φ uma sentença, dizemos que φ é consequência lógica de Γ se toda valoração que satisfaz Γ também satisfaz φ
                - Usamos a notação Γ ⊨ φ
                - Se Γ for um conjunto finito ( Γ = {a1, … , an}) então a leitura de Γ ⊨ φ é                  {a1, … , an} → φ
            - Teoremas
                - 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2074.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2075.png)
                    
                - 2
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2076.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2077.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2078.png)
                    
- Problema da satisfatibilidade
    - Problema: dada uma expressão φ da lógica proposicional pergunta-se: φ é satisfatível?
        - Para resolver uma instância do problema SAT, temos que realizar um certo número de operações booleanas, que depende do tamanho da expressão de entrada φ
    - Custo computacional
        
        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2079.png)
        
    - Métodos
        - Tabela-verdade
            - Consiste em construir uma tabela de valores-verdade onde suas linhas representam valorações-verdade e suas colunas representam subexpressões da proposição a qual queremos avaliar a sua satisfabilidade
                - Se na última coluna o 1 aparecer, então a expressçao é satisfatível
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2080.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2081.png)
                
                - Sim, é satisfatível
        - Tableaux
            - Esse método é baseado em uma árvore de possibilidades a partir de um conjunto de regras simples, o método dos tableaux; essa árvore resultante indica os conjuntos possíveis como sendo o caminho de sua raiz até a folha
            - Regras
                - As regras podem ser dispostas em tipos α (não bifurcam a árvore) e β (bifurca a árvore)
                - Tipo α
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2082.png)
                    
                    - Se v̂(¬φ) = 1, então v̂(φ) só pode ser 0 e vice-versa
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2083.png)
                    
                    - Se um “E” é 1 então ambos os parâmetros do E são 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2084.png)
                    
                    - Se um “OU” é 0 então ambos os parâmetros são 0
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2085.png)
                    
                    - Se um “SE-ENTÃO” é 0 então é porque o parâmetro “SE” é 1 e o parâmetro “ENTÃO” é 0
                - Tipo β
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2086.png)
                    
                    - Se um “E” é 0, então ou o primeiro parâmetro, ou o segundo, ou ambos são zero
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2087.png)
                    
                    - Se um “OU” é 1, então ou o primeiro, ou o segundo ou ambos são zero
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2088.png)
                    
                    - Se um “SE-ENTÃO” é 1, então ou o primeiro parâmetro é 0 ou ambos são 1
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2089.png)
                
                - Sim, é satisfatível; já que existe pelo menos um ramo que satisfaz
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2090.png)
                
                - Sim, é satisfatível; já que existe pelo menos um ramo que satisfaz
            - Quando perguntamos se uma fórmula é tautologia, vamos verificar se existe a possibilidade dela ser falsa (v̂(φ) = 0), se todos os ramos fecharem é porque φ de fato é uma tautologia; caso contrário não é uma tautologia
                - Por isso, o método tableaux é um método de prova por refutação
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2091.png)
                
                - Como todos os ramos estão fechados então não existe uma possibilidade para o que foi perguntado, logo v̂(φ) = 1 e é uma tautologia
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2092.png)
                
                - Como todos os ramos estão fechados então não existe uma possibilidade para o que foi perguntado, logo v̂(φ) = 1 e é uma tautologia
            - Caso a pergunta seja φ é refutável nós fazemos o método de tableaux considerando v̂(φ) = 0 e caso tenha contradição em algum ramo então φ é de fato refutável
                - Caso a pergunta seja φ é satisfatível fazemos o contrário
            - Caso a pergunta seja φ é insatisfatível nós fazemos o método de tableaux considerando v̂(φ) = 1 e caso tenha contradição em todos os ramos então φ é de fato insatisfatível
            - Quando perguntamos se Γ ⊨ φ (sendo Γ = {a1, … , an}), é a mesma coisa que perguntar se v̂({a1, … , an} → φ) é uma tautologia
                - No caso de tautologia usando o método de tableaux queremos procurar valorações que satisfaçam {a1, … , an} e que refute φ; caso não exista então φ é de fato consequência lógica de Γ
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2093.png)
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2094.png)
                
            - Vantagens e desvantagens
                
                ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2095.png)
                
        - Resolução
            - Conceitos
                - Literal: é uma fórmula atômica ou a negação de uma fórmula atômica
                - Cláusula: é uma disjunção ou conjunção de literais
            - Formas
                - Forma Normal Conjuntiva (FNC)
                    - Uma cláusula está na forma normal conjuntiva se for uma conjunção de cláusulas (”e’s entre as cláusulas”)
                    - Esta cláusula por sua vez deve ser uma disjunção de literais (”ou’s entre os literais”)
                    - A FNC é basicamente um e de “ou’s”
                    - Teorema
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2096.png)
                        
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2097.png)
                        
                - Forma Normal Disjuntiva (FND)
                    - Uma cláusula está na forma normal disjuntiva se for uma disjunção de cláusulas (”ou’s” entre as cláusulas)
                    - Esta cláusula por sua vez deve ser uma conjunção de literais (”e’s entre os literais”)
                    - A FND é basicamente um ou de “e’s”
                    - Teorema
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2098.png)
                        
                    - Exemplo
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%2099.png)
                        
                - Procedimento das formas normais
                    - 1º: Eliminar os conectivos → e ↔ de cada cláusula
                    - 2º: trazer o sinal de negação para imediatamente antes dos átomos usando a substituição da dupla negação e as Leis de Morgan
                    - 3º: Obter a forma normal (conjuntiva ou disjuntiva) utilizando as regras distributivas e as outras
                    - Exemplos
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20100.png)
                        
                        - 1
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20101.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20102.png)
                            
                        - 2
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20103.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20104.png)
                            
                        - 3
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20105.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20106.png)
                            
                        - 4
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20107.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20108.png)
                            
                        - 5
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20109.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20110.png)
                            
                        - 6
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20111.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20112.png)
                            
            - O método em si
                - Observações importantes
                    - Para uma fórmula na FNC ser INSAT, é suficiente que uma das cláusulas seja INSAT
                    - Para uma fórmula na FNC ser SAT nós checamos se ela é INSAT caso não seja, então ela é SAT
                    - Para uma fórmula na FNC ser TAUT, nós checamos se a negação dela é INSAT, caso seja então ela é TAUT
                    - Para uma fórmula na FNC ser REF, nós checamos se a fórmula não é TAUT
                    - Teoremas sobre consequência lógica
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20113.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20114.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20115.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20116.png)
                        
                        - Se a resposta do método for sim (α é INSAT), então Γ é consequência lógica de φ; caso contrário então Γ não é consequência lógica de φ
                - Para resolver o problema SAT pelo meio da resolução, primeiro pegamos a fórmula e transformamos ela em uma fórmula na FNC
                - Depois criamos novas cláusulas com base nisso:
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20117.png)
                    
                - Teorema
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20118.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20119.png)
                    
            - Exemplos
                - 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20120.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20121.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20122.png)
                    
                - 2
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20123.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20124.png)
                    
                - 3
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20125.png)
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20126.png)
                    
                - 4
                    
                    ![Untitled](../../assets/faculdade/periodo2/logica-p-computacao/Untitled%20127.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2020.png)
                    
        - Dedução natural
            - Uma dedução de uma fórmula A é uma árvore de fórmulas em que cada fórmula que não é uma suposição é a conclusão de uma aplicação correta de uma das regras de inferência
                - As suposições na dedução que não são descartadas em nenhuma regra nela são chamadas de suposições abertas da dedução
                - Se todas as suposições foram descartadas, ou seja, não houver suposições abertas, dizemos que a dedução é uma prova de A e que A é um teorema
            - Regras
                - Na implicação sobe e na eliminação desce
                - E
                    - Introdução
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2021.png)
                        
                    - Eliminação
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2022.png)
                        
                - Implicação
                    - Introdução
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2023.png)
                        
                        - Houve o descarte da hipótese (1) (a partir de A não importa mais de A é V ou T o que importa é que provamos que A implica em B)
                        - Caso especial
                            - Quando os 3 pontinhos são o conjunto vazio
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2024.png)
                            
                    - Eliminação
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2025.png)
                        
                - Ou
                    - Introdução
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2026.png)
                        
                    - Eliminação
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2027.png)
                        
                - Redução ao absurdo intuicionista (Ex falso quodibet (EFQ) ou RAI)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2028.png)
                    
                    - Do falso, pode-se inferir qualquer coisa (se A for atômica)
                - Redução ao absurdo clássica (ou RAC)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2029.png)
                    
                    - Mesma observação do RAI
                - Negação
                    - Sabemos que ¬A ≡A→⊥ (⊥ = Falso), logo as regras de introdução e eliminação da negação tornam-se casos especiais das regras I→ e E→
                    - Introdução
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2030.png)
                        
                    - Eliminação
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2031.png)
                        
                - O cálculo NJ inclui todas as regras acima, o cálculo NM inclui todas menos o Ex falso quodibet
            - ⊦ = símbolo de derivabilidade
                - Exemplo, se queremos derivar φ (⊦φ), vamos fazer uma árvore utilizando as regras dedutivas e caso seja possível fazer essa árvore então φ é uma tautologia
                - Podemos também derivar φ a partir de Ψ (Ψ⊦φ)
            - Corretude: se eu derivo φ então isso implica que φ é verdade
                - ⊦φ → ⊧φ
            - Quando vamos derivar, se houver alguma dependência como por exemplo, Ψ⊦φ, vamos utilizar as hipóteses (nesse caso, Ψ) para derivar φ e esta é assumida como verdadeira desde o início da derivação
                - Ao longo da derivação, vão surgindo hipóteses que são suposições temporárias feitas para derivar uma conclusão que pode ser eliminada mais tarde
            - Exemplos
                - 1
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2032.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2033.png)
                    
                - 2
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2034.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2035.png)
                    
                - 3
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2036.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2037.png)
                    
                - 4
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2038.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2039.png)
                    
                - 5
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2040.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2041.png)
                    
                - 6
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2042.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2043.png)
                    
                - 7
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2044.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2045.png)
                    
                - 8
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2046.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2047.png)
                    
                - 9
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2048.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2049.png)
                    
        - Cálculo de sequentes
            - Sequente
                - É uma estrutura de duas sequências de fórmulas separadas por uma seta ou um símbolo de derivabilidade
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2050.png)
                    
                    - Onde cada Ai e Bj é uma fórmula
                - Usamos letras gregas maiúsculas como metavariáveis para listas ou sequências finitas de fórmulas
                    - Γ ⇒ Δ
                - A sequência de fórmulas do lado esquerdo da seta é chamada de antecedente e a lado direito é chamada de consequente
                    - Os antecedentes possuem valoração F e os consequentes possuem valoração V
                - OBS: qualquer uma dessas sequências podem ser vazias
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2051.png)
                    
                - Significado
                    - n ≠ 0, m ≠ 0
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2052.png)
                        
                    - n = 0, m ≠ 0
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2053.png)
                        
                    - n ≠ 0, m = 0
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2054.png)
                        
                    - n = 0, m = 0
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2055.png)
                        
            - É basicamente uma árvore, na qual as folhas são sequentes chamados de axiomas, cada nó da árvore é um sequente obtido a partir do sequente anterior pelas regras do cálculo de sequentes
                - A raiz da árvore é o sequente final
            - Regras
                - Estruturais
                    - Weakening
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2056.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2057.png)
                            
                    - Contraction
                        - Duplicar o elemento mais longe da catraca
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2058.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2059.png)
                            
                    - Interchange (ou Permutation)
                        - 1 traço: troca exclusiva de um termo por outro termo
                        - 2 traços: reorganização liberada de qualquer termo por qualquer termo
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2060.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2061.png)
                            
                    - Cut
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2062.png)
                        
                        - Teorema da eliminação do corte (Hauptsatz)
                            - Toda derivação pode ser transformada numa equivalente sem o uso da regra do corte
                - Operacionais
                    - Conjunção
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2063.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2064.png)
                            
                    - Disjunção
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2065.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2066.png)
                            
                    - Implicação
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2067.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2068.png)
                            
                    - Negação
                        - Left
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2069.png)
                            
                        - Right
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2070.png)
                            
                - Só podemos aplicar as regras no axioma (à esquerda ou à direita) mais longe da catraca
            - Cálculos
                - LK: é o cálculo de sequentes para a lógica clássica
                - LJ: é o cálculo de sequentes para a lógica intuicionísta, possui as mesmas regras que o cálculo LK sendo que o sucedente possui no máximo uma fórmula
                - LM: é o cálculo LJ sem a regra WR (Weakening right)
            - Exemplos
                - 1
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2071.png)
                    
                    - LK
                    - LJ
                    - LM
                - 2
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2072.png)
                    
                - 3
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2073.png)
                    
                    - LJ
                    - LM
                - 4
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2074.png)
                    
                - 5
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2075.png)
                    
                - 6
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2076.png)
                    
                - 7
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2077.png)
                    
                - 8
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2078.png)
                    
                - 9
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2079.png)
                    
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2080.png)
                

---

## Lógica de primeira ordem

- Trata-se de uma linguagem simbólica para representação de enunciados na qual os objetos mencionados tenham uma representação própria nas sentenças simbólicas (vocabulário)
    - Temos que ter símbolos para os objetos e para predicados e relações, este conjunto de símbolos representa o vocabulário desta lógica
- Exemplo
    
    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2081.png)
    
    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2082.png)
    
    - Símbolos dos objetos
        
        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2083.png)
        
    - Símbolos dos predicados e relações
        
        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2084.png)
        
    - Resultado
        
        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2085.png)
        
- Estrutura
    - É o que dá significado ao vocabulário, dando a noção de valoração para associar valores aos objetos e predicados
    - Definição
        - Uma estrutura A é definida por 4 componentes
            - Um conjunto de elementos chamado domínio de A (dom(A)) ou universo de A, é o conjunto de objetos
            - Um conjunto de relações sobre dom(A), cada um com sua aridade
            - Uma coleção de elementos de dom(A), que são considerados elementos especiais
            - Um conjunto de funções sobre dom(A), cada uma com sua aridade
            - OBS: qualquer um destes conjuntos pode ser vazio
            - Exemplos
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2086.png)
                
    - Exemplo
        - 1
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2087.png)
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2088.png)
            
        - 2
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2089.png)
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2090.png)
            
    - Assinaturas
        - Para definir um vocabulário simbólico a ser usado na formalização de sentenças sobre uma dada estrutura de primeira ordem vamos precisar identificar os elementos destacados, as relações e suas respectivas aridades e as funções e suas respectivas aridades
            - O conjunto reunindo estes três fatores é chamado de assinatura
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2091.png)
            
            - Assinatura
                - Dois elementos destacados a, b
                - 1 relação binária R(_,_) e 1 relação unária S(_)
                - 1 função unária f(_) e 1 função binária g(_,_)
            - Interpretações
                - A
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2092.png)
                    
                - B
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2093.png)
                    
            - Exemplo
                - Sentenças
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2094.png)
                    
                - A
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2095.png)
                    
                - B
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2096.png)
                    
                - Podemos ver que as interpretações possuem significados diferentes, enquanto que as sentenças fazem sentido dentro da interpretação da assinatura A, elas não fazem sentido dentro da interpretação da assinatura B por conta de seu vocabulário
    - Seja A com uma assinatura L, dizemos que A é uma L-estrutura
    - Homomorfismo
        - Seja L uma assinatura e A e B L-estruturas
        - Seja h uma função de dom(A) em dom(B) (dom(A) → dom(B))
        - Dizemos que h é um homomorfismo da estrutura A para B se:
            - Para cada constante c de L, h(cA) = cB
            - Para todo símbolo de relação n-ária R de L e toda n-upla (a1, …, an) de elementos de A, se (a1, …, an) ∈ RA então (h(a1), …, h(an)) ∈ RB
            - Para todo símbolo de função n-ária g de L e toda n-upla (a1, …, an) de elementos de A, h(gA(a1, … an)) = gB(h(a1), …, h(an))
        - Exemplos
            - 1
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2097.png)
                
                - h não é um homomorfismo de A para B pois nem toda relação de binária de A (a1, a2) aplicada à função h pertence à B (exemplo: (2, 3) é uma relação binária de A, mas (h(2), h(3)) não é uma relação binária de B)
            - 2
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2098.png)
                
                - h é um homomorfismo de A em B pois para cada constante de A, h(cA) = cB (h(4) = 1) e para toda função g de L e toda tupla unária de A, h(gA(x)) = gB(h(x)) pelo fato de que gA aplicada à função h = x (pois 4x mod 3 é x) que é justamente a mesma coisa da função gB; logo h é um homomorfismo de A em B
            - 3
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%2099.png)
                
                - h é um homomorfismo de A em B pois para todo símbolo de função n-ária f de L e toda n-upla (a1, …, an) de elementos de A, h(fA(a1, …, an)) = fB(h(a1), … h(an))
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20100.png)
                    
        - Imersão
            - Uma imersão é todo homomorfismo na qual a função h é injetora e que para todo símbolo de relação n-ária R de L e toda n-upla (a1, …, an) de elementos de A, se (a1, …, an) ∈ RA se, e somente se (h(a1), …, h(an)) ∈ RB
        - Tipos
            - Isomorfismo
                - É uma imersão sobrejetora ou simplesmente um homomorfismo bijetivo, que mapeia uma estrutura para outra de maneira que as duas sejam essencialmente idênticas
            - Endomorfismo
                - É um homomorfismo de uma estrutura para si mesma, sem a necessidade de ser injetivo ou sobrejetivo
            - Automorfismo
                - É um isomorfismo de uma estrutura para si mesma, preservando toda a estrutura interna da lógica
    - Sub-estrutura
        
        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20101.png)
        
    - Termos
        - É qualquer expressão que pode denotar um objeto ou entidade no domínio da estrutura, termos podem representar constantes, variáveis, funções aplicadas a termos e “nada”
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20102.png)
            
        - O conjunto de termos de uma assinatura L é o fecho indutivo do conjunto X = {constantes} U {variáveis} U {destaques sob o conjunto dos símbolos das funções de L}
        - Um termo fechado não contém variáveis livres
    - Fórmulas atômicas
        
        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20103.png)
        
    - Escopo dos quantificadores
        - É a porção da fórmula que está “sob o controle” do quantificador
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20104.png)
            
    - Variável livre e ligada
        - Uma ocorrência de uma variável em uma fórmula é ligada se, e somente se, ela está no escopo de um quantificador aplicado a ela ou ela é a ocorrência de um quantificador
        - Uma ocorrência de uma variável em uma fórmula é livre se, e somente se, essa ocorrência não é ligada
        - Portanto, variável é ligada numa fórmula se pelo menos uma ocorrência dela é ligada; senão, ela é livre
        - Exemplo
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20105.png)
            
            - ‘a’ é ligada pois a ocorrência de ‘a’ no “para todo” é ligada
            - ‘x’ é ligada pois a ocorrência de ‘x’ no “existe” é ligada
            - ‘y’ é livre e ligada; pois na ocorrência de f(x, y) antes do “para todo ‘y’” é uma ocorrência livre e na ocorrência dentro do escopo do “para todo ‘y’” é uma ocorrência ligada
    - Fórmulas bem formadas
        - Uma fórmula bem formada da lógica de primeira ordem é definida recursivamente como:
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20106.png)
            
            - Fórmulas são geradas apenas por um finito número de aplicações das regras acima
    - Sentenças
        - São fórmulas sem variáveis livres
        - Uma sentença atômica é uma fórmula atômica sem variável
        - Significado de uma sentença atômica
            - Seja L uma assinatura e φ uma sentença atômica de L, o significado de φ segundo uma interpretação de L numa L-estrutura A é determinado pelo resultado da interpretação sobre os termos de φ e sobre o símbolo de relação de φ
            - Exemplo
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20107.png)
                
    - Modelo e contra-modelo
        - Seja L uma assinatura e A uma L-estrutura, dizemos que A é um modelo de φ sob uma determinada interpretação de L em A se φA for verdadeira
        - Seja L uma assinatura e A uma L-estrutura, dizemos que A é um contra-modelo de φ sob uma determinada interpretação L em A se φA for falsa
    - Diagrama positivo
        - Usado para passar de uma estrutura para um conjunto de sentenças que a descreve
        - Seja A uma L-estrutura, o conjunto de todas as sentenças atômicas de L que são verdadeiras (as sentenças podem ser puramente verdadeiras ou negações de sentenças atômicas falsas) sob determinada interpretação em A é chamado de diagrama positivo
        - Como construir
            - Para todo símbolo de relação n-ária R de L, inclua uma sentença atômica da forma R(t1, …, tn) se, e somente se, a tupla (t1A, …, tnA) ∈ RA
            - Para todo símbolo de função n-ária f de L, inclua uma sentença atômica da forma f(t1, …, tn) = tn+1 se, e somente se, fA(t1A, …, tnA) = tn+1A na estrutura A onde (t1A, …, tnA) são representações dos elementos de A
            - No início, começar por aplicações de relações e funções nos destaques
        - Extensão
            - Seja A uma L-estrutura, quando desejamos produzir o diagrama positivo de A e A possui elementos “sem nome”; definimos uma extensão de A chamada A’ que admite esses “sem nome” como novos elementos destacados
            - Isso significa dizer que a assinatura A’ é L’ = L U {c1, …, cn}, onde cada ci é um símbolo de constante para representar ai
                - Pode-se abreviar L U {c1, …, cn} como L(𝐶̅)
        - Exemplos
            - 1
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20108.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20109.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20110.png)
                
                - Exemplo de diagrama positivo = {Q(c), f(c, c) = 0, g(c) = 3, P(c, f(c, c)), f(f(c, c), c) = 1, Q(g(c)), …}
            - 2
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20108.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20111.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20112.png)
                
            - 3
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20113.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20114.png)
                
    - Modelo canônico
        - Dado um conjunto de sentenças atômicas T numa linguagem L, se quisermos construir a estrutura que satisfaça toda sentença, precisaremos então definir o domínio, destaques, relações e funções
        - Como construir
            - Domínio
                - O domínio da estrutura B que está sendo construído será definido pelo conjunto dos representantes das classes de equivalência (t~) dos termos fechados de L no conjunto T de sentenças atômicas
            - Destaques
                - Os destaques são os c~ dados onde c é um símbolo de constante L
            - Relações
                - Seja R um símbolo de relação n-ária de L, então para toda sentença de T da forma R(t1, …, tn) faremos com que a n-upla (t1~,  …, tn~) pertença à relação, ou seja, R(t1, …, tn) ∈ T se, e somente se, (t1~, …, tn~) ∈ RB
            - Funções
                - Seja f um símbolo de função n-ária de L, então para todo símbolo da função n-ária f, o representante da classe de equivalência de f(t1, …, tn) (f(t1, …, tn)~) é igual a fB aplicada aos elementos (t1~, …, tn~); ou seja, fB(t1~, …, tn~) = f(t1, …, tn)~
        - A L-estrutura B construída a partir de L e T é chamada de modelo canônico de T
            - Essa L-estrutura é parecida com o modelo ‘original’ descrito por T, isso quer dizer que podemos contruir um homomorfismo de B para qualquer outro modelo de T
            - A é chamada de modelo canônico pois funciona como uma espécie de referencial para todos os modelos de T
            - Mostrando que A é modelo canônico
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20115.png)
                
        - Exemplos
            - 1
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20116.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20117.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20118.png)
                
            - 2
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20116.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20119.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20120.png)
                
            - 3
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20121.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20122.png)
                
- Problema da satisfatibilidade
    - Dado um conjunto de sentenças C, caso C seja um conjunto de sentenças atômicas então C possui um modelo canônico
        - Caso contrário, precisaremos de novos conceitos para resolver este problema quando C contém fórmulas não atômicas
        - Esses conceitos combinados farão com que consigamos resolver o problema SAT utilizando o método da resolução (pode ser utilizado os outros métodos também)
    - Conceitos
        - Substituição
            - Técnica na qual substituímos variáveis de uma fórmula bem formada em termos constantes ou termos mais complexos, simplificando expressões e movendo a fórmula em direção a um formato mais próximo da lógica proposicional
            - Queremos definir precisamente o resultado da substituição das ocorrências da variável x em uma FBF φ por um termo t
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20123.png)
                
                - Nos quantificadores, só ocorre a substituição se x for uma variável livre
            - OBS: a substituição é feita se a variável, quando trocada, permanecer com o mesmo status de antes da substituição
            - OBS: o termo da variável a ser substituída não pode conter a própria variável
            - Exemplos
                - 1
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20124.png)
                    
                    - Não muda nada pois x é uma variável ligada
                - 2
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20125.png)
                    
                    - Muda para ∀x∀y(P(x, y) → R(f(a)))
                - 3
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20126.png)
                    
                    - Não muda nada, pois caso mudássemos seria realizada uma troca de uma variável livre z para uma variável ligada y, mudando o significado da fórmula
                        - Poderiamos fazer [w/z], assim ficaria uma substituição válida
                - 4
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20127.png)
                    
                    - A substituição não pode ser aplicada pois estariamos substituindo uma variável livre por uma variável ligada
                - 5
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20128.png)
                    
                    - A substituição não pode ser aplicada pois estariamos substituindo uma variável livre por uma variável ligada (f(x) contém x que é uma variável ligada)
                - 6
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20129.png)
                    
                    - A substituição não pode ser realizada pois o termo contém a própria variável a ser substituída
                - 7
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20130.png)
                    
                    - f(a)
                - 8
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20131.png)
                    
                    - g(g(a, b), g(f(f(c)), a))
                - 9
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20132.png)
                    
                    - A substituição não pode ser aplicada pois o termo f(y) contém a variável a ser substituída y
        - Valor verdade de uma sentença (Modelo de Tarski)
            - Seja L uma assinatura, A uma L-estrutura e .A uma interpretação dos símbolos de L na L-estrutura, o valor verdade de uma sentença φ de L é definida indutivamente da seguinte forma:
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20133.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20134.png)
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20135.png)
                
        - Satisfatibilidade de uma sentença
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20136.png)
            
            - Satisfabilidade de um conjunto de sentenças
                
                ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20137.png)
                
        - Equivalência lógica
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20138.png)
            
        - Satisfabilidade de uma fórmula
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20139.png)
            
            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20140.png)
            
        - Resolução para lógica de predicados
            - Temos os mesmos conceitos de literal, cláusula e FNC; mas precisamos de ainda mais conceitos
            - Forma normal prenex (Prenexação)
                - Definição
                    - Uma fórmula φ na FOL está na forma normal prenex se, e somente se, a fórmula está na forma (Q1x1)…(Qnxn)(M)
                        - Cada (Qixi), i = 1…n, ou é um (∀xi) ou é um ∃(xi) e M é uma fórmula sem quantificadores
                        - (Q1xi)…(Qnxn) é chamado de prefixo e M de matriz da fórmula φ
                    - Exemplos de fórmulas na FNP
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20141.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20142.png)
                        
                    - Teorema
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20143.png)
                        
                - Algoritmo
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20144.png)
                    
                    - Leis
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20145.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20146.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20147.png)
                        
                        - Nas leis 7 e 8, devemos renomear uma das variáveis ligadas
                    - O algoritmo em si
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20148.png)
                        
                - Exemplos
                    - 1
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20149.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20150.png)
                        
                    - 2
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20151.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20152.png)
                        
                    - 3
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20153.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20154.png)
                        
                    - 4
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20155.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20156.png)
                        
            - Forma padrão de Skolem (Skolemização)
                - Transformação de uma fórmula da FOL que elimina o quantificadores existenciais e os substitui por funções de Skolem, sem alterar a satisfabilidade da fórmula
                - Como construir
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20157.png)
                    
                    - Teorema de Lowenheim-Skolem
                        - Seja φ uma fórmula da lógica de predicados numa assinatura L, tal que φ está na FNP
                        - Seja φ’ a fórmula resultante da eliminação dos quantificadores existenciais que ocorrem em φ, cujas variáveis correspondentes são substituídas por termos do tipo f(x1, …, xn) onde f é um novo símbolo de função e x1, …, xn são variáveis universalmente quantificadas imediatamente anteriores a esse existencial
                        - Então se existe uma L-estrutura A que é modelo para φ, é possível construir uma L-estrutura A’ que é modelo para φ’ simplesmente acrescentando à L-estrutura A uma interpretação para cada símbolo novo de função em A’
                        - Caso não haja quantificadores universais, como por exemplo em ∃x∃y(P(x, y) → Q(y)); x e y são substituídas por constantes gerando P(a, b) → Q(b) que está na FPS
                            - Assim, na estrutura A’ é preciso acrescentar apenas mais dois novos destaques
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20158.png)
                        
                        - A fórmula já está na FNP e a matrix na FNC, agora precisamos eliminar os quantificadores existenciais e substituir por funções de Skolem
                            - Ao eliminar o quantificador existencial ∃y, o argumento y dentro de R(x, y) é substituído por uma função de Skolem na qual esta função depende das variável ligadas aos quantificadores universais
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20159.png)
                        
                - Exemplos
                    - 1
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20160.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20161.png)
                        
                    - 2
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20162.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20163.png)
                        
                    - 3
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20164.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20165.png)
                        
            - Herbrand
                - Desenvolveu um algoritmo para provar teoremas na FOL (falar que uma fórmula é tautologia na FOL), que é o algoritmo da unificação
                - Método de Herbrand
                    - Um conjunto de cláusulas é insatisfatível se, e somente se, ele é falso sob todas as interpretações sobre todos os domínios
                    - Como existem infinitos domínios fixamos um domínio H, chamado de universo de Herbrand
                        - Herbrand provou que basta mostrar que o conjunto de cláusulas é insatisfatível sob todas as interpretações nesse domínio
                - Universo de Herbrand
                    - Seja H0 o conjunto de constantes que aparecem em um conjunto S de cláusulas, se nenhuma constante aparece em S então H0 = {a}
                    - Para i = 0, 1, …, seja Hi+1 a união de Hi e o conjunto de todos os termos da forma f^n(t1, …, tn) para todos os símbolos da função n-ária f que ocorrem em S onde tj, j = 1, …, n são membros do conjunto Hi; então cada Hi é chamado de conjunto constante do nível i de S, e H∞ é chamado de universo de Herbrand
                - Instância básica de uma cláusula
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20166.png)
                    
                - Teorema de Herbrand
                    - Um conjunto S de cláusulas é insatisfatível se, e somente se, existe um conjunto finito insatisfatível S’ de instâncias básicas de clásulas de S
                - Unificação
                    - Sejam t1 e t2 termos de uma assinatura L nos quais podem aparecer ocorrências das variáveis x1, …, xn
                    - O problema da unificação de t1 e t2 é definido como sendo o problema de se encontrar (caso exista) uma substituição das variáveis x1, …, xn por termos s1, …, sn tal que quando aplicadas a t1 e t2 produzem termos idênticos
                        - Em outras palavras, t1 = t1’, …, tn = tn’ pode ser visto como um sistema de equações com x1, …, xn (variáveis que ocorrem nos termos) como sendo os indeterminantes do sistema, ou seja, dado S = {t1 = t1’, …, tn = tn’} buscamos uma solução, caso exista, na forma [s1/x1, …, sn/xn] onde s1, …, sn são termos de L
                    - Uma equação x = t está na forma resolvida em um sistema de equação S se x for uma variável que não aparece nem no termo t e nem em qualquer outro termo de S
                        - Um sistema S está na forma resolvida se todas as suas equações estão na forma resolvida
                        - Se um sistema S é unificável, então o método encontra o unificador mais geral (u.m.g.)
                    - Método
                        - É um conjunto de 3 regras
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20167.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20168.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20169.png)
                            
                    - Exemplos
                        - 1
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20170.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20171.png)
                            
                        - 2
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20172.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20173.png)
                            
                        - 3
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20174.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20175.png)
                            
                        - 4
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20176.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20177.png)
                            
                        - 5
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20178.png)
                            
                            ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20179.png)
                            
                            - *[y/b, y/v, h(a, g(v))/x, g(y)/w, a/z]
                - Exemplos
                    - 1
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20180.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20181.png)
                        
                    - 2
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20182.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20183.png)
                        
                        - Faltou [h(g(a))/x]
                    - 3
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20184.png)
                        
                        ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20185.png)
                        
            - Exemplos
                - 1
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20186.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20187.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20188.png)
                    
                - 2
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20189.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20190.png)
                    
                    ![image.png](../../assets/faculdade/periodo2/logica-p-computacao/image%20191.png)