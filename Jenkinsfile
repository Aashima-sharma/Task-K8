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
                    sh "docker login -u ${DOCKER_USERNAME} -P ${DOCKER_PASSWORD}"
                    sh "docker push aashima3613/pyapp"
                }
            }
        }
    }
}
