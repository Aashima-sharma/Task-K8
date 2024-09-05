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
                git branch: 'main', url: 'https://github.com/your-repo/your-project.git'
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
    }
}
