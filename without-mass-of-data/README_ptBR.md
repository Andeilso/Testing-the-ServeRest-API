# Teste da Api ServeRest without mass of data
## Teste no Postman
> Se já possuir um workspace pode pular a seção 'Novo workspace'.
- Novo workspace:
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

- Utilizando o Environment:
    - Do lado direito da tela no canto superior tem um campo que selecionamos nossa váriavel de ambiente, clique nele.
    - Selecione o environment chamado `serverest2`.
- Clique na pasta root `ServeRest2`.
- Na aba que abriu, no canto direito temos um campo chamado `> Run`, clique nele.
- Nessa nova aba chamada `Runner`:
    - Em `Choose how to run your collection`, selecione a opção `Run manually` para rodar manualmente nossa coleção de testes/requisições.
    - No campo `Run configuration` temos a quantidade de interações, você pode colocar quantas interações quiser. Ele irá repetir o teste no número de vezes que você passar.
    - Clique em `Run ServeRest` para rodar nossos testes.
- Pronto! Os testes iram rodar e o Postman mostrará o relatório de cada teste executado.

## Teste no newman
- Agora vamos rodar com o `newman` nossos testes.
- Abra uma novo terminal (CMD/Powershell) e navegue até a pasta do projeto `without-mass-of-data`, ou clique com o botão direito na pasta e clique em `abrir no terminal`. Se um terminal já está aberto é só navegar até a pasta.
- Execute o comando:
    ```bash
    newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli
    ```
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
