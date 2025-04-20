pipeline {
    agent {label 'jenslave-new'}

    stages {
        stage('Hello') {
            agent{
                docker{
                    image 'node:18-alpine'
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
                
                echo 'Hello World'
                sh 'npm --version'
            }
        }
    }
}
