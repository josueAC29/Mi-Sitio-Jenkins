pipeline {
    agent any

    stages {
        stage('1. Clonar Código') {
            steps {
                echo 'Obteniendo el código más reciente desde GitHub...'
                git url: 'https://github.com/josueAC29/Mi-Sitio-Jenkins.git', branch: 'main'
            }
        }

        stage('2. Desplegar en Servidor Web') {
            steps {
                echo 'Copiando archivos al servidor Nginx con Docker...'
                powershell '''
                    # Levantar contenedor Nginx si no existe
                    if (-not (docker ps -q --filter "name=mi-nginx")) {
                        docker run -d --name mi-nginx -p 8080:80 nginx
                    }

                    # Copiar archivos HTML al contenedor
                    docker cp *.html mi-nginx:/usr/share/nginx/html/

                    Write-Output "Archivos copiados al contenedor Nginx"
                '''
            }
        }
    }
}
