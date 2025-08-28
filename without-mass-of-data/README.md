# Testing the ServeRest API without mass data

## Testing in Postman
> If you already have a workspace, you can skip the 'New workspace' section.

- New workspace:
    - Open your preferred Postman (Web or Desktop).
    - Click the `Workspaces` tab.
    - Click the `Create Workspace` button.
    - Select the `Blank workspace` option and click next.
    - Create a name for your workspace.
    - Select the workspace type:
        - Internal (for you to create and test the API yourself) or 
        - Public (available to everyone).
    - Further down, under the `Manage access` option, select the `Only you and invited people` option.

- Importing the project:
    - After entering the workspace, on the left side, next to your workspace name, there are two buttons: `New` and `Import`. Click `Import` so we can use the test folder.
    - You can drag the test folder or click on `files`.
    - Drag or select the files within the project's `without-mass-of-data` folder, named `ServeRest2.postman_collection` and `serverest2.postman_environment`.
    - After selecting the files, click on `Import`.
    - Our API tests are now visible. In our workspace, we have the root folder called `ServeRest2` and its subfolders, which contain the requests and tests performed.

- Using the Environment:
    - On the top right of the screen, there's a field where we select our environment variable, click on it.
    - Select the environment called `serverest2`.

- Testing
    - Click on the root folder `ServeRest2`.
    - In the tab that opened, in the right corner, there's a field called `> Run`; click on it.
    - In this new tab called `Runner`:
        - Under `Choose how to run your collection`, select the `Run manually` option to manually run our collection of tests/requests.
        - In the `Run configuration` field, we have the number of interactions. You can enter as many interactions as you want. It will repeat the test as many times as you pass.
        - Click `Run ServeRest` to run our tests.
        - Done! The tests will run, and Postman will show the report for each test run.

## Test in Newman
- Now let's run our tests with `Newman`.
- Open a new terminal (CMD/Powershell) and navigate to the `without-mass-of-data` project folder, or right-click the folder and click `open in terminal`. If a terminal is already open, just navigate to the folder.
- Run the command:
    ```bash
    newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli
    ```
- Newman will run the tests and display a report at the end via the terminal.
- We can generate a more beautiful and interactive report with `newman-reporter-htmlextra`, run the command:
    ```bash
    newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli,htmlextra
    ```
    > Using only `newman run` with the `cli` and `htmlextra` report types may return a constant error stating that newman-reporter-htmlextra is not installed.
    - If the error persists, reinstall htmlextra locally in the terminal:
        ```
        npm install newman-reporter-htmlextra
        ```
    - Then run the command with npx to run htmlextra locally:
        ```
        npx newman run .\ServeRest2.postman_collection.json -e .\serverest2.postman_environment.json -r cli,htmlextra
        ```
- Done! The tests will run, and you will have both a report in the terminal and in interactive HTML.
- reporter-htmlextra creates a folder called `newman` and saves the report inside it.


<br>
<br>
<br>
<br>
<br>
<br>

Text translated on [Google Translate](https://translate.google.com/)