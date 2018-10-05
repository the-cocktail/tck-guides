---
title: 2.3.- Elementos de trabajo
slug: qap-work-elements
---

En base al marco que se ha descrito anteriormente, se han especificado una serie de elementos que engloban el trabajo a realizar en las diferentes áreas y permite entregar con garantía a los clientes.

La jerarquía de los elementos ha de cumplirse estrictamente, ya que todo el trabajo que se va a realizar en cada _sprint_ se basa en ello. La idea principal de esta jerarquía es que los elementos superiores agrupan a los inferiores, capturando el valor propio de negocio, cuanto más arriba esté el elemento.

El valor máximo de negocio es la _épica_, completado por las historias de usuario. A continuación, aparecen las tareas y los defectos, que no tienen valor de negocio y que, simplemente describen el trabajo a realizar de manera interna. En el caso de defecto, solucionan algún tipo de problema encontrado a lo largo de un _sprint_ o versión.

En los siguientes puntos, podemos observar, con más detalle cada elemento de trabajo utilizado en el proceso de calidad de _TCK_.


#### Épica

Son los elementos superiores que agrupan al resto y se pueden realizar a lo largo de varios _sprints_. En los siguientes puntos, se detallan en profundidad las acciones que se realizan dentro de ellas.

Las épicas tienen un valor global, por sí mismas, de cara a cliente y cumplen los siguientes criterios de manera obligatoria:


* Aportan un valor empresarial o de negocio.
* Son estimables de cara a disgregarse en diferentes historias de usuario y tareas que entren en un _sprint_.
* Son comprobables. El cliente debe de poder comprobar el valor real de la épica.

Las épicas forman parte de la planificación que se ha cerrado con el cliente y, por lo tanto, son los hitos más importantes que hay que cumplir para que el proyecto se desarrolle en fecha y con garantía. Estas _épicas_, a su vez, están disgregadas en diferentes controles que aplican a cada área y que se encargan de medir el trabajo realizado y entregado por las mismas y si ha sido correcto o no, posibilitando la mejora continua dentro de cada _sprint_.


#### Historia de usuario

Una historia de usuario es un elemento con valor de negocio por sí mismo. Junto con las tareas, engloba y forma cada _épica_ y son atómicas, es decir, se pueden poner en producción por sí solas y aportan el valor suficiente a cliente para su utilización.

Las historias se completan a través del documento funcional (o requisitos funcionales) y tienen que contener toda la información posible para que las diferentes áreas puedan trabajar de la manera más adecuada.

Una historia de usuario tiene que cumplir los siguientes criterios:

* **Ser atómica**, para entrar en un solo _sprint_. Aunque puede retrasarse y postergarse, puede llegar el momento en que una historia pueda separarse en dos o en las que sean necesarias.
* **Tener valor por sí misma**, de cara al cliente, a la hora de finalizar y desplegar en producción.
* **Ser estimable**. La definición tiene que ser suficiente para que las áreas de trabajo proporcionen una estimación idónea en las reuniones de inicio de _sprint_.

La historia de usuario tiene que contener de manera obligatoria y lo más específicamente posible una buena definición, unos criterios de aceptación y toda la información adjunta que sea posible.

#### Tarea

Las tareas son unidades que se realizan a lo largo de los _sprints_. Cubren el trabajo a realizar en las diferentes áreas y habitualmente sirven para marcar las pautas a realizar de cara a las diferentes historias de usuario. Cada tarea contiene un esfuerzo que se debe de cumplimentar obligatoriamente, además, solo pueden depender de una persona.

#### Defecto

Los errores son los elementos que contienen los problemas encontrados a lo largo de los diferentes _sprint_ o entregables del proyecto. No tienen que ser siempre problemas de mal funcionamiento, también pueden ser carencias, peticiones o revisiones dentro de estos entregables.

Es muy importante la correcta priorización de los errores, para que se introduzcan en el _sprint_ desde los más críticos hacia los menos.

#### Caso de prueba

Los casos de prueba son elementos de trabajo que comprueban los pasos a seguir para garantizar el correcto funcionamiento de los mismos a nivel funcional y no funcional. Pueden ser automáticos o manuales.

Estos elementos de trabajo pueden ir asignados a un elemento superior o no, ya que pueden probar secciones de la plataforma de manera transversal sin ser desarrollos directos.

El caso de prueba no tiene persona asignada ya que es un elemento que se puede ejecutar por cualquiera dentro del proyecto. Son elementos transversales entre áreas y personas.
