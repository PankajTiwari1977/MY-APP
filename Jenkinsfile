pipeline {
    agent any

    // environment {
    //     NODE_ENV = 'production'
    // }

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

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'build/**', followSymlinks: false
            }
        }
    }
}
