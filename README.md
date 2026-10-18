# Landing page CEDIPE

Sitio estático (HTML + CSS + JS, sin frameworks ni build) para el Centro de Enfermedades Digestivas Pediátricas (CEDIPE). Pensado para publicarse gratis en GitHub Pages.

## Sesión de Claude Code

Este proyecto se desarrolló con Claude Code. Para retomar la conversación original (contexto completo de decisiones y avances):

- Sesión: https://claude.ai/code/session_013gv3KFRhZiAnftV2SngTTV

Ver también `PROYECTO.md` para la bitácora de objetivos, decisiones y pendientes.

## Estado: publicado, pendiente de habilitar indexación

El sitio ya está publicado en GitHub Pages (repo `drajeco/cedipeWeb`, rama `main`) y tiene el número de WhatsApp real. `robots.txt` (`Disallow: /`) y la meta `<meta name="robots" content="noindex, nofollow">` en `index.html` todavía bloquean su indexación en buscadores; pueden retirarse cuando se decida habilitarla.

El sitio incluye un formulario de contacto visual como canal alternativo, pero **todavía no envía datos**: al enviarlo, informa que la vía disponible es WhatsApp. Para activarlo se requiere configurar un endpoint de Formspree y confirmar el email `cedipe.gastro@gmail.com` desde la cuenta propietaria.

## Antes de anunciar el sitio: revisar datos de contacto

1. **Dirección/teléfono/email**, si cambian, están en `index.html` en las secciones "Ubicación" y "Contacto", y en el `<footer>`. El WhatsApp actual es `+598 92 021 615` (en los enlaces se utiliza el formato `59892021615`).

## Seguimiento de visitas (analytics)

Se eligió **Google Analytics (GA4)** (se probó primero Cloudflare Web Analytics, pero el alta del sitio quedó trabada en el dashboard). Falta el paso final:

1. Crear una propiedad en [analytics.google.com](https://analytics.google.com) con un flujo de datos "Web" apuntando a `https://drajeco.github.io/cedipeWeb/`.
2. Copiar el **Measurement ID** (`G-XXXXXXXXXX`) que te da GA4.
3. Agregarlo en `index.html`, dentro del `<head>`, con el snippet estándar de `gtag.js` (ver [instrucciones de Google](https://support.google.com/analytics/answer/9304153)).

Ya se agregó en el `<footer>` un aviso breve de que el sitio usa Analytics, ya que GA4 usa cookies.

## Cómo publicar en GitHub Pages (gratis)

> Para este proyecto ya está hecho (repo `drajeco/cedipeWeb`, Pages activo). Estos pasos quedan como referencia por si hay que rehacerlo o replicarlo en otro repo.

1. Creá un repositorio nuevo en GitHub (puede ser público, es requisito del plan gratuito de Pages).
2. Desde esta carpeta:
   ```bash
   git init
   git add .
   git commit -m "Landing page CEDIPE"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
   git push -u origin main
   ```
3. En GitHub: **Settings → Pages** → en "Build and deployment" elegí *Deploy from a branch*, rama `main`, carpeta `/ (root)`.
4. En un par de minutos el sitio queda disponible en `https://TU_USUARIO.github.io/TU_REPO/`.

Para actualizar el sitio ya publicado (remoto ya configurado como `origin`), alcanza con:
```bash
git add .
git commit -m "Descripción del cambio"
git push
```
GitHub Pages redespliega solo en cada push a `main`.

Si más adelante compran un dominio propio, se agrega en la misma sección de Pages ("Custom domain") y se genera automáticamente un archivo `CNAME` — no hace falta tocar el resto del sitio.

## Estructura

```
index.html
css/style.css
js/script.js
assets/img/       imágenes optimizadas para el sitio
contenido/        material fuente (logo original, fotos, textos de Instagram) — no se publica tal cual
robots.txt        bloqueo temporal de indexación (sacar cuando el sitio tenga datos reales)
.nojekyll         evita que GitHub Pages procese el sitio con Jekyll
PROYECTO.md       bitácora de objetivos, decisiones y pendientes del proyecto
```

## Ver el sitio localmente

Alcanza con abrir `index.html` en el navegador. Si preferís un servidor local:

```bash
python3 -m http.server 8000
```

y entrar a `http://localhost:8000`.
