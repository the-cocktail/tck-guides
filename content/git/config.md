---
title: Configuración
slug: configuracion
weight: 10
pre: "<i class='fa fa-wrench'></i> "
---

Antes de ponernos a trabajar con ningún repositorio, debemos de configurar las opciones generales de Git para nuestro flujo de trabajo.

### Configura tu identidad

* Configura nombre y correo asociados a los commits:

  ```bash
  $ git config --global user.name ‘Nombre’
  $ git config --global user.email ‘usuario@dominio.com’
  ```

### Configura algunas opciones

* Configuramos las opciones por defecto para pull y merge.

  ```bash
  $ git config --global merge.ff false
  $ git config --global branch.autosetuprebase always
  ```

Con **_merge.ff false_**, hacemos que todos los _merges_ sean --no-ff, es decir que siempre se genere un nuevo commit al hacer un merge. Por defecto los commits en Git son fast-forward, es decir, que si no tienen la necesidad crear un nuevo commit dejarán las cabezas de las dos ramas a mergear en el mismo punto, dejando la rama mas limpia, pero la historia menos descriptiva. Nosotros preferimos optar por tener toda la información posible en la historia, así podremos ver de que rama estaba viniendo un commit.

Con **_branch.autosetuprebase always_** forzamos que el comando **git pull** haga siempre un **rebase** para actualizar las ramas remotas con las locales. Al tener el merge como no-ff, siempre nos dejaría un commit al hacer pull, y en este caso no aporta nada a la historia global del repositorio.

**NOTA:** mucho ojo si ya has empezado a trabajar con Git y activas el autorebase posteriormente. Esta opción añade la opción cundo se crea una rama, por lo que las ramas ya creadas anteriormente no la tendrán. Para añadirla, edita el fichero **.git/config** del proyecto en cuestion y añade **rebase = true** en las ramas que no lo tengan. Por ejemplo:

  ```bash
  [branch "master"]
  	remote = origin
  	merge = refs/heads/master
  	rebase = true
  ```

### Plantilla (_template_) para las _Pull Requests_

  * Añade en el fichero `.github/pull_request_template.md` del proyecto la [plantilla para las _pull requests_](http://guides.the-cocktail.com/git/flujo/#plantillas). De esta forma todas las _pull requests_ que se generen en el proyecto tendrán la misma estructura lo que ayudará a unificar criterios y facilitar las revisiones.

### Hooks

Con el fin de ayudarnos a revisar antes de hacer un _commit_, un _push_, etc, podemos añadir hooks de ayuda por defecto en nuestros proyectos:

* Validaciones _staging_ (nuevas ramas, merges).
* Avisos de higiene (borrar ramas ya mergeadas a master).
* Avisos de mantenimiento (ramas desactualizadas).

Los hooks no deben depender del proyecto, sólo al propio repositorio, por lo tanto hooks que pasen pruebas, formateos y demás que dependan del stack de cada uno, deberan de ser gestionados personalmente. [Aqui](https://github.com/the-cocktail/tools/tree/master/git_hooks) puedes encontrar una guía de instalación y algunos _hooks_ interesantes.
