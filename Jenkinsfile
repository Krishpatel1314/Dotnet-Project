pipeline {
    agent any
    
    environment {
        DOTNET_ROOT = "/usr/share/dotnet"  // Update path if necessary
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Krishpatel1314/Dotnet-Project.git'
            }
        }

        stage('Restore Dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --configuration Release'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'dotnet test --logger trx'
            }
        }

        stage('Publish Artifacts') {
            steps {
                sh 'dotnet publish -c Release -o ./publish'
            }
        }

    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}