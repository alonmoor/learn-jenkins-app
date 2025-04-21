pipeline {


    
    agent {label 'vjenslave'}
 
 
 
    stages {
       stage('Clean Workspace') {
            steps {
                deleteDir() // Deletes all files in the workspace
            }
        }

        /*
 
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

                '''

            }

        }

        */
 
        stage('Test') {

            agent {

                docker {

                    image 'node:18-alpine'

                    reuseNode true

                }

            }
 
            steps {

                sh '''

                    #test -f build/index.html

                    npm test

                '''

            }

        }
 
        stage('E2E') {

            agent {

                docker {

                    image 'mcr.microsoft.com/playwright:v1.39.0-jammy'

                    reuseNode true

                }

            }
 
            steps {

                sh '''

                    npm install serve

                    node_modules/.bin/serve -s build &

                    sleep 10

                    npx playwright test
                    npm install --save-dev jest-junit

                '''

            }

        }

    }
 
    post {

        always {
             
            junit 'jest-results/junit.xml'

        }

    }

}

 
