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
	stage('sonarCoverage') {
	
	sh '''
	 mvn clean verify sonar:sonar -Dsonar.projectKey=mysonarproject -Dsonar.projectName='mysonarproject' -Dsonar.host.url=http://3.85.142.220:5678 -Dsonar.token=sqp_4840de2f24bb5aca1999c05bbd1388318a40dc1a
	'''

	}
	stage('SendingToNexus') {
	
	sh '''
	 curl -v -u admin:admin123 --upload-file /var/lib/jenkins/workspace/myproject/target/*.war http://3.85.142.220:8081/nexus/content/repositories/myproject
	'''
	
	
	}
	stage('DockerBuild') {
	
	app = docker.build("dnyani28/mydynamicapp")
	
	
	}
	
	stage('DockerPush'){
	
	docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
      
        }
		
      }
	stage('connetingtoEKS') {
	
	sh '''
	  aws eks update-kubeconfig --region us-east-1 --name sample-ekscluster
	  kubectl get nodes
	'''

	}
  }
      
