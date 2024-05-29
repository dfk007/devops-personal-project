pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('my-node-app')
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-credentials') {
                        docker.image('my-node-app').push('latest')
                    }
                }
            }
        }
    }
}
