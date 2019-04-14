pipeline{
    agent any
    stages{
        stage("Build"){
            echo 'this is building phase'
        }
        stage("Deploy"){
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