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
    }
}
