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
        withCredentials([string(credentialsId: 'dockerhub', variable: 'DOCKERHUB_CREDENTIALS')]) {
        sh 'echo $DOCKERHUB_CREDENTIALS | docker login -u hemali1310 --password-stdin'
        }
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