# ALGORITMOS E ESTRUTURAS DE DADOS

---

[https://sites.google.com/a/cin.ufpe.br/if672/](https://sites.google.com/a/cin.ufpe.br/if672/)

## O que são algoritmos?

São uma sequência de instruções a fim de resolver um problema em um tempo finito e que consiga ler qualquer input desejado

- Exemplo
    - Algoritmo para ver qual o MDC entre dois números
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled.png)
        
        - Input example
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%201.png)
            
            - Passa da linha 1, linha 2:
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%202.png)
                
                - Linha 3: m = 24; Linha 4: n = 12; (retorna para o while pois n ≠ 0)
                    - Com isso, Linha 1: entra no while pois n ≠ 0; Linha 2: r agora é igual à 0; Linha 3: m = 12; Linha 4: n = 0; Como n == 0, não entra no while
                        - Linha 5: return m = 12, que é nossa resposta

---

## Tipos de busca

- Sequential search
    - Compara sucessivamente os elementos da array com uma Key específica até encontrar uma correspondência (bem-sucedida) ou até esgotar a lista (mal-sucedida)
    - Simplicidade e pouca eficiência
    - Exemplo
        - Assumindo que a array esteja ordenada de modo crescente
        - Exemplo 1
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%203.png)
            
            - Os parâmetros são a array A e a search key K (valor)
            - 1ª linha
                - i recebe o valor de 0 (índice auxiliar)
            - 2ª linha
                - Um while é declarado, para entrar nele basta que i seja menor que n (tamanho da array A) e que A[i] ≠ de K
            - 3ª linha
                - Enquanto que a condição seja True, uma unidade é incrementada no i até que ele seja igual à n ou até que A[i] seja igual à K
            - 4ª linha
                - Saiu do while, logo uma das condições foi cumprida, a condição da linha é se i < n; pois quer dizer que não percorreu todos os elementos da lista e i é índice em que A[i] = K
            - 5ª linha
                - A outra condição de saída do while, i = n; logo não achou um A[i] que seja igual à K; por isso retorna -1
- Binary search
    - O binary search funciona comparando uma search key K com A[m] (o meio de uma array), se eles correspondem então o algoritmo para caso contrário o algoritmo repete recursivamente para as duas metades que se dividem em A[0, …, m] e A[m+1, …, n-1]
        - É possível aplicar Binary search sem essa ideia recursiva
    - Mais eficiente
    - Exemplo
        - Assumindo que a array esteja ordenada de modo crescente
        - Exemplo 1
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%204.png)
            
            - Algoritmo BS que usa recursão
            - Os parâmetros são a array A, o limitante esquerdo l, o limitante direito r e a search key K
            - 1ª linha
                - Checa se o limitante direito é maior ou igual ao limitante esquerdo
            - 2ª linha
                - A condição é verdadeira, e m recebe o valor da função piso de (l + r)/2; basicamente o índice do meio da array
            - 3ª linha
                - Checa se A[m] é igual à K
            - 4ª linha
                - Caso K = A[m] então o código retorna m que é o índice em que K está
            - 5ª linha
                - Uma segunda condição que checa se K é menor que A[m]
            - 6ª linha
                - Caso K < A[m] uma chamada recursiva é declarada sendo l o limitante esquerdo e m - 1 o limitante direito (pois como A[m] > K; logo o índice está pelo menos uma unidade à esquerda de m)
            - 7ª linha
                - Uma terceira condição que checa se K > A[m]
            - 8ª linha
                - Caso K > A[m] uma chamada recursiva é declarada sendo m + 1 o limitante esquerdo e r o limitante direito (pois como K > A[m]; logo o índice está pelo menos uma unidade à direita de m)
            - 9ª e 10ª linha
                - Caso r seja menor que l, retorna -1; ou seja, retorna uma falha
        - Exemplo 2
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%205.png)
            
            - Algoritmo de BS que não usa recursão
            - Os parâmetros são a array A e a search key K
            - 1ª e 2ª linha
                - l recebe o valor de 0 e r recebe o valor de n - 1 (basicamente são respectivamente o primeiro e o segundo índice de uma array)
            - 3ª linha
                - Um while é declarado e possui como condição l ≤ r
            - 4ª linha
                - A condição é verdadeira, e m recebe o valor da função piso de (l + r)/2; basicamente o índice do meio da array
            - 5ª e 6ª linha
                - Primeira condição que checa se K = A[m], caso seja verdade a função retorna o valor de m (índice em que K está)
            - 7ª e 8ª linha
                - Segunda condição que checa se K < A[m], caso seja verdade então r recebe o valor de m - 1 pois significa que o índice em que K está; está à esquerda do meio
                    - Logo, o limitante direito deve ser o índice do meio menos um
            - 9ª e 10ª linha
                - Terceira condição que checa se K > A[m], caso seja verdade então l recebe o valor de m - 1 pois significa que o índice em que K está; está à direita do meio
                    - Logo, o limitante esquerdo deve ser o índice do meio mais um
            - 11ª linha
                - Caso l seja maior que r ou o índice não foi encontrado dentro do while retorna -1; logo, uma falha

---

## Tipos de algoritmos

- Brute Force
    - São algoritmos baseados na força bruta, basicamente exaustão
    - São caracterizados pela simplicidade e uma das mais facéis de se aplicar, um exemplo desse algoritmo é o exemplo mais acima
    - Utiliza Sequential search
    - Tipos
        - Exemplo: aplicação para problemas de sorting uma array de N elementos
        - Selection sort
            - No Selection sort, primeiro escaneamos toda a array para verificar qual é o menor elemento e depois mudá-lo de posição com o primeiro elemento da lista
                - Depois fazemos isso em loop n-1 vezes (pois a array é de tamanho N)
            - É chamada de Selection sort pois selecionamos um elemento específico de uma array e mudamos ele de lugar
            - Exemplo de algoritmo para solucionar o problema
                - Exemplo 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%206.png)
                    
                    - O único parâmetro é a array A
                    - 1ª linha
                        - Na primeira linha, fazemos i ← 0 to n - 2
                            - Fazemos isso por dois motivos; o primeiro é porque o i tem a função de ser o índice da nossa array, logo os índices das arrays começam em 0 e vai até n - 1; o segundo motivo é porque não precisamos passar pela array inteira para orderná-la, basta passar por todos os elementos com exceção de um pois este último já estará ordenado, logo fazemos i ← 0 to n - 2
                    - 2ª linha
                        - Na segunda linha, o elemento min (mínimo) recebe i
                    - 3ª linha
                        - Na terceira linha, começa mais um loop que vai de j ← i + 1 to n - 1
                            - j recebe i + 1 pois i já é o mínimo, não sendo necessário comparar um elemento com ele mesmo
                            - Esse for vai até de j = i + 1 (índice atual + 1) até o n - 1 (último índice da lista) pois assim ele percorre todos os elementos com execeção dos elementos da esquerda, que já estão ordenados
                    - 4ª linha
                        - Na quarta linha, comparamos se A[j] < A[min], caso seja True min recebe o valor de j
                            - Como min recebe o índice i, que é o índice atual, essa troca é positiva apenas se o elemento do índice j for menor que o do índice min
                    - 5ª linha
                        - Na quinta linha, acontece o swap dos elementos fazendo com que a array fique ordenada
        - Bubble sort
            - No Bubble sort, comparamos os elementos adjacentes da array e trocamos eles caso estejam fora de ordem e fazendo isso, acabamos por “Bubbling up” o maior elemento pro final da array
                - Fazendo isso repetidamente, acabamos por “Bubbling up” o segundo maior elemento da array e assim por diante
            - Exemplo de algoritmo para solucionar o problema
                - Exemplo 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%207.png)
                    
                    - O único parâmetro é a array A
                    - 1ª linha
                        - Na primeira linha, fazemos um for i ← 0 to n - 2 pelo mesmo motivo que fazemos no Selection sort
                    - 2ª linha
                        - Na segunda linha, fazemos um for j ← 0 to n - 2 - i
                            - Fazemos o j = 0 até n - 2 - i pois os elementos maiores vão ficando ao final da lista, não tendo necessidade de percorrer eles de novo (por isso o ‘- i ‘)
                                - Com isso, os menores elementos vão ficando pro início da array e precisamos de menos loops para trocá-los de lugar apropiadamente
                    - 3ª linha
                        - Na terceira linha comparamos se A[j + 1] < A[j], caso seja True a troca de posições é realizada
- Decrease and conquer
    - Algoritmos baseados na exploração da relação entre a solução de um determinado problema e a solução para um problema de menor do mesmo tipo
    - Pode ser feita de duas formas
        - Top-down
            - Implementação recursiva
            - A ideia é dividir o problema original em subproblemas menores, resolver esses subproblemas recursivamente e depois combinar as soluções dos subproblemas para obter a solução do problema original
                - A implementação final pode ser iterativa embora inicialmente seja recursiva
        - Bottom-up,
            - Implementação iterativa
            - Começando com a solução para o menor problema possível, ela vai construindo soluções para problemas cada vez maiores até chegar à solução do problema original
    - Variações
        - Decrease by a constant
            - O tamanho da instância do problema é reduzido por um valor fixo a cada iteração do algoritmo
                - Normalmente, essa constante é igual a um
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%208.png)
            
        - Decrease by a constant factor
            - Sugere reduzir o tamanho da instância do problema por um fator constante em cada iteração do algoritmo
                - Na maioria das aplicações, esse fator constante é igual a dois
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%209.png)
            
        - Variable decrease
            - O padrão de redução do tamanho da instância do problema varia de uma iteração para outra do algoritmo
    - Utiliza binary search (no caso de ‘Decrease by a constant factor’)
    - Tipos
        - Exemplo: aplicação para problemas de sorting uma array de N elementos
        - Insertion sort
            - A ideia é que nós temos uma array A que está ordenada de [0] até [n-2] e precisamos inserir [n-1] de modo que a array continue ordenada
                - Isso é feito percorrendo os elementos da array da direita pra esquerda até achar um elemento que seja menor ou igual à A[n-1]
                    - Quando acharmos este elemento, fazemos um ‘Insert’ no índice deste elemento que encontramos e adicionamos um
            - Exemplo de algoritmo para solucionar o problema
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2010.png)
                
                - O único parâmetro a array A
                - 1ª linha
                    - Na primeira linha fazemos um for de i ← 1 até n - 1
                - 2ª linha
                    - Na segunda linha, criamos a variável auxiliar v que guada o valor de A[i] e criamos uma variável auxiliar de índice j e atribuímos à j o valor de i - 1 (inicialmente j é 0)
                - 3ª linha
                    - Na terceira linha, criamos um while que tem as condições de que j seja maior ou igual à 0 e que A[j] seja maior que v (que recebeu A[i])
                - 4ª linha
                    - Na quarta linha, se o código entrou nesta linha então quer dizer que as condições do while estão verdadeiras
                        - Enquanto a condição é True, o valor de A[j + 1] recebe o valor de A[j] e j recebe o valor dele mesmo menos 1
                            - Isso faz com que eventualmente j seja igual à 0 ou que A[j] seja menor ou igual que v (A[i])
                            - Quando esta condição é True, os elementos de a partir j até o início da array são colocados um índice a mais na direita
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2011.png)
                                
                                - Neste caso, por exemplo; v = A[i] = 29 e j = i - 1 = 3
                                - Quando entra no while, j ≥ 0 e A[j] = 90 > 29
                                    - Logo, isso faz com que A[j + 1] receba o valor de 90 e A[j] também é 90; além de decrescer o j
                                - No próximo loop, j ≥ 0 e A[j] = 89 > 29
                                    - Logo, A[j + 1] que era 90 agora recebe o valor de 89 e A[j] continua sendo 89 e assim por diante; até que a array fique ordenada de 0 até i
                        - Se a condição é False, ou seja, o elemento de v que guarda A[i] for maior que j; então não entra no while e nada acontece pois isso quer dizer que aquela parte da array já está ordenada
                - 5ª linha
                    - Na quinta linha atribuímos o valor de A[j + 1] à v
                        - Colocamos mais um pois fazemos insert no índice ao lado do elemento menor que o elemento atual
                            - Caso o elemento atual seja o menor, então j = -1 por causa do while e quando fazemos j + 1 o elemento é inserido no índice 0
                        - Caso a condição do while seja False, o j + 1 serve para que nada aconteça; pois j + 1 = i; logo, A[j + 1] = v = A[i]
