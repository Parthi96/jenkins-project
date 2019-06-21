pipeline {
    agent any
     tools {
            maven 'localMaven'
     }			
     stages {
        stage('Build') {
            steps {
                   bat script: 'mvn clean package'
            }
        }
       
    }
}
