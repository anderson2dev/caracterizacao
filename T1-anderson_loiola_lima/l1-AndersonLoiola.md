# Caracterização linguagem golang

[![gologo](img/big_gopher.jpg)](https://go.dev/)

## Aspectos gerais

Go é uma linguagem compilada e estaticamente tipada desenvolvida pelo Google e criada por [Robert Griesemer](https://en.wikipedia.org/wiki/Robert_Griesemer_(computer_programmer)), [Rob Pike](https://en.wikipedia.org/wiki/Rob_Pike) e [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson).

Go possui uma certa similaridade com o C (tanto sintática como em algumas features como por exemplo controle de ponteiros), mas também possui caracteristicas como segurança de memória (memory safety), garbage collection, structural typing e suporte a concorrencia no estilo [CSP](https://en.wikipedia.org/wiki/Communicating_sequential_processes).

## Atributos de qualidade

### Legibilidade

A go lang possuí uma sintaxe muito comum ao C como poder ser visto nos exemplos abaixos:

```c
// Programa escrito em c
#include<stdio.h>

int main(void) {
  println("Hello world\n");
  return 0;
}
```

```go
// Programa escrito em golang

package main

import "fmt"

func main() {
  fmt.PrintLn("Hello world\n")
}
```

Apesar das semelhanças sintáticas a golang possui um padrão sintático bem  particular
onde o case da primeira letra do identificador da variável/função/struct dita a visibilidade do mesmo por exemplo:

```go
package timer

import "time"

// A StopWatch is a simple clock utility.
// Its zero value is an idle clock with 0 total time.
type StopWatch struct {
    start   time.Time
    total   time.Duration
    running bool
}

// Start turns the clock on.
func (s *StopWatch) Start() {
    if !s.running {
        s.start = time.Now()
        s.running = true
    }
}
```

### Simplicidade

Go é uma linguagem extremamente simples e rápida de se aprenter uma vez que ela é extremamente enxuta (possuindo apenas 25 palavras reservadas), e possui uma sintaxe bem natural.

### Ortogonalidade

Para conseguir a  ortogonalidade, a  Golang é guiada pelos seguintes principios de design:

+ Faça uma coisa bem
+ Mantenha as coisas simples
+ Tenha uma maneira padrão de comunicação

O príncipio de  se fazer uma coisa bem (análogo ao simple responsability pattern na engenharia de software) pode ser percebido ao repararmos que o core da golang (a standard library) é orgazinado em pequenos pacotes onde cada um deles possui uma tarefa especifica e a faz muito bem, um exemplo de pacote que segue essa filosofia de design é o pacote de [http](godoc.org/net/http).

O principio de se fazer as coisas de maneira simples pode ser percebido ao analisarmos que go possui um conjunto extremamente enxuto de palavras reservadas (apenas 25) e que os módulos interno da linguagem nada mais são do que conjuntos de [struct](https://www.geeksforgeeks.org/structures-in-golang/), funções e variáveis aproveitando o próprio vocabulário da linguagem.

[![linguagens usadas no desenvolvimento da golang](img/golang_github_languages.PNG)](https://github.com/golang/go)

Já o principio de se manter uma maneira padronizada de se comunicar de maneira padronizada (uniforme) entre os módulos é alcançada por meio da definição de [interfaces](https://go.dev/doc/effective_go#interfaces), que servem para definir o comportamento de um objeto, especificando o que ele pode fazer exemplo:

```go
type clients []string

func (c &clients) AddClient(s string): bool {
  /** adds client*/
}

func (c clients) IsAdded(s string): bool {
  /** returns a client **/
}
```

O código acima define as operações operações que podem ser implementadas pelo tipo clients

Outro exemplo de definição de interface é

### Estruturas de controle

### Estruturas e tipos de dados

#### Tipos de dados

Tipos de dados especificam o que uma variável válida em go pode armazenar, podemos subdividr os tipos de dados presentes na linguagem golang em 4 tipos:

<table>
  <tr>
    <td> Nome: </td>
    <td> Descrição: </td>
  </tr>
    <tr>
      <td> Tipos primitivos </td>
      <td> Números, String e booleanos </td>
    </tr>
    <tr>
      <td> Tipos Agregados </td>
      <td> Array e <a href="https://www.geeksforgeeks.org/structures-in-golang/">Estruturas</a> </td>
    </tr>
    <tr>
      <td> Tipos de referência </td>
      <td> Ponteiros, slicers, maps, funções e channels </td>
    </tr>
    <tr>
      <td> Tipos de interfaces</td>
      <td> </td>
    </tr>
</table>

##### Números

Inteiros (Integers):  Na linguagem Go, ambos os números positivos e negativos estão disponíveis, onde um inteiro com sinal é representado por um int e um inteiro sem sinal é representado por uint

<table>
<tr>
  <td> Tipo: </td>
  <td> Descrição </td>
</tr>
<tr>
  <td> int8 </td>
  <td> Inteiro de 8 bit com sinal</td>
</tr>
<tr>
  <td> int16 </td>
  <td> Inteiro de 16 bit com sinal</td>
</tr>
<tr>
  <td> int64 </td>
  <td> Inteiro de 16 bit com sinal </td>
</tr>
<tr>
  <td> uint8 </td>
  <td> Inteiro de 8 bit sem sinal (positivo) </td>
</tr>
<tr>
  <td> uint16 </td>
  <td> Inteiro de 16 bit sem sinal </td>
</tr>
<tr>
  <td> uint32 </td>
  <td> Inteiro de 32 bit sem sinal </td>
</tr>
<tr>
  <td> uint64 </td>
  <td> Inteiro de 64 bit sem sinal </td>
</tr>
<tr>
  <td> int </td>
  <td> Inteiro que possui 32 ou 64 bit </td>
</tr>
<tr>
  <td> uint </td>
  <td> Inteiro sem sinal que possui 32 ou 64 bit</td>
</tr>
<tr>
  <td> rune </td>
  <td> Sinonimo de int32 </td>
</tr>
<tr>
  <td> byte </td>
  <td> sinonimo de int8 </td>
</tr>
<tr>
  <td> uintptr </td>
  <td> inteiro sem sinal com tamanho indefinido, mas pode armazenar todos os bits de um valor de um ponteiro </td>
</tr>
</table>

Números de ponto flutuante:  Na linguagem go, números de ponto flutuante são divididos em duas categorias conforme mostrado abaixo

<table>
<tr>
  <td>Tipo:</td>
  <td> Descrição: </td>
</tr>
<tr>
  <td> complex64 </td>
  <td>
    Ambas as partes real e a imaginária possuem 32 bit
  </td>
</tr>
<tr>
  <td> complex128 </td>
  <td> 
    Ambas as partes real e imaginária possuem 64 bits
  </td>
</tr>
</table>

<table>
<tr>
  <td>Tipo:</td>
  <td> Descrição: </td>
</tr>
<tr>
  <td> float32 </td>
  <td> Número de ponto flutuante de 32 bit no padrão IEEE 754 </td>
</tr>
<tr>
  <td> float64 </td>
  <td> Número de ponto flutuante de 64 bit no padrão IEEE 754 </td>
</tr>
</table>

##### Booleanos

Podem assumir os valores true ou false



#### Estruturas



### Aspectos sintáticos
