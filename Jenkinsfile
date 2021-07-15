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
                echo 'Deploying....'
		sh 'mvn deploy'
		sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/WebAppCal-1.1.2.war centos@100.24.106.159:/home/centos/apache-tomcat-7.0.94/webapps'}
            }
        }
    }
}
