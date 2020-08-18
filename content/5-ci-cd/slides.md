# Continuous Integration & Continuous Delivery (CI/CD)

## Continuous Integration (CI)

This is a software development practice in which members of a team integrate their work frequently, at least daily, leading to multiple integrations per day.

## Continuous Delivery (CD)

This is a software development discipline where software is built in a manner that allows for deploying to customers at any time.

##  Continuous Deployment

This extends Continuous Delivery by automating the deployment process so that code is automatically deployed to production after it passes automated testing.

## What is the CI/CD Pipeline?

**CI/CD pipeline** - an automated sequence of events that is initiated after you update the code.

These events take care of the work that you would otherwise need to perform manually:
- previewing your in-development site
- testing your new code
- deploying it to your production server

# CI/CD with Travis CI and deployment platforms

[Travis CI Tutorial](https://docs.travis-ci.com/user/tutorial/)

## CD using Heroku

[Heroku Deployment](https://docs.travis-ci.com/user/deployment/heroku/)

[Automatically deploy with Travis CI and Heroku (article)](https://medium.com/@felipeluizsoares/automatically-deploy-with-travis-ci-and-heroku-ddba1361647f)

## CD using Netlify

[Netlify Drop](https://app.netlify.com/drop)

[Netlify Drop Deployment](https://docs.travis-ci.com/user/deployment-v2/providers/netlify/)

# The CI/CD Pipeline Sequence

The flow of events:

1. You create a new branch in your local Git repository and make code changes to your Gatsby project.

2. You push your branch to your GitHub repository and create a pull request.

3. Netlify automatically creates a preview of the site with a unique URL that can be shared.

4. Travis CI automatically builds the site in an isolated container and runs any declared tests.

5. When all tests pass, you merge the PR into the repository’s master branch, which automatically triggers a deployment to your production.
