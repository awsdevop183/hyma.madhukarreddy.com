pipeline {
    agent any

    stages {
        stage('Create Docker image') {
            steps {
                sh 'docker build -t hyma:v1 .'
            }
        }
        stage('Deleting old container') {
            steps {
                sh 'docker rm -f hyma'
            }
        }
        
        
        stage('Create a container') {
            steps {
                sh 'docker run -d --name hyma -p 84:80 -v /home/rishi/hyma:/usr/share/nginx/html hyma:v1'
            }
        }
        stage('Dangling Image remove') {
            steps {
                sh 'docker rmi $(docker images -f dangling=true)'
            }
        }
        
    }
}