- Divide and conquer
    - São algoritmos que fazem a partição de um problema em vários subproblemas do mesmo tipo
        - O problema é dividido por b subproblemas de tamanho n/b com a deles tendo de ser resolvidas
        - Estes problemas são resolvidos tipicamente recursivamente
        - Se necessário, as soluções dos subproblemas são combinadas
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2012.png)
        
    - Tipos
        - Exemplo: aplicação para problemas de sorting uma array de N elementos
        - Merge sort
            - No Merge sort, dividimos a array de N elementos em duas de A[0, …, n/2 -1] e A[n/2, …, n-1] (de acordo com as posições) e depois dividimos de novo até chegar em um tamanho unitário ordenando cada subarray recursivamente e depois “Merge” (junta, combina) as subarrays no final
            - É um método bem eficiente mas gasta memória extra por causa das subarrays
            - Divisão imediata e conquista não imediata (o custo é unir as subarrays)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2013.png)
            
            - Exemplo de algoritmo para solucionar o problema
                - Exemplo 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2014.png)
                    
                    - Essa função recebe a array A[0, …, n-1]; l que é o primeiro índice (na primeira vez é 0) e r que é o último índice (na primeira vez é n-1)
                    - 1ª linha
                        - Primeiro comparamos se já chegamos em um array de tamanho unitário, caso contrário entra dentro do bloco
                    - 2ª linha
                        - m recebe o valor do índice do meio, calculado pela função piso de (l + r)/2
                    - 3ª linha
                        - Fazendo uso da recursão, chamamos novamente a função Mergesort da array mas agora para dois novos intervalos; que são de l (início) até m (meio) e outro intervalo de m + 1 (meio mais um) até r (final)
                            - Essa recursão se repete até que a subarray seja de valor unitário
                        - Com isso, quando o código voltar das chamadas recursivas; o intervalo de l até m e o intervalo de m + 1 até r estarão ordenados e a função de Merge de l até r é chamada
                    - Os valores de l e r mudam de acordo que entram na chamada recursiva, pois as subarrays vão ficando de valor unitário e vão se ordenando à medida que vão voltando da chamada recursiva
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2015.png)
                    
                    - 1ª linha
                        - Na primeira linha dessa função temos um for i ← l to r do temp[i] ← A[i]
                            - Isso significa que o i recebe o valor de l (índice do limitante esquerdo) e vai até r (índice do limitante direito)
                                - E este for faz com que uma (sub)array temporária temp seja criada e cada índice A vire também de temp
                    - 2ª linha
                        - Na segunda linha, criamos uma variável m que recebe o valor da função piso de (l + r)/2; basicamente o meio da (sub)array
                    - 3ª linha
                        - Na terceira linha, criamos mais dois índices que são i1 (recebe o valor de l) e i2 (recebe o valor de m (meio) mais 1)
                    - 4ª linha
                        - Na quarta linha criamos um outro for que vai de curr (variável auxiliar que recebe o valor de l) até r e possui 4 condições que estas vão ordenar a nossa array A
                    - 5ª linha
                        - Na quinta linha, a condição é de que se i1 = m + 1 (ou seja, i1 já chegou no meio da array + 1 (ou seja, todos os elementos à esquerda do meio já estão ordenados)); caso seja True, então A[curr (que recebe o valor de l)] recebe o valor de A[i2++] (pois como i2 = m + 1; logo precisa incrementar mais uma unidade, por isso i2++)
                    - 6ª linha
                        - Na sexta linha, a condição é de que se i2 > r (ou seja, se o índice i2 já chegou no final da (sub)array); então A[curr] recebe o valor de temp[i1++] pois todos os elementos à direita do meio já estão ordenados
                    - 7ª e 8ª linha
                        - Nas linhas 7 e 8, o código checa a condição de que temp[i1] =< temp[i2]; ou seja esta condição (ou a condição da linha 9) seriam as primeiras condições a serem utilizadas pois as condições acima são para checar se o código já ordenou boa parte da array A
                            - Esta condição significa dizer se o valor do fragmento à esquerda é menor que o valor do fragmento à direita
                            - Se o código entrar na condição, então A[curr] recebe o valor de A[i1++] pois o valor o fragmento à esquerda é menor
                    - 9ª linha
                        - Na linha 9, a condição implícita que está checando é se temp[i2] < temp[i1]; ou seja, se o valor do fragmento à direita é menor que o valor do fragmento à esquerda
                            - Se o código entrar na condição, então A[curr] recebe o valor de temp[i2++] pois o valor do fragmento à direita é menor
        - Quick sort
            - Ao contrário do Merge sort que divide os problemas baseados na posição, o Quick sort divide estes problemas baseados no valor
            - Para isso, escolhemos um pivô s por meio de uma partição e movemos os elementos menores que o pivô para a esquerda e movemos os elementos maiores que o pivô para a direita (se existir um elemento igual ao pivô ele fica ou na direita ou na esquerda)
            - Divisão não imediata (por causa da partição) e conquista imediata
            - Exemplo de algoritmo para solucionar o problema
                - Exemplo 1
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2016.png)
                    
                    - 1ª linha
                        - Na primeira linha, há um condição de se o limitante esquerdo é menor que o direito; se a condição for False então a array tem tamanho 1 e por isso já está ordenada
                    - 2ª linha
                        - Na segunda linha, o código entrou nela pois há mais de um elemento na array, criamos uma variável de pivô s que recebe o valor do particionamento da array A e dos limitantes esquerdo e direito
                            - O s seria um elemento que já está na sua posição correta
                    - 3ª e 4ª linha
                        - São linhas de chamada recursiva, mas uma é para os elementos à esquerda de s e a outra é para os elementos à direita de s
                    - Exemplos de partição
                        - Hoare partition
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2017.png)
                            
                            - 1ª, 2ª e 3ª linha
                                - Uma variável de pivô p é criada e recebe o valor de A[l] (elemento mais à esquerda do array no intervalo em que queremos particionar), além da criação das variáveis de índice i = l (vai caminhar da esquerda para a direita) e j = r + 1 (j inicialmente é um índice ‘fora’ do range da array pois dessa forma o código consegue percorrer o último índice (r) na linha 9; vai percorrer da direita para a esquerda)
                            - 4ª e 12ª linha
                                - É criado um laço de repetição repeat-until, neste laço antes de checar as condições primeiro o código lê o que está escrito dentro do escopo e só depois checa se a condição já foi alcançada
                                    - Neste caso, o repeat vai até que i seja maior ou igual à j
                            - 5ª, 6ª e 7ª linha
                                - É criado mais um repeat-until, dessa vez o laço acontece até que A[i] seja ≥ à que p (A[l]) ou até que i seja ≥ r
                                    - Caso A[i] ≥ p = A[l], isso significa que programa achou uma posição i na qual A[i] é maior ou igual à p, isso significa que todas as posições à esquerda de i são de fato menores que o pivô p
                                    - Caso o programa ache que i ≥ r, significa dizer que todas as posições indexadas por i de l até r (incluindo r pois l já é o índice de p) já são menores que p
                                    - Até quando a condição não for True, i é incrementado em uma unidade
                                    - i indexa a posição do primeiro elemento da esquerda pra direita que é maior ou igual ao pivô
                            - 8ª, 9ª e 10ª linha
                                - É criado mais um repeat-until, dessa vez o laço acontece até que A[j] seja menor ou igual à que p (A[l]), à medida que o repeat continua estamos certificando que os elementos à direita do pivô são maiores que ele até encontre algum elemento que é de fato maior que p ou até que chegue no próprio índice de p, que no caso é l (nesse caso podemos afirmar que p é o menor valor da array e i certamente é o primeiro índice desta array)
                                    - j indexa a posição do primeiro elemento da direita pra esquerda que é menor ou igual ao pivô
                            - 11ª linha
                                - É feito uma troca entre A[i] e A[j]
                                    - A ideia é de que o elemento que está indexado em i (parte esquerda) é maior que ou igual que o pivô e o elemento indexado em j (parte direita) é menor ou igual que o pivô; logo, é preciso trocá-los de posição a fim de ordenar a array pois com certeza A[i] ≥ A[j] (e se for igual não tem problema em realizar a troca)
                            - 13ª linha
                                - Após a condição de parada ser verdadeira, fazemos mais um swap de A[i] com A[j]
                                    - Isso acontece pois no penúltimo swap da linha 11, o elemento A[j] é realmente menor que o elemento A[i]; porém, na última vez em que o swap é realizado nós estamos repetindo o swap anterior (o penúltimo), logo esse swap não deveria acontecer
                                        - Isso acontece pois quando i cruza o j (i ≥ j) os elementos que estão indexados A[i] e A[j] são iguais no penúltimo e no último swap; logo no penúltimo swap eles trocam de lugar pois A[j] é menor que A[i] (correto, pois queremos ordenar) mas no último swap acontece  isso de novo, então os elementos voltam ‘aos lugares originais’
                                            - Por isso, fazendo novamente um swap na linha 13 faz com que a ordenação na array continue
                            - 14ª linha
                                - Nesta linha acontece novamente mais um swap, mas agora entre A[l] (pivô p) e A[j]
                                    - Realizamos esse swap pois como verificado anteriormente com os laços de repeat until, temos certeza de que o elemento indexado por j é menor que p
                            - 15ª linha
                                - O código retorna a posição final do pivô (a sua posição correta considerando todos os elementos da array) que está indexada por j, já que ocorreu o swap entre l e j
                                    - Esse return é necessário pois a função de QuickSort() vai utilizar a posição do pivô para realizar a recursão e ordenar a array inteira
                                        - A posição é guardada pela variável s na função de QuickSort() e após a variável receber um valor, acontece uma recursão mas agora entre o limitante esquerdo e a posição à esquerda do pivô (Quicksort(A, l, s-1)) e outra recursão entre a posição à direita do pivô e o limitante direito (QuickSort(A, s+1, r))
                            - Exemplo de entrada para analisar o funcionamento do código
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2018.png)
                                
                                - Linha 1 à 3
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2019.png)
                                
                                - Primeiro loop do repeat-until principal até a linha 10 (a condição de parada não foi verdadeira)
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2020.png)
                                
                                - Linha 11, acontece o swap entre 0 e 7 (ficaram ordenados)
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2021.png)
                                
                                - Segundo loop do repeat-until principal, acontece de novo um swap entre 0 e 7 (swap que não deveria ter acontecido) e a condição de parada é True
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2022.png)
                                
                                - Linha 13, desfaz o último swap
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2023.png)
                                
                                - Linha 14, faz o swap entre p e A[j] (0 e 5), ambos ficam em posições ordenadas pois na esquerda do pivô só há elementos menores ou iguas à ele e na sua direita há elementos maiores ou iguais à ele
                                    - Retorna a posição 3, pois return j
                                - E assim por diante…
                        - Lobuto partition
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2024.png)
                            
