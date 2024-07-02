pipeline {
    agent any

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

