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

       /*stage('Testing Application') {
            steps {
                sh''' 
                composer install --no-dev --optimize-autoloader
                composer require fakerphp/faker --dev
                php artisan test
                '''
            }
        }*/

       stage('Code Quality Analysis') {
            steps {
                sh''' 
                sonar-scanner \
                 -Dsonar.projectKey=laravel-blog \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://172.23.5.22:9000 \
                -Dsonar.token=sqp_de6881ca66747a14babf144a81a70ac4ef5a713b
                
                '''
            }
        }

       
       
       
       
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
