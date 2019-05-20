pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs('node latest') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Test : Master') { 
            when { branch 'master' }
            steps {
                nodejs('node latest') {
                    //sh 'npm test'  
                    sh 'npm --version'
                    sh 'node --version'
                    echo 'Test master Completed'
                }
            }
        }
        stage('Test : Develop') { 
            when { branch 'develop' }
            steps {
                nodejs('node latest') {
                    //sh 'npm test'  
                    sh 'npm --version'
                    sh 'node --version'
                    echo 'Test develop Completed'
                }
            }
        }
     
        stage('Deliver') { 
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo "MASTER URL"
                    }else if (env.BRANCH_NAME == 'develop') {
                        echo "DEVELOP URL"
                    }   
                }
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