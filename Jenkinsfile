pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub + Jenkins!'
            }
        }

        stage('Show Files') {
            steps {
                sh 'ls -la'
            }
        }
    }
}
