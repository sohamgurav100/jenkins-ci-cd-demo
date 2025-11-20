pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sohamgurav100/jenkins-ci-cd-demo.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myjavaapp-image .'
            }
        }

        stage('Deploy to Nginx Container') {
            steps {
                sh 'docker rm -f myjavaapp || true'
                sh 'docker run -d -p 8081:80 --name myjavaapp nginx'
            }
        }
    }
}
