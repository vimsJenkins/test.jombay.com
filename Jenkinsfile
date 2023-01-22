pipeline {
  agent any
  environment {
    DOCKERHUB_CREDS=credentials('vimleshpatel')
  }
  stages {
    stage('Cloning Git') {
      steps {
        sh 'git clone https://github.com/vimsJenkins/node.jenkins.in.git'
      }
    }
    stage('Building image') {
      steps {
        sh 'docker build -t vimleshpatel/node.jenkins:latest .'
      }
    }
    stage('Login') {
      steps {
        withCredentials([usernamePassword(credentials: 'vimleshpatel', usernameVariable: username, passwordVariable: password)]){
          sh 'echo $password | docker loging -u $username --password-stdin'
        }
      }
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
}
