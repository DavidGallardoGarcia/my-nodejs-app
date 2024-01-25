pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'my-node-app' // Change this to your desired Docker image name
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your version control system
                checkout scm
            }
        }

        // stage('Build Docker Image') {
        //     steps {
        //         // Build Docker image using the provided Dockerfile
        //         script {
        //             sh "docker build -t ${DOCKER_IMAGE} ."
        //         }
        //     }
        // }

        // stage('Push Docker Image') {
        //     steps {
        //         // Push Docker image to a container registry
        //         script {
        //             sh "docker push ${DOCKER_IMAGE}"
        //         }
        //     }
        // }
    }
}
