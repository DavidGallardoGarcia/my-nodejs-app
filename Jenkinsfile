pipeline {
    agent any

    environment {
        // Customize environment variables if needed
        NODE_VERSION = '14'
        DOCKER_IMAGE = "node:${NODE_VERSION}"
        APP_NAME = 'my-nodejs-app'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system (e.g., Git)
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Use the specified Node.js version
                docker.image(params.DOCKER_IMAGE).inside {
                    sh 'npm install'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build(params.APP_NAME)
                }
            }
        }

        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             // Push the Docker image to a container registry
        //             docker.withRegistry('https://your-docker-registry', 'docker-registry-credentials-id') {
        //                 docker.image(APP_NAME).push()
        //             }
        //         }
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         // Deploy your application using the Docker image
        //         script {
        //             docker.image(APP_NAME).inside {
        //                 sh 'docker-compose up -d'
        //             }
        //         }
        //     }
        // }
    }

    // post {
    //     success {
    //         echo 'Deployment successful!'
    //     }
    //     failure {
    //         echo 'Deployment failed!'
    //     }
    // }
}
