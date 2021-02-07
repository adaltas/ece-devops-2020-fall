# Labs

Continuous Integration & Continuous Delivery (Deployment) (CI/CD)

## Before starting

It is required to have an example application with automated tests. It is suggested to use the application on NodeJS created in the module 4 "Continuous testing". 

1. To use the example application, copy the `modules/4-continuous-testing/assets/userapi` folder to any place on your computer.

2. Initialize a new Git repository containing all the source files of the example project and push it to a new remote repository on GitHub.

## 1. CI part - using Travis CI

1. Go to [travis-ci.com](https://travis-ci.com/) and sign up with a GitHub account

2. Sync your GitHub account with Travis CI account

3. Create `.travis.yml` configuration file under the root of your project repo:

```yaml
language: node_js
node_js:
- '12'
- '14'
services:
- redis-server
script:
- echo 'Starting'
- npm install
- echo 'Testing'
- npm test
```

And push it to the remote master.

5. Practice a regular workflow of the software development life cycle. Create a pull request to `master` branch:

- create a new branch and publish it to your remote GitHub repository
- make any change in you source code, commit and push it
- make a **Pull Request** on GitHub
- wait for Travis CI to test it (observe the process on Travis CI)
- review the commit and Merge this Pull Request into `master` branch

6. Check the Travis CI build log.

## 2. CD part - using Heroku

1. Create an account on [Heroku](https://heroku.com)

2. Create an app on [Heroku](https://dashboard.heroku.com/new-app) and configure it

Under the "Deploy tab":

  - sync the app with the GitHub repository
  - enable option "Automatic deploys / Wait for CI to pass before deploy"

3. Add Redis service to Heroku deployment - https://elements.heroku.com/addons/heroku-redis

**Note!** Redis service on Heroku is free, but it requires adding credit card information. Considering this limitation we will not run Redis on Heroku, and the application will be partially non-functional (it will print the "Hello world!" message on the home page, but the user API will not work). However, it will be enough to experience our CI/CD pipeline.

4. Configure `.travis.yml` with Heroku

**Install CLIs:**

  - [`travis`](https://github.com/travis-ci/travis.rb#installation)
  - [`heroku`](https://devcenter.heroku.com/articles/heroku-cli)

**Configuration:**

Link to configuration instruction - [Heroku Deployment](https://docs.travis-ci.com/user/deployment/heroku/)

You can use this command:

```
travis setup heroku
```

After that in the `.travis.yml` will be appended something like:

```yaml
deploy:
  provider: heroku
  api_key:
    secure: N2vEDW5kJSmMYsxdfgfdQLJCxoNoGZFmpMM4Hpc6Rf1FdsHqtbgXgmX6gbu48mo1ZIF0FFDJEDG4lES2FbFcjxfNpvH7r9zpuTffHe8p3Cbq5Y5C+X5m0fCWUoQGPgL/qczoN/Xla/J0U8DN14cX2+f9OSWmjAcTFzogG6AEm4XOHCzhY7tSYbGP65N40SWxKIcMQ48wKGifeeQSB2vbm4Lu9SKHiLFo1VyQN3o5Ziu+f9NoByIcKtyEnjAfyWdZ8uAea1ZXH/HqivpFCAgPIoaw5qJcRcCIlj84qteLbdtbYCWB2MMyWZ0XQ0TCrI8TUNefqbM+AaS3OgAb+z/CAHPVgfJuEt6vfq9asH6aVDhTIva/whjS2S4JXeZUNNkBdp3IEeYKwpu6uNXAqjZ05132Gq/RiRAeqOXcWj+FgCZ2F/EjmXiP3Vpm8k5/cPOt+7ilrXc27XF3HoHs+AKFaMc75aa+0Rx2GSAw1+WSyBrFTLFKqBG0QzGsiBjUyrc+9bEj9NEte/mbYLJuna2D+JzwXaZdv3s3Cjpnz0xxQaDgt8xeuFz/StzB/6DZfgpBWIvIMzW6hTERTtuToxS8BjhnIvfoGC2eiI2jM0keZrzf/eTyizwfjxEXhFOamnGmmQx903jXlTmPZ8rTyUFhJr68T9i3MlDp6M4EwLsqzExUUiGo=
  app: ece-userapi
  on:
    repo: sergkudinov/ece-userapi
```

And push it to the remote master.

**Note!**

If you have an error like *"Message: Invalid credentials provided."* in your Travis CI log, [read this](https://stackoverflow.com/questions/51925918/issues-with-deploying-to-heroku-via-travis-ci?answertab=votes#tab-top).

5. Create a pull request to the master branch to test your CI/CD pipeline.

6. Test your public domain on Heroku.
