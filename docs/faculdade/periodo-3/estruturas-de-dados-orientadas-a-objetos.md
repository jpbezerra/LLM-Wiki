# ESTRUTURAS DE DADOS ORIENTADAS À OBJETOS

---
- link: [https://sites.google.com/cin.ufpe.br/edoo](https://sites.google.com/cin.ufpe.br/edoo)
## Especificidades de C++
- Linguagem orientada à objetos com grande controle da memória
<details>
<summary>Tabela de inteiros e floats</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
</details>
<details>
<summary>Sequência de caracteres especiais</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
</details>
<details>
<summary>Macros</summary>
	- Macros: comandos que permitem a substituição de texto antes do código ser compilado, usando o `#define`
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	- Outros comandos
		- #define: define os macros ou substituição de texto
		- #undef: cancela a definição
		- #ifdef: executa o bloco de código se o macro foi definido
		- #ifndef: executa o bloco de código se o macro não foi definido
		- #if: executa um bloco de código se a expressão for verdadeira
		- #elif: adiciona uma condição else if para o #if
		- #else: define um bloco de código a ser executado caso nenhuma condição seja verdadeira
		- #endif: finaliza um bloco iniciado por #ifdef, #ifndef ou #if
</details>
<details>
<summary>Header files</summary>
	- Arquivos de texto contendo declarações e macros
	- Utilizando um `#include`, estas declarações e macros podem ser utilizados
	- Exemplos: \<iostream\>, \<string\>, etc.
	- É possível criar os próprios header files
</details>
<details>
<summary>iostream</summary>
	- É um header file para inputs e outputs contendo stream classes de istream e ostream derivadas da classe ios que atua como interface para as duas (que por sua vez é derivada da ios_base)
	- Há também ifstream, ofstream e fstream que são classes derivadas de istream, ostream e iostream e servem para leitura, escrita, leitura e escrita em arquivos
	<details>
	<summary>Manipuladores</summary>
		- Funções que podem ser inseridas e chamadas no input e output
			- Precisa incluir a biblioteca `<iomanip>`
		- showpos: exibe explicitamente o sinal de `+` para números positivos
		- noshowpos: faz justamente o contrário de showpos (comportamento padrão)
		- oct: retorna um número na base octadecimal
		- hex: retorna um número na base hexadecimal
		- dec: retorna um número na base decimal (padrão)
		- uppercase: deixa todas as letras maiúsculas
		- nouppercase: contrário de uppercase (padrão)
		- showpoint: mostra um caractere de ponto após a parte inteira, independente de ser float ou não
			- Após isso mostra os dígitos correspondentes à precisão
		- noshowpoint: contrário de showpoint
		- fixed: output em notação de ponto fixo, onde tem um número fixo de casas decimais (precisa de setar uma precisão antes)
		- scientific: output em notação científica
		- setprecision (int n): coloca a precisão dos dígitos de um float ou double
		<details>
		<summary>fields</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
		</details>
	</details>
	- .setf: faz parte da classe std::ios, logo, é aplicável para todas as classes de iostream
		- Usada para configurar flags que definem o comportamento de uma das classes de iostream
		- Sintaxe: stream.setf(flasg, mask) → flag define qual funcionalide quer modificar e mask determina qual configuração está modificando (opcional)
		- Exemplo: cout.setf(std:\:ios\::showpos)
	-  unsetf: o contrário de .setf
	- Como alternativa ao cin e cout, tem o .get(char ch) e .put(char ch) para ler e escrever char e .getline(cin, text, delimiter) para ler strings usando put() para escrever 
		- O cin lê até o primeiro whitespace, enquanto que o getline lê até o primeiro \\n
</details>
<details>
<summary>Strings</summary>
	- Podem ser concatenadas usando `+`
	- Para comparar strings, podemos usar os operadores de comparação
	- Podemos inserir caracteres em posições específicas da string usando .insert() e podemos apagar porções da string usando .erase()
		- Além disso, é possível substituir porções da string
	- Para encontrar caracteres ou palavras dentro de ums string, basta usar o .find()
	- Para acessar, basta usar índices
</details>
<details>
<summary>Funções</summary>
	- É possível fazer protótipo de funções
	<details>
	<summary>Stack após uma chamada de função</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	</details>
	- inline function: função em que o compilador tenta expandir diretamente no ponto onde ela é chamada em vez de realizar uma chamada de função tradicional
		- O compilador considera que funções criadas dentro de uma classe são inline, não precisando explicitamente usar a keyword `inline`, a não ser que seja uma função muito grande, que envolva operações complexas ou que o compilador decidir que a expansão inline não melhora o desempenho
		- Útil em funções pequenas
</details>
<details>
<summary>Storage class</summary>
	- Define como e onde uma variável é armazenada, seu tempo de vida, seu escopo e sua visibilidade, ou seja, determinam as propriedades de uma variável relacionadas ao gerenciamento de memória e contexto
		<table>
<tr>
<td>**Storage Class**</td>
<td>**Tempo de Vida**</td>
<td>**Escopo**</td>
<td>**Visibilidade**</td>
<td>**Uso Comum**</td>
</tr>
<tr>
<td>`auto`</td>
<td>Escopo local</td>
<td>Local</td>
<td>Somente dentro do escopo</td>
<td>Dedução de tipo moderno (C++11 em diante).</td>
</tr>
<tr>
<td>`register`</td>
<td>Escopo local</td>
<td>Local</td>
<td>Somente dentro do escopo</td>
<td>Variáveis de acesso rápido (antigo).</td>
</tr>
<tr>
<td>`static`</td>
<td>Duração de todo o programa</td>
<td>Local ou Global</td>
<td>Depende do contexto</td>
<td>Persistência de valor ou ligação interna.</td>
</tr>
<tr>
<td>`extern`</td>
<td>Duração de todo o programa</td>
<td>Global</td>
<td>Entre arquivos</td>
<td>Compartilhamento de variáveis globais.</td>
</tr>
<tr>
<td>`mutable`</td>
<td>Depende do objeto</td>
<td>Classe</td>
<td>Acessível mesmo em objetos `const`</td>
<td>Modificável em objetos `const`.</td>
</tr>
<tr>
<td>`thread_local`</td>
<td>Durante a execução da thread</td>
<td>Local, Global</td>
<td>Separado para cada thread</td>
<td>Dados específicos por thread.</td>
</tr>
		</table>
	<details>
	<summary>extern</summary>
		- Keyword usada para indicar que uma variável ou função é definida em outro arquivo ou escopo, permitindo que seja usada em múltiplos arquivos no mesmo programa
		- Funciona como uma declaração (informando ao compilador que algo existe) e a definição real (onde a memória é alocada) deve ser fornecida em outro lugar
		<details>
		<summary>Exemplo</summary>
			```c++
// main.cpp

#include <iostream>
using namespace std;

extern int x; // Declaração: "x" está definido em outro lugar

int main() {
    cout << "Valor de x: " << x << endl;
    return 0;
}

// global.cpp
int x = 42; // Definição: "x" é inicializado aqui
			```
			- Compilação
				- g++ -c main.cpp<br>g++ -c global.cpp
			- Linkedição
				- g++ main.o global.o -o programa
		</details>
	</details>
</details>
<details>
<summary>Namespace</summary>
	- Forma de organizar e agrupar identificadores, usado para evitar conflitos de nomes especialmente em projetos grandes
	<details>
	<summary>Exemplo</summary>
		- Sem namespace
			```c++
#include <iostream>
using namespace std;

// Duas funções com o mesmo nome em escopos globais causariam conflito:
void imprime() {
    cout << "Função 1" << endl;
}

void imprime() { // Erro de redefinição
    cout << "Função 2" << endl;
}

int main() {
    imprime();
    return 0;
}
			```
		- Com namespace
			```c++
#include <iostream>
using namespace std;

namespace Lib1 {
    void imprime() {
        cout << "Função da Lib1" << endl;
    }
}

namespace Lib2 {
    void imprime() {
        cout << "Função da Lib2" << endl;
    }
}

int main() {
    Lib1::imprime(); // Chama a função da Lib1
    Lib2::imprime(); // Chama a função da Lib2
    return 0;
}
			```
	</details>
	- Os namespaces são importados para o escopo atual por meio do `using`
		- Pode importar elementos específicos de um namespace
	- namespaces podem ser aninhados
		```c++
namespace Lib {
    namespace Util {
        void funcao() {
            std::cout << "Dentro do Lib::Util" << std::endl;
        }
    }
}

int main() {
    Lib::Util::funcao(); // Acessa o namespace aninhado
    return 0;
}
		```
</details>
<details>
<summary>Ponteiros</summary>
	- É um tipo de variável ao qual seu valor corresponde à um endereço de memória de uma outra variável ou estrutura
	- Útil pois se utiliza de memória dinâmica, deixando o programa mais rápido e eficiente
</details>
<details>
<summary>Arrays e ponteiros</summary>
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	- int\* ptr = arr; o ponteiro aponta para arr\[0\]
	- Os três são equivalentes
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	- Os quatro são equivalentes
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
</details>
<details>
<summary>Exception handling</summary>
	- Possui blocos try-catch
</details>
---
## Orientação à objetos
<details>
<summary>Especificidades em C++</summary>
	- Objetos são construídos por meio de classes
		- Possuem atributos e métodos, que podem ser públicos, privados ou protegidos
		- Essa classe é construída por meio de um arquivo de cabeçalho e outro arquivo de implementação, essa construção faz com que outras partes do código utilizem a classe sem precisar conhecer detalhes de sua implementação, garantindo a modularidade
		- No arquivo de teste, não é preciso incluir o arquivo de implementação, ao invés disso é melhor fazer esse link apenas na compilação
			<details>
			<summary>Exemplo</summary>
				- Exemplo: arquivos myClass.h, myClass.cpp e myClass_t.cpp
				- Primeiro passo: compilação
					- `g++ -c myClass.cpp` → gera myClass.o
					- `g++ -c myClass_t.cpp` → gera myClass_t.o
				- Segundo passo: linkedição
					- `g++ myClass.o myClass_t.o -o programa` → gera um .exe
			</details>
	- Para acessar membros basta utilizar o `.`
	- Pode existir ponteiros de classes
		- Ao invés de acessar membros com o `.`, usa o `->`
	- Em C++, structs podem ser usados para criar objetos mas todos os atributos vêm públicos por padrão
		- Também existe os unions para criar objetos, mas nestes em particular todos os membros compartilham a mesma memória; logo, apenas um membro pode ser acessado por vez
		- Também existem os enums, mas é um conjunto de valores constantes associados à números inteiros, usado principalmente para representar conjuntos de estados ou valores fixos.
		- Entretanto, o mais comum é usando classes, pois dão suporte total à POO ao invés de structs que possui suporte mas não é o foco e unions e enums onde não possuem suporte à POO
	- As classes possuem construtores (que podem ser mais de um, diferenciando-se nos parâmetros) e um destrutor, ambos são implicitamente inline functions
	- Para acessar atributos privados o melhor a se fazer é criar métodos públicos que retornam estes atributos e métodos que modificam este atributo (getters e setters)
	- Em classes, há um ponteiro embutido `this` que funciona como a própria instância do objeto dentro da classe
	- Classes podem ser utilizadas como tipo de retorno de função
	- Classes podem ter atributos constantes, que não podem ser alterados
	- Métodos estáticos devem manipular apenas atributos estáticos
	<details>
	<summary>Operadores</summary>
		- Os operadores convencionais podem ser reprogramados
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- Com isto, classes podem ser usadas em operações aritméticas e o que acontece depende da implementação
	</details>
	<details>
	<summary>friend</summary>
		- Palavra chave para permitir que uma função ou outra classe tenha acesso privilegiado aos membros privados de uma classe
		- Apesar de não ser parte da própria classe, um amigo pode acessar seus dados como se fosse um membro da classe
		- Podem ser tratadas como funções globais
		<details>
		<summary>Tipos</summary>
			<details>
			<summary>Friend functions</summary>
				- Uma função amiga é uma função externa que não pertence à classe, mas pode acessar os membros privados e protegidos dessa classe
				```c++
#include <iostream>
using namespace std;

class MyClass {
private:
    int value;

public:
    MyClass(int val) : value(val) {}

    // Declarando a função amiga
    friend void display(const MyClass& obj);
};

// Função amiga
void display(const MyClass& obj) {
    cout << "Valor privado: " << obj.value << endl;
}

int main() {
    MyClass obj(42);
    display(obj); // Acessa diretamente o membro privado
    return 0;
}

				```
			</details>
			<details>
			<summary>Friend classes</summary>
				- Quando uma classe é declarada como amiga de outra, todos os métodos da classe amiga podem acessar os membros privados/protegidos da classe que a declarou como amiga
				```c++
#include <iostream>
using namespace std;

class ClassA {
private:
    int privateValue;

public:
    ClassA(int val) : privateValue(val) {}

    // Tornando ClassB amiga
    friend class ClassB;
};

class ClassB {
public:
    void display(const ClassA& obj) {
        cout << "Valor privado de ClassA: " << obj.privateValue << endl;
    }
};

int main() {
    ClassA objA(42);
    ClassB objB;
    objB.display(objA); // ClassB acessa membro privado de ClassA
    return 0;
}
				```
			</details>
			<details>
			<summary>Funções Membro de Outra Classe como Amigas</summary>
				- Uma função específica de outra classe pode ser tornada amiga, em vez de tornar a classe inteira amiga
				```c++
#include <iostream>
using namespace std;

class ClassA;

class ClassB {
public:
    void display(const ClassA& obj);
};

class ClassA {
private:
    int privateValue;

public:
    ClassA(int val) : privateValue(val) {}

    // Tornando apenas ClassB::display amiga
    friend void ClassB::display(const ClassA& obj);
};

void ClassB::display(const ClassA& obj) {
    cout << "Valor privado de ClassA: " << obj.privateValue << endl;
}

int main() {
    ClassA objA(42);
    ClassB objB;

    objB.display(objA); // Apenas esta função pode acessar membros privados
    return 0;
}
				```
			</details>
			<details>
			<summary>Reciprocal friendship</summary>
				- Duas classes podem ser amigas uma da outra, permitindo acesso mútuo aos seus membros privados
				```c++
#include <iostream>
using namespace std;

class ClassB; // Declaração antecipada

class ClassA {
private:
    int valueA;

public:
    ClassA(int val) : valueA(val) {}

    friend class ClassB; // ClassB é amiga de ClassA
};

class ClassB {
private:
    int valueB;

public:
    ClassB(int val) : valueB(val) {}

    void display(const ClassA& obj) {
        cout << "Valor privado de ClassA: " << obj.valueA << endl;
    }

    friend class ClassA; // ClassA é amiga de ClassB
};

int main() {
    ClassA objA(42);
    ClassB objB(100);

    objB.display(objA); // ClassB acessa membro privado de ClassA
    return 0;
}
				```
			</details>
		</details>
	</details>
	<details>
	<summary>explicit</summary>
		- Keywork usada para evitar conversões implícitas ou involuntárias de objetos ao usar construtores de uma única entrada
		```c++
#include <iostream>
using namespace std;

class MyClass {
public:
    MyClass(int x) { // Construtor de um único parâmetro
        cout << "Construtor chamado com: " << x << endl;
    }
};

int main() {
    MyClass obj = 42; // Conversão implícita de int para MyClass
    return 0;
}

#include <iostream>
using namespace std;

class MyClass {
public:
    explicit MyClass(int x) { // Construtor marcado como explicit
        cout << "Construtor chamado com: " << x << endl;
    }
};

int main() {
    // MyClass obj = 42; // ERRO: Conversão implícita não permitida
    MyClass obj(42);      // OK: Construção explícita
    return 0;
}
		```
	</details>
	<details>
	<summary>Templates</summary>
		- Em C++, é possível criar códigos genéricos usando template, permitindo que funções e classes trabalhem com diferentes tipos de dados sem precisar ser reescritas para cada tipo
		<details>
		<summary>Exemplos</summary>
			<details>
			<summary>Template de função</summary>
				```c++
#include <iostream>
using namespace std;

template <typename T> // Define um tipo genérico T
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(3, 4) << endl;        // Funciona com int
    cout << add(2.5, 3.1) << endl;    // Funciona com double
    cout << add(string("Hello, "), string("World!")) << endl; // Funciona com string
    return 0;
}
				```
			</details>
			<details>
			<summary>Template de classe</summary>
				```c++
#include <iostream>
using namespace std;

template <typename T>
class Box {
private:
    T value;

public:
    Box(T val) : value(val) {}

    void display() {
        cout << "Value: " << value << endl;
    }
};

int main() {
    Box<int> intBox(10);    // Classe Box com int
    Box<double> doubleBox(3.14); // Classe Box com double
    Box<string> stringBox("Hello"); // Classe Box com string

    intBox.display();
    doubleBox.display();
    stringBox.display();

    return 0;
}
				```
			</details>
			<details>
			<summary>Template variádicos</summary>
				```c++
#include <iostream>
using namespace std;

template <typename... Args>
void printAll(Args... args) {
    (cout << ... << args) << endl; // Expansão do parâmetro variádico
}

int main() {
    printAll(1, 2, 3, "Hello", 4.5); // Mistura de tipos
    return 0;
}
				```
			</details>
			<details>
			<summary>Templates específicos</summary>
				```c++
#include <iostream>
using namespace std;

template <typename T>
class Box {
public:
    void display(T value) {
        cout << "Genérico: " << value << endl;
    }
};

// Especificação para int
template <>
class Box<int> {
public:
    void display(int value) {
        cout << "Específico para int: " << value << endl;
    }
};

int main() {
    Box<double> doubleBox;
    Box<int> intBox;

    doubleBox.display(3.14);
    intBox.display(42);

    return 0;
}
				```
			</details>
		</details>
	</details>
</details>
<details>
<summary>Herança</summary>
	- Conceito que permite que uma classe (chamada de classe derivada) herde as características de outra classe (classe base), promovendo a reutilização de código e extensibilidade permitindo criar novas classes com base em uma pré-existente
	<details>
	<summary>Exemplo</summary>
		```c++
#include <iostream>
using namespace std;

// Classe Base
class Animal {
public:
    void eat() {
        cout << "Este animal está comendo." << endl;
    }
};

// Classe Derivada
class Dog : public Animal {
public:
    void bark() {
        cout << "O cachorro está latindo." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Método herdado de Animal
    myDog.bark(); // Método específico de Dog
    return 0;
}
		```
		- A classe Dog herda o método eat() além de ter seu próprio método bark
	</details>
	- Em C++, o tipo de herança é determinado pelo especificador de acesso public, protected e private
		<details>
		<summary>protected</summary>
			- Membros protegidos são inacessíveis diretamente fora da classe mas são acessíveis por herança
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
		</details>
	- Os construtores da classe base não são herdados automaticamente, mas podem ser chamados explicitamente na classe derivada
		<details>
		<summary>Exemplo</summary>
			```c++
#include <iostream>
using namespace std;

class Animal {
public:
    Animal() {
        cout << "Animal criado." << endl;
    }
};

class Dog : public Animal {
public:
    Dog() {
        cout << "Cachorro criado." << endl;
    }
};

int main() {
    Dog myDog;
    return 0;
}
			```
			- Output: 
				- Animal criado.<br>Cachorro criado.
		</details>
	<details>
	<summary>Herança múltipla</summary>
		- O C++ permite que uma classe herde mais de uma classe base
		```c++
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() { cout << "Comendo..." << endl; }
};

class Pet {
public:
    void play() { cout << "Brincando..." << endl; }
};

class Dog : public Animal, public Pet {
    // Herda membros de Animal e Pet
};

int main() {
    Dog myDog;
    myDog.eat();
    myDog.play();
    return 0;
}
		```
	</details>
	<details>
	<summary>Herança e construtores</summary>
		- A classe derivada sempre vai chamar o construtor da classe base seja de forma explícita ou implícita
		- A classe derivada pode possuir construtores próprios
	</details>
</details>
<details>
<summary>Polimorfismo</summary>
	- Capacidade de uma função, método ou objeto de assumir diferentes formas
	- O polimorfismo permite que o mesmo nome de função/método seja usado para realizar diferentes comportamentos, dependendo do contexto
	<details>
	<summary>Tipos de polimorfismo em C++</summary>
		<details>
		<summary>Static polymorphism</summary>
			- Decidido em tempo de compilação
			<details>
			<summary>Sobrecarga de funções</summary>
				- Permite que várias funções tenham o mesmo nome, mas diferentes assinaturas (tipos ou parâmetros)
				```c++
#include <iostream>
using namespace std;

class Math {
public:
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
};

int main() {
    Math math;
    cout << math.add(3, 4) << endl;       // Chama add(int, int)
    cout << math.add(2.5, 3.1) << endl;  // Chama add(double, double)
    return 0;
}
				```
			</details>
			<details>
			<summary>Sobrecarga de operadores</summary>
				- Permite redefinir o comportamento de operadores para tipos definidos pelo usuário
				```c++
#include <iostream>
using namespace std;

class Complex {
private:
    double real, imag;

public:
    Complex(double r, double i) : real(r), imag(i) {}

    // Sobrecarga do operador +
    Complex operator+(const Complex& c) {
        return Complex(real + c.real, imag + c.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(1.0, 2.0), c2(3.0, 4.0);
    Complex c3 = c1 + c2; // Usa o operador sobrecarregado
    c3.display();
    return 0;
}
				```
			</details>
			<details>
			<summary>Templates</summary>
				- Permitem criar funções ou classes genéricas que se adaptam a diferentes tipos de dados
				```c++
#include <iostream>
using namespace std;

template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(3, 4) << endl;       // Trabalha com int
    cout << add(2.5, 3.1) << endl;  // Trabalha com double
    return 0;
}
				```
			</details>
		</details>
		<details>
		<summary>Dynamic polymorphism</summary>
			- Decidido em tempo de execução
			<details>
			<summary>Funções virtuais</summary>
				- Basicamente consiste numa sobrescrita dos métodos de uma classe base em uma classe derivada para alterar seu comportamento
				- A keyword `virtual` é usada para declarar um método em uma classe base que pode ser sobrescrito em uma classe derivada
				- A keyword `override` é usada para indicar explicitamente que um método está sobrescrevendo um método virtual de sua classe base
				<details>
				<summary>Exemplo</summary>
					```c++
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal faz algum som." << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "O cachorro late." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.sound(); // Chama a versão sobrescrita de Dog
    return 0;
}
					```
					- Output: O cachorro late.
				</details>
				- Destrutores podem ser virtuais, enquanto que construtores não
					- Como alternativa, em vez de usar construtores virtuais pode usar fábricas virtuais que envolvem a criação de um método virtual que retorna uma nova instância da classe derivada
					<details>
					<summary>Exemplo</summary>
						```c++
#include <iostream>
using namespace std;

class Base {
public:
    virtual Base* create() const = 0; // Método "virtual construtor"
    virtual void display() const = 0;
    virtual ~Base() = default; // Destrutor virtual
};

class Derived : public Base {
public:
    Derived* create() const override {
        return new Derived();
    }

    void display() const override {
        cout << "Derived class" << endl;
    }
};

int main() {
    Base* obj = new Derived();
    Base* newObj = obj->create(); // Cria um novo objeto de Derived

    newObj->display();

    delete obj;
    delete newObj;
    return 0;
}
						```
					</details>
			</details>
			<details>
			<summary>Classes abstratas</summary>
				- Uma classe abstrata possui pelo menos uma função puramente virtual (sem implementação) que é usada como base para criar outras classes
				<details>
				<summary>Exemplo</summary>
					```c++
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0; // Função puramente virtual
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Desenhando um círculo." << endl;
    }
};

class Square : public Shape {
public:
    void draw() override {
        cout << "Desenhando um quadrado." << endl;
    }
};

int main() {
    Shape* shape1 = new Circle();
    Shape* shape2 = new Square();

    shape1->draw(); // Chama Circle::draw
    shape2->draw(); // Chama Square::draw

    delete shape1;
    delete shape2;
    return 0;
}
					```
				</details>
			</details>
		</details>
	</details>
</details>
---
## Tipos abstratos de dados e estruturas de dados
<details>
<summary>Type</summary>
	- É uma coleção de valores; no caso do bool, a sua coleção de valores consiste em true e false
</details>
<details>
<summary>Data item</summary>
	- É uma peça de informação na qual o valor vêm do type
	- Um data item é um member do type
</details>
<details>
<summary>Data type</summary>
	- É o tipo de dado juntamente com a coleção de operações que manipulam o type
		- Por exemplo, a operação de somar no type int
</details>
<details>
<summary>Abstract data type (ADT)</summary>
	- É basicamente o data type como um componente de software (e não de hardware)
</details>
<details>
<summary>Data structure</summary>
	- É a implementação do ADT
		- Em linguagens orientadas à objeto, por exemplo, o ADT juntamente com sua implementação é chamado de class e cada operação associada com o ADT é implementada pelos methods
		- Um object é uma instância de uma classe, ou seja, algo criado e que ocupa armazenamento durante a execução do programa
		- Além disso, as variáveis que definem o espaço requerido por um data item são referidos como data members
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
</details>
<details>
<summary>Tipos de ADT</summary>
	<details>
	<summary>Listas</summary>
		- É uma finita e ordenada sequência de itens de dado conhecido como elements
			- Ordenada significa que cada elemento tem uma posição dentro da lista
				- Cada elemento possui um data type
				- Pode ter listas com mais de um data type dentro dela
		- O conceito mais importante numa lista é a posição, ter a percepção do primeiro elemento da lista, segundo elemento e etc.
			- Quando a lista está vazia significa que não há elementos dentro dela
		- Length (tamanho) - número de elementos; Head (cabeça) - começo da lista; Tail (cauda) - final da lista 
		- Os elementos dentro da listas podem estar sortidos (sorted lists), com elementos em uma ordem disposta especificamente em ordem de valor
		- Quando vamos criar a nossa classe de lista, devemos criar um “tipo” E que serve como um espaço reservado para qualquer tipo de elemento (exemplo, se tivermos uma lista com char e int, se utilizarmos apenas char ou int daria um problema; então criamos E)
		<details>
		<summary>Operações básicas</summary>
			- Para criar os nossos métodos, precisamos de ter conhecimento acerca da posição inicial
			<details>
			<summary>Métodos</summary>
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
			</details>
			- Podemos criar mais métodos a depender do que queremos fazer
		</details>
		<details>
		<summary>Abordagens</summary>
			<details>
			<summary>Listas baseadas em array (Array-Based List)</summary>
				- Os elementos são armazenados em locais de memória unidos, formando uma array
				- Cada elemento possui um índice fixo que corresponde à posição deles na array
				<details>
				<summary>Exemplo</summary>
					<details>
					<summary>C</summary>
					</details>
					<details>
					<summary>C++</summary>
						```c++
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
					</details>
				</details>
			</details>
			<details>
			<summary>Listas encadeadas (Linked List)</summary>
				- Utiliza ponteiros e alocação de memória dinâmica
				- Uma lista encadeada é feita com uma série de objetos chamadas de nós da lista
					- É uma boa prática fazer uma classe de nó separada
					- Os objetos dentro dessa classe contém um local de elemento para guardar o valor desse elemento e um campo next para armazenar um ponteiro para o próximo nó na lista (porque para cada nó há um ponteiro para o próximo nó da lista)
				- Na classe da lista, haverá três ponteiros, que apontam para o começo da lista (head), final da lista (tail) e para a posição do elemento atual (curr)
					- Não precisamos declarar uma array de tamanho fixo quando a lista é criada, logo o parâmetro do tamanho é dispensável para listas encadeadas
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
				<details>
				<summary>Exemplo (fazer exemplo)</summary>
					<details>
					<summary>C</summary>
											</details>
					<details>
					<summary>C++</summary>
						```c++

						```
					</details>
				</details>
				<details>
				<summary>Doubly Linked Lists</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
				</details>
				<details>
				<summary>Circular Linked Lists</summary>
					> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
				</details>
			</details>
			<details>
			<summary>Array-based list vs Linked list</summary>
				- As listas baseadas em array tem a desvantagem de que o tamanho delas deve ser predeterminada antes que a array seja alocada 
					- Além disso, elas só cresem até o tamanho pré estabelecido
				- As listas baseadas em array tem a vantagem de que não há desperdício de espaço para um elemento
					- As listas encadeadas precisam de criar um ponteiro extra para cada nó da lista, o que pode ser uma quantidade considerável de armazenamento
				- No geral, é melhor utilizar listas encadeadas mas há casos em que listas baseadas em array são melhores
			</details>
		</details>
	</details>
	<details>
	<summary>Pilhas</summary>
		- É uma estrutura semelhante à uma lista, na qual os elementos são inseridos ou removidos apenas de uma das cabeças (head ou tail, LIFO (Last in First out, the element that is inserted last comes out first) or FILO (First in Last out, the element that is insert first comes out last))
			- Geralmente se usa LIFO
			- Basicamente podemos imaginar esse conceito como uma pilha de pratos, na qual o último prato a ser colocado é o primeiro a ser removido
				- Essa restrição faz com que pilhas sejam menos flexíveis que listas, mas não tira a eficiência da pilha
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
		<details>
		<summary>Operações básicas</summary>
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
		</details>
		<details>
		<summary>Abordagens</summary>
			<details>
			<summary>Pilhas baseadas em array</summary>
				- Nessa implementação, listArray deve ser criada com um tamanho fixo quando a pilha for criada
				<details>
				<summary>C</summary>
				</details>
				<details>
				<summary>C++</summary>
					```c++
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
				</details>
			</details>
			<details>
			<summary>Pilhas encadeadas</summary>
				- Como estamos lidando apenas com o elemento que está no topo da pilha, não utilizaremos os três ponteiros; apenas precisamos de um ponteiro que aponte para o elemento do topo da pilha
					- Possui uma lógica semelhante à listas encadeadas
				```c

				```
			</details>
			- Ambas as abordagens são eficientes
			<details>
			<summary>C</summary>
			</details>
			<details>
			<summary>C++</summary>
			</details>
		</details>
	</details>
	<details>
	<summary>FIlas</summary>
		- Assim como as pilhas, as filas são estruturas semelhantes à uma lista que fornece acesso restrito aos seus elementos
			- A diferença é que os elemento são inseridos no final da fila (enqueue operation) e são removidos no começo da fila (dequeue operation) (FIFO, First in, First out)
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
		<details>
		<summary>Operações</summary>
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
		</details>
		<details>
		<summary>Abordagens</summary>
			<details>
			<summary>Filas baseadas em array</summary>
				<details>
				<summary>C</summary>
				</details>
				<details>
				<summary>C++</summary>
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
				</details>
			</details>
			<details>
			<summary>Filas encadeadas</summary>
				- rear e front são ponteiros
				<details>
				<summary>C</summary>
				</details>
				<details>
				<summary>C++</summary>
					```c

					```
									</details>
			</details>
		</details>
	</details>
</details>
---
## Sets
<details>
<summary>Definição</summary>
	- Um set pode ser descrito como como uma coleção de elementos desordenados
		- Um set pode ser definido de forma explícita, listando os elementos, ou especificando uma propriedade de todos os elementos do set
</details>
<details>
<summary>Implementação</summary>
	- Pode ser implementado de duas formas
		<details>
		<summary>A primeira forma considera apenas sets que são subsets de um grande set U (universal set)</summary>
			- Se o set possui n elementos, então cada subset S de U pode ser representado por um bit string de tamanho n (bit vector); na qual se o i-th elemento de U pertence à S é igual à 1
				- Exemplo: U = \{1, 2, 3, 4, 5\}; S = \{2, 3, 5\}; então o bit vector de S \[e 01101
		</details>
		<details>
		<summary>A segunda forma é utilizando é usando estruturas de listas para indicar os elementos do set</summary>
			- É a forma mais comum de utilizar
			<details>
			<summary>Importante saber as diferenças entre sets e listas</summary>
				- Sets não admitem elementos iguais dentro dele, já a lista permite
					- Essa diferença é contornado pela introdução de multiset ou bag (coleção não ordenada de items que não são necessariamente distintos)
				- Outra coisa, sets são coleções não ordenadas de elementos, mas mudando a ordem dos elementos não causa mudanças no set
					- Por outro lado, se mudarmos a posição de elementos em uma lista isso causa mudanças na lista
			</details>
			- Na computação, as operações mais utilizadas que precisamos utilizar em sets são: encontrar um item pedido, adicionar um novo item e deletar um item da coleção
				- Uma estrutura de dados que implementa todas essas operações é chamada de dicionário
					- Por isso, uma implementação eficiente de um dicionário precisa encontrar um compromisso entre a eficiência da pesquisa e a eficiência das outras duas operações
						- Algumas maneiras de fazer isso é usando arrays (não muito indicado), listas encadeadas ou hashing e pesquisa balanceada de árvores
		</details>
	- Várias aplicações de computação requer partição dinâmica de um set de n-elementos em uma coleção de subsets disjuntos
		- Depois de ser inicializada como uma coleção de n subsets de elementos 1, a coleção está sujeita a uma sequência de operações mistas de união e busca
			- Problema de união de sets
	<details>
	<summary>ADT de um dicionário</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	</details>
</details>
---
## Trees
- Uma árvore (mais precisamente uma árvore livre) é um grafo conectado acíclico
	- Um grafo acíclico mas não necessariamente conectado é chamado de floresta
	> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
<details>
<summary>Árvores enraizadas</summary>
	- É basicamente uma árvore que possui uma raiz (nível 0) e possui no máximo dois filhos (nível 1) e cada filho dessa raiz possui no máximo mais dois filhos (nível 2) e assim por diante
	- Muito útil para implementar dicionários, acessar data sets muito largos e etc.
	<details>
	<summary>Nomenclatura</summary>
		- Root (Raiz): é o vértice originário da árvore
		- Parent (Pai): é um vértice que possui filhos
		- Child (Filho): é um vértice que vêm de um pai
		- Siblings (Irmãos): vértices que vêm do mesmo pai
		- Leaf (Folha): um vértice que não possui filhos
		- Parental (Parente): é um vértice que possui pelo menos um filho
		- Descendants (Descendentes): Todos os vértices que se originaram de um vértice v
		- Depth (Profundidade): a profundidade de um vértice v é basicamente quantos vértices ele precisa passar para chegar na raiz
		- Heigth (Altura): o maior tamanho entre uma folha e a raiz
	</details>
</details>
<details>
<summary>Árvores ordenadas</summary>
	- É uma árvore enraizada onde todo vértice está ordenado
	- Árvore binária
		- Uma árvore em que cada vértice não tem mais que dois filhos e cada filho é designado como ou filho à esquerda do pai ou filho à direita do pai; além disso, ela pode ser uma árvore vazia
</details>
<details>
<summary>Binary search tree (BST) (Árvore de busca binária)</summary>
	- É uma árvore binária ordenada em que cada vértice representa um número
	- Todo filho à esquerda é um número menor que o número do pai e todo filho à direita é um número maior ou igual ao número do pai
		- A raiz é a única que não é filho à esquerda ou à direita pois não possui pais, logo a árvore é baseada no valor da raiz
		- Para implementar, é preciso de ponteiros em todos os vértices
	<details>
	<summary>Exemplo</summary>
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
		> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
	</details>
</details>
<details>
<summary>Traversals (Travesias)</summary>
	- Percorrer todos os elementos de um grafo
	<details>
	<summary>Pre-order</summary>
		- Percorremos primeiro a raiz e depois percorremos o filho à esquerda dela
			- Após isso, percorremos o filho à esquerda dos filhos da esquerda
				- Caso algum filho à esquerda possua um filho à direita, ele será percorrida apenas quando o código percorrer o último filho à esquerda de forma de recursiva
		- Após isso, o filho à direita da raiz é percorrido seguindo a mesma lógica acima
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- Pre-order: 37 (raiz), 24 (filho à esquerda da raiz), 7 (neto à esquerda à esquerda da raiz), 2 (bisneto à esquerda à esquerda à esquerda da raiz), 32 (neto à esquerda à direita da raiz), 42 (filho à direita da raiz), 40 (neto à direita à esquerda da raiz), 42 (neto à direita à direita da raiz), 120 (bisneto à direita à direita da raiz)
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- Pre-order: 5, 3, 2, 1, 4, 7, 6, 8, 7, 12, 9, 14, 23, 21, 18, 56
		</details>
	</details>
	<details>
	<summary>In-order</summary>
		- Percorremos primeiro o último dos filhos à esquerda e vamos voltando recursivamente dando prioridade para os filhos à esquerda e depois aos filhos à direita (desde o primeiro à direita até o último) antes de chegar à raiz
		- Após percorrer todo o lado esquerdo da raiz, percorremos a raiz e logo após percorremos o lado direito da raiz dando prioridade aos filhos à esquerda de cada vértice (percorremos eles e depois percorremos o próprio vértice)
		- Vendo à risca, é basicamente uma ordem não decrescente
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- In-order: 2, 7, 24, 32, 37, 40, 42, 42, 120
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- In-order: 1, 2, 3, 4 (esquerda da raiz), 5, 6, 7, 7, 8, 9, 12, 14, 18, 21, 23, 56
		</details>
	</details>
	<details>
	<summary>Post-order</summary>
		- Primeiro percorremos o lado esquerdo da raiz, depois o lado direito e por fim percorremos a raiz
			- Ao percorrer o lado esquerdo, percorremos o último filho à esquerda de todos e depois percorremos o seu irmão, caso ele tenha algum filho à esquerda então antes percorremos ele e caso tenha um filho à direita percorremos ele antes também; a lógica prevalece para o lado direito
		<details>
		<summary>Exemplo</summary>
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- Post-order: 2, 7, 32, 24, 40, 120, 42, 42, 37
			> 🖼️ *Imagem não migrada ainda — [ver original no Notion](https://www.notion.so/13c237a419458082a01edd1dc5c9d1b6)*
			- Post-order: 1, 2, 4, 3, 6, 7, 9, 18, 21, 56, 23, 14, 12, 8, 7, 5
		</details>
	</details>
</details>
---
