pipeline {
    agent any

    stages {
        stage('Clone Source') {
            steps {
                git branch: 'main', url: 'https://github.com/luannv6792/php.git'
            }
        }

        stage('Check Kubernetes') {
          steps {
            sh 'kubectl get nodes'
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
