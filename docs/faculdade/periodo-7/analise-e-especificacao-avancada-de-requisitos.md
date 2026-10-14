# ANÁLISE E ESPECIFICAÇÃO AVANÇADA DE REQUISITOS DE SISTEMAS

---

Disciplina do Centro de Informática da UFPE, ministrada pela **Profa. Dra. Edna Dias Canedo**, que aprofunda a Engenharia de Requisitos (ER) além do que é visto em disciplinas introdutórias, com foco em requisitos não funcionais, segurança, privacidade, ética e nas técnicas mais recentes — especialmente **Design Thinking, criatividade e empatia** — usadas para elicitar requisitos de software.

!!! note "Organização da disciplina"
    - **Unidade 1** — Processos da Engenharia de Requisitos
    - **Unidade 2** — Requisitos funcionais
    - **Unidade 3** — Requisitos não funcionais
    - **Unidade 4** — Requisitos de Segurança
    - **Unidade 5** — Requisitos de Privacidade
    - **Unidade 6** — Ética em Requisitos
    - **Unidade 7** — Técnicas, Metodologias, Frameworks e Ferramentas para Elicitar Requisitos

    O material-base desta página é o primeiro conjunto de slides da disciplina, que desenvolve a **Unidade 1** (processo de ER) por completo e avança bastante na **Unidade 7** (Design Thinking, criatividade e empatia como técnicas de elicitação). As Unidades 2 a 6 aparecem, neste material, apenas como os **temas da Avaliação Diagnóstica** (ver ao final) — cada aluno escolhe um deles, lê um artigo recente e apresenta à turma — e devem ser aprofundadas com o material específico de cada unidade conforme a disciplina avança.

## Unidade 1 — Processos da Engenharia de Requisitos

### O que é Engenharia de Requisitos

A ER surgiu como área de pesquisa em **1993**, com a primeira *IEEE International Symposium on Requirements Engineering*; em **1994** ocorreu a primeira *IEEE International Conference on Requirements Engineering (RE)* — conferência que segue acontecendo anualmente até hoje (ver referências externas ao final).

Três definições clássicas, trabalhadas em aula:

> "Um conjunto de atividades utilizadas para **identificar e comunicar** a finalidade de um **sistema de software**, e o contexto no qual será usado. Assim, a ER atua como a **ponte entre as necessidades reais** dos usuários, clientes e outros grupos afetados por um sistema de software, e as potencialidades e oportunidades oferecidas pela tecnologia." — **Easterbrook (2004)**

> "Uma **área multidisciplinar, centrada no ser humano e em seus problemas**. Deve investigar como as pessoas percebem e entendem o mundo ao seu redor, como interagem e como a sociologia dos locais de trabalho afeta suas ações. A ER deve se utilizar das ciências sociais e cognitivas — filosofia, psicologia cognitiva, sociologia e linguística — para fornecer fundamentos teóricos e técnicas para elicitar e modelar requisitos." — **Nuseibeh (2000)**

> "Um processo **iterativo, incremental, cognitivo, social, comunicativo e criativo**, cujos objetivos são conhecer, entender, estruturar, representar, comunicar e transcrever as informações relevantes de um sistema, extraídas de diferentes segmentos: ambiente da organização, a organização, a gerência e o desenvolvimento." — **Carvalho (2003)**

A ER normalmente ocorre em um **sistema de atividade humana**, onde "os donos do problema" são pessoas: a obtenção incorreta dos requisitos leva à disponibilização de **sistemas inadequados** às organizações (**Rocha, 2002**). O desenvolvimento de software continua sendo, hoje, uma atividade **imprevisível e de alto risco**, com pouca transparência sobre o processo e baixa garantia do que o usuário vai efetivamente receber.

!!! quote "Fred Brooks"
    "A parte mais difícil no desenvolvimento de um sistema de software é decidir, de forma precisa, **o que precisa ser construído**. Nenhuma outra parte é tão crítica quanto o entendimento do que o sistema precisa fazer. Nenhuma outra parte é tão difícil de ser corrigida depois."

!!! quote "Tom DeMarco"
    27 anos depois de cunhar a célebre frase "**você não pode controlar o que você não consegue medir**", o próprio DeMarco passou a considerar que o desenvolvimento de software é, na prática, uma atividade **imprevisível e experimental**. A qualidade de um sistema depende da qualidade dos requisitos: requisitos errados geram, inevitavelmente, sistema errado. São os requisitos que determinam escopo, prazo, custo e qualidade dos projetos.

