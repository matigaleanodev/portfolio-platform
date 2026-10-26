# Roadmap

## Base entregada

La versión 1.3.0 incorpora diagramas editoriales Archify, publicación programada con guardas de fecha, historial acotado del chat, contexto profesional curado y métricas sin texto de conversaciones. El almacenamiento privado de suscriptores y las herramientas de migración están implementados. El registro operativo fechado informa que terminó el corte SAM OIDC de producción y la retirada del rol legado.

## API cloud y siguiente 1.1.0

La API pública activa es `portfolio-api-cloud` 1.0.0; NestJS/EC2 se conserva como espejo intercambiable y recuperable. Para 1.1.0: reorganizar `src` por dominio, HTTP y runtime; después integrar Middy para declarar las seis operaciones y componer middleware. Mantener CDK, una Lambda, `infra/` separado y los contratos/controles actuales. Powertools queda opcional. Esta evolución está planificada, no implementada.

## Pendientes

Los pendientes de API se trabajan en `portfolio-api-cloud` después de completar las migraciones restantes, sin trabajo previo ni paralelo sobre NestJS/EC2. Las implementaciones originales quedan congeladas.

- Validar la primera publicación programada con página/índice/RSS públicos, resultados cloud y recuperación; configurar el cron no demuestra una ejecución diaria completada.
- Mantener cobertura conjunta de contratos frontend/API/cloud y knowledge; observar frescura, TTL y fallback según la documentación de la API.
- Seguir el resultado de la migración de suscriptores privados por separado del código preparado; conservar copias verificadas y recuperación hasta confirmar el corte.
- Mejorar recuperación de notificaciones sin afirmar idempotencia por destinatario; los envíos parciales pueden duplicar correos.
- Mantener comprobantes de diagramas y documentación bilingüe alineados; continuar mejoras editoriales y UX dentro de los límites actuales.

[English](03-roadmap.md).
