pipeline {
    agent {
        docker {
            label 'docker-agent'
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
                branch 'master'
            }
            steps {
                sh """
                    mvn clean package
                """
            }
        }
    }
}