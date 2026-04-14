pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Checkout Code') {
            steps {
                // Pulls the code from your GitHub repo
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                // Builds the Docker image from the Dockerfile
                bat 'docker build -t my-automated-node-app .'
            }
        }
        stage('Deploy Docker Container') {
            steps {
                // Stops and removes the old container if it exists, then runs the new one
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    bat 'docker stop running-node-app'
                    bat 'docker rm running-node-app'
                }
                bat 'docker run -d -p 3050:3000 --name running-node-app my-automated-node-app'
            }
        }
    }
}
