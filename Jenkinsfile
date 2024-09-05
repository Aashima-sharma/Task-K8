pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'pyapp'  
        BUILD_NUMBER = "${env.BUILD_NUMBER}" 
    }

    stages {
        stage('Clone repository') {
            steps {
                // Clone the repository from Git
                git branch: 'main', url: 'https://github.com/Aashima-sharma/Task-K8.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh "docker build -t ${DOCKER_IMAGE}:${BUILD_NUMBER} ."
                }
            }
        }
        stage('push image') {
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_USERNAME} --password-stdin"
                        def dockerImageTag = "${DOCKER_IMAGE}:${env.BUILD_NUMBER}"
                        sh "docker push ${dockerImageTag}"
                }
            }
        }
    }
}
