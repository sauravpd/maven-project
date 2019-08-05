pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                build job: 'package'
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'deployToStaging'
            }
        }

        stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }

                build job: 'deployToProd'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                }

                failure {
                    echo ' Deployment failed.'
                }
            }
        }


    }
}