# Estruturas de Controle

Estruturas de controle são responsáveis por controlar o fluxo de execução de um programa.

Com elas, é possível:
- tomar decisões;
- repetir ações;
- controlar comportamentos específicos do sistema.

Na linguagem Go, as principais estruturas de controle são:

- `if`
- `for`
- `switch`

Diferente de outras linguagens, Go busca manter essas estruturas simples e objetivas.

---

# Estrutura Condicional IF

A estrutura `if` é utilizada para executar um bloco de código apenas quando uma condição for verdadeira.

---

# Sintaxe Básica

```go
if condição {
    // código
}
```

---

# Exemplo Simples

```go
package main

import "fmt"

func main() {
    idade := 18

    if idade >= 18 {
        fmt.Println("Maior de idade")
    }
}
```

---

# Explicando o código

## Condição

```go
idade >= 18
```

Essa expressão retorna:
- `true`
- ou `false`

Se o resultado for verdadeiro, o bloco do `if` será executado

---

# Operadores Relacionais
| Operador | Significado |
|---|---|
| == | Igual |
| != | Diferente |
| > | Maior |
| < | Menor |
| >= | Maior ou igual |
| <= | Menor ou igual |

---

# IF com ELSE

O `else` é utilizado quando queremos executar outro bloco caso a condição seja falsa.

```go
package main

import "fmt"

func main() {
    idade := 15

    if idade >= 18 {
        fmt.Println("Maior de idade")
    } else {
        fmt.Println("Menor de idade")
    }
}
```

---

# IF com ELSE IF

O `else if` permite testar múltiplas condições.

```go
package main

import "fmt"

func main() {
    nota := 7

    if nota >= 9 {
        fmt.Println("Excelente")
    } else if nota >= 7 {
        fmt.Println("Aprovado")
    } else {
        fmt.Println("Reprovado")
    }
}
```

---

# Declaração Curta Dentro do IF

Go permite criar variáveis diretamente dentro da estrutura.

```go
package main

import "fmt"

func main() {
    if idade := 20; idade >= 18 {
        fmt.Println("Maior de idade")
    }
}
```

---

# Importante Sobre Chaves

Em Go:
- as chaves `{}` são obrigatórias;
- não existe `if` sem bloco.

!!! warning "Atenção"
    Diferente de algumas linguagens, Go não permite omitir chaves em estruturas condicionais.

---

# Estrutura de Repetição FOR

Go possui apenas uma estrutura oficial de repetição: o `for`.

Apesar disso, ela é extremamente versátil.

Com o `for`, é possível criar:
- loops tradicionais;
- loops infinitos;
- estruturas semelhantes ao `while`.

---

# FOR Tradicional

```go
for inicialização; condição; incremento {
    // código
}
```

---

# Exemplo

```go
package main

import "fmt"

func main() {
    for i := 1; i <= 5; i++ {
        fmt.Println(i)
    }
}
```

Saída:

```text
1
2
3
4
5
```

---

# Explicando o FOR

## Inicialização

```go
i := 1
```

Cria a variável de controle.

---

## Condição

```go
i <= 5
```

Enquanto essa condição for verdadeira, o loop continuará executando.

---

## Incremento

```go
i++
```

Aumenta o valor da variável a cada repetição.

---

# FOR Como WHILE

Go não possui a palavra-chave `while`.

No lugar disso:

```go
contador := 0

for contador < 5 {
    fmt.Println(contador)
    contador++
}
```

---

# Loop Infinito

Também é possível criar loops infinitos.

```go
for {
    fmt.Println("Executando...")
}
```

!!! warning "Cuidado"
    Loops infinitos podem travar programas caso não exista uma condição de parada, para isso, podemos usar o BREAK.

---

# BREAK

O comando `break` encerra imediatamente o loop.

```go
package main

import "fmt"

func main() {
    for i := 1; i <= 10; i++ {

        if i == 5 {
            break
        }

        fmt.Println(i)
    }
}
```

---

# CONTINUE

O comando `continue` pula para a próxima repetição.

```go
package main

import "fmt"

func main() {
    for i := 1; i <= 5; i++ {

        if i == 3 {
            continue
        }

        fmt.Println(i)
    }
}
```

Saída:

```text
1
2
4
5
```

---

# Estrutura SWITCH

O `switch` é utilizado para múltiplas decisões.

Ele deixa o código mais organizado quando existem muitas condições.

---

# Sintaxe Básica

```go
switch variável {
case valor:
    // código
}
```

---

# Exemplo Simples

```go
package main

import "fmt"

func main() {
    linguagem := "Go"

    switch linguagem {
    case "Python":
        fmt.Println("Linguagem Python")

    case "Go":
        fmt.Println("Linguagem Go")

    default:
        fmt.Println("Outra linguagem")
    }
}
```

---

# DEFAULT

O bloco `default` funciona como o `else`.

Ele será executado caso nenhum `case` seja verdadeiro.

---

# SWITCH Sem Variável

Go também permite utilizar `switch` sem informar uma variável.

```go
package main

import "fmt"

func main() {
    idade := 20

    switch {
    case idade < 18:
        fmt.Println("Menor de idade")

    case idade >= 18:
        fmt.Println("Maior de idade")
    }
}
```

---

# SWITCH com Múltiplos Valores

```go
package main

import "fmt"

func main() {
    letra := "a"

    switch letra {
    case "a", "e", "i", "o", "u":
        fmt.Println("Vogal")

    default:
        fmt.Println("Consoante")
    }
}
```

---

# FALLTHROUGH

Por padrão, Go NÃO executa automaticamente o próximo `case`.

Para isso existe o comando `fallthrough`.

```go
package main

import "fmt"

func main() {
    numero := 1

    switch numero {
    case 1:
        fmt.Println("Um")
        fallthrough
    case 2:
        fmt.Println("Dois")
    }
}
```

---

# Diferença Entre Go e Outras Linguagens

Em linguagens como C, Java e JavaScript:
- o `break` normalmente é obrigatório no `switch`.

Em Go:
- cada `case` já termina automaticamente;
- isso reduz erros acidentais.

---

# Comparando Estruturas

| Estrutura | Utilização |
|---|---|
| if | Decisões simples |
| else if | Múltiplas condições |
| for | Repetições |
| switch | Muitas possibilidades |

---

# Boas Práticas

Ao utilizar estruturas de controle:

- mantenha condições simples;
- evite muitos níveis de indentação;
- utilize `switch` quando houver muitas verificações;
- evite loops infinitos desnecessários.

---

# Exemplo Completo

```go
package main

import "fmt"

func main() {

    for i := 1; i <= 5; i++ {

        if i % 2 == 0 {
            fmt.Println(i, "é par")
        } else {
            fmt.Println(i, "é ímpar")
        }

    }

}
```

---

# Explicando o Operador %

```go
i % 2
```

O operador `%` representa o resto da divisão.

Exemplo:
- `4 % 2 = 0`
- `5 % 2 = 1`

Isso é muito utilizado para verificar:
- números pares;
- números ímpares.

---

# Conclusão

As estruturas de controle são fundamentais em qualquer linguagem de programação.

Em Go, elas foram projetadas para serem:
- simples;
- legíveis;
- eficientes.

Compreender corretamente:
- `if`
- `for`
- `switch`

é essencial para desenvolver programas mais complexos e organizados.