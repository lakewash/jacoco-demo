pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/Cellar/maven/3.9.11/libexec/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Code Coverage Report') {
            steps {
                echo 'Generating JaCoCo report...'
                sh 'mvn jacoco:report'
            }
        }
    }

    post {
        success {
            echo '✅ Build and tests completed successfully!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
