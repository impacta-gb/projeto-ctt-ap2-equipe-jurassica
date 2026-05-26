# Structs e Métodos

Structs agrupam dados relacionados.

## Struct

```go
type Pessoa struct {
    Nome string
    Idade int
}
```

## Método

```go
func (p Pessoa) Apresentar() {
    fmt.Println(p.Nome)
}
```

!!! note "Boa prática"
    Structs ajudam na organização do código.
