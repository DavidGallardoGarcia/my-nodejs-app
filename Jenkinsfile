pipeline {
    agent any
    
    environment {
        // Define environment variables if needed
        DOCKER_IMAGE = 'node:14' // Change the Node.js version as needed
        APP_NAME = 'my-nodejs-app'
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
                    docker.image(DOCKER_IMAGE).inside {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests inside the Docker container
                script {
                    docker.image(DOCKER_IMAGE).inside {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image for the Node.js app
                script {
                    docker.build(APP_NAME, '.')
                }
            }
        }

        // stage('Push Docker Image') {
        //     steps {
        //         // Push Docker image to a container registry
        //         script {
        //             docker.withRegistry('https://your-registry-url', 'your-registry-credentials') {
        //                 docker.image(APP_NAME).push()
        //             }
        //         }
        //     }
        // }
    }
}
