pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/RohitYadav07/library'
            }
        }

        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build React') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t ebook-app .'
            }
        }

        stage('Start Minikube') {
            steps {
                bat '"C:\\Windows\\System32\\minikube.exe" start --driver=docker'
            }
        }

        stage('Load Image to Minikube') {
            steps {
                bat '"C:\\Windows\\System32\\minikube.exe" image load ebook-app'
            }
        }

        stage('Kubernetes Deploy') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
}