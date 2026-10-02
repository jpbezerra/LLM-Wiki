# DESENVOLVIMENTO DE SOFTWARE

---

- livro: https://engsoftmoderna.info/?authuser=2
- Capítulos do livro Engenharia de Software Moderna
    - 1 - Introdução
        - 1.1 - Definições, Contexto e História
            - Engenharia de Software trata da aplicação de abordagens sistemáticas, disciplinadas e quantificáveis para desenvolver, operar, manter e evoluir software
                - É a área da computação que se preocupa em propor e aplicar princípios de engenharia na construção de software
            - Dificuldades essenciais da engenharia de software
                - Complexidade: dentre as construções que o homem se propõe a realizar, software é uma das mais desafiadoras e mais complexas que existe
                - Conformidade: pela sua natureza software tem que se adaptar ao seu ambiente, que muda a todo momento no mundo moderno
                - Facilidade de mudanças: consiste na necessidade de evoluir sempre, incorporando novas funcionalidades; quanto mais bem sucedido for um sistema de software, mais demanda por mudanças ele recebe
                - Invisibilidade: devido à sua natureza abstrata, é difícil visualizar o tamanho e consequentemente estimar o esforço de construir um sistema de software
            - A engenharia de software possui também dificuldades acidentais, que são aquelas associadas a problemas tecnológicos em que os Engenheiros de Software podem resolver, se devidamente treinados e caso tenham acesso às devidas tecnologias e recursos
        - 1.2 - O que se Estuda em Engenharia de Software?
            - Para isso, foi criado um guia chamado [SWEBOK](https://www.computer.org/education/bodies-of-knowledge/software-engineering) que possui o objetivo de documentar o corpo do conhecimento que caracteriza a área que hoje é chamada de engenharia de software
            - Segundo o guia, engenharia de software possui 12 áreas do conhecimento, que são: Engenharia de Requisitos; Projeto de Software; Construção de Software; Testes de Software; Manutenção de Software; Gerência de Configuração; Gerência de Projetos; Processos de Software; Modelos de Software; Qualidade de Software; Prática Profissional; Aspectos Econômicos; Fundamentos de Computação; Fundamentos de Matemática e Fundamentos de Engenharia
                - As 3 últimas áreas não vão ser tratadas neste capítulo
            - 1.2.1 - Engenharia de Requisitos
                - Engenharia de requisitos inclui o conjunto de atividades realizadas com o objetivo de definir, analisar, documentar e validar os requisitos de um sistema
                    - Existem requisitos funcionais e não-funcionais
                - Requisitos funcionais definem o que um sistema deve fazer (funcionalidades e serviços ao qual o sistema deve implementar)
                - Requisitos não-funcionais definem o modo de operação do sistema (restrições e qualidade de serviço)
                    - Exemplos de requisitos não-funcionais: desempenho, disponibilidade, tolerância a falhas, segurança, privacidade, interoperabilidade, capacidade, manutenibilidade e usabilidade
                - Exemplo no contexto de home-banking
                    - Requisitos funcionais: informar o saldo da conta, informar o extrato, realizar transferência entre contas, pagar um boleto bancário, cancelar um cartão de débito, etc
                    - Requisitos não-funcionais:  Desempenho: informar o saldo da conta em menos de 3 segundos; Disponibilidade: estar no ar 99% do tempo; Tolerância a falhas: continuar operando mesmo se um determinado centro de dados cair; Segurança: criptografar todos os dados trocados com as agências; Privacidade: não disponibilizar para terceiros dados de clientes; Interoperabilidade: integrar-se com os sistemas do Banco Central; Capacidade: ser capaz de armazenar dados de 1 milhão de clientes; Usabilidade: ter uma versão para deficientes visuais.
            - 1.2.2 - Projeto de Software
                - Durante o projeto, são definidas suas principais unidades de código porém apenas no nível de interfaces, incluindo interfaces providas e interfaces requeridas
                    - Interfaces providas são aqueles serviços que uma unidade de código torna público para uso pelo resto do sistema
                    - Interfaces requeridas são aquelas interfaces das quais uma unidade de código depende para funcionar
                - Portanto, durante o projeto de um sistema de software, não entramos em detalhes de implementação de cada unidade de código, tais como detalhes de implementação dos métodos de uma classe (caso o sistema seja implementado em uma linguagem orientada a objetos)
                - Projeto de software é diferente de implementação!
                - Exemplo
                    
                    ```java
                    class ContaBancaria {
                       private Cliente cliente;
                       private double saldo;
                       public double getSaldo() { ... }
                       public String getNomeCliente() { ... }
                       public String getExtrato (Date inicio) { ... }
                    }
                    ```
                    
                    - ContaBancaria oferece uma interface para as demais classes do sistema, na forma de três métodos públicos, que constituem a interface provida pela classe
                    - ContaBancaria depende da classe Cliente, logo, a interface Cliente é uma interface requerida por ContaBancaria
                        - Em outras palavras, ContaBancaria possui uma dependência para Cliente
                - OBS: arquitetura de software trata da organização de um sistema em um nível de abstração mais alto do que aquele que envolve classes ou construções semelhantes
            - 1.2.3 - Construção de Software
                - Trata-se da implementação/codificação do sistema
                - Definição dos algoritmos, estruturas de dados, frameworks, bibliotecas, técnicas de tratamento de exceções, padrões de nomes, layout, documentação do código e as ferramentas que serão utilizadas no desenvolvimento
            - 1.2.4 - Testes de Software
                - Execução de um programa com um conjunto finito de casos a fim de verificar se o programa possui o comportamento esperado
                - “Testes de software mostram a presença de bugs, mas não a sua ausência”
                - Testes de software
                    - Testes de unidade: quando se testa uma pequena unidade do código
                    - Testes de integração: quando se testa uma unidade de maior granulidade (como um conjunto de classes)
                    - Testes de performance: quando se submete o sistema a uma carga de processamento para verificar seu desempenho
                    - Testes de usabilidade: verificar a usabilidade da interface do sistema
                    - Entre outros tipos
                - Podem ser usados tanto para verificação como para validação de sistemas
                    - Verificação: garantir que um sistema atende à sua especificação
                        - “Estamos implementando o sistema corretamente? Isto é, de acordo com seus requisitos.”
                    - Validação: garantir que o sistema atende às necessidades de seus clientes
                        - “Estamos implementando o sistema correto? Isto é, aquele que os clientes ou o mercado está querendo.”
            - 1.2.5 - Manutenção e Evolução de Software
                - Tipos de manutenção realizadas em sistemas de software
                    - Corretiva: corrigir bugs reportados por usuários ou outros desenvolvedores
                    - Preventiva: corrigir bugs latentes no código (que ainda não causaram falhas junto aos usuários do sistema)
                    - Adaptativa: adaptar um sistema a uma mudança em seu ambiente, incluindo tecnologia, legislação, regras de integração com outros sistemas ou demandas de novos clientes
                    - Refactoring: modicações realizadas em um software preservando seu comportamento e visando exclusivamente a melhoria do código ou projeto
                    - Evolutiva: incluir uma nova funcionalidade ou introduzir aperfeiçoamentos importantes em funcionalidades existentes
            - 1.2.6 - Gerência de Configuração
                - Desenvolver um software com um sistema de controle de versões como o git
                - Definição de um conjunto de políticas para gerenciar as diferentes versões de um sistema
                - As releases podem ser identificadas no formato xyz, onde um incremento em z ocorre quando se lança uma nova release com apenas correções de bugs (normalmente chamada de patch), um incremento em y ocorre quando se lança uma release da biblioteca com pequenas funcionalidades (normalmente chamada de versão minor), e um incremento em x ocorre quando se lança uma release com funcionalidades muito diferentes daquela última release (normalmente chamada de versão major)
                    - Esse esquema de numeração de release é conhecido como versionamento semântico
            - 1.2.7 - Gerência de Projetos
                - Uso de práticas e atividades de gerência de projetos
                    - Exemplos: negociação de contratos com clientes, gerência de recursos humanos, gerência de riscos, acompanhamento da concorrência, etc.
                - Stakeholder: aqueles que afetam ou que são afetados pelo projeto, podendo ser pessoas físicas ou organizações
                - “A inclusão de novos desenvolvedores em um projeto que está atrasado contribui para torná-lo ainda mais atrasado.”
                    - Lei de Brooks
                    - Esse efeito acontece porque os novos desenvolvedores terão primeiro que compreender todo o sistema, sua arquitetura e seu projeto antes de começarem a produzir código útil
                    - Equipes maiores exigem maior esforço de comunicação e coordenação para tomar e explicar decisões
                        - Exemplo: um time de 3 desenvolvedores possuem 3 canais de comunicação (p1-p2, p1-p3, p2-p3), já um time de 4 desenvolvedores possuem 6 canais e assim por diante
            - 1.2.8 - Processos de Desenvolvimento de Software
                - Define quais atividades e etapas devem ser seguidas para construir e entregar um sistema de software
                - Tipos de processo
                    - Processos Waterfall
                        - Processos dirigidos por planejamento
                        - Propõem que a construção de um sistema deve ser feita em etapas sequenciais, como uma cascata de água
                        - Etapas
                            
                            ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image.png)
                            
                        - Elaborado mais antigamente, foi muito criticado devido aos atrasos e problemas recorrentes
                    - Processos Ágeis
                        - Devido às críticas dos processos waterfall, foi criado um novo modo de para construção de software
                        - A ideia é que um sistema deve ser construído de forma incremental e iterativa
                            - Pequenos incrementos de funcionalidades são produzidos e logo em seguida validado pelos usuários
                        - Diversos métodos que concretizam os princípios ágeis foram propostos, como XP, Scrum, Kanban e Lean Development
                        - Esses métodos ajudaram a disseminar diversas práticas de desenvolvimento de software, como testes automatizados, test-driven development (escrever os testes primeiro antes do próprio código) e integração contínua
                        - Integração Contínua
                            - Recomenda que os desenvolvedores integrem o código que produzem imediatamente
                            - Tem como objetivo evitar que os desenvolvedores fiquem muito tempo trabalhando localmente sem integrar o código que estão produzindo no repositório principal do projeto
                            - Quanto maior o time de desenvolvimento, aumenta as chances de conflitos de integração
            - 1.2.9 - Modelos de Software
                - Permitir que os desenvolvedores possam analisar propriedades e características essenciais de um sistema de modo fácil e rápido sem ter que mergulhar nos detalhes do código
                - Estes modelos podem apoiar a engenharia avante (modelos criados antes do código para ter um entendimento de mais alto nível de um sistema antes de implementar o código) ou podem apoiar a engenharia reversa (modelos criados depois de um código criado a fim de entender essa porção de código)
                - Frequentemente modelos de software são baseados em notações gráficas, entre elas a UML
                - UML
                    - Notação que define mais de uma dezena de diagramas gráficos para representar propriedades estruturais e comportamentais de um sistema
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%201.png)
                        
                        - As caixas retangulares representam classes do sistema incluindo seus métodos e atributos
                        - As setas indicam uma relação entre duas classes
            - 1.2.10 - Qualidade de Software
                - Qualidade externa: considera fatores que podem ser aferidos sem analisar o código
                    - Ou seja, pode ser avaliada por usuários comuns que não são especialistas em engenharia de software
                    - Fatores
                        - Correção: o software atende à sua especificação? Nas situações normais, ele funciona como esperado?
                        - Robustez: o software continua funcionando mesmo quando ocorrem eventos anormais, como uma falha de comunicação ou de disco? Por exemplo, um software robusto não pode sofrer um *crash* (abortar) caso tais eventos anormais ocorram. Ele deve pelo menos avisar por qual motivo não está conseguindo funcionar conforme previsto.
                        - Eficiência: o software faz bom uso de recursos computacionais? Ou ele precisa de um hardware extremamente poderoso e caro para funcionar?
                        - Portabilidade: é possível portar esse software para outras plataformas e sistemas operacionais? Ele, por exemplo, possui versões para os principais sistemas operacionais, como Windows, Linux e macOS? Ou então, se for um app, ele possui versões para Android e iOS?
                        - Facilidade de Uso: o software possui uma interface amigável, mensagens de erro claras, suporta mais de uma língua, etc? Pode ser também usado por pessoas com alguma deficiência, como visual ou auditiva?
                        - Compatibilidade: o software é compatível com os principais formatos de dados de sua área? Por exemplo, se o software for uma planilha eletrônica, ele importa arquivos em formatos XLS e CSV?
                - Qualidade interna: considera propridades e características relacionadas com a implementação de um sistema
                    - Pode ser avaliada somente por um especialista em engenharia de software
                    - Exemplos de fatores: modularidade, legibilidade do código, manutenibilidade e testabilidade
                - Para garantir a qualidade, diversas estratégias podem ser usadas
                    - Métricas para acompanhar um produto de software, como número de linhas de um programa, número de defeitos reportados e etc.
                    - Revisões de códigos, com o objetivo de detectar bugs antecipadamente, antes de o sistema entrar em produção e tambpem garantir a qualidade do código
                        - Para apoiar os processos de revisão de código existem ferramentas como o GitHub
            - 1.2.11 - Prática Profissional
                - Questionamentos sobre o papel e a responsabildiade ética dos profissionais formados em Computação, em uma sociedade na qual os relacionamentos humanos são cada vez mais mediados por algoritmos e sistemas de software
                - [Código de Ética da ACM](https://www.acm.org/code-of-ethics)
                - [Código de Ética da IEEE Computer Society](https://www.computer.org/education/code-of-ethics)
            - 1.2.12 - Aspectos Econômicos
                - Decisões e questões econômicas se entrelaçam com o desenvolvimento de sistemas
                - Custos de oportunidade de uma decisão
                    - Estas oportunidades são as preteridas quando se descartou uma das decisões alternativas
        - 1.3 - Classificação de Sistemas de Software
            - Sistemas A (Acute)
                - Sistemas de missão crítica
                - Sistemas nos quais qualquer falha pode causar um imenso prejuízo (incluindo a perda de vidas humanas)
                - O desenvolvimento desses sistemas deve ser feito de acordo com processos rígidos, incluindo rigorosa revisão de código e certificação por organizações externas
            - Sistemas B (Business)
                - Incluem as mais variadas aplicações corporativas, sistemas web variado, aplicações de uso geral, bibliotecas, frameworks e sistemas de software básico
                - Tipo de sistema trabalhado ao longo do livro
            - Sistemas C (Casuais)
                - Não sofrem pressão para terem altos níveis de qualidades
                - Podem ter alguns bugs os quais não vão comprometer fundalmentalmente o funcionamento
                - Geralmente são sistemas pequenos e não críticos
                - Nesse tipo de software, o maior risco é o over-engineering, ou seja, o uso de recursos mais sofisticados em um contexto que não demanda tanta preocupação
    - 2 - Processos
        - 2.1 - Importância de Processos
            - Um processo de desenvolvimento de software define um conjunto de passos, tarefas, etapas, eventos e práticas que devem ser seguidos por desenvolvedores na produção de um sistema
                - Projetos pessoais (Exemplo: Linux e TeX ambos na implementação inicial, aos quais foram desenvolvidos apenas por 1 pessoa) não precisam se preocupar tanto com a adoção de processos, pois nestes tipos de projeto o processo pode depender mais dos príncipios, práticas e decisões tomadas por um único desenvolvedor; tendo impacto apenas sobre ele mesmo
            - Porém, atualmente os projetos de software são mais complexos tornando impossível de serem desenvolvidos apenas por uma única pessoa; os sistemas modernos são desenvolvidos em equipe
                - Estas equipes precisam de um ordenamento a fim delas não trabalharem de forma descoordenada, e é aí que vêm os processos como por exemplo os processos ágeis (que serão vistos a seguir)
        - 2.2 - Manifesto Ágil
            - No começo, o processo utilizado na engenharia de software foi o processo de cascata, o que foi algo natural pois as outras engenharias utilizavam deste mesmo processo
                - Depois perceberam que software é diferente de outros produtos e por isso um grupo de profissionais decidiram lançar uma nova base de conceitos de processo de software as quais foram registradas em um documento chamado de Manifesto Ágil
            - Características de processos ágeis
                - A principal característica de processos ágeis é a adoção de ciclos curtos e iterativos de desenvolvimento
                    - De início implementa-se uma primeira versão do sistema com as funcionalidades mais urgentes segundo cliente
                        - O sistema é implementado de forma gradativa começando por aquilo que é mais urgente para o cliente
                        - Caso esta versão seja aprovada, um novo ciclo (ou iteração) inicia-se. com as próximas funcionalidades também priorizadas pelos clientes
                            - normalmente estes ciclos são curtos, por isso o sistema é construído de forma incremental ao qual cada incremento é devidamente aprovado pelos clientes
                - Esquema de processo ágil
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%202.png)
                    
                    - O esquema pode sugerir que cada iteração é uma mini-waterfall e que ao final de cada iteração tem-se de colocar o sistema em produção para uso pelos usuários finais, ambas não são verdade
                - Outras características
                    - Maior ênfase na documentação: apenas o essencial deve ser documentado
                    - Menor ênfase em planos detalhados: o importante no desenvolvimento ágil é conseguir avançar, mesmo em ambientes com informações imperfeitas, parciais e sujeitas a mudanças
                    - Inexistência de uma fase dedicada a design: em vez disso, o design é incremental, evoluindo à medida que o sistema vai nascendo, ao final de cada iteração
                    - Desenvolvimento em times pequenos: com cerca de uma dezena de desenvolvedores
                    - Ênfase em novas práticas de desenvolvimento: programação em pares, testes automatizados e integração contínua
                - As características dos processos ágeis são consideradas genéricas e abrangentes, por isso alguns métodos foram propostos para ajudar desenvolvedores a adotar os princípios ágeis de forma mais concreta
            - Aprofundamento
                - Processo: conjunto de passos, etapas e tarefas que se usa para construir um software
                - Método: define e especifica um determinado processo de desenvolvimento
                - Todo método de desenvolvimento deve ser entendido como um conjunto de recomendações
        - 2.3 - Extreme Programming (XP)
            - Método leve recomendado para desenvolver softwares com requisitos vagos ou sujeito a mudanças
            - É um método definido de forma abstrata, usando-se de valores e princípios que devem fazer parte da cultura e dos hábitos de times de desenvolvimento de software
            - 2.3.1 - Valores
                - XP defende que o desenvolvimento de projetos de software seja norteado por três valores principais: comunicação, simplicidade e feedback
            - 2.3.2 - Princípios
                - Humanidade: gestão de pessoas é fundamental para o sucesso de projetos de software
                    - Peopleware: termo que significa parte humana que interage com sistemas computacionais (usuários, devs, etc.)
                - Economicidade: se por um lado peopleware é fundamental, software é caro pois demanda alocação de recursos financeiros consideráveis; por isso, é importante ter consciência que é preciso que o software gere resultados econômicos
                - Benefícios mútuos: um projeto de software tem que beneficiar múltiplos stakeholders
                - Melhoras contínuas
                - Falhas acontecem: XP não advoga que as falhas devem ser acobertadas, mas elas não devem ser usadas para punir membros do time
                - Baby steps: pequenas melhorias são melhores que grandes revoluções
                - Responsabilidade pessoal: os desenvolvedores devem ter uma clara ideia do seu papel e responsabilidade na equipe
            - 2.3.3 - Práticas sobre o Processo de Desenvolvimento
                - Envolvimento dos clientes com o projeto de modo que os times incluam pelo menos um representante dos clientes
                    - Uma das funções deste representante é escrever as user stories, que são os documentos feitos a mão que descrevem os requisitos do sistema a ser implementado de forma resumida
                        - Exemplo de user stories
                            
                            ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%203.png)
                            
                            - Podem ser vistos como lembretes para que depois o requisito seja verbalmente detalhado pelo representante dos clientes
                - Depois da escrita das user stories, os desenvolvedores estimam o tempo que será necessário implementá-las e este tempo é medido em story points
                    - Muitas vezes se usa a sequência de Fibonacci para estimar os story points
                    - Outra técnica usada para estimar os story points é o Planning Poker ao qual consiste na interação e discussão dos desenvolvedores a fim de definir os story points
                - A implementação das histórias são feitas em iterações, com uma duração fixa e bem definida (1-3 semanas por exemplo)
                    - Estas iterações por sua vez criam ciclos mais longos, chamados de releases (2-3 meses por exemplo)
                        - OBS: estas releases não possuem relação com versões de sistemas e etc.
                    - A velocidade de um time é o número de story points que eles conseguem implementar em uma iteração, e por isso ela deve ser bem definida
                - Após a definição de user histories, duração de uma iteração, número de iterações de uma release, estimativas de cada história e a velocidade o representante de clientes deve priorizar as histórias num processo chamado de planejamento de releases e após este planejamento a equipe de desenvolvedores deve se reunir para realizar o planejamento de iterações ao qual possui o objetivo de decompor as histórias de uma iteração em tarefas para cada membro da equipe
                    - XP defende também que os times para cada iteração programem algumas folgas (slacks), que são tarefas que podem ser adiadas caso necessário
                    - Essas folgas possuem dois objetivos: criar um buffer de segurança em uma iteração que pode ser usado caso alguma tarefa demande mais tempo que o previsto e também permitir que os desenvolvedores descansem um pouco
            - 2.3.4 - Práticas de Programação
                - Design incremental: o time deve reservar um tempo para definir o design do sistema que está sendo desenvolvido e esta atividade deve ser simples, contínua e incremental
                    - O momento ideal para pensar em design é quando ele se revelar importante
                    - Design incremental somente é possível caso seja adotado em conjunto com as outras práticas de XP, principalmente refactoring, que deve ser continuamente aplicado para melhorar a qualidade do design
                - Programação em pares: toda tarefa de codificação deve ser realizada por dois desenvolvedores trabalhando juntos compartilhando o mesmo teclado e monito, um deles é chamado de líder (ou driver) e é quem fica no comando do mouse e teclado, já o outro é chamado de navegador e possui a função de revisor e questionador
                    - XP propões que os paressejam trocados a cada sessão, invertendo os papéis de líder e revisor
                - Propriedade coletiva do código: o desenvolvedor (ou par) pode modificar qualquer parte do código, seja para implementar uma nova feature, crrigir bug, etc.
                - Testes automatizados: implementação de programas para executar pequenas unidades de um sistema e verificar se as saídas produzidas são aquelas esperadas
                - Desenvolvimento dirigido por testes (TDD): implementa-se primeiro o teste de um método e após isso o seu código
                    - Objetivo de evitar que a escrita de testes seja deixada para depois e também de utilizar do senso crítico do desenvolvedor pois assim este se coloca no papel de cliente do método testado, fazendo com que ele pense primeiro na interface e incentiva a criação de métodos mais amigáveis no ponto de vista da interface provida para os clientes
                - Build automatizado: o processo de build (geração de uma versão de um sistema que seja executável e que possa ser colocada em produção) deve ser automatizado sem nenhuma intervenção dos desenvolvedores a fim deles não se preocuparem com as tarefas de rodar scripts e concentrar-se apenas na implementação das histórias
                    - Este build deve ser o mais rápido possível para que os desenvolvedores recebam o feedback o mais rápido possível
                - Integração contínua: sistemas de software são desenvolvidos com o apoio de sistemas de controle de versões ou VCS (como o git), que armazenam o código fonte do sistema e de arquivos relacionados
                    - Quando se usa um VCS, primeiro é preciso baixar o código fonte para a máquina local antes de começar a trabalhar em uma tarefa (pull)
                    - Feito isso, os desenvolvedores devem subir o código modificado (push), ocorrendo uma integração da modificação no código principal armazenado no VCS
                    - Porém, entre um pull e push outro desenvolvedor pode ter modificado o mesmo trecho de código e realizado a sua integração, nesse caso quando o primeiro desenvolvedor tentar subir o código o VCS irá impedir a integração dizendo que existe um conflito
                        - Estes conflitos são ruins pois devem ser resolvidos manualmente e costumam demandar um grande esforço resultando no que se chama integratio hell
                    - Por isso, a ideia de XP é que os desenvolvedores integrem seu código sempre a fim de evitar que estes passem muito tempo trabalhando localmente sem integrar o código ocasionando a diminuição de chances de conflito
                    - Para garantir a qualidade do código que está sendo integrado, costuma-se usar um serviço de integração contínua, ao qual antes de realizar qualquer integração o serviço faz o build do código e executa os testes
            - 2.3.5 - Práticas de Gerenciamento de Projetos
                - Ambiente de trabalho: deve-se evitar times fracionado, nos quais alguns desenvolvedores trabalham apenas alguns dias da semana no projeto e os outros dias em um outro projeto
                    - A XP defende que todos os desenvolvedores trabalhem em uma mesma sala para facilitar comunicação e feedback além de jornada de trabalho sustentáveis
                - Contratos com escopo aberto: em contratos de escopo fechado a empresa contratante define, mesmo que de forma mínima, os requisitos do sistema além do preço e prazo de entrega
                    - Porém, estes contratos são arriscados, de acordo com XP, pois os requisitos mudam e nem mesmo o cliente sabe antecipadamente o que ele quer que o sistema faça, de modo preciso
                        - Isso faz com que a entrega possa ser um sistema com problemas de qualidade
                    - Em contratos de escopo aberto o pagamento ocorre de acordo com a hora trabalhada, o contrato pode ser rescindido ou renovado e etc.
                        - Contratos de escopo aberto são mais compatíveis com os princípios do Manisfesto Ágil, que valoriza colaboração com o cliente mais do que negociação de contratos
                - Métricas de processo: prática para que gerentes e executivos possam acompanhar um projeto XP recomenda-se o uso de duas métricas principais: número de bugs em produção e intervalo de tempo entre o início do desenvolvimento e o momento em que o projeto começar a gerar os seus primeiros resultados financeiros
        - 2.4 - Scrum
            - Método ágil para gerenciamento de projetos, que não necessariamente precisam ser projetos de desenvolvimento de software, além de não propor nenhuma prática de programação
                - Diferentemente do XP, que é voltado exclusivamente para desenvolvimento de software
            - 2.4.1 - Papéis
                - Times Scrum são formados por um Dono de Produto (Product Owner ou PO), um Scrum Master e de 3 a 9 desenvolvedores
                - PO
                    - Tem o mesmo papel do Representante dos Clientes em XP
                    - Deve possui a visão do produto que será construído e responsável por maximizar o retorno do investimento feito no projeto
                - Scrum Master
                    - Especialista Scrum do time, responsável por garantir que s regras do método estão sendo seguidas
                    - Funções de um facilitador dos trabalhos e removedor de impedimentos
                - Times de Scrum são cross-funcionais (ou multidisciplinares), ou seja, eles devem incluir além do PO e do Scrum Master todos os especialistas necessários para desenvolver o produto de forma a não depender de membros externos
                    - Em casos de projetos de software, devem incluir desenvolvedores front,-end, back-end, especialistas em banco de dados, projetistas de interface, etc.
            - 2.4.2 - Principais Artefatos e Eventos
                - Os dois artefatos principais são o backlog do produto e o backlog do sprint, já os principais eventos são sprints e planejamento de sprints
                - Backlog do Produto
                    - Lista de histórias ordenadas por prioridades
                        - Escritas e organizadas pelo PO e constituem uma descrição resumida das funcionalidades que devem ser implementadas no projeto
                    - Deve ser continuamente atualizado
                - Sprints
                    - Iteração
                    - Ao final de cada sprint, deve-se entregar um produto com valor tangível para o cliente
                    - O resultado de um sprint é chamado de um produto potencialmente pronto para entrar em produção (potencially shippable product)
                - Planejamento do Sprint
                    - Reunião na qual o time se reúne para decidir as histórias que serao implementadas no sprint que vai se iniciar
                    - Dividida em duas partes
                        - A primeira é comandada pelo PO, ao qual ele propõe histórias para o sprint e o restante do time decide se tem velocidade para implementá-las
                        - A segunda parte é comandada pelos desenvolvedores, ao qual eles quebram as histórias em tarefas e estimam a duração delas
                            - No entanto, o PO deve estar continuar presente nessa parte final para tirar dúvidas sobre as histórias selecionadas para o sprint
                - Backlog do Sprint
                    - Gerado ao final do planejamento do sprint, que consiste em uma lista com as tarefas do sprint e a duração das mesmas
                        - Tarefas podem se mostrar desnecessárias e outras podem surgir ao longo do sprint
                        - A única coisa que não pode ser alterada é o sprint goal, a lista de histórias que o PO selecionou para o sprint e que o time de desenvolvimento se comprometeu a implementar na duração do mesmo
                - Terminada a reunião do projeto tem início o sprint, ou seja, o time começa a trabalhar na implementação das tarefas do backlog
                    - Os times Scrum tem autonomia para decidir como e por quem as histórias serão implementadas
                - Quadro Scrum (Scrum Board)
                    - Quadro com tarefas a fazer, em andamento e finalizadas
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%204.png)
                    
                - Uma decisão importante em projetos de Scrum enolve os critérios para considerar uma história ou tarefa concluídas
                    - Tais critérios devem ser combinados com o time e ser do conhecimento de todos os membros
                - Gráfico de Burndown
                    - A cada dia do sprint, o gráfico mostra quantas horas são necessárias para se implementar as tarefas que ainda não estão concluídas
                        - Dia X do sprint restam Y tarefas que se somam Z horas
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%205.png)
                    
            - 2.4.3 - Outros Eventos
                - Reuniões Diárias
                    - Devem ser de cerca 15 minutos, das quais todos os membros do time debem participar
                    - Cada membro deve responder o que ele fez no dia anterior, o que ele pretende fazer no dia corrente e se ele está enfrentando algum problema mais sério
                    - Essas reuniões tem como objetivo melhorar a comunicação entre os membros do time, fazendo com que eles se socializem melhor durante o projeto
                - Revisão do Sprint
                    - Reunião para mostrar os resultados de um sprint
                    - Devem participar todos os membros do time e idealmente outros stakeholders que estejam envolvidos com o resultado do sprint
                    - Caso o PO detecte problema em alguma história, ela deve voltar para o backlog do produto para ser retrabalhada em um próximo sprint
                - Retrospectiva
                    - Reunião do time Scrum com o objetivo de refletir sobre o sprint que está terminando e identificar os pontos de melhoria no processo, pessoas, relacionamentos e ferramentas usadas
                - Uma característica de todos os eventos Scrum é terem uma duração bem definida, chamada de time-box da atividade
                - Time-box
                    - Exemplo de time-box
                        
                        ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%206.png)
                        
        - 2.5 - Kanban
            - Mais simples que o Scrum, pois não usa nenhum dos artefatos do Scrum: os eventos (incluindo os sprints) nem os papéis (PO, Scrum Master, etc.)
                - A única exceção é o quadro de tarefas, que é chamado de Quadro Kanban que inclui o backlog do produto
            - Quadro Kanban (Kanban Board)
                - A primeira coluna é o backlog do produto (funciona igual ao Scrum)
                - As demais colunas são os passos que devem ser seguidos para transformar uma história do usuário em uma funcionalidade executável
                    - Colunas de especificação, implementação e revisão de código
                    - A ideia é que as histórias sejam processadas passo a passo da esquerda pra direita
                - Cada coluna é subdividida em subcolunas “em execução” e “concluídas”
                    - Tarefas concluídas em um passo estão aguardando serem puxadas, por um membro do time, para o próximo passo
                    - Por isso, Kanban é chamado de sistema de pull
                - Exemplo
                    - Antes
                        
                        ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%207.png)
                        
                    - Depois
                        
                        ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%208.png)
                        
            - Limites WIP (Work In Progress)
                - Limite máximo de tarefas que podem estar um cada um dos passos de um Quadro Kanban
                    - Conta-se aqueles na primeira coluna (em andamento) e na segunda coluna (concluídos) de cada passo, com exceção do último passo que conta apenas a primeira coluna
                - Exemplo
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%209.png)
                    
                    - A história H3 não pode ser puxada para a fase de especificação pois nesta fase o limite WIP é 2 e há 5 tarefas
                    - Pode-se puxar uma tarefa de especificação para a implementação
                - Estes limites são necessários para evitar que os times Kanban fiquem sobrecarregados
            - 2.5.1 - Calculando os Limites WIP
                - Existe mais de uma alternativa, mas o livro aborda um algoritmo proposto por Eric Brechner
                - Passo a passo
                    - Primeiro, temos que estimar quanto tempo em média cada tarefa vai ficar em cada passo do Quadro Kanban, esse tempo é chamado de lead time (LT)
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2010.png)
                            
                        - O lead time inclui o tempo em fila, que é o tempo que a tarefa vai ficar na 2ª subcoluna dos passos do Quadro Kanban aguardando ser puxada para o passo seguinte
                    - Segundo, deve-se estimar o throughput (TP) do passo com maior lead time do Quadro Kanban, isto é, o número de tarefas produzidas por dia nesse passo
                        - Exemplo
                            - O throughput desse passo é então: 8 / 21 = 0.38 tarefas/dia (21 dias úteis)
                    - Por fim, o WIP de cada passo é definido como
                        - WIP(passo) = TP * LT(passo), onde o TP refere-se ao TP mais lento conforme calculado no item anterior
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2011.png)
                            
                - Neste algorimo sugere-se adicionar uma margem de erro de 50% nos WIPs calculados
            - 2.5.2 - Lei de Little
                - O procedimento para cálculo de WIPs explicado anteriormente é uma aplicação direta da Lei de Little, um dos resultados mais importantes da Teoria de Filas
                - A lei diz que o número de itens em um sistema de filas é igual à taxa de chegada desses itens multiplicado pelo tempo que cada item fica no sistema (o sistema seria um passo de um processo do Kanban e os itens seriam suas tarefas)
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2012.png)
                    
        - 2.6 - Quando Não Usar Métodos Ágeis?
            - Quando não usar determinadas práticas de desenvolvimento ágil
                - Design Incremental
                    - Esse tipo de design faz sentido quando o time tem uma primeira visão do design do sistema
                    - Se o time não tem essa visão, ou o domínio do sistema é novo e complexo, ou o custo de mudanças futuras é muito alto, recomenda-se adotar uma fase de design e análise inicial, antes de partir para iterações que requeiram implementações de funcionalidades
                - Histórias do Usuário
                    - Histórias são um método leve para especificação de requisitos, que depois são clarificados com o envolvimento cotidiano de um representante dos clientes no projeto.
                    - Porém, em certos casos, pode ser importante ter uma especificação detalhada de requisitos no início do projeto, principalmente se ele for um projeto de uma área totalmente nova para o time de desenvolvedores
                - Envolvimento do Cliente
                    - Se os requisitos do sistema são estáveis e de pleno conhecimento do time de desenvolvedores, não faz sentido ter um Representante dos Clientes ou Dono do Produto integrado ao time
                - Documentação Leve e Simplificada
                    - Em certos domínios, documentações detalhadas de requisitos e de projeto são mandatórias
                - Times Auto-organizáveis
                    - Times ágeis são autônomos e empoderados para trabalhar sem interferências durante o time-box de uma iteração
                    - Consequentemente, eles não precisam prestar contas diárias para os gerentes e executivos da organização
                    - No entanto, essa característica pode ser incompatível com os valores e cultura de certas organizações, principalmente aquelas com uma tradição de níveis hierárquicos e de controle rígidos
                - Contratos com Escopo Aberto
                    - Em contratos com escopo aberto, a remuneração é por hora trabalhada
                    - Algumas organizações podem não se sentir seguras para assinar esse tipo de contrato, principalmente quando elas não têm uma experiência prévia com desenvolvimento ágil ou referências confiáveis sobre a empresa contratada
            - Existem duas práticas atualmente adotadas na grande maioria de projetos de software
                - Times pequenos, pois o esforço de sincronização cresce muito quando os times são compostos por dezenas de membros
                - Iterações (Sprints), mesmo que com duração maior do que aquela típica de métodos ágeis
        - 2.7 - Outros métodos interativos
            - Modelo em Espiral
                - Nesse modelo, um sistema é desenvolvido na forma de uma espiral de iterações
                    - Cada iteração ou volta completa na espiral inclui quatro etapas
                        - Definição de objetivos e restrições como custos, cronogramas, etc.
                        - Avaliação de alternativas e análise de riscos
                        - Desenvolvimento e teses, ao final dessa etapa deve-se gerar um protótipo que possa ser demonstrado aos usuários do sistema
                        - Planejamento da próxima iteração ou então tomar a decisão de parar
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2013.png)
                    
                - Cada iteração somando-se as quatro fases pode levar de 6 a 24 meses
            - Rational Processo Unificado (RUP)
                - Método de processo unificado implementado pela Rational
                - É vinculado a duas tecnologias específicas
                    - Vinculado às linguagens de modelagem UML, pois muitos dos resultados do RUP são documentados e representados usando-se diagramas gráficos de UML
                    - Ferramentas de apoio ao projeto e análise de software, conhecidas como ferramentas CASE (Computer-Aided Software Engineering)
                        - Estas ferramentas vão ser aonde iremos fazer os diagramas gráficos de UML
                        - Exemplo
                            
                            ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2014.png)
                            
                - Fases do RUP
                    - Inception, inclui análise de viabilidade, definição de orçamentos, análise de riscos e definição de escopo do sistema
                    - Elaboração, inclui a especificação de requisitos (via diagrama de casos de uso de UML, por exemplo), definição da arquitetura do sistema e plano para o seu desenvolvimento
                        - Ao final dessa fase, todos os riscos identificados na fase anterior devem estar devidamente controlados e mitigados
                    - Construção, na qual se realiza o projeto de mais baixo nível, implementação e testes do sistema
                        - Ao final dessa fase, deve ser disponibilizado um sistema funcional, incluindo documentação e manuais, que possam ser validados pelos usuários
                    - Transição, na qual ocorre a disponibilização do sistema para produção, incluindo a definição de todas as rotinas de implantação, como políticas de backup, migração de dados de sistemas legados, treinamento da equipe de operação, etc.
                - Pode-se repetir várias vezes o processo
                    
                    ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2015.png)
                    
                - O RUP também define um conjunto de disciplinas de engenharia que incluem por exemplo: modelagem de negócios, definição de requisitos, análise e design, implementação, testes e implantação
                    - Esses fluxos de trabalho podem ocorrer em qualquer fase, porém, espera-se que algumas disciplinas sejam mais intensas em determinadas fases
                    - Exemplo
                        
                        ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2016.png)
                        
                        - Quanto maior a área, maior a intensidade da disciplina durante cada fase
                
    - 3 - Requisitos
        - 3.1 - Introdução
            - Requisitos definem o que um sistema deve fazer e sob quais restrições
                - Requisitos funcionais → o que um sistema deve fazer, funcionalidades
                - Requisitos não-funcionais → restrições do sistema, relacioandos à qualidade do do serviço, desempenho, segurança, portabilidade e etc.
                - Requisitos do usuário → requisitos de mais alto nível, escritos por usuários, normalmente em linguagem natural e sem entrar em detalhes técnicos
                - Requisitos de sistema → requisitos técnicos, precisos e escritos pelos próprios desenvolvedores
        - 3.2 - Engenharia de Requisitos
            - Nome que se dá ao conjunto de atividades relacionadas com a descoberta, análise, especificação e manutenção dos requisitos de um sistema
            - Elicitação de requisitos
                - As atividades relacionadas com a descoberta e entendimento dos requisitos de um sistema são chamadas de elicitação de requisitos
                    - Diversas técnicas podem ser usadas na elicitação de requisitos, como entrevistas com stakeholders, aplicação de questionários, prototipação e etc.
                    - Etnografia designa a técnica de engenharia de requisitos que recomenda que o desenvolvedor se integre ao ambiente de trabalho dos stakeholders e observe como ele desenvolve suas atividades
                    - Após a elicitação, os requisitos devem ser documentados, verificados, validados e priorizados
                - Documentação
                    - No desenvolvimento ágil, a documentação de requisitos é feita por meio de user stories
                        - Por outro lado, em alguns projetos ainda se exige um documento de especificação de requisitos no qual todos os requisitos do software que se pretende construir são documentados em linguagem natural
                            - Padrão IEE 830
                                - Padrão de documentação de projetos advindo do waterfall, sendo ainda o mais usado atualmente
                                
                                ![image.png](../../assets/faculdade/periodo3/desenvolvimento-de-software/image%2017.png)
                                
                - Verificação e validação
                    - Garantir que os requisitos estejam:
                        1. Corretos
                        2. Precisos
                            
                            Não devem ser ambíguos
                            
                        3. Completos
                            
                            Não pode esquecer de especificar certos requisitos
                            
                        4. Consistentes
                        5. Verificáveis
                            
                            Deve ser possível testar se os requisitos estão sendo atendidos
                            
                - Priorização
                    - Nem sempre aquilo que é especificado pelos clientes será implementado nas releases iniciais
            - Rastreabilidade
                - Capacidade de dado trecho de um código identificar os requisitos implementados por ele e vice-versa
                - Requisitos devem ser facilmente rastreáveis para que ele possa ser identificado e atualizado de forma simples
        - 3.3 - Histórias do Usuário
            - As histórias do usuário possuem o objetivo de substituir os documentos de requisitos tradicionais (usados no Waterfall), tornar os requisitos flexiveis e ajustáveis às mudanças ao longo do desenvolvimento e garantir que as funcionalidades agreguem valor ao negócio e sejam validadas com critérios objetivos
            - Componentes
                - Cartão
                    - Pequena descrição escrita pelo cliente sobre uma funcionalidade desejada no sistema
                - Conversas
                    - Diálogo contínuo entre clientes e desenvolvedores para esclarecer e detalhar a funcionalidade ao longo do sprint
                - Confirmação
                    - Testes definidos pelo cliente para validar se a história foi implementada corretamente, devem ser escritos preferencialmente no início de uma iteração
                        - Estes testes são chamados de testes de aceitação
            - INVEST
        - 3.4 - Casos de Uso
        - 3.5 - Produto Mínimo Viável (MVP)
        - 3.6 - Testes A/B