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
        stage('approval'){
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                echo "Hello, nice to meet you."
            }
        }
    }
}