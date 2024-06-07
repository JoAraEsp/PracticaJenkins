pipeline {
    agent any

    stages {
        stage('Build and Run') {
            steps {
                script {
                    // Usar docker-compose para construir y ejecutar el contenedor
                    sh 'docker-compose up --build -d'
                }
            }
        }
        stage('Test') {
            steps {
                // Ejecutar pruebas aquí, puedes hacer peticiones HTTP a tu API, por ejemplo
                sh 'curl http://localhost:3000/api/v1/welcome'
            }
        }
        stage('Cleanup') {
            steps {
                script {
                    // Detener y remover los contenedores
                    sh 'docker-compose down'
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

