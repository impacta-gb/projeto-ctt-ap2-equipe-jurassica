# Goroutines

Goroutines permitem concorrência em Go.

## Criando uma Goroutine

```go
go minhaFuncao()
```

## Exemplo

```go
func mensagem() {
    fmt.Println("Executando")
}

func main() {
    go mensagem()
}
```

!!! warning "Cuidado"
    Goroutines podem gerar problemas de concorrência sem sincronização.
