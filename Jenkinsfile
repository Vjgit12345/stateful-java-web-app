pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', 
                                          path: '', 
                                          url: 'http://3.108.215.219:8001/')], 
                       contextPath: 'Stateful-Tracker/', 
                       war: '**/target/*.war'
            }
        }
    }
}
