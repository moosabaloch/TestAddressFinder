pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs('recent node') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Test') {
            steps {
                nodejs('recent node') {
                    //sh 'npm test'
                    echo 'npm --version'
                }
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Run Deliver App ./jenkins/scripts/deliver.sh' 
                // input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                echo 'Kill all process ./jenkins/scripts/kill.sh' 
            }
        }
    }
}