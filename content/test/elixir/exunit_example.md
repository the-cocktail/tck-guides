---
title: "ExUnit test"
slug: exunit-test
weight: 30
pre: "<i class='fa fa-file-text-o'></i>"
---

## 1.- ExUnit

Es una librería de test que viene con Elixir y que nos proporciona todo lo necesario para cubrir nuestros test.

### 1.1.- Utilidades

* Describe: Es una función muy utilizada para organizar y agrupar los test por funcionalidad.
  ```
    defmodule Factory.UserTest do

      describe "user" do
        test "expected values are validated" do
          user_changeset = User.changeset(%User{}, %{name: "John", email: "john@test.com"})

          assert user_changeset.valid?
        end

        test "email is required" do
          user_changeset = User.changeset(%User{}, %{name: "John", email: nil})

          refute user_changeset.valid?
        end
      end
    end
  ```

* Setup: En algunos casos es necesario ejecutar algún tipo de código antes de lanzar nuestros test, para ello tenemos:
  - setup: es invocado antes de ejecutar a cada uno de los test.
    ```
      defmodule Factory.UserTest do
        setup do
          {:ok, name: "John"}
        end
        test "it works", %{name: name} do
          assert name == "John"
        end
      end
    ```

    - setup_all: es invocado una vez por módulo antes de ejecutar cada uno de los test.
      ```
        defmodule Factory.UserTest do
          setup_all do
            {:ok, name: "John"}
          end
          test "it works", %{name: name} do
            assert name == "John"
          end
        end
      ```

* Mock: En algunos casos queremos comprobar ciertos comportamientos de otros servicios, como por ejemplo una llamada a una API, lo cual nos permite sobreescribir este servicio con la funcionalidad esperada.

    ```
    defmodule MyTest do
      use ExUnit.Case
      import Mock

      test "get" do
        with_mock HTTPotion,
            [get: fn("http://example.com", _headers) ->
                    HTTPotion.Response.new(status_code: 200,
                        body: "hello") end] do
          # Code which calls HTTPotion.get
          # Check that the call was made as we expected
          assert called HTTPotion.get("http://example.com", :_)
        end
      end
  end
```

## 2.- Ejemplos

Ejemplos de testing de los distintos tipos de módulos en Phoenix.

### 2.1.- Schema Module
```
  defmodule Factory.Accounts.UserTest do
    use Factory.DataCase

    alias Factory.Accounts.User

    @valid_attrs %{email: "john@example.com", name: "John", bio: "my life ..."}
    @invalid_attrs %{}

    test "changeset with valid attributes" do
      changeset = User.changeset(%User{}, @valid_attrs)
      assert changeset.valid?
    end

    test "changeset with invalid attributes" do
      changeset = User.changeset(%User{}, @invalid_attrs)
      refute changeset.valid?
    end

    test "email is required" do
      changeset = User.changeset(%User{}, Map.delete(@valid_attrs, :email))
      refute changeset.valid?
    end
  end
```

### 2.2.- Controller
```
  describe "index/2" do
   setup [:create_user]
   test "index/2 responds with all Users", %{conn: conn, user: user} do

     response =
       conn
       |> get(user_path(conn, :index))
       |> json_response(200)

     expected = %{"data" => [%{"name" => user.name, "email" => user.email}]}

     assert response == expected
   end
  end
```

### 2.3.- Channel

```
  setup do
    {:ok, _, socket} =
      socket("user_id", %{some: :assign})
      |> subscribe_and_join(RoomChannel, "room:lobby")

    {:ok, socket: socket}
  end

  test "ping replies with status ok", %{socket: socket} do
    ref = push socket, "ping", %{"hello" => "there"}
    assert_reply ref, :ok, %{"hello" => "there"}
  end
```
