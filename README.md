## Proyecto LinkBio con HTML:
Este es un proyecto de una página LinkBio para Kike Garcia desarrollado en HTML utilizando Tailwind CSS. La página tiene una foto de perfil, nombre con icono de verificación, una sección con Redes Sociales con los iconos a cada red social, una sección con grids a LinkedIn, Github, GH, Financial-Tools y un pié de página con link a un email.
Utiliza el archivo /assets/sprite.svg para mostrar los Iconos.
Importa fuente Inter del archivo /assets/inter.woff2.

### Puedes ver funcionando la app en el siguiente link:
https://kikegarciabio.netlify.app/

## Inicializar el proyecto en una carpeta nueva:
npm init -y

## Instalar las librerias npm:
npm install

## Instalar dependencias:
npm install tailwindcss @tailwindcss/cli
npm install @midudev/tailwind-animations

## Crear un archivo .vscode/settings.json y asociar Tailwind con archivos de tipo css:
{
  "files.associations": {
    "*.css": "tailwindcss"
  }
}

## Para compilar a un archivo css que podamos exportar y luego ejecutar:
1- Crear el archivo input.css con los import y librerias a utilizar.

2- Importar el pluggin en el archivo input.css:
@plugin "@midudev/tailwind-animations";

3- Agregar este scrip en el archivo package.json:
"build:styles": "npx @tailwindcss/cli -i ./input.css -o ./assets/output.css"

4- Ejecutar el scrip para compilar Tailwind y generar el archivo output.css:
npm run build:styles

5- Para desplegar copia el archivo index.html y la carpeta assests al sitio de despilegue que elijas.

---

## Plugging importado:
Páginas del pluggin:
https://tailwindcss-animations.vercel.app/

https://github.com/midudev/tailwind-animations

