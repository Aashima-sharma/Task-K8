pipeline{
    agent any
    environment {
        DOCKER_IMAGE = 'pyapp'  
        BUILD_NUMBER = "${env.BUILD_NUMBER}" 
    }
    stages{
        stage('Clone repository') {
             steps {
                 git 'https://github.com/Manisha148/Task-K8.git'
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