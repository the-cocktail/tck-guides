---
title: 4.- Modelo de trabajo
slug: qap-work-model
---

En base al proceso y los elementos descritos en los puntos anteriores, se diseña un modelo de trabajo acorde a las necesidades de _TCK_ y sus proyectos.

El proceso de Calidad y, por lo tanto, el modelo que se va a describir, va a organizarse en diferentes fases, que se van a tratar con detalle en los siguientes puntos. Estas descripciones, ordenan la manera de trabajar a lo largo de los _sprints_, dentro de un proyecto.

En los siguientes puntos se define el marco de trabajo y se tratan las diferentes fases del ciclo de vida del desarrollo de los proyectos de _TCK_.

Dentro de cada fase, se describe una serie de pautas y puntos a seguir, en forma de reunión, para que la interlocución entre las diferentes personas que integran los proyectos se realice de la forma adecuada y se pueda cerrar la fase con total garantía.


### F0 - Fase de inmersión

Es la fase inicial. En ella se va a diseñar el _mapa de proyecto_ que se va a seguir a lo largo de los _sprints_ a realizar y los requisitos que se van a utilizar en el resto de fases.

Además, se diseña el sistema de ramas, entornos y despliegues que se va a utilizar en el proyecto.

![](/images/qap/fase-de-inmersion.png)

Este _mapa de proyecto_ se basa en los siguientes puntos, que se deben de obtener en una etapa temprana de inicio de proyecto:

* _**Formalización**_: Dentro de la formalización de un proyecto se deben realizar los siguientes puntos:

      * **Kick-Off con cliente**: donde se capturan las ideas principales o incluso, hay una nube de ideas donde capturar la información más importante.
      * **Workshops**: se realizan una serie de “encuentros”, donde se van formalizando las ideas iniciales y se las da forma para convertirlas en entregables o ideas a presentar.
      * **Estrategia**: las ideas se ordenan en forma de documento, presentación o similar donde se va cerrando el alcance del proyecto.

* _**Planificación**_: Dentro de la planificación, existen los siguientes puntos que se deben de seguir:
      * **Pautas metodológicas**: se capturan las pautas dentro de la metodología que más se adecuan al proyecto, puede ser no necesario el utilizar todas las disponibles.
      * **Herramientas**: se elabora un sistema de las herramientas que se van a utilizar, en qué lenguaje vamos a desarrollar o que le vamos a aportar al cliente y en qué formato. También se contempla la automatización.
      * **Necesidades**: se acuerda entre _TCK_ y cliente, qué necesidades son las primordiales para llevar a cabo de manera adecuada el proyecto.

* _**Priorización**_: De cara a la priorización, es importante seguir los siguientes puntos:
      * **Cierre de Fechas**: se cierran las fechas previstas para el inicio y finalización del proyecto, además de los hitos que se quieran cubrir.
      * **Acuerdo de Sprint**: en base a las fechas, acordamos la realización de _Sprints_ más o menos largos, sin pasar las cuatro semanas máximas por cada uno.
      * **Entregables**: se marcan los hitos principales, en base a las fechas y qué entregables, con valor de negocio, se van a ir realizando a lo largo de estos _sprints_. Estos marcan los _KPIs_ o controles de Calidad que se van a utilizar en el proyecto. Se hace un esqueleto del _documento funcional_ a presentar y de los casos de prueba.

Una vez que obtenemos toda la información de los puntos anteriores y se han realizado las reuniones correspondientes, se definen y describen, por todas las áreas, los requisitos del proyecto, que cerrarán y darán forma al _mapa de proyecto_ definitivo y serán la base para el trabajo en las siguientes fases.


#### Construcción del _Sprint 0_

La primera reunión interna que hay que realizar, es la reunión de inicio (que será igual que la reunión de inicio de _sprint_, pero con una entidad mayor). En ella, vamos a realizar la apertura del _sprint 0_ del proyecto, además de organizar todas las tareas e intentar adecuar, entre todos, el posible _backlog_ que se irá realizando en posteriores _sprints_.

