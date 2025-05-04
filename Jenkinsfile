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
                    echo "Setting Docker env from Minikube"
                    eval $(minikube docker-env) || exit 1
                    docker info
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
