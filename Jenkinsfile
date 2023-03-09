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
	  mvn clean verify sonar:sonar -Dsonar.projectKey=mainproject -Dsonar.host.url=http://100.26.145.207:1234 -Dsonar.login=sqp_756314a784d18c923da6e7f967689134ac4cd3c6
	'''
	
	
	}
	stage('SendingToNexus') {
	
	sh '''
	  
          curl -v -u admin:admin123 --upload-file /var/lib/jenkins/workspace/project/target/*.war http://100.26.145.207:8082/nexus/content/repositories/project
	'''
	
	
	}
	
	
  }
      
