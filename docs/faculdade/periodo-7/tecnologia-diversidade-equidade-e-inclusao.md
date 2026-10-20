# TECNOLOGIA, DIVERSIDADE, EQUIDADE E INCLUSÃO

!!! note "Sobre esta página"
    Disciplina **CIN0161 – Tecnologia, Diversidade, Equidade e Inclusão (TDEI)**, do Centro de Informática (CIn) da UFPE. A disciplina aborda Diversidade e Inclusão sob a perspectiva de Engenharia de Software, cobrindo **cinco dimensões de diversidade** (gênero/sexualidade, raça/etnia, idade, deficiência e neurodivergência) sob **duas perspectivas**: a dos usuários (requisitos de software) e a das equipes de desenvolvimento (aspectos humanos de Engenharia de Software), além de alguns aspectos de sustentabilidade. Boa parte do material é composta por **artigos acadêmicos** (não apenas slides), lidos previamente pelos alunos para discussão em sala — por isso esta página resume fielmente o conteúdo de cada artigo, além dos slides do professor quando existentes.

    Esta página cobre as aulas para as quais já havia material disponível no momento da escrita (Aulas 1, 2, 4, 5, 6, 7, 8, 9, 10 e 11). As demais aulas do cronograma serão adicionadas conforme o material for disponibilizado.

## Aula 1 — Apresentação da disciplina

A primeira aula (slides "Aula01-TDEI.pdf") estabelece o tom e as regras de convivência da disciplina, antes de entrar no conteúdo técnico:

!!! note "Safe space e código de conduta"
    - A disciplina se declara um **"safe space"**: ambiente de aprendizado em que é permitido errar, sem julgamentos e sem espaço para discurso de ódio.
    - Uso e respeito aos **pronomes de escolha** de cada pessoa; abertura para que pessoas neurodivergentes avisem (em privado, se preferirem) sobre necessidade de acompanhamento diferenciado.
    - Reconhecimento de que a disciplina terá naturalmente discussões com viés político, pedindo postura apartidária; o próprio professor se coloca em "construção de conhecimento" e pede que apontem se ele usar algum termo considerado inapropriado.
    - **Código de Conduta** baseado na política contra assédio da ACM (`acm.org/about-acm/policy-against-harassment`): espera-se consideração e respeito em fala/ações, nunca comportamento depreciativo/discriminatório/de assédio; forma de reportar comportamento inaceitável: formulário anônimo da disciplina ou a ouvidoria do CIn (`ouvidoria@cin.ufpe.br`).

- **Alinhamento de conceitos**: pergunta disparadora em sala — "O que você entende por Diversidade / Inclusão?".
- **Expectativas**: estrutura de reflexão em três perguntas — "De onde vim", "Por que estou aqui", "Pra onde quero ir".
- **Formato das aulas e avaliação**: palestras convidadas, leitura prévia de artigos, vídeos do YouTube, discussão em sala, seminários.

## Aula 2 — Fundamentos de Diversidade, Equidade e Inclusão em Engenharia de Software

A Aula 2 estabelece as bases teóricas do curso: o que é diversidade, equidade e inclusão (D&I/DEI), como esses conceitos se aplicam à Engenharia de Software, e por que a área tem um papel duplo — tanto de **agravar** quanto de **resolver** problemas de representatividade.

### A Nova Agenda Digital: Ética, Inclusão, Sustentabilidade, Participação e Equidade na Computação

!!! quote "Claudia Cappelli — Revista Computação Brasil (jan. 2026)"
    Artigo de opinião que analisa o documento **"Grandes Desafios da Computação no Brasil 2025–2035"** da SBC, propondo 4 eixos para a próxima década: (A) ecossistemas computacionais éticos, inclusivos e sustentáveis; (B) formação de recursos humanos para um futuro inclusivo; (C) educação para ética, inclusão e cidadania digital; (D) políticas públicas para ecossistemas digitais éticos, inclusivos e sustentáveis.

A autora defende o conceito de **inovação social** — inovação tecnológica que amplia impacto social, transformação territorial e engajamento comunitário, citando como populações mais afetadas por barreiras de acesso: comunidades periféricas, grupos racializados, mulheres, povos tradicionais e pessoas com deficiência. Para a Engenharia de Software, isso significa incorporar princípios sociotécnicos em todo o ciclo de vida: auditoria/explicabilidade de algoritmos, uso transparente e responsável de dados, padrões de acessibilidade digital e participação cidadã na avaliação de impacto social. Conclusão: "tecnologia não deve ser apenas eficiente, deve ser justa."

### Livro: *Equity, Diversity, and Inclusion in Software Engineering* (Apress, 2024)

Coletânea acadêmica de **29 capítulos em 6 partes**, organizada por Daniela Damian, Kelly Blincoe, Denae Ford, Alexander Serebrenik e Zainab Masood — primeira grande obra dedicada especificamente a D&I em Engenharia de Software (diferente de obras mais amplas sobre gênero em TI). Dados citados na Introdução: menos de 25% dos engenheiros de software no mundo são mulheres; nos EUA, menos de 5% são negros; na Nova Zelândia, apenas 8% são Māori; homens em relacionamentos do mesmo sexo têm 12 pontos percentuais menos chance de concluir graduação em STEM que homens em relacionamentos heterossexuais.

??? note "Capítulo 1 — Roads Ahead to Diversity and Inclusion by Software Engineering (Ayushi Rastogi)"
    Argumenta que a Engenharia de Software está em posição única: ao mesmo tempo em que o software **exacerba** problemas de diversidade em ritmo sem precedentes (ex.: reconhecimento facial que classifica mal populações marginalizadas), também oferece um **espaço de solução** inédito — no nível do software (algoritmos mais justos, auditoria, testes de fairness) e no nível humano (equipes mais diversas e inclusivas).

    Caracteriza estudos de D&I em ES por 4 dimensões: objetivo, contexto, stakeholders e dados/métodos. Discute **intersecionalidade** como fronteira pouco explorada: melhorar diversidade em um eixo não necessariamente melhora em outro.

    > "Unless designed to meet the requirements of any, [algorithms] are likely to miss the needs of many." — a menos que desenhados para atender às necessidades de qualquer um, os algoritmos tendem a não atender às necessidades de muitos.

