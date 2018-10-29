---
title: 2.- Dockerfile
slug: dockerfile
chapter: false
---

### Utilizar imágenes base oficiales

Al definir un _Dockerfile_, seleccionar una imagen oficial desde los registros de _Docker_:

![](/images/docker/debian_image.png)

```Dockerfile
FROM debian
```

### Ignorar ficheros innecesarios o sensibles

Todos los ficheros que no sean necesarios para la creación de la imagen deben de añadirse al _.dockerignore_.

### Minimizar el número de layers y utilizar multi-lines

Agrupar las layers lo máximo posible y utilizar multi-lines para hacerlo más visible:

```Dockerfile
RUN apt update -y && apt install -y \
    vim \
    ruby \
    git &&\
    apt clean -y
```

### Utilizar variables

Utilizar variables en la medida de lo posible para facilitar los cambios y hacerlo lo más estándar posible.

```Dockerfile
ARG RUBY_VERSION=2.1.2

RUN cd /srv &&\
    wget https://ruby-lang.org/pub/ruby/ruby-${RUBY_VERSION}.zip &&\
    unzip ruby-${RUBY_VERSION}.zip &&\
    cd ruby-${RUBY_VERSION} &&\
    ./configure &&\
    make -j"$(nproc)" &&\
    make install &&\
    rm -fr /srv/ruby-${RUBY_VERSION}.zip
```

### Fijar el _Workdir_

Fijar el _workdir_ donde trabajaremos (en caso de necesitarlo).

```Dockerfile
WORKDIR /app
```

### Definir los puertos

Definir los puertos para poderse conectar posteriormente.

```Dockerfile
EXPOSE 443
```

### Definir los _environments_

Definir las variables de entorno necesarias.

```Dockerfile
ENV GOPATH=/go
```

### Definir _locale_ del sistema

Generar la _locale_ del sistema para evitar problemas de _encoding_. Por ejemplo:

```Dockerfile
RUN echo "es_ES.UTF-8 UTF-8" > /etc/locale.gen \
 && locale-gen es_ES.UTF-8

ENV LANG es_ES.UTF-8
ENV LANGUAGE es_ES:es
```

### Definir los volúmenes

Definir los volúmenes que van a necesitar ser montados.

```Dockerfile
VOLUME /var/lib/mysql
```

### Utilizar usuarios non-root

Es recomendable utilizar usuarios que no tengan permisos de _root_. También se puede controlar desde el _docker-compose.yml_.

```Dockerfile
ARG USR=deploys
RUN useradd -ms /bin/bash -u 1000 ${USR}
USER ${DEPLOY_USR}
```

### Código en la imagen

En entornos productivos (_production, staging, nft…_) es recomendable añadir el código y la instalación de gemas (en el caso de que sea _Ruby_) en el propio _Dockerfile_.

```Dockerfile
FROM thecocktail/ruby-base:test
ARG GITHUB_TOKEN
ARG DEPLOY_USR=deploys
COPY . /app
RUN useradd -ms /bin/bash ${DEPLOY_USR}&&\
    chmod 755 /app &&\
    chown -R ${DEPLOY_USR} /app
USER ${DEPLOY_USR}
WORKDIR /app
RUN bundle config github.com thecocktail:${GITHUB_TOKEN} &&\
    bundle install -j"$(nproc)" &&\
    bundle config --delete github.com
```
