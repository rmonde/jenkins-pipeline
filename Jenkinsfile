pipeline{
    agent any

    parameters {
        string(name: 'tomcat_stage', defaultValue: '3.86.181.248', description: 'Staging Server')
        string(name: 'tomcat_prod', defaultValue: '3.80.126.73', description: 'Production Server')
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
        stage('Deployment'){
            steps {
                build job: 'deploy-to-staging'
            }
            post {
                success {
                    sh 'echo "Successful deployment"'
                }
                failure {
                    sh 'echo "Failed to deploy the code"'
                }
            }
        }
    }
}