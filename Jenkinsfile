pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Vjgit12345/stateful-java-web-app.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(
                                    credentialsId: 'Tomcat', 
                                    path: '', 
                                    url: 'http://3.108.215.219:8001/manager/text')], 
                       contextPath: '/Stateful-Tracker', 
                       war: '**/target/*.war'
            }
        }
    }
}