La idea principal de la reunión, es que todo el equipo del proyecto se siente durante un tiempo estipulado, se acuerden pautas de trabajo y se ordene el camino para que todos lo sigan y tengan la misma idea en la cabeza.

Entre todos, se toman las prioridades y necesidades de negocio del cliente, se determinan cuales van a ser las funcionalidades que se incorporan al primer _sprint_ y se estiman, si fuese necesario.

Para esta reunión, **es necesario**, tal y como se puede observar en los puntos anteriores, tener una **base para la realización de los requisitos** que es el fín de la misma.

En esta reunión **es totalmente obligatorio que esté presente todo el equipo de trabajo**.


#### Construcción de los requisitos

Para realizar la construcción de requisitos del proyecto, se debe de realizar una especificación de requisitos adecuada y que cubra una serie de características:

* **Completa.** Se deben de manejar todos los requisitos y que estén en la especificación. Deben de estar reflejadas todas las referencias.
* **Consistente.** Una especificación tiene que ser coherente con todos los requisitos y con la documentación que se genere.
* **Inequívoca.** Los requisitos tienen que estar definidos y redactados de manera clara y entendible para todo el mundo.
* **Correcta.** El software debe cumplir con los requisitos de la especificación.
* **Trazable.** La identificación de cualquier elemento, ya sea _historia de usuario_ o no, se debe de verificar a través de la identificación almacenada y documentada en la especificación.
* **Priorizable.** Los requisitos deben de tener priorización según la importancia de negocio y además, deben de poder clasificarse.
* **Modificable.** Aunque todo requerimiento es modificable, se refiere a que debe ser fácilmente modificable.
* **Verificable.** Deben de poder probarse y verificarse a lo largo de todo el proceso.

Además, al realizar estos, **se deben de describir utilizando la _Plantilla Unificada de Requisitos de The Cocktail_**.

#### Tipos de requisitos

De manera general, existen una serie de tipos de requisitos que deben de seguirse en todo proyecto y nos sirven para poder obtener toda la información para iniciar el proyecto de manera adecuada:

* **Funcional:** Describen lo que tiene que hacer el sistema en el que vamos a trabajar. Dependen, específicamente del tipo de sistema y de los posibles usuarios.
* **No Funcional:** Son aquellos que no se refieren directamente a las funciones que realiza el sistema, sino a propiedades como tiempo de respuesta, capacidad de almacenamiento y otros aspectos como el diseño, temas legales o éticos o de seguridad.
* **Usuario:** Son requisitos que detallan de una manera más coloquial y sin tecnicismos diferentes requisitos para que sean entendibles por todos los usuarios o integrantes del proyecto.
* **Sistema:** Son versiones extendidas de los requisitos de usuario y que se utilizan por desarrollo como punto de partida para el diseño del sistema. Tienen el detalle adecuado a nivel técnico.


#### Priorización de los requisitos

En base a diferentes aspectos, los requisitos se pueden categorizar en tres opciones:

1. **Esenciales:** Son requisitos que hay que realizar de manera obligatoria, que aportan el valor total de la demanda de cliente y que forman parte esencial del proyecto.
2. **Condicionales:** Son requisitos que pueden condicionar el funcionamiento del desarrollo o alguna decisión por parte de cliente. Habitualmente tienen dependencia entre sí. No todos son obligatorios de realizar.
3. **Opcionales:** Son requisitos que se pueden realizar o no y aportan un valor extra. Siempre son valorables si el tiempo para su realización es el adecuado y tenemos margen para introducirlos entre el resto de requisitos obligatorios.


#### Construcción del _mapa de proyecto_

El _mapa de proyecto_, se enfoca en la planificación que se va a realizar en las fases posteriores, marcando diferentes hitos que tienen unas fechas de entrega ya cerradas. Habitualmente, será un cronograma donde estén marcados estos hitos y podamos valorar qué tiempo nos va a llevar un proyecto en sí y cómo vamos a darle forma a lo largo del tiempo del mismo.

