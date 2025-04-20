pipeline {

node {
    echo "JAVA_HOME: ${env.JAVA_HOME}"
    sh "${env.JAVA_HOME}/bin/java -version"
}

    
    agent {label 'vjenslave'}
 
    stages {
        stage('Hello2') {
          steps{
              echo "Hello"
          }   
        }  
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
