pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    registryUrl 'https://r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp'
                    registryCredentialsId '8837eed2-4720-449f-b3e9-926944d8ef6f'
                    image 'r-airbus-docker-local.artifactory.2b82.aws.cloud.airbus.corp/2e28-acs-eks/images/node:v3.8.1'
                    args '-u root:root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
