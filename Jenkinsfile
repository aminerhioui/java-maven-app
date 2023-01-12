
def gv
pipeline {
    agent any
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
                    echo 'building the application....'
                }  
            }  
        }
        
        stage('build image') {
            
            steps {
                
                script{
                    echo 'building the docker image...'
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
