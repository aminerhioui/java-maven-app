
def gv
pipeline {
    agent any
    environment{
        NEW_VERSION='1.3.0'
    }
    tools{
        maven 'maven-3.8.6'
    }
    stages {
        stage('init'){
            steps{
                script{
                    gv=load "script.groovy"
                }
            }
        }
        stage('test') {
            steps{
                script{
                    echo 'testing the application....'
                }  
            }  
        }
        stage('build') {
            when{
                expression{
                    BRANCH_NAME == 'master'
                }
            }
            steps{
                script{
                    sh 'mvn package'
                }  
            }  
        }
        
        stage('build image') {
            
            steps {
                
                script{
                    echo 'building the docker image...'
                    //withCredentials([usernamePassword(credentialsId:'docker-hub-repo',passwordVariable:'PASS',usernameVariable:'USER')]){
                      //  sh 'docker build -t aminerhioui/demo-app:jma-2.0 .'
                        //sh "echo $PASS | docker login -u $USER --password-stdin" 
                        //sh 'docker push aminerhioui/demo-app:jma-2.0'
                    //}
                }
            }
        }
        stage('deploy') {
            steps {
                script{
                    gv.deployApp()
                }
            }
        }
    }
}
