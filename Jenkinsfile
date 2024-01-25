pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git url: 'https://github.com/Alazzze/wordpress-docker-phpmyadmin.git', branch: 'main'
                }
            }
        }
        stage('Build and Test') {
            steps {
                script {
                    sh '''
                        docker-compose -f docker-compose.yml down -v
                        docker-compose -f docker-compose.yml up --build --detach
                        docker-compose -f docker-compose.yml logs -f --tail="all" --timestamps --no-color | timeout 10m cat
                    '''
                }
            }
        }
    }
}
