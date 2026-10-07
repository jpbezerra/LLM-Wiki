# AULA 1 — IMPLEMENTAÇÃO EM QISKIT

Complemento prático da [Aula 1](aula-1.md): como representar e manipular os conceitos de **sistemas únicos** (vetores de estado, medição, operações unitárias) usando o **Qiskit**, a biblioteca Python da IBM para computação quântica. Baseado na página escrita ["Qiskit implementation"](https://quantum.cloud.ibm.com/learning/en/courses/basics-of-quantum-information/single-systems/qiskit-implementation) do curso.

Os exemplos abaixo foram testados com `qiskit==2.5.2`. Como o Qiskit muda de versão com alguma frequência (inclusive com mudanças que quebram compatibilidade), vale sempre checar a versão instalada:

```python
import qiskit
print(qiskit.__version__)
```

!!! note "Instalação"
    ```bash
    pip install qiskit qiskit-ibm-runtime
    # para os exemplos desta página (visualização, LaTeX, notebooks):
    pip install matplotlib pylatexenc sympy jupyter ipython
    ```

## 1. Vetores e matrizes "na mão", com NumPy

Antes de usar as classes específicas do Qiskit, vale ver que nada impede representar tudo isso com NumPy puro — afinal, um estado quântico *é*, matematicamente, só um vetor coluna.

```python
import numpy as np

ket0 = np.array([[1], [0]])
ket1 = np.array([[0], [1]])

plus = (ket0 + ket1) / np.sqrt(2)
print(plus)
# [[0.70710678]
#  [0.70710678]]

H = (1 / np.sqrt(2)) * np.array([[1, 1], [1, -1]])
print(H @ ket0)   # H|0> = |+>
# [[0.70710678]
#  [0.70710678]]
print(H @ plus)   # H|+> = |0>  (a segunda entrada dá ~0, só erro de arredondamento)
# [[1.00000000e+00]
#  [2.23711432e-17]]
```

O operador `@` é o produto matricial do NumPy (equivalente a `np.matmul`), tanto para multiplicação matriz-matriz quanto matriz-vetor — é o que usamos aqui para aplicar $H$ a um vetor.

Essa abordagem funciona, mas fica trabalhosa rapidamente (ler um vetor coluna "cru" não é tão legível quanto a notação de Dirac, e não há verificação automática de que algo é de fato um estado quântico válido). É aí que entram as classes do Qiskit.

## 2. Estados, medições e operações com `qiskit.quantum_info`

### 2.1 Definir e exibir vetores de estado: `Statevector`

A classe `Statevector` representa um vetor de estado quântico e sabe, por exemplo, verificar se ele é válido (norma euclidiana igual a 1):

```python
from qiskit.quantum_info import Statevector
import numpy as np

v = Statevector([1, 0])
print(v)
# Statevector([1.+0.j, 0.+0.j], dims=(2,))

plus = Statevector([1 / np.sqrt(2), 1 / np.sqrt(2)])
print(plus.is_valid())
# True

nao_normalizado = Statevector([1, 1])
print(nao_normalizado.is_valid())
# False
```

Dentro de um notebook Jupyter, `display(plus.draw("latex"))` mostra o estado formatado como $\tfrac{\sqrt2}{2}|0\rangle+\tfrac{\sqrt2}{2}|1\rangle$; fora de um notebook, `draw("latex_source")` devolve a string LaTeX puro:

```python
print(plus.draw("latex_source"))
# \frac{\sqrt{2}}{2} |0\rangle+\frac{\sqrt{2}}{2} |1\rangle
```

### 2.2 Simulando medições: `measure()` e `sample_counts()`

O método `measure()` simula **uma única** medição na base padrão: devolve o resultado obtido (aleatório, de acordo com as probabilidades do estado) e o novo estado do sistema após o colapso.

```python
outcome, post_state = plus.measure()
print(outcome, post_state)
# (por exemplo) 0   Statevector([1.+0.j, 0.+0.j], dims=(2,))
```

Rodar de novo pode dar `1` em vez de `0` — é aleatório, com 50% de chance cada, como esperado para o estado $|+\rangle$. Importante: o `post_state` devolvido pode vir multiplicado por uma fase global (ex.: $-|0\rangle$ em vez de $|0\rangle$) — como visto na [Aula 1](aula-1.md#fase-global), isso representa exatamente o mesmo estado físico.

Para ver a *distribuição* de resultados (sem alterar o estado original), usa-se `sample_counts(n)`, que simula `n` medições independentes e devolve as frequências:

```python
counts = plus.sample_counts(4000)
print(counts)
# {'0': 2015, '1': 1985}   (valores exatos variam a cada execução)
```

Com `n` grande, as frequências relativas se aproximam das probabilidades teóricas ($1/2$ e $1/2$) — lei dos grandes números. `qiskit.visualization.plot_histogram(counts)` desenha isso como um gráfico de barras (requer matplotlib e, tipicamente, um ambiente de notebook para exibir a figura).

### 2.3 Operações com `Operator`

A classe `Operator` representa uma matriz (tipicamente unitária, mas não exclusivamente) e sabe verificar se é unitária:

```python
from qiskit.quantum_info import Operator

H = Operator([[1 / np.sqrt(2), 1 / np.sqrt(2)], [1 / np.sqrt(2), -1 / np.sqrt(2)]])
S = Operator([[1, 0], [0, 1j]])
T = Operator([[1, 0], [0, (1 + 1j) / np.sqrt(2)]])

print(H.is_unitary())
# True
```

Para aplicar uma operação a um estado, usa-se `Statevector.evolve`:

```python
estado = plus.evolve(T).evolve(H)   # H(T|+>)
print(estado)
# Statevector([0.85355339+0.35355339j, 0.14644661-0.35355339j], dims=(2,))
```

Esse resultado confere exatamente com o cálculo feito "na mão" na [Aula 1](aula-1.md#exemplos-de-acao-dessas-operacoes) para $HT|+\rangle$: $\left(\tfrac12+\tfrac{1+i}{2\sqrt2}\right)|0\rangle + \left(\tfrac12-\tfrac{1+i}{2\sqrt2}\right)|1\rangle \approx 0{,}854+0{,}354i$ na primeira entrada.

### 2.4 Um adiantamento de circuitos quânticos: `QuantumCircuit`

O Qiskit também permite montar a mesma sequência de operações como um **circuito quântico** — a forma como, na prática, se programa um computador quântico de verdade (circuitos são o assunto de uma lição futura, mas o Qiskit já deixa fazer essa ponte aqui):

```python
from qiskit import QuantumCircuit
from qiskit.quantum_info import Operator, Statevector

qc = QuantumCircuit(1)
qc.h(0)
qc.t(0)
qc.h(0)

print(qc.draw(output="text"))
#    ┌───┐┌───┐┌───┐
# q: ┤ H ├┤ T ├┤ H ├
#    └───┘└───┘└───┘
```

(`qc.draw(output="mpl")` desenha a mesma coisa com Matplotlib, com uma estética mais parecida com a dos circuitos impressos em artigos/livros — útil em notebooks.)

A partir do circuito, dá para extrair a matriz unitária que ele representa, e aplicá-la a um estado inicial — confirmando que é exatamente a mesma conta de antes, agora partindo de $|0\rangle$ em vez de $|+\rangle$ (lembrando que $|+\rangle = H|0\rangle$, e o circuito já inclui esse primeiro $H$):

```python
U = Operator.from_circuit(qc)
print(U)
# Operator([[0.85355339+0.35355339j, 0.14644661-0.35355339j],
#           [0.14644661-0.35355339j, 0.85355339+0.35355339j]], ...)

resultado = Statevector([1, 0]).evolve(U)
print(resultado)
# Statevector([0.85355339+0.35355339j, 0.14644661-0.35355339j], dims=(2,))

contagens = resultado.sample_counts(4000)
print(contagens)
# {'0': ~3414, '1': ~586}   (≈ 85.4% / 14.6%, consistente com |amplitude|² de cada entrada)
```

!!! tip "Por que isso importa"
    Essa seção já antecipa a virada de chave do curso: tudo que fizemos até aqui (vetores, medição, matrizes unitárias) tem uma representação direta como **circuito** — a forma universal de descrever algoritmos quânticos e de efetivamente rodá-los num computador quântico real (via `qiskit-ibm-runtime`) ou num simulador. As próximas lições do curso (sistemas múltiplos, e depois a unidade de circuitos) constroem em cima exatamente dessa ponte.
