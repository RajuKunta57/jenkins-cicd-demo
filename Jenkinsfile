
pipeline {
    agent any

    environment {
        SONAR_ORGANIZATION = 'rajukunta57'
        SONAR_PROJECT_KEY = 'RajuKunta57_jenkins-cicd-demo'
    }

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

        stage('Maven Build and Test') {
            steps {
                sh 'mvn clean verify'
            }
        }

        stage('SonarQube Cloud Analysis') {
            steps {
                withCredentials([string(
                    credentialsId: 'sonarcloud-token',
                    variable: 'SONAR_TOKEN'
                )]) {
                    sh '''
                        mvn org.sonarsource.scanner.maven:sonar-maven-plugin:sonar \
                          -Dsonar.organization=$SONAR_ORGANIZATION \
                          -Dsonar.projectKey=$SONAR_PROJECT_KEY \
                          -Dsonar.host.url=https://sonarcloud.io \
                          -Dsonar.token=$SONAR_TOKEN
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Build and SonarQube analysis completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check the stage logs.'
        }
    }
}
