# Arrays, Slices e Maps

Ao desenvolver aplicações em Go, frequentemente precisamos armazenar múltiplos valores.

Para isso, Go oferece diferentes estruturas de dados, sendo as principais:

- Arrays
- Slices
- Maps

Cada uma possui características específicas e diferentes formas de utilização.

---

# Arrays

Arrays são estruturas que armazenam múltiplos valores do mesmo tipo.

Em Go:
- arrays possuem tamanho fixo;
- o tamanho faz parte do tipo da variável.

---

# Criando um Array

```go
package main

import "fmt"

func main() {

    var numeros [5]int

    numeros[0] = 10
    numeros[1] = 20
    numeros[2] = 30

    fmt.Println(numeros)

}
```

---

# Explicando o Código

```go
var numeros [5]int
```

Isso significa:

- `numeros` → nome da variável;
- `[5]` → tamanho do array;
- `int` → tipo dos elementos.

O array poderá armazenar:
- exatamente 5 números inteiros.

---

# Índices

Arrays utilizam índices iniciando em `0`.

| Índice | Valor |
|---|---|
| 0 | Primeiro elemento |
| 1 | Segundo elemento |
| 2 | Terceiro elemento |

---

# Exemplo Visual

```go
[10, 20, 30, 0, 0]
```

---

# Inicialização Direta

Também é possível criar arrays já preenchidos.

```go
package main

import "fmt"

func main() {

    frutas := [3]string{
        "Maçã",
        "Banana",
        "Uva",
    }

    fmt.Println(frutas)

}
```

---

# Obtendo o Tamanho

Utilizamos a função `len()`.

```go
fmt.Println(len(frutas))
```

Saída:

```text
3
```

---

# Limitações dos Arrays

Arrays possuem algumas limitações:
- tamanho fixo;
- pouca flexibilidade;
- cópia completa ao serem passados para funções.

Por isso, em Go, normalmente utilizamos `slices`.

---

# Slices

Slices são estruturas dinâmicas baseadas em arrays.

Eles são muito mais utilizados em aplicações reais.

---

# Criando um Slice

```go
package main

import "fmt"

func main() {

    nomes := []string{
        "Carlos",
        "Ana",
        "Julia",
    }

    fmt.Println(nomes)

}
```

---

# Diferença Principal

Array:

```go
[3]string
```

Slice:

```go
[]string
```

No slice:
- não definimos tamanho fixo.

---

# Adicionando Elementos

Utilizamos a função `append()`.

```go
package main

import "fmt"

func main() {

    numeros := []int{1, 2, 3}

    numeros = append(numeros, 4)

    fmt.Println(numeros)

}
```

Saída:

```text
[1 2 3 4]
```

---

# Explicando o APPEND

```go
append(numeros, 4)
```

A função:
- adiciona novos elementos;
- retorna um novo slice atualizado.

---

# Acessando Valores

```go
nomes[0]
```

Representa o primeiro elemento.

---

# Alterando Valores

```go
nomes[1] = "Pedro"
```

---

# Percorrendo Slices

Normalmente utilizamos `for`.

```go
package main

import "fmt"

func main() {

    numeros := []int{10, 20, 30}

    for i, valor := range numeros {
        fmt.Println(i, valor)
    }

}
```

---

# Explicando o RANGE

```go
range numeros
```

O `range` percorre:
- índices;
- valores.

---

# Saída

```text
0 10
1 20
2 30
```

---

# Criando Slices com MAKE

A função `make()` permite criar slices com tamanho e capacidade.

```go
package main

import "fmt"

func main() {

    numeros := make([]int, 5)

    fmt.Println(numeros)

}
```

---

# Explicando o MAKE

```go
make([]int, 5)
```

Significa:
- criar slice de inteiros;
- com tamanho 5.

---

# Capacidade do Slice

Slices possuem:
- tamanho (`len`);
- capacidade (`cap`).

```go
package main

import "fmt"

func main() {

    numeros := make([]int, 5, 10)

    fmt.Println(len(numeros))
    fmt.Println(cap(numeros))

}
```

---

# Explicando

```go
make([]int, 5, 10)
```

- tamanho inicial = 5;
- capacidade = 10.

---

# MAPS

Maps armazenam dados em formato:
- chave → valor.

São semelhantes a:
- dicionários;
- objetos JSON;
- hashmaps.

---

# Criando um Map

```go
package main

import "fmt"

func main() {

    usuario := map[string]string{
        "nome":  "Carlos",
        "cidade": "São Paulo",
    }

    fmt.Println(usuario)

}
```

---

# Explicando o Tipo

```go
map[string]string
```

Significa:

- chave do tipo `string`;
- valor do tipo `string`.

---

# Acessando Valores

```go
fmt.Println(usuario["nome"])
```

Saída:

```text
Carlos
```

---

# Adicionando Valores

```go
usuario["idade"] = "25"
```

---

# Alterando Valores

```go
usuario["cidade"] = "Rio de Janeiro"
```

---

# Removendo Valores

Utilizamos `delete()`.

```go
delete(usuario, "cidade")
```

---

# Verificando Existência

```go
valor, existe := usuario["nome"]
```

---

# Exemplo Completo

```go
package main

import "fmt"

func main() {

    usuario := map[string]string{
        "nome": "Ana",
    }

    valor, existe := usuario["nome"]

    if existe {
        fmt.Println(valor)
    }

}
```

---

# Percorrendo Maps

```go
package main

import "fmt"

func main() {

    usuario := map[string]string{
        "nome":  "Carlos",
        "cidade": "Curitiba",
    }

    for chave, valor := range usuario {
        fmt.Println(chave, valor)
    }

}
```

---

# Comparando Estruturas

| Estrutura | Característica |
|---|---|
| Array | Tamanho fixo |
| Slice | Tamanho dinâmico |
| Map | Chave e valor |

---

# Quando Utilizar Arrays

Arrays são úteis quando:
- o tamanho é conhecido;
- os dados são fixos;
- não haverá crescimento.

---

# Quando Utilizar Slices

Slices são ideais para:
- listas dinâmicas;
- coleções flexíveis;
- aplicações reais.

!!! tip "Boa prática"
    Em Go, slices são muito mais utilizados do que arrays.

---

# Quando Utilizar Maps

Maps são ideais para:
- buscas rápidas;
- associações entre dados;
- armazenamento de configurações.

---

# Exemplo Completo Integrando Tudo

```go
package main

import "fmt"

func main() {

    numeros := []int{10, 20, 30}

    usuario := map[string]string{
        "nome": "João",
    }

    for _, numero := range numeros {
        fmt.Println(numero)
    }

    fmt.Println(usuario["nome"])

}
```

---

# Explicando o Underscore (_)

```go
for _, numero := range numeros
```

O `_` é utilizado para ignorar valores.

Nesse caso:
- ignoramos o índice;
- utilizamos apenas o valor.

---

# Cuidados Importantes

!!! warning "Atenção"
    Acessar índices inexistentes em arrays e slices gera erro.

Exemplo incorreto:

```go
numeros[100]
```

---

# Outro Cuidado

!!! warning "Maps retornam valor zero"
    Ao acessar uma chave inexistente em um map, Go retorna o valor padrão do tipo.

Por isso, normalmente verificamos:
- se a chave existe;
- antes de utilizar o valor.

---

# Conclusão

Arrays, slices e maps são estruturas fundamentais em Go.

Cada uma possui objetivos específicos:

- Arrays → dados fixos;
- Slices → listas dinâmicas;
- Maps → associações chave e valor.

Compreender corretamente essas estruturas é essencial para construir aplicações organizadas, eficientes e escaláveis em Go.