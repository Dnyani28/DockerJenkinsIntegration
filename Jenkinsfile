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
	  mvn clean verify sonar:sonar -Dsonar.projectKey=project -Dsonar.host.url=http://107.23.59.198:4567 -Dsonar.login=sqp_13d2be19d067f4bc06cecad87af0e98cf2d32d05
	'''
	
	
	}
	
 }
      
