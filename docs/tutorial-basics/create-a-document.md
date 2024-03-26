---
sidebar_position: 2
---

# Crear un documento

Documents are **groups of pages** connected through:

- a **sidebar**
- **previous/next navigation**
- **versioning**

## Crea tu primer documento

Crea un archivo **Markdown** en la ruta `docs/hello.md`:

```md title="docs/hello.md"
# Hola Mundo

Este es mi **Primer documento en Docusaurus**!
```

El nuevo documento estará disponible en [http://localhost:3000/docs/hello](http://localhost:3000/docs/hello).

## Configura el sidebar

:::info
Un **sidebar** o **barra lateral** es un elemento que se utiliza dentro del diseño web para ordenar o listar información importante en una columna situada a la izquierda, a la derecha o a ambos lados de la pantalla.
:::

Docusaurus crea automáticamente un sidebar a partir de la carpeta `docs`.

Agrega metadatos para personalizar la etiqueta y la posición de la barra lateral:

```md title="docs/hello.md" {1-4}
---
sidebar_label: 'Hola!'
sidebar_position: 3
---

# Hola Mundo

Este es mi **Primer documento en Docusaurus**!
```

It is also possible to create your sidebar explicitly in `sidebars.js`:

```js title="sidebars.js"
export default {
  tutorialSidebar: [
    'intro',
    // highlight-next-line
    'hello',
    {
      type: 'category',
      label: 'Tutorial',
      items: ['tutorial-basics/create-a-document'],
    },
  ],
};
```
