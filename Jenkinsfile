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
                withDotNet {
                    sh 'dotnet build "Jenkins Example/Jenkins Example.csproj"'
                }
            }
        }

        stage('Test') {
            steps {
                withDotNet {
                    sh 'dotnet test "Jenkins Example/Jenkins Example.csproj"'
                }
            }
        }
    }
}

def withDotNet(body) {
    tool 'dotnet'
    body()
}