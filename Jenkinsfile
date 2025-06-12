pipeline {
    agent any

    stages {
        stage('Pull Apache Image') {
            steps {
                script {
                    sh 'docker pull httpd:latest'
                }
            }
        }

        stage('Run Apache Container') {
            steps {
                script {
                    sh '''
                    docker rm -f apache-server || true
                    docker run -d --name apache-server -p 80:80 httpd:latest
                    '''
                }
            }
        }

        stage('Check Apache Container Status') {
            steps {
                script {
                    sh 'docker ps -f name=apache-server'
                }
            }
        }
        stage('Kill the Container') {
            steps {
                script {
                    sh 'docker rm -f apache-server'

                }
            }
        }
        stage('Check Apache Container Status') {
            steps {
                script {
                    sh 'docker ps -f name=apache-server'
                }
            }
        }
    }
}
