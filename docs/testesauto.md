# Testes Automatizados em GO

## O que são testes automatizados?

Testes automatizados são códigos criados para verificar se o programa está funcionando corretamente.

Eles ajudam a:

- encontrar erros
- validar funções
- evitar bugs
- garantir qualidade
- facilitar manutenção

Em GO, os testes já fazem parte da linguagem.

Não é necessário instalar frameworks externos para criar testes básicos.

---

# Por que testar aplicações?

Durante o desenvolvimento, alterações no código podem quebrar funcionalidades antigas.

Os testes servem para garantir que:

- tudo continue funcionando
- mudanças não criem erros inesperados
- o sistema permaneça estável

---

# Sistema de testes do GO

GO possui um pacote chamado:

```go
testing
```

Esse pacote é utilizado para criar testes automatizados.

---

# Estrutura de arquivos de teste

Os arquivos de teste devem terminar com:

```bash
_test.go
```

---

# Exemplo

```bash
matematica.go
matematica_test.go
```

---

# Criando uma função simples

## Arquivo: matematica.go

```go
package main

func Somar(a int, b int) int {
    return a + b
}
```

---

# Criando o primeiro teste

## Arquivo: matematica_test.go

```go
package main

import "testing"

func TestSomar(t *testing.T) {

    resultado := Somar(10, 5)

    esperado := 15

    if resultado != esperado {

        t.Errorf(
            "Resultado incorreto. Esperado: %d | Obtido: %d",
            esperado,
            resultado,
        )
    }
}
```

---

# Explicando o teste

## Nome da função

```go
func TestSomar
```

Funções de teste DEVEM começar com:

```go
Test
```

Caso contrário o GO não reconhecerá o teste.

---

# Pacote testing

```go
import "testing"
```

Importa o sistema oficial de testes do GO.

---

# Objeto t

```go
t *testing.T
```

Representa o controle do teste.

Ele permite:

- gerar erros
- registrar mensagens
- interromper testes
- exibir resultados

---

# Verificando resultados

```go
if resultado != esperado
```

Aqui verificamos se o retorno da função está correto.

---

# Exibindo erro

```go
t.Errorf()
```

Mostra uma mensagem caso o teste falhe.

---

# Executando testes

Para executar todos os testes:

```bash
go test
```

---

# Resultado esperado

Se tudo estiver correto:

```bash
PASS
ok
```

---

# Exemplo de teste falhando

Se o valor esperado estiver errado:

```go
esperado := 20
```

Resultado:

```bash
--- FAIL: TestSomar
Resultado incorreto. Esperado: 20 | Obtido: 15
FAIL
```

---

# Testando múltiplos cenários

É comum testar vários casos diferentes.

---

# Exemplo

```go
package main

import "testing"

func TestSomar(t *testing.T) {

    resultado1 := Somar(2, 3)

    if resultado1 != 5 {
        t.Errorf("Erro no teste 1")
    }

    resultado2 := Somar(10, 20)

    if resultado2 != 30 {
        t.Errorf("Erro no teste 2")
    }
}
```

---

# Testes em tabela (Table Driven Tests)

GO utiliza muito testes em tabela.

Essa é uma prática extremamente comum na linguagem.

---

# Exemplo completo

```go
package main

import "testing"

func Somar(a int, b int) int {
    return a + b
}

func TestSomar(t *testing.T) {

    testes := []struct {
        nome      string
        valor1    int
        valor2    int
        esperado  int
    }{
        {"Teste 1", 2, 3, 5},
        {"Teste 2", 10, 5, 15},
        {"Teste 3", 100, 50, 150},
    }

    for _, teste := range testes {

        resultado := Somar(teste.valor1, teste.valor2)

        if resultado != teste.esperado {

            t.Errorf(
                "%s falhou. Esperado: %d | Obtido: %d",
                teste.nome,
                teste.esperado,
                resultado,
            )
        }
    }
}
```

---

# Vantagens dos testes em tabela

