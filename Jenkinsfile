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

        stage('Run Tests'){
            steps {
                // Run npm tests to run the tests defined
                sh 'npm test'
            }
        }
        
        //stage('Deploy to Render') {
            //Steps {
                // Start the server on Render using 'node server'
                //sh 'node server'
            //}
        }
    }