### Evolução dos processos de desenvolvimento

Entre 1970 e 2010 os processos evoluíram em camadas sucessivas: **processos preditivos** (cascata) → **processos iterativos** (Spiral, RAD, RUP) → **processos ágeis/adaptativos** (Scrum, XP, Lean, Open UP, FDD, Crystal) → **Enterprise Agility** (agilidade em escala organizacional). As chamadas "fábricas de software" ilustram o problema histórico: produtos customizados feitos com ferramentas ineficientes e processos pouco repetíveis, pouca coordenação entre profissionais capacitados, qualidade variável entre equipes e, no fim, um produto que "satisfaz os requisitos básicos" mas deixa de atender inúmeras necessidades nunca exploradas.

A **inovação de produtos** depende de soluções criativas que atendam às necessidades reais e latentes dos usuários — daí a importância de **técnicas de criatividade e empatia** e do **Design Thinking** já na elicitação de requisitos (desenvolvido em detalhe mais adiante nesta página).

A ER pode ser vista como a **interseção** (diagrama de Venn) entre os *requisitos dos usuários* e a *solução de software* — a disciplina que reduz esse gap. De forma geral, a ER executa as mesmas atividades tanto em processos tradicionais quanto ágeis; o que muda é a **filosofia** que orienta como essas atividades são conduzidas.

### Funções da Engenharia de Requisitos

- **Estabelece uma visão comum** entre usuário e equipe de desenvolvimento sobre o que o software deve atender;
- **Documenta e controla** os requisitos para uso gerencial e da engenharia de software;
- **Mantém** artefatos e atividades consistentes com os requisitos alocados;
- **Navega** por todo o processo de desenvolvimento, da elicitação até a manutenção e evolução.

Se os requisitos não são bem capturados, o risco não é apenas atraso: pode-se construir um **excelente software para resolver o problema errado**, com perda de tempo e dinheiro, frustração da equipe e usuários insatisfeitos.

Dependendo da complexidade do projeto e da equipe, vários papéis participam da ER: engenheiro de software, analista de sistemas, analista de negócios, analista de requisitos, revisor de requisitos e demais stakeholders.

### O processo "genérico" de ER

```
Problemas do Mundo Real → Especificação do Problema → Especificação do Sistema → Sistema
         (tudo isso coberto pela Engenharia de Requisitos, com participação dos stakeholders
          e gerência de requisitos apoiada por um repositório/base de dados)
```

Em ciclo, as quatro grandes atividades se retroalimentam continuamente:

```
Elicit Requirements → Analyze Requirements → Document Requirements → Validate Requirements
        ↑__________________________|_________________________|______________________|
```

!!! note "Dados empíricos sobre o problema"
    - Pesquisas empíricas sugerem que o processo de ER é deficiente em **75%** das empresas de software.
    - Um estudo com **38 profissionais de TIC no Reino Unido** apontou "obter requisitos claros e detalhados" como o principal fator crítico de sucesso de um projeto de software.
    - Principais riscos de projetos de software, por frequência: **requisitos instáveis / mudanças frequentes (66%)**; **especificação de requisitos pobre (55%)**; **atitudes dos stakeholders — demora na aprovação, mudanças, dificuldade de comunicação (42%)**.

### Tipos de requisitos de software

| Tipo | Descrição |
|---|---|
| **Requisitos Funcionais** | Definem as funcionalidades que o sistema deve satisfazer |
| **Requisitos Não Funcionais** | Restrições e atributos de qualidade: desempenho, usabilidade, confiabilidade, segurança, privacidade, escalabilidade, portabilidade, ética etc. |
| **Requisitos Organizacionais (de domínio)** | Metas da empresa/domínio, políticas internas e estratégicas, estilo de gestão, posição de mercado, legislação (ex.: **LGPD**) — podem ser funcionais ou não funcionais |

### Stakeholders

São toda e qualquer parte envolvida ou afetada pelo sistema — clientes, usuários, competidores, órgãos reguladores etc. Envolvê-los de forma eficaz esbarra em dificuldades recorrentes:

- **Compromisso** — a alta gerência raramente tem tempo para se envolver na elicitação;
- **Habilidade** — stakeholders tendem a descrever *soluções*, não *necessidades*;
- **Envolvimento** — difícil manter interesse e participação ao longo de todo o projeto;
- **Divergência** — o modelo conceitual da equipe de analistas pode ser muito diferente do dos stakeholders;
- **Conflito de interesse** — grupos de stakeholders podem ter visões e objetivos opostos.

