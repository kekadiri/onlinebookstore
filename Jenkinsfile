pipeline {
  agent { label 'maven' }
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[git branch: 'J2EE', credentialsId: 'git', url: 'https://github.com/kekadiri/onlinebookstore.git']]])
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
  }
}
