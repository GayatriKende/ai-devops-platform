pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "gayatrik2003/devops-ai"
        CONTAINER_NAME = "devops-${BUILD_NUMBER}" 
        HOST_PORT = "5000"
        CONTAINER_PORT = "5000"
    }

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE}:latest ."
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push ${DOCKER_IMAGE}:latest"
            }
        }

        stage('Deploy Container') {
            steps {
                sh """
                
                docker ps -a --filter "name=devops" --format "{{.Names}}" | xargs -r docker stop
                docker ps -a --filter "name=devops" --format "{{.Names}}" | xargs -r docker rm

                
                docker run -d -p ${HOST_PORT}:${CONTAINER_PORT} --name ${CONTAINER_NAME} ${DOCKER_IMAGE}:latest
                """
            }
        }

    }

    post {
        success {
            echo "Pipeline completed successfully! Deployed container: ${CONTAINER_NAME}"
        }
        failure {
            echo "Pipeline failed! Check the logs."
        }
    }
}
