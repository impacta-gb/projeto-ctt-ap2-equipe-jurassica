# Channels

Channels permitem comunicação entre goroutines.

## Criando um channel

```go
ch := make(chan string)
```

## Exemplo

```go
func main() {
    ch := make(chan string)

    go func() {
        ch <- "Olá"
    }()

    mensagem := <- ch

    fmt.Println(mensagem)
}
```

!!! note "Importante"
    Channels ajudam a evitar problemas de concorrência.
