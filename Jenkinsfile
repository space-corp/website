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
                 success {
                     jiraSendDeploymentInfo environmentId: 'DEV', environmentName: 'DEV', environmentType: 'development'
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
                }
            }
             post {
                 success {
                     jiraSendDeploymentInfo environmentId: 'QA', environmentName: 'QA', environmentType: 'testing'
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
                 success {
                     jiraSendDeploymentInfo environmentId: 'PROD', environmentName: 'PROD', environmentType: 'production'
                 }
             }
        }
    }
}
