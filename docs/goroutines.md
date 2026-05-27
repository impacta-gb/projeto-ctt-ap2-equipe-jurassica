# Goroutines em Go

As goroutines são uma das funcionalidades mais importantes da linguagem Go.

Elas permitem executar funções de forma concorrente, possibilitando que várias tarefas aconteçam ao mesmo tempo.

A concorrência é uma das principais características do Go.

---

# O que é concorrência?

Concorrência é a capacidade de executar múltiplas tarefas simultaneamente.

Exemplos:

- baixar arquivos enquanto o usuário navega
- processar múltiplas requisições em um servidor
- executar cálculos paralelos
- rodar tarefas em segundo plano

---

# O que é uma goroutine?

Uma goroutine é uma função executada concorrentemente.

Criar uma goroutine em Go é extremamente simples:

```go
go nomeDaFuncao()
```

A palavra-chave `go` inicia uma nova goroutine.

---

# Primeiro exemplo

```go
package main

import (
    "fmt"
    "time"
)

func mensagem() {

    fmt.Println("Executando goroutine")
}

func main() {

    go mensagem()

    time.Sleep(time.Second)
}
```

---

# Explicando o código

A linha:

```go
go mensagem()
```

executa a função `mensagem()` concorrentemente.

Entretanto, o programa principal pode terminar antes da goroutine executar.

Por isso usamos:

```go
time.Sleep(time.Second)
```

para esperar um pouco antes do encerramento do programa.

---

# Importando o pacote `time`

Para usar pausas temporárias:

```go
import "time"
```

Exemplo:

```go
time.Sleep(time.Second)
```

Isso faz o programa esperar 1 segundo.

---

# Executando múltiplas goroutines

```go
package main

import (
    "fmt"
    "time"
)

func tarefa(nome string) {

    for i := 1; i <= 5; i++ {

        fmt.Println(nome, "-", i)

        time.Sleep(500 * time.Millisecond)
    }
}

func main() {

    go tarefa("Goroutine 1")

    go tarefa("Goroutine 2")

    time.Sleep(4 * time.Second)
}
```

---

# Resultado esperado

A saída aparecerá misturada:

```text
Goroutine 1 - 1
Goroutine 2 - 1
Goroutine 1 - 2
Goroutine 2 - 2
```

Isso acontece porque ambas executam simultaneamente.

---

# Funções anônimas com goroutines

Também podemos usar funções anônimas.

Exemplo:

```go
package main

import (
    "fmt"
    "time"
)

func main() {

    go func() {
        fmt.Println("Executando função anônima")
    }()

    time.Sleep(time.Second)
}
```

---

# Goroutines são leves

As goroutines consomem pouca memória.

Isso permite criar milhares delas ao mesmo tempo.

Essa é uma das vantagens do Go em aplicações concorrentes.

---

# Diferença entre threads e goroutines

## Threads

Threads são controladas pelo sistema operacional.

Elas são mais pesadas e consomem mais recursos.

---

## Goroutines

Goroutines são controladas pelo runtime do Go.

São mais leves e eficientes.

---

# Problema comum: programa encerrando cedo

Observe:

```go
package main

import "fmt"

func mensagem() {
    fmt.Println("Olá")
}

func main() {

    go mensagem()
}
```

Muitas vezes nada será exibido.

O programa termina antes da goroutine executar.

---

# Solução simples

Adicionar espera:

```go
time.Sleep(time.Second)
```

Embora funcione em exemplos pequenos, aplicações reais normalmente utilizam sincronização com `WaitGroup`.

---

# Introdução ao WaitGroup

O `WaitGroup` pertence ao pacote `sync`.

Ele permite esperar múltiplas goroutines terminarem.

---

# Exemplo com WaitGroup

```go
package main

import (
    "fmt"
    "sync"
)

func tarefa(nome string, wg *sync.WaitGroup) {

    defer wg.Done()

    fmt.Println(nome)
}

func main() {

    var wg sync.WaitGroup

    wg.Add(2)

    go tarefa("Goroutine 1", &wg)

    go tarefa("Goroutine 2", &wg)

    wg.Wait()
}
```

---

# Explicando o WaitGroup

## `wg.Add(2)`

Informa que existem 2 goroutines.

---

## `wg.Done()`

Indica que uma goroutine terminou.

Normalmente usamos:

```go
defer wg.Done()
```

---

## `wg.Wait()`

Faz o programa esperar todas as goroutines terminarem.

---

# Aplicações reais de goroutines

As goroutines são muito usadas em:

- servidores web
- APIs
- processamento paralelo
- sistemas distribuídos
- microserviços
- tarefas assíncronas
- filas de processamento

---

# Cuidados com concorrência

Concorrência pode causar problemas quando múltiplas goroutines acessam os mesmos dados.

Isso é chamado de:

- condição de corrida (race condition)

Em aplicações maiores usamos:

- mutex
- channels
- sincronização

---

# Introdução aos channels

Channels permitem comunicação entre goroutines.

Exemplo:

```go
canal := make(chan string)
```

Eles serão estudados mais profundamente em tópicos avançados.

---

# Exemplo simples com channel

```go
package main

import "fmt"

func mensagem(canal chan string) {

    canal <- "Olá do channel"
}

func main() {

    canal := make(chan string)

    go mensagem(canal)

    msg := <-canal

    fmt.Println(msg)
}
```

---

# Explicando o exemplo

Enviar valor:

```go
canal <- "Olá"
```

Receber valor:

```go
msg := <-canal
```

Channels ajudam goroutines a se comunicarem com segurança.

---

# Resumo

Nesta página aprendemos:

- O que são goroutines
- Como criar goroutines
- Concorrência em Go
- Uso de `time.Sleep`
- Uso de funções anônimas
- Uso de `WaitGroup`
- Introdução a channels
- Cuidados com concorrência

As goroutines são uma das funcionalidades mais poderosas e famosas da linguagem Go.