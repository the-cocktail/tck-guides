---
title: "Buenas prácticas"
slug: buenas-practicas
weight: 30
pre: "<i class='fa fa-thumbs-up'></i> "
---

## Evitar el acoplamiento en los _steps_

Imaginemos que tenemos un _step_:

```
  Dado un usuario registrado
```

Aquí hay dos enfoques diferentes a la hora de implementarlo:

1. Interactuar con la aplicación y registrar el usuario, rellenando el formulario de registro, pinchando en el mail de verificación, etc.
  ```ruby
    step "un usuario registrado" do
      visit home_path
      fill_in "Username", with: "JohnDoe"
      fill_in "Password", with: "mypass"
      fill_in "Password confirmation", with: "mypass"
      click_button "Sign up"
    end
  ```
2. Crear el usuario en la base de datos directamente usando el modelo de la aplicación.
  ```ruby
  step "un usuario registrado" do
    User.create!(username: "JohnDoe", password: "mypass")
  end
  ```

Obviamente con el segundo enfoque vamos a ahorrar código y tiempo de ejecución en el test, pero esto tiene un problema y es que el test va a estar acoplado con el código y va a incrementar la [fragilidad](#fragilidad) del test.

La ventaja del primer enfoque es que el test va a ser 100% un test de integración y ni siquiera requiere que quien lo desarrolla conozca los detalles de la implementación de lo que significa que un usuario esté registrado, acercándose más por tanto a ser una prueba de __caja negra__.

## Solucionar regresiones

Siempre debe escribirse un test que reproduzca el bug y después debe hacerse pasar ([TDD](#tdd)). Es la única manera de asegurarse que el test cubre el problema.

Idealmente debería usarse un test unitario si es posible, normalmente no merece la pena usar un test de integración.

## Cucumber vs. Spinach

El buque insignia de los tests de integración siempre ha sido [Cucumber](https://github.com/cucumber/cucumber/). No obstante, su flexibilidad puede inducir a algunos problemas, y por tanto cualquier otra librería que sea un _port_ de Cucumber va a heredarlos:

### Los _steps_ son globales

En [Spinach](https://github.com/codegram/spinach) los steps están escritos en módulos de ruby normales y corrientes, __no son globales__ y en caso de necesitar reutilizarlos es tan fácil como usar `include`.

### Soporte para variables y tablas en los steps:
```ruby
  Dado /un descuento del (.+) en los productos del tipo (.+)%/ do |discount,type|
    [...]
  end
```

Es muy flexible, pero por motivos de legibilidad y mantenibilidad es mejor ceñirse a frases concretas y directamente no usar variables. (Spinach no soporta variables a propósito).

```
Esquema del escenario: comer
  Dado que hay <start> pepinillos
  Cuando me como <eat> pepinillos
  Entonces deberían quedar <left> pepinillos

  Ejemplos:
    | start | eat | left |
    |  12   |  5  |  7   |
    |  20   |  5  |  15  |
```

Esta especificación lo que haría sería ejecutar las diferentes permutaciones del escenario según la tabla provista en "Ejemplos".

Es fácil ver por qué alguien querría usar este estilo. Tenemos un [test de integración](#test-de-integraci%C3%B3n) y podemos reutilizarlo para probar casos extremos y cómo estos se solapan. Problema: los [tests de integración](#test-de-integraci%C3%B3n) son __lentos__. Lo ideal sería probar __un caso base__ desde un [test de integración](#test-de-integraci%C3%B3n) __sin variables__, y las diferentes permutaciones aquí representadas en la tabla de ejemplos en [tests unitarios](#test-unitario), que son mucho más rápidos.

### Conclusión

Aunque se utilice Cucumber u otra librería que tenga soporte para variables y tablas, es mejor ceñirse a _steps_ que no soporten variables. Esto obviamente queda siempre a discreción de quien desarrolle los tests y no es obligatorio, es simplemente una recomendación.

Una buena explicación de todo esto se puede ver en [esta presentación sobre Spinach](http://codegram.github.io/spinach-presentation).