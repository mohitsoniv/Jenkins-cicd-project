pipeline {
    agent any

     tools {
        maven 'maven' 
    }
    parameters {
  string defaultValue: 'Mohit Soni', name: 'What is your Name?'
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

