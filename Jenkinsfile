pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t hemali1310/devops .'
      }
    }
    stage('Login') {
      steps {
        sh 'cp /home/ubuntu/.docker/config.json $HOME/.docker/config.json'
      }
    }


    stage('Push') {
      steps {
        sh 'docker push hemali1310/devops'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}