pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
            post {
                success{
                      archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('deploy to stage'){
    	    steps{   
             build job:"deployToStaging"
    	    }    
        }
        stage('deploy to prod'){
    	    steps{
                build job:"deployToProd"
    	    }    
        }
    }
}