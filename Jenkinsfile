pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    args '-v /usr/local/share/ca-certificates/corporate-ca.crt:/tmp/corporate-ca.crt:ro'
                }
            }
            environment {
                npm_config_cache = '/tmp/.npm-cache'
                NODE_EXTRA_CA_CERTS = '/tmp/corporate-ca.crt'
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
