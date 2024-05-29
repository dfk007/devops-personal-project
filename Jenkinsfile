pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-node-app'
        DOCKER_CREDENTIALS_ID = 'dockerhub-credentials' // ID of your DockerHub credentials
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
            }
        }
        stage('Deploy') {
    steps {
        script {
            docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') { 
                // ... (Tagging remains the same)
                sh "docker push dfk007i/my-node-app:latest"  // Replace with your actual username
            }
        }
    }
}

    }
}
