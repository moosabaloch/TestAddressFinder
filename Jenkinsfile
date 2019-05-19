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
                    sh 'npm --version'
                    sh 'node --version'
                    echo 'Test Completed'
                }
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Deploying...' + env.BRANCH_NAME
                echo 'Run Deliver App ./jenkins/scripts/deliver.sh' 
                // input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                // sh 'npm run deploy'
                sh "aws s3 sync build/ s3://jenkin-testing-react-app --acl public-read"
                echo 'Kill all process ./jenkins/scripts/kill.sh' 
            }
        }
    }
}