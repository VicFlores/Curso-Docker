# Versión del compose file
version: "3.8"

# Servicios que componen nuestra aplicación.
## Un servicio puede estar compuesto por uno o más contenedores.
services:
# nombre del servicio.
  app:
  # Imagen a utilizar.
    image: platzi-app
	# Declaración de variables de entorno.
    environment:
      MONGO_URL: "mongodb://db:27017/test"
	# Indica que este servicio depende de otro, en este caso DB.
	# El servicio app solo iniciara si el servicio debe inicia correctamente.
    depends_on:
      - db
	# Puerto del contenedor expuesto.
    ports:
      - "3000:3000"

  db:
    image: mongo

-------------------------------------------------------------------------------------------------------------

Sub comandos

docker-compose up -d (crea todo lo declarado en el archivo docker-compose.yml)

docker network ls (listo las redes)

docker network inspect docker_default (veo la definición de la red)

docker-compose logs (veo todos los logs)

docker-compose logs app (solo veo el log de “app”)

docker-compose logs -f app (hago un follow del log de app)

docker-compose exec app bash (entro al shell del contenedor app)

docker-compose ps (veo los contenedores generados por docker compose)

docker-compose down (borro todo lo generado por docker compose)

-------------------------------------------------------------------------------------------------------------

$ docker-compose build (crea las imágenes)
$ docker-compose up -d (crea los servicios/contenedores)
$ docker-compose logs app (veo los logs de “app”)
$ docker-compose logs -f app (hago un follow de los logs de “app”)

--------------------------------------------------------------------------------------------------------------

$ touch docker-compose.override.yml (creo el archivo override)
$ docker-compose up -d (crea los servicios/contenedores)
$ docker-compose exec app bash (entro al bash del contenedor app)
$ docker-compose ps (veo los contenedores del compose)
$ docker-compose down (borro todo lo creado con compose)

version: "3.8"

services:
  app:
    build: .
    environment:
      VARIABLE_TEST: "mongodb://mongoDB:27017/test"


-------------------------------------------------------------------------------------------------------------

Conectar diferentes puertos de mi maquina a los servidores

$ docker-compose up -d --scale app=2 (escalo dos instancias de app, previamente tengo que definir un rango de puertos en el archivo compose)

version: "3.8"

services:
  app:
    image: platzi-app
    environment:
      MONGO_URL: "mongodb://mongoDB:27017/test"
    depends_on:
      - mongoDB
    ports:
      - "3000-3001:3000"

  mongoDB:
    image: mongo

---------------------------------------------------------------------------------------------------------------




