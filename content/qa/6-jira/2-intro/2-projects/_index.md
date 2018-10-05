---
title: Proyectos
slug: projects
---

En el módulo de proyectos podemos acceder a los proyectos en los que estamos trabajando actualmente. Al pulsar en el módulo de la cabecera, se muestra lo siguiente:

![](/images/qap/jira/20.png)

1. **Proyecto actual**: Aquí se muestra el último proyecto al que hemos accedido o en el que estamos en este momento.

2. **Proyectos recientes**: Son los últimos proyectos donde hemos accedido y hemos estado trabajando.

3. **Tipos de Proyectos**: Una serie de filtros con los tipos de proyectos dados de alta en el Jira de la compañía.

4. **Ver todos los proyectos**: Desde este enlace se muestra un listado con todos los proyectos que están dados de alta en Jira.

Si accedemos a uno de los proyectos que nos sale en el listado, por defecto se nos mostrará la pizarra del mismo, con un aspecto similar al siguiente:

![](/images/qap/jira/21.png)

En esta pantalla, podemos observar lo siguiente:

1. **Iconos de acceso a submódulos del proyecto**: Se muestran a la izquierda de la pantalla, donde podemos acceder a las pizarras, al listado del backlog, versionado, gráficas… (en el caso de ser administrador, también aparece una rueda dentada de ajustes del proyecto al final de la columna).

2. **Filtros rápidos**: Configurados desde el sistema, aparecen “Solo mis incidencias” y “Recientemente actualizadas” por defecto.

3. **Botón de _Pizarra_**: Desde este botón, se puede gestionar la pizarra, crear nuevas o editar las opciones necesarias o acordes a las necesidades del usuario.

4. **Ver en Tempo**: Se puede acceder al “Time Tracking” del proyecto, donde se ven las imputaciones y las planificaciones de las tareas.

5. **Estados actuales de los elementos del proyecto**: Son las columnas de la pizarra. Dependiendo del esquema seleccionado por el proyecto, aparecen unas columnas u otras (en este caso es un kanban al ser un proyecto interno de un área en concreto).

6. **Elementos del proyecto**: Dentro de cada columna de la pizarra, se muestran los elementos que están en activo en el proyecto para un sprint o entrega en concreto.


## Iconos de acceso a submódulos

Están situados a la izquierda de la página principal del proyecto y nos muestran accesos directos a cada submódulo del mismo. Son los siguientes:

![](/images/qap/jira/22.png)

1. **Trabajo pendiente**: Al pulsar en el submódulo de trabajo pendiente entramos en el listado y organización de los elementos de trabajo del proyecto.

2. **Sprints Activos**: Entramos a la vista de la pizarra del sprint activo que tengamos en el proyecto.

3. **Entregas**: Este submódulo nos reportará las entregas que realizamos en el proyecto en base a las versiones de código que vayamos entregando a validación por parte del equipo de Calidad o a certificación de Cliente.

4. **Informes**: Según el sprint activo o los elementos de trabajo que tengamos, aparecen una serie de gráficas y métricas que nos muestran el estado en el que se encuentra el proyecto en ese momento.

5. **Incidencias**: Se muestra un filtro rápido con los elementos abiertos en el proyecto. Siendo incidencias, cualquier elemento del tipo: “historia de usuario”, “Tarea” o “Error”.

6. **Componentes**: Cada elementos del proyecto se puede “componentizar”. De esta manera podemos añadir diferentes elementos o incidencias a un componente y cuando estén finalizadas, sabremos que el componente está finalizado. Los componentes están compartidos entre los proyectos.

7. **Timesheets**: Desde este enlace, se puede acceder a una vista rápida de las imputaciones y planificaciones realizadas en el proyecto para tener un control del tiempo invertido o que se invertirá en el mismo.

8. **Complementos**: El enlace de complementos no está en uso en TCK.

9. **Enlaces rápidos**: Se pueden añadir una serie de enlaces rápidos a los proyectos para que todo el equipo tenga acceso de un solo vistazo. Por ejemplo a la URL del site de pruebas.

