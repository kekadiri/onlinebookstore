pipeline {
  agent any
  stages {
    stage("build"){
      steps {
        echo 'build the application ..'
      }
    }
    stage("test"){
      steps {
        sh 'mvn clean package'
      }
    }
    stage("deploy"){
      steps {
        echo 'deploy the application ..'
      }
    }
  }
}
