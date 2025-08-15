pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_FILE = "docker-compose.yml"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/soundarya211120042/microservices-ci-cd.git', credentialsId: 'git_pat'

            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build"
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                script {
                    sh "docker-compose -f ${DOCKER_COMPOSE_FILE} up -d"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    // Simple check if containers are running
                    sh "docker ps"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline run completed!"
        }
    }
}
