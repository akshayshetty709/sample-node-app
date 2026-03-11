pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git url: "https://github.com/akshayshetty709/django-notes-app.git", branch:"main"
            }
        }

        stage('Installing Dependencies') {
            steps {
                sh "npm install"
            }
        }

        stage('Building Docker Image') {
            steps {
                sh "docker build -t node-app:latest ."
            }
        }

        stage('Running Container') {
            steps {
                sh "docker run -d -p 3000:3000 --name node-app node-app:latest"
            }
        }

    }
}
