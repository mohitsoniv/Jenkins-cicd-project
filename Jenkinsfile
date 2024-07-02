pipeline {
    agent any
    parameters {
  string defaultValue: 'Mohit Soni', name: 'What is your Name?'
}
    tools { 
        maven 'maven'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Unit test') {
            steps {
                echo 'Testing...'
                sh 'mvn test'
            }
        }
        stage('QA') {
            steps {
                echo 'QA...'
            }
        }
        stage('Release') {
            steps {
                echo 'Release...'
            }
        }
    }
}

