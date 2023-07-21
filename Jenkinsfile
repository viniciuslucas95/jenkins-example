pipeline {
    agent any

    tools {
        dotnet '.NET SDK'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build Jenkins Example/Jenkins Example.csproj'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test Jenkins Example/Jenkins Example.Tests.csproj'
            }
        }
    }
}