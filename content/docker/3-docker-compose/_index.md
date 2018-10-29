---
title: 3.- Docker Compose
slug:
chapter: false
---

### Nombre de contenedor

Establecer un nombre de contenedor para poder gestionar los contenedores independientemente de la carpeta padre.

```
services:
  app1:
    image: thecocktail/ruby-base:2.3.3
    container_name: app1
```

### Utilizar _healthchecks_

Utilizar _healthchecks_ para verificar el estado de los contenedores

```
services:
  db:
    image: 'mysql:5.6'
    environment:
      MYSQL_ROOT_PASSWORD: password
    healthcheck:
      test: ["CMD", "mysqladmin" ,"ping", "-h", "localhost"]
      timeout: 20s
      retries: 10
```

### Utilizar usuarios non-root

Usar usuarios que no sean _root_. Esto se puede gestionar desde el _dockerfile_ o desde el _docker-compose_. De este modo el contenedor se levantará con el _UID_ del usuario que lo ejecute.

```
services:
  app1:
    image: thecocktail/ruby-base:2.3.3
    container_name: app1
    user: "${UID}:${GID}"
```

```
$ UID=${UID} GID=${GID} docker-compose up
```

### Dependencias

Marcar las dependencias entre los contenedores para que en caso de arrancar solo uno, se arranquen sus dependencias.

```
services:
  app1:
    image: thecocktail/ruby-base:2.3.3
    depends_on:
      - db
  db:
    image: mysql:5.6
    environment:
      MYSQL_ROOT_PASSWORD: password
```

### Networking

Si los contenedores de un _docker-compose_ tienen que conectarse a los contenedores de otro _docker-compose_, gestionarlo mediante _networks_ y no contra conexiones a puertos de _localhost_.

Crear la _red de travesía_:

```
docker network create app-net
```

* **_Docker-compose-app-1_**:

```
services:
  app1:
    image: thecocktail/ruby-base:2.3.3
    container_name: app1
    networks:
     - app-net   
networks:
  app-net:
    external:
      name: app-net
```

* **_Docker-compose-app-2_**:

```
services:
  app2:
    image: thecocktail/ruby-base:2.3.3
    container_name: app2
    networks:
     - app-net
networks:
  app-net:
    external:
      name: app-net
```

### Interactive processes

Si se van a ejecutar comandos desde consola en el _Docker_, es recomendable habilitar el _tty_ y el *stdin_open*.

```
services:
  app1:
    image: thecocktail/ruby-base:2.3.3
    Container_name: app1
    stdin_open: true
    tty: true
```

### Gestión de volúmenes

A no ser que se le quieran pasar ficheros o directorios existentes a _Docker_, utilizar la gestión de volúmenes de _Docker_.

```
services:
  db:
    image: mysql:5.6
      environment:
        MYSQL_ROOT_PASSWORD: password  
    volumes:
      - db:/var/lib/mysql
volumes:
  db:
```
