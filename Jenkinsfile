pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t omarhafiz/k8s-python-app:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push omarhafiz/k8s-python-app:latest'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'export KUBECONFIG=/home/ubuntu/.kube/config && kubectl apply -f k8s/'
                sh 'export KUBECONFIG=/home/ubuntu/.kube/config && kubectl rollout restart deployment python-app'
            }
        }
    }
}
