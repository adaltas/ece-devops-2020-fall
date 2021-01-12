# Project

## Deadline

The deadline was extended from 20 to 23 of December.

**December 23, 2020**

## Opportunities

1. The DevOps project is based on all the labs passed during the course, it is allowed to use them.

2. Work on the project can be carried out by 1 student or a team of 2 or a **maximum of 3 students**.

3. You are allowed to collaborate with students from another group.

## Instructions

### 1. Create a web application

Create a web application on any programming language (NodeJS, Java, Ruby, Python etc.), storing data in a database (Redis, MonogoDB, MySQL, ...) and cover it with tests of different levels.

**Are proposed:**

- a little user API application with [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) user functionality
- storage in Redis database
- tests: unit, API, configuration, connection.

**Note!** You are allowed to use the draft application located in the [assets/userapi](modules/4-continuous-testing/assets/userapi) folder, but you have to enrich it by at least completing all comment sections marked "TODO".

### 2. Apply CI/CD pipeline 

Configure and apply CI/CD (including deployment) pipeline using any platforms (GitLab CI/CD, Jenkins, Travis CI, Netlify, Heroku etc.).

**Note!** If the chosen deployment platform (like Heroku) requires any subscription to make use their database service to connect to your app, then you can skip usage this service. In this case you application won't be running properly, but it must successfully display the homepage. 

### 3. Configure and provision a virtual environment and run your application using IaC approach

1. Configure with Vagrant: 1 VM running on any Linux distribution 
2. Provision the VM with Ansible, that includes installing and running:
  - language runtime
  - database
  - your application (use [sync folders](https://www.vagrantup.com/docs/synced-folders))
  - health check of your application

### 4. Build Docker image of your application

1. Create Docker image of your application
2. Push the image to Docker Hub

**Note!** You must [ignore](https://docs.docker.com/engine/reference/builder/#dockerignore-file) all the files and folders that do not need to be included in the image.

### 5. Make container orchestration using Docker Compose

1. Create `docker-compose.yml` file that will start your application

### 6. Make docker orchestration using Kubernetes

1. Install Kubernetes cluster using Minikube
2. Create Kubernetes Manifest yaml files:
  - deployments
  - services
  - persistent volume and persistent volume claim

### 7. Make a service mesh using Istio

1. Deploy your application using Istio
2. Create configuration:
  - route requests between 2 different versions of your app
  - traffic shifting between 2 different versions of your app

### 8. Describe your project in the `README.md` file

1. List of all the work performed (briefly, describing features and bonus tasks).

2. Instructions:
  - Installation
  - Usage
  - Testing
  
4. All the necessary links with the platforms and tools integrated:
  - Travis CI
  - Heroku
  - Docker Hub
  - ...
  
4. Author

5. Other additional info that you want to include

**Note!** Use correct Markdown syntax to keep your readme file looking good.

## Structure

Here is an example structure of your project repository:

```
src/
test/
conf/
iac/
  Vagrantfile
  playbooks/
k8s/
istio/
README.md
CHANGELOG.md
Dockerfile
.travis.yml
<Other configuration files like: package.json>
...
```

## How to get bonuses?

Every initiative will be counted. 

List of bonus tasks proposed:

1. Use different tools and platforms instead of what has been passed in the labs, for example: GitLab CI/CD, Netlify, etc.
2. Use different language (Java, Ruby, Python etc.) to develop the application
3. If you use the NodeJS application provided in [assets](assets) folder, bring it with additional features:
  - more different API methods
  - more different unit/functional/integration tests
  - using another database (like MongoDB, MySQL, ...)
  - integrate to your source code a documenting package, for example, [Swagger UI](https://www.npmjs.com/package/express-swagger-generator)
4. Any number Kubernetes tasks from [this list](https://kubernetes.io/docs/tasks/). 
5. [Securing microservice communication](https://istio.io/latest/docs/tasks/security/) or with Istio 
6. Etc. 

## How to send a project for evaluation?

**ATTENTION!** Make sure your repository is **PRIVATE** and **you have sent an invitation** to GitHub account - https://github.com/sergkudinov. Otherwise, **if it isn't PRIVATE the final grade will be reduced to 0**.

After you have sent the invitation, send an email to [sergei@adaltas.com](mailto:sergei@adaltas.com) containing following:

  - **Subject format:** "ECE - DevOps project - \<LASTNAME Firstname\> - \<Group number (ex: SI03)\>"
  - **Message:**
    - **The link to the repository** on GitHub/GitLab
    - List of authors and **the group number**

## Grading system

| Subject                                                         |   Code    | Max. grade|
|:----------------------------------------------------------------|:---------:|:---------:|
| Enriched web application with automated tests                   |   APP     |    +1     |
| Continuous Integration and Continuous Delivery (and Deployment) |   CICD    |    +3     |
| Containerisation with Docker                                    |   D       |    +1     |
| Orchestration with Docker Compose                               |   DC      |    +2     |
| Orchestration with Kubernetes	                                  |   KUB     |    +4     |
| Service mesh using Istio                                        |   IST     |    +2     |
| Infrastructure as code using Ansible                            |   IAC     |    +4     |
| Accurate project documentation in README.md file                |   DOC     |    +3     |
| Each bonus tasks                                                |   BNS     |    +1     |
| Each penalty                                                    |   PNL     |    -1     |

It is also taken into account:

- richness of the commit history
- accuracy and purity of the project (descriptions, source code, files)
- activity in during course sessions
