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
        stage('Deploy'){
            steps{
                sh '/var/lib/jenkins/deploy.sh run'
            }
        }
       }
}
