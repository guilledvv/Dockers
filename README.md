# Docker
---
Docker es una plataforma que permite a los desarrolladores crear, empaquetar y ejecutar aplicaciones en *contenedores*.
- GitHub : [@ainhoafdez](https://github.com/ainhoafdez)

## Instalación de Docker

Add Docker's official GPG key:
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

Add the repository to Apt sources:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

## Comandos en Docker

- `docker images` -> ver las imágenes descargadas
- `docker pull hello-world` -> instalar una imagen de docker
- `docker run hello-world` -> iniciar una imagen (en este caso hello-world)
- `docker stop hello-world` -> parar una imagen
- `docker kill hello-world` -> fuerza la detención de una imagen
- `docker rmi` -> borra una imagen

- `docker ps -a` -> ver contenedores activos y no activos (-a)
- `docker start -a a64` -> iniciar por id del contenedor, muestra su salida (-a)
- `docker rm` -> borra un contenedor
- `docker rm $` -> borra todos los contenedores

- `docker run -d nginx` -> inicia un servidor web (nginx) en segundo plano (-d)
- `docker run -d -p puertoHost:puertoContenedor` -> inicia "" abriendo el puerto host al puerto del contenedor
- `docker exec -it (id) bin/bash` -> entrar al contenedor para editar la página web de manera iterativa
- Ruta de página web de nginx: /usr/share/nginx/html

- `docker run -d -p 80:8080 tsongpon/pon` -> inicia tsongpon/pingpong en el puerto 80:8080 en segundo plano
- `docker run -d -p 443:8080 tsongpon/pon` -> inicia tsongpon/pingpong en el puerto 443:8080 en segundo plano para tener los 2 a la vez
- `sudo curl localhost/ping` -> devuelve "pong" con tsongpon/pon

- `docker inspect (id) -f"{{NetworkSettings.IPAdress}}"` -> para sacar toda la información de un contenedor (IP)
- `docker run -d (ubuntu) sleep infinity` -> para que ubuntu no se apague solo al no tener nada
- `docker run -d -o 80:80 -v /home/ainhoa/vol_practica:/usr/share/nginx/html nginx:latest` -> compartir carpeta de ubuntu vol_practica con html de nginx de su última versión. Hay que crear un intex.html a parte para que no se superpongan las carpetas

- `docker volume create` -> docker crea un volume
- `docker volume ls` -> ver volumes creados
- `docker volume inspect(volume)` -> ver detalles de un volume
- `docker volume prune` -> borrar todos los volumes que no se estan usando
