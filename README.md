# WhAIgent — Sitio web

Sitio estático de marketing para [whaigent.com](https://whaigent.com). Un solo `index.html` autocontenido (CSS y JS inline, cero dependencias externas, cero requests de terceros). **Lighthouse mobile 30-jul-2026: Performance 100 · Accesibilidad 100 · Best Practices 100 · SEO 100** (LCP 1.2s, CLS 0, TBT 0ms). Al hostear, activar Brotli + cache headers (Cloudflare Pages lo hace solo) para mantenerlo.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | Todo el sitio (marcado, estilos, JS mínimo, JSON-LD) |
| `og-image.png` | Imagen para compartir en WhatsApp/redes (1200×630, con logo oficial) |
| `brand-logo-white.png` / `brand-logo-color.png` | Logos oficiales (rescatados de la web anterior) |
| `brand-favicon.png` | Favicon oficial |
| `brand-meta-partner.webp` | Badge Meta Business Partner oficial |
| `robots.txt` | Permite todo + apunta al sitemap |
| `sitemap.xml` | Sitemap (una URL) |
| `llms.txt` | SEO agéntico: resumen del producto para agentes IA (ChatGPT, Claude, Perplexity, etc.) |

## Cómo hostearlo gratis y conectar el dominio

Recomendado: **Cloudflare Pages** (gratis, CDN global, SSL automático).

1. Crear cuenta en [pages.cloudflare.com](https://pages.cloudflare.com) → "Upload assets" (o conectar un repo de GitHub con esta carpeta).
2. Subir esta carpeta tal cual. No hay build: es estático puro.
3. En el proyecto → Custom domains → agregar `whaigent.com` y `www.whaigent.com`.
4. En el DNS del dominio (donde esté registrado): apuntar según lo que indique Cloudflare (CNAME a `<proyecto>.pages.dev`). Si el dominio hoy apunta a HubSpot, este cambio de DNS es lo único que hay que tocar para salir de HubSpot — el contenido ya no depende de ellos.

Alternativas igual de válidas: **Netlify** (drag & drop en app.netlify.com/drop) o **Vercel**.

### Verificación post-deploy

- `https://whaigent.com/` carga y redirige www → apex (o al revés, consistente).
- `https://whaigent.com/robots.txt`, `/sitemap.xml`, `/llms.txt`, `/og-image.png` responden.
- Pasar [PageSpeed Insights](https://pagespeed.web.dev/) — mobile y desktop.
- Pegar la URL en un chat de WhatsApp para ver la preview (og-image).
- Dar de alta en [Google Search Console](https://search.google.com/search-console) y enviar el sitemap.

## Capturas del administrador — YA INTEGRADAS

La sección "La plataforma por dentro" usa capturas reales del negocio "Demo WhatsApp Agent" (datos ficticios sembrados el 30-jul-2026): Kanban de Prospectos, Seguimientos, Envíos masivos y Métricas. Archivos `shot-*.webp` (versión 1600px + `-sm` 800px con srcset, lazy-loading — no afectan PageSpeed). Para renovarlas: capturar el módulo, recortar el chrome del browser y regenerar los WebP con calidad 80.

Pendiente opcional: una captura de **Conversaciones** con datos demo (la actual del admin tiene chats reales, no publicable).

## Datos integrados de la web anterior

- WhatsApp de contacto: **+54 9 341 579-8632** (wa.me/5493415798632) — botón flotante, CTA final y footer.
- Precios: Starting $100.000 / Growing $150.000 / Enterprise $250.000 ARS/mes (1.000/5.000/10.000 respuestas), implementación $0 — sección #precios + FAQ + JSON-LD.
- Identidad: logo oficial (estrella + wordmark azul/teal), paleta #4d8af0 + #00bfa6, badge Meta Business Partner.

## Pendientes conocidos

- **Redes sociales**: la web vieja tenía íconos pero apuntaban a links genéricos (facebook.com sin perfil). Faltan las URLs reales para footer + JSON-LD `sameAs`.
- **Email de contacto**: no figura ninguno en la web vieja. Si existe (hola@whaigent.com?), va en footer + schema.
- **Legales**: aviso legal / política de privacidad / términos — la web vieja tenía links genéricos. Hay que redactarlos (los pide Meta para apps de WhatsApp).
- **Versión EN**: el producto es bilingüe; el sitio hoy es solo ES. Cuando quieras, se agrega `/en/` con hreflang.
- **Analytics**: no hay ningún tracker instalado. Si querés medir (Meta Pixel para campañas, o algo liviano como Plausible), decime y lo agrego sin romper el score.

## Editar

Todo está en `index.html`, organizado por secciones comentadas (`<!-- ===== HERO ===== -->`, etc.). Los colores y tipografía salen de las variables CSS en `:root` al principio del `<style>`.
