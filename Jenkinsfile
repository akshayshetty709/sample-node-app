pipeline {
    agent { label "shetty" }

    parameters {
        string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'Docker Image Tag')
    }

    environment {
        DOCKER_IMAGE = "akshaykumarshetty/node-demo"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git url: "https://github.com/akshayshetty709/sample-node-app.git", branch: "main"
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
                    sh "docker login -u ${env.DockerhubUser} -p ${env.DockerhubPass}
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
