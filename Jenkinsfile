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

        stage ('Build') {
            steps {
                echo 'Hello there'
            }
        }

        stage ('Deploy') {
            steps {
                echo 'Deployed an artifact'
            }
        }
    }
}
