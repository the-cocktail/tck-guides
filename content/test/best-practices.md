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