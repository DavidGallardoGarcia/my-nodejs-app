pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-nodejs-app'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Run Test') {
            steps {
                script {
                    echo 'Run Test'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }

        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             docker.withRegistry('https://your-docker-registry', 'docker-credentials-id') {
        //                 docker.image(env.DOCKER_IMAGE).push()
        //             }
        //         }
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         script {
        //             sh 'docker run -p 3000:3000 -d --name your-node-app ${DOCKER_IMAGE}'
        //         }
        //     }
        // }
    }

    // post {
    //     success {
    //         echo 'Build, push, and deployment successful!'
    //     }
    //     failure {
    //         echo 'Build, push, or deployment failed!'
    //     }
    // }
}