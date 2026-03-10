# DevOps Capstone Project – CI/CD Pipeline Implementation

## Project Overview

This project demonstrates the implementation of a complete **DevOps lifecycle** for a web application using modern DevOps tools and practices.

The objective is to automate the **build, test, and deployment process** using a CI/CD pipeline. The application is containerized using Docker and deployed through Jenkins pipeline jobs triggered by GitHub commits.

This project was implemented as part of a DevOps Capstone Project simulating a real-world scenario at **Abode Software**, where a Senior DevOps Engineer is responsible for implementing DevOps automation.

---

## Project Architecture

The DevOps pipeline integrates the following components:

* GitHub – Source code management
* Jenkins – CI/CD automation
* Docker – Application containerization
* Configuration Management Tool – Software installation and environment setup

The pipeline is triggered automatically when code changes are pushed to GitHub.

---

## Tools & Technologies Used

| Category                 | Tools        |
| ------------------------ | ------------ |
| Source Control           | GitHub       |
| CI/CD                    | Jenkins      |
| Containerization         | Docker       |
| Configuration Management | Ansible      |
| Programming              | HTML         |
| Base Image               | hshar/webapp |

---

## Git Workflow

Two primary branches are used:

### develop branch

* Developers push code here
* Jenkins pipeline triggers **Build + Test**
* Application is **NOT deployed to production**

### master branch

* Stable production-ready code
* Jenkins pipeline triggers **Build + Test + Production Deployment**

---

## CI/CD Pipeline Stages

The Jenkins pipeline is divided into three jobs:

### Job1 – Build

* Pulls the latest code from GitHub
* Builds the Docker image using the Dockerfile
* Uses base image `hshar/webapp`
* Copies application code to:

```
/var/www/html
```

---

### Job2 – Test

* Runs container to validate the application
* Ensures the website loads correctly

---

### Job3 – Production Deployment

* Triggered only for **master branch commits**
* Deploys the Docker container to production environment

---

## Docker Implementation

The application is containerized using Docker.

Key configuration:

Base Image:

```
hshar/webapp
```

Application directory:

```
/var/www/html
```

Docker image is automatically built whenever code is pushed to GitHub.

---

## Automation Workflow

1. Developer pushes code to GitHub
2. GitHub triggers Jenkins pipeline
3. Jenkins executes:

   * Build
   * Test
   * Deploy (only for master branch)
4. Docker container runs the application

---

## Repository Structure

```
devops-capstone-project
│
├── Capstone Project.ppt
├── Project Specifications
├── Dockerfile
├── Jenkinsfile
├── index.html
├── README.md

```

---

## Key DevOps Concepts Implemented

* CI/CD Pipeline Automation
* Infrastructure Automation
* Git Branching Strategy
* Docker Containerization
* Automated Build & Deployment

---

## Learning Outcome

This project demonstrates practical knowledge of:

* Continuous Integration
* Continuous Deployment
* Jenkins Pipeline automation
* Docker containerization
* Git workflow management

---

## Author

Akshatha Gowda
DevOps & Cloud Enthusiast
