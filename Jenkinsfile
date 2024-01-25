pipeline {
    agent any
    
    environment {
        // Define environment variables if needed
        DOCKER_IMAGE = 'node:14' // Change the Node.js version as needed
        APP_NAME = 'my-node-app'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your version control system
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Use the Node.js Docker image to build the app
                script {
                    sh "docker run --rm -v \$(pwd):/app -w /app ${DOCKER_IMAGE} npm install"
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests inside the Docker container
                script {
                    sh "docker run --rm -v \$(pwd):/app -w /app ${DOCKER_IMAGE} npm test"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image for the Node.js app
                script {
                    sh "docker build -t ${APP_NAME} ."
                }
            }
        }

        // stage('Push Docker Image') {
        //     steps {
        //         // Push Docker image to a container registry
        //         script {
        //             sh "docker push ${APP_NAME}"
        //         }
        //     }
        // }
    }
}
