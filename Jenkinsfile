pipeline {
    agent any
 
    tools {
        maven 'localMaven'
    }
 
stages{
        stage('Build'){
            steps {
                'mvn.cmd'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}

