pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        stage('Deploy') {
            steps {
                sshagent(['0013']) {
                    sh "cp webapp/target/webapp.war /opt/apache-tomcat-10.1.34/webapps"
        }
            }
        }
    }
}
