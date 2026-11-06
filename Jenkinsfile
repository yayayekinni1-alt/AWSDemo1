pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yayayekinni1-alt/SimpleJenkinsPipeline.git', branch: 'master'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t iamyekinniyayaisaiah/jenkinspipeline .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d --name web-demo -p 8082:80 iamyekinniyayaisaiah/jenkinspipeline'
            }
        }
    }
}

