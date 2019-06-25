pipeline {
    agent any
     tools {
            maven 'localMaven'
     }			
     stages {
        stage('Build') {
             steps {
                sh 'mvn clean package'
                sh 'pwd'
                sh 'whoami'
                sh "docker build -t webapp:${env.BUILD_ID} ."
                sh 'docker login -u parthi1996 -p Parthi96$'
                sh "docker tag webapp:${env.BUILD_ID} parthi1996/webapp:${env.BUILD_ID}"
                sh "docker push parthi1996/webapp:${env.BUILD_ID}"
            }	
        		
        }
    }
}
