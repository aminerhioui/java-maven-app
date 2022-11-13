pipeline {
    agent any
    environment{
        NEW_VERSION='1.3.0'
    }
    stages {
        stage('build') {
            steps {
                echo 'building application...'
                echo "building ${NEW_VERSION}"
            }
        }
        stage('test') {
            when{
                expression {
                    BRANCH_NAME=='master'
                }
            }
            steps {
                echo 'testing application...'
            }
        }
        stage('deploy') {
            steps {
                echo 'deploying application...'
            }
        }
    }
}
