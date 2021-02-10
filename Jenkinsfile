pipeline {
    agent any

    stages {
        
        stage('Build') {
            steps {
                withGradle {
                    sh 'chmod +x ./gradlew'
                    sh './gradlew assemble'

                }
            }

            post {
                success {
                    archiveArtifacts 'build/libs/*.jar'
                }
            }


        }
        

	stage('Publish') {
            steps {
		    archiveArtifacts 'build/libs/*.jar'
                   	    
			withCredentials([usernamePassword(credentialsId: 'credenciales', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
				 sh './gradlew publish'
			}
                
            }
	}

      

        
    }
}

