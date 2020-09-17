pipeline {
  agent any
  stages {
    stage('Cloning Source') {
      parallel {
        stage('Cloning Source') {
          steps {
            git(url: 'https://github.com/fmaulana240699/docker-pipeline.git', branch: 'master', credentialsId: 'fmaulana24')
          }
        }

        stage('Build Image') {
          steps {
            sh 'docker build -t testing-pipeline . '
          }
        }

      }
    }

    stage('Tag Image') {
      steps {
        sh 'docker tag testing-pipeline fmaulana24/testing-pipeline'
      }
    }

    stage('Push Image') {
      steps {
        sh 'docker push fmaulana24/testing-pipeline'
      }
    }

    stage('Deploy Apps') {
      steps {
        sh 'docker run -tid -p 80:80 fmaulana24/testing-pipeline'
      }
    }

  }
}