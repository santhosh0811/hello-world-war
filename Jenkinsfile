pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/santhosh0811/hello-world-war.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                sh 'cp /opt/jenkins/workspace/hello-world-war/target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.1.34/webapps/'
            }
        }
    }
}
