pipeline {
    agent {
        docker {
            image 'docker:latest'
            alwaysPull true
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yayayekinni1-alt/SimpleJenkinsPipeline.git', branch: 'master'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t iamyekinniyayaisaiah/1jenkinspipeline .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d --name web-1demo -p 8083:80 iamyekinniyayaisaiah/1jenkinspipeline'
            }
        }
    }
}

