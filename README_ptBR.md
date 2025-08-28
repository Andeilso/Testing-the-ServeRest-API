# Testando a API ServeRest com Postman
> [English version of the walkthrough](./README.md)

Este projeto consiste em testar a API publica ServeRest com a utilização do Postman.

- Para a versão com massa de dados, foi utilizado um arquivo de dados em massa chamado "mass-of-data.csv".
- Para a versão sem massa de dados, foi utilizada uma API chamada "Random User Generation".

## Tecnologias utilizadas
- postman web version
- node - LTS version
- newman v6.2.1
- newman-reporter-htmlextra v1.23.1

## Documentação das APIs
- [Swagger - API ServeRest](https://serverest.dev/#/)
- [Random User Generator](https://randomuser.me/)

## Como rodar os testes

### Instalação e pré-requisitos
> Atenção: Para evitar erros de versionamento, as linhas de comando abaixo utilizaram as versões usadas nesse projeto

- Postman:
    - Usaremos a ferramenta `Postman` para fazer os testes, você pode usar a ferramenta pela web ou instalá-la no seu computador.

    - Para utilizar o Postman precisamos de um usuário, caso já possua cadastro, faça login e prossiga para o próximo passo, caso não possua, acesse o site oficial do [Postman] (https://www.postman.com/), clique no botão `Sign Up for Free` e siga o passo a passo do cadastro.

    - Para utilizar o `Postman Web` acesse o site oficial do Postman e efetue o login, a ferramenta já estará disponível para uso.

    - Para utilizar o `Postman Desktop` acesse o link de download do [Postman Desktop](https://www.postman.com/downloads/) baixe a versão para seu sitema operacional e siga o passo a passo do instalador. Abra o Postman Desktop e efetue login. Pronto! Postman Desktop estará disponível para você utilizar.

- Node.js:
    - Utilizamos o `Node` para instalar e rodar nosso gerador de relatório, o `newman`.
    - Acesse o [site de download oficial do Node](https://nodejs.org/pt/download) e baixe a versão LTS(versão mais estável) do node e siga os passos do instalador.

- Newman:
    - [Newman](https://www.npmjs.com/package/newman) é utilizado para rodar coleções de testes do postman em terminal.
    - Para instalar, abra um terminal (CMD/PowerShell) e execute o comando abaixo:
        ```bash
        npm install -g newman@6.2.1
    - A versão `6.2.1` do newman será instalado em seu computador e estará vísivel em todos os diretórios no terminal.

- Newman-reporter-htmlextra:
    - [Newman-reporter-htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra) utilizamos para gerar um relatório mais visual com uma página html interativa.
    - Para instalar, abra um terminal (CMD/PowerShell) e execute o comando abaixo:
        ```bash
        npm install -g newman-reporter-htmlextra@1.23.1
    - A versão `1.23.1` newman-reporter-htmlextra será instalado em seu computador e estará vísivel em todos os diretórios no terminal.

- Projeto
    - Precisamos dos arquvios do projeto para rodar nossos testes tanto no Postman quando no newman via terminal.
    - Clique no botão `<> Code`, no inicio da página, depois clique em `Download ZIP`, após baixar o projeto descompacte em um local/diretório de sua preferência.


- Testando
    - Clique em uma das opções abaixo para ler o passo a passo de cada tipo de teste:
        - [Testes com massa de dados](./with-mass-of-data/README_ptBR.md)
        - [Testes sem massa de dados](./without-mass-of-data/README_ptBR.md)