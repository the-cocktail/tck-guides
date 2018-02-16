---
title: "Glosario"
slug: glosario
weight: 20
pre: "<i class='fa fa-book'></i> "
---

## Cobertura

Es una métrica que indica qué porcentaje del código de la aplicación está siendo probado por los tests. Hay que tener cuidado con ella porque puede generar una falsa sensación de seguridad: una cobertura alta no es sinónimo ni de robustez del código ni de calidad de los tests, pero al mismo tiempo probablemente no queremos que haya una cobertura baja.

No obstante, hay que tener en cuenta que en el testing no se trata de llegar al 100% de cobertura. Se trata de testear de forma adecuada cada parte de la aplicación. Las funcionalidades críticas mediante [tests de integración](#test-de-integraci%C3%B3n), los casos extremos con [tests unitarios](#test-unitario), etc. y siempre bajo el criterio de quien desarrolle la aplicación. ¿Merece la pena testear una vista en un test unitario? Normalmente no, pero depende del caso. En el fondo es una cuestión de retorno de inversión.

## Mantenibilidad

En el contexto del testing, que los tests estén desacoplados del código se traduce en una mayor mantenibilidad de los mismos. En el caso de los [tests de integración](#test-de-integraci%C3%B3n) es fácil conseguir esto si se siguen [buenas prácticas](#buenas-practicas).

## Historia de usuario

Es una representación por escrito de un requisito de la aplicación contada desde el punto de vista del usuario. Es importante que esté expresada en términos del cliente y jamás debe incorporar jerga técnica (a no ser que el negocio del cliente tenga que ver con asuntos técnicos, obviamente).

Es muy habitual el formato [Gherkin](https://github.com/cucumber/cucumber/wiki/Gherkin), con la estructura _Given-When-Then_.

## Step

Es cada una de las líneas que componen una historia de usuario:

```
Dado un usuario registrado
Si visita la home
Entonces ve un mensaje de bienvenida
```

Ejemplo:

```ruby
step "visita la home" do
  visit home_path
end

step "ve un mensaje de bienvenida" do
  expect(page).to have_text("¡Hola!")
end
```

Estos _Steps_ deben implementarse siguiendo [buenas prácticas](#buenas-practicas).

## TDD

Test-driven development. Metodología de desarrollo que requiere que los tests se escriban __antes__ de la funcionalidad.

Incluso en el caso de proyectos que ya están funcionando, puede (y debe) hacerse TDD a la hora de solucionar [regresiones](#regresi%C3%B3n).

## Test de integración

A diferencia de los [tests unitarios](#test-unitario), los test de integración prueban todo el stack interactuando con la aplicación como si de un usuario final se tratase. Son por tanto ideales para asegurar el correcto funcionamiento de funcionalidades críticas para el negocio.

Su mayor pega es que son lentos, y sus ventajas es que son fáciles de escribir, no requieren mayor conocimiento del código de la aplicación si se [evita el acoplamiento en los steps](#evitar-el-acoplamiento-en-los-steps), que además conlleva un incremento de su [mantenibilidad](#mantenibilidad).

## Test funcional

Se utilizan para testear parte de la aplicación sin llegar a levantar todo el stack, pero implicando varias clases o funciones. Queda a criterio de la persona que los implemente saber cuándo y por qué es necesario un test funcional y no varios unitarios o uno de integración.

Un caso típico sería una test de una clase pero que necesita interactuar con la base de datos (y por tanto tiene como mínimo una dependencia en el ORM y en la propia base de datos).

## Test unitario

Pruebas de código que verifican el funcionamiento de clases/métodos/funciones de forma aislada, sin dependencias. Tienen la ventaja de que se ejecutan mucho más rápido que los [tests funcionales](#test-funcional) o los de [integración](#test-de-integraci%C3%B3n).

1. Ayudan a diseñar buen código.
  * Si una clase o una función es difícil de testear es que está mal diseñada o tiene demasiadas responsabilidades.
  * Para obtener el mayor beneficio de este punto lo ideal es hacer [TDD](#tdd).
2. Son ideales para testear casos extremos de forma rápida.
  * Por ejemplo, un sistema de descuentos en el que haya que probar que se aplican correctamente según diferentes criterios, a saber: compra mínima, peso del pedido, productos que ya tienen descuento, etc. Probar todos los casos con tests de integración sería demasiado lento.
3. Son ideales para reproducir bugs y evitar regresiones sin falta de tener que levantar todo el stack en un test de integración para el mismo cometido.
4. Similar al punto 3, pueden usarse para testear casos erróneos.
  * Otra vez, usar tests de integración para probar cada caso en el que puede aparecer un error en pantalla es excesivo e ineficiente.

La desventaja de los tests unitarios es que son más difíciles de escribir y de mantener y requieren por tanto más experiencia que los de integración. No resulta siempre fácil que estén desacoplados del código (aunque el acoplamiento suele ser un indicativo de que o bien el test no está bien pensado o el código que se está testeando no está bien diseñado).

## Fragilidad

Un test frágil es aquel que tiene más probabilidad de fallar debido a cambios en la implementación, incluso aunque el comportamiento no haya cambiado. Esto es, es un test que está acoplado con el código que testea.

Los tests deben siempre comprobar que el __comportamiento__ de la aplicación es el adecuado, nunca la __implementación__. En resumen, los tests deben ser pruebas de __caja negra__.

## Especificación ejecutable

Un test escrito de forma consensuada con el cliente en forma de [test de integración](#test-de-integraci%C3%B3n). La clave aquí es que la especificación no deja de ser un __contrato__ con el cliente: __especifica qué debe hacer la aplicación y evita regresiones__.

## Regresión

Aparición de un bug en una funcionalidad que hasta ahora funcionaba sin problema.
A la hora de solucionar este tipo de bugs, lo que se debe hacer es usar [TDD](#tdd): reproducimos el bug en un test, y lo hacemos pasar.

## Product Owner

Este término proviene de scrum, pero en cualquier proyecto sería el rol desempeñado por la persona que ejerce de interlocutor con el cliente: conoce el proyecto, las necesidades de negocio y sabe priorizar tareas e identificar las funcionalidades críticas.

## Refactorizar

Es un proceso que no afecta a la funcionalidad, y que sólo persigue mejorar el diseño del código. En un proyecto sin tests la
