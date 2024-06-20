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
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                    echo "Checking build/index.html is exist?"
                    [ -f build/index.html ] && echo "index.html exists" || echo "index.html does not exist"
                    echo "Running test.."
                    npm test
                '''
            }
        }
    }
}
