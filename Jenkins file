pipeline {
    agent {
        label 'ubuntu-latest' // This assumes you have an agent labeled 'ubuntu-latest'
    }
    triggers {
        // This triggers the pipeline on commits to the main branch
        gitlabPush branch: 'main'
    }
    environment {
        // Setup Python version or any other environment variables
        PYTHON_VERSION = '3.x'
    }
    stages {
        stage('Checkout repository') {
            steps {
                checkout scm // This checks out the current pipeline repo
            }
        }
        stage('Set up Python environment') {
            steps {
                // Assuming Python 3.x is already installed on the agent
                // You can specify the Python version if needed using a tool or script
                script {
                    if (isUnix()) {
                        sh 'python3 --version'
                    } else {
                        bat 'python3 --version'
                    }
                }
            }
        }
        stage('Install dependencies') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'make install'
                    } else {
                        bat 'make install'
                    }
                }
            }
        }
        stage('Execute tests') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'make test'
                    } else {
                        bat 'make test'
                    }
                }
            }
        }
    }
}
