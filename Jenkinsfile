pipeline {
    agent any

    stages {
        stage('Restore') {
            steps {
                echo 'Restoring NuGet packages...'
                bat 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'dotnet build --no-restore --configuration Release'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
        success {
            echo 'Build and test succeeded.'
        }
        failure {
            echo 'Build or test failed. Check the logs for details.'
        }
    }
}
