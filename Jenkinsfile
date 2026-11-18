
pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-docker-demo .'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'docker run --rm jenkins-docker-demo python -c "import app"'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker rm -f jenkins-demo 2>NUL'
                bat 'docker run -d --name jenkins-demo -p 5000:5000 jenkins-docker-demo'
            }
        }
    }
}
