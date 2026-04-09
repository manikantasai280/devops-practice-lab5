pipeline {
    agent any

    environment {
        IMAGE_NAME = "helloworld-java"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/manikantasai280/devops-practice-lab5.git'
            }
        }

        stage('Compile Java') {
            steps {
                bat 'javac HelloWorld.java'
            }
        }

        stage('Run Java') {
            steps {
                bat 'java HelloWorld'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '''
                docker build -t %IMAGE_NAME%:%IMAGE_TAG% .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker run -d --name hello-container-%IMAGE_TAG% %IMAGE_NAME%:%IMAGE_TAG%
                '''
            }
        }

        stage('List Running Containers') {
            steps {
                bat 'docker ps'
            }
        }
    }
}