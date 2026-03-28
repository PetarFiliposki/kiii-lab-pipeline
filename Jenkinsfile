pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/USERNAME/kiii-lab-pipeline'
            }
        }

        stage('Build image') {
            steps {
                bat 'docker build -t USERNAME/nginx-test .'
            }
        }

        stage('Push image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    bat 'docker login -u %USERNAME% -p %PASSWORD%'
                    bat 'docker push USERNAME/nginx-test'
                }
            }
        }
    }
}
