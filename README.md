# Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx


## - PASOS PREVIOS -

- Tener 'Docker' instalado 


## - INSTALACIÓN -

- Ejecutamos la imagen de 'nginx' con el siguente comando `docker run --rm -d -p 8080:80 --name web nginx`, dirá que no la encuentra y a continuación la descargara

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/1.PNG)

- Para comprobar que todo ha salido bien, visitamos http://localhost:8080

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/2.PNG)

- Una vez comprobemos que todo esta bien, ejecutamos el comando `sudo docker stop web` para parar el contenedor llamado 'web'


## - HTML -

- Nos metemos en el directorio `documentos` y creamos 2 directorios `nginx` y `site-content`

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/4.PNG)

- Finalmente dentro de `site-content` creamos el archivo `index.html`

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/5.PNG)

- Dentro de `index.html` introducimos el siguiente código

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Docker Nginx</title>
</head>
<body>
  <h2>Hello desde Cibeseguridad</h2>
</body>
</html>
```

- Por último ejecutamos el siguente comando `docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx` agragando la marca `-v` para crear un volumen

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/6.PNG)

- Y ya deberiamos poder ver el resultado refrescando http://localhost:8080

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/7.PNG)

## - CREACIÓN DE UNA IMAAGEN PERSONALIZADA -

- Creamos un 'Dockerfile' dentro del directorio `./Documentos/nginx/`
- Usamos el comando `sudo nano Dockerfile`
- Dentro de `Dockerfile` escribimos lo siguente
    ```
   FROM nginx:latest
   COPY ./site-content/index.html /usr/share/nginx/html/index.html
    ```
    
    ![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/8.PNG)

- Para continuar, copiamos el archivo `index.html` que hemos creado anteriormente en el directorio `./Documentos/nginx/site-content/` dentro del directorio `./usr/share/nginx/html` con el comando `cp index.html ./usr/share/nginx/html/`

- Ahora ya estamos listos para construir la imagen, podemos hacerlo con el comando `sudo docker build -t webserver .`

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/9bis.PNG)

- Deberia salir de la siguente manera

![img](https://github.com/DavidMuletMelia/Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx/blob/main/nginxDocker/10.PNG)

