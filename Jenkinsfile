pipeline {
    agent {label'devops-01-maydian'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/maydiansunarlie/laravel-blog.git'
            }
        }
        
        stage('copy env variables') {
            steps {
                sh '''
                cp /usr/share/nginx/html/laravel-blog/.env .env
                '''
            }
        }

       /* stage('Testing Application') {
            steps {
                sh''' 
                composer install --no-dev --optimize-autoloader
                composer require fakerphp/faker --dev
                php artisan test
                '''
            }
        }*/

        stage('Build Container Image') {
            steps {
                sh '''
                docker compose build
                '''
            }
        }
        stage('Deploy Container Application') {
            steps {
                sh '''
                docker compose up -d
                '''
            }
        }
        
        /*stage('Publish Container Image') {
            steps {
                echo 'Publish Container Image'
            }
        }*/
        
        stage('Publish Container Image') {
            steps {
                sh '''
                docker compose push
                '''
            }
        }
    }
}
