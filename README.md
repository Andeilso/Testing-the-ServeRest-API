# Testing API ServeRest with Postman
> [Versão do passo a passo em português](./README_ptBR.md)

This project consists of testing the ServeRest public API using Postman.

- For the mass of data version, a mass data file called "mass-of-data.csv" was used.
- For the version without data mass, an API called "Random User Generation" was used.

## Technologies used
- postman web version
- node - LTS version
- newman v6.2.1
- newman-reporter-htmlextra v1.23.1

## API Documentation
- [Swagger - API ServeRest](https://serverest.dev/#/)
- [Random User Generator](https://randomuser.me/)

## How to use

### Installation and prerequisites
> Attention: To avoid errors due to versions, the command lines below will be using the versions used in the project.

- Postman:
    - We will use the `Postman` tool to do the tests, you can use the tool via the web or install it on your computer.
    - To use Postman we need a user, if you already have a registration, log in and proceed to the next step, if not, access the official [Postman](https://www.postman.com/) website, click on the `Sign Up for Free` button and follow the registration step by step.
    - To use Postman Web, access the official Postman website and log in. The tool will now be available for use.
    - To use Postman Desktop, access the [Postman Desktop download link](https://www.postman.com/downloads/), download the version for your operating system, and follow the installation instructions. Open Postman Desktop and log in. That's it! Postman Desktop will be available for you to use.

- Node.js:
    - We use Node to install and run our report generator, `Newman`.
    - Access the [official Node download site](https://nodejs.org/pt/download) and download the LTS (most stable version) of Node and follow the installation steps.

- Newman:
    - [Newman](https://www.npmjs.com/package/newman) is used to run Postman test collections in the terminal.
    - To install, open a terminal (CMD/PowerShell) and run the command below:
        ```bash
        npm install -g newman@6.2.1
        ````
    - Version `6.2.1` of newman will be installed on your computer and will be visible in all directories in the terminal.

- Newman-reporter-htmlextra:
    - [Newman-reporter-htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra) is used to generate a more visual report with an interactive HTML page.
    - To install, open a terminal (CMD/PowerShell) and run the command below:
        ```bash
        npm install -g newman-reporter-htmlextra@1.23.1
        ```
    - Version `1.23.1` of newman-reporter-htmlextra will be installed on your computer and will be visible in all directories in the terminal.

- Project
    - We need the project files to run our tests in both Postman and Newman via the terminal.
    - Click the "<> Code" button at the top of the page, then click "Download ZIP." After downloading the project, unzip it to a location/directory of your choice.


- Testing
    - Click one of the options below to read the step-by-step instructions for each test:
        - [Test with mass of data](./with-mass-of-data/README.md)
        - [Test without mass of data](./without-mass-of-data/README.md)


<br>
<br>
<br>
<br>
<br>
<br>

Text translated on [Google Translate](https://translate.google.com/)