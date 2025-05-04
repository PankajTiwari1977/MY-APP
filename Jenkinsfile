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
                sh '''
                    export DOCKER_TLS_VERIFY="1"
                    export DOCKER_HOST="tcp://192.168.49.2:2376"
                    export DOCKER_CERT_PATH="/home/pankaj/.minikube/certs"
                    export MINIKUBE_ACTIVE_DOCKERD="minikube"
                    docker build -t react-app .
                '''
            }            
        }
        stage('deploy my app') {
            steps {
                sh 'kubectl apply -f deploy/react-deployment.yaml'
                sh 'kubectl apply -f deploy/react-service.yaml'
            }
            
        }
    }
}
