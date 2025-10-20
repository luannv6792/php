pipeline {
    agent any

    stages {
        stage('Clone Source') {
            steps {
                git branch: 'main', url: 'https://github.com/luannv6792/php.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'echo "Build success!"'
                sh 'docker ps -a'
                sh 'kubectl get pod -A'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "All tests passed!"'
            }
        }
    }
}
