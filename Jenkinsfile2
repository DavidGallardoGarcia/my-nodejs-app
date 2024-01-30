pipeline {
    agent any

    parameters {
        string(name: 'DOCKER_IMAGE', defaultValue: 'my-nodejs-app', description: 'Docker image name')
        string(name: 'DOCKER_REGISTRY', defaultValue: 'https://your-docker-registry', description: 'Docker registry URL')
        string(name: 'DOCKER_CREDENTIALS_ID', defaultValue: 'docker-credentials-id', description: 'Docker credentials ID')
        booleanParam(name: 'PUSH_DOCKER_IMAGE', defaultValue: false, description: 'Push Docker image to registry')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy Docker image')
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
                    docker.build(params.DOCKER_IMAGE)
                }
            }
        }

        // stage('Push Docker Image') {
        //     when {
        //         expression { params.PUSH_DOCKER_IMAGE }
        //     }
        //     steps {
        //         script {
        //             docker.withRegistry(params.DOCKER_REGISTRY, params.DOCKER_CREDENTIALS_ID) {
        //                 docker.image(params.DOCKER_IMAGE).push()
        //             }
        //         }
        //     }
        // }

        stage('Deploy') {
            when {
                expression { params.DEPLOY }
            }
            steps {
                script {
                    input "Deploy to production?"
                    sh "docker run -p 3000:3000 -d --name my-nodejs-app ${params.DOCKER_IMAGE}"
                }
            }
        }
    }

    post {
        success {
            echo 'Build, push, and deployment successful!'
        }
        failure {
            echo 'Build, push, or deployment failed!'
        }
    }
}