pipeline {
    agent any
    environment {
        DOCKERHUB_USERNAME = 'balkissd'
        // Uncomment and modify the following lines if needed
        // STAGING_TAG = "${DOCKERHUB_USERNAME}/angular:v1.0.0"
         SEMGREP_APP_TOKEN = '02c49e2911421009cc385a2fdc1b1bc7cd56c1dbb9e6db7d107f79ef627adbfe'
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
        stage('Install Dependencies') {
            steps {
                dir('/var/lib/jenkins/workspace/App/webapp/') {
                    sh 'npm cache clean --force'
                    sh 'npm install'
                    sh 'npm run build'
                    //sh 'npm test'
                }
            }
        }
         stage('Run Tests') {
            steps {
                script { 
                 
                def appPath = "/var/lib/jenkins/workspace/Front"
                docker.image('opensecurity/nodejsscan:latest').inside('--privileged -u root:root') {
                    sh 'nodejsscan --json .'
                }
                }
            }
        }
        stage('Analysis with SEMGREP') {
            steps {
                sh "docker run -e SEMGREP_APP_TOKEN=${SEMGREP_APP_TOKEN} --rm -v \${PWD}:/src semgrep/semgrep semgrep ci "
            }
        }
    }
}
