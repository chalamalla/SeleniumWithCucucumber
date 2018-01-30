pipeline {
    agent any 

    stages {
	
        stage('Compile Stage') {
		
			steps {
				withMaven(maven : 'Maven_3_5_2') {
					sh 'mvn clean compile'
				}
			}
		}	
		
		
		stage('Testing Stage') {
			
			steps {
				withMaven(maven : 'Maven_3_5_2') {
					sh 'mvn test'
				}
			}
		}

		stage('Deployment Stage') {
			
			steps {
				withMaven(maven : 'Maven_3_5_2') {
					sh 'mvn deploy'
				}
			}
		}
    }
	
	
	    post {
    		failure {
      // notify users when the Pipeline fails
      		mail to: 'srvmware1@gmail.com',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
    }
	        
   
}
}
