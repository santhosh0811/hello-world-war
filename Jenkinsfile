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

            }
}
        
    

