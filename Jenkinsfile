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

        stage('Docker Stop Old') {
            steps {
                bat 'docker stop ebook-container || exit 0'
                bat 'docker rm ebook-container || exit 0'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t ebook-app .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker run -d -p 3000:3000 --name ebook-container ebook-app'
            }
        }
    }
}