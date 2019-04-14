pipeline{
    agent any
    stages {
        stage("Build") {
            step {
                sh 'echo "this is building phase"'
            }
            post {
                success {
                    sh 'echo "Build succeeded"'
                }
            }
        }
        stage("Deploy") {
            step {
                sh 'echo "this is deployment phase"'
            }
            post {
                always {
                    sh 'echo "Always"'
                }
                success {
                    sh 'echo "Archiving artifacts"'
                }
            }
        }
    }
}