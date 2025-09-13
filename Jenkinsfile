pipeline {
    agent any
    stages {
        stage('1. Clonar Código') {
            steps {
                echo 'Obteniendo el código más reciente desde GitHub...'
                // ▼▼▼ ¡¡IMPORTANTE!! Cambia esta URL por la de tu repositorio ▼▼▼
                git url: 'https://github.com/josueAC29/Mi-Sitio-Jenkins.git', branch: 'main'
            }
        }
        stage('2. Desplegar en Servidor Web') {
            steps {
                echo 'Copiando archivos al servidor Nginx...'
                sh 'cp -f *.html /var/website-data/'
            }
        }
    }
}
