pipeline {
	agent any
stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-user', url: 'https://github.com/devopsdeepdive/maven-web-project.git']]]) 
            }
        }
		stage('Build') { 
            steps {
              sh 'mvn compile'
            }
        }
		stage('Test') { 
            steps {
              sh 'mvn test'
            }
        }
		stage('Package') { 
            steps {
              sh 'mvn package'
            }
        }
	
	stage('Deploy') { 
            steps {
             sshagent(['tomcat_deploy']) {
		sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven_deploy/target/maven-web-application.war ubuntu@54.164.100.159:/opt/apache-tomcat-8.5.84/webapps'   
            }
        }
	}
}
