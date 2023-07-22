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
                sh 'dotnet add "Jenkins Example" package xunit.runner.console'
                sh 'dotnet restore "Jenkins Example/Jenkins Example.csproj"'
                sh 'dotnet test "Jenkins Example/Jenkins Example.csproj"'
            }
        }
    }
}