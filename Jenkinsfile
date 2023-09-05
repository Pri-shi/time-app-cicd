pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from your Git repository
                script {
                    git branch: 'main', credentialsId: 'bitbucket-credentials', url: 'https://pri-shi-admin@bitbucket.org/pri-shi/time-app-cicd.git'
                    sh"""
                    ls
                    """
                }
            }
        }

        // stage('Build ') {
        //     steps {
        //         // Build and test your web application
        //         script {
        //             sh '''npm install
        //                   npm run build'''
        //             // Add commands for testing, e.g., HTML/CSS validation
        //         }
        //     }
        // }
        //  stage('Lint') {
        //     steps {
        //         // Build and test your web application
        //         script {
        //             sh 'htmlint '
        //             sh 'npm run build'
        //             // Add commands for testing, e.g., HTML/CSS validation
        //         }
        //     }
        // }
        // stage('Deploy') {
        //     when {
        //         // Only deploy if the previous stages were successful
        //         expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
        //         branch "main"
        //     }
        //     steps {
        //         // Add deployment commands here
        //         script {
        //             // Example: Deploy to a web server using SCP
        //             sh 'scp -r ./dist/* user@your-server:/path/to/your/webroot/'
        //             // Make sure Jenkins has SSH access to your server
        //         }
        //     }
        // }
    }
}
