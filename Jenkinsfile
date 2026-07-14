pipeline {

    agent {
        label 'ubuntu'
    }

    tools {
        maven 'maven'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Maven project...'

                sh '''
                    mvn clean compile
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'

                sh '''
                    mvn test
                '''
            }
        }
    }

    post {

        always {
            archiveArtifacts artifacts: 'target/**/*', fingerprint: true
        }

        success {
            echo 'Build completed successfully.'
        }

        failure {
            echo 'Build failed.'
        }
    }
}
