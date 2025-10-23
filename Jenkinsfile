pipeline {
    agent any
    stages {
        stage('code') {
            steps {
                echo 'code cloning'
                git url: "https://github.com/ayushrathore09/django-notes-app.git", branch: "main"
            }
        }

        stage('build') {
           steps {
                echo 'building the image.'
                sh 'docker build -t ayush:latest .'
            }
        }
        
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId:'dockerHub',usernameVariable:'dockerHubUser',passwordVariable:'dockerHubPass')]){
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker tag ayush:latest ${env.dockerHubUser}/ayush:21-10-2025"
                    sh "docker push ${env.dockerHubUser}/ayush:21-10-2025"
                }
            }
        }

        stage ('Deploy the code'){
            steps{
                sh "docker run -d -p 8000:8000 ${env.dockerHubUser}/ayush:21-10-2025"
            }
        }
    }
}