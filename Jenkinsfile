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
            
                    scp target/hello.war root@3.80.138.35:/opt/tomcat/webapps/
            
                    ssh root@3.80.138.35 /opt/tomcat/bin/shutdown.sh
            
                    ssh root@3.80.138.35 /opt/tomcat/bin/startup.sh
            
            
                """
            }
        }
    }
}
