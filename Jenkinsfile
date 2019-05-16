pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'npm --version'
                sh 'node --version'
		        sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') { 
            steps {
                sh 'npm test' 
            }
        }
        stage('Deploy') { 
            steps {
                echo 'Ready for deploy '
            }
        }
    }
}