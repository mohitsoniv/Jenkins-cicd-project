pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system
                git 'https://github.com/mohitsoniv/Jenkins-cicd-project.git'
            }
        }
        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Archive the generated artifacts (e.g., JAR files)
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            // Publish JUnit test results
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
