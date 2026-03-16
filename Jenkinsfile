pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/GayatriKende/ai-devops-platform.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t gayatrik2003/devops-ai .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push gayatrik2003/devops-ai'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop devops || true
                docker rm devops || true
                docker run -d -p 5000:5000 --name devops gayatrik2003/devops-ai
                '''
            }
        }
    }
}
