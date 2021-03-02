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
                sh "echo git diff-tree --no-commit-ud --name-only -r ${env.GIT_COMMIT} | cut -d/ -f1| sort -u > folder.txt" 
                script {
                    project_dir_name = readfile('folder.txt').trim()
                }
                echo "${project_dir_name}"
                build job: "${project_dir_name}"
            } 
        }
    }
}

