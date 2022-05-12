# claseDeDocker

Primero hemos comenzado realizando el pull de una imagen existente con el comando:
  *docker pull httpd:latest*

A continuación, como hemos utilizado un disco duro, el cual contenía docker, el directorio .docker/ ya existe por lo tanto, nos movemos al este directorio:
  *cd .docker/*
  
Una vez dentro del directorio, vamos a crear nuestro archivo dockerfile. Para ello utilizamos el siguiente comando:
  *nano dockerfile*
  
En su interior vamos a escribir: FROM httpd:latest, para poder hacer una conexión con la imagen que hemos descargado.
Una vez guardado el dockerfile, estando dentro del directorio, procedemos a escribir el siguiente comando para su montaje:
  *docker build -t prueba:latest .* Con este comando hacemos el montaje y con '-t' le damos un tag, en este caso, sería 'prueba'.
  
  
(Para poder ver las imagenes que tenemos montadas, podemos hacerlo mediante el comando: *docker images*)


A continuación, procedemos a correr la imagen y crear nuestro contenedor, para ello, escribimos el siguiente comando:
  *docker run -p 8080:80 prueba:latest*
  
  
Con este comando, añadimos el puerto que vamos a utilizar tambien.
En caso de querer ver las todos los contenedores activos, con el comando *docker ps*.


Para, pararlos, con el comando *docker stop <id>*.
 
  
Para cambiar el texto por defecto de nuestra imagen mostrado en el localhost. Crearemos un index.html y lo moveremos al directorio .docker/ y accederemos al docker file
dejandolo de esta forma: FROM httpd:latest
                         COPY index.html /usr/local/apache2/htdocs/index.html
 
 
Y a continuacion lanzandolo de nuevo con el run.
 
 
Introduciendo el index creado en el directorio htdocs, de esta forma cambiamos el mensaje a gusto propio.
  
 
A continuación si queremos ver la información de nuestra imagen, podremos hacerlo mediante el comando: 
  *docker inspect <id imagen>*
 
 
Nos saca información desde los volumenes montados, configuraciones, etc.

 
Para crear un nuevo volumen lo haremos mediante el comando: *docker create volume <nombrevolumen>*

 
Para asignar un volumen a una imagen, lo haremos mediante el comando:
  *docker run -v <nombrevolumen>:/opt/data -p 8080:80 <nombreimagen>*
Si accedemos al inspect de dicha imagen, podremos ver como el volumen ha sido asignado correctamente.

  
También podemos ver la información de los volumenes con el comando *docker inspect <nombrevolumen>*
En esta información, podremos ver la fecha de creación, el punto donde esta montado y el nombre entre otras cosas.

 
Para poder acceder a la terminal de una imagen, podremos hacerlo mediante el uso del exec: *docker exec -it <iddeimagen> bash*
Aqui dentro podremos acceder por ejemplo a los directorios que lo componen mediante un ls.
 

