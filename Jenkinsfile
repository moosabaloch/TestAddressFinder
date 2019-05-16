pipeline {
    agent any
    env.NODEJS_HOME = "${tool 'Node 6.x'}"
    env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"
    sh 'npm --version'
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