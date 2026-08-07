# LinkBio — Kike Garcia

Página LinkBio de una sola vista para Kike Garcia, desarrollada en **HTML** con **Tailwind CSS v4**, animaciones listas para usar y SEO completo. Incluye foto de perfil con badge de verificación, sección de redes sociales con iconos SVG, tarjetas de enlaces (LinkedIn, GitHub, GH, Financial-Tools), y un pie de página con contacto por email.

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

## Desplegar

Copiá el `index.html` y la carpeta `assets/` al sitio de despliegue que elijas. El CSS ya queda incrustado por el `index.html` como `assets/output.css`.

> SEO: los meta tags (Open Graph, Twitter Cards, JSON-LD) ya vienen embebidos en el `<head>` de `index.html`. Los archivos `robots.txt` y `sitemap.xml` viven en la raíz del sitio y deben desplegarse junto con el `index.html`.