pipeline {
    agent {label'devops-01-maydian'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/maydiansunarlie/laravel-blog.git'
            }
        }
        stage('Testing Application') {
            steps {
                sh 'php artisan test'
            }
        }
        stage('Build Container Image') {
            steps {
                echo 'Build Container Image'
            }
        }
        stage('Deploy Container Application') {
            steps {
                echo 'Deploy Container Application'
            }
        }
        
        stage('Publish Container Image') {
            steps {
                echo 'Publish Container Image'
            }
        }
    }
}
