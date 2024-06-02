pipeline { agent any tools { maven 'local_maven' 
                            // Ensure Maven is installed and configured in Jenkins jdk 'JDK 11' 
                            // Ensure JDK is installed and configured in Jenkins } stages { stage('Checkout') 
                            { steps { git 'https://github.com/mohitsoniv/Jenkins-cicd-project.git' } } stage('Build') 
                            { steps { sh 'mvn clean package' } } stage('Test') { steps { sh 'mvn test' } } stage('Deploy')
                            { steps { // Add your deployment steps here echo 'Deploying application...' } } } 
                            post { success { echo 'Pipeline completed successfully!' } failure { echo 'Pipeline failed!' } } }
