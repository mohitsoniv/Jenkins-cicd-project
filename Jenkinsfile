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
                sh 'test'
                 jacoco exclusionPattern: '**/*Test*.class', inclusionPattern: '**/*.class', sourceInclusionPattern: '**/*.java'
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
