# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Proyecto

Sitio web estático de **LaNik** — marca de gorras tejidas artesanalmente en Buenos Aires. Single-page application en HTML/CSS/JS vanilla, desplegada en GitHub Pages en `https://edgardo-lamas.github.io/LaNik/`.

No hay build system, bundler, ni dependencias npm. Todo el código vive en `index.html`.

## Estructura

- `index.html` — todo el sitio: HTML, CSS (inline en `<style>`) y JS (inline en `<script>`)
- `gorras img/` — imágenes de productos (`Gorro-1.jpeg` a `gorro-10.jpeg`)
- `Logo/` — logo de la marca
- `.nojekyll` — evita el procesamiento Jekyll en GitHub Pages
- `.claude/skills/optimizar/` — skill custom para optimización del sitio

## Arquitectura del HTML

El sitio está organizado en secciones con IDs para navegación interna:

| Sección | ID | Fondo |
|---|---|---|
| Hero | — | `--charcoal` (#1A1A1A) |
| Colección (productos) | `#coleccion` | `--charcoal-mid` (#2C2C2C) |
| Historia / valores | `#historia` | `--crema` (#F5EFE0) |
| Proceso (4 pasos) | `#proceso` | `--charcoal` |
| Galería scroll | `#galeria` | `--charcoal-mid` |
| Contacto / CTA | `#contacto` | `--terracota` (#B5432A) |
| Footer | — | `--charcoal` |

## Sistema de diseño

Variables CSS definidas en `:root`:
- **Colores principales**: `--terracota` (#B5432A), `--charcoal` (#1A1A1A), `--charcoal-mid` (#2C2C2C), `--crema` (#F5EFE0), `--sage` (#8FAF9A), `--ocre` (#C4882A)
- **Tipografías**: `--font-head` (Space Grotesk), `--font-body` (Inter) — cargadas desde Google Fonts

## Convenciones de código

- CSS organizado por sección con comentarios `/* ─── NOMBRE ── */`
- Responsive con breakpoints en `900px` (tablet) y `600px` (mobile)
- Hamburger menu mobile: `.nav-hamburger` / `.nav-mobile-menu` con clases `.open`
- Scroll reveal: elementos con `.reveal` + IntersectionObserver en JS
- Estado de stock bajo: clase `.low-stock` en `.product-card` (borde ocre + badge pulsante)

## Analytics y contacto

- **GA4**: ID `G-DH6MSEKGQW` — trackea `click_whatsapp` y `click_instagram` vía `gtag('event', ...)`
- **WhatsApp**: número `5491100000000` (placeholder, debe actualizarse con el real)
- **Instagram**: `@lanik`
- **Email**: `lanik@gmail.com`

## Deploy

Push a `main` → GitHub Pages despliega automáticamente. No hay CI/CD adicional.
Para verificar el sitio localmente, abrir `index.html` directo en el browser o usar cualquier servidor estático:
```
python3 -m http.server 8000
```

## Skill disponible

`/optimizar` — audita y aplica mejoras de Performance, SEO, Accesibilidad y Core Web Vitals directamente en `index.html`.
