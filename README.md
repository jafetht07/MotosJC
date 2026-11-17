# MotosJC

> Catálogo estático de motocicletas en una sola página, con secciones por marca y cotización por WhatsApp.

## 🇪🇸 Español

### ¿Qué es?

MotosJC es una página única que muestra un catálogo de motocicletas de Costa Rica agrupado por marca. El visitante elige una marca en un desplegable y se muestra la sección correspondiente con las fichas de cada modelo (imagen, cilindraje, precio y año). Cada ficha tiene un botón que abre WhatsApp con un mensaje prellenado para cotizar.

Todo el contenido está escrito directamente en el HTML: no hay base de datos, backend ni llamadas de red.

### Características

- **Selección por marca**: un `<select>` con 14 marcas y la función `showModels()`, que oculta todas las secciones y muestra la que coincide con el `id` elegido.
- **95 fichas de motos** distribuidas en 14 secciones: Honda, Formula, Yamaha, Suzuki, Freedom, Katana, Serpento, Haojue, Bajaj, Benelli, Vento, TVS, Cuadraciclos y BICIMOTOS.
- **Cotización por WhatsApp**: la función `sendMessage(modelo)` abre `wa.me` con un mensaje que incluye el modelo consultado. El número de destino está definido en `indexx.html`.
- **Estilos en dos capas**: un bloque `<style>` dentro del `<head>` y una hoja de estilos externa enlazada.
- Maquetación simple con `display: none` para las secciones y fondo de imagen fija.

### Stack técnico

- HTML5 y CSS3 sin frameworks.
- JavaScript vanilla, sin dependencias ni build.
- Sin Firebase, sin `localStorage`, sin `sessionStorage`, sin `fetch` y sin JSON: los datos son HTML estático.

### Estructura del proyecto

```
MotosJC/
├── indexx.html   # Página completa: estilos en línea, 14 secciones y las 95 fichas
├── styles.css    # En realidad es un documento HTML completo ("Mundo Motor"), no una hoja CSS
├── script.js     # Variante de sendMessage() que no está enlazada desde el HTML
└── README.md     # 9 bytes
```

Las imágenes se referencian por nombre de archivo relativo (por ejemplo `Honda XR190L.jpeg`) y están incluidas en el repositorio: son cerca de 95 archivos `.jpeg` en la raíz. Deben permanecer en la misma carpeta que el HTML.

### Cómo ejecutarlo

No requiere instalación ni servidor: abre `indexx.html` en el navegador. Para publicarlo en GitHub Pages hay que renombrarlo a `index.html`, porque ese es el nombre que Pages busca como portada; con `indexx.html` la URL raíz no lo mostrará.

### Datos y configuración

- Los datos de las motos están escritos a mano en `indexx.html`; para actualizar precios o modelos hay que editar el HTML.
- El número de WhatsApp usado en las cotizaciones está en la función `sendMessage` de `indexx.html`.
- No hay credenciales, panel de administración ni almacenamiento de datos.

### Relación con los otros repositorios

Los tres repositorios (`MOTOMANIA-JC`, `MotosJC` y `JCMOTOS`) son variantes del mismo catálogo de motos, no proyectos independientes.

- **`MOTOMANIA-JC` es la versión más completa y la evolución de este código.** Mueve el catálogo a Firebase (Firestore y Storage) y añade panel de administración con CRUD de motos y marcas, generador de volantes PDF, estadísticas, login y un catálogo público renderizado en JavaScript con 109 motos de 15 marcas. En lugar de secciones fijas en el HTML, la página se construye a partir de los datos.
- **`MotosJC` y `JCMOTOS` comparten exactamente el mismo `indexx.html` y el mismo `script.js`** (idénticos byte a byte). La única diferencia está en `styles.css`.
- **`MotosJC` parece ser la revisión posterior de `JCMOTOS`**: su `styles.css` añade una `meta description`, un ajuste para móviles que desactiva la imagen de fondo por debajo de 768 px y ajustes de tamaño para `h1` y botones. Nada de eso existe en `JCMOTOS`.
- Este repositorio **no** reproduce las funciones del panel de administración ni del PDF; es la etapa estática previa, con los datos escritos en el HTML.

### Notas y limitaciones

- **`styles.css` no es CSS**: ambos archivos contienen un documento HTML completo de una plantilla llamada "Mundo Motor", con `<!DOCTYPE html>`, `<head>` y su propio `<style>`. El navegador no puede aplicarlo como hoja de estilos, de modo que la apariencia real proviene del `<style>` interno de `indexx.html`.
- **`script.js` no se usa**: `indexx.html` no lo enlaza y define su propia versión de `sendMessage`. El archivo contiene una variante que pregunta por financiamiento o contado y, en el caso de financiamiento, solicita la cédula por `prompt`; esa lógica no está activa.
- **ID duplicado**: al final del documento hay una segunda `<section id="Benelli">` con texto de relleno. Como los `id` deben ser únicos, la sección real de Benelli es la primera y la segunda queda inalcanzable.
- **Ficha duplicada**: la BICIMOTO KATANA MINI aparece dos veces con los mismos datos.
- **Sin validación ni mantenimiento**: los precios y cilindrajes son texto escrito a mano; un cambio de precio exige editar el HTML.
- **Rutas de imagen relativas**: si las fotos no están junto al HTML, las fichas quedan sin imagen y sin mensaje de error.
- **El nombre `indexx.html` impide usarlo como portada** en GitHub Pages u otro hosting que espere `index.html`.

