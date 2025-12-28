pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                #!/bin/bash
                echo "Building from branch: ${BRANCH_NAME}"

                # Build docker image using pre-built container
                docker build -t webapp:${BRANCH_NAME} .
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                #!/bin/bash
                echo "Testing branch: ${BRANCH_NAME}"

                # Simple test: verify code exists inside container
                docker run --rm webapp:${BRANCH_NAME} ls /var/www/html
                '''
            }
        }

        stage('Prod') {
            when {
                branch 'master'
            }
            steps {
                sh '''
                #!/bin/bash
                echo "Deploying to production"

                # Stop existing container if running
                docker stop webapp-prod || true
                docker rm webapp-prod || true

                # Run production container
                docker run -d \
                --name webapp-prod \
                -p 80:80 \
                webapp:master
                '''
            }
        }
    }
}