- Transform and conquer

---

## Efficiency

- Depende do running time e memory space que dependem do input size
- Running time
- Memory space
    - Quantidade de memória do algoritmo (memória do input + memória do output)
- Units for measuring running time
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2025.png)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2026.png)
    
- Notações
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2027.png)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2028.png)
    
- Tipos de eficiências
    - Worst-case
    - Average-case
    - Best-case
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2029.png)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2030.png)
    
- Sequential search vs BS search
    - Sequential search efficiency = n
    - BS search efficiency = n log n (ordering the array) + log n (BS)
    - For one search or few searchs, sequential search is the best to use; otherwise it’s better to use BS search
- Comparando algoritmos de ordenação
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2031.png)
    

---

## Tipos abstratos de dados e estruturas de dados

- Type
    - É uma coleção de valores; no caso do bool, a sua coleção de valores consiste em true e false
- Data item
    - É uma peça de informação na qual o valor vêm do type
    - Um data item é um member do type
- Data type
    - É o tipo de dado juntamente com a coleção de operações que manipulam o type
        - Por exemplo, a operação de somar no type int
- Abstract data type (ADT)
    - É basicamente o data type como um componente de software (e não de hardware)
- Data structure
    - É a implementação do ADT
        - Em linguagens orientadas à objeto, por exemplo, o ADT juntamente com sua implementação é chamado de class e cada operação associada com o ADT é implementada pelos methods
        - Um object é uma instância de uma classe, ou seja, algo criado e que ocupa armazenamento durante a execução do programa
        - Além disso, as variáveis que definem o espaço requerido por um data item são referidos como data members
    
    ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2032.png)
    
- Tipos de ADT
    - Listas
        - É uma finita e ordenada sequência de itens de dado conhecido como elements
            - Ordenada significa que cada elemento tem uma posição dentro da lista
                - Cada elemento possui um data type
                - Pode ter listas com mais de um data type dentro dela
        - O conceito mais importante numa lista é a posição, ter a percepção do primeiro elemento da lista, segundo elemento e etc.
            - Quando a lista está vazia significa que não há elementos dentro dela
        - Length (tamanho) - número de elementos; Head (cabeça) - começo da lista; Tail (cauda) - final da lista
        - Os elementos dentro da listas podem estar sortidos (sorted lists), com elementos em uma ordem disposta especificamente em ordem de valor
        - Quando vamos criar a nossa classe de lista, devemos criar um “tipo” E que serve como um espaço reservado para qualquer tipo de elemento (exemplo, se tivermos uma lista com char e int, se utilizarmos apenas char ou int daria um problema; então criamos E)
        - Operações básicas
            - Para criar os nossos métodos, precisamos de ter conhecimento acerca da posição inicial
            - Métodos
                - Clear
                    - Deixa a lista vazia
                - Insert
                    - Inserir um elemento na posição atual
                - Append
                    - Adicionar um elemento ao final da lista
                - Remove
                    - Remove o elemento na posição atual
                - moveToStart
                    - A posição atual passa a ser o início da lista
                - moveToEnd
                    - A posição atual passa a ser o fim da lista
                - prev
                    - A nova posição passa a ser a posição à esquerda da posição atual (-1 no index)
                - next
                    - A nova posição passa a ser a posição à direita da posição atual (+1 no index)
                - length
                    - O tamanho atual da lista
                - currPos
                    - Checa a posição atual
                - moveToPos
                    - A nova posição vai ser a posição que escolheremos
                - getValue
                    - Pegamos o valor da posição atual
            - Podemos criar mais métodos a depender do que queremos fazer
        - Abordagens
            - Listas baseadas em array (Array-Based List)
                - Os elementos são armazenados em locais de memória unidos, formando uma array
                - Cada elemento possui um índice fixo que corresponde à posição deles na array
                - Exemplo
                    - C
                    - C++
                        
                        ```cpp
                        #include <iostream>
                        
                        using namespace std;
                        #define DEFAULT_SIZE = 5
                        
                        // esse tipo E é um tipo arbitrário, podemos tirar o E e substituir
                        // por int por exemplo, e tiramos o template
                        template <typename E>
                        class ArrList { 
                        private:
                            int maxSize;
                            int listSize;
                            int curr;
                            E *listArray;
                        public:
                            explicit ArrList(int size = DEFAULT_SIZE) {
                                maxSize = size;
                                listSize = curr = 0;
                                listArray = new E[maxSize];
                        	    }
                        
                            void clear() {
                                delete[] listArray;
                                listSize = curr = 0;
                                listArray = new E[maxSize];
                            }
                            
                            void insert(E value) {
                                if (listSize >= maxSize) {
                                    cerr << "Error! List is full";
                                    exit(1);
                                }
                                
                                int i = listSize;
                        
                                while (i > curr) {
                                    listArray[i] = listArray[i - 1];
                                    i--;
                                }
                                
                                listArray[curr] = value;
                                listSize++;
                            }
                        
                            void moveToStart() {
                                curr = 0;
                            }
                        
                            void moveToEnd() {
                                curr = listSize;
                            }
                        
                            void prev() {
                                if (curr != 0) {
                                    curr--;
                                }
                            }
                        
                            void next() {
                                if (curr < listSize){
                                    curr++;
                                }
                            }
                        
                            void append(E it) {
                                if (listSize < maxSize) {
                                    cerr << "Error! List is full";
                                    exit(1);
                                }
                                
                                listArray[listSize++] = it;
                            }
                        
                            E remove() {
                                if (curr < 0 || curr >= listSize) {
                                    return NULL;
                                }
                        
                                E it = listArray[curr];
                                E i = curr;
                        
                                while (i < listSize - 1) {
                                    listArray[i] = listArray[i + 1];
                                    i++;
                                }
                        
                                listSize--;
                                return it;
                            }
                        
                            int length() {
                                return listSize;
                            }
                        
                            int currPos() {
                                return curr;
                            }
                        
                            void moveToPos(int pos) {
                                if (pos >= 0 && pos <= listSize) {
                                    curr = pos;
                                }
                            }
                        
                            E getValue() {
                                if (curr >= 0 && curr <= listSize) {
                                    return listArray[curr];
                                }
                            }
                        
                            ~ArrList() {
                                delete[] listArray;
                            }
                        };
                        
                        ```
                        
            - Listas encadeadas (Linked List)
                - Utiliza ponteiros e alocação de memória dinâmica
                - Uma lista encadeada é feita com uma série de objetos chamadas de nós da lista
                    - É uma boa prática fazer uma classe de nó separada
                    - Os objetos dentro dessa classe contém um local de elemento para guardar o valor desse elemento e um campo next para armazenar um ponteiro para o próximo nó na lista (porque para cada nó há um ponteiro para o próximo nó da lista)
                - Na classe da lista, haverá três ponteiros, que apontam para o começo da lista (head), final da lista (tail) e para a posição do elemento atual (curr)
                    - Não precisamos declarar uma array de tamanho fixo quando a lista é criada, logo o parâmetro do tamanho é dispensável para listas encadeadas
                    
                    ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2033.png)
                    
                - Exemplo (fazer exemplo)
                    - C
                        
                        
                    - C++
                        
                        ```cpp
                        
                        ```
                        
                - Doubly Linked Lists
                    
                    ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2034.png)
                    
                - Circular Linked Lists
                    
                    ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2035.png)
                    
            - Array-based list vs Linked list
                - As listas baseadas em array tem a desvantagem de que o tamanho delas deve ser predeterminada antes que a array seja alocada
                    - Além disso, elas só cresem até o tamanho pré estabelecido
                - As listas baseadas em array tem a vantagem de que não há desperdício de espaço para um elemento
                    - As listas encadeadas precisam de criar um ponteiro extra para cada nó da lista, o que pode ser uma quantidade considerável de armazenamento
                - No geral, é melhor utilizar listas encadeadas mas há casos em que listas baseadas em array são melhores
    - Pilhas
        - É uma estrutura semelhante à uma lista, na qual os elementos são inseridos ou removidos apenas de uma das cabeças (head ou tail, LIFO (Last in First out, the element that is inserted last comes out first) or FILO (First in Last out, the element that is insert first comes out last))
            - Geralmente se usa LIFO
            - Basicamente podemos imaginar esse conceito como uma pilha de pratos, na qual o último prato a ser colocado é o primeiro a ser removido
                - Essa restrição faz com que pilhas sejam menos flexíveis que listas, mas não tira a eficiência da pilha
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2036.png)
            
        - Operações básicas
            - clear
                - Limpa a pilha
            - push
                - Adiciona um elemento no topo da pilha
            - pop
                - Remove o elemento do topo da pilha
            - topValue
                - Retorna o elemento que está no topo da pilha
            - length
                - Retorna a altura da pilha
        - Abordagens
            - Pilhas baseadas em array
                - Nessa implementação, listArray deve ser criada com um tamanho fixo quando a pilha for criada
                - C
                - C++
                    
                    ```cpp
                    #include <iostream>
                    
                    using namespace std;
                    
                    #define MAX 100;
                    
                    // esse tipo E é um tipo arbitrário, podemos tirar o E e substituir
                    // por int por exemplo, e tiramos o template
                    template <typename E>
                    class ArrStack {
                        int top;
                    public:
                        int stackArray[MAX];
                    
                        ArrStack() {
                            top = -1;
                        }
                    
                        bool push(int x) {
                            if (top >= (MAX - 1)) {
                                cout << "Stack Overflow";
                                return false;
                            }
                            
                            else {
                                stackArray[++top] = x;
                                cout << x << " pushed into stack\n";
                                return true;
                            }
                        }
                    
                        int pop() {
                            if (top < 0) {
                                cout << "Stack Underflow";
                                return 0;
                            }
                    
                            else {
                                int x = stackArray[top--];
                                return x;
                            }
                        }
                    
                        int topValue() {
                            if (top < 0) {
                                cout << "Stack is Empty";
                                return 0;
                            }
                    
                            else {
                                int x = stackArray[top];
                                return x;
                            }
                        }
                    
                        bool isEmpty() {
                            return (top < 0);
                        }
                    
                        int length() {
                            return (top + 1);
                        }
                    };
                    ```
                    
            - Pilhas encadeadas
                - Como estamos lidando apenas com o elemento que está no topo da pilha, não utilizaremos os três ponteiros; apenas precisamos de um ponteiro que aponte para o elemento do topo da pilha
                    - Possui uma lógica semelhante à listas encadeadas
                
                ```c
                
                ```
                
            - Ambas as abordagens são eficientes
            - C
            - C++
    - FIlas
        - Assim como as pilhas, as filas são estruturas semelhantes à uma lista que fornece acesso restrito aos seus elementos
            - A diferença é que os elemento são inseridos no final da fila (enqueue operation) e são removidos no começo da fila (dequeue operation) (FIFO, First in, First out)
        
        ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2037.png)
        
        - Operações
            - clear
                - Vai limpar a fila
            - enqueue
                - Inserir um novo elemento no final da fila
            - dequeue
                - Remover o elemento do começo da fila
            - frontValue
                - Retorna o elemento do começo da fila sem removê-lo
            - rear
                - Retorna o elemento do final da fila sem removê-lo
            - length
                - Retorna o tamanho da fila
        - Abordagens
            - Filas baseadas em array
                - C
                - C++
                    
                    ```c
                    #include <iostream>
                    
                    using namespace std;
                    
                    #define MAX 100;
                    
                    // esse tipo E é um tipo arbitrário, podemos tirar o E e substituir
                    // por int por exemplo, e tiramos o template
                    template <typename E>
                    class ArrQueue {
                    private:
                       int front;
                       int rear;
                       E *queuearray;
                    public:
                        ArrQueue() {
                            front = rear = -1;
                            queuearray = new E[MAX]
                        }
                    
                        bool isEmpty() {
                            return front == rear;
                        }
                    
                        bool isFull() {
                            return rear == MAX - 1;
                        }
                    
                        void enqueue(E value) {
                            if (isFull()) {
                                cout << "Queue is full!" << endl;
                                return;
                            }
                    
                            rear++;
                            queuearray[rear] = value;
                    
                            if (front == -1) {
                                front = rear;
                            }
                            
                            cout << value << "enqueued" << endl;
                        }
                    
                        E dequeue() {
                            if (isEmpty()) {
                                cout << "Queue is empty!" << endl;
                                return NULL;
                            }
                            
                            E item = queuearray[front];
                            front++;
                    
                            if (front == rear) {
                                front = rear = -1;
                            }
                    
                            return item;
                        }
                    
                        E frontValue() {
                            if (isEmpty()) {
                                cout << "There is no front value" << endl;
                                return NULL;
                            }
                    
                            return queuearray[front];
                        }
                    
                        E rearValue() {
                            if (isEmpty()) {
                                cout << "There is no rear value" << endl;
                                return NULL;
                            }
                    
                            return queuearray[rear];
                        }
                    };
                    
                    ```
                    
            - Filas encadeadas
                - rear e front são ponteiros
                - C
                - C++
                    
                    ```c
                    
                    ```
                    

