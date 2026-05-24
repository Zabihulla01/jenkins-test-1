pipeline {
    agent any
    environment{
        DOCKER = credentials('Docker')
    }
    stages{
        stage('clone'){
            steps{
                git branch: 'main' , url: 'https://github.com/Zabihulla01/jenkins-test-1.git'
            }
        }
        stage('build'){
            steps{
                sh 'docker rm -f abc'
                sh 'docker build -t zabihulla01/app-test .'
            }
        }
        stage('login'){
            steps{
                sh 'echo $DOCKER_PSW | docker login -u $DOCKER_USR --password-stdin'
            }
        }
        stage('push docker hub'){
            steps{
                sh 'docker push zabihulla01/app-test'
            }
        }
        stage('deployed'){
            steps{
                sh 'docker run -d -p 80:80 --name abc zabihulla01/app-test'
            }
        }
    }
}
