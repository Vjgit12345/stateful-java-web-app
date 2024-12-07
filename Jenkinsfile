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
                                          url: 'http://15.206.84.254:8001')], 
                       contextPath: 'Stateful-Tracker/', 
                       war: '**/target/*.war'
            }
        }
    }
}
