pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Application Build') {
      steps {
        sh 'script ./scripts/build.sh'
      }
    }

    stage('Application Test') {
      steps {
        sh 'script ./scripts/test.sh'
      }
    }

  }
}
