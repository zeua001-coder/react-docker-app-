pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/zeua001-coder/react-docker-app-.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t zeua001/reactprod .'
            }
        }

        stage('Deploy') {
            steps {
                // Elimina contenedor previo si existe
                sh 'docker rm -f reactprod || true'
                // Levanta nuevo contenedor
                sh 'docker run -d --name reactprod -p 80:80 zeua001/reactprod'
            }
        }
    }
}
