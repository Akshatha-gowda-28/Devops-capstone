pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building from branch: ${env.BRANCH_NAME}"
                sh 'ls -l'
                sh 'docker build -t webapp:${env.BRANCH_NAME} .'
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