---

## Sets

- Definição
    - Um set pode ser descrito como como uma coleção de elementos desordenados
        - Um set pode ser definido de forma explícita, listando os elementos, ou especificando uma propriedade de todos os elementos do set
- Implementação
    - Pode ser implementado de duas formas
        - A primeira forma considera apenas sets que são subsets de um grande set U (universal set)
            - Se o set possui n elementos, então cada subset S de U pode ser representado por um bit string de tamanho n (bit vector); na qual se o i-th elemento de U pertence à S é igual à 1
                - Exemplo: U = {1, 2, 3, 4, 5}; S = {2, 3, 5}; então o bit vector de S [e 01101
        - A segunda forma é utilizando é usando estruturas de listas para indicar os elementos do set
            - É a forma mais comum de utilizar
            - Importante saber as diferenças entre sets e listas
                - Sets não admitem elementos iguais dentro dele, já a lista permite
                    - Essa diferença é contornado pela introdução de multiset ou bag (coleção não ordenada de items que não são necessariamente distintos)
                - Outra coisa, sets são coleções não ordenadas de elementos, mas mudando a ordem dos elementos não causa mudanças no set
                    - Por outro lado, se mudarmos a posição de elementos em uma lista isso causa mudanças na lista
            - Na computação, as operações mais utilizadas que precisamos utilizar em sets são: encontrar um item pedido, adicionar um novo item e deletar um item da coleção
                - Uma estrutura de dados que implementa todas essas operações é chamada de dicionário
                    - Por isso, uma implementação eficiente de um dicionário precisa encontrar um compromisso entre a eficiência da pesquisa e a eficiência das outras duas operações
                        - Algumas maneiras de fazer isso é usando arrays (não muito indicado), listas encadeadas ou hashing e pesquisa balanceada de árvores
    - Várias aplicações de computação requer partição dinâmica de um set de n-elementos em uma coleção de subsets disjuntos
        - Depois de ser inicializada como uma coleção de n subsets de elementos 1, a coleção está sujeita a uma sequência de operações mistas de união e busca
            - Problema de união de sets
    - ADT de um dicionário
        
        ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2038.png)
        

---

## Trees

- Uma árvore (mais precisamente uma árvore livre) é um grafo conectado acíclico
    - Um grafo acíclico mas não necessariamente conectado é chamado de floresta
    
    ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2039.png)
    
- Árvores enraizadas
    - É basicamente uma árvore que possui uma raiz (nível 0) e possui no máximo dois filhos (nível 1) e cada filho dessa raiz possui no máximo mais dois filhos (nível 2) e assim por diante
    - Muito útil para implementar dicionários, acessar data sets muito largos e etc.
    - Nomenclatura
        - Root (Raiz): é o vértice originário da árvore
        - Parent (Pai): é um vértice que possui filhos
        - Child (Filho): é um vértice que vêm de um pai
        - Siblings (Irmãos): vértices que vêm do mesmo pai
        - Leaf (Folha): um vértice que não possui filhos
        - Parental (Parente): é um vértice que possui pelo menos um filho
        - Descendants (Descendentes): Todos os vértices que se originaram de um vértice v
        - Depth (Profundidade): a profundidade de um vértice v é basicamente quantos vértices ele precisa passar para chegar na raiz
        - Heigth (Altura): o maior tamanho entre uma folha e a raiz
- Árvores ordenadas
    - É uma árvore enraizada onde todo vértice está ordenado
    - Árvore binária
        - Uma árvore em que cada vértice não tem mais que dois filhos e cada filho é designado como ou filho à esquerda do pai ou filho à direita do pai; além disso, ela pode ser uma árvore vazia
- Binary search tree (BST) (Árvore de busca binária)
    - É uma árvore binária ordenada em que cada vértice representa um número
    - Todo filho à esquerda é um número menor que o número do pai e todo filho à direita é um número maior ou igual ao número do pai
        - A raiz é a única que não é filho à esquerda ou à direita pois não possui pais, logo a árvore é baseada no valor da raiz
        - Para implementar, é preciso de ponteiros em todos os vértices
    - Exemplo
        
        ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2040.png)
        
        ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2041.png)
        
- Traversals (Travesias)
    - Percorrer todos os elementos de um grafo
    - Pre-order
        - Percorremos primeiro a raiz e depois percorremos o filho à esquerda dela
            - Após isso, percorremos o filho à esquerda dos filhos da esquerda
                - Caso algum filho à esquerda possua um filho à direita, ele será percorrida apenas quando o código percorrer o último filho à esquerda de forma de recursiva
        - Após isso, o filho à direita da raiz é percorrido seguindo a mesma lógica acima
        - Exemplo
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2042.png)
            
            - Pre-order: 37 (raiz), 24 (filho à esquerda da raiz), 7 (neto à esquerda à esquerda da raiz), 2 (bisneto à esquerda à esquerda à esquerda da raiz), 32 (neto à esquerda à direita da raiz), 42 (filho à direita da raiz), 40 (neto à direita à esquerda da raiz), 42 (neto à direita à direita da raiz), 120 (bisneto à direita à direita da raiz)
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2043.png)
            
            - Pre-order: 5, 3, 2, 1, 4, 7, 6, 8, 7, 12, 9, 14, 23, 21, 18, 56
    - In-order
        - Percorremos primeiro o último dos filhos à esquerda e vamos voltando recursivamente dando prioridade para os filhos à esquerda e depois aos filhos à direita (desde o primeiro à direita até o último) antes de chegar à raiz
        - Após percorrer todo o lado esquerdo da raiz, percorremos a raiz e logo após percorremos o lado direito da raiz dando prioridade aos filhos à esquerda de cada vértice (percorremos eles e depois percorremos o próprio vértice)
        - Vendo à risca, é basicamente uma ordem não decrescente
        - Exemplo
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2044.png)
            
            - In-order: 2, 7, 24, 32, 37, 40, 42, 42, 120
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2045.png)
            
            - In-order: 1, 2, 3, 4 (esquerda da raiz), 5, 6, 7, 7, 8, 9, 12, 14, 18, 21, 23, 56
    - Post-order
        - Primeiro percorremos o lado esquerdo da raiz, depois o lado direito e por fim percorremos a raiz
            - Ao percorrer o lado esquerdo, percorremos o último filho à esquerda de todos e depois percorremos o seu irmão, caso ele tenha algum filho à esquerda então antes percorremos ele e caso tenha um filho à direita percorremos ele antes também; a lógica prevalece para o lado direito
        - Exemplo
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2046.png)
            
            - Post-order: 2, 7, 32, 24, 40, 120, 42, 42, 37
            
            ![Untitled](../../assets/faculdade/periodo3/estruturas-de-dados-orientadas-a-objetos/Untitled%2047.png)
            
            - Post-order: 1, 2, 4, 3, 6, 7, 9, 18, 21, 56, 23, 14, 12, 8, 7, 5
- Balanced search tree (Árvore de busca balanceada)
    - Uma árvore de busca balanceada nada mais é que o equílibrio entre os lados esquerdo e direito da raiz a medida em que novos elementos são adicionados, basicamente uma BST balanceada
    - AVL
        - A AVL possui uma proposta de tornar uma árvore não balanceada em uma árvore balanceada por meio de um auto-balanceamento de modo que a diferença de altura entre os lados esquerdo e direito de cada nó nunca seja maior que 1
            - Essa diferença é chamada de fator de balanceamento, caso o nó esteja balanceado a diferença deverá ser 0, -1 ou 1; caso seja diferente desses valores é necessário realizar uma rotação
            - OBS: o tamanho de uma árvore vazia é -1
            - Essas rotações são feitas a fim de melhorar a eficiência temporal de busca, inserção e etc.
        - Rotações
            - A rotação é o macanismo da AVL para balancear a árvore
            - L-rotation
                - Rotação simples para a esquerda
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2048.png)
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2049.png)
                
            - R-rotation
                - Rotação simples para a direita
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2050.png)
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2051.png)
                
            - LR-rotation
                - Rotação dupla para a esquerda e depois para a direita
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2052.png)
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2053.png)
                
            - RL-rotation
                - Rotação dupla para a direta e depois para a esquerda
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2054.png)
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2055.png)
                
            - Toda vez que fazemos essas rotações, nós temos que atualizar as alturas dos nós
        - Exemplo
            - Input de inserir (nessa ordem): 4, 6, 8, 3, 2, 5
            - Inserir 4 e 6
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2056.png)
                
            - Inserir 8
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2057.png)
                
                - Podemos ver que o nó 4 está desbalanceado, pois se subtraímos a altura da subárvore esquerda com a subárvore direita obtemos -2 (-1 da esquerda subtraído de 1 da direita)
                - Como a parte direita da subárvore direita está desbalanceada, devemos fazer uma L-rotation, trocando o 6 de lugar com o 4
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2058.png)
                    
            - Inserir 3
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2059.png)
                
            - Inserir 2
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2060.png)
                
                - Podemos ver que o nó 4 está desbalanceado, pois se subtraímos a altura da subárvore esquerda com a subárvore direita obtemos 2 (1 da esquerda subtraído de -1 da direita)
                - Como a parte esquerda da subárvore esquerda está desbalanceada, devemos fazer uma R-rotation, trocando o 3 de lugar com o 4
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2061.png)
                

---

## Space and time trade-offs

