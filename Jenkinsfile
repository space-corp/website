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
            post {
                 always {
                     jiraSendDeploymentInfo environmentId: 'us-east-1', environmentName: 'us-east-1', environmentType: 'development'
                 }
             }
        }
      stage('Deploy to QA') {
            when {
                expression {
                return env.GIT_BRANCH == "origin/main"
                }
        } 
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                input "Deploy to QA?"
                echo 'Deploying to QA....'
                    post {
                 always {
                     jiraSendDeploymentInfo environmentId: 'us-west-1', environmentName: 'us-west-1', environmentType: 'testing'
                 }
             }
                }
            }
          
        }
      stage('Deploy to PROD') {
         when {
                expression {
                return env.GIT_BRANCH == "origin/main"
                }
        } 
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                input "Deploy to PROD?"
                echo 'Deploying to PROD....'
                }
            }
          post {
                 always {
                     jiraSendDeploymentInfo environmentId: 'us-central-1', environmentName: 'us-central-1', environmentType: 'production'
                 }
             }
        }
    }
}
