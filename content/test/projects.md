---
title: "Proyectos"
slug: proyectos
weight: 10
pre: "<i class='fa fa-folder-open'></i> "
---

## Proyectos existentes

1. Identificar __funcionalidades críticas__ para el negocio,
2. Escribir __historias de usuario__ de esas funcionalidades,
3. Implementar los __tests de integración__ de las historias de usuario.

En un proyecto que ya está funcionando y en el que por tanto no vamos a hacer [TDD](tdd), el objetivo es añadir [tests de integración](#test-de-integraci%C3%B3n) para __funcionalidades críticas__ y así evitar [regresiones](/test/glosario/#regresi%C3%B3n).

Idealmente es el cliente o en su defecto el [_Product Owner_](#product-owner) quien debe identificar dichas funcionalidades y escribir [historias de usuario](#historia-de-usuario) que el equipo de desarrollo se encargará de implementar como [especificaciones ejecutables](#especificaci%C3%B3n-ejecutable) en forma de [tests de integración](#test-de-integraci%C3%B3n).

Una vez identificadas y escritas las historias de usuario en formato [Gherkin](https://github.com/cucumber/cucumber/wiki/Gherkin), debe implementarse el código que interactúa con la aplicación ([Steps](#steps)). Para ello podemos valernos de librerías como [Cucumber](https://github.com/cucumber/cucumber/) o [Spinach](https://github.com/codegram/spinach) (ruby) o [Behat](http://behat.org/) (PHP).

Idealmente, en este último paso deberíamos seguir las [prácticas](#buenas-practicas) recomendadas más abajo.

Estos tests simplemente deben replicar lo que el usuario haría: pinchar en enlaces y botones, rellenar formularios, etc. para después comprobar que el estado de la aplicación y de la interfaz es el que se espera.

No es un escenario ideal porque al estar ya en funcionamiento la aplicación todos los participantes en el proyecto van a estar condicionados a la hora de escribir las historias y los tests (en contraposición a [TDD](#tdd)).

## Nuevos proyectos

En un proyecto nuevo el objetivo es hacer [TDD](#tdd). Los pasos a seguir en realidad son los mismos que en un [proyecto existente](#proyectos-existentes), con la diferencia de que los tests de integración han de estar escritos __antes__ de hacerlos pasar.

Es un escenario ideal en el que los tests de integración son aún más si cabe [especificaciones ejecutables](#especificaci%C3%B3n-ejecutable) y que además permite recopilar las historias de usuario de una forma más eficiente mediante metodologías como [Event Storming](https://en.wikipedia.org/wiki/Event_storming).
