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
                expression {
                return env.GIT_BRANCH == "origin/main"
                }
        } 
            steps {
                input "Deploy to QA?"
                echo 'Deploying to QA....'
            }
        }
      stage('Deploy to PROD') {
          when {
                branch 'main'
             }
            steps {
                input "Deploy to PROD?"
                echo 'Deploying to PROD....'
            }
        }
    }
}
