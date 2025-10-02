pipeline {
    agent {
        docker {
            image 'node:22.20.0-alpine3.22'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building the application"'
                sh 'echo "Build artifacts created" > build-artifact.txt'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests"'
                sh 'mkdir -p test-reports'
                sh 'echo "<?xml version=\\"1.0\\" encoding=\\"UTF-8\\"?><testsuite tests=\\"3\\" failures=\\"0\\" time=\\"0.1\\"><testcase classname=\\"TestClass\\" name=\\"testMethod1\\" time=\\"0.03\\"/><testcase classname=\\"TestClass\\" name=\\"testMethod2\\" time=\\"0.04\\"/><testcase classname=\\"TestClass\\" name=\\"testMethod3\\" time=\\"0.03\\"/></testsuite>" > test-reports/results.xml'
            }
        }
    }
    post {
        always {
            junit 'test-reports/**/*.xml'
            archiveArtifacts artifacts: '*.txt', allowEmptyArchive: true
        }
    }
}
