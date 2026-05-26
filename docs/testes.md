# Testes Automatizados em Go

Go possui suporte nativo para testes.

## Arquivo de teste

```go
func TestSoma(t *testing.T) {
    resultado := Soma(2, 2)

    if resultado != 4 {
        t.Error("Erro no teste")
    }
}
```

## Executando testes

```bash
go test
```

!!! note "Importante"
    Testes automatizados aumentam a confiabilidade do software.
