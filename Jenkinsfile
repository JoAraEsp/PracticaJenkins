pipeline {
    agent any

    stages {
        stage('Build and Run') {
            steps {
                script {
                    // Usa 'docker compose' en lugar de 'docker-compose'
                    sh 'docker compose up --build -d'
                }
            }
        }
        stage('Test') {
            steps {
                // Asumiendo que quieres hacer algún test, como un simple curl para verificar que el servidor responde.
                sh 'curl -m 5 http://localhost:3000'
            }
        }
        stage('Cleanup') {
            steps {
                script {
                    // Usa 'docker compose down' para limpiar después de los tests
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
