pipeline {
    agent any
    parameters {
  string defaultValue: 'Mohit Soni', name: 'What is your Name?'
}
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

