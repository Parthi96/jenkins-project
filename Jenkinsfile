pipeline {
    agent any
     tools {
            maven 'localMaven'
     }			
     stages {
        stage('Build') {
            steps {
			       echo 'Building the project...'
                   sh 'mvn clean package'
            }
			post{
			       success{
				           echo 'Archiving artifacts...'
						   archiveArtifacts artifacts: '**/*.war'
				   }
			}
        }
		stage('Quality Analysis') {
            steps {
                
                parallel(
                        "Integration Test": {
                            echo 'Run integration tests'
                        },
                        "Sonar Scan": {
                            sh "mvn sonar:sonar"
                        }
                )
            }
        }			
       
    }
}
