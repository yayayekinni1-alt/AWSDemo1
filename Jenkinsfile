pipeline {
  agent {
    docker {
      image 'docker:latest'
      alwaysPull true
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
  environment {
    HOME = "${env.WORKSPACE}"  // ✅ Use workspace instead of /
    IMAGE_NAME = 'iamyekinniyayaisaiah/1jenkinspipeline'
    CONTAINER_NAME = 'web-1demo'
    HOST_PORT = '8083'
    CONTAINER_PORT = '80'
  }
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/yayayekinni1-alt/SimpleJenkinsPipeline.git', branch: 'master'
      }
    }
    stage('Cleanup') {
      steps {
        sh '''
          docker stop ${CONTAINER_NAME} || true
          docker rm ${CONTAINER_NAME} || true
        '''
      }
    }
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t ${IMAGE_NAME} .'
      }
    }
    stage('Run Container') {
      steps {
        sh '''
          docker run -d \
            --name ${CONTAINER_NAME} \
            -p ${HOST_PORT}:${CONTAINER_PORT} \
            ${IMAGE_NAME}
        '''
      }
    }
    stage('Verify') {
      steps {
        sh 'sleep 3 && curl -f http://localhost:${HOST_PORT} || exit 1'
      }
    }
  }
}

