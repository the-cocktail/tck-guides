---
title: Flujo de trabajo
slug: flujo
weight: 30
pre: "<i class='fa fa-retweet'></i> "
---

Por lo general los proyectos tendrán como mínimo tres ramas de largo recorrido, **master**, **integration** y **staging**.

* _master_: contiene el código que se desplegará en los servidores de producción.
* _integration_: se integra el código de las distintas funcionalidades que se van desarrollando, previo paso a _master_.
* _staging_: contiene el código que se desplegará en los servidores de prueba.

Existe la posibilidad que por motivos de proyecto no exista un entorno de _staging_, en algún punto del proyecto. En este caso, no existirá esta rama en nuestro flujo de Git y obviaremos las siguientes referencias a dicha rama. En el momento en el que un proyecto tenga entorno de _staging_, se deberá crear e introducir en el flujo una rama _staging_.

## Consideraciones generales

* **Nunca** hacer commits directos sobre _master_, salvo casos especiales de **intervención sobre producción** (_hotfixes, infraestructura_).
* Las ramas nuevas **siempre** saldrán de _master_
* Las ramas nuevas **jamás** saldrán de _staging_.
* La rama de _staging_ **jamás** se mergeará sobre otra rama.
* Las ramas deberían de mergearse primero a _staging_ para probar su funcionamiento en el servidor de pruebas (en los proyectos que aplique).
* Antes de mergear una rama B personal sobre una rama A común, actualizar la rama A (_git pull_) y si hay cambios nuevos cambios con respeto a la rama B, llevarlos a B para resolverlos en nuestra rama personal antes de llevarlos a la común.
* Comprobar que una rama funciona correctamente antes de pushear.
* No pushear cambios en _master_ que no se puedan desplegar. La rama _master_ contiene el código que se despliega en los servidores y puede necesitarse hacer un despliegue de emergencia, o en aplicaciones con autoescalado, en cualquier momento podría crearse una nueva instancia con su código.
* **Nunca reescribir la historia ya publicada.** Ciertos comandos como el rebase pueden reescribir la historia de los commits. Si esos commits ya estaban publicados, nunca debemos de vovler a publicarlos ya que afectaremos al resto de compañeros que los tengan en su repositorio local.
* Salvo casos muy particulares y completamente controlados, **jamás hacer git push -f**.

## Flujo de trabajo

En este apartado describiremos el flujo de trabajo de ramas a seguir en todos los proyectos:

**NOTA**: Dada la gran cantidad de proyectos distintos, puede haber clientes que requieran necesidades particulares. Cuando el flujo de trabajo no encaje exactamente con el descrito en esta sección, se deberá tratar como una excepción y tendrá que ser consensuada y autorizada por él, la o los encargados técnicos del proyecto.

### Funcionalidades

Las nuevas funcionaliades saldrán siempre de la rama _master_. Se podrán ir llevando a _staging_ para probar en los servidores de prueba (si aplica) y una vez listas, con _pull request_ a la rama _integration_.

![Funcionalidades](/images/git/features.png "Funcionalidades")

### Intervenciones sobre producción

Las correcciones urgentes o cambios que apliquen directamente al entorno de producción (infraestructura) pueden ver su flujo alterado. Probarse en _staging_ (si aplica), volver a _master_ (con _pull request_ y tageo tras despliegue) y actualizarse en _integration_. Es importante que este tipo de intervenciones se actualicen en el resto de ramas comunes.

![Fixes](/images/git/fixes.png "Fixes")

### _Releases_

En casos muy particules en los que un proyecto tenga despliegues de desarrollos muy planificados, puede llevarse una rama de release donde concentrar solo esos desarrollos. Por ejemplo, podría darse el caso de tener una máquina específica para desplegar ese desarrollo de forma aislada del resto para una validación específica del cliente.

![Releases](/images/git/releases.png "Releases")

### _Pull requests_

Haremos siempre _pull requests_ de nuestras ramas a la hora de unificar nuestros cambios con resto del código.

Dado que el objetivo principal de las _pull requests_ es que el resto del equipo haga una revisión del código, deberemos de asegurarnos con el encargado del proyecto de que exista una persona al menos que vaya a poder revisarla. En caso contraro la _pull requests_ pierde el sentido, las _pull requests_ no son un diario de desarrollo.

Consideraciones generales:

