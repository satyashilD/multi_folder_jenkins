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
                sh """ 
                   echo `git diff-tree --no-commit-ud --name-only -r ${env.GIT_COMMIT} | cut -d/ -f1| sort -u`  > folder.txt
                   cat folder.txt
                """
                script {
                    project_dir_name = readFile('folder.txt').trim()
                }                
            }
        }
        stage("Run service build") {
            steps {
                script {
                    service = service_build("${project_dir_name}")
                }
            }
        }
    }
}

def service_build(service_name) {
    String commit_name = service_name;
    List commit_files = commit_name.split(" ");
    SERVICE_DIR = env.BRANCH_NAME.replace("/", "%sF")

    build job: "${commit_name}/${SERVICE_DIR}"
}

