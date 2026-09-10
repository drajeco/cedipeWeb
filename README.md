# Landing page CEDIPE

Sitio estático (HTML + CSS + JS, sin frameworks ni build) para el Centro de Enfermedades Digestivas Pediátricas (CEDIPE). Pensado para publicarse gratis en GitHub Pages.

## Sesión de Claude Code

Este proyecto se desarrolló con Claude Code. Para retomar la conversación original (contexto completo de decisiones y avances):

- Sesión: https://claude.ai/code/session_013gv3KFRhZiAnftV2SngTTV

Ver también `PROYECTO.md` para la bitácora de objetivos, decisiones y pendientes.

## Antes de publicar: 3 cosas por reemplazar

1. **Número de WhatsApp real.** Ahora mismo el sitio usa un número de prueba (`598910303333`). Buscá y reemplazá `598910303333` en `index.html` (aparece en el botón flotante, el header y varias secciones) por el número real, en formato internacional sin espacios ni símbolos (ej: `59899123456`).

2. **Formulario de contacto (Formspree).**
   - Creá una cuenta gratuita en [formspree.io](https://formspree.io) (hasta 50 envíos/mes sin costo).
   - Creá un formulario nuevo y copiá el ID que te da (algo como `xzbqjkvw`).
   - En `index.html`, buscá `https://formspree.io/f/TU_ID_DE_FORMSPREE` y reemplazá `TU_ID_DE_FORMSPREE` por ese ID.
   - Formspree te va a pedir confirmar el email la primera vez que llegue un mensaje de prueba.

3. **Dirección/teléfono/email**, si cambian, están en `index.html` en las secciones "Ubicación" y "Contacto", y en el `<footer>`.

## Cómo publicar en GitHub Pages (gratis)

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

Si más adelante compran un dominio propio, se agrega en la misma sección de Pages ("Custom domain") y se genera automáticamente un archivo `CNAME` — no hace falta tocar el resto del sitio.

## Estructura

```
index.html
css/style.css
js/script.js
assets/img/       imágenes optimizadas para el sitio
contenido/        material fuente (logo original, fotos, textos de Instagram) — no se publica tal cual
```

## Ver el sitio localmente

Alcanza con abrir `index.html` en el navegador. Si preferís un servidor local:
```bash
python3 -m http.server 8000
```
y entrar a `http://localhost:8000`.
