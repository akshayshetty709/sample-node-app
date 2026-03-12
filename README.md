Node.js CI/CD Pipeline with Jenkins

Project Overview

This project demonstrates a simple CI/CD pipeline using GitHub, Jenkins, and Docker to build and deploy a Node.js application.

Whenever code is pushed to the GitHub repository, Jenkins automatically triggers a pipeline to build a Docker image and deploy the application.

---

Technologies Used

- Node.js
- Express.js
- Jenkins
- Docker
- GitHub

---

Project Structure

node-jenkins-app
│
├── app.js
├── package.json
├── Dockerfile
├── Jenkinsfile
└── README.md

---

Application Description

This is a simple Node.js web application built using Express.js.
The application runs on port 3000 and displays a welcome message.

---

CI/CD Pipeline Workflow

1. Developer pushes code to GitHub repository
2. Jenkins pipeline is triggered
3. Jenkins clones the repository
4. Docker image is built
5. Docker container is started
6. Application is deployed and accessible through browser

Pipeline Flow:

Developer → GitHub → Jenkins → Docker Build → Deploy Container

---

Prerequisites

The following tools must be installed:

- Git
- Node.js
- Docker
- Jenkins

---

Running the Application Locally

Install Dependencies

npm install

Start the Application

node app.js

Open in browser:

http://localhost:3000

---

Docker Commands

Build Docker Image

docker build -t node-jenkins-app .

Run Docker Container

docker run -d -p 3000:3000 node-jenkins-app

Access application:

http://<server-ip>:3000

---

Jenkins Pipeline

The Jenkins pipeline is defined inside the "Jenkinsfile".
It automates the following stages:

- Clone Source Code
- Install Dependencies
- Build Docker Image
- Run Docker Container

---

Author

Akshay Shetty

---

Conclusion

This project demonstrates a basic DevOps workflow by integrating GitHub, Jenkins, and Docker to automate application build and deployment.
