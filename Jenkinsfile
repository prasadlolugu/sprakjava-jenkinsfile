pipeline{
    agent any 
    
    environment{
        PATH = "/opt/maven36/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git 'git@github.com:KUMAR-REDDY-BAVANASI/sparkjava-war-example.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh 'mvn clean package'
                sh 'mv target/*.war target/hello.war'
            }
        }
        stage("Deploy"){
            steps{
                sh """ 
            
                    scp target/hello.war root@3.8.127.207:/opt/tomcat9/webapps/
            
                    ssh root@3.8.127.207 /opt/tomcat9/bin/shutdown.sh
            
                    ssh root@3.8.127.207 /opt/tomcat9/bin/startup.sh
            
            
                """
            }
        }
    }
}
