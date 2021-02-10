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
                   	    
			withCredentials([string(credentialsId: 'credenciales', variable: 'USERPASS')]){
				 sh './gradlew publish'
			}
                
            }
	}

      

        
    }
}

