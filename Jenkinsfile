pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0'
    }

    stages {
        stage('Install .NET SDK') {
            steps {
                script {
                    sh "curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin --version ${env.DOTNET_VERSION}"
                    sh "export PATH=\"$HOME/.dotnet\":\$PATH"
                }
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
                sh 'dotnet test Jenkins Example/Jenkins Example.csproj'
            }
        }
    }
}