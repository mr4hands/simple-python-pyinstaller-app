pipeline {
  agent none
  options {
    skipStagesAfterUnstable()
  }
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
    stage ('Test') {
      agent {
        docker {
          image 'qnib/pytest'
        }
      }
      steps {
        sh 'py.test --verbose --junit-xml test-reports/results.xml /var/jenkins_home/workspace/simple-python-pyinstaller-app/sources/test_calc.py'
      }
      post {
        always {
          junit 'test-reports/results.xml'
        }
      }
    }
    stage ('Deliver') {
      agent {
        docker {
          image 'cdrx/pyinstaller-linux:python2'
        }
      }
      steps {
       sh 'pyinstaller --onefile sources/add2vals.py'
      }
      post {
        success {
          archiveArtifacts 'dist/add2vals'
        }
      }
    }
  }
}