10. **Configuración del proyecto** (solo con usuarios administradores): Se accede a las diferentes opciones de configuración del proyecto.

## Filtros rápidos

En la cabecera de cada submódulo, aparecen una serie de filtros y un buscador para interaccionar con los elementos de trabajo del proyecto:

1. **Lupa**: Podemos realizar cualquier tipo de búsqueda de elemento de trabajo, filtrando por lo que consideremos.

2. **Solo mis incidencias**: se realiza un filtro con las incidencias en las que estamos como responsable (no las que hemos creado nosotros).

3. **Recientemente actualizadas**: aparecen los elementos que hemos actualizado nosotros recientemente.

## Botón de _Pizarra_

En la parte de la derecha, en la cabecera, aparece un botón de _“Pizarra”_, donde aparecen varias opciones relacionadas:

![](/images/qap/jira/23.png)

1. **Configurar**: Desde esta opción se puede configurar la pizarra actual del proyecto para adecuarla a las necesidades que se tengan en ese momento.

2. **Copiar**: Se puede copiar la pizarra actual para llevarla a todos los proyectos que se considere.

3. **Crear _Pizarra_**: Pulsando en esta opción se pueden crear pizarras nuevas y personalizadas de scrum y de kanban.

4. **Mostrar (Ocultar) vista detallada / Ampliar todos los carriles / Contraer todos los carriles**: En estas opciones ampliamos o contraemos la información para ver más detalle en el panel.

5. **Ocultar (Mostrar) etiquetas de épicas**: En esta opción hacemos aparecer o desaparecer las diferentes etiquetas de las épicas, siempre y cuando las historias de usuario estén enlazadas a ellas.

6. **Imprimir tarjetas**: En esta opción se muestran las tarjetas de la pizarra en un formato imprimible para poder compartir con todo el equipo.

## Ver en Tempo

En el botón _“Ver en Tempo”_, tenemos un desplegable con la opción _“Time Tracking”_ donde vemos el tiempo estimado, planificado y trabajado en los elementos que forman el proyecto.

![](/images/qap/jira/24.png)

En esta pantalla se puede filtrar por épicas, sprint y equipo para poder observar el tiempo dedicado de cada uno y sacar las métricas que consideremos.

## Estados actuales de los elementos

En la sección de pizarra se pueden observar los estados en los que se encuentran los elementos de trabajo. Dependiendo del tipo de proyecto, aparecen una serie de columnas dinámicas en las que se puede realizar “drag & drop” de las tarjetas con cada elemento de trabajo. El aspecto de la pizarra es el siguiente (en este caso se está utilizando una serie de elementos sencillos por el tipo de proyecto interno):

![](/images/qap/jira/25.png)

Pulsando con el ratón en la tarjeta del elemento que se considere y arrastrándolo a la siguiente columna o a la anterior de donde se encuentra, el elemento pasa automáticamente a ese estado nuevo y se actualiza.

En los proyectos donde se utiliza el marco de trabajo Agile, se observan los elementos activos en ese sprint.

## Elementos del proyecto

Dentro de la pizarra que se observa y detalla en el punto anterior, se muestran los elementos activos en ese momento tanto en el sprint (si el marco de trabajo es Agile) o en el proyecto (si el marco de trabajo es con Kanban).

Los elementos de trabajo dentro de la pizarra tienen este aspecto:

![](/images/qap/jira/26.png)

En cada elemento, dentro de la pizarra se observa lo siguiente:

* **ID**: Se muestra el ID único del elemento, formado por las siglas del proyecto y un número que no se repite.

* **Prioridad**: La prioridad se marca en base a la necesidad de resolución del elemento.

* **Título**: Título marcado en el elemento de trabajo.

* **Estimación**: La estimación se muestra en un círculo gris debajo de la foto del responsable del elemento.

* **Responsable**: La persona encargada de realizar el elemento de trabajo.

![](/images/qap/jira/27.png)
