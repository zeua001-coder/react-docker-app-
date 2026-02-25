pipeline {
    agent {
        docker {
            image 'node:20'
            args '-u root'
        }
    }

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

