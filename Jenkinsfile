pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '52.43.141.131', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '34.209.233.6', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        bat "scp -i tomcat-k-aline-2.pem "C:\Program Files (x86)\Jenkins\workspace\deploy-to-staging\webapp\target\webapp.war" ec2-user@52.43.141.131:/var/lib/tomcat7/webapps"
                    }
                }

            }
        }
    }
}
