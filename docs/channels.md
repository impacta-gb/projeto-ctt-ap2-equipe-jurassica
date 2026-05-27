# Concorrência em GO: Channels

## O que são Channels?

Channels são mecanismos de comunicação entre goroutines.

Enquanto as goroutines executam tarefas simultaneamente, os channels permitem que elas troquem informações de forma segura.

Em GO existe uma frase muito famosa:

> “Não compartilhe memória entre goroutines. Compartilhe dados através de comunicação.”

Os channels ajudam exatamente nisso.

---

# Criando um Channel

Um channel é criado utilizando a função `make()`.

## Exemplo básico

```go
package main

import "fmt"

func main() {

    canal := make(chan string)

    go func() {
        canal <- "Olá Goroutine!"
    }()

    mensagem := <-canal

    fmt.Println(mensagem)
}
```

---

# Como funciona

## Criação do channel

```go
canal := make(chan string)
```

Aqui criamos um channel que transporta valores do tipo `string`.

---

## Enviando dados

```go
canal <- "Olá Goroutine!"
```

O operador `<-` envia dados para o channel.

---

## Recebendo dados

```go
mensagem := <-canal
```

Também usamos `<-`, mas agora para receber dados.

---

# Channels bloqueiam execução

Esse é um dos conceitos mais importantes.

## Ao enviar:

```go
canal <- valor
```

A execução pausa até alguém receber o valor.

---

## Ao receber:

```go
valor := <-canal
```

A execução pausa até alguém enviar algo.

Isso ajuda na sincronização automática entre goroutines.

---

# Exemplo com números

```go
package main

import "fmt"

func enviarNumero(canal chan int) {
    canal <- 10
}

func main() {

    canal := make(chan int)

    go enviarNumero(canal)

    numero := <-canal

    fmt.Println("Número recebido:", numero)
}
```

---

# Channels possuem tipos

## Exemplos

```go
chan int
chan string
chan bool
```

Você não pode enviar um tipo diferente do declarado.

---

# Channel somente leitura

```go
package main

import "fmt"

func receber(canal <-chan int) {

    numero := <-canal

    fmt.Println(numero)
}

func main() {

    canal := make(chan int)

    go func() {
        canal <- 50
    }()

    receber(canal)
}
```

---

## Significado

```go
<-chan int
```

Esse channel apenas recebe dados.

---

# Channel somente envio

```go
package main

func enviar(canal chan<- int) {
    canal <- 20
}

func main() {

    canal := make(chan int)

    go enviar(canal)

    <-canal
}
```

---

## Significado

```go
chan<- int
```

Esse channel apenas envia dados.

---

# Buffered Channels

Por padrão, channels armazenam apenas um valor por vez.

Mas podemos criar channels com buffer.

---

## Exemplo

```go
package main

import "fmt"

func main() {

    canal := make(chan string, 2)

    canal <- "Primeira mensagem"
    canal <- "Segunda mensagem"

    fmt.Println(<-canal)
    fmt.Println(<-canal)
}
```

---

## O que significa o número 2?

```go
make(chan string, 2)
```

O channel consegue armazenar até 2 valores antes de bloquear.

---

# Loops com Channels

Podemos percorrer channels usando `range`.

## Exemplo

```go
package main

import "fmt"

func main() {

    canal := make(chan int)

    go func() {

        for i := 1; i <= 5; i++ {
            canal <- i
        }

        close(canal)

    }()

    for numero := range canal {
        fmt.Println(numero)
    }
}
```

---

# Função close()

A função `close()` fecha o channel.

```go
close(canal)
```

Isso indica:

> “Nenhum valor novo será enviado.”

---

# Importância do close()

Sem o `close()`, loops com `range` podem nunca terminar.

---

# Select

O `select` permite esperar múltiplos channels ao mesmo tempo.

---

## Exemplo completo

```go
package main

import (
    "fmt"
    "time"
)

func main() {

    canal1 := make(chan string)
    canal2 := make(chan string)

    go func() {

        time.Sleep(2 * time.Second)

        canal1 <- "Resposta do canal 1"

    }()

    go func() {

        time.Sleep(1 * time.Second)

        canal2 <- "Resposta do canal 2"

    }()

    select {

    case mensagem1 := <-canal1:
        fmt.Println(mensagem1)

    case mensagem2 := <-canal2:
        fmt.Println(mensagem2)
    }
}
```

---

# O que acontece nesse exemplo?

O `select` espera múltiplos channels.

Como o `canal2` responde primeiro, ele será executado.

---

# Vantagens dos Channels

## Comunicação segura

Evita problemas de concorrência.

---

## Sincronização automática

As goroutines esperam umas pelas outras.

---

## Código mais organizado

A comunicação fica mais clara e previsível.

---

# Relação entre Goroutines e Channels

| Recurso | Função |
|---|---|
| Goroutine | Executa tarefas simultâneas |
| Channel | Permite comunicação entre goroutines |

---

# Conclusão

Channels são fundamentais para concorrência em GO.

Eles permitem:

- Comunicação entre goroutines
- Sincronização de tarefas
- Compartilhamento seguro de dados
- Controle de concorrência

Junto das goroutines, os channels formam a base da programação concorrente em GO.