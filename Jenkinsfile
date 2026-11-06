pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yayayekinni1-alt/AWSDemo1.git', branch: 'master'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t iamyekinniyayaisaiah/jenkinpipeline .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d --name web-demo -p 8081:80 iamyekinniyayaisaiah/jenkinpipeline'
            }
        }
    }
}

