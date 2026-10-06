# BEND2: TIPOS DEPENDENTES E PROVAS FORMAIS

Fontes consultadas: [bend2.dev](https://bend2.dev/notes/what-is-bend2/) (notes, learn, llms.txt), repositório oficial [`github.com/bendlang/bend`](https://github.com/bendlang/bend).

## 1. O que é o Bend (Bend2)

Bend2 é uma linguagem de programação funcional com **tipagem estática**, que combina **tipos dependentes** com **execução paralela em CPUs e GPUs**. A ideia central: um programa pode incluir provas de que suas funções satisfazem propriedades especificadas, e o compilador checa essas provas antes de executar o código.

### Pilares da linguagem

**Tipos dependentes e provas (laws).** Um tipo dependente pode conter um valor — ex.: um tipo de lista pode incluir seu próprio comprimento, obrigando uma função que pega o primeiro elemento a exigir uma lista não-vazia. Tipos também podem expressar proposições sobre uma computação: uma igualdade entre duas expressões é um tipo, e uma prova é uma definição que habita esse tipo. Na prática, escreve-se uma `law` (propriedade a garantir) e um `def` de mesmo nome que é a prova — por exemplo, uma lei de que cancelar um pedido duas vezes é igual a cancelar uma vez (idempotência), checada matematicamente pelo compilador, não só testada.

**Ownership (posse de dados).** Uma ligação comum é "afim" (só pode ser usada uma vez); dados reutilizáveis precisam de contagem de referência. O runtime nativo recupera dados consumidos sem um garbage collector tradicional.

**Paralelismo explícito.** A sintaxe `a b = f(x) g(y)` inicia duas chamadas independentes e usa os resultados depois que terminam — o programador escolhe onde dividir o trabalho, o runtime atribui as chamadas aos workers. Para GPU, `f!(x)` marca uma chamada para execução em GPU (backends nativos: Metal no macOS, CUDA no Linux).

**Compilação.** O compilador nativo emite C para o BendRT (runtime próprio para CPU/GPU); um backend separado emite JavaScript.

### Limitações honestas (documentadas pelo próprio site)

- Exige termos de prova **explícitos**, sem linguagem de táticas ou busca automática de provas.
- Anotações de tipo são comuns; compilação nativa produz um arquivo C por programa, sem compilação incremental.
- Tipos numéricos embutidos: `Nat`, `U32`, `F32` — **não há `F64`**, limitando workloads científicos de alta precisão.
- Projeto **não-oficial**, não afiliado à Higher Order Company (empresa por trás do Bend original/HVM).

## 2. O exemplo de referência: colisão de galáxias

O exemplo `galaxy-encounter` do site oficial simula **8.192 estrelas** ao redor de três núcleos de galáxia que se atraem mutuamente, dividindo as estrelas em chamadas recursivas independentes. O código prova formalmente sete leis, por exemplo:

- **`kick_position`**: gravidade muda velocidade sem mover o corpo durante o "kick" (impulso).
- **`preserves_roster`**: toda estrela mantém seu ID, origem, massa e posição na árvore — nenhuma estrela "vaza" ou troca de identidade durante a simulação.
- **`resume`**: rodar $n$ passos e depois $m$ passos dá o mesmo resultado que rodar $n+m$ passos de uma vez — pausar/retomar não muda o resultado.

!!! warning "Prova formal ≠ física correta"
    As provas garantem propriedades **estruturais** (conservação de identidade, massa, contagem de partículas, comutatividade de pausar/retomar), mas **não garantem trajetórias fisicamente corretas**. O próprio site é explícito: devolver o corpo original de `orbit` (sem mover nada) passaria em todas as sete provas, porque "não mover" também preserva identidade, massa e contagem. A correção física real é verificada separadamente por **testes numéricos tradicionais**: uma força conhecida, convergência orbital conforme o passo de tempo diminui, e posições finitas ao longo dos primeiros 2.400 passos.

O modelo é simplificado por natureza: só 3 núcleos centrais + partículas de teste, sem gravidade estrela-estrela, sem gás, sem fricção dinâmica — descreve um encontro de maré (*tidal encounter*), não uma fusão de galáxias completa. Em resumo: prova formal garante "o programa não quebra suas próprias regras estruturais"; correção numérica é um problema separado, verificado com testes convencionais.

## 3. Para que serve

Útil em domínios onde se quer garantias formais sobre invariantes do programa, combinadas com paralelismo massivo:

- **Simulações científicas** (física, dinâmica de partículas, N-corpos) onde é crítico que atualizações não percam/dupliquem entidades, e que rodar em lotes/pausar dê o mesmo resultado que rodar contínuo.
- **Sistemas com regras de negócio críticas** (ex.: pedidos/cancelamento) onde se quer provar formalmente que uma transição de estado é idempotente, não corrompe saldos etc.
- **Processamento paralelo em CPU/GPU** sem escrever kernels CUDA à mão.
- **Agentes de IA que geram código** — há nota específica do site sobre isso (`ai-agents-bend`): provas dão uma rede de segurança contra alucinações de LLMs ao gerar código.

## 4. Bend2 vs. Lean 4

| Aspecto | Lean 4 | Bend2 |
| --- | --- | --- |
| Como se prova | Termos explícitos **ou** táticas (`simp`, etc.) que geram os termos automaticamente | Só termos explícitos e "rewrite motives" — sem táticas, sem busca automática |
| Bibliotecas | Mathlib — enorme acervo de lemas e teoremas prontos | `Base` (biblioteca padrão) e demos publicados — bem mais enxuto |
| Paralelismo nativo | `Task` (thread pool do runtime) | Fork/join balanceado, explícito na sintaxe (`a b = f(x) g(y)`) |
| GPU | Via código externo/bibliotecas | Chamadas marcadas com `!`, compiladas para Metal/CUDA nativamente |
| Formalização do próprio checker | Kernel pequeno e confiável, testado há anos | Formalização em Lean existe, mas o README aponta divergências entre ela e o `bend.ts` real |

**Síntese**: Lean é uma ferramenta de prova matemática madura, com décadas (relativamente) de bibliotecas/táticas que economizam muito trabalho de prova. Bend é mais jovem, exige provas manuais (sem táticas), mas tem paralelismo CPU/GPU embutido na linguagem — algo que em Lean exigiria bibliotecas externas/FFI. Não são bem "concorrentes diretos": têm ênfases diferentes que se sobrepõem na parte de tipos dependentes.

## 5. Projeto de comparação: `kirchhoff-ising`

Para comparar as duas linguagens com dados concretos (em vez de opiniões), foi desenhado um projeto — repositório real em `github.com/jpbezerra/kirchhoff-ising` — implementando e provando propriedades sobre **dois modelos físicos discretos**, escolhidos por exigirem técnicas de prova estruturalmente diferentes entre si (e por isso diferentes do exemplo de referência "árvore + conservação global" da galáxia).

!!! note "Por que não um projeto de matéria/energia"
    A primeira ideia (conversão discreta matéria↔energia, análoga ao exemplo `inventory-conservation` do site) foi descartada por ser estruturalmente idêntica ao exemplo da galáxia: mesma estrutura de dados (árvore `Leaf`/`Fork`), mesmo tipo de lei ("uma transformação preserva X"), mesma técnica de prova (indução estrutural por `Fork`). O projeto final troca deliberadamente o "esqueleto" da prova, mantendo o tema físico/matemático.

### Resumo executivo

1. **Circuito elétrico resistivo** (Lei das Correntes de Kirchhoff): o modelo é um **grafo**, não uma árvore; a lei provada é uma invariante **local** (em cada nó), preservada por uma operação de análise de malhas (*mesh current*) — não uma soma global.
2. **Rede de spins tipo Ising** (magnetismo): o modelo é uma **grade 2D**; as leis provadas são sobre **variação controlada** (quanto uma atualização de spin pode mudar a magnetização/energia total), não conservação exata.

Os dois módulos são implementados e provados em paralelo nas duas linguagens, com o mesmo relatório comparativo aplicado a ambos. Ambos evitam ponto flutuante de propósito — `Nat`/`Int` bastam, contornando a limitação de `F64` do Bend2.

### Entidades e leis

| Tipo | Campos | Descrição |
| --- | --- | --- |
| `Node` (Módulo A) | id (Nat) | Identificador de nó |
| `Edge` (Módulo A) | from, to (Nat), current (Int) | Aresta/resistor com corrente sinalizada |
| `Circuit` (Módulo A) | edges (List\<Edge\>) | Circuito completo |
| `Loop` (Módulo A) | nodes (List\<Nat\>) | Sequência cíclica formando malha fechada |
| `Spin` (Módulo B) | value (+1/-1, via Bool) | Estado de um spin |
| `Lattice` (Módulo B) | rows (List\<List\<Spin\>\>) | Grade 2D |
| `Coupling` (Módulo B) | j (Int) | Constante de acoplamento entre vizinhos |

| Lei | Módulo | Enunciado |
| --- | --- | --- |
| `preserves_node_balance` | A | Corrente líquida em qualquer nó não muda ao aplicar corrente de malha |
| `loop_current_conserves_total` | A | Soma de todas as correntes do circuito não muda ao aplicar corrente de malha |
| `flip_twice_identity` | B | Aplicar `flip` duas vezes na mesma posição retorna a grade original |
| `flip_changes_magnetization_by_two` | B | A diferença de magnetização antes/depois de um `flip` é exatamente 2 |
| `preserves_lattice_shape` | B | `flip` não muda as dimensões da grade |
| `resume` (fase avançada) | A e B | Rodar em lotes é equivalente a rodar tudo de uma vez |

Diferente do projeto descartado, as leis aqui não seguem um único molde: o Módulo A prova invariante local por indução sobre **lista de arestas de tamanho variável** (não árvore binária); o Módulo B prova **limites de variação** (diferença = 2, não soma preservada).

### Metodologia de comparação

| Eixo | Como medir |
| --- | --- |
| Esforço de prova | Linhas de código só de prova por lei |
| Automação vs. manual | % de provas fechadas só com tática automática vs. termo explícito (N/A para Bend2, que não tem táticas) |
| Tempo de checagem | Tempo de `bend PROOF.bend` / `lake build`, mesmo hardware |
| Tempo de execução | N passos, 1 thread |
| Paralelismo CPU | Speedup com múltiplos núcleos |
| GPU | Speedup com `!`/Metal-CUDA (não medido — sem GPU dedicada disponível) |
| LOC (não-prova) | Tipos + funções puras |
| Curva de aprendizado | Tempo real gasto por fase |

Princípios: mesmo hardware/máquina/sessão; mesmo autor (reduz viés de familiaridade); reportar honestamente assimetrias estruturais (Lean tem Mathlib/táticas; Bend2 tem paralelismo nativo) em vez de neutralizá-las artificialmente; todas as medições reprodutíveis via script de benchmark versionado.

### Roadmap

| Fase | Entregável |
| --- | --- |
| 0 — Setup | Compilador Bend2 (fonte) + Lean 4/Lake/Mathlib funcionando; repositório criado |
| 1 — Núcleo mínimo | `flip_twice_identity` (Módulo B) provado nas duas linguagens |
| 2 — Modelo completo | Todas as leis (A e B) provadas nas duas linguagens |
| 3 — Comparação de dados | Tabela de benchmarks preenchida com números reais |
| 4 — Extensões opcionais | Paralelismo CPU no `sweep` medido (sem GPU); visualização; lei `resume`, se o tempo permitir |
| 5 — Relatório final | Documento comparativo publicável |

Cada fase só começa quando a anterior tem as leis provadas nas **duas** linguagens, evitando que uma implementação avance demais e distorça a comparação. Maior risco identificado: subestimar o tempo de prova em Bend2 para `preserves_node_balance` (indução sobre lista de tamanho variável, sem táticas) — mitigado começando pelo Módulo B (Ising), estruturalmente mais simples, para validar o pipeline antes do Módulo A.

## 6. Execução prática — problemas reais encontrados (Claude Code)

O projeto foi implementado via Claude Code (não Cowork), já que o trabalho envolve escrever `.bend`/`.lean`, rodar compiladores, gerenciar repositório git e iterar em erros de prova.

### Erro de permissão: `blockReadsOutsideWorkingDirectories`

```
bend names a path that is computed at run time, which cannot be checked against the read block (permissions.blockReadsOutsideWorkingDirectories)
```

Causa: trava do Claude Code que bloqueia comandos (como `bend`, fora da lista de comandos read-only conhecidos) cujo caminho não pode ser verificado estaticamente como "dentro do diretório de trabalho" — mesmo que esteja, na prática (comum em paths do Git Bash/MSYS no Windows).

**Solução recomendada** (escopada ao projeto, não global) — `.claude/settings.local.json` na raiz do repo:

```json
{
  "permissions": {
    "blockReadsOutsideWorkingDirectories": false
  }
}
```

Esse arquivo não vai para o git (Claude Code já o ignora automaticamente). Desligar globalmente (`~/.claude/settings.json`) deixaria qualquer sessão em qualquer pasta permissiva — por isso a preferência por escopar ao projeto.

### Ajuste de formatação em relatório HTML

Uma lista numerada (`ol.steps`) usando CSS `counter()` via `::before` quebrava mal em itens de texto longo (quebra palavra por palavra) — número gerado via counter misturado com texto solto dentro do mesmo `<li>` em grid de 2 colunas é um padrão frágil. Correção: trocar o contador CSS por elementos explícitos (`<div class="step-num">` + `<div class="step-body">`), igual ao padrão já usado em outra seção da mesma página. Também foi adicionada a tag de viewport que estava faltando, importante para renderização em mobile.

## 7. Referências

- [What is Bend2?](https://bend2.dev/notes/what-is-bend2/)
- [Galaxy encounter](https://bend2.dev/learn/galaxy-encounter/)
- [Bend2 vs Lean](https://bend2.dev/notes/bend2-vs-lean/)
- [Bend2 syntax primer](https://bend2.dev/notes/bend2-syntax-primer/)
- [BendRT explained](https://bend2.dev/notes/bendrt-explained/)
- [Bend2 examples](https://bend2.dev/learn/examples.json) (inclui `inventory-conservation`)
- [Bend oficial](https://github.com/bendlang/bend)
- [Lean 4 reference](https://lean-lang.org/doc/reference/latest/Introduction/)
- [Mathlib4](https://github.com/leanprover-community/mathlib4)
