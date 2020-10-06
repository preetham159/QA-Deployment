pipeline {
    agent any
    stages {
        stage('SCM Checkout') {
            steps {
               git 'https://github.com/preetham159/QA-Deployment'
            }
        }
        stage('Build using maven') {
            steps {
               sh 'mvn clean package'
            }
        }
        stage('Deployment') {
            steps {
               sshagent(['tomcat8']) {
            sh 'scp target/*.war ubuntu@172.31.39.138:/opt/tomcat8/webapps/'
             }
            }
        }
    }
}
