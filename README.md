# ECE DevOps course

Materials for the DevOps course for ECE students.

## Modules

1. Introduction to DevOps
2. Source Control Management (SCM) and supporting platforms
3. Infrastructure as Code (IaC)
4. Continuous testing
5. Continuous integration and delivery (CI/CD)
6. Containers with Docker
7. Container orchestration
8. Advanced Kubernetes
9. Cloud native architecture
10. DevOps in practice

## Project

// TODO: to complete

## Usage

Modules' materials are contained in the markdown files in the [content](content) folder.

Each module folder contains following:

- `index.md` file - description of the module
- `labs.md` file - content of labs
- `slides.md`file  - theory content
- `assets` folder - materials for the labs
- `image` folder - images used in the `.md` files

## Build slides

This project uses [Gatsby.js](https://www.gatsbyjs.org/) framework and requires [Node.js](https://nodejs.org/en/) installed. 

To build and run slides in your browser run the commands:

```
git clone https://github.com/adaltas/ece-devops-course.git
cd ece-devops-course
npm install
npm run serve
```

Then, open in a browser http://localhost:9000 (could be another port number).

## Author

Sergei Kudinov   
sergei@adaltas.com   
Developer and Data Engineer at [Adaltas](https://www.adaltas.com/)
