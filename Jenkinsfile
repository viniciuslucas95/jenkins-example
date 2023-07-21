pipeline {
    agent any

    tools {
        dotnet 'dotnet'
    }

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
                sh 'dotnet build "Jenkins Example/Jenkins Example.csproj"'
            }
        }
    }
}