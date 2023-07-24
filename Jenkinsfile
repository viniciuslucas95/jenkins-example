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
                    sh 'docker build -t viniciuslucas95/jenkins-example -f "Jenkins Example/Dockerfile" "Jenkins Example"'
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                        sh "docker push viniciuslucas95/jenkins-example"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh "kubectl apply -f Deployment.yaml"
            }
        }
    }
}