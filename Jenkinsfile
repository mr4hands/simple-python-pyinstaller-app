pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'python:2-alpine'
        }
      }
      steps {
        sh 'python -m py_compile /var/jenkins_home/workspace/simple-python-pyinstaller-app/sources/add2vals.py /var/jenkins_home/workspace/simple-python-pyinstaller-app/sources/calc.py'
      }
    }
  }
}