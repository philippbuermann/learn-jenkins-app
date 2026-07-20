pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    registryUrl 'https://r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp'
                    registryCredentialsId '8837eed2-4720-449f-b3e9-926944d8ef6f'
                    image 'r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp/alpine:3.19'
                    reuseNode true
                }
            }
            steps {
                powershell '''
                    $ErrorActionPreference = "Stop"
                    Get-ChildItem -Force

                    nvs use artifactory/25.8.1/x64
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    Get-ChildItem -Force
                '''
            }
        }
    }
}
