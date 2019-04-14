pipeline{
    agent any

    parameters {
        string(name: 'tomcat_stage', defaultValue: '3.87.210.247', description: 'Staging Server')
        string(name: 'tomcat_prod', defaultValue: '3.85.193.45', description: 'Production Server')
    }

    stages {
        stage("Build") {
            steps {
                sh 'echo "this is building phase"'
                sh 'mvn clean package'
            }
            post {
                success {
                    sh 'echo "Now Archiving..."'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
                failure {
                    sh 'echo "Failed to build the project code"'
                }
            }
        }
        stage("Deploy") {
            parallel{
                stage('Deploy to staging'){
                    steps {
                        sh 'scp -i 'F:\Study\AWS\myKeypair.pem' **/target/*.war ubuntu@${params.tomcat_stage}:/var/lib/tomcat8/webapps/ROOT/'
                    }
                }
                stage('Deploy to production'){
                    steps {
                        sh 'scp -i 'F:\Study\AWS\myKeypair.pem' **/target/*.war ubuntu@${params.tomcat_prod}:/var/lib/tomcat8/webapps/ROOT/'
                    }
                }

            }
        }
    }
}