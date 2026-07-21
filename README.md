# El Pirata Ranch — sitio web

Sitio de **El Pirata Ranch**, restaurante de comida cubana al aire libre en Miami: picaderas, pescado frito entero, cerdo asado en leña, música en vivo y eventos. Una marca con dos locales:

- **Ranch #1** — 15901 SW 200th St, Miami, FL 33187 · 786-566-4587 · página `/ranch-1/`
- **Richmond Dr** — 19511 SW 168th St, Miami, FL 33187 · 786-622-4291 · página `/richmond/`

("Richmond Dr" es el nombre público provisional del local que el dueño llama internamente #0; se ajustará cuando confirme cómo le llama la gente.)

- **Estado:** sitio oficial v1, indexable. Sin menú de precios ni pedidos online todavía (Fase 2: integración Clover; Fase 3: delivery propio con SMS).
- **Ver en vivo:** https://cisnerosmusic.github.io/elpirataranch-site/
- **Dominio:** elpirataranch.com (GoDaddy; CNAME incluido en el repo, DNS apuntando a GitHub Pages).

## Qué es

HTML y CSS estáticos, sin frameworks ni dependencias: una página de marca + una página por local, cada una con su schema.org `Restaurant` propio (base del SEO local: cada ficha de Google Business apuntará a su página). Identidad rojo pirata, negro y dorado, con el logo vectorial oficial recompuesto (RANCH centrado, sin "#1") y fotografía profesional entregada por el dueño.

## Estructura

```
index.html          marca: hero, especialidades, eventos, los dos locales
ranch-1/index.html  local SW 200th St: eventos, música en vivo, ficha
richmond/index.html local SW 168th St: desayuno 6 AM, para llevar, ficha
styles.css          estilos compartidos
img/                fotos optimizadas (~200 KB) y logo de marca
CNAME, robots.txt, sitemap.xml
```

## Pendientes

- Menú con precios reales confirmados por el dueño (y rotación por día).
- Horarios del Ranch #1 confirmados (mientras tanto la página dice "llámanos").
- Nombre público definitivo del local de Richmond Dr.
- Versión en inglés y llms.txt.
- Fase 2: pedidos online con Clover · Fase 3: delivery propio + SMS (ver SPEC en carpeta local de trabajo).
- Reclamar y unificar Google Business, Yelp y las páginas de Facebook.

---

Construido por [Index01](https://index01.net) · Diseño web, SEO y AEO · Miami.
