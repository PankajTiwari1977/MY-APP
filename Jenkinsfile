pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'sudo npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'sudo npm run build'
            }
        }

        stage('Serve (optional)') {
            steps {
                sh 'sudo npm install -g serve'
                sh 'sudo serve -s build -l 3000 &'
            }
        }
        stage('Display(optional)') {
            steps {
                sh 'sudo localhost:8080'
                
            }
    }

    post {
        success {
            echo 'React app built and served successfully!'
        }
        failure {
            echo 'Build failed. Check the logs.'
        }
    }
}
}