pipeline {
    agent any
    stages {
        stage('taking souce code from github') {
            steps {
                echo 'Hello World we are starting with github code'
                // lets use git option to clone data from repo 
                git 'https://github.com/srujanapadakanti/srujana-cisco-webUI.git'
                // my slave nodes are linux so we use sh incase of windows we use bat
                sh 'ls '
                sh  'java -version'
            }
        }
        stage('building image and create container'){
            steps {
                // using docker version 
                echo 'running docker command !..'
                sh 'docker version'
                sh 'docker-compose up -d --build'
                sh 'docker-compose ps'
                sh 'docker images'
            }
        }
        stage('testing container status by accessing page') {
            steps {
                sh 'curl -f http://localhost:1040/health.html'
                // informing
                echo 'health page is wokring fine'

            }
        }
    }
}
