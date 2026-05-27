# Gerenciamento de Pacotes em GO (Go Modules)

## O que são Go Modules?

Go Modules são o sistema oficial de gerenciamento de dependências da linguagem GO.

Eles permitem:

- Organizar projetos
- Controlar versões de bibliotecas
- Baixar dependências automaticamente
- Compartilhar projetos facilmente
- Evitar conflitos entre versões

Antes dos Go Modules, o GO utilizava o `GOPATH`, que era mais limitado e difícil de gerenciar.

---

# O que é uma dependência?

Dependências são bibliotecas externas utilizadas no projeto.

Por exemplo:

- Frameworks web
- Bibliotecas de banco de dados
- Ferramentas de autenticação
- APIs
- Pacotes utilitários

---

# Criando um projeto com Go Modules

## Passo 1: criar uma pasta

```bash
mkdir meu-projeto
```

---

## Passo 2: entrar na pasta

```bash
cd meu-projeto
```

---

## Passo 3: iniciar o módulo

```bash
go mod init meu-projeto
```

---

# O que esse comando faz?

O comando:

```bash
go mod init meu-projeto
```

Cria o arquivo:

```bash
go.mod
```

Esse arquivo controla todas as dependências do projeto.

---

# Estrutura inicial do projeto

```bash
meu-projeto/
│
├── go.mod
└── main.go
```

---

# Conteúdo do arquivo go.mod

Após executar o comando, o arquivo ficará parecido com isso:

```go
module meu-projeto

go 1.25
```

---

# Significado das linhas

## Nome do módulo

```go
module meu-projeto
```

Define o nome do projeto.

---

## Versão do GO

```go
go 1.25
```

Define a versão da linguagem utilizada.

---

# Criando o primeiro programa

## Arquivo: main.go

```go
package main

import "fmt"

func main() {
    fmt.Println("Olá GO Modules!")
}
```

---

# Executando o projeto

```bash
go run main.go
```

---

# Instalando dependências

Uma das principais funções dos Go Modules é instalar bibliotecas externas.

---

# Exemplo de biblioteca externa

Vamos utilizar um framework web chamado Gin.

---

## Instalando o Gin

```bash
go get github.com/gin-gonic/gin
```

---

# O que acontece após instalar?

O GO:

- baixa a biblioteca
- salva a versão
- registra tudo no `go.mod`
- cria o arquivo `go.sum`

---

# Estrutura após instalação

```bash
meu-projeto/
│
├── go.mod
├── go.sum
└── main.go
```

---

# Arquivo go.sum

O `go.sum` armazena verificações de integridade das dependências.

Ele garante que:

- os pacotes não foram alterados
- os downloads são seguros
- as versões permanecem consistentes

---

# Exemplo de uso da biblioteca

```go
package main

import "github.com/gin-gonic/gin"

func main() {

    servidor := gin.Default()

    servidor.GET("/", func(c *gin.Context) {
        c.JSON(200, gin.H{
            "mensagem": "Servidor funcionando"
        })
    })

    servidor.Run()
}
```

---

# Atualizando dependências

Para atualizar bibliotecas:

```bash
go get -u
```

---

# Atualizando uma dependência específica

```bash
go get -u github.com/gin-gonic/gin
```

---

# Removendo dependências não utilizadas

```bash
go mod tidy
```

---

# O que o go mod tidy faz?

Esse comando:

- remove dependências inúteis
- organiza o projeto
- limpa imports não utilizados
- atualiza o `go.mod`

É um dos comandos mais importantes do GO.

---

# Verificando dependências

```bash
go list -m all
```

---

# Resultado esperado

O comando exibe todos os módulos instalados no projeto.

---

# Baixando dependências manualmente

```bash
go mod download
```

---

# Quando usar?

Esse comando é muito usado em:

- servidores
- CI/CD
- containers Docker
- pipelines automáticos

---

# Verificando problemas nas dependências

```bash
go mod verify
```

---

# O que ele faz?

Verifica se os arquivos baixados estão corretos e íntegros.

---

# Trabalhando com versões

GO Modules suporta versionamento.

---

# Instalando versão específica

```bash
go get github.com/gin-gonic/gin@v1.9.0
```

---

# Instalando última versão

```bash
go get github.com/gin-gonic/gin@latest
```

---

# Instalando versões antigas

```bash
go get github.com/gin-gonic/gin@v1.7.0
```

---

# Exemplo de go.mod completo

```go
module meu-projeto

go 1.25

require github.com/gin-gonic/gin v1.9.0
```

---

# Imports no GO

Quando uma dependência é instalada, ela pode ser importada normalmente.

---

## Exemplo

```go
import "github.com/gin-gonic/gin"
```

---

# Dependências indiretas

Às vezes uma biblioteca depende de outras.

Essas dependências aparecem como:

```go
// indirect
```

No arquivo `go.mod`.

---

# Exemplo

```go
require (
    github.com/gin-gonic/gin v1.9.0
    github.com/go-playground/validator/v10 v10.14.0 // indirect
)
```

---

# Vantagens dos Go Modules

## Controle de versões

Cada projeto possui suas próprias versões.

---

## Organização

As dependências ficam centralizadas no `go.mod`.

---

## Reprodutibilidade

Outro desenvolvedor consegue baixar exatamente as mesmas bibliotecas.

---

## Facilidade em equipes

Todos trabalham com o mesmo ambiente.

---

# Compartilhando projetos

Quando alguém clona o projeto:

```bash
git clone repositorio
```

Basta executar:

```bash
go mod tidy
```

ou:

```bash
go mod download
```

E todas as dependências serão instaladas automaticamente.

---

# Go Modules e GitHub

É muito comum usar bibliotecas hospedadas no GitHub.

Exemplo:

```bash
go get github.com/gin-gonic/gin
```

O GO baixa diretamente do repositório.

---

# Relação entre arquivos

| Arquivo | Função |
|---|---|
| go.mod | Controla módulos e versões |
| go.sum | Garante integridade dos pacotes |
| main.go | Código da aplicação |

---

# Comandos principais

| Comando | Função |
|---|---|
| go mod init | Inicializa módulo |
| go get | Instala dependências |
| go mod tidy | Limpa dependências |
| go mod download | Baixa módulos |
| go list -m all | Lista módulos |
| go mod verify | Verifica integridade |

---

# Conclusão

Go Modules são essenciais no desenvolvimento moderno com GO.

Eles permitem:

- gerenciamento de dependências
- controle de versões
- compartilhamento de projetos
- organização do código
- maior segurança

Praticamente todo projeto profissional em GO utiliza Go Modules.