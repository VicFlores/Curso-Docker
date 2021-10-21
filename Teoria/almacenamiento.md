Bind Mounts

Nos permite enlazar un directorio en la maquina anfitriona con el contenedor

1) creamos una carpeta donde queramos enlazar nuestro contenedor
2) docker run -d --name mongoDB -v /home/vicflores11/Desktop/Curso-Docker/Bind-mounts:/data/db mongo
3) docker exec -it mongoDB bash

---------------------------------------------------------------------------------------------------------

Volumenes

$ docker volume ls (listo los volumes)

$ docker volume create dbdata (creo un volume)

$ docker run -d --name db --mount src=dbdata,dst=/data/db mongo (corro la BBDD y monto el volume)

$ docker inspect db (veo la información detallada del contenedor)

---------------------------------------------------------------------------------------------------------

Comandos:


$ touch prueba.txt (creo un archivo en mi máquina)

$ docker run -d --name copytest ubuntu tail -f /dev/null (corron un ubuntu y le agrego el tail para que quede 
activo)

$ docker exec -it copytest bash (entro al contenedor)

$ mkdir testing (creo un directorio en el contenedor)

$ docker cp prueba.txt copytest:/testing/test.txt (copio el archivo dentro del contenedor)

$ docker cp copytest:/testing localtesting (copio el directorio de un contenedor a mi máquina)
con “docker cp” no hace falta que el contenedor esté corriendo