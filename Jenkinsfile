pipeline {
  agent {
    node {
      label 'client'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/nkwochidubem/curriculum-app', branch: 'dev')
      }
    }

  }
}