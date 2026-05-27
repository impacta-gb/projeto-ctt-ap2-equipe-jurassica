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
