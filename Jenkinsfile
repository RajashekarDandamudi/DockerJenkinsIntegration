node {
    def app

    stage('Clone') {
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
       /*stage('SonarCoverageResults'){
	
	sh '''
	  mvn clean verify sonar:sonar -Dsonar.projectKey=mysonarproject -Dsonar.host.url=http://44.207.3.149:5678 -Dsonar.login=sqp_37b237fc93cce9ff22f7c425b0f777790f99d514
	'''
	
	
	}
	stage('SendingToNexus'){
	
	sh '''
	  
          curl -v -u admin:admin123 --upload-file /var/lib/jenkins/workspace/myproject/target/*.war http://44.207.3.149:8081/nexus/content/repositories/myproject/
	'''
	
	
	}*/
       stage('DockerBuild'){
	
	app = docker.build("mannam786/mydynamicapp")
	
	
	}
       stage('DockerPush'){
	
	docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
      
             }
	
	
	}
	stage('Runnning'){
	
	sh '''
	  docker run -d -p 6666:8080 mannam786/mydynamicapp
	  

	'''
	
	
	}
   
  }
