pipeline {

    agent any

    stages {

        stage('Clone Repository') {

            steps {

                git 'https://github.com/username/Website-CICD.git'

            }

        }

        stage('Build Docker Image') {

            steps {

                sh 'docker build -t website .'

            }

        }

        stage('Stop Existing Container') {

            steps {

                sh '''
                docker stop website || true
                docker rm website || true
                '''
            }

        }

        stage('Deploy Container') {

            steps {

                sh '''
                docker run -d \
                --name website \
                -p 80:80 \
                website
                '''
            }

        }

    }

}
