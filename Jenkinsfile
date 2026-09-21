pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t maven-practice:1.0 .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker rm -f maven-app || true'
                sh 'docker run --name maven-app maven-practice:1.0'
            }
        }
    }
}
