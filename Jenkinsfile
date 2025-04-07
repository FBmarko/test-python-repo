pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t my-python-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop my-python-app || true'
                sh 'docker rm my-python-app || true'
                sh 'docker run -d -p 5000:5000 --name my-python-app my-python-app'
            }
        }
    }
}