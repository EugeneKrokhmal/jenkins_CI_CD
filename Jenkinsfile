pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-node-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/EugeneKrokhmal/jenkins_CI_CD.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop $IMAGE_NAME || true'
                sh 'docker rm $IMAGE_NAME || true'
                sh 'docker run -d -p 3000:3000 --name $IMAGE_NAME $IMAGE_NAME'
            }
        }
    }
}
