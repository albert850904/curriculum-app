pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/albert850904/curriculum-app', branch: 'dev', credentialsId: 'freecodecamp-jenkins')
      }
    }

    stage('sh log') {
      parallel {
        stage('sh log') {
          steps {
            sh 'ls -la'
          }
        }

        stage('fe unit test') {
          steps {
            sh 'cd curriculum-front && npm i && npm run test:unit'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile . -t kairucheng/curriculum-front:latest'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'kairucheng'
        DOCKERHUB_PASSWORD = 'u4PPGke8ozRKWr'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('push') {
      steps {
        sh 'docker push kairucheng/curriculum-front-test:latest'
      }
    }

  }
}