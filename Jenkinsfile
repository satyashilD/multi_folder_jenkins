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

        stage('Get folder name') {
            steps {
                sh "echo git diff-tree --no-commit-ud --name-only -r ${env.GIT_COMMIT} " 
            } 
        }
    }
}

