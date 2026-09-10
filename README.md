# Landing page CEDIPE

Sitio estático (HTML + CSS + JS, sin frameworks ni build) para el Centro de Enfermedades Digestivas Pediátricas (CEDIPE). Pensado para publicarse gratis en GitHub Pages.

## Sesión de Claude Code

Este proyecto se desarrolló con Claude Code. Para retomar la conversación original (contexto completo de decisiones y avances):

- Sesión: https://claude.ai/code/session_013gv3KFRhZiAnftV2SngTTV

Ver también `PROYECTO.md` para la bitácora de objetivos, decisiones y pendientes.

## Estado: publicado, en modo de prueba

El sitio ya está publicado en GitHub Pages (repo `drajeco/cedipeWeb`, rama `main`), pero todavía usa un número de WhatsApp de prueba (ver abajo). Mientras tanto, `robots.txt` (`Disallow: /`) y la meta `<meta name="robots" content="noindex, nofollow">` en `index.html` bloquean su indexación en buscadores. **Sacá esas dos protecciones recién cuando el WhatsApp sea el real** — si no, quedaría indexado con un dato de prueba.

El sitio **no tiene formulario de contacto** — solo botón de WhatsApp y email como texto. Se sacó porque requería Formspree, que necesita que el dueño de `cedipe.gastro@gmail.com` confirme un email de verificación, y quien mantiene este repo no tiene acceso a esa casilla. Si en algún momento se resuelve ese acceso, se puede reincorporar (ver `PROYECTO.md`).

## Antes de anunciar el sitio: cosas por reemplazar

1. **Número de WhatsApp real.** Ahora mismo el sitio usa un número de prueba (`598910303333`). Buscá y reemplazá `598910303333` en `index.html` (aparece en el botón flotante, el header y varias secciones) por el número real, en formato internacional sin espacios ni símbolos (ej: `59899123456`).

2. **Dirección/teléfono/email**, si cambian, están en `index.html` en las secciones "Ubicación" y "Contacto", y en el `<footer>`.

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
