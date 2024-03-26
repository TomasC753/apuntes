---
sidebar_position: 3
---

# Crear un Blog Post

Un **blog​** o **bitácora​** es un sitio web que incluye, a modo de diario personal de su autor o autores, contenidos de su interés, que suelen estar actualizados con frecuencia y a menudo son comentados por los lectores.

Sirve como publicación en línea de historias con una periodicidad muy alta, que son presentadas en orden cronológico inverso, es decir, lo más reciente que se ha publicado es lo primero que aparece en la pantalla. Antes era frecuente que los blogs mostraran una lista de enlaces a otros blogs u otras páginas para ampliar información, citar fuentes o hacer notar que se continúa con un tema que empezó otro blog.​

---

Docusaurus crea una **página para cada entrada del blog**, pero también **una página de índice del blog**, un **sistema de etiquetas**, un feed **RSS**...

## Crea tu primer post

Crea un archivo en `blog/2021-02-28-greetings.md`:

```md title="blog/2021-02-28-greetings.md"
---
slug: greetings
title: Greetings!
authors:
  - name: Joel Marcey
    title: Co-creator of Docusaurus 1
    url: https://github.com/JoelMarcey
    image_url: https://github.com/JoelMarcey.png
  - name: Sébastien Lorber
    title: Docusaurus maintainer
    url: https://sebastienlorber.com
    image_url: https://github.com/slorber.png
tags: [greetings]
---

Congratulations, you have made your first post!

Feel free to play around and edit this post as much you like.
```

Una nueva publicación de blog ya está disponible en [http://localhost:3000/blog/greetings](http://localhost:3000/blog/greetings).
