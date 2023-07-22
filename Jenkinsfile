pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build "Jenkins Example/Jenkins Example.csproj"'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet add "Jenkins Example" package Microsoft.NET.Test.Sdk'
                sh 'dotnet test "Jenkins Example/Jenkins Example.csproj"'
            }
        }
    }
}