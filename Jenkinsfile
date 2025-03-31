pipeline {
	agent any
	
	tools {
		jdk 'jdk11'
    }

	stages {
		stage('clone-Repo') {
			steps {
				checkout scm
			}
		}

		stage('Build') {
			steps {
				sh 'mvn install - Dmaven.test.skip=true'
			}
		}
		
		stage('Deployment') {
			steps {
				sh 'sshpass -p "sravan" scp target/flipkart.war sravan@172.17.0.2://apache-tomcat-9.0.102/webapps'
				sh 'sshpass -p "sravan" ssh sravan@172.17.0.2 "/apache-tomcat-9.0.102/bin/startup.sh"'

			}
		}
	}
}
	
	

	
    
    
	

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	

	
	
	
