pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/lakewash/jacoco-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test and Code Coverage') {
            steps {
                sh 'mvn test'
            }
        }

        stage('JaCoCo Report') {
            steps {
                jacoco execPattern: '**/target/*.exec', classPattern: '**/target/classes', sourcePattern: '**/src/main/java', exclusionPattern: ''
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco()
        }
    }
}
