# Projeto Jest - Integração Contínua com GitHub Actions

Este é meu primeiro projeto de integração contínua (CI) usando GitHub Actions. O projeto é parte da disciplina **Cultura e Práticas DevOps** do curso de pós-graduação em **Arquitetura de Sistemas Distribuídos** na PUC Minas.

## Descrição

O objetivo deste projeto é criar uma pipeline de CI que automatize a execução de testes unitários utilizando o framework **Jest**. A pipeline é configurada para instalar as dependências, realizar o build do projeto e rodar os testes de forma automática em cada push ou pull request no repositório.

## Configuração da CI

A pipeline está definida no arquivo `.github/workflows/ci.yml` e consiste em um único job chamado `teste-unidade`. Este job prepara o ambiente de execução e realiza os seguintes passos:

1. **Instalação do Node.js**: Define a versão do Node.js para o ambiente de execução.
2. **Instalação das Dependências**: Instala todas as dependências necessárias para o projeto utilizando `npm install`.
3. **Build do Projeto**: Realiza o build do projeto (se aplicável).
4. **Execução dos Testes**: Roda os testes unitários utilizando o Jest.

## Estrutura da Pipeline

Aqui está uma visão geral do job `teste-unidade`:

```yaml
name: CI

on:
  push: 
    branches: [ main ]

jobs:
  teste-unidade:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@sv3
      - name: Usar Node 20.15.0
        uses: actions/setup-node@v3
        with: 
          node-version: '20.15.0'

      - name: Instalar dependecias
        run: npm install

      - name: Build
        run: npm run build

      - name: Rodar teste de unidade com jest
        run: npm run test
```

## Como rodar os testes localmente

1. Certifique-se de que você tem o Node.js instalado.
2. Instale as dependências do projeto executando:

```
npm install
```

3. Rode os testes unitários com o comando

```
npm run test
```

## Tecnologias Utilizadas
- **Jest**: Framework de testes unitários em JavaScript.
- **GitHub Actions**: Plataforma de CI/CD para automação de workflows de desenvolvimento.
- **Node.js**: Ambiente de execução JavaScript.