### Práticas por fase do processo (ciclo)

| Fase | Práticas |
|---|---|
| **Elicitação** | Identificar stakeholders; definir escopo e problema; selecionar técnicas de elicitação |
| **Modelagem** | Modelar requisitos funcionais e não funcionais; verificar erros/problemas; armazenar artefatos |
| **Análise** | Criar modelos de análise; priorizar e negociar requisitos |
| **Validação** | Revisão e inspeção de requisitos; criar casos de teste |
| **Gerenciamento** | Gerenciar versões, controle de mudanças, análise de impacto e rastreabilidade |

O fluxo linear equivalente é **Elicitação → Análise e Negociação → Documentação → Verificação → Validação**, com retroalimentação contínua para o início.

!!! example "Scaled Agile Framework (SAFe)"
    Como exemplo de processo ágil em escala organizacional, a disciplina apresenta o **Scaled Agile Framework (SAFe)**, estruturado em três camadas: **Portfolio** (Lean, Program Portfolio Management, métricas, *value streams*, épicos de negócio e de arquitetura), **Program** (roadmap, visão, *release management*, *backlog* de programa, requisitos não funcionais, *Agile Release Train*, *features*) e **Team** (Product Owner, Scrum Master, times ágeis, *backlog* do time, *sprint goals*, iterações). O framework mostra como os requisitos — incluindo os não funcionais — fluem do nível estratégico até a execução.

Para melhorar continuamente o processo de requisitos, a disciplina reforça quatro guidelines: se os requisitos não forem bem obtidos, nenhuma fase seguinte conseguirá garantir satisfação do cliente; o **envolvimento de stakeholders, clientes e usuários** é fator crítico de sucesso; **mudanças são inevitáveis** e precisam ser gerenciadas; e é fundamental garantir que **todos os envolvidos compartilhem o mesmo entendimento** sobre metas, expectativas e requisitos. Isso é resumido como um equilíbrio entre quatro peças: **Pessoas, Processo, Melhores Práticas e Ferramentas**, estimulando a troca de conhecimento em ER entre academia e indústria.

## Atividades da Engenharia de Requisitos

### Elicitação de requisitos

A elicitação cruza o **"gap semântico"** entre o mundo dos problemas reais e o mundo da solução computacional. Pode ser considerada a **atividade mais importante** do processo de ER (**Goguen, 1994**): um processo cuidadoso de análise da organização, do domínio e do processo de negócio no qual o sistema será utilizado (**Pressman, 2002**), e também um processo de **transferência de conhecimento** do stakeholder para o engenheiro de requisitos (**Kotonya, 1998**), que exige forte comunicação entre as partes.

Técnicas citadas: estudo de documentação, análise de contexto, observação, análise social, estudo etnográfico, entrevista, reunião **JAD** (*Joint Application Development*), *brainstorming*, *workshop*, grupo focal, questionário, prototipação, cenários, entre outras. As principais são detalhadas a seguir.

#### Questionários

Técnica sólida de coleta de dados demográficos e de opinião, com a vantagem de poder ser distribuída a um grupo amplo e geograficamente disperso (papel, e-mail ou web). Questões fechadas são mais fáceis de analisar; é preciso cuidado para não induzir respostas com perguntas tendenciosas, lembrando sempre que **o que as pessoas dizem nem sempre é o que fazem**.

??? note "Recomendações para elaborar questionários"
    1. Perguntas claras e específicas.
    2. Preferir perguntas fechadas, com várias opções de resposta.
    3. Oferecer anonimato.
    4. Incluir uma opção "não tenho opinião".
    5. Evitar perguntas múltiplas e complexas.
    6. Garantir que a ordem das escalas seja intuitiva e consistente.
    7. Cuidado com o uso de negativas.
    8. Evitar jargões; considerar questionários diferentes para públicos diferentes.
    9. Referência prática: **40%** de taxa de resposta é excelente; **20%** é normalmente aceitável.

#### Entrevistas

Permitem contato direto entre analista e stakeholder; aplicar no ambiente de trabalho (ou de casa) do entrevistado costuma deixá-lo mais à vontade.

| Tipo | Características |
|---|---|
| **Não estruturada** | Sem roteiro pré-definido; rica, mas difícil de replicar |
| **Estruturada** | Guiada por roteiro fixo, como um questionário; replicável, mas restritiva |
| **Semiestruturada** | Roteiro básico com espaço para questões emergentes; melhor equilíbrio entre riqueza e replicabilidade |

