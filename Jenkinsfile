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
        sh 'docker login -u hemali1310 -p Hems@1234'
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