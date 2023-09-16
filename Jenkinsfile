pipeline {

    agent {
        label: "jenkins-agent-ubuntu-slave3"
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from your Git repository
                script {
                    git branch: 'main', credentialsId: 'bitbucket-credentials', url: 'https://pri-shi-admin@bitbucket.org/pri-shi/time-app-cicd.git'
                    sh"""
                    ls
                    pwd
                    """
                }
            }
        }

//         stage('Build ') {
//             steps {
//                 // Build and test your web application
//                 script {
//                     sh """
//                     npm install
//                     npm run build
//                     echo 'export PATH=$PATH:$(npm bin -g)' >> $HOME/.bashrc
//                     """
//                     // Add commands for testing, e.g., HTML/CSS validation
//                 }
//             }
//         }
//          stage('Lint') {
//             steps {
//                 // Build and test your web application
//                 script {
//                     sh """
//                     npx htmlhint index.html
//                     npx stylelint --fix --config .stylelintrc.temp.json style.css
//                     """
//                     // Add commands for testing, e.g., HTML/CSS validation
//                 }
//             }
//         }
//         stage('Deploy') {
//             when {
//                 // Only deploy if the previous stages were successful
//                 expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
//                 branch "main"
//             }
//             steps {
//                 // Add deployment commands here
//                 script {
//                     // Example: Deploy to a web server using SCP
//                     // deploys web application to port 8080 of agent
//                     sh """
//                     npm deploy 
//                     """
//                     // Make sure Jenkins has SSH access to your server
//                 }
//             }
//         }
    }
}
