pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Bhargava7032/task.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t web .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
               docker ps -q --filter "name=web" | xargs -r docker rm -f
               docker run -d -p 8081:80 --name web web
                '''
            }
        }
    }
}

