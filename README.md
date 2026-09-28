# LinkBio — Kike Garcia

Página LinkBio de una sola vista para Kike Garcia, desarrollada en **HTML** con **Tailwind CSS v4**, animaciones listas para usar y SEO completo. Incluye foto de perfil con badge de verificación, sección de redes sociales con iconos SVG, tarjetas de enlaces (LinkedIn, GitHub, GH, Financial-Tools), una sección **Productos digitales** con los productos publicados en Hotmart, y un pie de página con contacto por email.

## En vivo

▶ https://kikegarciabio.netlify.app/

## Stack

| Componente | Descripción |
|------------|-------------|
| HTML | Página estática de una sola vista |
| CSS | Tailwind CSS v4 compilado vía `@tailwindcss/cli` |
| Animaciones | Plugin `tailwind-animations` (vía `@import`) |
| Iconos | Sprite SVG en `assets/sprite.svg` |
| Tipografía | Fuente Inter (`assets/inter.woff2`) |
| SEO | Meta tags, Open Graph, Twitter Cards, JSON-LD, `robots.txt`, `sitemap.xml` y `og-image` |

## Puesta en marcha

Instalá las dependencias:

```bash
npm install
```

## Compilar los estilos

El archivo `input.css` declara los `@import` y el tema (colores, fuente, breakpoints). Compilalo a `assets/output.css`:

```bash
npm run build:styles
```

> `build:styles` = `npx @tailwindcss/cli -i ./input.css -o ./assets/output.css`

### ¿Qué contiene `input.css`?

```css
@import "tailwindcss";
@import "tailwind-animations";   /* plugin de animaciones */
```

## Productos digitales

La sección «Productos digitales» (debajo de la grilla de enlaces) lista los productos publicados en Hotmart. Cada producto es una tarjeta `<a>` con imagen cuadrada, badge de formato, título, bajada, precio y garantía.

Para publicar un producto nuevo, copiá la tarjeta existente en `index.html` y actualizá:

| Dato | De dónde sale |
|------|---------------|
| `href` | Link de pago de Hotmart + parámetros de seguimiento |
| `src` y `alt` | Imagen de listado **cuadrada** guardada en `assets/` |
| Precio | Precio fijado en **USD**, nunca en ARS: el checkout convierte al tipo de cambio del día |

### Parámetros de seguimiento

El link de pago usa `sck` y `utm_source`, los parámetros oficiales de Hotmart para identificar el origen de las ventas:

- `sck` — específico de Hotmart, para **productores** que dirigen el tráfico directo a la página de pago. Se consulta en el *Dashboard Origen de Ventas* (pestaña SCK).
- `utm_source` — estándar de marketing, compatible con Google Analytics.
- `src` — es para enlaces de afiliados o páginas de ventas alternativas, **no** para este caso.

> Los parámetros **no** se propagan al checkout si el link apunta a una página de ventas de Hotmart Pages: su CTA los descarta. Por eso la tarjeta apunta directo al link de pago.

## Desplegar

Copiá el `index.html` y la carpeta `assets/` al sitio de despliegue que elijas. El CSS ya queda incrustado por el `index.html` como `assets/output.css`.

> SEO: los meta tags (Open Graph, Twitter Cards, JSON-LD) ya vienen embebidos en el `<head>` de `index.html`. Los archivos `robots.txt` y `sitemap.xml` viven en la raíz del sitio y deben desplegarse junto con el `index.html`.