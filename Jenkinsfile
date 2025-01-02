pipeline {
    agent {label 'slave'}
    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf hello-world-war'
				sh 'git clone https://github.com/santhosh0811/hello-world-war.git'
            }
        }
		stage('checkout') {
            steps {
                sh 'cd hello-world-war'
				sh 'mvn clean pacakge'
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['0014']) {
				    sh 'rm -rf hello-world-war-1.0.0war'
                    sh 'ssh-keyscan -H 13.126.42.57 >> ~/.ssh/known_hosts'
                    sh 'sudo scp /var/lib/jenkins/workspace/pipeline_job2/target/hello-world-war-1.0.0.war root@13.126.42.57:/opt/apache-tomcat-10.1.34/webapps/'
                }
            }
			post {
			  success {
			     echo "pipeline success"
				 mail (
				       to: 'santhoshkumar0811@gmail.com'
					   subject: "job is success:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is succees for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}
                ) 							 						
        }
		failure {
		    echo 'pipeline is failed. please check the logs.'
			mail (
				       to: 'santhoshkumar0811@gmail.com'
					   subject: "job is failed:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is failed for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}
							 )
    }
}
