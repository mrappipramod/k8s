peline {
    agent any
    environment {
        IMAGE_NAME = "hello-k8s"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/YOUR_USERNAME/hello-k8s.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'podman build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                sh 'minikube image load $IMAGE_NAME:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }

    post {
        success {
            echo "✅ Deployed to K8s successfully!"
        }
    }
}
