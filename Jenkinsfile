pipeline {
    agent any
    stages {
        stage ('Build Servlet Project') {
            steps {
                /* Maven step */
                bat 'mvn clean package'
            }
            /*Post-build actions*/
            post {
                success {
                    echo 'Now Archiving...'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }

        stage ('Deploy Build in Staging Area') {
            steps {
                build job : 'Deploy_StagingArea_Pipeline'
            }
        }

        stage ('Deploy Build in Production Environment') {
            steps {
                timeout (time: 5, unit: 'Days') {
                    input message : 'Approve PRODUCTION Deployment?'
                }

                build job : ''
            }

            post {
                success {
                    echo 'Deployment on PRODUCTION is Successful'
                }

                failure {
                    echo 'Deployment Failure on PRODUCTION'
                }
            }
        }
    }
}
