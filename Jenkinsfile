pipeline {
    agent any

    stages {

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
                    bat 'docker run -d --name dev-container -p 5000:5000 flaskapp'
                }
            }
        }

        stage('Run Test Container') {
            steps {
                dir('Program 9') {
                    bat 'docker run -d --name test-container -p 5001:5000 flaskapp'
                }
            }
        }
    }
}