---

## 🇬🇧 English

### What is it?

MotosJC is a single-page motorcycle catalog for Costa Rica, grouped by brand. The visitor picks a brand from a dropdown and the matching section appears with one card per model (photo, displacement, price and year). Each card has a button that opens WhatsApp with a prefilled quote request.

All content is written directly in the HTML: there is no database, backend or network call.

### Features

- **Brand selection**: a `<select>` with 14 brands and the `showModels()` function, which hides every section and shows the one matching the selected `id`.
- **95 motorcycle cards** across 14 sections: Honda, Formula, Yamaha, Suzuki, Freedom, Katana, Serpento, Haojue, Bajaj, Benelli, Vento, TVS, Cuadraciclos and BICIMOTOS.
- **WhatsApp quotes**: `sendMessage(model)` opens `wa.me` with a message that includes the selected model. The destination number is defined in `indexx.html`.
- **Two styling layers**: a `<style>` block inside `<head>` plus a linked external stylesheet.
- Simple layout using `display: none` for sections and a fixed background image.

### Tech stack

- HTML5 and CSS3, no frameworks.
- Vanilla JavaScript, no dependencies and no build step.
- No Firebase, no `localStorage`, no `sessionStorage`, no `fetch` and no JSON: the data is static HTML.

### Project structure

```
MotosJC/
├── indexx.html   # Full page: inline styles, 14 sections and all 95 cards
├── styles.css    # Actually a complete HTML document ("Mundo Motor"), not a CSS file
├── script.js     # A sendMessage() variant that is never linked from the HTML
└── README.md     # 9 bytes
```

Images are referenced by relative filename (for example `Honda XR190L.jpeg`) and are included in the repository: roughly 95 `.jpeg` files at the root. They must stay next to the HTML.

### How to run it

Nothing to install and no server needed: open `indexx.html` in a browser. To publish it on GitHub Pages, rename it to `index.html`, since that is the entry point Pages looks for; with `indexx.html` the root URL will not serve it.

### Data and configuration

- Motorcycle data is hand-written in `indexx.html`; updating prices or models means editing the HTML.
- The WhatsApp number used for quotes lives in the `sendMessage` function in `indexx.html`.
- There are no credentials, no admin panel and no data storage.

### Relationship to the other repositories

The three repositories (`MOTOMANIA-JC`, `MotosJC` and `JCMOTOS`) are variants of the same motorcycle catalog, not independent projects.

- **`MOTOMANIA-JC` is the most complete version and the evolution of this code.** It moves the catalog to Firebase (Firestore and Storage) and adds an admin panel with motorcycle and brand CRUD, a PDF flyer generator, statistics, login, and a JavaScript-rendered public catalog with 109 motorcycles across 15 brands. Instead of fixed HTML sections, the page is built from data.
- **`MotosJC` and `JCMOTOS` share exactly the same `indexx.html` and `script.js`** (byte-for-byte identical). The only difference is `styles.css`.
- **`MotosJC` appears to be the later revision of `JCMOTOS`**: its `styles.css` adds a `meta description`, a mobile rule that disables the background image below 768 px, and size adjustments for `h1` and buttons. None of that exists in `JCMOTOS`.
- This repository does **not** reproduce the admin panel or PDF features; it is the earlier static stage, with data written into the HTML.

### Notes and limitations

- **`styles.css` is not CSS**: both files contain a full HTML document for a template called "Mundo Motor", with `<!DOCTYPE html>`, `<head>` and its own `<style>`. The browser cannot apply it as a stylesheet, so the real look comes from the inline `<style>` in `indexx.html`.
- **`script.js` is unused**: `indexx.html` never links it and defines its own `sendMessage`. The file contains a variant that asks about financing versus cash and, for financing, requests the national ID through `prompt`; that logic is not active.
- **Duplicate ID**: a second `<section id="Benelli">` with placeholder text sits at the end of the document. Since IDs must be unique, the real Benelli section is the first one and the second is unreachable.
- **Duplicate card**: the BICIMOTO KATANA MINI appears twice with identical data.
- **No validation or maintainability**: prices and displacements are hand-written text; changing a price means editing the HTML.
- **Relative image paths**: if the photos are not next to the HTML, cards render without an image and without any error message.
- **The `indexx.html` name prevents using it as a landing page** on GitHub Pages or any host that expects `index.html`.

---

Autor: Jafeth (GitHub: [@jafetht07](https://github.com/jafetht07))
