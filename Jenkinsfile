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
                    scp -i /root/aws.pem /var/lib/jenkins/workspace/kins-multibranch-pipeline_master/target/sample-application-0.0.3-SNAPSHOT.war ec2-user@3.16.147.26:/opt/tomcat9/webapps
                   '''
            }
        }
        stage('Deploy'){
            steps{
                sh ''' 
                      ssh -i /root/aws.pem ec2-user@3.16.147.26 '/opt/tomcat9/bin/catalina.sh run' 
                   '''
            }
        }
       }
}
