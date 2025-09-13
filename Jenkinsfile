pipeline {
    agent any

    stages {
        stage('1. Clonar código') {
            steps {
                echo 'Obteniendo el código más reciente desde GitHub...'
                git branch: 'main', url: 'https://github.com/josueAC29/Mi-Sitio-Jenkins.git'
            }
        }

        stage('2. Desplegar en Servidor Web') {
            steps {
                echo 'Copiando archivos al servidor Nginx con Docker...'
                powershell '''
                    # Eliminar contenedor previo si existe
                    if (docker ps -a --format "{{.Names}}" | findstr "mi-nginx") {
                        docker rm -f mi-nginx
                    }

                    # Levantar contenedor nuevo
                    docker run -d --name mi-nginx -p 8080:80 nginx

                    # Copiar archivos HTML al contenedor
                    docker cp index.html mi-nginx:/usr/share/nginx/html/

                    Write-Output "Archivos copiados al contenedor Nginx"
                '''
            }
        }
    }
}
