# El Pirata Ranch — elpirataranch.com

Sitio oficial de **El Pirata Ranch**, restaurante de comida cubana al aire libre en Miami: picaderas, pescado frito entero, cerdo asado en leña, música en vivo y eventos. Una marca, dos locales:

- **Ranch #1** — 15901 SW 200th St, Miami, FL 33187 · 786-566-4587 · [`/ranch-1/`](https://elpirataranch.com/ranch-1/)
- **Richmond Dr** — 19511 SW 168th St, Miami, FL 33187 · 786-622-4291 · [`/richmond/`](https://elpirataranch.com/richmond/)

## Estado: EN PRODUCCIÓN (lanzado 20 jul 2026)

- **https://elpirataranch.com** con HTTPS forzado; www y http redirigen al apex.
- DNS en GoDaddy: 4 registros A de GitHub Pages + CNAME www → cisnerosmusic.github.io.
- **Google Search Console verificada**, sitemap enviado y aceptado, indexación solicitada a mano.
- **PageSpeed: 100 Rendimiento (móvil y desktop) · 100 SEO · 100 Recomendaciones · 90 Accesibilidad · 3/3 navegación con agentes.**

## Qué es técnicamente

HTML y CSS estáticos a mano, sin frameworks ni dependencias (filosofía Index01: rápido, ligero, cero peso muerto). Página de marca + una página por local, cada una con su schema `Restaurant` propio: la base del SEO local, para que cada ficha de Google Business apunte a su propia URL.

```
index.html            marca: hero, especialidades, eventos, FAQ, los dos locales
ranch-1/index.html    local SW 200th St: eventos, música en vivo, ficha + breadcrumb
richmond/index.html   local SW 168th St: desayuno, horarios, ficha + breadcrumb
en/                   versión en inglés (espejo reescrito: /en/, /en/ranch-1/, /en/richmond/)
styles.css            estilos compartidos (incluye selector de idioma .lang)
img/                  fotos optimizadas (~200 KB), logo de marca, favicons, tarjetas OG
favicon.ico           medallón pirata multitamaño (raíz)
llms.txt              ficha del negocio para asistentes de IA (AEO), bilingüe
humans.txt            créditos
robots.txt            allow universal + bienvenida explícita a crawlers de IA
sitemap.xml           6 URLs (ES+EN) con lastmod y alternates hreflang
CNAME                 elpirataranch.com (dominio custom de GitHub Pages)
404.html              página de error con marca
docs/                 documento rector de marca (PDF)
```

### Bilingüe ES/EN (21 jul 2026)

- `/en/` es reescritura para su público (anglo de Miami, turistas, campers del Thousand Trails junto al Ranch #1), no traducción literal.
- `hreflang` es/en/x-default en las 6 páginas (x-default → español, el idioma del negocio); selector ES↔EN en el header de todas.
- Schema EN reutiliza los mismos `@id` de entidad (una sola entidad por local ante Google); FAQPage propio en inglés (`/en/#faq`, `inLanguage: en`).
- Sitemap con los 6 URLs y alternates `xhtml:link`.

### Identidad

- Logo vectorial oficial recompuesto: "RANCH" centrado bajo "EL PIRATA".
- Favicon (versión pro, 21 jul 2026): medallón rehecho desde el logo de marca, calavera más grande y aro dorado más grueso, legible a 16 px. Set completo 16/32/48/192/512 + `.ico` multitalla + `apple-touch-icon`.
- Tarjetas OG 1200x630 por página (home, Ranch #1, Richmond Dr): foto real del plato con degradado, logo, título serif, subrayado oro, dirección y barra roja. Al compartir cualquier URL sale la marca completa.
- **Documento rector de marca (PDF, 10 págs.):** copia de consulta en [`docs/documento-rector-de-marca.pdf`](docs/documento-rector-de-marca.pdf).
- Fotografía profesional optimizada para web (originales 6000px → 1600px / ~200 KB), encuadres por regla de los tercios.

### SEO / AEO aplicado

- Schema.org: `Restaurant` de marca + uno por local (con `hasMap`, `acceptsReservations`, `amenityFeature`: aire libre, música en vivo, parking gratis, pet-friendly), `FAQPage` (5 preguntas con búsqueda local real), `BreadcrumbList` en fichas.
- FAQ visible en portada, títulos y descripciones con keywords locales (Redland/Richmond, 33187), enlaces cruzados en el pie, og:locale, fetchpriority en logo del hero.
- robots.txt permite y nombra crawlers de IA (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, CCBot, Applebot-Extended...) y referencia llms.txt.

## Decisiones editoriales vigentes

- **Sin menú con precios**: el menú cambia según el día; la web invita a preguntar por teléfono.
- **Teléfono como único canal de pedidos y reservas**, reflejado en toda la web.
- Horarios publicados según las fichas oficiales de Google Business de cada local.

## Afinado pendiente (Fase 1)

- [ ] Accesibilidad 90→100: revisar contrastes señalados por Lighthouse.
- [ ] Bing Webmaster Tools (importar desde Search Console).
- [ ] Fotografía adicional de platos para completar tarjetas.
- [x] Versión en inglés + hreflang — HECHO 21 jul 2026 (ver sección Bilingüe).

Las fases siguientes del proyecto (pedidos online y delivery) están especificadas y se gestionan en la documentación interna del estudio.

---

Construido por [Index01](https://index01.net) · Diseño web, SEO y AEO · Miami.
