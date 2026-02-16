pipeline {
    agent any
    
    tools {
        maven 'Maven-3'
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/vivekkumar1611/demo-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Stop Old App') {
            steps {
                sh 'docker rm -f demo-app || true'
            }
        }

        stage('Run App on 8081') {
            steps {
                sh 'docker build -t demo-app .'
                sh 'docker run -d --name demo-app -p 8081:8081 demo-app'
            }
        }
    }
}
