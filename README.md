# Documentação da Linguagem Go

## Equipe Jurássica

### Integrantes

* Matheus Farias de Queiroz
* João Victor Santana Pereira

---

# Site Publicado

[Documentação da Linguagem Go](https://impacta-gb.github.io/projeto-ctt-ap2-equipe-jurassica/)

---

# Sobre o Projeto

Este projeto foi desenvolvido para a criação de uma documentação da linguagem Go utilizando Zensical, GitHub Actions e GitHub Pages.

O trabalho teve como foco:

* documentação em Markdown
* fluxo colaborativo com Git/GitHub
* Pull Requests e Code Review
* automação CI/CD
* deploy automatizado

---

# Tecnologias Utilizadas

* Go
* Markdown
* Git
* GitHub
* Zensical
* GitHub Actions
* GitHub Pages
* Python

---

# Inicialização do Projeto

## Clonar repositório

```bash id="j7n0xn"
git clone https://github.com/impacta-gb/projeto-ctt-ap2-equipe-jurassica.git
```

## Entrar na pasta

```bash id="h0s8mc"
cd projeto-ctt-ap2-equipe-jurassica
```

## Criar ambiente virtual

```powershell id="7w2qrl"
python -m venv .venv
```

## Ativar ambiente virtual

### PowerShell

```powershell id="g6fg2e"
.\.venv\Scripts\Activate.ps1
```

### Git Bash

```bash id="1rt9ub"
source .venv/Scripts/activate
```

## Instalar Zensical

```bash id="b7n5u0"
pip install zensical
```

## Executar localmente

```bash id="vy7njv"
zensical serve
```

---

# Estrutura de Desenvolvimento

As páginas foram criadas dentro da pasta:

```text id="f4aqz8"
docs/
```

Cada nova página adicionada também precisava ser incluída no arquivo:

```text id="71i0p3"
zensical.toml
```

---

# Fluxo de Trabalho

## Criar branch

```bash id="k9pq7r"
git checkout -b feat/nome-da-feature
```

## Adicionar alterações

```bash id="l1kz4r"
git add .
git commit -m "Mensagem do commit"
```

## Enviar branch

```bash id="55grta"
git push origin feat/nome-da-feature
```

## Abrir Pull Request

As alterações foram revisadas antes do merge na branch `main`.

---

# Proteção da Main

A branch `main` foi protegida para:

* impedir push direto
* exigir Pull Request
* exigir revisão antes do merge

---

# CI/CD

O pipeline foi configurado no arquivo:

```text id="vqk45x"
.github/workflows/CI-CD.yml
```

---

# Funcionalidades do Pipeline

* execução em `push`
* execução em `pull_request`
* execução semanal com `schedule`
* validação em múltiplas versões do Python
* cache de dependências
* separação de jobs
* upload/download de artifacts
* deploy automático no GitHub Pages

---

# Jobs do Workflow

## validate

Responsável pela validação do build em python.

## build_site

Responsável pela geração do site.

## deploy_site

Responsável pela publicação no GitHub Pages.

---

# Publicação

O deploy do site ocorre automaticamente após merge na branch `main`.

---

# Conclusão

O projeto permitiu aplicar conceitos de:

* documentação técnica
* Git/GitHub
* CI/CD
* automação
* colaboração em equipe
* GitHub Actions
* GitHub Pages
