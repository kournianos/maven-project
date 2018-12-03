pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                    echo 'Archived'
                }
            }
        }

        input{
            message "Press Ok to continue"
        }

        stage ('Deploy to Staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }

        stage ('Deploy to Production'){
            steps{
                 build job: 'deploy-to-Prod'
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