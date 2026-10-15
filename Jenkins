
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    environment {
        IMAGE_NAME = 'flask-cicd-app:1.0'
        CONTAINER_NAME = 'flask-cicd-container'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh '''
                    docker run --rm \
                      --entrypoint python \
                      -v "$PWD:/workspace" \
                      -w /workspace \
                      python:3.12-slim \
                      -m pip --version
                '''
                sh '''
                    docker run --rm \
                      -v "$PWD:/workspace" \
                      -w /workspace \
                      python:3.12-slim \
                      sh -c "pip install -r requirements.txt && python -m pytest -v"
                '''
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t "$IMAGE_NAME" .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f "$CONTAINER_NAME" 2>/dev/null || true
                    docker run -d \
                      --name "$CONTAINER_NAME" \
                      -p 5000:5000 \
                      "$IMAGE_NAME"
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                    docker exec "$CONTAINER_NAME" \
                      python -c "import urllib.request; r=urllib.request.urlopen('http://127.0.0.1:5000/health', timeout=10); print(r.read().decode()); assert r.status == 200"
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed. Check Console Output.'
        }
    }
}
