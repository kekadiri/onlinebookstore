pipeline{
    agent any
    stages{
        stage("GIT checkout"){
            steps{
                git branch: 'J2EE', credentialsId: 'git', url: 'https://github.com/kekadiri/onlinebookstore.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
         }
    }
}
