# ANX Creative Studio — Landing Page

Sitio estático. Sin build, sin npm, sin dependencias que instalar.

## Estructura

```
anx-creative-studio/
├── index.html            ← todo el sitio (markup + estilos + lógica)
├── videofuncional.mp4    ← video de la tarjeta Taller
├── support.js            ← runtime (no editar)
└── image-slot.js         ← componente de placeholders de imagen
```

## Editar en Visual Studio Code

1. Abre la carpeta `anx-creative-studio` en VS Code.
2. Instala la extensión **Live Server** (Ritwick Dey).
3. Click derecho en `index.html` → **Open with Live Server**.

> Ábrelo con Live Server, no con doble click. Cargarlo como `file://`
> bloquea el video del hero por CORS.

## Dónde está cada cosa en index.html

| Qué                          | Buscar en el archivo                    |
| ---------------------------- | --------------------------------------- |
| Fuentes / keyframes / resets | `<helmet>` (arriba)                     |
| Navbar                       | `<!-- A) NAVBAR`                        |
| Hero + video de fondo        | `<!-- B) HERO`                          |
| Manifesto                    | `<!-- C) MANIFESTO`                     |
| Servicios                    | `id="services"`                         |
| Proyecto destacado (Taller)  | `<!-- Featured Project — TALLER`        |
| Formulario de cotización     | `<!-- E) CONVERSION HUB`                |
| Footer                       | `<footer`                               |
| Botón flotante WhatsApp      | `<!-- F) FLOATING WHATSAPP`             |
| Lógica (JS)                  | `class Component extends DCLogic`       |

## Cambios rápidos

**WhatsApp** — busca `whatsappNumber` en el bloque `data-props` al final:

```
"whatsappNumber": { ..., "default": "+52 33 1159 9014", ... }
```

El link `wa.me` se arma solo (limpia espacios y símbolos). El texto visible
del botón está en la sección `F) FLOATING WHATSAPP`.

**Video del hero** — busca `DEFAULT_VIDEO` (inicio del `<script>`).

**Color de acento** — busca `"accent"` en `data-props`. Se propaga a todo el
sitio vía la variable CSS `--accent`.

**Timing del typewriter del hero** — método `heroReveal()`:
`1000` = pausa inicial en ms (video limpio) · `50 + Math.random() * 30` = ms por
carácter · `240` = pausa entre líneas.

**Colores del hero** — en el `<h1>`, cada `data-hero-type` lleva su propio color:
apoyo en `rgba(255,255,255,0.65)`, "Experiences" en `0.85`, "Real." en `#ffffff`
con `font-weight:900` y glow vía `text-shadow`.

**Imagen del proyecto** — el `<image-slot id="anx-work-taller">`. Para usar una
imagen real, reemplaza el tag por `<img src="./img/taller.jpg" style="width:100%;
height:100%; object-fit:cover" alt="Taller" />`.

## Estilos

Todo es CSS inline en los atributos `style`. Es intencional: pinta de inmediato
y no hay hoja de estilos que sincronizar. Los estados hover/focus usan
`style-hover` / `style-focus` / `style-active`.

Lo único que vive en `<helmet><style>` es lo que no puede ser inline:
`@font-face`, `@keyframes` y resets de `body`.

## Publicar

Sube las 3 carpetas/archivos tal cual a cualquier hosting estático:

- **Netlify / Vercel** — arrastra la carpeta. Sin comandos de build.
- **cPanel / Hostinger** — sube todo a `public_html`.
- **GitHub Pages** — push a la rama, activa Pages en Settings.

Existe también un `index.html` de un solo archivo (todo incrustado) en la raíz
del proyecto original, si prefieres publicar un único archivo sin carpeta.

## Contacto del estudio

Guadalajara, MX — Worldwide · WhatsApp +52 33 1159 9014 · hola@anx.studio
