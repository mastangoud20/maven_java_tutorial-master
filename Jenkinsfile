pipeline {
    agent any
    tools {
        maven 'M2_HOME'
        jdk 'jdk1.8'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }
        
                stage ('Compile') {
            steps {
                    bat 'cd NumberGenerator & mvn compile'
            }
                }
        
                stage ('Test') {
            steps {
                    bat 'cd NumberGenerator & mvn test'
            }
                }

        stage ('Build') {
            steps {
                    bat 'cd NumberGenerator & mvn package'
            }
             post {
                success {
                    junit 'NumberGenerator/target/surefire-reports/*.xml'
                        }
                 }
               

           
            }
        
           stage ('Test') {
            steps {
                    bat 'cd NumberGenerator & mvn deploy'
            }
                }
        }
    
}
