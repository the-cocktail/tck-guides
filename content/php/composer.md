---
title: composer
slug: composer
weight: 30
pre: "<i class='fa fa-list-alt'></i> "
---

Composer se ha convertido en el gestor de dependencias más usado en los proyectos de PHP. A continuación una serie de normas y trucos:

* En los proyectos de The Cocktail siempre tendremos el `composer.json` y el `composer.lock` en el repositorio de código.
* NUNCA ejecutes `composer update`. Si necesitas actualizar algún paquete actualiza solo ese paquete y no todos los demás. Ejemplo, si necesitas una versión actualizada de Fos Http Cache Bundle, ejecuta `composer update friendsofsymfony/http-cache-bundle`. Caso de necesitar actualizar otros paquetes debido a la actualización de Fos, composer se encargará de ese trabajo.
* NUNCA modifiques las dependencias del `composer.json` de forma manual. Hazlo SIEMPRE vía comandos de composer. La razón es que haciéndolo así tu `composer.lock` se actualizará de forma automática, cosa que no ocurriría si lo haces solo de forma manual. Comandos:
  * `composer require [package]` traerá una nueva dependencia.
  * `composer update [package]` actualizará una de las dependencias instaladas.
  * `composer remove [package]` eliminará la dependencia.
* EVITA usar versiones `dev-master` de tus dependencias. Siempre trata de usar versiones tagueadas de las mismas.
 Si te encuentras con un proyecto que solo tiene versión `dev-master`, puedes hacerle un fork, taguearlo y usar el proyecto
 desde un repositorio de The Cocktail.
* NUNCA hagas depender tu dependencia de un commit específico de la misma, ya siempre pueden reescribir la historia.