??? note "Capítulo 2 — ED&I and SE: Challenges, Progress, and Lessons (Grundy et al.)"
    Revisão de **aspectos humanos** que impactam a Engenharia de Software (gênero, idade, emoções, desafios físicos/mentais, idioma, status socioeconômico, cultura/etnia), com diversos estudos empíricos próprios: 2.611 reviews de apps de COVID-19 analisados manualmente (716 relacionados a aspectos humanos, mais de 50% sobre privacidade); 1.691 comentários de issues do GitHub categorizados; personas de diferentes gerações testadas em e-commerce (Amazon/Alibaba) revelando viés de idade; checklist/ferramenta NLP para detectar viés de gênero em anúncios de vagas de ES (baseado no GenderMag).

### Interseccionalidade e metodologia de pesquisa com populações marginalizadas

O artigo **"The Choice is Yours: Intersectional Studies versus Studies of Intersectional Populations in Computing Education Research"** (Rankin, Erete, Thomas, Pinkard — SIGCSE 2024) faz uma distinção metodológica importante usando autoetnografia crítica e o **Black Feminist Thought** de Patricia Hill Collins:

| | Estudos *de* populações intersecionais | Estudos intersecionais |
|---|---|---|
| Papel do grupo-alvo | Objeto de estudo | Agente de conhecimento |
| Normas/costumes do grupo | Tratadas como "deficientes" | Valorizadas igualmente |
| Relações de poder | Não consideradas | Identificadas e exploradas |
| Resultado da pesquisa | Não compartilhado de volta | Cocriado, compartilhado |
| Objetivo final | — | Justiça social, transformação, liberdade |

> "One cannot use the same techniques to study the knowledge of the dominated as one uses to study the knowledge of the powerful." — Patricia Hill Collins

### "Lack of Diversity: Are you part of the problem or its solution?" (Mirella Moro, EduComp'22)

Ensaio com survey exploratório (118 professores brasileiros de Computação, out/2021) sobre se educadores cobrem DEI em suas disciplinas. Define o **modelo de Harrison e Klein (2007)** para diversidade (separação, variedade, disparidade) e distingue **equidade** (Lotte Bailyn: vai além de "salário igual, acesso igual") de **inclusão** (Kelly Gaither: qualidade da experiência de pertencimento).

Achados: metade dos respondentes (59/118) cobre DEI em aula; disciplinas "sociais" cobrem mais DEI (Pensamento Computacional 83,3%) que disciplinas técnicas (Programação Intermediária 29,2%); principais razões para não cobrir: "fora da ementa", falta de conhecimento, falta de tempo, medo de ofender alguém.

### Diversidade e Inclusão de Desenvolvedores de Software (SDDI) — agenda de pesquisa 2030

O artigo **"Making Software Development More Diverse and Inclusive"** (Hyrynsalmi et al., TOSEM 2025, fruto de um encontro NII Shonan 2023 com 23 pesquisadores) propõe 4 cenários para 2030 (2 utópicos, 2 distópicos) e identifica 4 eixos de pesquisa: metodologias/métricas, intersecionalidade, transferência de conhecimento (modelo da "hélice quádrupla": sociedade, academia, governo, indústria) e conexões com entendimento socioeconômico em larga escala.

!!! warning "IA generativa e SDDI"
    O artigo discute como LLMs/Copilot herdam e criam novos desafios de diversidade: GitHub Copilot produz respostas piores para prompts em chinês vs. inglês/japonês; "tinkering" (experimentação lúdica) é mais comum entre homens; desempenho de LLMs em tarefas cognitivas é mais similar a pessoas de sociedades **WEIRD** (Western, Educated, Industrialized, Rich, Democratic); desenvolvedores racialmente minorizados relatam maior "AI Skill Threat" e avaliam ferramentas de IA mais negativamente.

    Dados: apenas 17% dos especialistas em TIC na Europa são mulheres; no Stack Overflow Developer Survey 2022, ~92% dos respondentes se identificaram como homens e 77% como brancos/europeus, contra uma população global ~50% masculina e ~16% branca.

### AgeTech e interseccionalidade (idade/geração)

