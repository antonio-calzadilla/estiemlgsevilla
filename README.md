# ESTIEM LG Sevilla — sitio web

Web estática (HTML + CSS + JS, sin frameworks ni backend) lista para publicarse
en **GitHub Pages**. Incluye selector de idioma (9 idiomas), galería por
álbumes, ficha de la directiva, calendario de eventos, sección de donaciones
con buzón de sugerencias, y un blog.

## 🚀 Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `estiem-lg-sevilla`).
2. Sube **todo** el contenido de esta carpeta a la raíz del repositorio
   (no lo metas dentro de otra subcarpeta).
3. En el repositorio: **Settings → Pages → Build and deployment**
   → Source: `Deploy from a branch` → Branch: `main` / carpeta `/ (root)`.
4. Espera 1–2 minutos y tu web estará en
   `https://TU-USUARIO.github.io/estiem-lg-sevilla/`.

No hace falta instalar nada ni configurar un backend: todo funciona con
ficheros estáticos.

## 🗂️ Estructura del proyecto

```
estiem-lg-sevilla/
├── index.html          ← página única (todas las secciones viven aquí)
├── css/style.css        ← todos los estilos
├── js/
│   ├── i18n.js          ← textos en los 9 idiomas
│   ├── data.js          ← contenido editable: directiva, galería, calendario, blog
│   └── main.js          ← lógica de la web (no hace falta tocarlo normalmente)
└── assets/images/       ← aquí van tus fotos reales
    ├── board/            (fotos de la directiva)
    ├── gallery/           (una carpeta por álbum/evento)
    └── blog/              (miniaturas de las entradas del blog)
```

## ✏️ Cómo editar el contenido (lo normal es tocar solo `js/data.js`)

Todo el contenido "real" —quién forma la directiva, qué álbumes hay en la
galería, qué eventos aparecen en el calendario y qué entradas tiene el
blog— vive en **`js/data.js`**, con comentarios explicando cada campo.
No hace falta tocar HTML ni CSS para actualizar contenido del día a día.

### Directiva
Edita el array `BOARD_MEMBERS`. Cada persona tiene nombre, cargo, grado,
curso, email, Instagram, LinkedIn y una ruta de imagen. Si la imagen no
existe todavía, se muestra automáticamente un círculo con las iniciales.

### Galería
Edita el array `GALLERY_ALBUMS`. Cada álbum (viaje/evento) tiene un
`slug` (identificador único en la URL, sin espacios), título, fecha,
portada y una lista de `photos`. Añade tus imágenes dentro de
`assets/images/gallery/<slug>/` y actualiza las rutas.

### Calendario
Edita el array `CALENDAR_EVENTS`. Cada evento tiene una fecha
(`YYYY-MM-DD`), un `type` (`local`, `international`, `deadline` o
`workshop` — cada uno tiene su color) y un título.

### Blog
Edita el array `BLOG_POSTS`. Cada entrada tiene `slug`, título, fecha,
autor, miniatura, un extracto corto y el contenido completo (separa
párrafos con una línea en blanco).

### Donaciones
Los métodos de pago (Bizum, transferencia, PayPal) son textos de
ejemplo. Sustitúyelos por los datos reales de la asociación editando
las claves `bizum_desc`, `bank_desc` y `paypal_desc` **dentro de
`js/i18n.js`**, en cada uno de los 9 idiomas (busca `donate:`).

### Buzón de sugerencias
El formulario no necesita servidor: al enviarse abre el cliente de
correo del usuario con un mensaje ya redactado dirigido a
`info@estiemlgsevilla.org`. Cambia esa dirección en `js/main.js`
(función `suggestionForm` → variable `mailto`) por el correo real de
la asociación. Si más adelante quieres que el formulario envíe el
correo automáticamente sin abrir el cliente de correo del usuario,
puedes sustituir esa función por un servicio como Formspree o EmailJS
(gratuitos y compatibles con GitHub Pages).

## 🌍 Idiomas

El desplegable de arriba a la derecha cambia entre Español, English,
Deutsch, Français, Português, Nederlands, Suomi, Polski e Italiano.
Todos los textos de interfaz (menús, botones, títulos de sección,
etiquetas del calendario, etc.) están traducidos en `js/i18n.js`.
El contenido dinámico (biografías de la directiva, entradas del blog,
títulos de álbumes y eventos del calendario) se guarda una sola vez en
`js/data.js` y se muestra igual en todos los idiomas — es la forma más
sencilla de mantener el sitio sin tener que traducir cada noticia. Si
en el futuro quieres traducir también ese contenido, se puede ampliar
`data.js` para admitir varios idiomas por campo.

## 🎨 Identidad visual

- **Burdeos** como color principal (identidad propia de ESTIEM LG Sevilla).
- **Verde y blanco** ("verdiblanco") reservado para la sección que habla de
  ESTIEM a nivel internacional, para diferenciarla visualmente del resto.
- Una franja de **azulejo sevillano** separa los bloques de contenido, y una
  retícula de **plano técnico** de fondo en la portada — un guiño tanto a
  Sevilla como a la ingeniería.
- Tipografías: **Fraunces** (títulos), **Work Sans** (texto) e
  **IBM Plex Mono** (fechas, etiquetas y datos), cargadas desde Google Fonts.

## 🖼️ Sobre las imágenes

El sitio funciona perfectamente sin ninguna imagen real: allá donde falte
una foto (directiva, álbumes, blog) se muestra automáticamente un
marcador de posición con el color de la identidad y, en el caso de la
directiva, las iniciales de la persona. Añade tus imágenes en
`assets/images/...` con el mismo nombre de archivo indicado en
`js/data.js` y sustituirán al marcador automáticamente.

## ✅ Compatibilidad

Sitio 100 % estático, sin dependencias de compilación (no hace falta
`npm install` ni build). Compatible con GitHub Pages, Netlify, Vercel o
cualquier hosting estático. Responsive desde móvil hasta escritorio.
