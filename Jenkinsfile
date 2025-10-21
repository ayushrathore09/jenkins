pipeline {
    agent {label 'vinod'}
    stages {
        stage('code') {
            steps {
                echo 'cloning the code.'
                git url: "https://github.com/ayushrathore09/django-notes-app.git", branch: "main"
            }
        }

        stage('build') {
           steps {
                echo 'building the image.'
                sh 'docker build -t django-notes-app:21-10-2025 .'
            }
        }
        
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId:'dockerhub',usernameVariable:'dockerhubUser',passwordVariable:'dockerhubPass')]){
                    sh 'docker login -u ${env.dockerhubUser} -p ${env.dockerhubPass}'
                    sh 'docker tag django-notes-app:21-10-2025 ${env.dockerhubUser}/django-notes-app:21-10-2025'
                    sh 'docker push ayushrathore09/django-notes-app:21-10-2025'
                }
            }
        }
    }
}