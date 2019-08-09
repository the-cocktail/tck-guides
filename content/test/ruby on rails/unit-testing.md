---
title: "Tests unitarios"
slug: test-unitarios
weight: 30
pre: "<i class='fa fa-file-text-o'></i>"
---

Aquí vamos a especificar algunas de las herramientas para poder hacer testing unitario de nuestras aplicaciones Ruby&Rails y los primeros pasos para configurarlo y hacer  los primeros tests en nuestras aplicaciones, así como algunas herramientas adionales que son útiles.

## 1.- Herramientas

Con estas herramientas nos centraremos en testear la parte unitaria de la aplicación. En ellos analizaremos todos los posibles casos extremos que nuestra lógica de negocio pueda tener.

### 1.1.- Minitest

[Documentación](https://github.com/seattlerb/minitest)

Para la parte Rails, es necesaria incluir la gema [`minitest-rails`](https://github.com/blowmage/minitest-rails)

### 1.2.- Rspec

[Documentación](https://github.com/rspec/rspec-rails)

## 2.- Descripción

### 2.1.- Estructura

Dependiendo de la herramienta utilizada, tendr
A la hora de implementar los tests, estos se organizan mediante una serie de convenciones para ayudar a la definición y a la estructura de los mismos. Siguen el orden `describe`,`context` e `it`:

```ruby
describe '#destroy' do

  it 'responds with 200'
  it 'shows the resource'

  context 'when resource is not found' do
    it 'responds with 404'
  end

  context 'when resource is not owned' do
    it 'responds with 404'
  end
end
```

  - `describe`: Se utiliza para describir el método o función que se va a testear.
  - `context`: Especifican el contexto en el que se integra la prueba a realizar para que sea fácil de entender. Se recomienda que comiencen con `when` o `with`. En el caso de MiniTest, para añadirlo se utiliza la gema [minitest-spec-context](https://github.com/ywen/minitest-spec-context)
  - `it`: Describe el comportamiento del test. Debe ser una descripción corta y concisa.

Se puede consultar algunas de las buenas prácticas en este [enlace](http://www.betterspecs.org/)

### 2.2.- Implementación

Dentro de cada `it` definiremos nuestro test. Configuraremos el código y siempre esperaremos una verificación de un comportamiento o salida esperada, ya sea un response, una comparación de un objeto o un bool de confirmación del proceso.

Existen conceptos muy útiles, como el `before` o los mocks, que nos ayudarán a que nuestros tests sean menos traumáticos.

## 3.- Herramientas adicionales

A la hora de testear en R&R existen muchas gemas que pueden facilitarnos la vida a la hora de escribir nuestros tests. Aquí vamos a definir algunas de las más interesantes

### 3.1.- Simplecov

[Documentación](https://github.com/colszowka/simplecov): Analiza el porcentaje de nuestro código que está cubierto por tests.

### 3.2.- FactoryBot

[Documentación](https://github.com/thoughtbot/factory_bot): Anteriormente conocida como FactoryGirl. Nos permite definir factorias genéricas para la utilización de objetos en nuestros test.

### 3.3.- Faker

[Documentación](https://github.com/stympy/faker): Nos permite generar datos aleatorios de un determinado tipo para utilizar en nuestras pruebas: emails, contraseñas, citas, nombres, etc.

### 3.4.- Shoulda Matchers

[Documentación](https://github.com/thoughtbot/shoulda-matchers): Extiende las opciones para realizar comprobaciones de una forma sencilla e intuitiva.

### 3.5.- DatabaseCleaner

[Documentación](https://github.com/DatabaseCleaner/database_cleaner): DatabaseCleaner permite configurar una serie de estrategias para limpiar la base de datos en Ruby, el cuál garantiza un estado de limpieza durante las pruebas.

## 4. Casos practicos de Test

### Test unitario
Los test unitarios deben ser lo mas sencillo posible y solo se debe comprobar la llamada de un método.
```ruby
require 'rails_helper'

RSpec.describe User, type: :model do
  let(:user) { create(:user, first_name: 'Jhon', last_name: 'Doe') }

  describe '#full_name' do
    subject { user.full_name }

    it { is_expected.to be_a(String) }
    it { is_expected.to eq('Jhon Doe') }
  end
end
```

### Test funcional
Los test funcionales implican interacción con otras clases o modulos.
```ruby
require 'rails_helper'

RSpec.describe ShoppingCart, type: :model do
  let(:products) { ProductsService.run }
  let(:user) { create(:user, first_name: 'Jhon', last_name: 'Doe') }
  let(:cart) { ShoppingCart.new(user, products) }

  describe '#total_price' do
    subject { cart.total_price }

    it { is_expected.to be_a(Integer) }
  end

  describe '#full_name' do
    subject { cart.full_name }

    it { is_expected.to eq('Jhon Doe') }
  end
end
```
Al estar invocando el método de otra clase estariamos probando el funcionamiento de ProductsService y ShoppingCart.

### Method Stubs
Para que nuestros test sean mas sencillos y rápidos al ejecutarlos en muchos casos es mejor utilizar Stubs.
```ruby
describe '#publish' do
  before { allow(user).to receive(:role) { role } }

  subject { user.publish(post) }

  context 'when the user is publisher' do
    let(:role) { 'publisher' }

    it { is_expected.to be true }
  end

  context 'when the user is not publisher' do
    let(:role) { nil }

    it { is_expected.to be false }
  end
end
```
Si no utilizamos un Stub debemos conocer la lógica de como un usuario obtiene el rol publisher y esto haria nuestro test mas dificil de leer y mas lento al ejecutarse.

### Mock Http request
En nuestros test no deberiamos hacer llamadas http a servicios externos, lo que queremos probar es que nuestra lógica de negocio funciona correctamente no el servicio externo.
Para esto se puede utilizar la gema [webmock](https://github.com/bblimke/webmock) o [VCR](https://github.com/vcr/vcr).
```ruby
subject(:response) { Net::HTTP.get('www.example.com', '/') }

context 'with unauthorized access' do
  before {
    stub_request(:any, 'www.example.com')
      .to_return(body: 'foo', status: 200)
  }

  it 'returns foo' do
    expect(response.body).to eq('foo')
  end
end
```
Para saber mas http://www.betterspecs.org/
