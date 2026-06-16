# Cómo subir el Dashboard a Vercel

Este paquete contiene 2 archivos:
- `index.html` — el dashboard completo (renombrado desde proinsular_dashboard.html)
- `vercel.json` — configuración básica de seguridad (opcional pero recomendado)

No necesitas instalar nada de programación. Vercel detecta automáticamente que es un sitio estático y lo publica tal cual.

## Opción A — Sin cuenta de GitHub (la más rápida)

1. Ve a https://vercel.com y crea una cuenta gratis (puedes usar tu correo o Google).
2. Una vez dentro, busca el botón **"Add New..."** → **"Project"**.
3. Selecciona la pestaña **"Deploy"** o busca la opción de **subir una carpeta directamente** (drag and drop). Si no la ves de inmediato, instala la CLI con el método B, es más confiable.

## Opción B — Con la CLI de Vercel (recomendado, 5 minutos)

Esto requiere tener Node.js instalado en tu computadora (lo más probable es que ya lo tengas si en algún momento instalaste algo de programación; si no, descárgalo gratis de https://nodejs.org).

1. Abre una terminal (en Windows: "Símbolo del sistema" o "PowerShell"; en Mac: "Terminal").
2. Instala la herramienta de Vercel escribiendo:
   ```
   npm install -g vercel
   ```
3. Entra a la carpeta donde están estos archivos (`index.html` y `vercel.json`). Por ejemplo, si los descargaste a tu carpeta de Descargas:
   ```
   cd Descargas
   ```
4. Ejecuta:
   ```
   vercel
   ```
5. Te va a pedir iniciar sesión (te abre el navegador, inicias sesión con Google o GitHub, gratis).
6. Te hará algunas preguntas — responde así:
   - "Set up and deploy?" → Enter (sí)
   - "Which scope?" → Enter (tu cuenta personal)
   - "Link to existing project?" → escribe `n` (no)
   - "What's your project's name?" → escribe algo como `proinsular-dashboard` y Enter
   - "In which directory is your code located?" → Enter (la carpeta actual)
   - El resto de preguntas (framework, build command, etc.) → solo presiona Enter para aceptar las opciones por defecto, Vercel detecta que es HTML puro.
7. Al terminar te da una URL como `https://proinsular-dashboard-xxxx.vercel.app` — esa es la dirección pública de tu dashboard, ya funcionando.

## Para futuras actualizaciones

Cada vez que yo te entregue una nueva versión del archivo:
1. Reemplaza el `index.html` viejo por el nuevo en la misma carpeta.
2. Desde la terminal, en esa misma carpeta, ejecuta otra vez:
   ```
   vercel --prod
   ```
3. Eso actualiza la misma URL con los cambios nuevos, sin perder el link que ya tengas guardado o compartido.

## Dominio propio (opcional)

Si más adelante quieres que la URL sea algo como `dashboard.proinsular.com` en vez de `proinsular-dashboard-xxxx.vercel.app`:
1. Compra el dominio (en Namecheap, GoDaddy, o donde prefieras — normalmente 10-15 USD al año).
2. En el panel de Vercel, dentro de tu proyecto, ve a **Settings → Domains** y agrega el dominio.
3. Vercel te da unos registros DNS que debes configurar en el panel de tu proveedor de dominio (ellos mismos suelen tener guías para esto).

## Nota sobre la API Key de Anthropic

El dashboard usa una API Key de Anthropic para el Asistente IA, que cada usuario configura desde el ícono de llave en el panel lateral. Esa clave se guarda únicamente en el navegador de quien la ingresa (localStorage), no en Vercel ni en ningún servidor — así que cada persona que use el dashboard desde un navegador distinto deberá configurar su propia clave la primera vez.