- Melhora da eficiência temporal em detrimento da eficiência espacial
- Abordagens
    - Input enhancement (Aprimoramento de Entrada) (COMPLETAR)
        - Basicamente a ideia é pré-processar a entrada do problema no todo ou em parte e armazenar as informações adicionais obtidas para acelerar e resolver o problema depois
        - Implementações
            - Couting sorted methods
                - Comparison counting sort
                    - Nesse tipo de sort, levamos em consideração a posição dos números em um array count
                        - Essas posições seriam a ordem correta dos números de uma array A de forma não decrescente
                        - Ao final do programa, quando terminamos de guardar todas as devidas posições dos elementos, nós criamos uma nova array que vai receber os números em ordem não decrescente
                    - Algoritmo
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2062.png)
                        
                        - O array count é uma array de tamanho array.len() que guarda a posição correta (de modo que teremos uma array com elementos em ordem não decrescente) de cada elemento da array A; logo, cada elemento i-th da array count representa a correta posição do elemento i-th da array A
                        - S seria a array resultante da ordem não decrescente dos elementos da array A
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2063.png)
                        
                        - Explicando o algoritmo
                            - Inicialmente count vai receber o valor de 0 para cada elemento da array count
                            - Depois, dentro do for, checamos a cada iteração o elemento A[i] (com i = 0 inicialmente e incrementando) e checamos com todos os outros valores à direita de A[i]
                                - Caso A[i] seja maior que A[j], então incrementamos +1 em count[i]
                                - Caso contrário, count[j] vai ser incrementado em +1
                            - No final, todos os elementos de count vão ser os índices corretos dos elementos de A de acordo com a ordem não decrescente deles
                                - Por exemplo, 3 é o índice correto do elemento 62 considerando os outros elementos; 1 é o índice correto do elemento 31 e assim por diante
                - Distribution couting
                    - Nessa implementação, consideramos o menor e maior elemento e outras duas coisas: a frequência de um elemento e o seu valor de distribuição
                        - A frequência seria a quantidade de vezes em que o elemento aparece na array
                        - O valor de distribuição está associado com os índices dos elementos
                            - Primeiro pegamos o menor elemento e atribuímos o valor de 1 à ele, pro segundo elemento pegamos o valor de distribuição do primeiro e somamos com a frequência dele próprio e assim conseguimos o valor de distribuição do segundo elemento; e fazemos assim por diante
                    - Baseando-se na frequência e valor de distribuição de cada elemento da array, nós percorremos A da direita pra esquerda e a cada vez que o elemento é percorrido colocamos o elemento no índice correspondente ao valor de distribuição - 1 na array S, e após isso decrementamos em 1 o valor de distribuição
                    - Algoritmo
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2064.png)
                        
                        - Exemplo
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2065.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2066.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2067.png)
                            
            - Boyer-Moore algorithm for string matching
                - Simplified version by Horspool
    - Prestructuring (COMPLETAR)
        - Explora compensações entre espaço e tempo simplesmente usando espaço extra para facilitar o acesso mais rápido e/ou flexível dos dados
        - Algum processamento é feito antes que um problema em questão seja realmente resolvido, mas, ao contrário da variedade de input enhancement, esse approach lida com acesso de estruturas
        - Implementações
            - Hashing
                - Uma maneira muito eficiente de implementar dicionários
                - Hashing é baseado na ideia de distribuir chaves em uma array de dimensão 1 H[0, …, m-1] chamada de Hash Table (Tabela Hash)
                    - Essas chaves são basicamente os identificadores (ID’s) dos elementos do nosso dicionário
                    - Basicamente estamos mapeando a nossa array
                - Essa distribuição é feito computando para cada chave o valor de uma função pré-definida chamada Hash Function (função que calcula a chave de cada elemento)
                - Essa função retorna um inteiro entre 0 e m - 1 e é chamado de Hash Address (Endereço de Hash)
                - Key types
                    - int
                        - Se as chaves são números não negativos, a nossa Hash Function pode ser do tipo: h(K) = K mod m
                        - Example
                            - Trivial method
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2068.png)
                                
                            - Mid-Square method
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2069.png)
                                
                    - char
                        - Se as chaves são letras do alfabeto podemos definir que as letras estão em uma posição, como o número ASCII, e depois aplicar a mesma função que há para inteiros
                    - string
                        - Se nossas chaves são do tipo inteiro, podemos somar os valores ASCII de cada letra e fazer um mod m
                        - Example
                            - fold
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2070.png)
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2071.png)
                                
                            - sfold
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2072.png)
                                
                - Hash tables
                    - Devem ser fáceis de computar
                    - O tamanho da Hash Table não deve ser excessivamente grande comparado ao número de chaves mas deve ser suficiente para não complementar a eficiência temporal da implementação
                    - A função Hash deve distribuir as chaves entre as posições da tabela de maneira mais uniforme possível
                - Colisions
                    - Fenômeno em que duas ou mais chaves possuem a Hash Function iguais, logo elas estariam na mesma posição da Hash Table
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2073.png)
                        
                    - Logicamente, se escolhermos um tamanho m da Hash Table menor que o número de chaves n iremos ter colisões
                        - Mas essas colisões devem ser esperados mesmo que se considerarmos m bem maior que n
                        - No pior caso, todas as chaves irão ter o valor de Hash Function iguais
                            - Felizmente, com um tamanho apropriado para a Hash Table e uma boa Hash Function, essa situação deve acontecer raramente
                            - Mesmo assim, todo esquema de Hashing deve ter um mecanismo de resolução de colisões
                    - Approachs to solve collisions
                        - Open hashing (Separate Chaining)
                            - In open hashing, keys are stored in linked lists attached to cells of a hash table
                                - Each list contains all the keys hashed to its cell
                                - In other words, each hash address is associated with a linked list
                            - Example
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2074.png)
                                
                                - A = 1 and Z = 26
                                - Sum of all of the letters of each word mod 13
                                - Note that are and soon has the same keys, but are came first so it’s the first cell of 11 and then comes soon
                            - Implementation
                                - ADT dict
                                    
                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2075.png)
                                    
                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2076.png)
                                    
                                - Functions
                                    - Insert
                                        - Insert at the element at index j
                                            - But inside the cell j can be or can’t be sorted
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2077.png)
                                        
                                        - Temporal efficiency (unsorted): Θ(1)
                                        - Temporal efficienct (sorted): Θ(1) + Θ(sorted method)
                                        - Implementation
                                            
                                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2078.png)
                                            
                                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2079.png)
                                            
                                    - Search
                                        - Search the index j element
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2080.png)
                                        
                                        - Temporal efficiency:
                                            
                                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2081.png)
                                            
                                    - Delete
                                        - Delete the element from j
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2082.png)
                                        
                                        - Temporal efficienct similar to the temporal efficiency of searching
                        - Closed hashing (Open addressing)
                            - In closed hashing, keys are sotred in the hash table itself without the use of linked lists
                            - Strategies
                                - Linear probing
                                    - Checks the cell following the one where the collision occurs
                                    - Example
                                        - Hash table
                                            
                                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2083.png)
                                            
                                        - Hash key: key mod 5
                                        - Steps
                                            - First
                                                - If we insert 50, this element will be mapped to slot 0 (50 % 5 == 0)
                                                    
                                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2084.png)
                                                    
                                            - Second
                                                - If we insert 70, this element should be mapped to slot 0 (70 % 5 == 0), but 50 already occupies this slot, so 70 will occupie slot 1
                                                    
                                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2085.png)
                                                    
                                            - Third
                                                - If we insert 76, this element should be mapped to slot 1 (76 % 5 == 1), but 70 already occupies this slot, so 76 will occupie slot 2
                                                    
                                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2086.png)
                                                    
                                            - Fourth
                                                - If we insert 85, this element should be mapped to slot 0 (85 % 5 == 0), but 50 already occupies this slot, so we check then if slot 1 is occupied; which is true, and then 85 will be inserted on the next free slot in this case is slot 3
                                                    
                                                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2087.png)
                                                    
                                    - Functions
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2088.png)
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2089.png)
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2090.png)
                                        
                                    - Is intuitive and easy to implement but suffers a problem known as primary clustering
                                        - This problem occurs because the table is large enough therefore time to get an empty cell or to search for a key is quite large
                                        - This happens mainly because consecutive elements form a group and then it takes a lot of time to find an element or an empty cell which ultimately makes the worst case time complexity of searching, insertion and deletion operations to be O(n), where n is the size of the table
                                        - Basically performance degradation because there is many elements close, so if we insert an element with the same key as one of these elements it can be slow to insert
                                - Pseudo-random probing
                                    - Prevents primary clustering by randoming choosing the slot and checking if this slot is free
                                        - It doesn’t prevents 100% but it has less chance to have primary clustering such as linear probing
                                    - Implementation
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2091.png)
                                        
                                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2092.png)
                                        
                                    - Example
                                        - Hash key = key - (8 * (key // 8))
                                        - Perm = {2, 6, 7, 3, 1, 4, 5}
                                        - Pseudo-random probing function: p(key, i) = Perm[i - 1]
                                            - Perm is an array of length M - 1 (M = length of the hash table), which contains random permutation of numbers from 1 to M - 1
                                        - Values: 2, 4, 8, 16, 32, -12
                                        - Steps
                                            - First, insert 2; key (2) = 2
                                            - Second, insert 4; key(4) = 4
                                            - Third, insert 8; key(8) = 0;
                                            - Fourth, insert 16; key(16) = 0
                                                - Because slot 0 = 8, we need to get another key to 16 by using pseudo-random probing
                                                - Calling the probing
                                                    - key(16) +  p(key, 1) = Perm[0] = 2; but slot 2 already has the element 2, so we call this function again
                                                    - key(16) + p(key, 2) = Perm[1] = 4 = 6; slot 6 is free so we will insert element 16 on this slot
                                            - Fifth, insert 32; key(32) = 0
                                                - Because slot 0 = 8, we need to get another key to 32 by using pseudo-random probing
                                                - Calling the probing
                                                    - key(32) + p(key, 1) = Perm[0] = 2; but slot 2 already has the element 2, so we call this function again
                                                    - key(32) + p(key, 2) = Perm[1] = 4 = 6; but slot 2 already has the element 16, so we call this function again
                                                    - key(32) + p(key, 3) = Perm[2] = 7; slot 7 is free so we will insert element 32 on this slot
                                            - Sixth, insert -12; key(-12) = 4
                                                - Because slot 4 = 4, we need to get another key to -12 by using pseudo-random probing
                                                - Calling the probing
                                                    - key(-12) +(p(key, 1) = Perm[0]) = 6; but slot 6 already has the element 16, so we call this function again
                                                    - key(-12) + (p(key, 2) = Perm[1]) mod 8 = 2; but slot 2 already has the element 2, so we call this function again
                                                    - key(-12) + (p(key, 3) = Perm[2]) mod 8 = 3; slot 3 is free so we will insert element -12 on this slot
                                            - Final hash table
                                                
                                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2093.png)
                                                
                                - Quadratic probing
                                    - When the collision occurs, we look to the i²-th slot in the i-th iteration
                                    - Example
                                        - Hash key = key - (7 * (key // 7)) or simply key % 7
                                        - Quadratic probing function: p(key, i) = (i² + i)/2
                                        - Values: 2, 4, 8, 16, 32, -12
                                        - Steps
                                            - First, insert 2; key (2) = 2
                                            - Second, insert 4; key(4) = 4
                                            - Third, insert 8; key(8) = 0;
                                            - Fourth, insert 16; key(16) = 0
                                                - Because slot 0 = 8, we need to get another key to 16 by using quadractic probing
                                                - Calling the probing
                                                    - key(16) + p(key, 1) = 1; slot 1 is free so we will insert element 16 on this slot
                                            - Fifth, insert 32; key(32) = 0
                                                - Because slot 0 = 8, we need to get another key to 32 by using quadractic probing
                                                - Calling the probing
                                                    - key(32) + p(key, 1) = 1; slot 1, but slot 1 already has the element 16; so we call the probing again
                                                    - key(32) + p(key, 2) = 3; slot 3 is free so we will insert element 32 on this slot
                                            - Sixth, insert -12; key(-12) = 4
                                                - Because slot 4 = 4, we need to get another key to -12 by using quadractic probing
                                                - Calling the probing
                                                    - key(-12) + p(key, 1) = 5; slot 5 is free so we will insert element -12 on this slot
                                            - Final hash table
                                                
                                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2094.png)
                                                
                                    - The problem is that we are not sure if we can probe all locations of our table
                                    - Another problem is called secondary clustering
                                        - Secondary clustering is the tendency for a collision resolution scheme such as quadratic probing to create long runs of filled slots away from the hash position of keys
                                            
                                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2095.png)
                                            
                                - Double hashing
                                    - Prevents primary and secundary clustering
                                    - Basially we will have two hash functions to determine probe sequence
                                        - With these two hash functions we can use in many ways to insert into the hash tables
                        - Open x Closed hashing
                            - Open hashing
                                - Advantages
                                    - One of the simplest methods
                                    - We can add any number to the chain
                                    - Used when we don’t know about the number of elements and the number of keys that can be inserted and deleted
                                - Disadvantages
                                    - Some amount of wastage of space occurs
                                    - The complexity of searching and deleting becomes O(n) in the worst case when the chain becomes long
                                    - The keys in the hash table aren’t evenly distributed
                            - Closed hashing
                                - Provides better cache performance because all data is stored in the same table only
                                - Easy to implement (no pointers involved)
                                - Different strategies to resolve collisions can be adopted as per the use case
            - Indexing with binary trees
    - Dynamic programming (DP)

---

## Heaps

- Pode ser definida como uma árvore binária que obedece duas condições
    - Shape property (Propriedade de forma): é uma árvore binária completa (ou seja os elementos são inseridos na árvore de cima pra baixo e da esquerda para a direita)
    - Parental dominance (Dominância parental): para qualquer nó da heap, esse nó (ou chave) deve ser maior que os seus filhos (max_heap - heap máxima) ou menor que os seus filhos (min_heap heap mínima)
- Utilizada para implementar filas de prioridades
    - Essas filas devem ter uma função de find_max, remove_max e add
- Exemplo
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2096.png)
    
    - A árvore à esquerda é uma heap, a árvore do meio não é uma heap pois não respeita a propriedade de forma e a árvore à direita não é uma heap pois não respeita a dominância parental mínima nem máxima
