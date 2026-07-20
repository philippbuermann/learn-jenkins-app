pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    //registryUrl 'https://r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp'
                    //registryCredentialsId '8837eed2-4720-449f-b3e9-926944d8ef6f'
                    //mage 'r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp/alpine:3.19'
                    image 'node:18-alpine'
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
