pipeline {
    agent any

    environment {
        IMAGE_NAME = 'luannv67922/php'
        DOCKERHUB_CREDENTIALS = 'dockerhub' // thêm credential này trong Jenkins UI
    }

    stages {

        stage('Checkout Source') {
            steps {
                git branch: 'main', url: 'https://github.com/luannv6792/php.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${DOCKERHUB_CREDENTIALS}") {
                        dockerImage.push("${BUILD_NUMBER}")
                        dockerImage.push("latest")
                    }
                }
            }
        }

/*        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh "kubectl apply -f k8s/deployment.yml"
                    sh "kubectl apply -f k8s/service.yml"
                    sh "kubectl rollout status deployment/phpinfo-app-deployment"
                }
            }
        }
    }
*/
    post {
        success {
            echo "✅ Deployment completed successfully!"
        }
        failure {
            echo "❌ Deployment failed!"
        }
    }
}
