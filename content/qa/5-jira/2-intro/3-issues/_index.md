---
title: Tareas
slug: issues
---

En el menú de tareas se observan las últimas incidencias que hemos actualizado por el usuario que hemos accedido (dar de alta, editar, cambiar de estado…). Además, se muestran los filtros que se han dado de alta por el usuario actual para consultar elementos a lo largo de todos los proyectos activos.

![](/images/qap/jira/27.png)

En la parte final del menú se observa una opción para administrar los filtros que hemos creado o a los que se nos han dado permisos.

## Filtros por defecto

Dentro de los filtros que se pueden configurar por el usuario basándose en los proyectos activos, aparecen tres filtros que vienen por defecto para ayudarnos a realizar búsquedas sencillas de elementos, son los siguientes:

* Búsqueda actual: nos muestra la búsqueda o búsquedas que hemos realizado en este mismo momento o la última que se ha realizado. Nos aparece en un listado.

* Buscar incidencias: nos muestra un listado de elementos recientes a lo largo de todos los proyectos activos que tengamos en Jira.

* Incidencias recientes: muestra una serie de elementos recientes (5 en concreto) que hemos utilizado o actualizado, además de un enlace “Más...” donde se listan los elementos que hemos utilizado recientemente en todos nuestros proyectos activos.

Todas estas búsquedas y filtros, se pueden afinar con las opciones proporcionadas en la cabecera:

![](/images/qap/jira/28.png)

Estas opciones las trataremos y explicaremos en los siguientes puntos con más detalle.

## Importar incidencias desde CSV

Si tenemos un archivo CSV con elementos de trabajo y queremos importarlos en masa, existe una herramienta en Jira que nos lo permite.

Al pulsar en esta opción se abre y debemos de completar los siguientes pasos:

![](/images/qap/jira/29.png)

Esta opción es muy útil si trabajamos con una serie de elementos muy grandes o tenemos clientes que utilizan otra herramienta y queremos migrar a Jira toda la información introducida en la misma. Hay una documentación oficial para preparar el archivo que se puede consultar aquí.

## Filtros de usuario activo

Dentro de los filtros personalizados que nos proporciona Jira, existen unos que son para los usuarios activos en ese momento:

* Mis incidencias abiertas: Se realiza una búsqueda de las incidencias abiertas por el usuario activo. Se puede afinar de la misma manera que las explicadas anteriormente.

* Informadas por mí: Aquí aparecen las incidencias que no son nuestras directamente (responsable) pero sí que tenemos nosotros asignadas como informador para trabajar en ellas.

Tras estos filtros por defecto, aparecen hasta 10 filtros creados por el usuario activo y un enlace “Más…” que nos lleva a la pantalla de administración de filtros activos. Igual que el enlace “Administrar filtros” que se encuentra en el último lugar del desplegable.

## Administración de filtros

Cuando accedemos a cualquier filtro o pulsamos en el botón “Administrar Filtros”, entramos a la pantalla donde podemos editar todas las consultas que tengamos bajo nuestro tejado. Además, de crear nuevos filtros.

![](/images/qap/jira/30.png)

Para modificar o editar un filtro, simplemente, en la cabecera, podemos retocar opciones como:

* Proyecto: Seleccionando uno o varios, según nuestras necesidades.
* Tipo: Si queremos filtrar por un tipo o varios de elementos de trabajo (historias de usuario, error, tarea…).
* Estado: Seleccionar los estados que queremos filtrar, en base a los flujos activos (done, to do, in progress…).
* Usuario: podemos hacer un filtro según un usuario, varios o los que necesitemos.
* Caja de texto: Se puede realizar el filtro según una palabra o letra que contenga el elemento.

También hay una opción de “búsqueda avanzada” que se puede configurar mediante ciertas condiciones que se pueden observar en la página oficial.
