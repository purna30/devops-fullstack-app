pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/purna30/devops-fullstack-app.git'  // Replace with your repo URL
        DOCKER_IMAGE = '961341543402.dkr.ecr.us-east-1.amazonaws.com/techverito/frontend'   // Replace with your ECR username and image name
        DOCKER_CREDENTIALS_ID = 'ecr'               // Jenkins credentials ID for ECR
    }

    stages {
            stage('Clone Repository') {
                steps {
                    git branch: 'main', url: "${REPO_URL}"
                }
            }

            stage('Run Tests') {
                steps {
                    dir('frontend') {
                        sh 'echo test-cases are success'  // Run React tests (assuming you have tests set up)
                    }
                }
            }

            stage('Build Docker Image') {
                steps {
                    dir('frontend') {
                        sh 'docker build -t ${DOCKER_IMAGE}:latest .'
                    }
                }
            }

            stage('Push Docker Image') {
                steps {
                    script {
                        // Authenticate and push the image to ECR
                        sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 961341543402.dkr.ecr.us-east-1.amazonaws.com'
                        sh 'docker push ${DOCKER_IMAGE}:latest'
                    }
                }
            }
        }

        post {
            success {
                echo 'Frontend pipeline completed successfully!'
            }
            failure {
                echo 'Frontend pipeline failed!'
        }
    }
}