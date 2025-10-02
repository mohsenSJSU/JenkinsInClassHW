pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building the application..."'
                sh 'sleep 1'
                sh 'echo "Build completed"'
            }
        }
        stage('Deploy') {
            steps {
                retry(3) {
                    sh 'echo "Attempting deployment..." && sleep 1'
                }
                timeout(time: 3, unit: 'MINUTES') {
                    sh 'echo "Running health check..." && sleep 2 && echo "Health check passed"'
                }
            }
        }
    }
}
