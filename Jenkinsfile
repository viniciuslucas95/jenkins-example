pipeline {
    agent any

    tools {
        dotnetsdk '.NET SDK'
    }

    stages {
        stage('Install .NET SDK dependencies') {
            steps {
                sh 'apt-get update'
                sh 'apt-get install -y libicu-dev'
            }
        }

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