---
title: code standard
slug: code-standard
weight: 30
pre: "<i class='fa fa-retweet'></i> "
---

## Proyectos que no usen Drupal

Todos los proyectos que no hagan uso de drupal DEBEN seguir el estándar psr2. https://www.php-fig.org/psr/psr-2/

Sus normas, también descritas en el enlace anterior, son las siguientes:

* El código DEBE cumplir una guía de estilo
* El código DEBE usar 4 espacios para indentar. NUNCA se debe usar tabs
* NO DEBE de existir un límite de caracteres por línea de código. Sin embargo, no deberíamos escribir nunca líneas de más de 120 caracteres. En todo caso, la recomendación es que las líneas de código no superen los 80 caracteres. 
* DEBE de haber una línea en blanco después de la declaración de namespace. También DEBE existir una línea en blanco después de cada bloque de sentencias use. 
* Las llaves de apertura de una clase DEBEN ir en la línea siguiente a la declaración de la clase. Las llaves de cierre de una clase DEBEN ir en la línea posterior al cierre del body de la misma. 
* Las llaves de apertura de un método DEBEN ir en la línea siguiente a la declaración de un método. Las llaves de cierre de una clase DEBEN ir en la línea posterior al cierre del body del mismo. 
* Todas las propiedades y métodos de una clase DEBEN declarar su visibilidad (public, protected, private). Cuando se usen abstract o final se declararán antes de la visibilidad. Si se usa static se añadirá después de la visibilidad. 
* Las keywords para control de estructura (if, for, foreach, switch…) DEBEN tener un espacio detrás de ellas. Las definiciones de métodos y llamadas a funciones NO DEBEN tener ningún espacio tras ellas. 
* Las llaves de apertura para estructuras de control DEBEN ir en la misma línea. Las llaves de cierre de una estructura de control deben ir en la línea siguiente al cierre del body de la misma. 
* Los paréntesis de apertura en un control de estructura no debe llevar ningún espacio tras ellos. Los paréntesis de cierre en un control de estructura no deben llevar ningún espacio antes de ellos. 

Tienes ejemplos de uso de todas estas reglas en la url https://www.php-fig.org/psr/psr-2/.

## Proyectos basados en Drupal

Drupal define su propio estándar de código. Puedes consultarlo en https://www.drupal.org/docs/develop/standards/coding-standards.

## Validación de estándar de código

Cada pull request hecha en nuestros proyectos PHP debería pasar una serie de validaciones entre ellas la de que cumpla el estándar de código.
Para ello utilizaremos esta librería: https://github.com/squizlabs/PHP_CodeSniffer.
Nuestros proyectos deberían tener esta dependencia en la zona `require-dev` del composer.json y el comando de validación de código debería ser ejecutado desde el “build” que se esté usando para validar las pull requests.

Ejemplo, en Casa Palacio añadimos le decimos a Circle CI que ejecute la validación de estándar de código con este comando.
https://github.com/the-cocktail/casapalacio/blob/master/circle.yml#L25
