pipeline {
    agent any

    when {
        branch 'feature-ci-pipeline'
    }

    stages {
        stage('Restore dependencies') {
            steps {
                // Restore project dependencies
                bat 'dotnet restore'
            }
        }
        stage('Build project') {
            steps {
                // Build the project without restoring dependencies again
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            steps {
                // Run tests without rebuilding, and set verbosity
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
