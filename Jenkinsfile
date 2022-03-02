pipeline {
    agent none
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }    
    stages {
        stage('COMPILE') {
            agent any
            steps {
                script{
                    echo "COMPILING THE CODE"
                    git 'https://github.com/amaddireddy/addressbook-1.git'                    
                    sh 'mvn compile'
                }
                          }
            }
        stage('UNITTEST'){
            agent{label 'linux_slave'}           
            steps {
                script{
                    echo "RUNNING THE UNIT TEST CASES"
                    sh 'mvn test'
                }
              
            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
            }
        stage('PACKAGE'){
            agent any            
           steps{
                script{
                    echo "PACKAGING THE CODE"
                    sh 'mvn package'                   
                }
            }
        }         
         }
}
