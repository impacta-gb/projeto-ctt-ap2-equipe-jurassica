# Tratamento de Erros

Go trata erros de forma explícita.

## Exemplo

```go
arquivo, err := os.Open("teste.txt")

if err != nil {
    fmt.Println("Erro ao abrir arquivo")
}
```

!!! warning "Importante"
    Sempre verifique erros em aplicações Go.
