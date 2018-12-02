pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            environment {
                AN_ACCESS_KEY = credentials('1fd9acac-5808-4eab-9898-b5eb6e08060e')
            }
            steps {
                sh 'printenv'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
