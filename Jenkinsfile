pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
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