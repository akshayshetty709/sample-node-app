pipeline {
    agent any

    parameters {
        string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'Docker Image Tag')
    }

    environment {
        DOCKER_IMAGE = "yourdockerhubusername/node-demo"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/yourusername/nodejs-demo-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $DOCKER_IMAGE:${params.IMAGE_TAG} ."
            }
        }

        stage('Push to DockerHub') {
            steps {
                    withCredentials([usernamePassword(
                    'credentialsId':"Dockerhubcred",
                    passwordVariable:"DockerhubPass",
                    usernameVariable:"DockerhubUser")]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh "docker push $DOCKER_IMAGE:${params.IMAGE_TAG}"
                }
            }
        }

        stage('Run Container') {
            steps {
                sh "docker run -d -p 3000:3000 $DOCKER_IMAGE:${params.IMAGE_TAG}"
            }
        }
    }
}