- A heap pode ser implementada como uma array
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2097.png)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2098.png)
    
    - Nesse caso, consideramos o índice zero da nossa array contendo nenhum elemento e portanto a heap começa a partir do índice 1
    - Por causa da propriedade de forma, dado uma heap de tamanho n; podemos dizer que os nós parentais estão dispostos na array da posição 1 até n//2 e os nós folha (que não tem filhos) estão dispostas na array da posição (n//2 + 1) até n
    - Além disso, os filhos dos nós de 1 ≤ i ≤ n//2 podem ser acessados pelos índices 2i (filho à esquerda) e 2i + 1 (filho à direita) caso esses valores sejam menores que n
        - De forma analóga, podemos acessar o pai de uma folha fazendo i//2
    - Como implementar
        - Existem duas formas de “heapficar” uma array, de como top-down e bottom-up
        - Top-down
            - Utilizado quando nós não sabemos os elementos que vão ser inseridos na heap
            - Os elementos são inseridos um por um e a cada inserção nós fazemos um heapify (heapficação), que nesse caso vai checar se a árvore atual é de fato uma heap caso não seja o heapify vai transformá-la em uma
            - Pior eficiência temporal para cada inserção - O(log n)
            - Pior eficiência temporal para criar a heap - O(n log n)
            - Exemplo
                - Criando uma heap máximo com os inputs: 2, 9, 7, 6, 5, 8, 10
                - Inserindo o 2
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%2099.png)
                    
                    - O processo de heapify não foi necessário
                - Inserindo o 9
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20100.png)
                    
                    - Como queremos uma heap máxima, com o processo de heapify o 9 vai trocar de lugar com o 2 a fim de obter uma heap máxima
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20101.png)
                    
                - Inserindo o 7
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20102.png)
                    
                    - O processo de heapify permaneceu a heap desse estado, pois está uma heap máxima
                - Inserindo o 6
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20103.png)
                    
                    - No processo de heapify, o 6 troca de lugar com o 2
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20104.png)
                    
                - Inserindo o 5
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20105.png)
                    
                    - Como 5 < 6; o processo de heapify não mudou a heap
                - Inserindo o 8
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20106.png)
                    
                    - Após o heapify
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20107.png)
                        
                - Inserindo o 10
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20108.png)
                    
                    - Como 10 > 8, trocamos o 10 no lugar de 8 pelo processo de heapify e como 10 > 9; também realizamos essa troca com o heapify
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20109.png)
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20110.png)
                        
                - Heap final:
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20110.png)
                    
        - Bottom-up
            - Utilizado quando nós sabemos os elementos que vão ser inseridos na heap
            - Os elementos são inseridos de vez e fazemos o heapify (heapficação) do nó mais interno até o nó mais externo da heap
            - Pior eficiência temporal para criar a heap - O(n)
            - Exemplo
                - Criando uma heap máximo com os inputs: 2, 9, 7, 6, 5, 8, 10
                - Heap inicial
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20111.png)
                    
                - Heapify
                    - Como no heapify de bottom-up fazemos do nó (parental) mais interno até o mais externo; fazemos primeiro com o 7
                    - Heapify com o 7
                        - Checamos os filhos do 7 com o próprio 7
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20112.png)
                            
                        - Nesse caso, 7 é menor que ambos os elementos; como 10 é o maior deles, então trocamos ele com o 7
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20113.png)
                            
                    - Heapify com o 9
                        - Como os filhos do 9 são menores que ele, então o processo de heapify não vai alterar a nossa heap
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20114.png)
                            
                    - Heapify com o 2
                        - Como o 2 é menor que ambos os filhos, trocamos o 2 com o maior deles; nesse caso o 10
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20115.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20116.png)
                            
                            - Após realizar a troca, precisamos fazer um heapify para verificar se os novos filhos do 2 são maiores que ele; e nesse caso eles são sim, logo trocamos o 2 com o maior deles, que nesse caso é o 8
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20117.png)
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20118.png)
                                
                - Resultado final
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20119.png)
                    
- Heapsort
    - Um algoritmo de ordenação baseado em heaps
    - Construímos a heap baseada em uma array (construção via bottom-up)
    - Após a construção, fazemos o uso da função remove_max; que vai deletar o maior elemento da heap
        - Fazemos isso n - 1 vezes, e isso vai retornar os elementos da heap de forma decrescente e podemos armazená-los em uma outra estrutura como uma fila ou pilha
        - Exemplo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20120.png)
            

---

## Grafos

- É um conjunto de vértices em um plano na qual alguns desses vértices estão conectados entre si formando arestas (G = ⟨V, E⟩)
- Caso um par de vértices desordenado ⟨u, v⟩ seja igual ao par ⟨v, u⟩ então dizemos que esses vértices são adjacentes e eles estão conectados por uma aresta não direcionada
- Se um par de vértices ⟨u, v⟩ é diferente do par ⟨v, u⟩ dizemos que temos uma aresta direcionada de u (head) para v (tail); ou seja, a aresta sai de u e vai para v
    - Um grafo em que todas as arestas são direcionadas é chamado de grafo direcionado
        - Grafos direcionados são chamados de dígrafos
        - OBS: o livro do Levitin considerado que os grafos não possuam loops (multigrafos)
- Um grafo que possui todos os seus vértices com pelo menos uma aresta é chamado de grafo completo (Notação: K|V|)
- Um grafo com relativamente poucas arestas faltando é chamado de denso
- Um grafo com poucas arestas em relação ao número de vértices é chamado de escasso ou disperso
- Representação algorítmica de grafos
    - Matriz de adjacência
        - Basicamente uma array de array ou vector de vector e etc
        - Essa matriz mostra todas as ligações de dois vértices, podendo ser representada por 0 ou 1 ou por alguma outra chave
            - É interessante possuiu uma matriz de booleanos auxiliar para marcar true ou false caso tenha uma ligação entre dois vértices
    - Lista de adjacência
        - Implementação de linked lists para representar as ligações do grafo
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20121.png)
    
    - Se um grafo é denso, então é mais interessante usar a matriz de adjacência
    - Se um grafo é disperso, é mais interessante o uso de lista de adjacência
- Grafos ponderados
    - É um grafo na qual as arestas possuem um número associado à elas e esse número significa o peso ou o custo de cada aresta
    - Essa implementação de grafos é interessante no quesito de achar o caminho mais curto de um grafo e etc.
    - Esse tipo de grafo pode ser facilmente representado por matrizes e listas de adjacências na qual estes podem conter os pesos das arestas entre dois vértices
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20122.png)
    
- Caminhos e ciclos
    - Um caminho é basicamente uma sequência que vai de um vértice u até um vértice v na qual é uma sequência de vértices adjacentes que começa de u e termina em v
        - Se todos os vértices de um caminho são distintos então o caminho é chamado de simples
    - O tamanho de um caminho é o número total de vértices que pertence à sequência menos 1
    - Um caminho direcionado é uma sequência de vértices na qual cada par de vértices está conectado por uma aresta direcionada pelo vértice listado primeiro e pelo vértice listado depois
    - Um grafo é dito conexo se existir um caminho entre qualquer par de vértices
    - Um caminho que começa e termina no mesmo vértice é chamado de ciclo
        - Se um grafo não possui ciclos então ele é um grafo acíclico, caso contrário ele é cíclico
