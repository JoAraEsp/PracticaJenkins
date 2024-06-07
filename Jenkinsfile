pipeline {
    agent any

    stages {
        stage('Build and Run') {
            steps {
                script {
                    sh 'docker compose up --build -d'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'curl -m 5 http://localhost:3000'
            }
        }
        stage('Cleanup') {
            steps {
                script {
                    sh 'docker compose down'
                }
            }
        }
    }

    post {
        always {
            echo 'Este mensaje siempre se ejecutará al final del pipeline.'
        }
        success {
            echo 'El pipeline se ejecutó correctamente!'
        }
        failure {
            echo 'El pipeline falló en algún paso.'
        }
    }
}
