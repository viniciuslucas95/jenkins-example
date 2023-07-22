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

        stage('Build image') {
            steps {
                script {
                    def dockerImage = docker.build(
                        "viniciuslucas95/jenkins-example:${env.BUILD_ID}",
                        "-f ./Jenkins Example/Dockerfile",
                        "./Jenkins Example"
                    )
                }
            }
        }
    }
}