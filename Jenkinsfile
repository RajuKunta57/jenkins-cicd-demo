pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub + Jenkins - AUTOMATIC BUILD!'
            }
        }

        stage('Show Files') {
            steps {
                sh 'ls -la'
            }
        }
    }
}
