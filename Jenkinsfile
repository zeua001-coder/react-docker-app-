pipeline {
    agent {
        docker {
            image 'node:20'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

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
                sh 'docker rm -f reactprod || true'
                sh 'docker run -d --name reactprod -p 80:80 zeua001/reactprod'
            }
        }
    }
}
