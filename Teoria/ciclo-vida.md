*Cada vez que un contenedor se ejecuta, en realidad lo que ejecuta es un proceso del sistema operativo,
este proceso se le conoce como Main process.

* Main process
Determina la vida del contenedor, un contenedor corre siempre y cuando su proceso principal este corriendo.

*Sub process
Un contenedor puede tener o lanzar procesos alternos al main process, si estos fallan el contenedor va a seguir
encendido a menos que falle el main.

-----------------------------------------------------------------------------------------------------------

Ejemplos manejados en el video:

(/dev/null => es conocido como un agujero negro es decir ese archivo es la nada…)

docker run --name alwaysup -d ubuntu tail -f /dev/null 

El output que te regresa es el ID del contenedor 

-----------------------------------------------------------------------------------------------------------

Te puedes conectar al contenedor y hacer cosas dentro del él con el siguiente comando (sub proceso)

docker exec -it alwaysup bash

-----------------------------------------------------------------------------------------------------------

Se puede matar un Main process desde afuera del contenedor, esto se ra conociendo el id del proceso principal del contenedor que se tiene en la maquina. Para saberlo se ejecuta los siguientes comandos

docker inspect --format '{{.State.Pid}}' alwaysup

El output del comando es el process ID

Para matar el proceso principal del contenedor desde afuera se ejecuta el siguiente comando (solo funciona en linux)

Kill -9 2474

-----------------------------------------------------------------------------------------------------------