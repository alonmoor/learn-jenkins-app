pipeline {
    agent any//{label 'jenslave-new'}

    stages {
        stage('Hello') {
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps {
                echo 'Hello World'
                sh 'npm --version'
            }
        }
    }
}
