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
          args '-v ${pwd}:/apps -v ~/.kube/config:/root/.kube/config'
          cmd 'init'
        }
      }
      steps {
        sh 'helm --help'
      }
    }
  }
}