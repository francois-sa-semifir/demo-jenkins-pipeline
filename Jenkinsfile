pipeline {
  agent {
    docker { image 'node:18-alpine' }
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/francois-sa-semifir/demo-jenkins-pipeline.git', branch: 'main'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Run tests') {
      steps {
        sh 'npm test'
        junit 'junit.xml'
      }
    }
  }

  post {
    always { echo 'Fin du pipeline.' }
    success { echo 'Succès des tests !' }
    failure { echo 'Échec des tests.' }
  }
}
