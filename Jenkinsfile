
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Buscando codigo do GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Construindo imagem Docker...'
                sh 'docker build -t minha-aplicacao:latest .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Atualizando site...'
                sh 'docker rm -f meu-site || true'
                sh 'docker run -d --name meu-site --restart unless-stopped -p 127.0.0.1:8080:80 minha-aplicacao:latest'
            }
        }
    }
}
