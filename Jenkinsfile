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
                echo 'Testing..'
            }
        }
        stage('DEV Deploy') {
            steps {
                echo 'Deploying to DEV....'
            }
        }
      stage('QA Deploy') {
            steps {
                input "Deploy to QA?"
                echo 'Deploying to QA....'
            }
        }
      stage('PROD Deploy') {
            steps {
                input "Deploy to PROD?"
                echo 'Deploying to PROD....'
            }
        }
    }
}
