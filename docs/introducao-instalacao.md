# Introdução e Instalação

Go, também conhecida como Golang, é uma linguagem de programação criada pelo Google em 2009. A linguagem foi desenvolvida por Robert Griesemer, Rob Pike e Ken Thompson com o objetivo de oferecer simplicidade, alto desempenho e suporte moderno à concorrência.

Go se tornou extremamente popular no desenvolvimento de aplicações backend, microsserviços, APIs, ferramentas de linha de comando, sistemas distribuídos e soluções em cloud computing.

Entre suas principais características estão:

- Sintaxe simples e objetiva
- Compilação extremamente rápida
- Excelente gerenciamento de concorrência
- Binários leves e eficientes
- Facilidade de manutenção
- Forte tipagem estática
- Biblioteca padrão robusta

---

## Por que aprender Go?

A linguagem Go vem sendo amplamente utilizada por grandes empresas de tecnologia devido à sua performance e simplicidade.

Diversos projetos famosos utilizam Go, como:

| Tecnologia | Utilização |
|---|---|
| Docker | Containers |
| Kubernetes | Orquestração de containers |
| Terraform | Infraestrutura como código |
| Grafana | Observabilidade |
| Prometheus | Monitoramento |

Além disso, Go possui uma curva de aprendizado relativamente amigável para iniciantes quando comparada a outras linguagens de baixo nível.

!!! note "Curiosidade"
    O apelido "Golang" surgiu para evitar ambiguidades em pesquisas na internet, mas o nome oficial da linguagem é apenas "Go".

---

# Instalação da Linguagem

A instalação do Go pode ser realizada diretamente pelo site oficial da linguagem.

## Download Oficial

Acesse:

```text
https://go.dev/dl/
```

Escolha a versão adequada para o seu sistema operacional:

- Windows
- Linux
- macOS

---

# Instalação no Windows

Após baixar o instalador:

1. Execute o arquivo `.msi`
2. Clique em "Next"
3. Aceite os termos
4. Finalize a instalação

O instalador normalmente configura automaticamente as variáveis de ambiente necessárias.

---

# Verificando a Instalação

Após concluir a instalação, abra o terminal e execute:

```bash
go version
```

Se tudo estiver funcionando corretamente, o terminal exibirá algo semelhante a:

```bash
go version go1.25 windows/amd64
```

!!! success "Instalação concluída"
    Se o comando acima retornar a versão do Go, a linguagem foi instalada corretamente.

---

# Primeiro Programa em Go

Tradicionalmente, o primeiro programa criado em qualquer linguagem é o famoso "Hello World".

Crie um arquivo chamado:

```text
main.go
```

Agora adicione o seguinte código:

```go
package main

import "fmt"

func main() {
    fmt.Println("Olá, mundo!")
}
```

---

# Explicando o Código

## package main

```go
package main
```

Todo programa executável em Go deve pertencer ao pacote `main`.

Pacotes são utilizados para organizar e modularizar o código.

---

## import "fmt"

```go
import "fmt"
```

A palavra-chave `import` é utilizada para importar bibliotecas.

O pacote `fmt` pertence à biblioteca padrão do Go e é utilizado para:
- impressão de texto
- formatação
- entrada e saída de dados

---

## Função main

```go
func main()
```

A função `main()` representa o ponto de entrada da aplicação.

Quando o programa é executado, é essa função que será iniciada automaticamente.

!!! warning "Importante"
    Sem a função `main()`, o programa não poderá ser executado como aplicação.

---

## fmt.Println()

```go
fmt.Println("Olá, mundo!")
```

O comando `Println()` imprime informações no terminal.

O `ln` significa "line", indicando que uma nova linha será criada após a impressão.

---

# Executando o Programa

Para executar o programa, utilize o comando:

```bash
go run main.go
```

A saída será:

```text
Olá, mundo!
```

---

# Compilando o Programa

Go é uma linguagem compilada.

Isso significa que o código-fonte pode ser transformado em um executável independente.

Para compilar:

```bash
go build
```

Após a compilação:

- No Windows será criado um `.exe`
- No Linux/macOS será criado um binário executável

---

# Estrutura Básica de um Projeto Go

Um projeto simples geralmente possui a seguinte estrutura:

```text
meu-projeto/
│
├── go.mod
├── main.go
└── README.md
```

## Arquivos importantes

| Arquivo | Função |
|---|---|
| go.mod | Gerencia dependências |
| main.go | Código principal |
| README.md | Documentação do projeto |

---

# Gerenciamento de Dependências

Go utiliza um sistema chamado Go Modules para controlar dependências.

Para inicializar um projeto Go:

```bash
go mod init meu-projeto
```

Isso criará automaticamente o arquivo:

```text
go.mod
```

---

# Vantagens da Linguagem Go

Go possui diversas vantagens no desenvolvimento moderno:

- Simplicidade
- Performance
- Compilação rápida
- Facilidade de deploy
- Concorrência nativa
- Código legível
- Excelente suporte para backend

Além disso, a linguagem possui uma comunidade ativa e documentação oficial extremamente bem organizada.

---

# Conclusão

Go é uma linguagem moderna, eficiente e relativamente simples de aprender. Sua combinação de performance, simplicidade e concorrência faz dela uma excelente escolha para aplicações backend, microsserviços e sistemas escaláveis.

Nos próximos tópicos serão abordados:
- variáveis
- estruturas de controle
- arrays
- slices
- maps
- concorrência
- tratamento de erros
- testes automatizados
- módulos e pacotes