pipeline {
    agent any

    environment {
        PATH = "C:\\Users\\shash\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin;C:\\Windows\\System32;${env.PATH}"
    }

    stages {

        stage('Check Docker') {
            steps {
                bat '''
                    echo Checking Docker...
                    docker --version
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'dir'
                bat 'docker build -t flaskapp .'
            }
        }

        stage('Run Dev Container') {
            steps {
                bat 'docker rm -f flaskapp 2>NUL || exit /B 0'
                bat 'docker run -d --name flaskapp -p 5000:5000 flaskapp'
            }
        }

        stage('Run Test Container') {
            steps {
                bat 'docker run --rm flaskapp'
            }
        }
    }
}