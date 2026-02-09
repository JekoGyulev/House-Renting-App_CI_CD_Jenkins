pipeline {
    agent any

    triggers {
        githubPush();
    }

    stages {

        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }

            post {
                success {
                    echo 'Successfully restored dependencies'
                }
            }
        }

        stage('Build App') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build'
            }
        }
        

    }

    post {
        success {
            echo "Workflow completed successfully"
        }

        failure {
            echo "Workflow failed"
        }

        always {
            echo "Workflow finished"
        }
    }
}