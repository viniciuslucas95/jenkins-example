pipeline {
    agent any

    environment {
        DOTNET_VERSION = "6.0.100"
        DOTNET_INSTALL_DIR = "/var/jenkins_home/tools/io.jenkins.plugins.dotnet.DotNetSDK"
    }

    stages {
        stage('Download and Install .NET SDK') {
            steps {
                script {
                    if (!fileExists(DOTNET_INSTALL_DIR)) {
                        sh "mkdir -p ${DOTNET_INSTALL_DIR}"

                        sh "curl -L -o dotnet-sdk.tar.gz https://dotnetcli.azureedge.net/dotnet/sdk/${DOTNET_VERSION}/dotnet-sdk-${DOTNET_VERSION}-linux-x64.tar.gz"
                        sh "tar -xzf dotnet-sdk.tar.gz -C ${DOTNET_INSTALL_DIR}"
                        sh "rm dotnet-sdk.tar.gz"

                        sh "echo 'export PATH=${DOTNET_INSTALL_DIR}:${PATH}' >> ~/.bashrc"
                        sh "source ~/.bashrc"
                    } else {
                        echo "The .NET SDK is already installed at ${DOTNET_INSTALL_DIR}. Skipping download and installation."
                    }

                    sh "dotnet --version"
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
                sh 'dotnet build "Jenkins Example/Jenkins Example.csproj"'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test "Jenkins Example/Jenkins Example.csproj"'
            }
        }
    }
}