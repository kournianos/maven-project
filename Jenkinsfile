pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo "Testing.. ${env.BUILD_ID}  --  credentials('1fd9acac-5808-4eab-9898-b5eb6e08060e')"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
