pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    echo "Copying files to Nginx container..."
                    sh 'docker cp index.html myjavaapp:/usr/share/nginx/html/'
                }
            }
        }
    }
}
