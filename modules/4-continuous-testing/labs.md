# Labs

Continuous testing

## Objectives

1. Use prepared User API application and run tests
2. Using test-driven development (TDD) create GET user method

## Before starting

1. Install Redis database

Installation instructions:

- **Windows:** https://redislabs.com/ebook/appendix-a/a-3-installing-on-windows/a-3-2-installing-redis-on-window/
- **MacOS:** `brew install redis` or https://redis.io/topics/quickstart
- **Linux or MacOS:** https://redis.io/topics/quickstart

After installation start Redis server:

- **Windows:** double click on `redis-server.exe` file (keep it open)
- **MacOS and Linux:** `redis-server`

Test if the Redis server is running:

- **Windows:** double click on `redis-cli.exe` and run the `ping` command inside this terminal
- **MacOS and Linux:** run in a new terminal window `redis-cli ping` (should answer with "PONG")

2. Install an **IDE or a text editor**, for example, [Atom](https://atom.io/) or [VS Code](https://code.visualstudio.com/)

3. Install **NodeJS**: https://nodejs.org/

## 1. Use prepared User API application and run tests

Go to `assets/userapi` folder and explore the project:

```
cd modules/4-continuous-testing/assets/userapi
```

Install application:

```
npm install
```

Run tests:

```
npm test
```

Start application:

```
npm start
```

## 2. Using test-driven development (TDD) create GET user functionality

Create a REST API GET `user` method that retrieves user information from the database.

**Hint!** The source code of the example application in the folder `modules/4-continuous-testing/assets/userapi` contains `TODO` comments in the places where you are supposed to make modifications to accomplish these steps.

1. Create `get` user controller:
  - Create **2 unit tests** (in the file `modules/4-continuous-testing/assets/userapi/test/user.controller.js`):
    - successfully get user
    - cannot get user when it does not exist
  - Create **the controller method** (in the file `modules/4-continuous-testing/assets/userapi/src/controllers/user.js`)

2. Create GET user REST API method:
  - Create **2 API tests** (in the file `modules/4-continuous-testing/assets/userapi/test/user.router.js`):
    - successfully get user
    - cannot get user when it does not exist
  - Create **GET user route** (in the file `modules/4-continuous-testing/assets/userapi/src/routes/user.js`)

## Bonus tasks

1. Integrate Swagger UI using this package - https://www.npmjs.com/package/express-swagger-generator
