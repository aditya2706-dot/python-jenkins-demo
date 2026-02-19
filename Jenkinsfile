pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://gitlab.com/aditya2706-dot/project-1.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run App') {
            steps {
                sh 'python3 app.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }
    }

    post {
        failure {
            emailext(
                subject: "❌ Python Pipeline Failed",
                body: "Build ${env.BUILD_NUMBER} failed",
                to: "yourgmail@gmail.com"
            )
        }
    }
}
