pipeline {
    agent any 

    environment {
        DOCKER_IMAGE = 'practica:latest'
    }

    stages {
        stage('Preparar') {
            steps {
               
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Construyendo la imagen Docker...'
                script {
                   
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                
                sh 'echo "Aquí van los comandos para ejecutar pruebas"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Desplegando a producción...'
                script {
                    sh 'echo "Desplegar utilizando algún script o herramienta"'
                }
            }
        }
    }

    post {
        always {
            echo 'Este mensaje siempre se ejecutará al final del pipeline.'
        }
        success {
            echo 'El pipeline se ejecutó correctamente'
        }
        failure {
            echo 'El pipeline falló en algún paso.'
        }
    }
}
