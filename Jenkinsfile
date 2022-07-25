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
        stage('Deploy to DEV') {
            steps {
                echo 'Deploying to DEV....'
            }
        }
      stage('Deploy to QA') {
          when {
                expression { BRANCH_NAME ==~ /main/ }
             }
            steps {
                input "Deploy to QA?"
                echo 'Deploying to QA....'
            }
        }
      stage('Deploy to PROD') {
          when {
                 expression { BRANCH_NAME ==~ /main/ }
             }
            steps {
                input "Deploy to PROD?"
                echo 'Deploying to PROD....'
            }
        }
    }
}
