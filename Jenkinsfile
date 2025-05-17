@Library('shared-library')_
pipeline {
    agent {label 'django' }

    stages {
        stage('Code') {
            steps {
                script{
                    clone("https://github.com/Aakanshi-garg/django-notes-app.git" , "main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    build("aakanshigarg" , "notes-app" , "latest")
                }
                
            }
        }
        stage('dockerHub_push') {
            steps {
                script{
                    docker_push("aakanshigarg" , "notes-app" , "latest")
                }
            }
        }

        stage('Deploy') {
            steps {
                sh "docker compose down"
                sh "docker compose up -d --build"
             
            }
        }
    }
}
