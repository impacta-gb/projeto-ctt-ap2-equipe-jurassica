# Tratamento de Erros em Go

O tratamento de erros é uma das características mais importantes da linguagem Go.

Diferente de outras linguagens que utilizam exceções automáticas (`try/catch`), Go trabalha com valores de erro explícitos, tornando o código mais previsível e fácil de entender.

---

# O tipo `error`

Em Go, erros são representados pela interface embutida chamada `error`.

Ela possui apenas um método:

```go
type error interface {
    Error() string
}
```

Quando uma função pode falhar, normalmente ela retorna:

- o valor esperado
- um erro

---

# Exemplo básico de erro

```go
package main

import (
    "fmt"
    "errors"
)

func dividir(a float64, b float64) (float64, error) {

    if b == 0 {
        return 0, errors.New("não é possível dividir por zero")
    }

    return a / b, nil
}

func main() {

    resultado, erro := dividir(10, 2)

    if erro != nil {
        fmt.Println("Erro:", erro)
        return
    }

    fmt.Println("Resultado:", resultado)
}
```

---

# Explicando o código

A função:

```go
func dividir(a float64, b float64) (float64, error)
```

retorna:

- um `float64`
- um `error`

Se ocorrer algum problema:

```go
return 0, errors.New("não é possível dividir por zero")
```

Caso tudo funcione corretamente:

```go
return a / b, nil
```

O valor `nil` significa ausência de erro.

---

# Verificando erros com `if`

Em Go, a maneira padrão de verificar erros é:

```go
if erro != nil {
    // tratar erro
}
```

Exemplo:

```go
if erro != nil {
    fmt.Println("Ocorreu um erro")
}
```

Esse padrão aparece constantemente em aplicações Go.

---

# Importando o pacote `errors`

O pacote `errors` permite criar erros personalizados.

```go
import "errors"
```

Criando um erro:

```go
errors.New("mensagem do erro")
```

Exemplo:

```go
erro := errors.New("arquivo não encontrado")
```

---

# Erros em leitura de entrada

Muitas funções da biblioteca padrão retornam erros.

Exemplo usando `fmt.Scanln`:

```go
package main

import "fmt"

func main() {

    var idade int

    fmt.Print("Digite sua idade: ")

    _, erro := fmt.Scanln(&idade)

    if erro != nil {
        fmt.Println("Valor inválido")
        return
    }

    fmt.Println("Idade:", idade)
}
```

---

# Múltiplos retornos

Go utiliza múltiplos retornos com frequência.

Exemplo:

```go
valor, erro := algumaFuncao()
```

Outro exemplo:

```go
arquivo, erro := os.Open("dados.txt")
```

---

# Ignorando valores com `_`

Às vezes queremos ignorar um retorno.

```go
_, erro := fmt.Scanln(&idade)
```

O `_` descarta o valor retornado.

---

# Criando funções seguras

Uma boa prática em Go é validar entradas antes de executar operações.

Exemplo:

```go
func sacar(saldo float64, valor float64) (float64, error) {

    if valor > saldo {
        return saldo, errors.New("saldo insuficiente")
    }

    saldo -= valor

    return saldo, nil
}
```

---

# Exemplo completo

```go
package main

import (
    "errors"
    "fmt"
)

func sacar(saldo float64, valor float64) (float64, error) {

    if valor <= 0 {
        return saldo, errors.New("valor inválido")
    }

    if valor > saldo {
        return saldo, errors.New("saldo insuficiente")
    }

    saldo -= valor

    return saldo, nil
}

func main() {

    saldo := 500.0

    novoSaldo, erro := sacar(saldo, 200)

    if erro != nil {
        fmt.Println("Erro:", erro)
        return
    }

    fmt.Println("Novo saldo:", novoSaldo)
}
```

---

# Boas práticas no tratamento de erros

## 1. Sempre verifique erros

Evite ignorar erros retornados por funções.

Errado:

```go
arquivo, _ := os.Open("dados.txt")
```

Correto:

```go
arquivo, erro := os.Open("dados.txt")

if erro != nil {
    fmt.Println("Erro ao abrir arquivo")
}
```

---

## 2. Use mensagens claras

Mensagens de erro devem explicar o problema.

Ruim:

```go
errors.New("erro")
```

Melhor:

```go
errors.New("usuário não encontrado")
```

---

## 3. Retorne erros cedo

Go utiliza muito o padrão:

```go
if erro != nil {
    return
}
```

Isso evita código excessivamente aninhado.

---

# Diferença entre Go e outras linguagens

Em muitas linguagens:

```java
try {
}
catch(Exception e) {
}
```

Em Go:

```go
if erro != nil {
    // tratar erro
}
```

Go prefere simplicidade e controle explícito.

---

# Resumo

Nesta página aprendemos:

- O que é o tipo `error`
- Como criar erros
- Como retornar erros em funções
- Como verificar erros com `if`
- Como usar `errors.New`
- Boas práticas no tratamento de erros

O tratamento explícito de erros é uma das marcas registradas da linguagem Go.