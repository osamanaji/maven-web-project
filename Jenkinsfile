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
		/*stage('Deploy') { 
            steps {
              sshagent(['jenkins_agent']) {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-web-project-batch-10/target/maven-web-application.war ubuntu@172.31.93.49:/opt/apache-tomcat-8.5.82/webapps/"
}
            } 
        } */
	}
}
