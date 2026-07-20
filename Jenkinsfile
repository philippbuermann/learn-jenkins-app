pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    registryUrl 'https://r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp'
                    registryCredentialsId 'artifactory-docker-creds'
                    image 'r-ce96-atip-docker-local.artifactory.2b82.aws.cloud.airbus.corp/alpine:3.19'
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
