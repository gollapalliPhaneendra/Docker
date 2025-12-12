pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/gollapalliPhaneendra/Docker'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t sample-app:v1 .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker stop sample-app || true'
                sh 'docker rm sample-app || true'
                sh 'docker run -d -p 8080:8080 --name sample-app sample-app:v1'
            }
        }
    }

    post {
        always {
            echo "Build Completed!"
        }
    }
}
