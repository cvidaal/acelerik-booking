# CLAUDE.md

## Qué es este proyecto

Web del producto **Acelerik Booking** (https://booking.acelerik.com): sistema de reservas de cumpleaños para **parques infantiles** (reserva online, cobro de señal con Stripe, panel de gestión, emails y recordatorios automáticos). Público: dueños de parques infantiles en España. Tono directo, sin cifras ni promesas no acreditadas.

Booking es un producto de **ACELERIK** (https://www.acelerik.com), empresa de sistemas de automatización con IA de Carlos Vidal. La web de la empresa es otro repo: `../acelerik-smart-automation`. Cada producto tiene su propia web e identidad; aquí no se habla de la empresa salvo el enlace "Un producto de Acelerik" del footer.

El software de reservas en sí está en `../acelerik-demo-cumple` (React + backend Go, Supabase, Stripe, n8n). La demo pública es https://acelerik-demo.onrender.com/reservar (datos ficticios, pagos de prueba). Consúltalo para describir funciones reales del producto; no anuncies nada que no exista allí.

## Stack

React 18 + TypeScript + Vite 5, Tailwind + shadcn/ui (`src/components/ui/`, alias `@/` → `src/`), React Router 6. Formulario de contacto con Formspree (mismo endpoint que la web de Acelerik; los envíos llevan `_subject` y `source` para distinguirlos). Sin backend, sin variables de entorno, sin analítica ni cookies. Hosting previsto: **Cloudflare Pages** (`public/_redirects`).

## Comandos

```bash
npm ci
npm run dev        # http://localhost:8080
npm run build      # salida en dist/
npx tsc --noEmit -p tsconfig.app.json
```

No hay tests automatizados.

## Estructura

- `src/pages/Home.tsx`: la landing (`/`). `/parques` redirige a `/` por los enlaces antiguos.
- `src/pages/LegalPage.tsx`: aviso legal, privacidad, cookies y términos (titular: ACELERIK).
- `src/components/Studio.tsx`: menú, `PageMeta` (restaura title/meta de la home) y animaciones `.reveal`.
- `src/components/{ParkViewSection,CasesSection,ContactSection,Footer}.tsx`: secciones (`#asi-lo-ve`, `#casos`, `#contacto`).
- `src/lib/site-config.ts`: única fuente de URLs, contacto (+34 657 506 301, hola@acelerik.com) y datos legales.
- `src/studio.css`: estilos del diseño (minificado).

## Convenciones

- Una ruta nueva: `App.tsx` (encima de `*`), `public/_redirects` y `public/sitemap.xml`.
- Los metadatos de `index.html` y `PageMeta` deben coincidir.
- Ningún servicio de terceros puede cargarse sin acción del usuario (YouTube solo al pulsar). Un servicio nuevo implica revisar privacidad y cookies.
- WhatsApp es el canal comercial; un bot de WhatsApp es una integración adicional con presupuesto aparte.
- Comprobar móvil a 320–390 px sin desbordamiento horizontal.
