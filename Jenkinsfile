@Library("Shared") _
pipeline {
    agent any
    stages {
        stage('code') {
            steps {
                script{
                    code_clone("https://github.com/ayushrathore09/django-notes-app.git", "main")
                }
            //     echo 'code cloning'
            //     git url: "https://github.com/ayushrathore09/django-notes-app.git", branch: "main"
                echo "code cloned successfully"
            }
        }

        stage('build') {
           steps {
               script{
                    code_build("ayush:latest")
               }
                // echo 'building the image.'
                // sh 'docker build -t ayush:latest .'
            }
        }
        
        stage('push') {
            steps {
                // withCredentials([usernamePassword(credentialsId:'dockerHub',usernameVariable:'dockerHubUser',passwordVariable:'dockerHubPass')]){
                //     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                //     sh "docker tag ayush:latest ${env.dockerHubUser}/ayush:21-10-2025"
                //     sh "docker push ${env.dockerHubUser}/ayush:21-10-2025"
                //     // use "" if using ${env.var} or use '' if using ${var}
                // }
                script{
                    code_push("ayush:latest", "ayushrathore09")
                }
            }
        }

        stage ('Deploy the code'){
            steps{
                sh "docker compose down && docker compose up -d"
                //sh "docker run -d -p 8000:8000 ayush:latest"
            }
        }
    }
}