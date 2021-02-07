# Labs

The goal of this practical work is to learn the proper way of creating an IT project using **best practices**. This is important since the core of implementing DevOps to companies' processes is writing a clean and high-quality source code as well as documenting it.

As a programming language example, we will use JavaScript with its server-side runtime - [NodeJS](https://nodejs.org/en/), because it is one of the most popular languages for building different types of applications and it's very easy to get started with. You are not obliged to only use NodeJS for these labs, you are allowed to repeat similar steps using any other programming language of your choosing like Java, C++ or Python, but each of these steps will be different for the specific runtime.

## Objectives

1. Start a project
2. Initialize a NodeJS package
3. Create a NodeJS script
4. Create a web application using the ExpressJS package
5. Create a `CHANGELOG.md` file
6. Describe the project in a `README.md` file

In result, you will achieve creation a documented project on NodeJS of a simple web server displaying a "Hello world!" message on a home page.

## Before starting

1. Install an **IDE or a text editor**, for example, [Atom](https://atom.io/) or [VS Code](https://code.visualstudio.com/).
2. Install **Git**, use for installation:
  - Windows: https://gitforwindows.org/
  - Linux: https://git-scm.com/download/linux
  - MacOS: https://git-scm.com/download/mac   
3. Install **NodeJS**: https://nodejs.org/
4. Open a command line interface:
  - MacOS or Linux: use **Terminal**
  - Windows: use **Git Bash** (should be installed when installing Git). **Note!** Don't use default *CMD.exe*, because it has different commands from a command line of the Linux OS, which is used in most IT environments.

## 1. Start a project

**Note!** Don't put spaces (` `) in folder names or in file names. Otherwise, you will have to use escaping characters when navigating to them. Use the "kebab-case" naming convention by separating words with dashes (`-`).

1. Using **CLI bash commands** in your terminal (Terminal or Git Bash) navigate to the directory where you will store your project folder.

[Learn basic CLI bash commands](https://www.educative.io/blog/bash-shell-command-cheat-sheet)

Example:

```bash 
cd ~/path/to/your-root-project-directory
```

2. Choose a name for your project (for example, `ece-devops`) and create a directory:

```bash
mkdir ece-devops
```

Then navigate to this directory:

```bash
cd ece-devops
```

3. Initialize a [Git repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)

```bash
git init
```

## 2. Initialize a NodeJS package

1. Initialize a NodeJS package by running this command:

```bash
npm init -y
```
This will create an initial `package.json` file with the package (NodeJS project) description. Later, you can manually modify the content respecting the [JSON format](https://en.wikipedia.org/wiki/JSON). For example, these values:
  - `author`
  - `description`

[Read more about NodeJS packages and modules](https://docs.npmjs.com/about-packages-and-modules)

[Read more about `package.json` file](https://nodejs.org/en/knowledge/getting-started/npm/what-is-the-file-package-json/)

2. Run the NPM script:

```bash
npm run test
# or
npm test
```

It will run the bash script `echo \"Error: no test specified\" && exit 1` defined in the `package.json` file, then outputs the string `Error: no test specified` to stdout.

## 3. Create a NodeJS script 

Now, we start using a text editor or IDE of your choice (Atom, VS Code, WebStorm). 

1. Open a project folder in your editor.

You also can use bash commands to open it. From the project's root directory, run one of the commands:

```bash
# For Atom
atom .

# For VS Code
code .
```

2. Create a file `index.js` with the following content:

```js
str = "Hello NodeJS!"
console.log(str)
```

3. Run the NodeJS script in the terminal:

```bash
node index.js
```

It will print the message `Hello NodeJS!`.

4. Define this command as a NPM script. Modify the `package.json` file like this:

```json
...
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
...
```

5. Run the NPM scrip with the command:

```bash
npm run start
# or
npm start
```

It will do the same as in the step 2.

## 4. Create a web application using ExpressJS package

1. Install the [ExpressJS](https://www.npmjs.com/package/express) package:

```bash
npm install express
```

It will install the package files and its dependencies sourced on GitHub to you project directory inside the `node_modules` folder.

Also, this command will add a dependency to your `package.json` like:

```json
...
"dependencies": {
    "express": "^4.17.1"
  }
...  
```

It is a NodeJS (actually NPM) "feature" to let developers install all the necessary packages for the current project using just one single command, instead of installing each package repeating such a command like `npm install <PACKAGE_NAME>`. You can experiment it by removing the entire `node_modules` folder and running the `npm install` command.

2. Modify the `index.js` file with the following content:

```js
const express = require('express')

const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello world!')
})

module.exports = app.listen(port, (err) => {
  if (err) throw err
  console.log("Server listening the port " + port)
})
```

3. Run the NPM `start` script like in the previous step.

## 5. Create a `CHANGELOG.md` file

`CHANGELOG.md` is a file that describes the evolution of the project. All notable changes will be documented in this file. 

[Read more about CHANGELOG](https://keepachangelog.com/en/1.0.0/)

1. Create the `CHANGELOG.md` file under the root of your project with a content like:

```md
# Changelog

## Unreleased

### Added

- Create a HTTP web server using Express
- Initialize a project
```

Starting now, when working on the project you will be constantly updating it. 

## 6. Describe the project in a `README.md` file

You may take an inspiration what to write in a `README.md` file from any [Adaltas projects on GitHub](https://github.com/adaltas/), where the best practices for writing such a file are followed.

Also, you can refer to [this documentation](https://www.makeareadme.com/) to learn more.

1. Create a `README.md` file and describe the project with an information such as:
  
- Short description
- List of functionalities
- Installation instructions
- Usage instructions
- Author information
