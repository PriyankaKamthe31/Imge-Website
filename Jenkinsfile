pipeline {

    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'git@github.com:PriyankaKamthe31/Imge-Website.git'
            }
        }

        stage('Check Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t image-website:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop image-website || true
                docker rm image-website || true
                docker run -d -p 8085:80 --name image-website image-website:v1
                '''
            }
        }

    }
}
