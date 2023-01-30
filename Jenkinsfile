pipeline {
  agent any
  stages {
    stage("build"){
      steps {
        sh 'mvn clean package'
      }
    }
    stage("test"){
      steps {
        echo 'test the application'
      }
    }
    stage("deploy"){
      steps {
        echo 'deploy the application ..'
      }
    }
  }
}
