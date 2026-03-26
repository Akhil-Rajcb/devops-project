pipeline {
    agent {
        label 'built-in'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Akhil-Rajcb/devops-project.git'
            }
        }

        stage('Build') {
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