Boas práticas: gravar com permissão; evitar perguntas longas ou tendenciosas; evitar jargões que constranjam o stakeholder; pedir revisão de colegas e fazer um estudo-piloto. A entrevista segue cinco etapas — **introdução** (apresentação e questões éticas) → **aquecimento** (perguntas fáceis) → **seção principal** (sequência lógica, do mais fácil ao mais difícil) → **período de descanso** (perguntas leves) → **encerramento** (agradecimento, desligar o gravador). Recomenda-se vestir-se de forma similar ao entrevistado, usar carta de consentimento, **aprender a ouvir sem interromper**, registrar as respostas exatamente como dadas e apoiar-se em artefatos (protótipos, cenários) para estimular comentários.

#### Grupo focal

Sessão com um grupo de stakeholders, facilitada pelo analista, partindo da premissa de que opiniões se desenvolvem em contexto social — útil para revelar consenso e também áreas de conflito. As reuniões **JAD** são um exemplo bastante estruturado. Recomenda-se reunir de **3 a 10 pessoas**, evitar que participantes de status elevado dominem a conversa, encorajar os mais quietos e, se possível, filmar a sessão. Vantagem: baixo custo e resultados rápidos; desafio: exige um facilitador habilidoso e agenda compatível com todos.

#### Observação

Técnica de origem antropológica (etnografia), de abordagem interpretativa: o analista convive com os stakeholders observando o trabalho em seu ambiente natural. Três abordagens: **"rápida e suja"** (informal, feita a qualquer hora); **em testes de usabilidade** (ambiente controlado, vídeos e logs); **em estudos de campo** (o observador pode ter perspectiva interna ou externa ao grupo). Gera dados ricos (diários, vídeos, conversas), mas exige mais tempo, comprometimento da equipe e aceitação do observador pela comunidade de stakeholders.

#### Estudo da documentação

Boa fonte para entender procedimentos, regras e o contexto de trabalho, sem exigir envolvimento direto dos stakeholders — útil sobretudo no início da elicitação, em domínios complexos pouco conhecidos pelo analista. Riscos: baixa confiabilidade (a documentação pode não refletir a realidade) e desatualização.

#### Abordagem centrada no usuário

Foco no usuário e em suas tarefas desde o início, combinando **avaliação empírica** (contato direto, observação em ambiente natural) e **design participativo** (ciclos de design para identificar pontos de melhoria ao longo do desenvolvimento).

#### Comparando as técnicas

| Técnica | Boa para | Tipo de dado | Vantagens | Desvantagens |
|---|---|---|---|---|
| Questionários | Responder questões específicas | Qualitativo e quantitativo | Atinge muitas pessoas com poucos recursos | Design crucial; demanda tempo; baixo índice de resposta |
| Entrevistas | Explorar questões | Majoritariamente qualitativo | Entrevistador guia o usuário; maior contato | Demanda tempo; pode intimidar |
| Grupo focal | Coletar vários pontos de vista | Majoritariamente qualitativo | Ressalta consenso/conflito; maior contato | Personalidades fortes dominam |
| Observação | Entender o contexto da atividade | Qualitativo | Percepções que outras técnicas não oferecem | Muito tempo; grande volume de dados |
| Estudo da documentação | Aprender procedimentos e padrões | Quantitativo | Não compromete o tempo dos usuários | O trabalho real difere do documentado |

Escolher a técnica certa depende do tipo de informação desejada (qualitativa ou quantitativa), dos recursos disponíveis (tempo, orçamento) e da localização/acessibilidade dos stakeholders — e exige que o próprio analista domine a técnica escolhida.

#### Técnicas complementares: prototipação, persona e cenário

