pipeline {
    agent any

    stages {
        stage('Check Docker') {
            steps {
                bat 'where docker'
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('Program 9') {
                    bat 'docker build -t flaskapp .'
                }
            }
        }

        stage('Run Dev Container') {
            steps {
                dir('Program 9') {
                    bat 'docker run -d --name flaskapp -p 5000:5000 flaskapp'
                }
            }
        }

        stage('Run Test Container') {
            steps {
                dir('Program 9') {
                    bat 'docker run --rm flaskapp'
                }
            }
        }
    }
}
