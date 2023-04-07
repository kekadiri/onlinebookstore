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
                sh "mv target/*.war target/onlinebookstore.war"
            }
         }
        stage("deploy-dev"){
       steps{
          sshagent(['tomcat-dev1']) {
          sh """
          scp -o StrictHostKeyChecking=no target/onlinebookstore.war  
          ubuntu@43.204.108.80:/opt/tomcat/webapps/
          ssh ubuntu@43.204.108.80 /opt/tomcat/bin/shutdown.sh
          ssh ubuntu@43.204.108.80 /opt/tomcat/bin/startup.sh
           """
            }
          }
    }
}
}
