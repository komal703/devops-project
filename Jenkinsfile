pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Trivy Image Scan') {
            steps {
                sh 'trivy image myapp:latest'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f myapp || true
                docker run -d -p 5000:5000 --name myapp myapp:latest
                '''
            }
        }
    }
}
