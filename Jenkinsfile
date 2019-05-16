pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
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