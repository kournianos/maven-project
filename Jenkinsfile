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
        stage('approval'){
            steps {
                script {
                    def result = input(id: 'Proceed1', message: 'Was this successful?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
                    echo 'result: ' + result
                }
            }
        }
    }
}