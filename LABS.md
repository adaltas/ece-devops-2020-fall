# Labs

## Module 1: Introduction

1. Live coding - Create an application on NodeJS (“Hello world“ ExpressJS)
2. Connect to Redis

**Achieved results:**

Creating a well structured and documented project.

**Comments:**

1. In the next labs this project will be upgraded to a simple UserAPI application with CRUD user operations, little API and Redis storage
2. I made my choice to include Redis for following reasons:
    - It will be useful to represent in practice different types of tests (unit, API, integration) and Container Orchestration with 2 containers
    - It is super easy to learn and apply (3 lines of code + understand redis-cli)

## Module 2: Source control and supporting platforms

1. Manipulate a git repo with the existing project (create repo on GitLab or GitHub, branches, tags, merging, rebase and so on)
3. Manage a project in GitLab (issues, boards)

**Achieved results:**

Advanced Git usage and project management with GitLab.

## Module 3: Infrastructure as code

1. Create VM with Vagrant
2. Provision with Ansible

**Achieved results:**

Automating infrastructure deployment.

**Comments:**

I propose 2 options for the step 2:
  - Install NodeJs and Redis (and run the UserAPI app)
  - Or GitLab installation

## Module 4: Continuous testing

1. Install Linter
2. Using TDD method create:
  - Create unit tests of the CRUD user operations
  - Create integration tests with Redis
  - Create API tests

**Achieved results:**

Applying continuous testing methods to a real project.

## Module 5: Continuous integration and delivery

1. CI part: using GitLab (it is free and Redis service is available)
2. CD part: integrate Gitlab with Heroku (also free, and there is a Redis service on Heroku side)

**Achieved results:**

Creating a CI/CD pipeline integrating different platforms.

## Module 6: Containers with Docker

1. Run any Linux container
2. Run a Redis container
3. Build docker image out of the UserAPI app and run it
4. Push the UserAPI app image to Docker Hub

**Achieved results:**

Using containers and containerisation of a real application.

## Module 7: Container orchestration

1. Run the UserAPI app with Docker Compose
2. Install Minikube cluster
3. Explore Kubernetes basics

**Achieved results:**

Orchestration containers with Docket Compose and Kubernetes

## Module 8: Advanced Kubernetes

1. Run the UserAPI app on Kubernetes (backend + database)
2. Advanced Kubernetes tasks (like Ingress, Monitoring)

**Achieved results:**

Using Kubernetes and running a real application on it.

## Module 9: Cloud native architecture

// TODO: complete the section

**Comments:**

I was thinking about service mesh with Istio (to show a canary deployment and load balancing). What are your proposals?

## Module 10: DevOps in practice

1. Applying best practices (project structure, documenting, testing)
2. Work on project

**Achieved results:**

Review of the labs and projects, answering questions.
