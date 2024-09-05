pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'aashima3613/pyapp'
        // BUILD_NUMBER is automatically available as env.BUILD_NUMBER
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
                    def dockerImageTag = "${DOCKER_IMAGE}:${env.BUILD_NUMBER}"
                    sh "docker build -t ${dockerImageTag} ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Authenticate with Docker Hub
                    withDockerRegistry([ credentialsId: "dockerid", url: "https://index.docker.io/v1/" ]) {
                        // Push the Docker image
                        def dockerImageTag = "${DOCKER_IMAGE}:${env.BUILD_NUMBER}"
                        sh "docker push ${dockerImageTag}"
                    }
                }
            }
        }
    }
}
