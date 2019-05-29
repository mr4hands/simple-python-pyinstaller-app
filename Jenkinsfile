pipeline {
  agent none
  options {
    skipStagesAfterUnstable()
  }
  stages {
    stage('Build') {
      agent {
        docker {
          image 'alpine/helm:2.9.0'
          args '-v ${pwd}:/apps'
        }
      }
      steps {
        sh 'helm --help'
      }
    }
  }
}