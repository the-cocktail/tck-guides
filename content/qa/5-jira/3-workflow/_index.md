---
title: 3.- Flujo de trabajo en Jira
slug: workflow
---

En este punto se describe el flujo de trabajo previsto en _Jira_ para _The Cocktail_, cómo se interactúa con los estados de la herramienta, y qué responsabilidades tiene cada perfil.

Es imprescindible que todos los integrantes de un proyecto utilicen este manual, y que el equipo unifique como se interactúa con la herramienta.

El flujo de trabajo en el que se apoya toda la información relacionada con este punto es el siguiente:

![](/images/qap/jira/31.png)

A continuación, se detallan todos los pasos que hay que realizar en cada estado, así como las responsabilidades que aplican en cada uno.

## _Nuevo_

El primer estado para cualquier elemento es _“Nuevo”_. Este, marca que el elemento se está diseñando o completando para comenzar a trabajar en él.

Lo más importante en este primer estado es cerciorarse de estar eligiendo correctamente el tipo de elemento que se quiere abrir. Existen tres:

1. **Historia de usuario** ![](/images/qap/jira/ico-historia_de_usuario.png)
 Este elemento sólo se debe abrir al inicio del proyecto y cuando se definen las historias de usuario que lo completarán. Pueden surgir nuevas historias de usuario, pero siempre serán en las reuniones de inicio de _sprint_ o de revisión del backlog.

2. **Tarea** ![Tarea](/images/qap/jira/ico-tarea.png)
 Este es el elemento que habitualmente utilizaremos a la hora de realizar una labor o trabajo concreto sobre una historia de usuario.

3. **Error** ![](/images/qap/jira/ico-error.png)
 Este elemento se abrirá cuando entremos en la fase de validación, y tendrá que ser revisado a lo largo de la misma.

Para abrir un elemento de trabajo, debemos de pulsar en los siguientes enlaces:

![](/images/qap/jira/32.png)

Es un estado muy útil a la hora de organizarse y saber qué elementos son factibles de empezar a trabajar en ellos. El elemento se crea en el _Backlog_. En este estado y antes de pasar al siguiente, se deben de cumplimentar los siguientes puntos:

* **Etiqueta de equipo** (en el punto _“3.3 Guía de etiquetas de trabajo”_): Se añade la etiqueta en el título según el equipo, por ejemplo: _“DEV - Título”, “UI - Título”_...

* **Responsable de la tarea**: La tarea tiene que tener ya el responsable que la va a realizar y canalice toda la información de la misma.

* **Fase y épica**: Se añade la fase (si aplica) y la épica a la que se quiere añadir la tarea.

## _Por hacer_

El estado siguiente, es _“Por Hacer”_. En este estado, ya se ha introducido toda la información valiosa de ser utilizada en los siguientes estados y por las siguientes personas del proyecto (si fuese necesario) se le introduce una épica y una fase.

![](/images/qap/jira/33.png)

Este estado **ya entra en un _sprint_ y se planifica adecuadamente**. Además, se debe de priorizar en base a los siguientes criterios:

* **Highest**: son los elementos críticos para el proyecto, son totalmente fundamentales para que el hito de negocio se cumpla, por lo tanto, en el caso de que no se cumpla, se considera que este ha fracasado.

* **High**: Son los elementos importantes, pero no imprescindibles, por lo tanto, deben de entregarse, pero pueden tener un cierto retraso o pueden pasarse a otro _sprint_ si no llegamos en plazo. El hito no fracasa si este elemento no es entregado en el plazo determinado.

* **Medium**: Son elementos que deben de realizarse en un periodo corto, no son importantes, pero marcan una continuidad de la calidad y del desarrollo dentro del _sprint_. Cubren expectativas de cliente.

* **Low**: Mejoran la experiencia de usuario o la satisfacción de cliente, pero no afectan a la funcionalidad de que se va a entregar.

* **Lowest**: habitualmente son mejoras, no están planificadas y surgen a lo largo del _sprint_. Se pueden reconsiderar o incluso eliminar por no aplicar.

## _En progreso_

El estado _“En progreso”_, comienza cuando se va a empezar a trabajar en concreto en lo que se ha descrito en el estado anterior. La persona responsable de esta tarea tiene que cubrir las estimaciones propuestas, y debe de ser consciente de que si existe una desviación en las mismas, **se ha de replanificar** para ajustar tiempos en el resto de las áreas.

En este estado, se comienzan a imputar las horas trabajadas en el elemento en concreto.

## _Listo para despliegue_

En este estado, la persona encargada de hacer la revisión sobre ese tipo de elemento, comenzará su trabajo. Para ello, es indispensable que se le asigne a la misma, de esta manera, se recibe un email donde se le avisa adecuadamente.

En este momento, la persona que ha dejado la tarea _“Para revisión interna”_ tiene que ser consciente de que **debe de aportar toda la información que pueda** para que no exista ninguna duda en esta revisión posterior. Se finaliza de imputar por la persona que lo ha tenido en estado _“En progreso”_.

## _En revisión_

La nueva persona a la que se le ha asignado este elemento de trabajo, comienza a realizar el trabajo de revisión (ya sea por el área de calidad o por el área que aplique).

Si esta revisión tiene **un resultado incorrecto la tarea vuelve a estado _“Por Hacer”_**, y se le vuelve a asignar al responsable de haberla realizado para que solvente las  deficiencias detectadas si estas existen. Este paso **puede ir acompañado de una serie de defectos adicionales** que se deben solventar antes de devolver la tarea a estado _“Para revisar”_.

Si la revisión tiene un resultado correcto, la tarea pasa a estado _“Cerrado”_.

## _Cerrado_

Este estado es el definitivo, y el que marca la definición de _“done”_ de los proyectos de _The Cocktail_. En este momento, el elemento ha sido revisado por el área correspondiente y **se puede proceder a la  entrega a cliente para certificar**.