- Travessias (falta escrever sobre o algoritmo de Khan)
    - Algoritmos de processamento de vértices e arestas de um grafo (podem ser utilizados para processar caminhos)
    - DFS (Depth-First Search)
        - Significa “Busca em profundidade”, esse algoritmo começa em um vértice arbitrário e a cada iteração o algoritmo avança para o próximo vértice (caso tenha mais de um vértice conectado ao primeiro, devemos desempatar, geralmente escolhemos o menor elemento)
            - Esse processo continu até um “beco sem saída”: um vértice que não possua vértices adjacentes não visitados
            - Quando isso acontece, então o algoritmo volta para o vértice anterior e tenta procurar o próximo vértice (caso este vértice em questão possua um empate, caso contrário volta mais uma vez até encontrar um vértice com vértices adjacentes não visitados)
        - No final do algoritmo, é esperado que todos os vértices que consigam ser alcançados pelo vértice inicial escolhido tenha sido alcançado e marcado como visitado
        - Algoritmo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20123.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20124.png)
            
            - Passo a passo
                - 1
                    - Primeiramente atribuímos a todos os vértices do grafo como não visitados
                - 2
                    - Com o DFS já chamado, escolhemos o primeiro vértice (nesse caso, o zero pois ele é o menor) e fazemos o DFS
                    - Como escolhemos o 0 então consideramos ele como visitado
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20125.png)
                    
                - 3
                    - A partir do zero, procuramos qual seriam os vértices conectados à 0, nesse caso só há o 2 então pelo DFS marcamos o 2 como visitado e escolhemos o próximo vértice
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20126.png)
                    
                - 4
                    - Como o vértice atual é o 2, agora procuramos o próximo vértice a visitar; como o 2 se conecta a mais de um vértice, escolhemos o menor deles, no caso o 1 e marcamos ele como visitado
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20127.png)
                    
                - 5
                    - O 1 agora é o vértice atual, procuramos o próximo vértice a visitar, como o 1 se conecta ao 2 e o 5, o próximo vértice seria o 2 pois ele é o menor; porém, ele já foi visitado, então visitamos o vértice 5
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20128.png)
                    
                - 6
                    - O vértice atual é o 5 e ele se conecta à 1, 2, 3 e 4; o próximo seria o 1 mas ele já foi visitado, depois dele é o 2 que também já foi visitado; por fim, o próximo vértice é o 3 que não foi visitado então o algoritmo prossegue com o 3
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20129.png)
                    
                - 7
                    - O vértice atual agora é o 3, ele se conecta aos vértices 2 e 5, o próximo vértice seria o 2 mas ele já foi visitado, o último vértice que tem conexão com o 3 é o 5 mas ele também já foi visitado
                        - Como ambos os vértices que se conectam à 3 foram visitados, então voltamos da chamada recursiva de volta para o vértice 5
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20130.png)
                        
                - 8
                    - O próximo vértice que o 5 tem a chance de visitar é o 4, como ele não foi visitado ainda então visitamos ele
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20131.png)
                    
                - 9
                    - Como todos os vértices já foram visitados, o que vai acontecer é basicamente as voltas recursivas de cada vértice visitado pelo algoritmo
                    - O vértice 4 se conecta ao 0 (visitado) e depois ao 5 (também visitado), então voltamos da chamada recursiva para o vértice visitado anteriormente, que é o 5
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20132.png)
                        
                    - O 5 já não possui mais vértices para visitar então voltamos mais uma vez da chamada recursiva
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20133.png)
                        
                    - O vértice 1 também já chechou todas as suas conexões, então voltamos mais uma vez
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20134.png)
                        
                    - Com o vértice 2, checamos apenas se o vértice 1 estava livre, agora checamos se o vértice 3 foi visitado (o que já ocorreu) e posteriormente checamos se o vértice 5 já foi visitado (também já ocorreu), como estes dois já foram percorridos então voltamos mais uma vez da chamada recursiva
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20135.png)
                        
                    - Por fim, estamos no vértice 0 de novo, além do 2 ele se conecta ao 4 que já foi visitado, então a nossa função acaba por aqui já que voltamos de todas as chamadas recursivas
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20136.png)
                        
    - BFS (Breadth-First Search)
        - Significa “Busca em largura”; esse algoritmo começa em um vértice arbitrário e a cada iteração ele percorre todos os vértices adjacentes e guarda em uma fila de prioridade
            - A partir dessa fila de prioridade, o algoritmo checa o próximo vértice da fila e percorre todos os vértices adjacentes à esse (os que não foram visitados, claro) e adiciona estes na fila de prioridade também
                - A fila de prioridade é baseada nos menores elementos, eles entram primeiro na fila de prioridade
            - E isso continua até que todos os vértices sejam percorridos
        - Algoritmo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20137.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20138.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20139.png)
            
            - Passo a passo
                - 1
                    - O primeiro vértice a ser escolhido é o zero, pois ele é o menor
                        - Marcamos o zero como visitado e adicionamos ele na fila de prioridade e logo em seguida tiramos ele pois já vamos checar seus adjacentes
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20140.png)
                    
                - 2
                    - Ao checar os adjacentes de 0, temos o 2 e 4 que vão ser adicionados na fila de prioridade pois ambos não foram visitados e marcamos estes como visitados
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20141.png)
                        
                - 3
                    - Como o 2 é o primeiro da fila de prioridade, vamos checar os seus adjacentes e adicioná-los na fila caso eles não foram visitados (no caso, o 1, 3 e 5), marcamos estes como visitados e removemos o 2 da fila de prioridade
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20142.png)
                        
                - 4
                    - O próximo da fila de prioridade é o 4, que se conecta ao 0 e ao 5; como o 0 e o 5 foram visitados então apenas removemos o 4 da fila
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20143.png)
                        
                    - O próximo da fila é o 1, que possui apenas vértices adjacentes visitados, então apenas removemos ele da fila também
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20144.png)
                        
                    - O próximo da fila é o 3 que também só possui vértices adjacentes visitados, logo apenas tiramos ele da fila
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20145.png)
                        
                    - O próximo da fila é o 5 que também só possui vértices adjacentes visitados, logo, apenas tiramos ele da fila deixando-a vazia e quebrando o loop do while, acabando assim o algoritmo BFS
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20146.png)
                        
    - Aplicações
        - Topological sorting (Classificação topológica)
            - Essa aplicação utiliza conceito de DFS
            - Seja G um grafo direcionado e acíclico, a classificação topológica baseia-se na ideia de encontrar uma ordem de vértices que satisfazem as relações de dependências (arestas dirigidas que não são ciclos)
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20147.png)
                
                - Neste exemplo, antes de percorremos o J5, precisamos primeiro ter passado por J2 e J4
                - Algoritmo
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20148.png)
                    
                    - OBS: push é o comando da stack para empilhar novos valores
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20149.png)
                    
                    - toposort do grafo do exemplo
            - Algoritmo de Khan
        - Caminho mais curto em grafos que não possui peso nas arestas
            - Essa aplicação utiliza conceito de BFS
            - Devemos começar o BFS a partir do vértice de origem e quando o destino é alcançado paramos a busca (dado que queremos encontrar o menor caminho)
                - Se for necessário reconstruir o caminho, podemos criar uma array auxiliar para guardar os predecessores
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20150.png)
                
                - Dado o grafo, qual um menor caminho entre 0 e 5?
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20151.png)
                    
                    - Vemos que 0 é predecessor (pai) de 2 e 4 e o 2 é predecessor de 1, 3 e 5
                    - Logo, podemos perceber que um menor caminho é 0 → 2 → 5 e o outro seria 0 → 4 → 5
                        - O caminho 0 → 2 → 5 provavelmente seria o menor caminho escolhido, já que 2 é menor que 4
- Algoritmo de Dijkstra
    - Um algoritmo para encontrar o menor caminho entre o vértice v (ponto de partida) e todos os outros vértices que pertencem à um grafo com pesos
        - Isso possui o nome de single-source shortest paths (menor caminho de um vértice de origem para todos os outros do grafo)
    - Este algoritmo não deve ser utilizado em casos em que os grafos com peso possuam pesos negativos
    - É um algoritmo guloso
        - Algoritmo guloso
            - São uma classe de algoritmos que fazem escolhas locais ótimas em cada estágio com a esperança de encontrar uma solução global ótima
            - Toma decisões com base em informações disponíveis no momento, sem reconsiderar essas decisões posteriormente
        - O dijkstra é um algoritmo guloso porque sempre seleciona o nó não visitado com a menor distância conhecida
    - Algoritmo
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20152.png)
        
        - Explicação do algoritmo
            - Parâmetros
                - int s - nó de partida, start
                - int[] D - um array das menores distâncias de s até cada um dos outros nós do grafo
            - Das linhas 1 à 3 temos a inicialização de algumas variáveis
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20153.png)
                
                - Colocamos o valor de infinito como a menor distância de s até todos os outros nós
                - Colocamos “-” em todos os índices do array P (parent, array de nós parentais usado para reconstruir os caminhos; ele guarda a informação de qual vértice se estava antes de se chegar em i)
                - Colocamos todos os nós como não marcados com o setMark
            - Na linha 4 iniciamos de fato o nosso código
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20154.png)
                
                - Fazemos D[s] para dizer que o menor caminho entre o próprio vértice s é 0
                - H é uma heap mínima criada de forma Top-Down e cada elemento desta é uma tripla que possui as informações de: (aonde se estava no caminho imediatamente antes desse vértice, vértice atual, custo acumulado para sair da origem e chegar no vértice indicado pelo elemento do meio da tripla)
            - O resto do código faz o proposto, diz o menor caminho entre s e todos os outros vértices do grafo
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20155.png)
                
        - Exemplo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20156.png)
            
            - Começando o algoritmo pelo vértice A
            - Passo a passo
                - Passo 1
                    - Primeiro inicializamos todos os elementos e colocamos (A, A, 0) na nossa Heap bem como D[s] = 0
                - Passo 2
                    - No primeiro laço de repetição com o vértice A entramos no repeat until apenas uma vez pois s ainda não foi marcadi, e atribuímos à (p, v) = A, A (desconsidera o custo acumulado) e marcamos v como visitado e P[v] = A
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20157.png)
                    
                - Passo 3
                    - w recebe o valor de B
                - Passo 4
                - Passo 5
                - Passo 6
                - Passo 7
                - Passo 8
                - Passo 9
- Algoritmo de Floyd-Warshall
    - Encontra os menores caminhos entre dois nós quaisquer de todos os pares de um grafo
    - Este algoritmo funciona para grafos com peso negativo
    - Não pode ser utilizado em grafos com ciclos negativos
    - Algoritmo
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20158.png)
        
        - Linhas 1 à 5, inicialização das distâncias (Diagonal é 0, se não à aresta entre dois nós então é infinito, caso contrário é o peso da aresta)
        - Exemplo
- Algoritmo de Bellman-Ford
    - Algoritmo utilizado para encontrar o menor caminho entre um vértice de origem e todos os outros vértices de um grafo com peso
        - Esses pesos podem ser negativos
    - Especialmente útil porque pode detectar ciclos de peso negativo
    - Algoritmo
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20159.png)
        
        - Primeiro preenchemos a matrix/lista de distâncias entre a origem e todos os outros nós
        - No segundo laço de repetição é feito a verificação de ciclos negativos
        - Exemplo
