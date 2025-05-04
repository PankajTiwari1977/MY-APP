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
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                        sh """
                            echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                            docker build -t pankajdevops2403/react-app:latest .
                            docker push pankajdevops2403/react-app:latest
                        """
                    }
                }
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
