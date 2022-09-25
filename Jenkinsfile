pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/albert850904/curriculum-app', branch: 'dev', credentialsId: 'freecodecamp-jenkins')
      }
    }

    stage('sh log') {
      steps {
        sh 'ls -la'
      }
    }

  }
}