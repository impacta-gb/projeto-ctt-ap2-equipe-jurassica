# Estruturas de Controle

Go possui estruturas simples para controle de fluxo.

## If

```go
idade := 18

if idade >= 18 {
    fmt.Println("Maior de idade")
}
```

## For

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

## Switch

```go
dia := 1

switch dia {
case 1:
    fmt.Println("Domingo")
default:
    fmt.Println("Outro dia")
}
```

!!! warning "Atenção"
    Go não possui while. O for é utilizado para repetição.