Dependiendo de la capacidad del proyecto y del tiempo destinado al mismo, el _mapa de proyecto_ no es un elemento estático, si no, que se debe de ir revisando periódicamente, para ajustarlo y actualizarlo en base a las necesidades que se vayan teniendo.

El _mapa de proyecto_ está cerrado cuando se obtiene toda la información suficiente para generar los requisitos del proyecto, además de información extra que nos sirva para avanzar a la siguiente fase con toda la información al respecto.

Un _mapa de proyecto_ debe de contener:

1. **Planificación a alto nivel**: _Se realiza una planificación estimada de lo que será el proyecto y definir los hitos más importantes._
2. **Requisitos**: _Se define un listado de los requisitos del proyecto que nos sirven como base para las historias de usuario que realizaremos posteriormente._
3. **Información complementaria**: _Se obtiene toda la información posible, que sea independiente de los requisitos para que se pueda realizar el desarrollo correcto del proyecto._

Toda la información debe de estar incluida en la unidad de equipo abierta previamente para organizar toda la documentación del proyecto.


### F1 - Fase de definición

Una vez hemos cerrado la entrega del _mapa de proyecto_ con su información al completo y los requisitos realizados, pasamos a la fase de definición, donde comenzamos a invertir el esfuerzo en la definición de las _historias de usuario_ y como entregable, la realización del _documento funcional_ con toda la información completa y detallada de lo que va a ser el proyecto.

Todos los puntos que entran dentro de esta fase se basan en toda la información recabada a lo largo de la fase de inmersión.

![](/images/qap/fase-de-definicion.png)

En esta fase de definición y entrando más en detalle, se deben de realizar los siguientes puntos, antes de continuar a la siguiente:


* **_Historias de usuario_**: Se definen las _historias de usuario_ entre todas las áreas, respetando y siguiendo los requisitos completados en la fase anterior. Como entregable a cliente, se puede utilizar la _Plantilla Unificada de Historias de Usuario de The Cocktail_.

* **Apartado técnico**:  Dentro del _documento funcional_, existe un apartado técnico que cubre estrictamente las necesidades de tecnología y define la arquitectura a seguir.


* **Criterios de aceptación**: Se cierran los criterios de aceptación con el cliente, que los usará posteriormente para certificar los entregables.


* **Documento funcional**: Se completa el _documento funcional_ con toda la información de los puntos anteriores y la referencia al documento de _historias de usuario_. El _documento funcional_ integra toda la información referente a los requisitos con total detalle y que _historias de usuario_ los cubren.


#### Construcción de _historias de usuario_

Por definición, la _historia de usuario_ es una representación de un requisito utilizando una frase corta en lenguaje coloquial y entendible, que no sea técnico.

Las _historias de usuario_ deben de cubrir una serie de características para que sean lo más adecuadas posible:

* **Independientes:** Las _historias de usuario_ han de ser independientes, tienen que aportar valor por sí mismas.
* **Negociables:** Las _historias de usuario_ deben de ser negociables entre las diferentes áreas implicadas de cara a dejar explícito el alcance de la misma.
* **Valoradas por los clientes:** Cada historia debe de tener un valor total de cara a cliente. Estas deben de ser valoradas como su entrega final.
* **Estimable:** Las _historias de usuario_ han de poder estimarse para completarlas. Lo ideal es dentro de un _sprint_.
* **Pequeñas:** Si el tamaño de una _historia de usuario_ no es el adecuado, no puede estimarse. Debe de permitirse el cubrir la funcionalidad en una sola iteración.
* **Verificables:** Las _historias de usuario_ tienen que cubrir los requisitos y por lo tanto han de poder ser verificables por el área de calidad. Incluso pueden llegar a automatizarse.

La _historia de usuario_ queda terminada cuando esté dispuesta toda la información referente a la misma.


#### Construcción del apartado técnico

Dentro del _documento funcional_, debe de existir un apartado técnico que cubra las especificaciones definidas. Este apartado técnico debe de contener lo siguiente:

* Arquitectura propuesta para el proyecto.
* Modelado de arquitectura.
* Diagramas de flujo o de estado según las necesidades.
* Información técnica y funcional en base al proyecto.