* Las _pull requests_ irán contra las ramas encargadas de la unificación del código _master_, _integration_, _release_... en cualquier caso nunca contra _staging_.
* Las _pull requests_ no son una interfaz gráfica para hacer un _merge_.
* Escribir un título descriptivo e indicar el ticket: `[Id del ticket] Título del ticket`
* Utilizar etiquetas para identificar el tipo y el estado: WIP, feature...
* Asignar los revisores adecuados.
* Si el proyecto tiene releases planificadas, usar las milestones para saber a cual corresponde. Por ejemplo una milestone con la fecha planificada del despliegue.

Pasos para la revisión:

1. Leer con calma la descripción.
2. Probar los cambios en local y ver que funciona como se explica.
3. Revisar el código de los commits.
4. Si aplica, intentar dar feedback constructivo educadamente.

#### Plantillas

Todos los proyectos deben de contener las siguientes plantilla _pull requests_ en una carpeta .github. Si aplica también se puede hacer una para _issues_.

Plantilla para _pull requests_, fichero **PULL_REQUEST_TEMPLATE.md**:

```md
[Ticket de referencia](SUSTITUIR_POR_URL_DE_TICKET)

## Resumen

Escribir aquí un resumen o listado breve de cosas que añade o cambia esta PR. Utilizar una check list para seguir el progreso.

- [X] Tarea 1.
- [ ] Tarea 2.
- [ ] Tarea 3.

## Pruebas

Ejemplos de como probar los cambios: pasos para replicar un problema, snippets de código para ejecutar en consola...

## Despliegue

Escribir aquí qué comandos y consideraciones que son necesarios para su despliegue (por ejemplo, borrar caché).
Si no hace falta ejecutar nada, se puede borrar esta parte.
```

#### Vida de una _Pull Request_

Las _pull request_ no son un recordatorio o un log de funcionalidades en desarrollo. Cuando se crea una _pull request_ se debe tener la convicción de que el código cumple con la funcionalidad definida y se generá una discusión para su aprobación.

* No deben de quedar desarrollos pendientes.
* Se puede trabajar sobre una _pull request_ abierta para mejoras o correcciones.
* Si fuera necesario hacer cambios o seguir desarrollando, se deberá cancelar la _pull request_, realizar los cambios correspondientes y después volverla a crear.
* La aprobación de la _pull request_ no significa que se deba mergear automáticamente.

La vida útil de una _pull request_ no debe más de una semanas, dependiendo del proyecto y sus periodos de aprobación/despliegue. Una _pull request_ que se dilata en el tiempo demasiado pierde su sentido, al no estar su código actualizado y poder generar conflictos. En caso de no poder hacer el merge por cualquier razón, se deberá de cerrar y cuando vuelva a ser posible hacerlo, actualizar la rama y abrir una nueva _pull request_.

Una vez se tenga la aprobación, el tiempo que debe transcurrir entre su merge con _integration_ y su merge con _master_ y futuro despliegue debe ser el menor tiempo posible, con el fin de evitar colisiones y que estás funcionalidades queden fuera de contexto.

### _Tags_

Cada vez que se haga un despliegue, crearemos un tag de git con la la fecha del despliegue. Si se hacen varios despliegues el mismo día, los diferenciaremos con un número

```
20180101
20180101-2
20180213
20180213-2
20180213-3
```

De esta formas crearemos puntos de control en el repositorio de todo el código desplegado.

Independientemente se podrán llevar tags versionadas como

### _Hooks_ [WIP]

Añadiremos hooks de ayuda por defecto en nuestros proyectos:

* Validaciones _staging_ (nuevas ramas, merges).
* Avisos de higiene (borrar ramas ya mergeadas a master).
* Avisos de mantenimiento (ramas desactualizadas).

Los hooks no deben depender del proyecto, sólo al propio repositorio, por lo tanto hooks que pasen pruebas, formateos y demás que dependan del stack de cada uno, deberan de ser gestionados personalmente.

### Ejemplos

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
  # Este paso se haría realmente con una pull request
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

## La policía de git

La policía de git no tendrá piedad con:

  * Crear una rama desde _staging_.
  * Mergear _staging_ sobre otra rama.
  * Hacer rebase en una rama ya publicada.
  * Forzar un push (-f).

  <iframe src="https://player.vimeo.com/video/82408340" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> <p><a href="https://vimeo.com/82408340">LA HE LIADO PARDA, versi&oacute;n PIWEEK de Kaleidos</a> from <a href="https://vimeo.com/user10956949">kaleidos</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
