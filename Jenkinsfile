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

    stage('Docker image build') {
      steps {
        sh 'docker build -t amirjaminov/cicd:$BUILD_NUMBER .'
      }
    }

    stage('Docker image deploy') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id')
          {
            docker.image("amirjaminov/cicd:$env.BUILD_NUMBER").push("latest")
          }
        }

      }
    }

  }
}
