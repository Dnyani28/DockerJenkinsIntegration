node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
       }
	stage('compile') {
	
	sh '''
	  mvn compile
	'''
	
	
	}
	
	stage('package') {
	
	sh '''
	  mvn package
	'''
	
	
	}
	stage('SonarCoverageResults') {
	
	sh '''
	  mvn clean verify sonar:sonar -Dsonar.projectKey=mainproject -Dsonar.host.url=http://100.26.145.207:1234 -Dsonar.login=sqp_a0f975dab0346b9e089717f13b04ea80e8688d97
	'''
	
	
	}
	
	
  }
      
