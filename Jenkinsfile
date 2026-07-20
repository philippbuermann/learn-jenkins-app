pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    registryUrl 'https://r-airbus-docker-local.artifactory.2b82.aws.cloud.airbus.corp'
                    registryCredentialsId '03cfdfea-1ff8-4112-8fab-7b4159c69358'
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
