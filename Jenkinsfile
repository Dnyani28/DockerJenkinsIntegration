node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
	stage('compile'){
	
	sh '''
	  mvn compile
	'''
	
	
	}
	
	stage('package'){
	
	sh '''
	  mvn package
	'''
	
	
	}
       stage('SonarCoverageResults'){
	
	sh '''
	  mvn clean verify sonar:sonar -Dsonar.projectKey=mysonarproject -Dsonar.host.url=http://34.234.66.90:1234 -Dsonar.login=sqp_a6cd717f05c64fd7f44ac5d157dcaf52b27c68d0 
	'''
	
	
	}
	stage('SendingToNexus'){
	
	sh '''
          curl -v -u admin:admin123 --upload-file /var/lib/jenkins/workspace/myproject/target/*.war http://34.234.66.90:8086/nexus/content/repositories/snapshots
	'''
	
	
	}
       stage('DockerBuild'){
	
	app = docker.build("dnyani28/mydynamicapp")
	
	
	}
       stage('DockerPush'){
	
	docker.withRegistry('https://registry.hub.docker.com', 'docker') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
      
             }
	
	
	}
	stage('ConnectingToEKS'){
	
	sh '''
	  aws eks update-kubeconfig --region us-east-1 --name sample-ekscluster
	  kubectl get nodes

	'''
	
	
	}
   
  }
