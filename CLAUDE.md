# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Proyecto

Sitio web de **LaNik** — marca de gorras tejidas artesanalmente en Buenos Aires. Single-page application en HTML/CSS/JS vanilla, desplegada en GitHub Pages en `https://edgardo-lamas.github.io/LaNik/`.

No hay build system, bundler, ni dependencias npm. Todo el código vive en `index.html`.

**Migración a Vercel** planeada cuando se desarrolle el agente de WhatsApp (necesita serverless functions).

---

## Roadmap de funcionalidades

| Estado | Tarea |
|---|---|
| ✅ Hecho | SEO técnico: favicon, sitemap.xml, robots.txt, Schema.org |
| ✅ Hecho | Datos de contacto reales: WhatsApp, email, Instagram |
| 🔜 Próximo | Integrar fotos nuevas `Fotos Lanik/` al sitio (7 modelos, 25 fotos) |
| ⏳ Pendiente | Migración a Vercel |
| ⏳ Pendiente | Agente de WhatsApp (Claude API + webhook + WhatsApp Business API) |
| ⏳ Pendiente | Dashboard con KPIs + agente IA (igual a Rodo's 3.0 y Sabiduría para el Corazón) |

---

## Datos de contacto reales

- **WhatsApp**: `5491131986298` (Alejandro)
- **Instagram**: `@Laniktejidos`
- **Email**: `laniktejidos@gmail.com`

---

## Estructura

- `index.html` — todo el sitio: HTML, CSS (inline en `<style>`) y JS (inline en `<script>`)
- `gorras img/` — imágenes antiguas de productos (`Gorro-1.jpeg` a `gorro-10.jpeg`)
- `Fotos Lanik/` — fotos nuevas profesionales: 7 modelos (`Mod 1/` a `Mod 7/`), 25 JPGs
- `Logo/Logo 1.jpeg` — logo original de la marca (kraft + azul + ovillo de lana)
- `favicon.svg` — favicon SVG monograma LN + ovillo terracota
- `sitemap.xml` — sitemap para Google
- `robots.txt` — apunta al sitemap
- `.nojekyll` — evita el procesamiento Jekyll en GitHub Pages

---

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

---

## Sistema de diseño

Variables CSS definidas en `:root`:
- **Colores principales**: `--terracota` (#B5432A), `--charcoal` (#1A1A1A), `--charcoal-mid` (#2C2C2C), `--crema` (#F5EFE0), `--sage` (#8FAF9A), `--ocre` (#C4882A)
- **Tipografías**: `--font-head` (Space Grotesk), `--font-body` (Inter) — cargadas desde Google Fonts

---

## Convenciones de código

- CSS organizado por sección con comentarios `/* ─── NOMBRE ── */`
- Responsive con breakpoints en `900px` (tablet) y `600px` (mobile)
- Hamburger menu mobile: `.nav-hamburger` / `.nav-mobile-menu` con clases `.open`
- Scroll reveal: elementos con `.reveal` + IntersectionObserver en JS
- Estado de stock bajo: clase `.low-stock` en `.product-card` (borde ocre + badge pulsante)

---

## Analytics

- **GA4**: ID `G-DH6MSEKGQW` — trackea `click_whatsapp` y `click_instagram` vía `gtag('event', ...)`

---

## Herramientas disponibles para creación de contenido

| Herramienta | Uso | Estado |
|---|---|---|
| **BFL Flux API** | Generación de imágenes con IA | ✅ `BFL_API_KEY` en `~/.zprofile` |
| **FLUX Kontext Pro** | Edición de imagen con referencia (I2I) | ✅ endpoint `/v1/flux-kontext-pro` |
| **Higgsfield CLI** | Generación de video IA (I2V) | ✅ autenticado, plan free (10 créditos) |
| **Canva MCP** | Diseño de assets visuales | ✅ MCP disponible en sesión |
| **ffmpeg** | Procesamiento y encoding de video | ✅ Homebrew (sin libfreetype — usar Python/Pillow para texto) |
| **Python + Pillow** | Generación de frames, texto sobre video, efectos Ken Burns | ✅ instalado |

### Notas de video
- ffmpeg **no tiene drawtext** compilado — para texto animado sobre video usar el script Python `/tmp/lanik_reel_gen.py`
- Higgsfield `cinematic_studio_video` cuesta ~8 créditos en plan free
- Higgsfield `kling2_6`, `wan2_7`, `seedance_2_0` requieren plan de pago

---

## Agente de WhatsApp — arquitectura planeada

Modelo de referencia: `api/spurgeon.js` de Sabiduría para el Corazón (más limpio que Rodo's).

```
Cliente escribe en WhatsApp
  → webhook POST a /api/lanik-agent (Vercel serverless)
  → carga knowledge base JSON del catálogo LaNik
  → llama a Claude API con system prompt especializado
  → responde de vuelta a WhatsApp vía Meta Cloud API o Twilio
```

Pendiente antes de desarrollar:
- Número dedicado para WhatsApp Business API
- Alejandro/Nati deben configurar Meta Business Suite y agregar a lamasedgardo2024@gmail.com como admin

---

## Deploy

Push a `main` → GitHub Pages despliega automáticamente. No hay CI/CD adicional.
Para verificar el sitio localmente:
```
python3 -m http.server 8000
```

## Skills disponibles

- `/optimizar` — audita y aplica mejoras de Performance, SEO, Accesibilidad y Core Web Vitals
- `/canvas-design` — crea flyers y assets visuales como PNG/PDF
- `/bfl-api` — guía de integración con BFL Flux API
