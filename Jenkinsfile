pipeline{
    agent any
    stages {
        stage("Build") {
            step {
                echo 'this is building phase'
            }
            post {
                success {
                    echo 'Build succeeded'
                }
            }
        }
        stage("Deploy") {
            step {
                echo 'this is deployment phase'
            }
            post {
                always {
                    echo 'Always'
                }
                success {
                    echo 'Archiving artifacts'
                }
            }
        }
    }
}