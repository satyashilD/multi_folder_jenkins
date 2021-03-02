pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo "${env.CHANGE_ID}"
                echo "${env.BRANCH_NAME}"
            }
        }
        stage('Git checkout') {
            steps {
                checkout scm    
            }
            
        }
    }
}

