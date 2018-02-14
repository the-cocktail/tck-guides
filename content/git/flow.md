---
title: Flujo de trabajo
slug: flujo
weight: 30
---

Por lo general los proyectos tendrán como mínimo dos ramas, **master** y **staging**. La rama _master_ es la que usan los servidores de producción para los despliegues, mientras que _staging_ es la de los servidores de prueba.

Consideraciones generales:

* Las ramas nuevas siempre saldrán de _master_, salvo casos especiales como una funcionalidad particular de una rama en desarrollo.
* No hacer commits directos sobre master.
* Salvo casos particulares, las ramas deberían de mergearse primero a _staging_ y tras asegurarnos de que todo funciona, a _master_.
* Antes de mergear una rama, actualizar la rama sobre la que vamos a mergear.
* Comprobar que una rama funciona correctamente antes de pushear.
* No pushear cambios en _master_ que no se puedan desplegar.
* Para actualizar las ramas podemos usar _git pull_ pero tambíen es recomendable hacer por separado _git fetch_ y _git rebase_. De esta forma veremos mas claramente que ha cambiado en el repositorio y haremos el rebase con más cuidado.
* Usa [tags](http://git-scm.com/book/es/v2/Fundamentos-de-Git-Etiquetado) para marcar puntos importates del repositorio.
* **Nunca reescribir la historia ya publicada.** Ciertos comandos como el rebase pueden reescribir la historia de los commits. Si esos commits ya estaban publicados, nunca debemos de vovler a publicarlos ya que afectaremos al resto de compañeros que los tengan en su repositorio local.
* En algunos casos como usar un rebase interactivo (git rebase -i) para dejar la historia más limpia, hacerlo siempre con ramas personales que no estén publicadas.


Ejemplo de flujo de trabajo con una nueva funcionalidad:

  ```bash
  # Nos vamos a master y creamos la rama
  $ git checkout master
  $ git checkout -b feature/oauth-migration

  # Trabajamos, y cuando esté listo lo llevamos a staging y comprobamos
  $ git checkout staging
  $ git fetch
  $ git rebase
  $ git merge feature/oauth-migration
  $ git push

  # Cuando tengamos que desplegar
  $ git checkout master
  $ git fetch
  $ git rebase
  $ git merge feature/oauth-migration
  $ git push

  # Si hemos acabado con la funcionalidad
  $ git branch -d feature/oauth-migration
  # Y si hemos pusheado nuestra rama
  $ git push origin :feature/oauth-migration
  ```

En caso de no poder pushear una rama porque nos olvidamos de actualizar antes de mergear, nos aseguramos de que no perdemos nada en esa rama, actualizamos con fetch y hacemos un **reset --hard** al remoto para volver a mergear con la rama actualizada:

  ```bash
  $ git checkout master
  $ git merge feature/oauth-migration
  $ git push
  # ERROR
  $ git fetch
  $ git reset --hard origin/master
  $ git merge feature/oauth-migration
  $ git push
  ```

Manten el repositorio (local y remoto) limpo, ejecuta comandos de mantenimiento cada cierto tiempo::

* [`git-gc(1)`](http://git-scm.com/docs/git-gc)
* [`git-prune(1)`](http://git-scm.com/docs/git-prune)
* [`git-fsck(1)`](http://git-scm.com/docs/git-fsck)


### La policía de git no tendrá piedad con:

  * Crear una rama desde _staging_.
  * Mergear _staging_ sobre otra rama.
  * Hacer rebase en una rama ya publicada.
  * Forzar un push (-f).

  <iframe src="https://player.vimeo.com/video/82408340" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> <p><a href="https://vimeo.com/82408340">LA HE LIADO PARDA, versi&oacute;n PIWEEK de Kaleidos</a> from <a href="https://vimeo.com/user10956949">kaleidos</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
