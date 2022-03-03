pipeline {
    agent any

    stages {
        stage('Tooling version') {
            steps{
                sh 'docker --version'// Get source code from a GitHub repository
            }
        }

        stage('Docker Build') {
            steps{
                sh 'docker build -t tthang7/react-test -f ./client/Dockerfile.dev ./client'// Do your build task
            }
        }

        stage('Docker run') {
            steps{
                sh 'docker run tthang7/react-test npm test -- --coverage'// Run unit tests, integration tests, and/or e2e tests
            }
        }

        stage('after success') {
            steps{
                sh 'docker build -t tthang7/multi-client ./client'// Publish your artifacts to somewhere.
                sh 'docker build -t tthang7/multi-nginx ./nginx'
                sh 'docker build -t tthang7/multi-server ./server'
                sh 'docker build -t tthang7/multi-worker ./worker'// However, in our hands-on, you just need to print the artifact list by Linux command 'ls -la'
            }
        }
    }
}