pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Copy war'){
            steps{
                sh '''
                    scp -i /var/lib/jenkins/aws.pem /var/lib/jenkins/workspace/POC_JAVA_master/target/sample-application-0.0.1-SNAPSHOT.war ec2-user@3.16.147.26:/opt/tomcat9/webapps
                   '''
            }
        }
        stage('Deploy'){
            steps{
                sh ''' 
                      ssh -i /var/lib/jenkins/aws.pem ec2-user@3.16.147.26 'sudo /opt/tomcat9/bin/catalina.sh run' 
                   '''
            }
        }
       }
}
