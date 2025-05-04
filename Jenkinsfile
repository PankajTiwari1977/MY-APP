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
                    docker build -t pankajdevops2403/react-app:v1 .
                    docker push pankajdevops2403/react-app:v1 
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
