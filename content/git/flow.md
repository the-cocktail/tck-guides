---
title: Flujo de trabajo
slug: flujo
weight: 30
pre: "<i class='fa fa-retweet'></i> "
---

Por lo general los proyectos tendrán como mínimo dos ramas, **master** y **staging**. La rama _master_ es la que usan los servidores de producción para los despliegues, mientras que _staging_ es la de los servidores de prueba.

Habrá proyectos más sencillos, en los que el concepto de _staging_ no haga falta. En ese caso obviaremos las partes que afecten a staging pero seguiremos aplicando el resto del flujo de la misma forma.

## Consideraciones generales

* **Nunca** hacer commits directos sobre master.
* Las ramas nuevas **siempre** saldrán de _master_, salvo casos especiales como una funcionalidad de largo recorrido con varias tareas.
* Las ramas nuevas **jamás** saldrán de _staging_.
* Las rama de _staging_ **jamás** se mergeará sobre otra rama.
* Salvo casos particulares, las ramas deberían de mergearse primero a _staging_ y tras asegurarnos de que todo funciona, a _master_ o donde corresponda en el proyecto, como por ejemplo _integration_.
* Antes de mergear una rama, actualizar la rama sobre la que vamos a mergear para resolver conflictos en nuestra rama.
* Comprobar que una rama funciona correctamente antes de pushear.
* No pushear cambios en _master_ que no se puedan desplegar.
* Para actualizar las ramas podemos usar _git pull_ pero tambíen es recomendable hacer por separado _git fetch_ y _git rebase_. De esta forma veremos mas claramente que ha cambiado en el repositorio y haremos el rebase con más cuidado.
* **Nunca reescribir la historia ya publicada.** Ciertos comandos como el rebase pueden reescribir la historia de los commits. Si esos commits ya estaban publicados, nunca debemos de vovler a publicarlos ya que afectaremos al resto de compañeros que los tengan en su repositorio local.
* Salvo casos muy particulares y completamente controlados, **jamás hacer git push -f**.

## Flujos de trabajo

Dada la gran cantidad de proyectos distintos y clientes con distintas necesidades no podemos tener un flujo común para todos. El encargado de cada proyecto deberá determinar el flujo de trabajo más óptimo según el estado en el que se encuentra el proyecto, por ejemplo un proyecto en mantenimiento con poca carga de trabajo no requerirá el mismo flujo que un proyecto con constantes evolutivos y varias personas con dedicación total.

En este apartado describiremos distintos flujos para casos a mínimo y máximos:

### Básico

En un flujo básico debemos crear una nueva rama (según las reglas) para cada nueva tarea que vayamos a realizar. Nuestro trabajo de forma particular deberá ir siempre en una rama independiente, nunca trabajaremos directamente sobre una rama con otro usuario.

Una vel la tarea este realizada procederemos según las reglas básicas, primero merge a staging para probar, finalmente _pull request_ a master y despliegue tras aceptación.

![Flujo básico](/images/git/basic.png "Básico")

### Máximos

Con multiples desarrolladores, multiples funcionalidades y tareas de mantenimiento en paralelo y múltiples revisiones de usuario.

Usar una rama de desarrollo o integración para unificar todo el código antes de llevarlo a master.

![Desarrollo](/images/git/development.png "Desarrollo")

Las nuevas funcionalidades se van llevando a staging para probar y con _pull request_ a desarrollo o integración.

**TODO:** Corregir, la rama siempre debe de salir de master y añadir staging.

![Funcionalidades](/images/git/features.png "Funcionalidades")

Los fixes urgentes deben salir de master, volver a master (con _pull request_ y tageo tras despliegue) y actualizarse en desarrollo o integración.

![Fixes](/images/git/fixes.png "Fixes")

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

1. Leer con clama la descripción.
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
