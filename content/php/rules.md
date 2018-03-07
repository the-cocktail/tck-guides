---
title: Rules
slug: rules
weight: 30
pre: "<i class='fa fa-list-alt'></i> "
---

## Documentación del código

Para documentar nuestro código utilizaremos phpdoc. Como norma, deberíamos documentar cada método de cada clase. Esta documentación debería consisitir en:

* Tipo de parámetros que recibe y tipo de valor que se espera.
* Opcionalmente, breve descripción de cada uno de los parámetros en el contexto de esa función.
* Opcionalmente, encima de la definición de parámetros, breve explicación de qué es lo que hace esa función.
* Opcionalmente, dentro de la función explicar por qué es necesario hacer tal o cual operación.

### Consideraciones

Debes considerar la documentación como una ayuda tanto para ti, como para tus compañeros. Cuando estés escribiendo un método, si consideras que con tu código no hace falta añadir más explicación, perfecto. Si en el proceso de pull request alguien te pregunta cosas del tipo _“Y esto, ¿por qué lo haces?”_ es posible que necesites modificar el método añadiendo esta documentación.

## Código comentado

Es bastante habitual que como desarrolladorxs hagamos cosas que luego comentemos para probar otras cosas. Esto está muy bien, pero el código comentado nunca debería subir al repositorio. Código comentado => Código a borrar.
Si la preocupación es recuperar ese código “por si acaso”, para eso tenemos nuestro control de versiones. Por tanto, NUNCA subamos código comentado al repositorio.
