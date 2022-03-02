pipeline {
    agent any
    parameters{
        string(name:'ENV',defaultValue:'Test',description:'version to deploy')
        booleanParam(name:'ExecuteTests',defaultValue:true,description:'decide to run tc')
        choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])
    }
    environment{
        NEW_VERSION = '2.1'
    }
    stages {
        stage('Build') {
            steps {
                script{
                    echo "Building the code"
                    echo "Building version ${NEW_VERSION}"
                }
                          }
            }
        stage('Test'){
            when{
                expression{
                    params.ExecuteTests == true
                }
            }
          steps {
                script{
                    echo "testing the code"
                }
              
            }
            } 
        stage('Deploy'){
          steps {
                script{
                    echo "Deploying the app"
                    echo "Deploying the app to env: ${params.ENV}"
                    echo "Deploying the app version: ${params.APPVERSION}"                
                }
              
            }
            }      
        }
}
