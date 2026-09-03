pipeline {
    agent any

    stages {

        stage('Check Docker') {
            steps {
                bat 'where docker'
                bat 'docker --version'
                bat 'docker info'
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
                bat 'docker rm -f flaskapp 2>NUL || exit /B 0'
                bat 'docker run -d --name flaskapp -p 5000:5000 flaskapp'
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
