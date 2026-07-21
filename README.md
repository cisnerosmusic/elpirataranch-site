# El Pirata Ranch — elpirataranch.com

Sitio oficial de **El Pirata Ranch**, restaurante de comida cubana al aire libre en Miami: picaderas, pescado frito entero, cerdo asado en leña, música en vivo y eventos. Una marca, dos locales:

- **Ranch #1** — 15901 SW 200th St, Miami, FL 33187 · 786-566-4587 · [`/ranch-1/`](https://elpirataranch.com/ranch-1/)
- **Richmond Dr** — 19511 SW 168th St, Miami, FL 33187 · 786-622-4291 · [`/richmond/`](https://elpirataranch.com/richmond/)

("Richmond Dr" es nombre público provisional del local que el dueño llama internamente #0; se ajustará cuando confirme cómo le llama la gente.)

## Estado: EN PRODUCCIÓN (lanzado 20 jul 2026)

- **https://elpirataranch.com** con HTTPS forzado; www y http redirigen al apex.
- DNS en GoDaddy: 4 registros A de GitHub Pages + CNAME www → cisnerosmusic.github.io. Se conservaron MX/SPF/DMARC de GoDaddy para futuro correo del dominio.
- **Google Search Console verificada**, sitemap enviado y aceptado (3 páginas), indexación solicitada a mano para las tres URLs.
- **PageSpeed: 100 Rendimiento (móvil y desktop) · 100 SEO · 100 Recomendaciones · 90 Accesibilidad · 3/3 navegación con agentes.**

## Qué es técnicamente

HTML y CSS estáticos a mano, sin frameworks ni dependencias (filosofía Index01: rápido, ligero, cero peso muerto). Página de marca + una página por local, cada una con su schema `Restaurant` propio: la base del SEO local, para que cada ficha de Google Business apunte a su propia URL.

```
index.html            marca: hero, especialidades, eventos, FAQ, los dos locales
ranch-1/index.html    local SW 200th St: eventos, música en vivo, ficha + breadcrumb
richmond/index.html   local SW 168th St: desayuno 6 AM, horarios, ficha + breadcrumb
styles.css            estilos compartidos
img/                  fotos optimizadas (~200 KB), logo de marca, favicons
favicon.ico           medallón pirata multitamaño (raíz)
llms.txt              ficha del negocio para asistentes de IA (AEO)
humans.txt            créditos
robots.txt            allow universal + bienvenida explícita a crawlers de IA
sitemap.xml           3 URLs con lastmod
CNAME                 elpirataranch.com (dominio custom de GitHub Pages)
```

### Identidad

- Logo vectorial oficial recompuesto: "RANCH" centrado bajo "EL PIRATA", sin el "#1" (cirugía del content stream del PDF de Illustrator; fuentes en la carpeta local de trabajo, `logo-elpirata-ranch.pdf/png`).
- Favicon fase 1: medallón (calavera + aro dorado sobre negro), extraído del vectorial. **Pendiente: versión pro diseñada.**
- Fotos profesionales del dueño (6000px originales, optimizadas a 1600px/~200 KB). En secciones principales solo las fotos SIN el logo antiguo estampado (ese logo dice "EL PIRATA" sin "RANCH").

### SEO / AEO aplicado

- Schema.org: `Restaurant` de marca + uno por local (con `hasMap`, `acceptsReservations`, `amenityFeature`: aire libre, música en vivo, parking gratis, pet-friendly), `FAQPage` (5 preguntas con búsqueda local real), `BreadcrumbList` en fichas.
- FAQ visible en portada, títulos y descripciones con keywords locales (Redland/Richmond, 33187), enlaces cruzados en el pie, og:locale, fetchpriority en logo del hero.
- robots.txt permite y nombra crawlers de IA (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, CCBot, Applebot-Extended...) y referencia llms.txt.

## Decisiones editoriales vigentes

- **Sin menú con precios**: el dueño no ha confirmado precios ni rotación por día. La web dice "el menú cambia según el día, pregunta por teléfono".
- **Sin Uber Eats / DoorDash**: las cuentas existen pero las tablets están desconectadas. Sin botones ni menciones de delivery hasta que sea real.
- **Horarios confirmados por las fichas de Google Business** (verificadas 20 jul 2026): Richmond Dr Lun-Jue 6-20, Vie-Dom 6-23 · Ranch #1 Lun-Mié 8-20, Jue-Dom 8-23. Precios GBP: Richmond $10-20, Ranch #1 $20-30. Ratings reales: 4.8★ (96) y 4.7★ (70) = 166 reseñas.
- Teléfono como único canal de pedidos/reservas, reflejado en toda la web.

## Pendientes de Fase 1 (afinado)

- [ ] Favicon "pro" diseñado (el actual es funcional, fase 1 OK).
- [ ] Los 10 puntos de Accesibilidad (90→100): revisar contrastes señalados por Lighthouse.
- [ ] Datos del dueño: nombre público definitivo del local de Richmond Dr, carácter de cada local, dónde se hace la pizza cubana (plato firma según reseñas, aún sin foto ni mención). (Horarios: RESUELTO vía fichas de Google Business.)
- [ ] Pregunta pendiente del TikTok (@el.pirata.miami, 2.7k seguidores, su canal más activo, ya enlazado en footer/schema/llms.txt): ¿qué es "El Pirata Ranch 3" que se ve en los letreros de los videos? ¿tercer local o nombre del ranchón?
- [ ] Foto limpia del pescado frito entero (el plato de la casa perdió su tarjeta por tener solo foto con logo viejo).
- [ ] Versión en inglés + hreflang.
- [ ] Bing Webmaster Tools (importar desde Search Console).
- [ ] Instagram: poner elpirataranch.com en la bio de @elpirata_cubanfood (primer backlink, lo hace el dueño en 30 segundos).
- [ ] Reclamar y unificar fichas: Google Business x2 (cada una apuntando a su página), Yelp x2, consolidar las 2-3 páginas de Facebook.
- [ ] Reponer botones Uber Eats/DoorDash cuando reconecten las tablets.

## Fase 2: pedidos online con Clover (especificación cerrada, pendiente de arrancar)

Arquitectura validada contra docs.clover.com (jul 2026). Spec completa en el documento de trabajo local `SPEC-pedidos-delivery.md` (carpeta OneDrive de El Pirata Ranch).

Resumen: widget de pedidos propio en la web → Cloudflare Worker → Clover de cada local (**cada local tiene su propio merchant ID**, confirmado): menú sincronizado por Inventory API (cache KV), orden por Atomic Orders API + `print_event` explícito a cocina, pago con iframe/checkout alojado por Clover (PCI queda en Clover), webhooks + reconciliación.

Pasos para arrancar:
1. [ ] Ernesto: crear cuenta en el Global Developer Dashboard de Clover + merchant de prueba en sandbox.
2. [ ] Prototipo end-to-end en sandbox: menú → orden → pago → impresión → webhooks.
3. [ ] Dueño (por cada local): Merchant ID, tokens Ecommerce API (requiere 2FA), verificar que la sección "Ecommerce API Tokens" existe en su dashboard (⚠️ riesgo principal del proyecto: es un entitlement de Fiserv; si no aparece, pedirlo al rep temprano), inventario de dispositivos/impresoras, plan contratado y tarifa CNP real (~3.5% + $0.10).
4. [ ] Producción con feature flag por local.

## Fase 3: delivery propio + SMS (especificación cerrada)

- Delivery con empleado propio; radio 10 millas validado por dirección en checkout (geocodificación puntual, **sin GPS ni tracking, decisión firme**).
- Se implementa para ambos locales pero **lanza activo solo en el Ranch #1** (el #0 no tiene transporte aún); flag `delivery_enabled` por local.
- Página móvil mínima para el repartidor (dos botones: "Salí" / "Entregado").
- SMS transaccionales vía Twilio, **bilingües ES/EN a elección del cliente** en checkout: pedido recibido → listo/en camino → entregado + enlace de reseña de Google (motor de reseñas para SEO local). Requiere registro A2P 10DLC (trámite de días: arrancar temprano) y casilla de consentimiento.

---

Construido por [Index01](https://index01.net) · Diseño web, SEO y AEO · Miami.
