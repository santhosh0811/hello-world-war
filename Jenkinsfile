pipeline {
    agent { label 'slave1' }
    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/santhosh0811/hello-world-war.git '
            }
        } 
       stage('build') {
            steps {
                sh 'cd hello-world-war'
                sh 'mvn clean package'
            }
        }
      stage('deploy') {
           steps {
             sh 'cp /opt/jenkins/workspace/pipeline_job7/target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.1.34/webapps/'
               }
          }
    }
post {
    success {
        mail to: "Santhoshkumar0811@gmail.com",
             subject: "Job Success",
             body: "The Jenkins job completed successfully."
    }
    failure {
        mail to: "santhoshkumar0811@gmail.com",
             subject: "Job is Failed",
             body: "The Jenkins job failed. Check the logs for details."
}
}
}
