pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/Hutishseju/jenkins-testing.git', branch: 'main'
      }
    }

    stage('List Files') {
      steps {
        sh 'ls -l'
      }
    }

    stage('Display HTML') {
      steps {
        sh 'cat index.html'
      }
    }
  }

  post {
    success {
      echo 'Pipeline executed successfully!'
    }
    failure {
      echo 'Pipeline failed.'
    }
  }
}
