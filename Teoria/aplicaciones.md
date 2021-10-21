Práctica desarrollada:

Clonación de un repositorio:

git clone https://github.com/platzi/docker
Comando para construir una imágen basado en el Dockerfile

docker build -t platziapp
Comando para listar las imágenes existentes en mi máquina con Docker

docker image ls
Crear el contenedor con la instrucción de borrarse una vez que sea detenido, además expone el puerto 3000 del contenedor en el puerto 3000 de la máquina anfitrión

docker run --rm -p 3000:3000 platziapp
Explicación del archivo Dockerfile

# especifica la imágen base, para este caso se trata de node con especificación de versión 12
FROM node:12

# copiar todo lo que existe en el directorio actual (durante el build, es decir se refiere al directorio de nuestra máquina host/anfitrión), 
# en el directorio /usr/src/ del contenedor, es así como al final podemos ejecutar el archivo index.js, dado que se encuentra en el 
# conjunto de archivos que copiamos desde nuestra máquina al contenedor.
COPY [".", "/usr/src/"]

# establecer el directorio de trabajo, similar a utilizar el comando cd /usr/src
WORKDIR /usr/src

# descargar las dependencias del proyecto al ejecutar el comando de npm (node package manager)
RUN npm install

# Expone este puerto del contenedor, es decir, lo pone a la escucha
EXPOSE 3000

# ejecuta el comando node index.js en el contenedor ya creado
CMD ["node", "index.js"]