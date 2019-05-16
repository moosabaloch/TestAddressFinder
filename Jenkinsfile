pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs('recent node') {
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Test Completed ./jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Run Deliver App ./jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                echo 'Kill all process ./jenkins/scripts/kill.sh' 
            }
        }
    }
}