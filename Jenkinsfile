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
                // Jenkins (Windows) tells WSL (Ubuntu) to build the image
                bat 'wsl docker build -t q5 .'
            }
        }
        stage('Deploy Docker Container') {
            steps {
                // Stops and removes the old container if it exists
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    bat 'wsl docker stop running-node-app'
                    bat 'wsl docker rm running-node-app'
                }
                // Runs the new container
                bat 'wsl docker run -d -p 3050:3000 --name running-node-app q5'
            }
        }
    }
}
