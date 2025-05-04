pipeline {
    agent any

     stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build App') {
            steps {
                sh 'npm run build'
            }
        }
        stage('minikube docker build docker image') {
            steps {
                sh 'eval $(minikube docker-env)'
            }
            steps {
                sh 'docker build -t react-app:latest .'
            }

        }
        stage('deploy my app') {
            steps {
                sh 'kubectl apply -f deploy/react-deployment.yaml'
            }
            steps {
                sh 'kubectl apply -f deploy/react-service.yaml'
            }
    }
}
