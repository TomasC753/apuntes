---
sidebar_position: 5
---

# Deploy del proyecto

Docusaurus es un **generador de sitios estáticos** (también llamado **[Jamstack](https://jamstack.org/)**).

Crea su sitio como simples **archivos HTML estáticos, JavaScript y CSS**.

## Construye tu sitio

Construye tu sitio **para producción** con el comando:

```bash
npm run build
```

Este comando generara los archivos estáticos en la carpeta `build`.

## Prueba el servidor de producción en local

Prueba el servidor de producción en en tu entorno local con el siguiente comando:

```bash
npm run serve
```

La carpeta `build` ahora se sirve en [http://localhost:3000/](http://localhost:3000/).

## Deploy en Github Pages
Docusaurus proporciona una manera fácil de publicar en [GitHub Pages](https://pages.github.com/), que viene gratis con cada repositorio de GitHub.

Por lo general, hay dos repositorios (al menos dos ramas) involucrados en un proceso de publicación: la **rama que contiene los archivos fuente** y la **rama que contiene el resultado de la compilación** que se entregará con GitHub Pages. En el siguiente tutorial, nos referiremos a ellos como **"fuente"** e **"implementación"**, respectivamente.

Cada repositorio de GitHub está asociado con un servicio de páginas de GitHub. Si el repositorio de implementación se llama `my-org/my-project` (donde `my-org` es el nombre de la organización o el nombre de usuario), el sitio implementado aparecerá en **"https://my-org.github.io/my-project/"**. Si el repositorio de implementación se llama `my-org/my-org.github.io` (el repositorio de páginas de GitHub de la organización), el sitio aparecerá en **"https://my-org.github.io/"**.

### Configuración
Primero, modifica tu `docusaurus.config.js` y agrega los siguientes parámetros:

| Nombre | Descripción |
| ------ | ----------- |
| `organizationName` | El usuario u organización de GitHub propietario del repositorio de implementación. |
| `projectName` | El nombre del repositorio de implementación. |
| `deploymentBranch`| El nombre de la rama de implementación. El valor predeterminado es **'gh-pages'** para repositorios de páginas de GitHub que no pertenecen a una organización. De lo contrario, debe ser explícito como campo de configuración o variable de entorno. |

Ejemplo:

```javascript title="docusaurus.config.js"
const config = {
  title: 'Apuntes',
  tagline: 'Docusaurus texts',
  favicon: 'img/favicon.ico', // Aquí va la imagen que se mostrara como "logo" de la pagina en las pestañas del navegador 

  // Establecer aquí la URL de producción de su sitio
  // La formula es 'https://<Nombre de usuario en github>.github.io'
  // highlight-next-line
  url: 'https://TomasC753.github.io',
  // Establece el nombre de ruta /<baseUrl>/ bajo el cual se sirve tu sitio
  // Para la implementación de páginas de GitHub, suele ser '/<Nombre del repositorio>'
  // highlight-next-line
  baseUrl: '/apuntes',

  // Configuración de para el deploy en GitHub pages
  // highlight-next-line
  organizationName: 'TomasC753', // Aquí va el nombre de usuario u organización de Github
  // highlight-next-line
  projectName: 'apuntes', // Aquí va el nombre del repositorio.

  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',

  /**
   * Resto del código ...
  */
}
```

### Deploy

Finalmente, para implementar el sitio en GitHub Pages, debes ejecutar el siguiente comando en **git bash**:

```bash
GIT_USER=<Nombre_de_usuario_de_github> npm deploy
```