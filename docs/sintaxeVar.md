# Sintaxe Básica e Variáveis

A linguagem Go foi criada com foco em simplicidade e legibilidade. Sua sintaxe é limpa, organizada e relativamente fácil de aprender quando comparada a outras linguagens de programação modernas.

Neste tópico serão apresentados os principais fundamentos da sintaxe da linguagem e o funcionamento de variáveis em Go.

---

# Estrutura Básica de um Programa

Todo programa executável em Go começa com uma estrutura semelhante a esta:

```go
package main

import "fmt"

func main() {
    fmt.Println("Olá, Go!")
}
```

---

# Entendendo Cada Parte

## package main

```go
package main
```

Todo arquivo Go pertence a um pacote.

O pacote `main` é especial porque indica que o programa poderá ser executado diretamente.

---

## import

```go
import "fmt"
```

A palavra-chave `import` é utilizada para importar bibliotecas.

Neste caso:
- `fmt` é uma biblioteca padrão da linguagem;
- utilizada para entrada e saída de dados.

---

## Função main

```go
func main() {
}
```

A função `main()` representa o ponto de entrada do programa.

Quando a aplicação é executada, é essa função que será iniciada automaticamente.

!!! note "Importante"
    Todo programa executável em Go precisa possuir uma função `main()` dentro do pacote `main`.

---

# Comentários

Comentários são utilizados para documentar o código e facilitar sua manutenção.

## Comentário de linha única

```go
// Isto é um comentário
```

---

## Comentário de múltiplas linhas

```go
/*
Comentário
de múltiplas
linhas
*/
```

---

# Variáveis

Variáveis são utilizadas para armazenar informações na memória durante a execução do programa.

Em Go, as variáveis possuem tipagem estática.

Isso significa que cada variável possui um tipo definido.

---

# Declarando Variáveis

## Forma tradicional

```go
var nome string = "Carlos"
```

Neste exemplo:

| Elemento | Função |
|---|---|
| var | Declara uma variável |
| nome | Nome da variável |
| string | Tipo da variável |
| "Carlos" | Valor armazenado |

---

## Exemplo completo

```go
package main

import "fmt"

func main() {
    var nome string = "Ana"

    fmt.Println(nome)
}
```

Saída:

```text
Ana
```

---

# Inferência de Tipo

Go consegue descobrir automaticamente o tipo da variável.

```go
var idade = 25
```

Nesse caso:
- Go identifica automaticamente que `idade` é do tipo `int`.

---

# Declaração Curta

Uma das formas mais utilizadas em Go é a declaração curta:

```go
nome := "Pedro"
```

Essa sintaxe:
- cria a variável;
- atribui o valor;
- infere automaticamente o tipo.

---

# Exemplo

```go
package main

import "fmt"

func main() {
    nome := "Maria"
    idade := 30

    fmt.Println(nome)
    fmt.Println(idade)
}
```

---

# Tipos Primitivos

Go possui diversos tipos básicos.

## Principais tipos

| Tipo | Descrição | Exemplo |
|---|---|---|
| int | Números inteiros | 10 |
| float64 | Números decimais | 3.14 |
| string | Texto | "Olá" |
| bool | Valores booleanos | true |

---

# Inteiros

```go
var numero int = 100
```

---

# Números Decimais

```go
var preco float64 = 19.99
```

---

# Strings

```go
var mensagem string = "Bem-vindo"
```

Strings representam textos.

---

# Booleanos

```go
var ativo bool = true
```

Valores booleanos podem ser:
- `true`
- `false`

---

# Impressão de Dados

A biblioteca `fmt` oferece diversas funções para exibir dados no terminal.

---

## fmt.Println()

```go
fmt.Println("Olá")
```

Adiciona uma quebra de linha automaticamente.

---

## fmt.Print()

```go
fmt.Print("Olá")
```

Não adiciona quebra de linha.

---

## fmt.Printf()

Permite formatar valores.

```go
nome := "Lucas"
idade := 22

fmt.Printf("Nome: %s | Idade: %d", nome, idade)
```

---

# Formatação com Printf

| Símbolo | Tipo |
|---|---|
| %s | string |
| %d | inteiro |
| %f | float |
| %t | booleano |

---

# Constantes

Constantes armazenam valores que não podem ser alterados.

```go
const pi = 3.14159
```

---

# Exemplo Completo

```go
package main

import "fmt"

func main() {
    const empresa = "Impacta"

    nome := "João"
    idade := 21
    altura := 1.75
    estudante := true

    fmt.Println("Empresa:", empresa)
    fmt.Println("Nome:", nome)
    fmt.Println("Idade:", idade)
    fmt.Println("Altura:", altura)
    fmt.Println("Estudante:", estudante)
}
```

---

# Entrada de Dados

Go também permite ler dados digitados pelo usuário.

## Exemplo com Scanln

```go
package main

import "fmt"

func main() {
    var nome string

    fmt.Print("Digite seu nome: ")
    fmt.Scanln(&nome)

    fmt.Println("Olá,", nome)
}
```

---

# Explicando o Operador &

```go
fmt.Scanln(&nome)
```

O símbolo `&` representa o endereço de memória da variável.

A função `Scanln()` precisa acessar diretamente a variável para modificar seu valor.

!!! warning "Atenção"
    O operador `&` é muito importante em Go e será bastante utilizado em conceitos mais avançados da linguagem.

---

# Boas Práticas

Ao trabalhar com variáveis em Go:

- utilize nomes claros;
- evite abreviações excessivas;
- prefira declaração curta (`:=`) quando apropriado;
- mantenha o código simples e legível.

---

# Convenções da Linguagem

Go possui algumas convenções importantes:

| Convenção | Exemplo |
|---|---|
| camelCase | nomeCompleto |
| nomes curtos | idade |
| nomes claros | quantidadeProdutos |

---

# Curiosidade Sobre Go

Diferente de muitas linguagens:
- Go não utiliza ponto e vírgula (`;`) explicitamente na maioria dos casos;
- o próprio compilador adiciona automaticamente quando necessário.

Isso ajuda a deixar o código mais limpo e legível.

---

# Conclusão

A sintaxe da linguagem Go foi projetada para ser simples, objetiva e eficiente. O sistema de variáveis é fácil de utilizar e contribui para a legibilidade do código.

Compreender corretamente:
- variáveis;
- tipos;
- constantes;
- entrada e saída de dados;

é fundamental para avançar nos próximos conceitos da linguagem.