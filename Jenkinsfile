pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/d2arshan/EPGC-ASSIGNMENT2', branch: 'gh-pages'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                  echo "Building Docker image..."
                  docker build -t myapp:latest .
                '''
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                  echo "Removing old container if exists..."
                  docker rm -f myapp || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                  echo "Running new container..."
                  docker run -d --name myapp -p 99:80 myapp:latest
                '''
            }
        }
    }
}
