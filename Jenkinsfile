pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            environment {
                npm_config_cache = '/tmp/.npm-cache'
                npm_config_strict_ssl = 'false'
                NODE_TLS_REJECT_UNAUTHORIZED = '0'
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules
                    npm ci || (cat /tmp/.npm-cache/_logs/*.log && false)
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
