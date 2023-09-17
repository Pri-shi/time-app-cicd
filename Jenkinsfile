pipeline {

    agent {
        label "jenkins-agent-ubuntu-slave3"
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from your Git repository
                script {
                    git branch: 'feature/cicd-jenkins', credentialsId: 'Pri-shi-github', url: 'https://github.com/Pri-shi/time-app-cicd.git'
                    sh"""
                    ls
                    pwd
                    """
                }
            }
        }
         stage('Lint') {
            steps {
                // Build and test your web application
                nodejs(nodeJSInstallationName: 'nodejs'){
                    sh '''
                        cd app/src
                        npm install
                        npx htmlhint@1.1.4 index.html
                        npx stylelint@15.10.3 --fix --config .stylelintrc.temp.json style.css
                    '''
                }
            }
        }
        stage('Build ') {
            steps {
                // Build and test your web application
               nodejs(nodeJSInstallationName: 'nodejs'){
                sh '''
                cd app/src
                npm run build
                '''
               }
            }
        }
        stage('Deploy') {
            when {
                // Only deploy if the previous stages were successful
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
                branch "main"
            }
            steps {
                // Add deployment commands here
                nodejs(nodeJSInstallationName: 'nodejs'){
                     sh """
                    cd app/src 
                    npm run deploy 
                    """
                }
            }
        }
    }
     post {
        always {
            archiveArtifacts artifacts: '*.log', onlyIfSuccessful: true, allowEmptyArchive: true
            emailext to: "priyamvadajoshii1@example.com",
            subject: "Jenkins Build: ${currentBuild.currentResult}: ${JOB_NAME}",
            body: "${currentBuild.currentResult}: Job ${JOB_NAME}",
            attachmentsPattern: 'my-pipeline-log.log'
            cleanWs()
        }
    }
}
