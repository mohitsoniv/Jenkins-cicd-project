pipeline {
    agent any
    tools {
        maven 'Maven' 
    }
    stages {
      stage('Build') {
            steps {
                echo 'Building'
                sh 'mvn compile'
            }
        }
         stage('Packaging') {
            steps {
                echo 'Creating Packages'
                sh 'mvn package'
            }
        }
    }
}
