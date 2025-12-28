pipeline {
    agent any

    stages {
        stage('Build') {
           steps {
                sh '''
                #!/bin/bash
                echo "Building from branch: ${BRANCH_NAME}"
                ls -l
                '''
           }
        }

        stage('Test') {
            steps {
                echo "Testing branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Prod') {
            when {
                branch 'master'
            }
            steps {
                echo "Deploying to production"
            }
        }
    }
}
