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
	  mvn clean verify sonar:sonar -Dsonar.projectKey=mysonarproject -Dsonar.host.url=http://54.152.250.9:1234 -Dsonar.login=sqp_7ba7bcea0080e361488289a44d9d037026ed2d3b
	'''
	
	
	}
	
 }
      
