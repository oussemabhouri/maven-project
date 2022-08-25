pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
        }
    }
    stages {
        stage('test') {
            when {
                changeRequest()
            }
            steps {
                sh """
                    mvn test
                """
            }
        }
        stage('build and deploy') {
            when {
                master()
            }
            steps {
                sh """
                    mvn clean package
                """
            }
        }
    }
}