---
name: optimizar
description: Optimiza un sitio web estático en 4 áreas: Performance, SEO, Accesibilidad y Core Web Vitals. Revisá el HTML principal y aplicá todas las mejoras posibles directamente en el código.
---

Optimizá el sitio web del proyecto actual aplicando mejoras en estas 4 áreas. Leé primero el archivo HTML principal, luego aplicá todos los cambios necesarios:

## 1. Performance
- Agregá `loading="lazy"` a todas las imágenes que no estén en el viewport inicial
- Agregá `fetchpriority="high"` a la imagen hero principal
- Asegurate que las fuentes de Google Fonts usen `display=swap`
- Mové cualquier JS no crítico al final del body o agregá `defer`
- Eliminá CSS o recursos que no se usen

## 2. SEO
- Verificá que exista `<meta name="description">` con texto descriptivo (150-160 caracteres)
- Agregá Open Graph tags: `og:title`, `og:description`, `og:image`, `og:url`, `og:type`
- Agregá Twitter Card tags: `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`
- Verificá que haya un solo `<h1>` y que la jerarquía de headings sea correcta (h1 → h2 → h3)
- Agregá `<link rel="canonical">` si no existe
- Verificá que el `<title>` sea descriptivo y tenga menos de 60 caracteres

## 3. Accesibilidad
- Revisá que todas las imágenes tengan `alt` descriptivo (no vacío, no genérico)
- Agregá `aria-label` a botones/links que solo tengan íconos SVG
- Verificá que los links de navegación sean descriptivos (no "click aquí")
- Asegurate que el orden de focus sea lógico
- Agregá `role` y atributos ARIA donde corresponda

## 4. Core Web Vitals
- Agregá `<link rel="preconnect">` para dominios externos usados (fonts, CDNs)
- Agregá `<link rel="preload">` para la imagen hero (LCP)
- Asegurate que no haya layout shifts: imágenes con dimensiones definidas o `aspect-ratio`
- Verificá que el viewport meta tag esté correcto

Al terminar, reportá un resumen de todos los cambios realizados organizados por categoría.
