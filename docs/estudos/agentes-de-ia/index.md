# AGENTES DE IA

Como agentes de IA (coding agents e agentes de decisão em geral) são construídos, otimizados e orquestrados por dentro — o "corpo" que envolve um LLM (harness), como ele aprende com correções sem retreino de pesos, como evita gastar tokens caros em trabalho mecânico, e como modelos especializados de decisão entram nesse ecossistema.

## Conteúdo

- [Harness e Pi](harness-e-pi.md) — o que é um harness, e o Pi (pi.dev) como estudo de caso de harness minimalista.
- [Otimização de tokens e roteamento de modelos](otimizacao-tokens-roteamento.md) — o caso Portal/Spotify, roteamento nativo no Claude Code e o padrão "codebase wiki".
- [Fine-tuning agêntico: a abordagem da Meta](fine-tuning-agentico-meta.md) — "aprender" sem retreinar pesos, via edição validada de arquivos de conhecimento/procedimento.
- [Jev: modelos de decisão](jev-modelos-decisao.md) — um modelo "System One" feito para decisões estruturadas em vez de prosa, e seu desempenho como juiz barato.

!!! note "Por que esses quatro estão juntos"
    Todos tratam do mesmo problema de fundo — como fazer um agente de IA raciocinar bem sem desperdiçar tempo/dinheiro/contexto em trabalho que não precisa do modelo mais caro/forte. Harness é a infraestrutura geral; roteamento de tokens é a otimização de custo tático; fine-tuning agêntico da Meta é a otimização de qualidade/conhecimento ao longo do tempo; Jev é um modelo inteiro desenhado só para a parte de "decisão/roteamento" desse ciclo.
