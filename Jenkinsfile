pipeline {
    agent any

    environment {
        IMAGE_NAME = "webapp"
    }

    stages {

        stage('Build') {
            steps {
                sh '''
                echo "Building from branch: ${BRANCH_NAME}"

                # Build docker image tagged with branch name
                docker build -t ${IMAGE_NAME}:${BRANCH_NAME} .
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                echo "Testing branch: ${BRANCH_NAME}"

                # Verify files exist inside the container
                docker run --rm ${IMAGE_NAME}:${BRANCH_NAME} ls /var/www/html
                '''
            }
        }

        stage('Prod') {
            when {
                branch 'master'
            }
            steps {
                sh '''
                echo "Deploying to production"

                # Stop & remove existing container safely
                docker stop webapp-prod || true
                docker rm webapp-prod || true

                # Run production container
                docker run -d \
                  --name webapp-prod \
                  -p 80:80 \
                  ${IMAGE_NAME}:master
                '''
            }
        }
    }
}
