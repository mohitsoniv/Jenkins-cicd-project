pipeline {
        agent any 
        tools { 
        maven 'local_maven'
        }
       
        stage("Build") {
            steps {
                 sh "cd calculator"
                 sh "mvn compile"
            }
        }       
                    
        stage("Unit test") {
            steps {
                sh "cd calculator"
                sh "mvn test"
            }
        }
        }
