---
title: "Mini test"
slug: mini-test
weight: 30
pre: "<i class='fa fa-file-text-o'></i>"
---

## 1.- Minitest

### 1.1.- Utilidades

* Bloques: Permiten ejecutar un bloque antes o despues de correr los test:
  - setup: se ejecuta el bloque antes de tus specs.
    ```ruby
      class UserTest < ActiveSupport::TestCase
        def setup
          @user = User.new
        end
        [...]
      end
    ```

  - teardown: se ejecuta el bloque después de tus specs.
    ```ruby
      class UserTest < ActiveSupport::TestCase
        def teardown
          @user.points = @user.points + 10
          @user.save
        end
        [...]
      end
    ```

* Mockup: Es probable que haya que recurrir a ciertos recursos donde en nuestro entorno de pruebas no se encuentren disponibles o con la información deseada, por ejemplo, llamadas a APIs externas, servicios de Oauth, etc. Para corregir este problema, sobreescribiremos dichos recursos para que en vez de ejecutar su código nos devuelvan los valores que esperamos.
  ```ruby
    def setup
      ApplicationController.stubs(:current_user).returns(build(:current_user))
    end
  ```
  ```ruby
    def setup
      stub_request(:any, "www.example.com").to_return(body: "foo", status: 200)
    end
  ```

Para esto se puede utilizar la gema [webmock](https://github.com/bblimke/webmock) o [VCR](https://github.com/vcr/vcr)

### 1.2.- Test unitario

Un test unitario comprueba una funcionalidad concreta, por ejemplo, de un metodo de una clase en concreto.
```ruby
class UserTest < ActiveSupport::TestCase
  def setup
    @user = User.new(name: 'user', email: 'user@mail.com')
  end
  test 'valid user' do
    assert @user.valid?
  end
end
```

### 1.3.- Test funcional

Un test funcional es algo más complejo y se ve implicada con la interacción de otras clases o modulos.
```ruby
class UserTest < ActiveSupport::TestCase
  test "#total_price" do
    products = ProductsService.run
    shopping_cart = ShoppingCart.new(products)
    assert_equal 50, shopping_cart.total_price
  end
end
```

## 2.- Ejemplos

### 2.1.- Modelos

Una buena practica y recomendada a la hora de testear modelos sería testear relaciones, validaciones y los metodos del modelo correspondiente.
```ruby
class UserTest < ActiveSupport::TestCase
  test 'valid user' do
    user = User.new(name: 'user', email: 'user@example.com')
    assert user.valid?
  end

  test 'invalid without name' do
    user = User.new(email: 'user@example.com')
    refute user.valid?
    assert_not_nil user.errors[:name]
  end

  test 'invalid without email' do
    user = User.new(name: 'user')
    refute user.valid?
    assert_not_nil user.errors[:email]
  end
end
```

### 2.2.- Controladores
```ruby
class ReporterControllerTest < ActionController::TestCase
  def test_show
    get :show
    assert_response 200
  end
end
```