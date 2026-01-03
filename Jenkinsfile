pipeline {
    agent any

    environment {
        IMAGE_NAME = "jallisivasri703/jenkins-autodeploy"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/jallisivasri/jenkins-docker-autodeploy.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker stop auto-app || true
                  docker rm auto-app || true
                  docker run -d --name auto-app -p 3000:3000 $IMAGE_NAME
                '''
            }
        }
    }
}
