pipeline {
  environment {
    imagename = "vimleshpatel/node.jenkins"
    registryCredential = 'vimleshpatel'
    dockerImage = ''
    DOCKERHUB_CREDS=credentials('vimleshpatel')
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/vimsJenkins/node.jenkins.in.git'
      }
    }
    stage('Building image') {
      steps{
        sh 'docker build -t vimleshpatel/node.jenkins:latest .'
      }
    }
    stage('Login') {
      sh 'echo $DOCKERHUB_CREDS_PSW | docker loging -u $DOCKERHUB_CREDS_USR --password-stdin'
    }
    stage('Deploy Image') {
      steps{
        sh 'docker push vimleshpatel/node.jenkins:latest'
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi vimleshpatel/node.jenkins:latest"
        sh "docker rmi $imagename:latest"
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
