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
        stage ('Deploy to Staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
        stage('Deploy to Prod'){
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
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