pipeline {
    agent any
    tools {
        maven 'Maven'
      }
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
            }
        }
     stage('Compile') {
            steps {
                script {
                sh 'mvn compile test'  
            }
            }
        }   
    }
    post { 
        failure { 
            script {
                // CHANGE_ID is set only for pull requests, so it is safe to access the pullRequest global variable
                if (env.CHANGE_ID) {
                    pullRequest.addLabel('Build Failed')
                }
            }
        }
    }
}
