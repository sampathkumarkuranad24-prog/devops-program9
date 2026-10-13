
pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flaskapp .'
            }
        }

        stage('Run Dev Container') {
            steps {
                bat 'docker rm -f dev-container 2>NUL || exit /b 0'
                bat 'docker run -d --name dev-container -p 5000:5000 flaskapp'
            }
        }

        stage('Run Test Container') {
            steps {
                bat 'docker rm -f test-container 2>NUL || exit /b 0'
                bat 'docker run -d --name test-container -p 5001:5000 flaskapp'
            }
        }
    }
}
