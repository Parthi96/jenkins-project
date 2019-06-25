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
		
        		
       
    }
}