- Árvore geradoras de custo mínimo (Minimum Spanning Tree) (MST)
    - Uma árvore geradora é uma árvore subgrafo de um grafo conectado e não direcionado que inclui todos os seus vértices
        - Em outras palavras, é um subconjunto de arestas do grafo conectado e não direcionado que forma uma árvore acíclica onde cada nó do grafo faz parte da árvore
    - Uma MST é uma árvore geradora que conecta todos os vértices de um grafo com o menor peso total possível
        - Propriedades
            - O número de vértices do grafo é o mesmo da MST
            - Existe um número fixo de arestas na árvore geradora, que é o número de arestas do grafo menos 1
            - A árvore geradora não deve ser desconexa (desconectada), pois deve haver apenas uma única fonte de componente
            - A árvore geradora deve ser acíclica
            - O peso total da árvore geradora é definida como a soma de todas os pesos das arestas da mesma
        - Logo, uma MST é uma árvore geradora que possui o menor peso total dentre todas as árvores geradoras de um grafo
    - Algoritmo de Prim
        - Similar ao algoritmo de Dijkstra, é um algoritmo guloso
        - Inicialmente o algoritmo escolhe um vértice arbitrário para fazer parte da MST e a cada iteração o algoritmo um novo vértice será adicionado à MST
            - A partir desse vértice escolhido primeiramente, o algoritmo escolherá um outro vértice conectado ao primeiro que tenha o menor custo de aresta dentre os vértices conectados
            - Depois disso, o algoritmo irá escolher outro vértice que se conecta ao anterior basedo na aresta de menor custo e assim por diante
            - Após escolher todos os vértices, temos a nossa MST
        - Pode ser utilizado em grafos com pesos negativos e em grafos com ciclos negativos
            - Esse algoritmo pode ser implementado utilizando priority_queue (heap)
        - Melhor para grafos densos
        - Algoritmo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20160.png)
            
            - O que está em vermelho são as alterações em relação ao pseudo-código de Dijkstra
            - No primeiro laço de repetição temos a inicialização das variáveis, array de distâncias, array que possui as arestas que fazem parte da MST do grafo e para cada índice (ou vértice) mostra a quem ele está conectado, e fazendo um setMark como não visitado
                - Após isso inicializamos a nossa Heap e depois vamos para o algoritmo de fato
            - Exemplo
    - Algoritmo de Kruskal
        - É um algoritmo guloso, inicialmente para um grafo de N vértices, o algoritmo cria N MST’s
            - A cada iteração ele escolhe uma aresta do grafo partindo da aresta de menor peso para a de maior peso e unindo MST’s (sem introduzir ciclos)
            - Dado certo ponto o algoritmo processa essas arestas até que esse conjunto de MST’s formem um única MST e assim o algoritmo para
        - Este algoritmo precisa de uma nova estruturas de dados que faz o papel de procurar se duas MST’s já estão unidas e também tem o papel de uní-las
            - Essa nova estrutura de dados é chamada de Union-Find
        - Conjuntos disjuntos (Disjoints subsets, Union-Find)
            - Possui as operações de find (retorna o conjunto onde o elemento x está) e union (une os conjuntos de dois elementos)
            - É importante que em cada subconjunto tenha um elemento representativo
            - Exemplo
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20161.png)
                
            - Implementações
                - Quick-find
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20162.png)
                    
                    - Faz uso de duas estruturas internas: um array de inteiros para armazenar os representativos de cada elemento e um array de listas ligadas para armazenar os conjuntos propriamente ditos
                        - O representante de cada conjunto é dado pelo primeiro elemento de cada lista ligada
                    - Algoritmo
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20163.png)
                        
                        - Observação: algumas otimizações válidas seriam unir de acordo com a lista de menor tamanho para de maior tamanho (que há no algoritmo, na linha 4 o algoritmo quer que l1 seja a maior lista e l2 a menor lista)
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20164.png)
                        
                - Quick-union
                    - Utiliza uma parent pointer tree (uma árvore em que os filhos apontam para os pais) onde a raiz dessa árvore é o elemento representativo
                        - Em código, isso seria um array em que cada índice representaria um nó e array[nó] representaria o pai deste nó
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20165.png)
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20166.png)
                            
                            - Neste exemplo, o pai de B é 0; isto é, está no índice 0 que é o A
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20167.png)
                    
                    - Otimizações: na união, unir de acordo com o tamanho (número de nós) e depois pelo ranque (tamanho da subárvore) e depois pela ordem lexicográfica dos parâmetros
                    - Uma segunda otimização opcional seria no find e está relacionado em compressão de caminhos
                        - Em toda vez que usamos o find, os nós que são trafegados até chegar na raiz passam a ser filhos diretos da raiz após a operação de find; tornando a operação de find mais eficiente
                            
                            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20168.png)
                            
                            - Exemplo
                                
                                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20169.png)
                                
                                - Ao unir H e E, temos que o caminho de H até a raiz é H, C e A (raiz de H); o caminho de E por sua vez é E, D, F (raiz de E)
                                    - Sem a compressão de caminhos, nós simplesmente checamos primeiro pela quantidade de nós de cada subárvore; a subárvore de raiz A possui 4 nós enquanto que a subárvore de raiz F possui 5, então como a subárvore de raiz A tem menos nós, A agora aponta para F
                                    - Com a compressão de caminhos, após realizar o find  descobrir a raiz de H e E; nós atualizamos o caminho percorrido no find e atualizamos o array de parents
                                        - No caso do H, o caminho é H, C e A; para chegar até A precisamos passar por H e C, logo atualizamos o array de parents como A em cada um desses nós
                                        - No caso do E, o caminho é E, D e F; para chegar até F precisamos passar por E e D, logo atualizamos o array de parents como F em cada um desses nós
                                        - Após essa compressão de caminhos realizamos a união
                    - Algoritmo
                        
                        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20170.png)
                        
                        - Este pseudocódigo já possui a compressão de caminho no find mas não tem nenhuma otimização no union
        - Algoritmo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20171.png)
            
            - Essa heap é teoricamente melhor de forma Bottom Up, como a priority_queue do c++ é Top Down; se queremos o teoricamente melhor, é preciso implementar a Heap
            - Como parâmetros, temos o nosso grafo padrão e um grafo G’ que é onde estaria guardada a MST final (pode substituir por um array V, semelhante ao algoritmo de Prim )
            - Explicação
                - Linhas 1 à 6 é apenas a inicialização da Heap (origem, destino, peso) percorrendo todos os vértices e checando todas as arestas
                    - Do jeito que está no código, em casos de grafos não dirigidos teríamos na heap por exemplo (a, b, 10) e (b, a, 10); o que não é interessante, a ideia é ter cada aresta sem repetições
                - Após isso temos o algoritmo de fato
            - Exemplo
        - Melhor para grafos esparsos

---

## Computabilidade e complexidade computacional

- Problemas tratáveis vs intratáveis
    - Problemas tratáveis podem ser resolvidos em tempo polinomial (algoritmos O(p(n)) onde p(n) é um polinômio em termos de n)
    - Problemas intratáveis não podem ser resolvidos em tempo polinomial
    - Todos esses problemas são decidíveis, mas existem problemas que não são decidíveis (Halting problem, Entscheidungsproblem)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20172.png)
    
- Algoritmos determinísticos vs não-determinísticos
    - Algoritmos determinísticos
        - São tipos de algoritmos que, dado um input, sempre vai produzir o mesmo output
    - Algoritmos não-determinísticos
        - São algoritmos que, apesar do mesmo input, podem produzir outputs diferentes
            - Um algoritmo é não-determinístico polinomial se o tempo de eficiência na fase de verificação é polinomial
        - Possuem dois estágios, o de solução (adivinhar uma solução) e o de verificação (verificar a validade da solução)
            - Um algoritmo não-determinístico resolve um problema de decisão se é capaz de adivinhar uma solução pelo menos uma vez e conseguir verificar a sua validade
        - Um algoritmo não-determinístico hipotético possui todos os comando típicos da linguagem com a adição de um pulo não-determinístico (nd-jump)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20173.png)
        
        - Exemplo
            - O problema k-clique: dado um grafo G = (V, E) um grafo não-direcionado e sem pesos com k pertencendo aos naturais de forma que k ≤ |V|; existe algum subgrafo completo de G com k vértices?
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20174.png)
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20175.png)
                
- Classes de complexidade
    - P
        - Classe de problemas de decisão (com respostas de sim ou não) que podem ser resolvidas em tempo polinomial por algoritmos determinísticos
        - Muitos problemas não são problemas de decisão mas podem ser reduzidos à uma série de problemas de decisão
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20176.png)
        
    - NP
        - A classe de problemas de decisão que podem ser resolvidas em tempo polinomial por algoritmos não determinísticos
        - k-clique
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20177.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20178.png)
            
        - NP-complete
            - São os problemas mais difíceis dentro da classe NP
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20179.png)
            
            - Exemplos de NP-complete: SAT, 3-SAT, e o problema do ciclo hamiltoniano
            - 3-SAT
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20180.png)
                
        - NP-hard
            - São todos os problemas que são tão difíceis quanto o problema mais difícil da classe NP
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20181.png)
    

---

## Backtracking

- Estratégia que permite resolver instâncias maiores de problemas intratáveis, porém, no pior caso continua sendo um problema intratável
    - É melhor que a busca exaustiva
    - O tempo de eficiência depende do problema e do tamanho da instância
- Consiste em criar uma árvore representando um espaço de estados (pode ser implícita ou explícita)
- A estratégia consiste em a partir de uma solução parcial, tentar expandir essa solução para uma solução maior até encontrar a solução final
    - Caso durante esse processo, caso uma solução parcial não seja promissora; nós voltamos um passo e tentamos uma nova solução (de forma recursiva)
    - Se assemelha a uma busca em profundidade de um grafo
- Exemplo
    - Problema das n-rainhas
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20182.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20183.png)
        
        - Valid() seria uma função que checa se a posição da rainha está na mesma coluna ou diagonal que uma outra rainha
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20184.png)
        
    - Problema do circuito hamiltoniano
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20185.png)
        
    - Problema da soma de subconjuntos
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20186.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20187.png)
        

---

## Branch and Bound

- Estratégia semelhante ao backtracking, porém, ao invés de se assemelhar à uma busca em profundidade; se assemelha à uma busca em largura de um grafo (porém, ao invés de ser breadth first é best first)
    - Mas ao contrário da busca em largura de um grafo, o breach and bound incorpora critérios de corte (bounding) para eliminar caminhos não tão promissores (o que não acontece no BFS padrão)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20188.png)
    
    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20189.png)
    
- Para definir um bom bound (limite), é preciso ser fácil de programar/computar (computacionalmente eficiente) e não pode ser tão simples (efeito na poda, limites muito simples podem ser imprecisos e não contribuir efetivamente para a poda do breach and bound além de que estes podem levar à podas insuficientes onde muitos caminhos desnecessários ainda são explorados)
    - Os bounds precisam ser fáceis de computar para não sobrecarregar o algoritmo e precisam ser precisos o suficiente para garantir uma poda eficazdo breach and bound
        - Se os bounds forem muito simples podem não ajudar a eliminar muitos caminhose se forem muito complexos podem tornar o algoritmo ineficiente
- Exemplo
    - Problema da atribuição
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20190.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20191.png)
        
    - Problema do caixeiro viajante
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20192.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20193.png)
        

---

## Programação dinâmica

- Essa estratégia baseia-se na divisão de um problema em outros subproblemas menores que este principal
    - Com isso, resolvemos cada subproblema uma vez e guardamos o resultado em uma tabela (pode ser uma array ou outra estrutura para guardar), evitando redundâncias
- Implementações
    - Bottom-up (Tabulation)
        - Começamos com o menor dos subproblemas e gradualmente construímos a solução do problema central
        - Preenchemos uma tabela com as soluções dos subproblemas de baixo para cima para evitar redundâncias
    - Top-down (Memoization)
        - Nessa abordagem, primeiro projetamos a solução final para depois se concentrar nos subproblemas fazendo isso de forma recursiva
            - As soluções dos subproblemas são guardados em uma tabela
    - Diferenças entre as implementações
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20194.png)
        
- Exemplos
    - Problema de Fibonacci
        - Fazer um algoritmo que retorna o número de Fibonacci de n
            - Sem usar DP
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20195.png)
                
            - Usando DP
                
                ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20196.png)
                
                - Árvore de Fibonacci 5
                    
                    ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20197.png)
                    
    - Problema da linha de moedas (Coin-Row)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20198.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20199.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20200.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20201.png)
        
    - Problema de mudança (Change making problem)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20202.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20203.png)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20204.png)
        
    - Problema da mochila (Knapsack problem)
        
        ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20205.png)
        
        - Bottom-up
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20206.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20207.png)
            
        - Top-down
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20208.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20209.png)
            

---

## Algoritmos de aproximação

- Algumas vezes é ainda mais difícil de encontrar uma solução para um problema, então uma alternativa é usar um algoritmo de aproximação; aonde a solução não precisa ser ótima, apenas aceitável
- Exemplo
    - Aproximação gulosa para o problema do caixeiro viajante
        - Algoritmo do vizinho mais próximo
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20210.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20211.png)
            
        - Algoritmo baseado em MST
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20212.png)
            
            ![Untitled](../../assets/faculdade/periodo2/algoritmos-e-estruturas-de-dados/Untitled%20213.png)
            

---

[C](algoritmos-e-estruturas-de-dados/c.md)