**"Future of AgeTech"** (Mei Lan Fang, PETRA'22) discute a **divisão digital** ("digital divide") entre pessoas idosas, com cinco fatores sociais associados (exposição à tecnologia via educação, renda, idade/geração, comorbidades físicas/cognitivas, contato social) e propõe o modelo da **"Intersectional Place Perspective" (IPP)** — combinação de feminismo intersecional e teoria de lugar para pensar equidade digital no envelhecimento.

### Manifesto IDEA

O PDF enviado para esta aula ("Um manifesto em favor da inclusão...") é na verdade uma **proposta de mesa temática** do EduComp'24 para apresentar o **Manifesto IDEA** (Inclusão, Diversidade, Equidade, Acessibilidade) da SBC, redigido pelo GT IDEA da CEduComp. O manifesto completo está publicado na *SBC Horizontes* (março de 2024) — não reproduzido neste PDF, apenas sua apresentação institucional.

## Aula 3 — Engenharia de Requisitos da Opressão

!!! note "Sobre esta seção"
    Não havia PDF enviado para esta aula. Como o tema do cronograma ("Engenharia de Requisitos da Opressão") corresponde diretamente ao keynote de **Amy J. Ko** na RE'21 — já citado como referência em outros materiais da disciplina (Aula 7) —, esta seção foi construída a partir de fontes públicas sobre essa palestra e sobre o programa de pesquisa da autora, em vez de um PDF de aula. As fontes estão listadas ao final da seção.

### O keynote "Requirements of Oppression" (Amy J. Ko, RE'21)

Apresentado em 22 de setembro de 2021 na 29ª *IEEE International Requirements Engineering Conference* (RE'21), o keynote de **Amy J. Ko** (University of Washington, Information School e Paul G. Allen School of Computer Science and Engineering) questiona as lentes tradicionais com que a Engenharia de Requisitos enxerga seu próprio objeto de trabalho.

**Argumento central:** a Engenharia de Requisitos tradicionalmente trata requisitos de forma técnica, contratual e abstrata — enquadramento que funcionou bem para sistemas operacionais e linguagens de programação, mas não atende às necessidades de pessoas nas margens da sociedade. Segundo a autora, o software ainda falha com grupos marginalizados em dimensões como classe, riqueza, sexo, gênero, raça, etnia, capacidade (deficiência) e cidadania:

> "Software still fails to meet the needs of people at the margins of society." — o software ainda falha em atender às necessidades de pessoas nas margens da sociedade.

Embora a área já tenha avançado ao incorporar dimensões humanas, sociais, organizacionais e éticas, Ko argumenta que essas abordagens continuam enquadrando requisitos sobretudo pelas lentes da **ética**, da **política** e do **direito** — e que definir requisitos por qualquer lente que não seja a da **justiça** pode levar à marginalização, à injustiça e à opressão. A palestra apresenta três estudos de caso sobre como requisitos se tornam opressivos, e propõe uma lente alternativa: a Engenharia de Requisitos como uma forma de **produção cultural**, que exige uma postura mais crítica e ativista por parte de quem projeta software.

### A trajetória pessoal da autora e os três argumentos da "educação crítica em computação"

Em outras palestras e materiais públicos (ex.: "Critical Computing Education", UC Irvine, 2021), Ko situa esse argumento dentro de uma trajetória pessoal: como mulher trans, relata experiências próprias de opressão mediada por tecnologia — revistas em aeroportos após escaneamento corporal, nomes antigos mantidos em bases acadêmicas, sistemas de saúde excludentes, cyberbullying. A partir dessa experiência, ela revisita o princípio de justiça que orientava seu próprio trabalho:

- **Antes:** a computação deve ser útil e acessível a todos; todos devem poder usá-la.
- **Depois:** a computação deve respeitar a dignidade de todas as pessoas, e todos devem poder usá-la para **resistir e desmontar sistemas de opressão**.

Isso se desdobra em três argumentos:

1. **A computação tem limites.** Há o mito de que a tecnologia resolve qualquer problema social (pobreza, crime, fome, mudança climática), mas ela pode desviar recursos de mudanças estruturais necessárias — ex.: juízes que delegam decisões a previsões algorítmicas enviesadas, sistemas automatizados que negam benefícios sociais. A computação não é neutra: código costuma conter erros, incorpora os valores de quem o criou, e frequentemente gera novos problemas em vez de resolver os antigos.
2. **Os dados têm limites.** Dados são tratados como algo inerte, mas na verdade registram o passado e tendem a reproduzi-lo — ex.: dados de criminalidade racialmente enviesados que sustentam vigilância desproporcional; dados cisnormativos que expõem pessoas trans a constrangimentos; modelos de capacidade física que tornam telas sensíveis ao toque inacessíveis a pessoas com deficiência motora.
3. **A área de Computação tem responsabilidade.** A cultura da área valoriza inovação, disrupção, poder e velocidade, frequentemente terceirizando escolhas morais para investidores ou para um discurso de determinismo tecnológico ("se pode ser feito, será feito"). Para Ko, as escolhas de design são coletivas e carregam os valores de quem as faz — os desenvolvedores são responsáveis pelo que criam.

!!! tip "Recomendações da autora para a comunidade"
    - **Pesquisadores:** considerar tanto o poder quanto o risco das próprias inovações.
    - **Docentes:** questionar quais valores o ensino promove, quem ele empodera, e como exemplos e avaliações reforçam (ou não) esses valores.
    - **Professores(as):** reconhecer o poder que têm — e que ser "apolítico" no ensino também é uma posição política.
    - **Todos:** aprender a ter conversas difíceis sobre computação e justiça.

### Trabalho relacionado: engenharia de requisitos "embutida em justiça"

O keynote de Ko dialoga com um movimento mais amplo de propostas que buscam incorporar justiça explicitamente ao processo de levantamento de requisitos, em vez de tratá-la como preocupação posterior ou puramente ética/jurídica. Um exemplo é o **Justice-Embedded Requirements Engineering (JERE)** (Arkhurst & Fu, DESIGN 2024, Georgia Tech/Univ. of Wisconsin–Madison): um processo que ajuda engenheiros a considerar, desde o início do projeto, os impactos de um sistema sobre comunidades historicamente marginalizadas e vulneráveis — demonstrado no artigo com um exemplo de sistema de energia solar concentrada, sob a ótica da **justiça energética** (*energy justice*).

### Referências

- Ko, Amy J. **"Requirements of Oppression."** Keynote, 29th IEEE International Requirements Engineering Conference (RE'21), 22 set. 2021. [conf.researchr.org/details/RE-2021/RE-2021-keynotes/2/Requirements-of-Oppression](https://conf.researchr.org/details/RE-2021/RE-2021-keynotes/2/Requirements-of-Oppression)
- Ko, Amy J. **"Critical Computing Education."** Palestra/slides, UC Irvine, 2021. [faculty.washington.edu/ajko/slides/UCIrvine2021CriticalComputingEducation.pdf](https://faculty.washington.edu/ajko/slides/UCIrvine2021CriticalComputingEducation.pdf)
- Arkhurst, B. K.; Fu, K. **"Justice-Embedded Requirements Engineering (JERE) for system design."** 18th International Design Conference (DESIGN 2024), DS 129, pp. 2493–2502, 2024.

## Aula 4 — Viés algorítmico, Fairness e explicabilidade em IA

### Software Fairness Debt (de Souza Santos, Fronchetti, Freire, Spinola — TOSEM 2025)

*Scoping review* de **39 estudos** (2017–2023) sobre fairness de software em ICSE/FSE/ICSME/EMSE/TSE/IEEE Software, propondo o conceito central de **"Software Fairness Debt"**:

> "A collection of design, implementation, or managerial constructs that provide immediate advantages in developing AI solutions but create long-term challenges with significant societal impacts by introducing biases that are difficult and costly to identify or correct in the long run."

O artigo identifica **oito causas-raiz de viés** (Cognitive, Design, Historical, Model, Requirement, Societal, Testing, Training Bias) e propõe um **roadmap de pesquisa em 4 estágios/6 metas**: Foundation, Framework, Support e Action. Diferente da dívida técnica (foco interno) e da dívida social (foco na equipe), a dívida de fairness tem a **sociedade** como preocupação central — seus efeitos extrapolam o ambiente de desenvolvimento.

### Complementos externos citados pelo slide da aula

!!! tip "Material complementar da Aula 4"
    Conforme indicado pelo próprio material da aula, dois recursos externos complementam o tema de viés em IA:

**1. "It's Too Easy to Hide Bias in Deep-Learning Systems"** (Matthew Hutson, IEEE Spectrum, jan. 2021) — explora o problema do **"fairwashing"**: sistemas podem parecer justos sem ser (excluir atributos protegidos não basta, pois outros dados funcionam como indicadores indiretos). Discute técnicas de manipulação de explicações: **LaundryML** (Aïvodji et al.) gera regras simples aparentemente justas para sistemas enviesados; Zachary Lipton mostrou que redes que não "prestavam atenção" a palavras de gênero ainda usavam gênero para classificar médicos. Apresenta o debate entre **Cynthia Rudin** (defende IA interpretável por design, não explicações sobre caixas-pretas) e **Zachary Lipton** (defende que XAI continua necessária, pois redes profundas são indispensáveis para várias tarefas).

**2. Vídeo "How to make AI systems more just"** (série *On What Matters*, Ford Foundation, 2023) — conversa entre Hilary Pennington e **Dr. Timnit Gebru**, fundadora do DAIR (Distributed Artificial Intelligence Research Institute), cujo princípio central é: *"AI is not inevitable, its harms are preventable"*. O episódio discute como uma abordagem inclusiva e colaborativa na criação de sistemas de IA pode lidar com os benefícios desiguais e os impactos prejudiciais da tecnologia na sociedade.

## Aula 5 — Raça, racismo, colonialidade e tecnologia/IA

A Aula 5 é a mais extensa do curso, reunindo 17 textos sobre racismo algorítmico, colonialismo digital, teoria racial crítica aplicada à Computação e justiça educacional.

### Fundamentos teóricos sobre raça e racismo no Brasil

Um trecho de capítulo teórico (base de uma dissertação sobre acesso de pessoas negras à Computação) apresenta os conceitos fundamentais do campo:

- **Racismo estrutural** (Sílvio Almeida): integra a organização econômica e política da sociedade; subtipos incluem racismo institucional, científico, epistemológico, recreativo e ambiental.
- **Preconceito racial** (juízo baseado em estereótipos) vs. **discriminação racial** (tratamento diferenciado efetivo, direto ou indireto/"colorblindness").
- **Mito da democracia racial**: ideologia que oculta a desigualdade e a violência sexual histórica contra mulheres negras e indígenas no Brasil.
- **Branquitude** (Lourenço Cardoso): "o lugar estrutural privilegiado de onde o sujeito branco vê os outros e a si mesmo" — distinguida em **acrítica** (não reconhece o próprio privilégio, naturaliza o racismo) e **crítica** (reconhece o privilégio e se engaja no antirracismo); **branquidade** é a dimensão fenotípica/estética da brancura, distinta da branquitude como posição política.

!!! note "Dados históricos citados"
    ~15 milhões de africanos escravizados trazidos à África toda / ~5 milhões ao Brasil; Pernambuco recebeu quase 1 milhão de pessoas escravizadas — mais que os EUA inteiro. Políticas públicas de acesso ao ensino superior citadas: FIES (1999), PROUNI (2004), Lei de Cotas 12.711/12, Lei 12.990/14 (cotas em concursos), heteroidentificação.

### Racismo algorítmico e reconhecimento facial

O capítulo **"O Racismo Algorítmico Frente aos Sistemas de Reconhecimento Facial"** (Oliveira & Spolle, no livro *Estudos Sociopolíticos da Inteligência Artificial*) analisa a campanha **#TireMeuRostodaSuaMira** e o projeto **Smart Sampa** (20–40 mil câmeras planejadas em SP), usando os conceitos de **necropolítica** (Achille Mbembe) e **racismo algorítmico** (Tarcízio Silva).

!!! danger "Dados centrais"
    **90% a 90,5%** dos presos por reconhecimento facial no Brasil são pessoas negras; **86%** dessas prisões são indevidas (Cruz, 2022 / Rede de Observatórios da Segurança). O estudo de Joy Buolamwini e Timnit Gebru (2018) é citado: taxa de erro >30% para mulheres negras vs. <0,7% para homens brancos em sistemas de reconhecimento facial.

### Microagressões raciais digitais

O capítulo "Racismo Algorítmico e Microagressões Raciais no Mundo Digital" apresenta 3 casos: (a) reconhecimento facial e segurança pública (retoma dados de 90,5%); (b) busca no Google Imagens por "mulher negra dando aula" retornando conteúdo pornográfico em 2019 (ligado à hipersexualização histórica da mulher negra — Angela Davis; dados: 61,1% das vítimas de feminicídio no Brasil são mulheres negras); (c) censura de termos antirracistas pelo TikTok em 2021, enquanto termos equivalentes pró-brancos eram aceitos.

> "As microagressões podem assumir uma série de formas diferentes, mas são definidas como breves indignidades verbais, comportamentais ou ambientais corriqueiras, sejam intencionais ou não intencionais, que comunicam ofensas hostis, depreciativas ou negativas dirigidas a grupos minoritários e/ou sub-representados." (Blosser, 2020)

### *Race After Technology* (Ruha Benjamin) e o "Novo Código de Jim"

Resenha do livro de Ruha Benjamin, *Race After Technology: Abolitionist Tools for the New Jim Code*, que propõe o conceito central do **"Novo Código de Jim"**: "o emprego de novas tecnologias que refletem e reproduzem desigualdades existentes, mas que são promovidas e percebidas como mais objetivas e progressistas que os sistemas discriminatórios de uma era anterior."

As **quatro dimensões** do Novo Código de Jim:

1. **Projeto Discriminatório** (*Engineered Inequity*): desigualdades projetadas diretamente na tecnologia — ex.: concurso de beleza julgado por IA (Beauty AI) que reproduziu racismo científico; sistema de risco de reincidência penal nos EUA que marcava réus negros como futuros criminosos duas vezes mais que réus brancos.
2. **Exposição Codificada** (*Coded Exposure*): Google Photos/Facebook rotulando pessoas negras como "gorilas"/"primatas"; fenotipagem forense baseada em DNA.
3. **Benevolência Tecnológica**: ferramentas que pretendem corrigir viés social mas reforçam discriminação — ex.: tornozeleiras eletrônicas como alternativa ao encarceramento, criando "realidades verticais" diferentes por grupo social.
4. **Ferramentas Abolicionistas**: app **Appolition** (troco de doações paga fiança de pessoas negras presas — libertou mais de 65 pessoas desde 2017); defesa da auditoria de algoritmos.

> "Quanto mais as máquinas aprendem a pensar como humanos, mais tendem a se tornar racistas." — Ruha Benjamin

### Colonialismo digital e geopolítica da IA

Dois textos de **Deivison Faustino e Walter Lippold** desenvolvem o conceito de **colonialismo digital**, com três dimensões: (1) extração massiva de dados ("acumulação primitiva de dados"); (2) danos socioambientais de datacenters (treinamento do LaMDA do Google gerou ~36.000 toneladas de CO2); (3) concentração geopolítica de poder nas big techs.

O capítulo "O DeepSeek, a geopolítica da IA e as insurgências possíveis" analisa a disputa EUA-China em IA e o lançamento do **DeepSeek** (treinado com chips de segunda linha, custo declarado de US$2,98 milhões) como uma "brecha insurgente" rumo à descentralização — mas ressalvando que "open weight" não é o mesmo que código totalmente aberto (dataset, código de pré-treinamento e de alinhamento permanecem fechados).

### IA Generativa, discriminação e impactos sociais

Coletânea organizada por **Tarcízio Silva** (2025) com 9 capítulos, cobrindo: imagens de controle (Patricia Hill Collins, Lélia Gonzalez) reproduzidas por IA generativa; viés em datasets de treinamento (estudo da Bloomberg: modelo gerou imagens de pele mais escura 70% das vezes para "trabalhador de fast-food" nos EUA, embora 70% desses trabalhadores sejam brancos); uso não autorizado de IA para recriar pessoas falecidas; técnicas **Nightshade** e **Glaze** para proteger artistas; tipologia de riscos (dados, trabalho humano, impactos ambientais, outputs); IA e arquitetura racial-punitiva do Estado (70% da população carcerária brasileira é negra); crise ambiental (Google emitiu 14,3 milhões de toneladas de CO2 em 2023, +48% desde 2019); caso **Timnit Gebru/Margaret Mitchell** demitidas do Google (2020) após o paper "Stochastic Parrots".

### Design, raça e o mito da escultura branca

O ensaio **"Um ensaio sobre Design e Raça"** (Mateus J. J. Paulo Filho, UX Collective) questiona a pretensa neutralidade/universalidade do design, usando **Frantz Fanon** e **Guerreiro Ramos** (conceito de **branquidade**: posição de privilégio sistemático originada no colonialismo). Desconstrói o mito do mármore branco greco-romano (pesquisa do arqueólogo Mark Abbe): estátuas antigas eram coloridas, e o mito do "mármore branco" foi inventado pelo Renascimento e reapropriado pelo nazismo/fascismo.

### Justiça educacional em Computação

Três artigos tratam de currículos de Computação "centrados em justiça" (*justice-centered*):

- **"Towards Justice in Undergraduate Computer Science Education"** (Medina-Kim, ASEE 2021): critica iniciativas de "ampliação da participação" por tratarem estudantes sub-representados como "mão de obra futura" sem questionar o setor tecnológico; propõe o curso **PEPC** (Power, Equity, and Praxis in Computing).
- **"Justice-Centered Educational Programming Language Design"** (Ko, Shapiro, Everson, Kivuva — ACM TOCE 2026): propõe o framework **ALTCODE**, com sete requisitos para linguagens de programação educacionais justas: **Accessible, Liberatory, Transparent, Cultural, Obtainable, Democratic, Enduring**. Discute exemplos reais (Scratch, Python, Hedy, Quorum, Processing) analisados sob cada requisito.

    > "The master's tools will never dismantle the master's house." — Audre Lorde, citada para questionar se EPLs focadas apenas em inclusão, sem reestruturar poder, promovem justiça de fato.

- **"Justice-Centered Computing Curriculum Design in Informal Learning Environments"**: usa **duo-etnografia** para examinar design curricular de computação em ambientes de aprendizagem informal.

### Interseccionalidade na extensão universitária

**"Explorando Interseccionalidades e Experiências Formativas na Computação"** (Marques et al., CSBC/WEI 2026) analisa dados do **Programa Meninas Digitais / RENACEE-MD** (232 atividades, 3.143 participantes em 2025, 10 instituições pelo Brasil), encontrando que participantes do gênero masculino, estudantes do ensino fundamental e da região Norte apresentaram menor probabilidade de atribuir nota máxima de satisfação — evidência de que marcadores interseccionais estruturam experiências mesmo diante de alta satisfação geral.

### Diversidade e produtividade em equipes ágeis

Dois estudos empíricos brasileiros conectam diversidade (incluindo racial) a desempenho de times: um estudo com 4 equipes ágeis (usando o **Índice de Blau**) encontrou que os times mais diversos tiveram melhores indicadores de produtividade/qualidade; outro descreve pesquisa-ação sobre gestão de diversidade étnico-racial em consultorias de tecnologia, propondo um modelo categorizado em **inclusão, desenvolvimento e representação**.

## Aula 6 — Gênero e Engenharia de Requisitos

### GenderMag: o método e seus estudos

O **GenderMag (Gender-Inclusiveness Magnifier)** é um método de inspeção de usabilidade criado por Margaret Burnett e colegas para revelar problemas de inclusão de gênero em software, documentado em dois artigos complementares:

!!! note "As cinco facetas de diferenças de gênero"
    Motivação, Estilo de Processamento de Informação, Autoeficácia Computacional, Aversão a Risco, e **Tinkering** (tendência a explorar/experimentar) — cada uma sustentada por múltiplos estudos empíricos (ex.: Excel, ferramentas de ML, Gidget).

O método combina quatro **personas facetadas** (Tim, Abby, Patricia e Patrick — as duas últimas idênticas entre si, cobrindo um valor intermediário para evitar estereotipagem binária) com um **Cognitive Walkthrough especializado por gênero**. O artigo canônico (*Interacting with Computers*, 2016) relata três estudos formativos; o *field study* do CHI'16 testou o método em três organizações reais dos EUA:

- As equipes encontraram problemas em 55 de 99 ações avaliadas (55%); **25% de todas as ações** tinham problemas ligados a gênero.
- Uma equipe descreveu o efeito do método: *"GenderMag has already infected us."*
- Conclusão recorrente: inclusão de gênero não está em categorizar pessoas por gênero, mas em apoiar uma gama de valores de facetas (pluralismo).

### GIRE: Gender-Inclusive Requirements Engineering

O modelo **GIRE** (Nunes, Moreira, Araujo — *Data & Knowledge Engineering*, 2023) propõe um modelo conceitual (diagrama UML) com quatro componentes — **Gender** (espectro, não binário), **Sociocultural Context**, **Human Actor**, **Software System** — e uma taxonomia de **24 características** empiricamente ligadas a gênero (risco, confiança, estilo de processamento de informação, tinkering etc.). Avaliado com 31 participantes: 83,9% consideraram o modelo útil ou muito útil.

!!! note "Dados sobre gênero em TIC citados no artigo"
    Mulheres são apenas **3%** dos graduados mundiais em TIC; ocupam **24%** dos empregos do setor digital; **2–4%** dos desenvolvedores open source; homens têm 15% mais chance de serem seniores e 2–4x mais chance de gerência/executivo.

## Aula 7 — Acessibilidade, Design Systems e consciência de diversidade

### Design Systems como interface para acessibilidade

**"Design Systems and Component Packages as an Interface for Accessibility"** (Diniz & Gama, SBES'24) avaliou os Design Systems das 5 maiores empresas digitais (Forbes Top 100) contra 46 diretrizes WCAG 2.2 aplicáveis: **Apple HIG** teve o melhor desempenho (39/46 "complies"), seguido por Fluent 2/Microsoft, One UI/Samsung e Material Design/Google. Os autores então criaram a **ALib**, biblioteca de componentes acessível baseada no Apple HIG, testada por 8 desenvolvedores — a maioria só considerava acessibilidade relevante em apps destinados *especificamente* a pessoas com deficiência.

### LLMs geram código acessível?

**"Designing for all? Accessibility of native android interfaces from large language models"** (Rabelo et al., 2026) testou ChatGPT-3.5/4o, Sabiá-3 e GitHub Copilot gerando 288 telas Android, encontrando **702 erros de acessibilidade** no total (média 2,44/tela).

!!! warning "Achado contraintuitivo"
    Pedir explicitamente acessibilidade no prompt (**AccessReq**) frequentemente **aumentou** o número de erros em vez de reduzi-los (t=-2,739, p=0,00694) — por exemplo, adicionando `contentDescription` desnecessariamente, confundindo leitores de tela. Prompts em **inglês geraram significativamente menos erros** que em português, usando o mesmo modelo.

    > "LLMs are valuable productivity aids but are currently inadequate as stand-alone generators of accessible UI code."

### Acessibilidade de jogos para pessoas com deficiência visual

Revisão de literatura (Agrimi et al., *Soft Computing*, 2024) sobre acessibilidade de jogos (principalmente de tabuleiro/cartas) para pessoas com deficiência visual (285 milhões no mundo segundo a OMS, 2018; 39 milhões cegas). Discute sonificação, ecolocalização, HRTF (simulação sonora 3D) e um estudo de caso com CNN (94,5% de acurácia) para identificar peças do jogo de tabuleiro "Quantik" por imagem.

### Consciência de desenvolvedores sobre diversidade de usuários

**"How Much Do You Know About Your Users?"** (Gama et al., REW 2024) — survey com 51 desenvolvedores brasileiros + 6 entrevistas com stakeholders de produto, sobre consciência das cinco dimensões de diversidade (Raça/Etnia, Gênero, Deficiência, Neurodiversidade, Idade).

!!! note "Achado central"
    Muitos desenvolvedores **equiparam acessibilidade a diversidade** — a maioria das respostas sobre guidelines mencionou apenas WCAG, ignorando outras dimensões. **Design Systems emergiram como mecanismo** citado por 5 de 6 entrevistados para incorporar D&I de forma transversal.

Trabalhos relacionados (do mesmo grupo de pesquisa, UFPE): **"Mobile Accessibility Guidelines Adoption..."** (de Almeida & Gama, CHASE 2021) encontrou que 64% dos desenvolvedores brasileiros desconhecem o WCAG (vs. 27% dos designers); **"On the Awareness about Diversity and Inclusion..."** (Gama, MO2RE 2024) é um artigo de posicionamento que sintetiza desafios por dimensão e propõe pontos de ação, incluindo o uso do GIRE e do GenderMag como ferramentas concretas.

## Aula 8 — Acessibilidade para pessoas autistas

### Frameworks de acessibilidade para TEA

O **GAIA** (Guia de Acessibilidade de Interfaces para Autismo — Britto & Pizzolato, UFSCar, *RBIE* 2018) é um dos guias centrais da aula: um conjunto de **28 recomendações** organizadas em **10 categorias** (Vocabulário Visual e Textual, Customização, Engajamento, Representações Redundantes, Multimídia, Resposta às Ações, Affordance, Navegabilidade, Estado do Sistema, Interação com Tela Sensível ao Toque), construído a partir de revisão bibliográfica + survey com 105 profissionais de TI + entrevistas com 7 famílias de crianças com TEA.

!!! note "Dados do survey do GAIA"
    **54%** dos profissionais de TI não consideram pessoas com deficiências cognitivas/neurais/de aprendizagem (DCNA) em seus projetos; **80%** afirmaram que a existência de recomendações os motivaria a incluí-las; **33,3%** desconhecem totalmente o WCAG.

O **AutismGuide** (Aguiar et al., *Behaviour & Information Technology*, 2022) é outro guia de referência, consolidando **155 recomendações** da literatura em **69 recomendações finais**, categorizadas pelos Critérios Ergonômicos de Bastien & Scapin (1993).

Uma **revisão de mapeamento** (Ribeiro et al., SBSI 2025) sobre acessibilidade para **adultos** autistas (a maioria da literatura foca em crianças) identificou 9 frameworks e usou a **Teoria da Carga Cognitiva** (Sweller) como lente: a barreira mais citada (17 de 23 artigos) é a de **processamento** (compreensão de imagens/texto/página). Um estudo comparativo (Ribeiro et al., IHC 2024) avaliou 8 apps de mobilidade urbana brasileiros com o GAIA — Google Maps teve a melhor pontuação (69/88), bicicletas compartilhadas a pior (~40%); **Personalização** e **Resposta a Ações** foram deficientes em todas as categorias de app.

## Aula 9 — Acessibilidade para pessoas idosas

Três revisões sistemáticas sintetizam os desafios de usabilidade para usuários idosos:

- **Dodd, Athauda & Adam (2017)** — 30 estudos, 3 categorias de desafios: físicos (visão, motricidade, audição), experiência com computadores, cognitivos (atenção, memória de trabalho, memória de longo prazo).
- **Elguera Paez & Zapata Del Río (2019)** — 28 estudos sobre apps móveis: idosos precisam de **50–100% mais tempo** que adultos <30 anos para completar tarefas; recomenda alvos de toque mínimos de 48dp×48dp.
- **Amouzadeh et al. (2025)** — 132 estudos (PRISMA): temas de design que ajudam incluem navegação simplificada, interfaces legíveis, elementos *touch-friendly*, interação por voz, e **design participativo/co-design** (ex.: app SMART diet diary cocriado com usuários com degeneração macular).

O **AdaptForge** (Wickramathilaka et al., *Automated Software Engineering*, 2025) propõe uma solução técnica: duas DSLs (Context DSL e Adapt DSL) para gerar automaticamente variantes de interface Flutter adaptadas a idosos, avaliada com 18 desenvolvedores (17 deram feedback positivo) e 22 idosos.

!!! note "Dado demográfico"
    Segundo a OMS, **1 em cada 6 habitantes do mundo** terá 60+ anos até 2030; a população global 60+ deve **dobrar para mais de 2 bilhões** até 2050.

## Aula 10 — Desigualdades de gênero em equipes de software

!!! note "Nota sobre numeração"
    Os arquivos de material enviados para esta aula estavam rotulados "aula 11" na pasta original. Pelo conteúdo (todo centrado em desigualdade de gênero em equipes de desenvolvimento), eles correspondem ao item 10 do cronograma oficial ("Desigualdades de gênero em equipes de software", 14/10/2026) — por isso foram posicionados aqui.

### Benefícios e dificuldades percebidas da diversidade de gênero

**"Benefits and Difficulties of Gender Diversity on Software Development Teams"** (Kohl & Prikladnicki, SBES 2022) — survey qualitativo (88 respondentes) usando a técnica do **Empathy Map Canvas**: entre os benefícios percebidos, destaca-se "Women Supporting Women" (o tema mais citado); entre as dificuldades, "No Diversity and Old Patterns" (times/lideranças majoritariamente homens brancos cisgêneros) e "Unawareness" (parte dos respondentes acha que diversidade "não importa").

> "It is an elitist area. And the elite has one color and one gender."

### Barreiras enfrentadas por mulheres desenvolvedoras no Brasil

**"Breaking one barrier at a time"** (Canedo et al., SBES 2021) — 17 entrevistas analisadas via Grounded Theory, identificando três categorias: **Challenges** (falta de confiança — a subcategoria mais citada), **Barriers** (viés de gênero na alocação de tarefas) e **Gender Issues** (assédio, linguagem sexista). Apenas 1 de 17 entrevistadas relatou time com 8-10 mulheres em liderança; a maioria relatou apenas uma mulher líder (ou nenhuma).

### Micro-inequidades e idade como fator de confusão

**"Mind the gap: gender, micro-inequities and barriers in software development"** (Guzmán, Fischer, Kok — *Empirical Software Engineering*, 2024) — survey global com 359 respondentes (49,3% mulheres):

!!! note "Resultados estatisticamente significativos"
    - Mulheres têm odds **3,22x maiores** de serem excluídas de oportunidades de networking.
    - **43,5%** das mulheres experimentaram assédio diretamente (odds 2,62x maior que homens).
    - **76%** das mulheres experimentaram ou testemunharam sexismo; **57%** diretamente (vs. 14% dos homens).
    - "Team dynamics" (ter que se provar repetidamente) é a maior fonte de tratamento injusto relatada por mulheres (64%); para homens, a maior categoria é "technical and project issues" (44%).

    > "I have to prove myself over and over and over and over again. Past accomplishments mean nothing. Male colleagues see me as someone that they can teach."

### Viés de gênero no GitHub: pull requests e o complemento do The Guardian

**"Gender Bias in Open Source: Pull Request Acceptance of Women Versus Men"** (Terrell et al., *PeerJ Preprints*, 2016) — até então o maior estudo sobre o tema, usando "gender linking" (e-mails do GitHub vinculados a perfis do Google+) em 1,4 milhão de contas.

!!! danger "O achado contraintuitivo"
    Mulheres têm taxa de aceitação de pull requests **maior** que homens (78,6% vs. 74,6%), mesmo fazendo mudanças maiores e em todas as 10 linguagens de programação mais comuns — contrariando a hipótese inicial dos próprios autores. Mas quando o gênero é **identificável** (foto/nome), a vantagem desaparece: a taxa de aceitação de mulheres **outsiders** cai de 71,8% (perfil neutro) para **62,5%** (perfil identificável como mulher).

    > "The frequent refrain that open source is a pure meritocracy must be reexamined."

Esse estudo foi amplamente noticiado, incluindo pelo artigo complementar indicado para esta aula — **"Women considered better coders – but only if they hide their gender"** (*The Guardian*, 12 fev. 2016) — que reportou os mesmos achados (mulheres com perfil neutro têm PRs aceitos com mais frequência que homens, mas a vantagem desaparece/inverte quando o gênero é revelado), amplificando a discussão pública sobre o viés de gênero em comunidades de código aberto além do meio acadêmico. A teoria final dos autores combina **viés de sobrevivência** (mulheres menos competentes abandonam a área mais cedo) com **discriminação direta** contra mulheres identificáveis como tal (um viés que McLoughlin, 2005, chamou de **"Type III bias"**).

## Aula 11 — Developer Experience e LGBTQIAPN+ em equipes de software

!!! note "Nota sobre numeração"
    Os arquivos de material enviados para esta aula estavam rotulados "aula 10" na pasta original. Pelo conteúdo (que inclui diversidade percebida em geral, mas sobretudo um bloco extenso sobre Developer Experience e pessoas LGBTQIAPN+ em equipes), eles correspondem ao item 11 do cronograma oficial ("Developer Experience e LGBTQIAPN+ em equipes de software", 21/10/2026) — por isso foram posicionados aqui.

### O panorama da pesquisa: diversidade percebida em Engenharia de Software

O SLR de referência **"Perceived diversity in software engineering"** (Rodríguez-Pérez, Nadri, Nagappan — *Empirical Software Engineering*, 2021) mapeou **131 estudos** (2003–2020), definindo **diversidade percebida** como "aspectos internos de diversidade com os quais os indivíduos nascem (gênero, idade, raça e nacionalidade)".

!!! danger "Lacuna racial"
    **Gênero** é a dimensão mais estudada (61% dos estudos); **raça** é a menos estudada (apenas 2%). Em open source, homens contribuíram com mais de 92% do código nos últimos 50 anos; mulheres só chegaram a 10% das contribuições anuais em 2019.

    > "This SLR show that SE research in racial diversity is very limited [...] we would like to create a 'call for future action' to research quantitatively and qualitatively racial diversity in SE."

O SLR também cataloga ferramentas propostas: **GenderMag**, **InclusiveMag** (generalização para outras dimensões), **AID Tool** (detector automatizado de bugs de inclusividade de gênero), **Themis** (ferramenta open-source para debugar discriminação em software).

### Developer Experience (DX) de pessoas LGBTQIAPN+ em equipes ágeis

Os slides de aula (Kiev Gama) dedicam um bloco inteiro ao tema central desta aula: **de Souza & Gama (2020, *IEEE RITA*)** entrevistaram pessoas LGBTI+ em duas empresas de TI multinacionais em Recife, concluindo que representatividade melhora o ambiente mas não garante por si só inovação — "**diversidade sem inclusão = tokenismo**". Um relato ilustra a tensão:

> "O programa [de inclusão LGBTI], pra mim, é só uma fraude. [...] Eles aparecem como os bonzinhos, mas na verdade as coisas não acontecem."

Estudos sobre **Developer Experience (DX)** de pessoas LGBTQIA+ em times ágeis (Wassouf-Jr, Fukuda & Fontão, 2025) mostram que invisibilidade, preconceito, discriminação e isolamento afetam negativamente a DX, enquanto segurança psicológica e políticas inclusivas favorecem coesão. Um mapeamento anterior (Silveira & Prikladnicki, 2019) achou 221 artigos sobre diversidade em ES, dos quais 129 sobre gênero e **apenas 2 sobre pessoas LGBTQI** — evidenciando a mesma lacuna que o SLR de diversidade percebida relata para raça.

!!! note "Estudantes trans e não-binários em Engenharia de Software (Graßl, ICSE-SEIS 2026)"
    13 entrevistas semiestruturadas; motivações para escolher a área incluem trabalho remoto como fonte de segurança (10 participantes), segurança financeira (7), desejo de criar tecnologias mais inclusivas (7). Desafios relatados: microagressões, *misgendering*, impactos na saúde mental, tensão entre "passing" e expressar identidade. Estratégias de inclusão propostas: representação/visibilidade, linguagem inclusiva, banheiros neutros em gênero, mentoria, bolsas direcionadas (com cuidado para evitar tokenismo).

### O backlash de DEI (2024–2026)

!!! warning "Retrocesso das iniciativas de DEI"
    Os slides documentam o retrocesso das iniciativas de DEI, com efeito direto sobre a pesquisa e as iniciativas voltadas a grupos como o público LGBTQIAPN+: ordens executivas nos EUA (jan. 2025) contra programas de DEI; organizações como *Girls in Tech* e *Women Who Code* encerraram ou se reestruturaram; Meta encerrou metas de representação; Google removeu Pride Month/Black History Month do Google Agenda; Amazon removeu seções sobre equidade racial e **direitos LGBTQ+** do site; Microsoft dispensou sua equipe de DEI; interrupção de ~2.000 projetos da NSF (US$ 697 milhões), incluindo o **GenderMag**; queda estimada de 10% nas publicações sobre DEI em Engenharia de Software entre 2024 e 2025. Relatório **"Diversity Wins"** (McKinsey, 2020), citado nos mesmos slides como contraponto de mercado: diversidade de gênero na diretoria associada a 25% mais chance de lucratividade acima da média; diferença de 48% de desempenho entre empresas mais e menos diversas.

## Aulas 12 a 16

!!! warning "Sem material disponível"
    Ainda não há material disponibilizado para estas aulas no momento da escrita desta página. A página será atualizada conforme o conteúdo for liberado ao longo do semestre.
