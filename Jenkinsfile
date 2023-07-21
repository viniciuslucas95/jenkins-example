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
                def dotnetTool = tool 'dotnet'
                sh "${dotnetTool}/dotnet build \"Jenkins Example/Jenkins Example.csproj\""
            }
        }

        stage('Test') {
            steps {
                def dotnetTool = tool 'dotnet'
                sh "${dotnetTool}/dotnet build \"Jenkins Example/Jenkins Example.csproj\""
            }
        }
    }
}