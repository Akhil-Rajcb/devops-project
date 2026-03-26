pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Anly2004/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mywebapp .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop mycontainer || true
                docker rm mycontainer || true
                docker run -d -p 80:80 --name mycontainer mywebapp
                '''
            }
        }
    }
}
