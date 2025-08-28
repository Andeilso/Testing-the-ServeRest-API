# Testing the ServeRest API with Mass Data

## Testing in Postman
> If you already have a workspace, you can skip the 'New Workspace' section.

- New Workspace:
    - Click the `Workspaces` tab.
    - Open your preferred Postman (Web or Desktop).
    - Click the `Create Workspace` button.
    - Select the `Blank Workspace` option and click next.
    - Create a name for your workspace.
    - Select the workspace type:
        - Internal (for you to create and test the API yourself) or
        - Public (available to everyone).
    - Further down, under the `Manage Access` option, select the `Only you and invited people` option.

- Importing the project:
    - After entering the workspace, on the left side, next to your workspace name, there are two buttons: `New` and `Import`. Click `Import` so we can use the test folder.
    - You can drag the test folder or click on `files`.
    - Drag or select the files within the project's `with-mass-of-data` folder, named `ServeRest.postman_collection` and `serverest.postman_environment`.
    - After selecting the files, click `Import`.
    - Our API tests are now visible. In our workspace, we have the root folder called `ServeRest` and its subfolders, which contain the requests and tests performed.

- Using the Environment:
    - On the top right of the screen, there's a field labeled `No environment`; click it.
    - Select the environment called `serverest`.

- Running tests with the test mass:
    - Click on the root folder `ServeRest`.
    - In the tab that opened, in the right corner, there's a field labeled `> Run`, click it.
    - In this new tab called `Runner`:
        - Under `Choose how to run your collection`, select the `Run manually` option to manually run our collection of tests/requests.
        - Further down under `Test data file`, click `Select File` to select our test mass file.
        - Click `Select from computer`.
        - Inside the `with-mass-of-data` folder, select the `mass-of-data.csv` file.
        - A preview screen of our test mass will appear.
        - Click the `Use locally` button.
    - Now in `Run configuration`, we have the number of interactions. Our test mass file has 7 items to be used, so the interaction becomes 7 as well. You can change it to have fewer interactions.
    - Click `Run ServeRest` to run our tests with the test mass.
- Done! The tests will run, and Postman will show the report for each test run.

## Test in Newman
- Now let's run our tests with `newman`.
- Open a new terminal (CMD/Powershell) and navigate to the `with-mass-of-data` project folder, or right-click the folder and click `open in terminal`.
- Run the command:
    ```bash
    newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli
    ```
- Newman will run the tests and display a report at the end via the terminal.
- We can generate a more beautiful and interactive report with `newman-reporter-htmlextra`, run the command:
    ```bash
    newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli,htmlextra
    ```
    > Using only `newman run` with the `cli` and `htmlextra` report types may return a constant error that newman-reporter-htmlextra is not installed.
    - If the error persists, reinstall htmlextra locally in the terminal:
        ```
        npm install newman-reporter-htmlextra
        ```
    - Then run the command with npx to run htmlextra locally:
        ```
        npx newman run .\ServeRest.postman_collection.json -e .\serverest.postman_environment.json -d .\mass-of-data.csv -r cli,htmlextra
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