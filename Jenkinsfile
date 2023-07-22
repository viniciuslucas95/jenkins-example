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
                sh 'docker build -t viniciuslucas95/jenkins-example:${env.BUILD_ID} -f "Jenkins Example/Dockerfile" "Jenkins Example"'
            }
        }

        stage('Push image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                    sh "docker push viniciuslucas95/jenkinsexample:${env.BUILD_ID}"
                }
            }
        }
    }
}