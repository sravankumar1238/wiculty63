 pipeline {
    agent any

	tools {
		jdk 'jdk11'
	}

//	environment {
//		M2_INSTALL = "/usr/bin/mvn"
//	}

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }

        stage('Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
		
 //       stage('Unit Tests') {
 //           steps {
 //               sh 'mvn compiler:testCompile'
 //               sh 'mvn surefire:test'
 //               junit 'target/**/*.xml'
 //           }
 //       }

        stage('Deployment') {
            steps {
                sh 'sshpass -p "sravan" scp target/flipkart.war sravan@172.17.0.2:/apache-tomcat-9.0.102/webapps'
                sh 'sshpass -p "sravan" ssh sravan@172.17.0.2 "/apache-tomcat-9.0.102/bin/startup.sh"'
            }
        }
    }
}