#### Construcción de los criterios de aceptación

Cada _historia de usuario_ debe de contener unos criterios de aceptación, que al fin y al cabo son las acciones que deben de cubrir el comportamiento correcto de la misma. Deben de cubrir las siguientes preguntas:

* ¿Se ha construido el producto correcto?
* ¿Se ha construido el producto correctamente?

Los criterios de aceptación se describen mediante tres puntos clave: un contexto, una respuesta y una consecuencia esperada.

Los criterios de aceptación deben de tener el siguiente formato:

_**Dado** <usuario y acción a realizar>_
_**Cuando** <acción esperada>_
_**Entonces** <acción que realiza el sistema>_

Por ejemplo:

1. **Dada** una petición a la página de búsqueda **cuando** se carga la página en el navegador **entonces** el cursor se desplaza al cuadro de búsqueda para que el usuario pueda comenzar a teclear de inmediato.
2. **Dado** que el usuario está en el cuadro de búsqueda y el usuario ha hecho login con su cuenta de Google **cuando** el usuario pulsa sobre el mismo cuadro de búsqueda **entonces** se le muestra una lista con sus últimas búsquedas.
3. **Dado** que el usuario está en el cuadro de búsqueda **cuando** el usuario teclea algo **entonces** se le muestra una lista con sugerencias de búsqueda relacionadas con lo que ha tecleado.


#### Apertura y revisión del Backlog

La generación del _backlog_ se realiza tras la aprobación del _mapa de proyecto_ y la definición de las _historias de usuario_. Cada área tendrá diferentes tareas a realizar sobre esas _historias de usuario_ y por lo tanto deben de transcribirse en el mismo.

Una vez que se realiza la priorización de los elementos de trabajo, estos, se subirán al _sprint_ que comience para que se pueda empezar a realizar el trabajo en cada uno de ellos. Esta priorización marca las necesidades de negocio y del producto en sí.

En esta fase también se continúa con la elaboración y ampliación del esqueleto de casos de prueba que posteriormente vamos a cerrar.


#### Priorización de los elementos de trabajo

Dentro del marco de trabajo, el _backlog_ marca hitos en base al _sprint_ en el que estemos trabajando. La priorización de los elementos es de suma importancia para comprobar cuales tienen que realizarse en primer lugar o cual puede ser posterior (esto es muy útil de cara al trabajo con defectos).

La priorización debe de realizarse en una reunión de priorización y planificación donde, entre todas las áreas, se deben de considerar los elementos que van a ser entregados en ese ciclo de tiempo.

La priorización que se lleva a cabo en la herramienta de trabajo que se utiliza en _TCK_ es la siguiente:

1. **Highest**: son los elementos críticos para el proyecto, son totalmente fundamentales para que el hito de negocio se cumpla, por lo tanto, en el caso de que no se cumpla, se considera que este ha fracasado.
2. **High**: Son los elementos importantes, pero no imprescindibles, por lo tanto, deben de entregarse, pero pueden tener un cierto retraso o pueden pasarse a otro _sprint_ si no llegamos en plazo. El hito no fracasa si este elemento no es entregado en el plazo determinado.
3. **Medium**: Son elementos que deben de realizarse en un periodo corto, no son importantes, pero marcan una continuidad de la calidad y del desarrollo dentro del _sprint_. Cubren expectativas de cliente.
4. **Low**: Mejoran la experiencia de usuario o la satisfacción de cliente, pero no afectan a la funcionalidad de que se va a entregar.
5. **Lowest**: habitualmente son mejoras, no están planificadas y surgen a lo largo del _sprint_. Se pueden reconsiderar o incluso eliminar por no aplicar.


#### Construcción del _documento funcional_

El _documento funcional_ debe de ser el primer paso a la hora de comenzar el desarrollo del proyecto y debe de marcar una hoja de ruta a seguir.  Para que un _documento funcional_ sea lo más correcto posible hay una serie de puntos importantes que se deben de tener en cuenta:

