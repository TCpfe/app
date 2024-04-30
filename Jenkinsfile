pipeline {
    agent any
    environment {
        DOCKERHUB_USERNAME = 'balkissd'
        // Uncomment and modify the following lines if needed
        // STAGING_TAG = "${DOCKERHUB_USERNAME}/angular:v1.0.0"
        // SEMGREP_APP_TOKEN = '1c87866c63498142b962151e4b3f762e2d7b7b5985048391c299968d474708b8'
        // REPORT_PATH = 'zap-reports'
        // REPORT_NAME = 'report.html'
    }
    stages {
        stage('Checkout Git') {
            steps {
                script {
                    git branch: 'master',
                    url: 'https://github.com/TCpfe/app.git'
                    // Uncomment the following line if you have credentials to access the repository
                    // credentialsId: 'test'
                }
            }
        }
         stage('NPM Build') {
            steps {
                script {
                    sh 'npm cache clean --force'
                    sh 'npm install --legacy-peer-deps --verbose'
                    sh 'npm run build'
                }
            }
        }
    }
}
