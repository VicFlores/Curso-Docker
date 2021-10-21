Comandos:

$ mkdir imagenes (creo un directorio en mi máquina)
$ cd imagenes (entro al directorio)
$ touch Dockerfile (creo un Dockerfile)
$ code . (abro code en el direcotrio en el que estoy)

##Contenido del Dockerfile##
FROM ubuntu:latest
RUN touch /ust/src/hola-platzi.txt (comando a ejecutar en tiempo de build)
##fin##

$ docker build -t ubuntu:platzi . (creo una imagen con el contexto de build <directorio>)
$ docker run -it ubuntu:platzi (corro el contenedor con la nueva imagen)
$ docker login (me logueo en docker hub)
$ docker tag ubuntu:platzi miusuario/ubuntu:platzy (cambio el tag para poder subirla a mi docker hub)
$ docker push miusuario/ubuntu:platzi (publico la imagen a mi docker hub)

docker image rm -f {id_image}