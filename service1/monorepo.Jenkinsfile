pipeline {
    agent any

    parameters {
         booleanParam(
                    defaultValue: false, 
                    description: 'Deploy artifacts', 
                    name: 'PUBLISH_ARTIFACT'
                            ),
        choice(
            name: 'DEPLOY_ALLL',
            choices: ['ALL', 'service1', 'service2', 'service3'],
            description: 'Deploy artifacts'
        )
        choice(
            name: 'BUILD_ALL',
            choices: ['ALL', 'service1', 'service2', 'service3'],
            description: 'Deploy artifacts'
        )
    }

    stage('Checkout repository') {
            steps {
                
                    checkout scm
                }
            }
    stages {
                stage ('Build All') {
            when {
                expression {
                    params.BUILD_ALL == 'ALL' &&params.PUBLISH_ARTIFACT == true && params.DEPLOY_ALL != true
                }
            }
            steps {
                sh """ 
                  BUILD scrip goes here
                """              
            }
        }
                stage ('Build service1') {
            when {
                expression {
                    params.BUILD_ALL == 'service1'
                }
            }
            steps {
                sh """ 
                  BUILD scrip goes here
                """              
            }
        }
        }
}

    stages {
                stage ('Publish artifacts All') {
            when {
                expression {
                    params.BUILD_ALL == 'ALL' &&params.PUBLISH_ARTIFACT == true
                }
            }
            steps {
                sh """ 
                  BUILD scrip goes here
                """              
            }
        }
                stage ('Build service1') {
            when {
                expression {
                    params.BUILD_ALL == 'service1' &&params.PUBLISH_ARTIFACT == 'service1
                }
            }
            steps {
                sh """ 
                  BUILD scrip goes here
                """              
            }
        }
        }
}

    stages {
                stage ('Deploy All') {
            when {
                expression {
                    params.BUILD_ALL == 'ALL' &&params.PUBLISH_ARTIFACT == true && params.DEPLOY_ARTIFACTS = 'ALL'
                }
            }
            steps {
                sh """ 
                  BUILD scrip goes here
                """              
            }
        }
                stage ('Deploy service1') {
            when {
                expression {
                    params.BUILD_ALL == 'service1' &&params.PUBLISH_ARTIFACT == 'service1' && params.DEPLOY_ARTIFACTS = 'service1'
                }
            }
            steps {
                sh """ 
                  DEPLOY scrip goes here
                """              
            }
        }
        }
