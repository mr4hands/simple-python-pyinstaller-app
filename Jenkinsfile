pipeline {
  agent none
  options {
    skipStagesAfterUnstable()
  }
  stages {
    stage('Build') {
      agent {
        docker {
          image 'dtzar/helm-kubectl'
        }
      }
      steps {
        sh 'helm --help'
      }
    }
  }
}