pipeline {
    agent any
     tools {
            maven 'localMaven'
     }			
     stages {
        stage('Build') {
            steps {
			       echo 'Building the project...'
                   bat script: 'mvn clean package'
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
                            bat script: "mvn sonar:sonar"
                        }
                )
            }
        }			
       
    }
}
