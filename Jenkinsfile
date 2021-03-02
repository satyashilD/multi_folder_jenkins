pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Git checkout') {
            steps {
                checkout scm    
            }
            
        }
    }
}

