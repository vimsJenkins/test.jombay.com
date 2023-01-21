pipeline {
  agent any
  stages {
    stage('Branch:2 Stage 1') {
      parallel {
        stage('Branch:2 Stage 1') {
          steps {
            echo 'Branch:2 Hello Stage 1 step 1'
            sleep 10
            echo 'Branch:2 Stage 1 step 3 after 10 seconds'
          }
        }

        stage('Branch:2 PStage2') {
          steps {
            echo 'Branch:2 PStage 2 step 1'
          }
        }

      }
    }

  }
}
