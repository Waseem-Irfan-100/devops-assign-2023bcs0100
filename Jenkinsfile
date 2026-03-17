pipeline {
    agent any

    environment {
        IMAGE_NAME = "2023bcs0100syedwaseemirfan/2023bcs0100_45"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Waseem-Irfan-100/devops-assign-2023bcs0100.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }
    }
}
