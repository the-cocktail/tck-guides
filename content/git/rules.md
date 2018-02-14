---
title: Reglas generales
slug: reglas
weight: 20
---


* Escribe los nombre en inglés y sólo con letras y números, nada de acentos, ñ's, # o caracteres que puedan dar problemas.

* Usa **guiones** para separar palabras.

* Usa nombres **cortos** y **descriptivos**:

  ```bash
  # bien
  $ git checkout -b oauth-migration

  # poco preciso
  $ git checkout -b login_fix
  ```

* Siempre que sea posible, añade el número de ticket:

  ```bash
  # Ticket #36500
  $ git checkout -b feature/oauth-migration-36500
  ```

* Agrupa las ramas en función del tipo de trabajo, para eso, nombra la rama empezando con el tipo y /, por ejemplo **feature/** para nuevas funcionalidades y **fix/** para correcciones:

  ```bash
  $ git checkout -b feature/oauth-migration
  $ git checkout -b fix/text-error
  ```

* Para grandes funcionalidades en las que van a trabajar varias personas, crear una rama específica y crear subcarpetas para las distintas tareas:

  ```bash
  # Rama común
  $ git checkout -b feature-redesign/master
  # Trabajo de back
  $ git checkout -b feature-redesign/back
  # Trabajo de front
  $ git checkout -b feature-redesign/front
  ```

* Cuidado con crear múltiples anidaciones ya que puede bloquear ramas. Si existe la rama **feature/oauth-migration** y se crea la rama **feature/oauth-migration/front**, la primera será un directorio para Git y no se podrá hacer checkout a ella.

* Borra tus ramas personales en local y del repositorio remoto cuando acabes de trabajar en una tarea y ya esté mergeada a master, a no ser que exista alguna razón para mantenerla. Mantengamos los repositorios limpios, ¿acaso no borras tus ramas en casa?

  Consejo: Borra siempre las ramas locales desde master con -d, en el caso de no estar mergeadas no te dejará.

  ```bash
  # Borrar la rama local
  $ git branch -d feature/oauth-migration
  # Borrar la rama remota
  $ git push origin :feature/oauth-migration
  ```

  Puedes listar las ramas mergeadas en master con:

  ```bash
  $ git branch --merged master | grep -v "\* master"`
  ```

  Puedes limpiar las ramas remotas que han sido borradas en el repositiorio con:

  ```bash
  $ git remote prune origin
  ```

## Commits

* Cada commit debe englobar el menor cambio "lógico" posible en vez de juntar múltiples cambios en un solo commit grande.

* Haz commits con lógica cada poco tiempo. Con commits pequeños y atómicos será más fácil entender la historia y revertir cambios si se producen problemas.

* Si has acumulado varios commits, al hacerlo procura mantener el orden lógico, es decir si un cambio en un commit depende de otro, el dependiente deberá de hacerse después. Y describe la dependencia en los comentarios.

### Mensajes

* Escribir mensajes descriptivos y consistentes:
  * Una primera línea con una descripción concisa de menos de 50 caracteres, para una correcta visualización tanto en clientes como en la consola. Primera palabra en mayúsculas, no acabar en punto la frase (es el asunto del commit) y usar el imperativo de la segunda persona del singular. Por ejemplo, en vez de escribir "He añadido comprobaciones para" o "Añadiendo comprobaciones para", utilizar la frase "Añade comprobaciones para"
  * Dejar una línea en blanco y escribir una descripción más detallada (por qué, cómo, número de ticket, enlaces...), máximo 72 caracteres por línea. Dependiendo del cliente lo detectará y lo mostrara como información colapsada junto a la descripción general.

  ```bash
  Asunto de menos de 50 carcteres

  Explicación detallada de lo acontecido en el ticket
  sin pasar de los 72 caracteres. La línea de separación
  hará que algunos clientes traten la primera línea como
  el asunto y esto como el cuerpo.

  Separar más párrafos con saltos de línea.

    - También está bien usar bullets.

  Información sacada de http://git-scm.com/book/es/v1/Git-en-entornos-distribuidos-Contribuyendo-a-un-proyecto
  ```
* Por esto, es más recomendable usar un editor para escribir los commits que los commits en línea (-m)
