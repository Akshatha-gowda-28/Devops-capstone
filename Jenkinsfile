pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git branch: "${BRANCH_NAME}", url: 'https://github.com/hshar/website.git'
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Testing application'
            }
        }
        stage('Prod') {
            when { branch 'master' }
            steps {
                sh 'docker run -d -p 80:80 webapp:${BUILD_NUMBER}'
            }
        }
    }
}
