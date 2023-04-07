pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
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
                sshagent(['d4bbf58b-b8e9-4bba-9fd1-917ac573a4e6']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/onlinebookstore.war  ubuntu@43.204.108.80:/opt/apache/webapps
                    
                    ssh ubuntu@43.204.108.80 /opt/apache/bin/shutdown.sh
                    
                    ssh ubuntu@43.204.108.80 /opt/apache/bin/startup.sh
                
                """
            }
            
            }
        }
    }
}
