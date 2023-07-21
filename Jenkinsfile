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
                script {
                    def dotnetTool = tool 'dotnet'
                    sh "${dotnetTool}/dotnet build \"Jenkins Example/Jenkins Example.csproj\""
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def dotnetTool = tool 'dotnet'
                    sh "${dotnetTool}/dotnet build \"Jenkins Example/Jenkins Example.csproj\""
                }
            }
        }
    }
}