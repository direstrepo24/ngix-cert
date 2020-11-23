pipeline {
    agent any

    stages {

        stage('Despliegue Domain') {
            steps {
                echo 'Desplegando en NGIX'
            }
        }
        stage('Aprobacion manual') {
            input {
                message "Esta seguro que desea desplegar a producción?"
                ok "Aprobar"
                parameters {
                    string(name: 'comentario', defaultValue: '', description: 'Deje aquí su comentario')
                }
            }
            steps {
                echo "${comentario}"
            }
        }
        stage('Despliegue PROD') {
            steps {
                echo "Desplegando en producción..."
                sh "docker-compose -f ./docker-compose.yml up -d --build"
            }
        }
    }
}
