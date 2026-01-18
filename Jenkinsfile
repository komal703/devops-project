pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/komal703/devops-project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Trivy Scan') {
            steps {
                sh 'trivy image myapp:latest'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f myapp || true
                docker run -d -p 5000:5000 --name myapp myapp:latest
                '''
            }
        }
    }
}
