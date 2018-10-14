pipeline {
    agent any
 
    tools {
        maven 'localMaven'
    }
 
stages{
        stage('Build'){
            steps {
                print "cmd /c mvn".execute().text
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

