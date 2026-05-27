# Structs e Métodos

Em Go, `structs` são utilizadas para agrupar diferentes tipos de dados em uma única estrutura.

Elas são muito importantes no desenvolvimento de aplicações porque permitem representar:
- usuários;
- produtos;
- veículos;
- sistemas;
- entidades do mundo real.

Além disso, Go permite associar funções diretamente às structs através dos métodos.

---

# O Que é uma Struct

Uma struct é uma estrutura composta por campos.

Cada campo:
- possui um nome;
- possui um tipo.

---

# Sintaxe Básica

```go
type NomeStruct struct {
    Campo tipo
}
```

---

# Exemplo Simples

```go
package main

import "fmt"

type Pessoa struct {
    Nome  string
    Idade int
}

func main() {

    var usuario Pessoa

    usuario.Nome = "Carlos"
    usuario.Idade = 25

    fmt.Println(usuario)

}
```

---

# Explicando o Código

```go
type Pessoa struct
```

Cria um novo tipo chamado `Pessoa`.

---

# Campos da Struct

```go
Nome  string
Idade int
```

A struct possui:
- um campo `Nome`;
- um campo `Idade`.

---

# Acessando Campos

Utilizamos ponto (`.`).

```go
usuario.Nome
```

---

# Saída do Programa

```text
{Carlos 25}
```

---

# Inicialização Direta

Também é possível criar structs já preenchidas.

```go
package main

import "fmt"

type Pessoa struct {
    Nome  string
    Idade int
}

func main() {

    usuario := Pessoa{
        Nome:  "Ana",
        Idade: 22,
    }

    fmt.Println(usuario)

}
```

---

# Vantagem da Inicialização Nomeada

Essa abordagem:
- deixa o código mais legível;
- evita erros de posição;
- facilita manutenção.

---

# Structs com Muitos Campos

```go
type Produto struct {
    Nome      string
    Preco     float64
    Estoque   int
    Categoria string
}
```

---

# Utilizando Structs em Aplicações

Structs são extremamente comuns em:
- APIs;
- bancos de dados;
- sistemas web;
- microsserviços;
- aplicações empresariais.

---

# Métodos em Go

Métodos são funções associadas a uma struct.

Eles permitem que a struct tenha comportamentos próprios.

---

# Sintaxe de Método

```go
func (variavel Tipo) NomeMetodo() {
}
```

---

# Exemplo de Método

```go
package main

import "fmt"

type Pessoa struct {
    Nome string
}

func (p Pessoa) Apresentar() {
    fmt.Println("Olá, meu nome é", p.Nome)
}

func main() {

    usuario := Pessoa{
        Nome: "Carlos",
    }

    usuario.Apresentar()

}
```

---

# Explicando o Receiver

```go
func (p Pessoa)
```

Esse trecho é chamado de `receiver`.

Ele indica:
- que o método pertence à struct `Pessoa`.

---

# Chamando Métodos

```go
usuario.Apresentar()
```

---

# Métodos com Retorno

Métodos também podem retornar valores.

```go
package main

import "fmt"

type Produto struct {
    Nome  string
    Preco float64
}

func (p Produto) PrecoComDesconto() float64 {
    return p.Preco * 0.9
}

func main() {

    produto := Produto{
        Nome:  "Notebook",
        Preco: 5000,
    }

    fmt.Println(produto.PrecoComDesconto())

}
```

---

# Explicando o RETURN

```go
return p.Preco * 0.9
```

O método retorna:
- o valor do produto;
- com 10% de desconto.

---

# Métodos com Parâmetros

```go
package main

import "fmt"

type Conta struct {
    Saldo float64
}

func (c Conta) Depositar(valor float64) float64 {
    return c.Saldo + valor
}

func main() {

    conta := Conta{
        Saldo: 100,
    }

    resultado := conta.Depositar(50)

    fmt.Println(resultado)

}
```

---

# Structs Aninhadas

Uma struct pode conter outra struct.

```go
package main

import "fmt"

type Endereco struct {
    Cidade string
}

type Pessoa struct {
    Nome     string
    Endereco Endereco
}

func main() {

    usuario := Pessoa{
        Nome: "Lucas",
        Endereco: Endereco{
            Cidade: "São Paulo",
        },
    }

    fmt.Println(usuario.Endereco.Cidade)

}
```

---

# Ponteiros em Métodos

Métodos podem utilizar ponteiros.

Isso permite alterar os dados originais da struct.

---

# Exemplo com Ponteiro

```go
package main

import "fmt"

type Conta struct {
    Saldo float64
}

func (c *Conta) Depositar(valor float64) {
    c.Saldo += valor
}

func main() {

    conta := Conta{
        Saldo: 100,
    }

    conta.Depositar(50)

    fmt.Println(conta.Saldo)

}
```

---

# Explicando o Ponteiro

```go
func (c *Conta)
```

O `*` indica:
- que estamos trabalhando diretamente na struct original;
- evitando cópias.

---

# Diferença Entre Receiver Normal e Ponteiro

| Tipo | Comportamento |
|---|---|
| `(p Pessoa)` | Trabalha com cópia |
| `(p *Pessoa)` | Trabalha com valor original |

---

# Encapsulamento em Go

Em Go:
- nomes iniciados com letra maiúscula são públicos;
- nomes iniciados com letra minúscula são privados.

---

# Exemplo

```go
type Usuario struct {
    Nome string
    senha string
}
```

---

# Explicando

| Campo | Visibilidade |
|---|---|
| Nome | Público |
| senha | Privado |

---

# Métodos Como Comportamentos

Métodos ajudam a organizar melhor o código.

Exemplo:
- `Usuario.Login()`
- `Produto.CalcularDesconto()`
- `Conta.Sacar()`

---

# Exemplo Mais Realista

```go
package main

import "fmt"

type Carro struct {
    Marca string
    Ano   int
}

func (c Carro) Exibir() {
    fmt.Println(c.Marca, c.Ano)
}

func main() {

    carro := Carro{
        Marca: "Toyota",
        Ano:   2022,
    }

    carro.Exibir()

}
```

---

# Structs Vazias

Go permite structs vazias.

```go
type Config struct {}
```

---

# Utilização de Structs Vazias

São usadas em:
- sinais;
- controle interno;
- otimizações de memória.

---

# Comparando Structs e Classes

Go não possui classes tradicionais como:
- Java;
- C++;
- C#.

Porém:
- structs + métodos;
- oferecem comportamento semelhante.

---

# Principais Diferenças

| Go | Linguagens OO |
|---|---|
| Structs | Classes |
| Métodos | Métodos |
| Sem herança tradicional | Herança clássica |

---

# Boas Práticas

Ao utilizar structs:

- mantenha nomes claros;
- utilize métodos para comportamentos;
- evite structs gigantes;
- organize responsabilidades.

---

# Exemplo Completo

```go
package main

import "fmt"

type Funcionario struct {
    Nome   string
    Salario float64
}

func (f Funcionario) Bonus() float64 {
    return f.Salario * 0.2
}

func main() {

    funcionario := Funcionario{
        Nome: "Marcos",
        Salario: 5000,
    }

    fmt.Println(funcionario.Nome)
    fmt.Println(funcionario.Bonus())

}
```

---

# Conclusão

Structs e métodos são fundamentais em Go.

Eles permitem:
- organizar dados;
- representar entidades;
- criar comportamentos reutilizáveis.

Dominar structs é essencial para desenvolver aplicações modernas, organizadas e escaláveis na linguagem Go.