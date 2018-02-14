---
title: Configuración
slug: configuracion
weight: 10
---

Antes de ponernos a trabajar con ningún repositorio, debemos de configurar las opciones generales de Git para nuestro flujo de trabajo.

* Configura nombre y correo asociados a los commits:

  ```bash
  $ git config --global user.name ‘Nombre’
  $ git config --global user.email ‘usuario@dominio.com’
  ```

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
