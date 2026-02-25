pipeline {
    agent any

    stages {

        stage('Instalar dependencias') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                }
            }
        }

        stage('Ejecutar Tests') {
            steps {
                dir('frontend') {
                    sh 'npm test -- --watchAll=false'
                }
            }
        }

        stage('Build') {
            steps {
                dir('frontend') {
                    sh 'npm run build'
                }
            }
        }

    }
}