## Organização

Facilita múltiplos cenários.

---

## Escalabilidade

Novos testes podem ser adicionados facilmente.

---

## Legibilidade

O código fica mais limpo.

---

# Executando testes detalhados

```bash
go test -v
```

---

# O que significa -v?

A flag `-v` significa:

```bash
verbose
```

Ela exibe detalhes de cada teste.

---

# Exemplo de saída

```bash
=== RUN   TestSomar
--- PASS: TestSomar
PASS
```

---

# Executando um teste específico

```bash
go test -run TestSomar
```

---

# Benchmark em GO

GO também suporta testes de desempenho.

Esses testes medem velocidade e performance.

---

# Exemplo de benchmark

```go
package main

import "testing"

func BenchmarkSomar(b *testing.B) {

    for i := 0; i < b.N; i++ {
        Somar(10, 20)
    }
}
```

---

# Executando benchmark

```bash
go test -bench=.
```

---

# O que significa b.N?

O GO executa a função várias vezes automaticamente para medir desempenho.

---

# Cobertura de testes

GO consegue medir quanto do código foi testado.

---

# Executando cobertura

```bash
go test -cover
```

---

# Exemplo de resultado

```bash
coverage: 85.3% of statements
```

---

# Gerando relatório detalhado

```bash
go test -coverprofile=coverage.out
```

---

# Visualizando relatório gráfico

```bash
go tool cover -html=coverage.out
```

---

# Testes paralelos

GO permite executar testes simultaneamente.

---

# Exemplo

```go
func TestAPI(t *testing.T) {

    t.Parallel()

    // código do teste
}
```

---

# Benefícios

- testes mais rápidos
- melhor aproveitamento do processador
- maior eficiência em projetos grandes

---

# Testes com falha imediata

## Exemplo

```go
t.Fatalf("Erro crítico")
```

---

# Diferença entre Errorf e Fatalf

| Método | Comportamento |
|---|---|
| Errorf | Registra erro e continua |
| Fatalf | Interrompe o teste imediatamente |

---

# Organização dos testes

Uma boa prática é separar:

```bash
projeto/
│
├── main.go
├── usuario.go
├── usuario_test.go
```

---

# Testando APIs

GO também permite testar APIs HTTP.

---

# Exemplo simples

```go
package main

import (
    "net/http"
    "net/http/httptest"
    "testing"
)

func TestStatusCode(t *testing.T) {

    requisicao := httptest.NewRequest(
        "GET",
        "/",
        nil,
    )

    resposta := httptest.NewRecorder()

    handler := http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.WriteHeader(http.StatusOK)
    })

    handler.ServeHTTP(resposta, requisicao)

    if resposta.Code != http.StatusOK {

        t.Errorf(
            "Status incorreto. Esperado: %d | Obtido: %d",
            http.StatusOK,
            resposta.Code,
        )
    }
}
```

---

# Vantagens dos testes automatizados

## Segurança

Reduz riscos de bugs.

---

## Qualidade

Garante funcionamento correto.

---

## Facilidade de manutenção

Mudanças ficam mais seguras.

---

## Desenvolvimento profissional

Projetos modernos normalmente exigem testes.

---

# Relação entre testes e CI/CD

Em pipelines CI/CD os testes são executados automaticamente.

Se um teste falhar:

- o deploy pode ser cancelado
- o merge pode ser bloqueado
- o erro é detectado rapidamente

---

# Comandos principais

| Comando | Função |
|---|---|
| go test | Executa testes |
| go test -v | Exibe detalhes |
| go test -run | Executa teste específico |
| go test -bench=. | Executa benchmarks |
| go test -cover | Mede cobertura |

---

# Conclusão

Os testes automatizados são essenciais em GO.

Eles ajudam a:

- validar funcionalidades
- reduzir bugs
- aumentar qualidade
- melhorar manutenção
- automatizar verificações

GO possui um sistema de testes simples, rápido e muito integrado à linguagem.