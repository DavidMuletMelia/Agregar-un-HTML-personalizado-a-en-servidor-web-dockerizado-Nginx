# Agregar-un-HTML-personalizado-a-en-servidor-web-dockerizado-Nginx


## - PASOS PREVIOS -

- Tener 'Docker' instalado 


## - INSTALACIÓN -

- Ejecutamos la imagen de 'nginx' con el siguente comando `docker run --rm -d -p 8080:80 --name web nginx`, dirá que no la encuentra y a continuación la descargara

![img]()

- Para comprobar que todo ha salido bien, visitamos ![Link](http://localhost:8080)

![img]()

- Una vez comprobemos que todo esta bien, ejecutamos el comando `sudo docker stop web` para parar el contenedor llamado 'web'


## - HTML -

- Nos metemos en el directorio `documentos` y creamos 2 directorios `nginx` y `site-content`
- Finalmente dentro de `site-content` creamos el archivo `index.html`
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

- Y ya deberiamos poder ver el resultado refrescando ![Link](http://localhost:8080)


