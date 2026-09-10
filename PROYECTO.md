# Proyecto: Landing page CEDIPE

> Este archivo es la bitácora del proyecto. Se va actualizando en cada sesión de trabajo para poder retomarlo en otro chat sin perder contexto. No se borra historia vieja: las decisiones superadas se marcan como tales en vez de eliminarse.

## Objetivo

Crear una landing page para CEDIPE (Centro de Enfermedades Digestivas Pediátricas), consultorio de gastroenterología pediátrica en Montevideo, Uruguay, con presencia activa en Instagram (**@cedipe.gastroped**) pero sin sitio web propio.

**Objetivo funcional:** que los pacientes puedan consultar/agendar citas médicas desde la web.

**Restricción principal:** minimizar al máximo los costos de desarrollo y mantenimiento (idealmente $0/mes).

## Decisiones tomadas

| Tema | Decisión | Motivo |
|---|---|---|
| Agendamiento | Botón de WhatsApp (`wa.me`) **+** formulario de contacto | WhatsApp es gratis e inmediato; el formulario suma un canal formal. |
| Formulario | Formspree (plan gratuito, hasta 50 envíos/mes) | No requiere backend propio ni costo. |
| Hosting | GitHub Pages | 100% gratis, requiere cuenta de GitHub y repo público. |
| Dominio | Por ahora el subdominio gratuito de GitHub Pages (`usuario.github.io`) | Se evalúa comprar uno propio más adelante; migrar es solo agregar un archivo `CNAME`, sin rehacer el sitio. |
| Stack | HTML + CSS + JS plano, sin frameworks ni build step | Menor complejidad de mantenimiento, ideal para GitHub Pages. |
| Equipo médico | Sin nombres ni fotos individuales por ahora — sección institucional genérica | Decisión explícita del usuario para arrancar más rápido. |
| Dirección publicada | Hospital Italiano, Planta Baja, Consultorio 17, Bv. Artigas 1632, Montevideo | Dato encontrado en material de Instagram (más completo que el dato inicial "Consultorio 19" sin calle); el usuario confirmó usar este. |
| Teléfono | Número de **prueba/placeholder**: `+598 91 030 3333` | El usuario pidió explícitamente no publicar un teléfono real todavía. **Pendiente reemplazar antes de publicar de verdad.** |
| Email de contacto | cedipe.gastro@gmail.com | Dato real provisto por el usuario. |
| Obras sociales/prepagas | No se listan en el sitio | Decisión del usuario ("obviemos esa información"). |
| Contenido | Se usa contenido real de Instagram (`contenido/texto.md` y `contenido/imagenes/`) en vez de placeholders genéricos | El usuario proveyó el material; da más autenticidad y ahorra tiempo de redacción. |

## Estado actual (última actualización: 2026-09-09)

Sitio construido y funcionando localmente. Estructura del proyecto:

```
07 - pagina_web/
├── index.html          → landing de una sola página
├── css/style.css        → estilos (paleta azul marino + celeste, tomada del logo real)
├── js/script.js         → menú móvil + año dinámico en el footer
├── assets/img/          → logo, favicon y 6 fotos optimizadas (comprimidas con sips, de ~1-2MB a 50-160KB)
├── contenido/            → material fuente original (logo, fotos, texto.md con posts de Instagram) — no se publica tal cual
├── .nojekyll             → evita que GitHub Pages procese el sitio con Jekyll
├── README.md             → instrucciones técnicas de despliegue y reemplazo de datos
└── PROYECTO.md           → este archivo
```

Secciones de `index.html`: Header con nav, Hero, Servicios (7 prestaciones), Sobre CEDIPE, Info para familias (acordeón con estreñimiento, celiaquía, intolerancia a la lactosa, EII, diarrea crónica, disquecia del lactante), Ubicación (con mapa embebido de Google Maps), Contacto (formulario + WhatsApp + email), botón flotante de WhatsApp, footer.

Se verificó que el servidor local sirve correctamente el HTML, CSS, JS y las 7 imágenes (todo 200 OK). El usuario abrió `index.html` en su navegador para revisión visual (feedback pendiente).

Se ejecutó `git init` y se creó el primer commit local (28 archivos) el 2026-09-10. Ese mismo día se creó el repositorio remoto en GitHub (`https://github.com/drajeco/cedipeWeb`, creado manualmente por el usuario en github.com) y se hizo el push inicial (`main` → `origin/main`).

El mismo 2026-09-10 el usuario activó GitHub Pages. Se verificó que el deploy (`pages build and deployment`) terminó exitoso y que el sitio responde 200 en `drajeco.github.io/cedipeWeb` (URL sin hipervínculo a propósito, ver nota de indexación más abajo), con HTML, CSS, JS e imágenes cargando correctamente y todas las secciones presentes.

**El sitio ya está online y públicamente accesible.** Sigue con los datos placeholder (WhatsApp de prueba, Formspree sin configurar) — ver pendientes.

**Indexación/discreción temporal:** dado que el sitio es público mientras todavía tiene datos placeholder, se agregó `robots.txt` (`Disallow: /`) y `<meta name="robots" content="noindex, nofollow">` en `index.html` para que buscadores como Google/Bing no lo indexen. Además, se sacó el hipervínculo activo a la URL publicada de `README.md`/`PROYECTO.md` (queda como texto plano en backticks), porque GitHub renderiza esos `.md` en una página de alta autoridad que los crawlers rastrean seguido, y un link ahí era la vía más probable de que el sitio se indexara sin querer. Ninguna de estas medidas oculta el sitio de alguien que ya tenga el link — solo evita que se descubra "por accidente" vía buscadores mientras se termina de cargar el contenido real.

## Pendientes / próximos pasos

1. **Feedback visual del usuario** sobre el diseño abierto en el navegador (colores, textos, orden de secciones, imágenes) — en curso.
2. Reemplazar el número de WhatsApp de prueba (`598910303333`) por el número real del consultorio.
3. Crear cuenta gratuita en [formspree.io](https://formspree.io), generar el ID de formulario y reemplazarlo en `index.html` (buscar `TU_ID_DE_FORMSPREE`).
4. Decidir si se publica ya o se espera a tener el teléfono real.
5. ~~Publicar en GitHub Pages: git init, crear repo remoto, push~~ → **hecho** (repo: `https://github.com/drajeco/cedipeWeb`).
6. ~~Activar GitHub Pages~~ → **hecho**, sitio online en `https://drajeco.github.io/cedipeWeb/`.
7. Reemplazar el WhatsApp de prueba por el real y configurar Formspree (pendientes 2 y 3) — ahora es más urgente porque el sitio ya es público.
8. (Opcional, futuro) Evaluar compra de dominio propio y conectarlo vía `CNAME`.

## Notas para retomar en otro chat

- Todo el código y contenido ya generado vive en esta carpeta (`07 - pagina_web/`) — no hace falta reexplicar el proyecto desde cero, alcanza con leer este archivo y `README.md`.
- El material fuente original de Instagram (fotos + texto completo de los posts) está en `contenido/`, por si se necesita agregar más secciones o contenido nuevo más adelante.
- Este archivo debe actualizarse cada vez que se tome una decisión nueva, se complete un pendiente, o cambie el alcance del proyecto.
