# Testing API ServeRest with Postman

Testing the ServerRest API using Postman.

- For the version with mass of data, a mass data file called "mass-of-data.csv" was used.
- For the version without mass of data, an API called "Random User Generation" was used.

## Technologies used
- postman web version
- node - LTS version
- newman v6.2.1
- newman-reporter-htmlextra v1.23.1

## Documentation
- API Document: [Swagger - API ServeRest](https://serverest.dev/#/)
- User Generator API Doc: [Random User Generator](https://randomuser.me/)

## How to use

### Instalação de pré requisitos
> Attention: To avoid errors due to versions, the command lines below will be using the versions used in the project.

- Postman:
    - Utilizaremos a ferramenta `Postman` para fazer os teste, você pode usar a ferramenta pela web ou instalar em seu computador.
    - Para utilizar o Postman precisamos de um usuário, se você já possui um cadastro faça login e siga para próxima etapa, se não, acesse o site oficial do [Postman](https://www.postman.com/), clique no botão `Sign Up for Free` e siga o passo a passo de cadastro.
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


### Teste da Api ServeRest with mass of data
- Teste no Postman
    - Novo Workspace:
        - Abra o Postman de sua preferência (Web ou Desktop).
        - Clique na aba `Workspaces`.
        - Clique no botão `Create Workspace`.
        - Selecione a opão `Blank workspace` e clique em next.
        - Crie um nome para seu workspace.
        - Selecione o tipo do worksapce se ele será interno(para você criar e testar a API sozinho) ou Public(Estará disponível para todos).
        - Mais abaixo na opção `Manage acess` selecione a opção `Only you and invited people`.

    - Importando o projeto:
        - Após entrar no workspace, do lado esquerdo perto do nome da sua workspace temos dois botões `New` e `Import`, clique em `Import` para que possamos utilizar a pasta dos testes.
        - Você pode arrastar a pasta de testes ou clicar em `files`.
        - Arraste ou selecione os arquivos dentro da pasta `with-mass-of-data`, do projeto, que possuem o nome `ServeRest.postman_collection` e `serverest.postman_environment`.
        - Após a seleção de arquivos clique em `Import`.
        - Nossos testes da api estão visíveis agora, na nossa workspace temos a pasta root chamada `ServeRest` e suas subpastas, que contém as requisições e os testes feitos.

    - Rodando os testes com massa de teste:
        - Environment:
            - Do lado direito da tela no canto superior tem um campo de escrito `No environment`, clique nele.
            - Selecione o environment chamado `serverest`.
        - Clique na pasta root `ServeRest`.
        - Na aba que abriu, no canto direito temos um campo chamado `> Run`, clique nele.
        - Nessa nova aba chamada `Runner`:
            - Em `Choose how to run your collection`, selecione a opção `Run manually` para rodar manualmente nossa coleção de testes/requisições.
            - Mais abaixo em `Teste data file` clique em `Select File` para selecionar nosso arquivo de massa de testes.
                - Clique em `Select from computer`.
                - Dentro da pasta `with-mass-of-data`, selecione o arquivo `mass-of-data.csv`.
                - Vai aparecer uma tela de preview das nossas massas de teste.
                - Clique no botão `Use locally`
            - Agora em `Run configuration` temos a quantidade de interações, nosso arquivo de massa de teste possui 7 items para ser usado, logo a interação se torna 7 também. Você pode alterar para que faça menos interações.
            - Clique em `Run ServeRest` para rodar nossos testes com a massa de teste.
        - Pronto! Os testes iram rodar e o Postman mostrará o relatório de cada teste executado.

- Teste no newman
    - Agora vamos rodar com o `newman` nossos testes.
    - Abra uma novo terminal (CMD/Powershell) e navegue até a pasta do projeto `with-mass-of-data`, ou clique com o botão direito na pasta e clique em `abrir no terminal`
    - Execute o comando:
        ```bash
        newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli
    - O newman irá rodar os teste e mostrar um relatório no final via terminal.
    - Podemos gerar um relatório mais bonito e interativo com o `newman-reporter-htmlextra`, execulte o comando:
        ```bash
        newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli,htmlextra
        ```
        > Utilizar apenas `newman run` com os tipos de ralatório `cli` e `htmlextra`, pode retornar um erro constante de que o newman-reporter-htmlextra não está instalado.
        - Se o erro persistir instale novammente o htmlextra localmente no terminal:
            ```
            npm install newman-reporter-htmlextra
            ```
        - Depois rode o comando com npx para rodar o htmlextra localmente:
            ```
            npx newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli,htmlextra
            ```
    - Pronto! Os testes irão rodar e você terá tanto um relatório no terminal quanto em html interativo.
    - O reporter-htmlextra cria uma pasta chamada `newman` e salva o relatório dentro dela.

### Teste da Api ServeRest without mass of data
- Teste no Postman
    - Se já possuir um workspace pode pular essa parte.
    - Novo Workspace:
        - Abra o Postman de sua preferência (Web ou Desktop).
        - Clique na aba `Workspaces`.
        - Clique no botão `Create Workspace`.
        - Selecione a opão `Blank workspace` e clique em next.
        - Crie um nome para seu workspace.
        - Selecione o tipo do worksapce se ele será interno(para você criar e testar a API sozinho) ou Public(Estará disponível para todos).
        - Mais abaixo na opção `Manage acess` selecione a opção `Only you and invited people`.

    - Importando o projeto:
        - Após entrar no workspace, do lado esquerdo perto do nome da sua workspace temos dois botões `New` e `Import`, clique em `Import` para que possamos utilizar a pasta dos testes.
        - Você pode arrastar a pasta de testes ou clicar em `files`.
        - Arraste ou selecione os arquivos dentro da pasta `without-mass-of-data`, do projeto, que possuem o nome `ServeRest2.postman_collection` e `serverest2.postman_environment`.
        - Após a seleção de arquivos clique em `Import`.
        - Nossos testes da api estão visíveis agora, na nossa workspace temos a pasta root chamada `ServeRest2` e suas subpastas, que contém as requisições e os testes feitos.

    - Rodando os testes com massa de teste:
        - Environment:
            - Do lado direito da tela no canto superior tem um campo que selecionamos nossa váriavel de ambiente, clique nele.
            - Selecione o environment chamado `serverest2`.
        - Clique na pasta root `ServeRest2`.
        - Na aba que abriu, no canto direito temos um campo chamado `> Run`, clique nele.
        - Nessa nova aba chamada `Runner`:
            - Em `Choose how to run your collection`, selecione a opção `Run manually` para rodar manualmente nossa coleção de testes/requisições.
            - No campo `Run configuration` temos a quantidade de interações, você pode colocar quantas interações quiser. Ele irá repetir o teste no número de vezes que você passar.
            - Clique em `Run ServeRest` para rodar nossos testes.
        - Pronto! Os testes iram rodar e o Postman mostrará o relatório de cada teste executado.

- Teste no newman
    - Agora vamos rodar com o `newman` nossos testes.
    - Abra uma novo terminal (CMD/Powershell) e navegue até a pasta do projeto `without-mass-of-data`, ou clique com o botão direito na pasta e clique em `abrir no terminal`. Se um terminal já está aberto é só navegar até a pasta.
    - Execute o comando:
        ```bash
        newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli
    - O newman irá rodar os teste e mostrar um relatório no final via terminal.
    - Podemos gerar um relatório mais bonito e interativo com o `newman-reporter-htmlextra`, execulte o comando:
        ```bash
        newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli,htmlextra
        ```
        > Utilizar apenas `newman run` com os tipos de ralatório `cli` e `htmlextra`, pode retornar um erro constante de que o newman-reporter-htmlextra não está instalado.
        - Se o erro persistir instale novammente o htmlextra localmente no terminal:
            ```
            npm install newman-reporter-htmlextra
            ```
        - Depois rode o comando com npx para rodar o htmlextra localmente:
            ```
            npx newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli,htmlextra
            ```
    - Pronto! Os testes irão rodar e você terá tanto um relatório no terminal quanto em html interativo.
    - O reporter-htmlextra cria uma pasta chamada `newman` e salva o relatório dentro dela.

