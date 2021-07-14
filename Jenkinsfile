pipeline {
    agent any

    stages {
        stage('validate') {
            steps {
                echo 'validating..'
		sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
		sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo Deploying..'
		sshagent(['tomcat']){ 
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/04-deploy/target/WebAppCal-1.3.6.war  centos@3.237.204.59:/home/centos/apache-tomcat-7.0.94/webapps/
}

            }
        }
    }
}