* Con el _documento funcional_ se puede evaluar la viabilidad técnica y económica de los procesos de desarrollo del proyecto.
* Se explican, de forma detallada, los diferentes requisitos funcionales y no funcionales a implementar que están introducidos en las _historias de usuario_ que se realicen en el proyecto.
* Analiza, controla y supervisa el desarrollo funcional de la aplicación, pudiendo obtener un desarrollo óptimo.
* Ayuda a realizar diferentes metodologías de validación y asegura la buena definición del plan de pruebas.
* Es la hoja de ruta para que todas las personas involucradas en el proyecto tengan toda la información del mismo y puedan trabajar en la misma línea.


#### _Definition of Ready_ (DoR) y _Definition of Done_ (DoD)

Cuando trabajamos con _historias de usuario_ es totalmente imprescindible el marcar dos definiciones a lo largo del proyecto para las mismas. Estas son, la definición de _*Ready*_ (o “listo”), y la definición de _*Done*_ (o “cerrado”). En los siguientes puntos vamos a dar una serie de criterios para verificar y acordar el marcado de estas dos definiciones.

##### Criterios para la realización del _“Definition of Ready”_

Para realizar el _“Definition of Ready”_, debemos de apoyarnos en una serie de criterios que pueden ser similares a los siguientes:

* Que la _historia de usuario_ pueda ser abordada y terminada en el _sprint_ sin tener bloqueos, dependencias, o impida que esto suceda.
* Todas las dependencias deben de quedar resueltas antes de empezar a trabajar con la _historia de usuario_.
* La complejidad de la _historia de usuario_ no debe de superar la estimación dada por el desarrollador para el _sprint_. Si esto es así, debe de dividirse en tareas pequeñas, que sigan aportando valor y sean más sencillas o abordables.

##### Criterios para la realización del _“Definition of Done”_

Prácticamente la definición más importante de un proyecto es la definición de cerrado para las _historias de usuario_. Sin esta definición, nunca sabremos cuando damos las cosas por completadas y por lo tanto, el _sprint_ jamás podría cerrarse o finalizarse.

Se pueden aplicar los siguientes criterios para marcar esta definición:

* La _historia de usuario_ debe de cumplir los estándares de calidad definidos, pasando todos los casos de prueba y tener todos los checks en verde.
* La _historia de usuario_ tiene que haber sido validada y verificada.
* La _historia de usuario_ tiene que haber sido puesta en producción o haberse realizado la petición para ello.


### F2 - Fase de implementación


La fase de implementación es la fase de desarrollo (no solo técnico, si no también funcional o aplicado a cada área) propiamente dicha. Este desarrollo se basa en la documentación funcional y en las _historias de usuario_. Además, de toda la información que va proporcionando el resto de áreas para que el desarrollo sea completo.

![](/images/qap/fase-de-implementacion.png)

Cada área, debe de participar en el desarrollo de las _historias de usuario_ que le apliquen. Desde tecnología, se comienzan a desarrollar las _historias de usuario_ tanto a nivel de _back_ como de _front_. Puede existir la posibilidad de que se creen varios _sprint_ en los que existan fases de desarrollo en los que no intervenga tecnología, siendo completados por el desarrollo del resto de áreas.

En esta fase, se deben de completar los siguientes puntos, para poder tener la garantía suficiente de que se ha realizado de una manera correcta:

* **Desarrollo de las _historias de usuario_**: Cada área realiza el desarrollo apropiado para finalizar y entregar la historia de usuario a cliente dentro del _sprint_ especificado.
* **Testing desarrollo**: Antes de dar por finalizada la historia de usuario y pasar al área de calidad para su validación es necesario realizar una serie de pruebas en desarrollo que están dentro del marco de trabajo especificado en la estrategia de testing para TCK.
* **Plan de pruebas**: El _Area de Calidad y Procesos_, define y completa el plan de pruebas de las _historias de usuario_ basándose en toda la información que han ido aportando el resto de áreas.
* **Demo**: La entrega de esta fase desemboca en una demo interna que se realiza con las personas que se consideren, y cuyo responsable de desarrollo se encargará de mostrar para que se dé el visto bueno para desplegar al _entorno de PRE_, donde se comenzará con su validación.

