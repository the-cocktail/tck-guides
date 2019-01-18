---
title: "Rspec"
slug: rspec
weight: 30
pre: "<i class='fa fa-file-text-o'></i>"
---

## 1.- Rspec

### 1.1.- Utilidades

* Bloques before: Aunque existe diferentes tipos de bloques los destacables son:
  - before(:each): se ejecuta el bloque una vez por cada uno de tus specs.
    ```ruby
      RSpec.describe User do
        before(:each) do
          @user = User.new
        end
        [...]
      end
    ```

  - before(:all): se ejecuta el bloque una única vez antes de que todos tus ejemplos corran.
    ```ruby
      RSpec.describe User do
        before(:all) do
          @user = User.new
        end
        [...]
      end
    ```

  Si no se le indica el tipo de before  por defector cogerá el de before(:each).

* Mockup: Es probable que haya que recurrir a ciertos recursos donde en nuestro entorno de pruebas no se encuentren disponibles o con la información deseada, por ejemplo, llamadas a APIs externas, servicios de Oauth, etc. Para corregir este problema, sobreescribiremos dichos recursos para que en vez de ejecutar su código nos devuelvan los valores que esperamos.
  ```ruby
    before do
      allow_any_instance_of(ApplicationController).to receive(:current_user).and_return(build(:current_user))
    end
  ```

  ```ruby
    before do
      stub_request(:any, 'www.example.com').to_return(body: 'foo', status: 200)
    end
  ```

Para esto se puede utilizar la gema [webmock](https://github.com/bblimke/webmock) o [VCR](https://github.com/vcr/vcr)

### 1.2.- Test unitario

Un test unitario comprueba una funcionalidad concreta, por ejemplo, de un método de una clase en concreto.

```ruby
RSpec.describe User, type: :model do
  let(:user) { create(:user, name: 'Jhon', last_name: 'Doe') }

  describe '#full_name' do
     it { expect(user.full_name).to eq('Jhon Doe') }
  end
end
```

### 1.3.- Test funcional

Un test funcional es algo más complejo y se ve implicada con la interacción de otras clases o modulos.

```ruby
RSpec.describe ShoppingCart, type: :model do
  let(:products) { ProductsService.run }
  let(:user) { create(:user, first_name: 'Jhon', last_name: 'Doe') }
  let(:cart) { ShoppingCart.new(user, products) }

  describe '#total_price' do
    subject { cart.total_price }

    it { is_expected.to be_a(Integer) }
  end
end
```

## 2.- Ejemplos

### 2.1.- Modelos

Una buena practica y recomendada a la hora de testear modelos sería testear relaciones, validaciones y los métodos del modelo correspondiente.

```ruby
RSpec.describe User, type: :model do

  describe 'Relationships' do
    it { is_expected.to have_one(:profile).dependent(:destroy) }
  end

  describe 'Validations' do
    it { is_expected.to validate_presence_of(:mail) }
    it { is_expected.to validate_uniqueness_of(:nif) }
  end

  describe '#unsubscribe' do
    let(:user) { User.create(name: 'user', mail: 'user@mail.com') }

    context 'when user is unsubscribed successfully' do
      it { expect(user.unsubscribe).to be_truthy }
    end
  end

end
```

### 2.2.- Controladores

```ruby
RSpec.describe UserController, type: :controller do

  describe 'POST #create' do
    subject { post :create, params: { mail: mail, password: password } }

    context 'with valid params' do
      let(:mail) { 'user@mail.com' }
      let(:password) { '12345678' }

      it { is_expected.to change(User.count).by(1) }

      it do
        subject
        expect(response).to have_http_status(200)
      end
    end

    context 'with invalid params' do
      let(:mail) { 'invalid_format' }
      let(:password) { '12345678' }

      it { is_expected.to change(User.count).by(0) }

      it do
        subject
        expect(response).to render_template(:new)
      end
    end
  end

end
```
