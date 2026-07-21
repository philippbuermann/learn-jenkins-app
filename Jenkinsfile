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
                    npm ci 2>&1 || true
                    echo "=== NPM DEBUG LOGS ==="
                    cat /tmp/.npm-cache/_logs/*.log 2>/dev/null || echo "No log files found"
                    echo "=== END NPM DEBUG LOGS ==="
                '''
            }
        }
    }
}