Una vez que se completan todos los puntos anteriores, se puede dar el paso a la siguiente fase. En la entrega de esta fase, la demo, es cuando se da el visto bueno final a todo lo realizado.


#### Construcción del plan de pruebas

El plan de pruebas que se especifica en esta fase, está cumplimentado con una serie de casos de prueba, que a su vez, agrupa una serie de pasos de prueba.

De cara a realizar una serie de buenas prácticas para crear un buen plan de pruebas, se deben de cumplir los siguientes puntos:

* **Entendibles:** el caso de prueba tiene que realizarse manera sencilla, con un lenguaje claro y fácil de ejecutar.
* **Eficientes:** El caso de prueba debe de alcanzar la mayor cobertura posible y que encuentre el mayor número de errores.
* **Certificables:** Lo ideal es que los casos de prueba sean revisables por el resto del equipo o incluso certificados por cliente para verificar que se cubre todo lo que se consideraba desde un inicio.
* **Revisables:** Es importante, mantener una cierta revisión en los casos de prueba para actualizarlos con posibles cambios que se produzcan a lo largo del proyecto.
* **Objetivos:** El caso de prueba debe ser objetivo y centrarse en una sola funcionalidad, esto permite centrarse solo en una cosa en concreto.
* **Autosuficientes:** El caso de prueba debe de contener toda la información completa para poder ejecutarlo y ser todo lo detallado que se pueda.
* **Concretos:** Los casos de prueba tienen que ser cortos, concisos y concretos. Deben de ir al grano y no tener muchos pasos. Si es así, es preferible partirlo en dos que realizar uno con un tamaño mayor.
* **Efectivos:** los casos de prueba que se acercan más a las acciones de los usuarios finales acaban encontrando defectos graves de manera más sencilla.


#### Ajuste de _sprint_

La reunión de ajuste de _sprint_ es opcional y permite, a mitad del _sprint_ aproximadamente, el realizar los ajustes necesarios si existe una desviación conocida o que prevemos que puede afectar la entrega final a cliente.

En esta reunión, se trata la desviación, se inicia una estrategia para solucionarla y si fuese necesario, se comunica a cliente lo antes posible para que las expectativas finales se adecuen al resultado propuesto.

En esta reunión es totalmente obligatorio, si se realiza, que estén las áreas afectadas.


### F3 - Fase de validación

Una vez se supera la fase anterior, comienza la fase de validación, donde existe una integración con el _entorno de PRE_ y se realiza la ejecución del plan de pruebas.

![](/images/qap/fase-de-validacion.png)

Esta ejecución nos da el resultado positivo o negativo de los elementos de trabajo y se abren los defectos correspondientes que serán reportados al área de desarrollo para su resolución.

Estos defectos se introducen en el _backlog_, correctamente priorizados y se irán metiendo al _sprint_ de manera progresiva y en orden de prioridad, para completar, cuanto antes, los críticos. Cuando el defecto se soluciona, se vuelve a ejecutar el caso de prueba que había quedado fallado y se comprueba que, efectivamente, todo funciona correctamente.

Esta etapa se da por finalizada cuando todas las _historias de usuario_, que estaban priorizadas, tienen un funcionamiento correcto y adecuado y son aptos para continuar con la siguiente fase.

Para que esta fase se realice de manera correcta, es necesario la realización de los siguientes puntos:

* **Validación calidad:** Se realiza la validación adecuada para garantizar el correcto funcionamiento de las _historias de usuario_ entregadas. Esta validación debe de cumplir la ejecución de los casos de prueba, las pruebas exploratorias que apliquen a las mismas y las pruebas de humo finales que dan el OK al entregable.
* **Certificación interna:** Cada área implicada en las _historias de usuario_ realiza una certificación interna que dará el OK definitivo a la misma y podrá ser entregada a cliente.
* **Informe de entrega:** Se realiza un informe de entrega con la información que se acuerde para entregar a cliente y comience la certificación.
* **Versionado:** La entrega de esta fase es la versión a la que se le ha dado el OK de manera interna, por todas las áreas del proyecto.