- **Prototipação** — representação de um produto imaginário com a qual os stakeholders interagem para explorar sua adequação, testar viabilidade técnica e esclarecer requisitos vagos. Protótipos de **baixa fidelidade** (papel/fichas) têm baixo custo e avaliam vários conceitos, mas verificam erros de forma limitada; protótipos de **alta fidelidade** (ex.: feitos no [Figma](https://www.figma.com/)) são totalmente interativos e funcionam como ferramenta de venda/marketing, mas são caros e demandam tempo.
- **Persona** — arquétipo fictício de um grupo de usuários-alvo, com nome, características, metas e histórico pessoal, usado quando há milhares de potenciais usuários e não é viável ouvir todos.
- **Cenário** — narrativa (storytelling) de uma situação real ou imaginária, sem mencionar explicitamente o uso de software. A partir da narrativa, extrai-se informação organizando as perguntas em **Who** (atores e stakeholders envolvidos), **What** (metas, o que acontece se não forem satisfeitas, o que dispara o cenário) e **How** (fluxo normal e fluxos alternativos de eventos) — de onde se deriva uma sequência de passos que já se aproxima de um caso de uso.

### Análise e negociação

Nem tudo o que se deseja em termos de software pode ser viabilizado: cabe ao engenheiro de requisitos expor os motivos que limitam certos requisitos e negociá-los, mostrando os riscos envolvidos, de modo a refinar os requisitos e assegurar que todas as partes compreendam os pontos de atenção e possíveis deficiências (**Wiegers, 2003**).

### Documentação

Os requisitos aprovados em análise e negociação devem ser registrados (**Kotonya, 1998**): a **especificação do sistema** é o produto de trabalho final do engenheiro de requisitos, e modelos gráficos ajudam a equipe a entender a estrutura do projeto (**Pressman, 2002**).

### Verificação e validação

> "A validação de requisitos examina a especificação para garantir que todos os requisitos tenham sido declarados de modo não ambíguo, que inconsistências, omissões e erros tenham sido detectados e corrigidos e que os produtos de trabalho estejam de acordo com as normas estabelecidas para o processo, projeto e produto." — **Pressman (2002)**

Verificação e validação podem ser conduzidas por seis tipos de revisão:

1. **Revisão de especialista** — um especialista avalia a qualidade dos requisitos, busca inconsistências/ambiguidades e comenta na documentação os erros e possíveis soluções.
2. **Inspeção dos requisitos** — processo detalhado, com equipe formada por seis papéis: organizador, moderador, autor, leitor, inspetor e secretário.
3. **Walkthrough** — versão mais simples e menos rígida da inspeção, com papéis que podem se acumular; identifica falhas e compartilha o entendimento do projeto.
4. **Verificação em diferentes perspectivas** — valida os requisitos sob a ótica de diferentes stakeholders (cliente, desenvolvedor, teste) e de diferentes critérios de qualidade do sistema (documentação, conteúdo, acordo).
5. **Validação por prototipagem** — usa um protótipo (descartável ou evolutivo) para testar e validar requisitos na prática junto aos stakeholders.
6. **Validação por checklist** — usada em projetos complexos, com perguntas/afirmações que ajudam a identificar erros; a checklist é atualizada continuamente conforme o projeto evolui.

A distinção clássica entre os dois conceitos: **Verificação** responde "estamos construindo o produto de maneira certa?" (comparação entre modelos); **Validação** responde "estamos construindo o produto certo?" (comparação entre o universo de informação real e um modelo).

### Gerência de requisitos

Administra os requisitos ao longo de todo o projeto, ajudando a equipe a identificar, controlar e rastrear requisitos e suas modificações a qualquer momento, mantendo a sincronia com as demais atividades do processo e avaliando impactos e riscos das mudanças. Princípios centrais: gerenciar as mudanças (aceite dos requisitos), gerenciar o relacionamento entre requisitos e gerenciar as dependências entre o documento de requisitos e os demais artefatos produzidos.

- **Identificação e armazenagem** — cada requisito precisa de um identificador único (ex.: *Req1*, *Req2* — ferramentas como o *Rational RequisitePro* organizam requisitos em árvore, com prioridade, dificuldade e localização). O ideal é armazenar com rastreio de dependências, capacidade de busca, controle de versões e visualização dos relacionamentos.
- **Gerência de mudança** — o grande problema é a **informalidade**: cerca de **80%** das mudanças em requisitos acontecem informalmente. O processo formal de mudança passa por três fases: análise do problema e especificação da mudança, análise de custo/risco e implementação da mudança.
- **Rastreabilidade** — liga claramente os requisitos às suas fontes e aos artefatos criados ao longo do ciclo de vida, permitindo rastrear o impacto de qualquer mudança (em dependências, lógica ou código de implementação dos requisitos) através de uma matriz/tabela de rastreabilidade — por exemplo, encadeando *Stakeholder Request → Feature → Use Case*.

## Unidade 7 (parcial) — Design Thinking, Criatividade e Empatia na elicitação de requisitos

### Por que ir além das técnicas clássicas

Muitos insucessos em projetos de software vêm de uma elicitação **incompleta**, que resulta em sistemas sem todas as funcionalidades necessárias ou sem espaço para inovação. Mesmo com o amplo ferramental já consolidado da ER, o mercado crescente de sistemas exige cada vez mais **empatia, inovação e criatividade** para entender as necessidades dos usuários e as particularidades de cada sistema — daí a adoção crescente de **Design Thinking (DT)**, **técnicas de criatividade** e **empatia** como complemento à elicitação tradicional.

### Design Thinking

> "O Design Thinking (DT) fornece uma metodologia para elicitar, de forma mais eficiente, as necessidades dos usuários. É uma metodologia que reúne práticas inspiradas no processo de design, para resolução e desenvolvimento de projetos, utilizando a empatia, incentivando a criatividade e a racionalidade para atender as necessidades dos usuários, convergindo para soluções inovadoras."

O objetivo central do DT é transformar observações dos usuários em **insights**, gerando produtos e serviços que melhorem a qualidade de vida de quem os usa. O foco é tratar o usuário com empatia, incentivando colaboração, participação e experimentação; a tarefa mais importante ao iniciar um projeto é entender *quem* são os usuários e *qual impacto* o produto final causará em suas vidas. No contexto de Engenharia de Software, o DT fornece uma metodologia de elicitação centrada no usuário que produz, tipicamente, uma série de protótipos convergindo para soluções inovadoras.

A literatura registra **diversos modelos de DT**, cada um com fases próprias:

| Modelo (autor/instituição) | Fases |
|---|---|
| Stanford University's D-School | Empatia → Definição → Ideação → Prototipação → Teste |
| HPI D-School | Compreensão → Observação → Ponto de Vista → Ideação → Prototipação → Teste |
| Brown | Inspiração → Ideação → Implementação |
| Hiremath e Sathiyam | Escopo → Pesquisa → Síntese → Ideação → Prototipagem → Validação → Apresentação |
| Sandino et al. | Definir → Explorar → Idealizar → Prototipar → Escolher → Implementar → Revisar |
| Coutinho et al. | Definição → Pesquisa → Ideação → Prototipação → Seleção → Implementação → Aprendizagem |
| De Paula e Araújo | Definir desafios → Observar pessoas → Formular insights → Quadro de oportunidades → Brainstorm de ideias → Tentar experimentos |
| Souza e Silva | Imersão → Ideação → Prototipação |
| DCIDT (Eris) | Divergente → Convergente |
| Dunne e Martin | Abdução → Dedução → Teste → Indução |
| DrivingBoard | Abordar → Desenvolver → Apresentar e provocar → Explorar → Refletir → Escapar |

Apesar da nomenclatura variada, todos convergem para o mesmo núcleo: **entender o usuário → gerar e refinar ideias → prototipar → validar**.

??? note "Técnicas e ferramentas de apoio ao Design Thinking citadas em aula"
    A disciplina cita um levantamento com **99 técnicas** de criatividade e Design Thinking identificadas na literatura (algumas servem a ambas as abordagens). Entre as mais citadas: Mapa de Empatia, *Clustering*, Personas, Matriz 2×2, Pesquisa 360º, *Storytelling*, *Brainstorming* (e variações: *brainwriting*, *rolestorming*, associação livre), 5 Porquês, Diagrama de Afinidade, *Customer Journey Map*, *Stakeholder Map*, Protótipos rápidos/de experiência/de serviço, *Mockup*, *Moodboard*, *Role Play*, *Walkthroughs*, *Six Thinking Hats*, Diagrama de Ishikawa, Casos de Uso, *User Story*, entre muitas outras técnicas mais específicas (Bodystorming, S.O.D.A., Synectics, TRIZ, *Lego Serious Play* etc.).

    Como ferramentas de apoio citadas: **Rabiscapp** (prototipação/esboços), **NVivo** (imersão e ideação, análise qualitativa), **Balsamiq** e **Axure RP** (prototipação), **Smaply** e **Stakeholder Circle** (empatia, *stakeholder mapping*), **Creately** (*service blueprint*), **Strategyzer** (*business model innovation*), entre outras. Há também o **DTA4RE** — *Assistente de Design Thinking para Elicitação de Requisitos* ([sites.google.com/site/dta4re](https://sites.google.com/site/dta4re/)) e um **Guia de Criatividade** para projetos de software ([sites.google.com/site/guiadecriatividade](https://sites.google.com/site/guiadecriatividade)), ambos citados como recursos práticos elaborados a partir de pesquisas sobre o tema.

### Criatividade

> Criatividade é "a capacidade de produzir um trabalho que seja ao mesmo tempo novo (original, inesperado) e apropriado (útil, adaptável em relação a tarefas e restrições)".

Segundo **Sommerville**, o desenvolvimento de software é um processo mais **criativo** que mecânico: o produto nasce de um conceito inicial e evolui até se tornar um sistema funcional. Técnicas de criatividade bem estabelecidas na indústria incluem *Brainstorming*, Cenários, *Storyboards*, Diagrama de Ishikawa, *Workshops*, Mapas Mentais, Hall da Fama e Grupo Focal; técnicas menos conhecidas mas também relevantes incluem Analogias, *Customer Journey Maps*, Heurísticas, *Ideabox* e Similaridades e Diferenças. Conhecer o repertório de técnicas e saber quando aplicar cada uma é essencial, já que elicitar requisitos é uma atividade **colaborativa** entre analista/desenvolvedor e usuários/stakeholders.

### Empatia

**Levy e Hadar** reforçam que a empatia com os usuários finais é uma habilidade de ER tão necessária quanto o conhecimento técnico e a competência social — sendo, segundo os mesmos autores, o **primeiro passo** do Design Thinking, o que tem despertado interesse das organizações por alavancar processos de design/inovação e melhorar a experiência do usuário final. **Gasparini** explora a empatia a partir de dois aspectos:

- **Empatia emocional (ou afetiva)** — resposta emocional compartilhada entre dois ou mais indivíduos (ex.: sentir medo ou excitação junto com o outro);
- **Empatia cognitiva** — capacidade de descobrir o que se passa na mente do outro, isto é, entender genuinamente o ponto de vista alheio.

A técnica mais associada à empatia é o **Mapa de Empatia (*Empathy Map*)**, que ajuda a desenhar modelos de negócio/produto a partir da perspectiva real do usuário, permitindo levantar **requisitos implícitos** ao explicitar o ambiente, comportamento, aspirações e preocupações de quem vai usar o sistema. Os *templates* trabalhados em aula organizam perguntas em torno de: o que a pessoa **vê**, **escuta**, **fala**, **faz**, **pensa e sente** (dores e desejos); sua rotina, hobbies e ambiente; sua **experiência com tecnologia** (uso de celular, tablet, apps); e, por fim, o encadeamento **Problemas → Necessidades → Soluções existentes**.

!!! example "Avaliação Diagnóstica da disciplina"
    Atividade individual: escolher um artigo recente sobre um dos dez temas a seguir, lê-lo e apresentá-lo à turma em até 45 minutos — técnicas/metodologias/frameworks/ferramentas para elicitar requisitos **funcionais** ou **não funcionais**; **qualidade de requisitos**; **técnicas de inspeção de requisitos**; **Design Thinking**, **empatia** ou **criatividade** na elicitação de requisitos; **requisitos de privacidade**; **requisitos de segurança**; e **ética em requisitos**. Esses dez temas correspondem, em boa parte, às Unidades 2 a 6 da ementa, que serão desenvolvidas em profundidade ao longo da disciplina.

## Referências e para saber mais

### Citadas diretamente no material da disciplina

- EASTERBROOK, S. **Definição de Engenharia de Requisitos** (2004), citada como referência central do curso — ver também Nuseibeh, B.; Easterbrook, S. [*Requirements Engineering: A Roadmap*](https://www.cs.utoronto.ca/~sme/papers/2000/Nuseibeh-Easterbrook-00.pdf), ICSE 2000 (*The Future of Software Engineering*), um dos artigos mais citados da área e provável origem/contexto da definição usada em aula.
- NUSEIBEH, B. **Definição de ER como área multidisciplinar** (2000).
- CARVALHO, A. **Definição de ER como processo iterativo/incremental/cognitivo** (2003).
- ROCHA, A. R. (2002) — sobre a obtenção incorreta de requisitos e sistemas inadequados.
- GOGUEN, J. (1994) — elicitação como a atividade mais importante da ER.
- KOTONYA, G.; SOMMERVILLE, I. *[Requirements Engineering: Processes and Techniques](https://eprints.lancs.ac.uk/id/eprint/57159)*. Wiley, 1998 — citado para a definição de elicitação como transferência de conhecimento e para a atividade de documentação.
- PRESSMAN, R. S. *Engenharia de Software*. 2002 (edição em português; ver também edições posteriores, ex. 6ª ed., Bookman/McGraw-Hill) — citado para elicitação, documentação e verificação/validação de requisitos.
- WIEGERS, K. E. *[Software Requirements](https://www.oreilly.com/library/view/-/0735618798/)*. 2ª ed., Microsoft Press, 2003 — citado na atividade de análise e negociação de requisitos.
- BROOKS, F. — citação sobre a dificuldade central de "decidir o que construir" (de *No Silver Bullet*, obra clássica de Brooks sobre engenharia de software, mencionada sem referência completa no slide).
- DEMARCO, T. — citação sobre a imprevisibilidade do desenvolvimento de software (autor de *Peopleware* e *Controlling Software Projects*, mencionado sem referência completa no slide).
- SOMMERVILLE, I. — citado sobre desenvolvimento de software como processo criativo (ver também Kotonya & Sommerville acima).
- LEVY, M.; HADAR, I. — citados sobre empatia como habilidade de ER e como primeiro passo do Design Thinking. Ver, por exemplo: Hadar, I. et al. [*The importance of empathy for analyzing privacy requirements*](https://arxiv.org/pdf/1908.07223), e Levy, M.; Hadar, I. [*Towards Understanding and Modeling Empathy for Use in Motivational Design Thinking*](https://arxiv.org/pdf/1907.12001).
- GASPARINI, I. — citada sobre empatia emocional/cognitiva no contexto do Design Thinking.
- Modelos de Design Thinking atribuídos em aula a: Hiremath e Sathiyam; Sandino et al.; Coutinho et al.; De Paula e Araújo; HPI D-School; DrivingBoard; Stanford University D-School; Dunne e Martin; Souza e Silva; Brown; Eris (DCIDT) — citados apenas por autoria no material, sem referência bibliográfica completa.

!!! warning "Sobre a fidelidade das citações"
    O material de aula cita a maioria dos autores acima apenas no formato **Autor, Ano** (ou só o sobrenome), sem título de obra, periódico ou DOI. Sempre que foi possível identificar com segurança a obra de origem (casos de Nuseibeh/Easterbrook, Kotonya/Sommerville, Wiegers e os artigos de Levy/Hadar), o link foi acrescentado acima como **enriquecimento externo**; os demais (Carvalho 2003, Rocha 2002, Goguen 1994, Gasparini, os autores dos modelos de Design Thinking) foram mantidos exatamente como citados em aula, sem inventar dados bibliográficos que não constam no material original.

### Leituras complementares indicadas pela professora (contexto da disciplina)

A professora compartilha periodicamente, no fórum da turma, chamadas e links para as principais conferências e periódicos da área — úteis tanto para a Avaliação Diagnóstica quanto para quem quiser acompanhar a pesquisa atual em Engenharia de Requisitos. Os links abaixo foram repassados em sala; **não foram lidos integralmente para esta página** (ao contrário das referências da seção anterior), e são listados aqui como ponto de partida para leitura futura:

**Conferências e periódicos da área:**

- [RefSQ 2026 — Research Papers track](https://refsq.org/2026/)
- [RE 2026 — Research Papers track](https://conf.researchr.org/track/RE-2026/RE-2026-research-papers)
- [RE 2026 — Workshops (Accepted Workshops)](https://conf.researchr.org/track/RE-2026/RE-2026-workshops)
- [RE 2025 — Research Papers track](https://conf.researchr.org/track/RE-2025/RE-2025-research-papers)
- [RefSQ 2025 — Research Papers track](https://refsq.org/2025/)
- [Springer, periódico *Requirements Engineering*](https://link.springer.com/journal/766) — lista de artigos
- ICSE 2026 e WER 2026 (Workshop em Engenharia de Requisitos, principal evento brasileiro da área) também foram mencionados como referências de acompanhamento.

**Artigos e preprints específicos indicados:**

- Trabalhos recentes sobre o uso de **LLMs (Large Language Models) para apoiar a Engenharia de Requisitos** — incluindo preprints no arXiv e um artigo com o título *"Using Distinct LLMs to Generate an Initial Software Functional Requirements List in Multiple Interactions"* — refletindo uma linha de pesquisa atual e ativa (geração/análise automática de requisitos com LLMs) relevante para o Design Thinking e as técnicas de elicitação vistos nesta disciplina.
- Artigos adicionais publicados em repositórios como ACM Digital Library, ScienceDirect, ResearchSquare, no repositório institucional do Politecnico di Torino (IRIS) e na AIS eLibrary, cobrindo temas afins de Engenharia de Requisitos.

    Como esses links vieram de um aviso de turma (não de um PDF anexado), eles não foram abertos/verificados nesta página — tratam-se de sugestões de leitura da professora, não de conteúdo já resumido aqui.
