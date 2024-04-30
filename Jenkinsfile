pipeline {
    agent any
    environment {
        DOCKERHUB_USERNAME = 'balkissd'
        //STAGING_TAG = "${DOCKERHUB_USERNAME}/angular:v1.0.0"
        //SEMGREP_APP_TOKEN = '1c87866c63498142b962151e4b3f762e2d7b7b5985048391c299968d474708b8'
       // REPORT_PATH = 'zap-reports'
        //REPORT_NAME = 'report.html'
    }
    stages {
        stage('Checkout Git') {
            steps {
                script {
                    git branch: 'master',
                    url: 'https://github.com/TCpfe/app.git',
                  //  credentialsId: 'test'
                }
            }
        }
    }
}