stage('2. Desplegar en Servidor Web') {
    steps {
        echo 'Copiando archivos al servidor Nginx con Docker...'
        powershell '''
            # Si ya existe el contenedor mi-nginx, lo eliminamos forzadamente
            if (docker ps -a -q --filter "name=mi-nginx") {
                docker rm -f mi-nginx
            }

            # Crear contenedor nuevo en el puerto 8080
            docker run -d --name mi-nginx -p 8080:80 nginx

            # Copiar todos los archivos HTML al contenedor
            Get-ChildItem *.html | ForEach-Object {
                docker cp $_.FullName mi-nginx:/usr/share/nginx/html/
            }

            Write-Output "Archivos copiados al contenedor Nginx"
        '''
    }
}
