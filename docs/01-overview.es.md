# Resumen

Portfolio tiene tres capas lógicas y cuatro repositorios de código:

- `portfolio`: frontend Angular, contenido editorial y hosting estático en Firebase.
- **API runtime única**: `portfolio-api-cloud` es la implementación activa TypeScript/CDK/Lambda; `portfolio-api` conserva el espejo NestJS/EC2. Ofrecen los mismos seis contratos de salud, contacto, chat y fachada de suscripciones.
- `portfolio-cloud`: automatización AWS SAM, publicación de knowledge y ownership de suscripciones/notificaciones.

El navegador consume `https://api.matiasgaleano.dev/api`. Cloudflare dirige ese hostname a API Gateway de la implementación CDK activa. NestJS permanece disponible para recuperación mediante el cambio de routing, sin reescribir clientes ni duplicar escrituras.

API cloud 1.0.0 mantiene una Lambda. Middy y la organización interna por responsabilidad quedan para 1.1.0; la automatización editorial sigue separada de la API pública.

Ver [arquitectura](02-architecture.es.md) y [evidencia](04-evidence.es.md).

[English](01-overview.md).
