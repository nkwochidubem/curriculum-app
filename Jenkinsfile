pipeline {
  agent {
    label 'client'
  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/nkwochidubem/curriculum-app', branch: 'dev')
      }
    }

    stage('log') {
      steps {
        sh 'ls -al'
      }
    }

    stage('Build Frontend') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile -t nkwochidubem/curriculum-front:latest .'
      }
    }

    stage('Build backend') {
      steps {
        sh 'docker build -f curriculum-back/Dockerfile -t nkwochidubem/curriculum-back:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'nkwochidubem'
        DOCKERHUB_PASSWORD = 'icui4cu5517'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push Frontend') {
      steps {
        sh 'docker push nkwochidubem/curriculum-front:latest'
      }
    }

    stage('Push Backend') {
      steps {
        sh 'docker push nkwochidubem/curriculum-back:latest'
      }
    }

    stage('Deploy') {
      steps {
        sh 'docker compose -f devops/ansible/docker-compose.yml'
      }
    }

  }
}
