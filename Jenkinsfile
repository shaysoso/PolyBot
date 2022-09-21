pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo building...'
            }
        }
        stage('Stage II') {
            steps {
                sh '''
                aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 352708296901.dkr.ecr.eu-central-1.amazonaws.com
                docker build -t shaybot:0.0.$BUILD_NUMBER  .
                docker tag shaybot:0.0.$BUILD_NUMBER  352708296901.dkr.ecr.eu-central-1.amazonaws.com/shaybot:0.0.$BUILD_NUMBER
                docker push 352708296901.dkr.ecr.eu-central-1.amazonaws.com/shaybot:0.0.$BUILD_NUMBER
                '''
            }
        }
        stage('Stage III ...') {
            steps {
                sh 'echo echo "stage III..."'
            }
        }
    }
}