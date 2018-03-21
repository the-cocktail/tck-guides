---
title: "Tests de integración"
slug: test-integracion
weight: 30
pre: "<i class='fa fa-file-text-o'></i>"
---

## 1.- Herramientas

Con estas herramientas nos centraremos en testear y analizar las funcionalidades críticas que una aplicación pueda tener.

### 1.1.- Cucumber

Cucumber es un framework test de alto nivel, el cual esta diseñado para poder realizar BDD (Behaviour Driven Development) y poder definir el comportamiento de una aplicación.

Cucumber permite testear la aplicación desde la perspectiva del usuario y en algunos casos eso significa tener que lidiar con elementos de la interfaz de usuario impulsados por JavaScript. Cucumber hace esto iniciando un navegador en segundo plano y lleva a cabo las interacciones que realizaria el usuario: hacer clic en links o botones, rellenar formularios, etc. Tienes que saber que Cucumber no se usa para hacer test unitarios, pero es perfecto para testear las interacciones que un usuario realiza.

[Documentación](https://github.com/cucumber/cucumber-rails)
[Wiki](https://github.com/cucumber/cucumber/wiki)

## 2.- Descripción

En los siguientes apartados se obtendrá la información necesaria para poder instalar y configurar Cucumber junto con Poltergeist en una aplicación para Ruby on Rails.

### 2.1.- Estructura

Añade la gema dentro del gemfile:
```ruby
 group :test do
  gem 'cucumber-rails', :require => false
  # database_cleaner is not required, but highly recommended
  gem 'database_cleaner'
end
```

Instala la gema:
```ruby
bundle install
```

Genera la estructura principal con el siguiente comando:
```ruby
rails generate cucumber:install
```

De esta forma te genera una estructura en la aplicación como en la siguiente:
```
$ app
.
└── features
    ├── step_definitions
    │   ├── example_steps.rb
    │   ├── example_steps.rb
    │   └── example_steps.rb
    ├── support
    │   └── env.rb
    ├── example_description.feature
    ├── example_description.feature
    └── example_description.feature
```

Los ficheros .feature es donde se definen las funcionalidades de uso. Dentro de la carpeta step_definitions se encuentran la implementación de los tests. Y en env.rb dentro de la carpeta support está la configuración de Cucumber.

### 2.2.- Implementación

La estructura de un feature debe de ser como la siguiente:
```ruby
Feature: Signin Description

User can be logged if has been sign up previously and input a mail and password valid.
User should not be logged until the user has not been sign up previously.
User should not be logged until the user input a mail or password not valid.

@signin
Scenario Outline: User sign in through mail and password.
  Given user account previously sign up with mail and password
    And sign in web page rendered
  When user fill sign in form successfully with mail and password
  Then user is rendered to home page
```

  - `Feature`: es la descripción de la funcionalidad el cual contiene un titulo descriptivo.
  - `Scenario`: es el bloque que contiene los pasos a seguir para realizar una funcionalidad concreta.


Una vez tengas las features y los scenarios definidos hay que ejecutar el comando **rake cucumber** (con Rake) o **[bundle exec] cucumber** (sin Rake) para que te genere la estructura básica que cada uno de los steps que has definido en tus .feature
anteriormente.

La estructura de un step debe de ser como la siguiente:
```ruby
Given("user account previously sign up with mail and password") do
  @user = create(:user, mail: 'user@mail.com', password: '12345678')
end

Given("sign in web page rendered") do
  visit new_user_session_path
end

When("user fill sign in form successfully with mail and password") do
  fill_in "user[mail]", with: @user.mail
  fill_in "user[password]", with: @user.password
  find_button("Entrar").trigger('click')
end

Then("user is rendered to home page") do
  expect(page).to have_current_path(root_path)
end
```

  - `Given`: indica de donde parte el test, con los prerequisitos definidos.
  - `When`: indica la acción que se realiza.
  - `Then`: es el resultado que debe de esperar al finalizar el test.

### 2.3.- Configuración

Para poder utilizar la funcionalidad de otras gemas se necesitan agregar los métodos al entorno de Cucumber. Este es un ejemplo para poder usar FactoryGirl/FactoryBot añadir:
```ruby
World(FactoryBot::Syntax::Methods)
```

### 2.4.- Etiquetas

Las etiquetas [tags](https://github.com/cucumber/cucumber/wiki/Tags) es la mejor forma de organizar tus escenarios. Los tags te permiten ejecutar unicmanete los test que deseas.

Puedes usar la opción --tags para indicarle a Cucumber que solamente quieres correr ciertos features o scenarios que contengan ciertos tags. Por ejemplo:
```ruby
cucumber --tags @user,@signin # Runs both scenarios (Scenarios with @user OR @signin)
```

### 2.6.- Hooks

Cucumber permite mediante [hooks](https://github.com/cucumber/cucumber/wiki/Hooks) correr un conjunto de tareas en cada ciclo de un test. Estos hooks se definen en features/support/env.rb.

Puede ser muy útil en el caso de que en tu aplicación contenga un cms y necesite cargar previamente ese cms a través de seeds.
```ruby
  Before('@no-txn,@selenium,@culerity,@celerity,@javascript') do
    system("RAILS_ENV=test rake db:seed")
  end
```

## 3.- Herramientas adicionales

### 3.1.- Poltergeist

El driver por defecto que usa Cucumber a través de Capybara se llama :rake_test. Este tiene algunas limitaciones, principalmente es el hecho de que este no soporta Javascript, por lo que necesitamos otros driver que soporte Javascript. Por lo general para los test que no requieran de Javascript podemos usar :rack_test pero en caso contrario usaremos Poltergeist driver.

Poltergeist es un driver de PhantomJS para Capybara.

[Documentación](https://github.com/teampoltergeist/poltergeist)

Para configurar Poltergeist añadir en features/support/env.rb:
```ruby
require 'capybara/poltergeist'

Capybara.app_host = "http://localhost:3000"
Capybara.server_host = "localhost"
Capybara.server_port = "3000"

Capybara.javascript_driver = :poltergeist
```

Para poder realizar los test levantando un navegador hay que añadir la etiqueta @javascript en la definición de los escenarios. Al correr cada uno de los test que contenga esta etiqueta se simulará la funcionalidad con su código Javascript necesario.

Aunque en esta guía se recomiendo el uso de Poltergeist, existen otros drivers como Selenium que permite levantar un navegador real y puede ser bastante útil en el caso de que se desee realizar pruebas en un navegador en concreto.

### 3.2.- DatabaseCleaner

DatabaseCleaner permite configurar una serie de estrategias para limpiar la base de datos en Ruby, el cuál garantiza un estado de limpieza durante las pruebas.

[Documentación](https://github.com/DatabaseCleaner/database_cleaner)