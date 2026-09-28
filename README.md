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

La sección «Productos digitales» (debajo de la grilla de enlaces) lista los productos publicados en Hotmart. Cada producto es una tarjeta `<a>` con imagen cuadrada, badge de formato, título, bajada, precio, garantía y llamada a la acción.

Para publicar un producto nuevo, copiá la tarjeta existente en `index.html` y actualizá:

| Dato | De dónde sale |
|------|---------------|
| `href` | **HotLink** de Hotmart (`go.hotmart.com/<CÓDIGO>`) + parámetros de seguimiento |
| `src` y `alt` | Imagen de listado **cuadrada** guardada en `assets/` |
| Precio y garantía | En **USD**, nunca en ARS: el checkout convierte al tipo de cambio del día |

### Por qué el precio y la garantía van en la tarjeta

La página de ventas de Hotmart Pages **no muestra el precio ni la garantía** (verificado: no aparecen en ningún punto del texto renderizado de la página). El precio recién se ve en el checkout, así que la tarjeta es la única fuente de esa información antes de pagar: no es decoración.

La página de ventas aporta lo que la tarjeta no puede: qué incluye la guía, los números del contenido, los resultados concretos y el posicionamiento. Cada paso del recorrido suma información nueva en vez de repetirla.

### El link es el HotLink, no la URL de la página de ventas

La tarjeta apunta al **HotLink** del producto:

```
https://go.hotmart.com/B107791130H?src=linkbio&utm_source=linkbio
```

El HotLink es el redirector de Hotmart: recibe los parámetros, **los registra en el servidor** y recién después manda al visitante a la página de ventas. Esa diferencia es determinante:

| Link | Qué pasa con el origen |
|------|------------------------|
| URL de la página de ventas + `?sck=...` | **Nada.** La página no guarda el parámetro en ninguna cookie y su CTA no lo reenvía al checkout |
| Link de pago + `?sck=...` | Funciona (es el caso que documenta Hotmart para `sck`), pero salta la página de ventas |
| **HotLink + `?src=...`** | Hotmart lo registra en la cookie `chkprm.hot` sobre `.hotmart.com`, que el checkout **sí** lee |

Verificado de punta a punta: tras el HotLink, `chkprm.hot` = `{"src":"linkbio","utm_source":"linkbio","a":"B107791130H"}`, y ese mismo valor sigue presente en la página de pago.

### Parámetros de seguimiento

- `src` — específico de Hotmart: **páginas de ventas alternativas** y enlaces de afiliación. Es el que corresponde cuando hay una página en el medio.
- `utm_source` — estándar de marketing, compatible con Google Analytics. Se registra junto con `src`.
- `sck` — específico de Hotmart, para productores que dirigen el tráfico **directo a la página de pago**. No sirve si hay una página de ventas en el medio.

> Lo que queda **sin verificar**: que el reporte *Origen de Ventas* escriba «linkbio» cuando se cierra la venta. Eso solo lo confirma una venta real. Hasta entonces, lo verificado es que el origen **llega** al checkout.

## Desplegar

Copiá el `index.html` y la carpeta `assets/` al sitio de despliegue que elijas. El CSS ya queda incrustado por el `index.html` como `assets/output.css`.

> SEO: los meta tags (Open Graph, Twitter Cards, JSON-LD) ya vienen embebidos en el `<head>` de `index.html`. Los archivos `robots.txt` y `sitemap.xml` viven en la raíz del sitio y deben desplegarse junto con el `index.html`.