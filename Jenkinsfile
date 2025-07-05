pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the Docker image...'
                sh 'podman build -t hello-k8s .'
            }
        }

        stage('Load to Minikube') {
            steps {
                echo 'Pushing image to Minikube...'
                sh 'minikube image load hello-k8s'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying to Kubernetes...'
                sh 'kubectl apply -f deployment.yaml'
            }
        }

        stage('Access App') {
            steps {
                echo 'Exposing service...'
                sh 'minikube service hello-k8s --url'
            }
        }
    }
}
