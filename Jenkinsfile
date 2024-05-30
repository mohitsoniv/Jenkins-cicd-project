pipeline {
    agent any
    tools {
        maven 'local_maven' 
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
