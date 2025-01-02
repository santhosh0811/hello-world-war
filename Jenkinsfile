pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['0014']) {
                    sh "scp webapp/target/webapp.war root@13.126.42.57/:opt/apache-tomcat-10.1.34/webapps"
                }
            }
        }
    }
}