#### Construcción del informe de entrega

El informe de entrega de versión, es uno de los puntos más importantes de cara a realizar el aviso a cliente para que pueda certificar. Este informe, debe de contener los siguientes puntos:

* **Historias de usuario**: Una sección de las _historias de usuario_ y _criterios de aceptación_ que se van a entregar en este _sprint_ y que el cliente puede certificar y ver en el _entorno de QA_.

* **Historias de usuario en _Gherkin_**: Una sección con la traducción de las historias de usuario pasadas a _Gherkin_ que cubren el test unitario y de integración realizado.
* **Resultado del plan de pruebas**: Sección donde aparecen estadísticas de la última ejecución del plan de pruebas.
* **Resumen**: Se explica el resumen total del proceso que se ha seguido en el _sprint_ y si existiese algún tipo de problema detectado y que se está trabajando en ello, se debe de especificar aquí para que el cliente tenga toda la visión de la entrega.


#### Reorganización de tareas

Tras la validación por parte del área de calidad y en el caso de que en la misma se encuentren un porcentaje alto de defectos críticos o bloqueantes, es necesario realizar una reunión de reorganización.

En esta reunión, se marcan las pautas a seguir para la resolución de estos defectos para poder solventar la entrega de la versión que se va a entregar en el _sprint_.

En esta reunión es totalmente obligatorio que estén las áreas afectadas.


### F4 - Fase de certificación

La fase de certificación comienza con el despliegue de la versión en el _entorno de QA_. De esta manera, los clientes pueden realizar una certificación, basándose en los criterios de aceptación, para comprobar que lo que se les entrega cumple con las expectativas que buscaban.

![](/images/qap/fase-de-certificacion.png)

Para que esta fase se realice de manera correcta, se deben de seguir los siguientes puntos:

1. **Regresión en QA:** Antes de dar el OK a cliente para que acceda al entorno para certificar, el _Área de Calidad y Procesos_, realiza una mínima regresión asegurándose de que todo está desplegado de manera adecuada.
2. **Aceptación de criterios:** El cliente certifica las _historias de usuario_ con los criterios de aceptación que se acordaron al inicio.
3. **Retrospectiva:** Es la entrega final de esta fase y que da el pistoletazo de salida al despliegue a producción.

Una vez que se cumplan estos puntos, el _sprint_ se da por finalizado y obtenemos una versión estable y garantizada para el usuario final.


#### Entrega de versión _certificada_

La entrega se inicia cuando se captura la versión estable y _certificada_ por cliente y es desplegada al entorno de producción para ser entregada a los usuarios finales.

Antes de dar acceso a los clientes finales, es necesario que el _Área de Calidad y Procesos_ realice una regresión mínima que garantice que todo se ha desplegado de manera correcta y adecuada.


#### _Retrospectiva_, cierre de _sprint_ e inicio de nuevo _sprint_
De cara a mantener la sostenibilidad del tiempo por parte de las diferentes áreas de trabajo, se acuerda la unificación de una única reunión para la realización de los tres hitos finales del _sprint_.

La _retrospectiva_, permite interactuar entre todos los miembros del equipo, mediante las siguientes cuestiones:

* **¿Qué ha funcionado bien?**
* **¿Qué hay que mejorar?**
* **¿Qué no ha funcionado bien?**
* **¿Qué vamos a hacer para mejorarlo?**

Cada persona escribirá en un _post-it_ las respuestas que necesite y se ordenarán en la pizarra. De esta manera se sacarán las medidas correctoras y mejoras para los siguientes _sprints_ (o proyectos, si es la última retrospectiva del mismo). En el caso de que no sea la última retrospectiva del proyecto, se realiza también un _cierre de sprint_, ordenando las tareas en el siguiente y priorizándolas adecuadamente y se procede a abrir el siguiente, comenzando el trabajo desde ese mismo momento.
