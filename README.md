# Acelerik Booking — web del producto

Landing de [Acelerik Booking](https://booking.acelerik.com), el sistema de reservas de cumpleaños para parques infantiles de [Acelerik](https://www.acelerik.com).

```bash
npm ci
npm run dev
npm run build
```

Despliegue en Cloudflare Workers (Workers Builds desde GitHub): build `npm run build`, deploy `npx wrangler deploy` (configuración en `wrangler.jsonc`).
