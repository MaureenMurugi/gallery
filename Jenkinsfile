pipeline {
    agent any
    tools {
        nodejs "Node-JS"
    }

    stages {
        stage('Cloning the Git Gallery Repo') {
            steps {
                // Clone the GitHub Repository
                git "https://github.com/MaureenMurugi/gallery.git"
            }
        }

        stage('Install Dependencies') {
            steps {
                // Run npm install to install project dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run npm tests to run the tests defined
                sh 'npm test'
            }
        }
    }

    post {
        always {
            // Send a Slack notification when the pipeline completes (both success and failure cases)
            slackSend(
                color: currentBuild.resultIsBetterOrEqualTo('SUCCESS') ? 'good' : 'danger',
                message: "Pipeline ${currentBuild.result}: ${currentBuild.fullDisplayName}\nResult: ${currentBuild.result}",
                channel: '#ip'
            )
            // Send an email notification as before
            emailext(
                subject: "Pipeline ${currentBuild.result}: ${currentBuild.fullDisplayName}",
                body: "The Jenkins pipeline has completed. Result: ${currentBuild.result}",
                to: "murugimaureen99@gmail.com"
            )
        }
    }
}
