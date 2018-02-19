# Guías de referencia de TCK

Ficheros fuente para generar un site estático con las guías de referencia de The Cocktail a partir de ficheros markdown con el framework [Hugo](https://gohugo.io/).

## ACCESO PÚBLICO

El site está acecsible en [https://guides.the-cocktail.com/](https://guides.the-cocktail.com/)

## USO

Descarga la versión de hugo para tu sistema:

[https://gohugo.io/getting-started/installing/](https://gohugo.io/getting-started/installing/)

Lanza el servidor local

```bash
hugo server -D
```

Compila el estático

```bash
hugo
```

## DESPLIEGE

Al hacer un _push_ de _master_, automáticamente el estático es generado y actualizado en un bucket de google donde apunta el host de la web.

Alternativamente hay un deploy para generar el estático y subirlo a la rama de gh-pages, pero actualmente no está en funcionando la [url de github pages](https://the-cocktail.github.io/tck-guides).

```bash
./deploy.sh
```