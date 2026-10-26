# Arquitectura

[Vista del sistema y visor interactivo](../README.es.md#arquitectura).

## Contenido y publicación

Los posts Markdown y los proyectos pertenecen a `portfolio`. La generación durante el build produce JSON editorial, entradas para prerender, RSS, sitemap, `.generated/release-manifest.json` y `.generated/chat/knowledge.json`. Se excluyen borradores y fechas futuras con `America/Argentina/Buenos_Aires`; se limpian detalles generados para evitar publicaciones residuales.

GitHub Actions publica en Firebase ante pushes a main, ejecución manual y una programación diaria a las 09:17 de Argentina. El run diario compara el hash del estado publicado y el commit para omitir un despliegue frontend sin cambios. Las etapas cloud siguen ejecutándose después de desplegar o verificar contenido idéntico en vivo, permitiendo reintentar handoffs fallidos. La programación puede demorarse en GitHub.

El orden es build → Firebase → `process-release` → `publish-chat-knowledge`. Son handoffs de CI, no llamadas del navegador a Lambdas de release. `process-release` invoca `generate-og` y `notify-post`; el publicador independiente escribe el conocimiento editorial canónico en R2. Las tres capas rechazan fechas editoriales inválidas o futuras. Una entrega parcial de correo todavía puede duplicar notificaciones al reintentar.

## Contrato dinámico

El navegador consume una sola API lógica en `https://api.matiasgaleano.dev/api`: `GET /api/health`, `POST /api/contact`, `GET /api/chat/starters`, `POST /api/chat`, `POST /api/subscriptions` y `DELETE /api/subscriptions`. La persistencia de suscripciones pertenece a cloud detrás de su fachada. Contacto usa Resend con validación y controles antispam.

El chat usa hechos profesionales curados locales y conocimiento editorial canónico de R2 para proyectos/posts. Las preguntas exclusivamente profesionales no cargan contenido editorial. Las peticiones editoriales conservan una respuesta de indisponibilidad cuando no existe una fuente válida. Los envelopes validan integridad; caché, TTL y contingencia están documentados en la API. El frontend envía hasta seis turnos previos dentro de los límites del payload; la API no agrega persistencia de conversaciones. Las métricas omiten preguntas, respuestas, historial e identidades.

## Almacenamiento y despliegue

La fuente editorial permanece en Git. Media/artefactos públicos de R2 y `SUBSCRIBERS_BUCKET` privado están separados; se rechazan nombres iguales. Los suscriptores existentes en almacenamiento público requieren la migración documentada de copia verificada, corte y limpieza; no basta cambiar una variable.

La implementación activa es `portfolio-api-cloud`: CDK TypeScript define API Gateway HTTP API, una Lambda ARM64, DynamoDB para cuotas y Secrets Manager para configuración. Cloudflare conserva el hostname público y la entrada verifica su origen. Los despliegues usan Actions, OIDC y changesets revisados. Las FAQ no usan IA; la generación usa GPT-6 Luna con controles compartidos.

`portfolio-api` conserva NestJS/Docker en EC2 detrás de Cloudflare Tunnel y Traefik. Es un espejo funcional de la misma API, no otro servicio en la cadena. La recuperación vuelve el routing al túnel conservado; los seis contratos y los clientes permanecen iguales. Se selecciona una implementación por request, evitando envíos o suscripciones duplicados. La recuperación no revierte escrituras de los proveedores compartidos.

El esquema representa ambas implementaciones en un nodo: **API del portfolio**, CDK/Lambda activa y NestJS/EC2 espejo. Para 1.1.0 se planifica ordenar `src` e integrar Middy, conservando una Lambda, CDK e `infra/` separado del runtime.

Cloud conserva AWS SAM. `PortfolioCloudGitHubDeployRole` pasa el ejecutor dedicado `PortfolioCloudCloudFormationExecutionRole`; seis roles runtime usan `PortfolioCloudRuntimeBoundary`. El deploy de producción valida cuenta, rol y región y admite changesets revisados. El registro del 11 de octubre informa UPDATE_COMPLETE, retiro del gate de migración y de los permisos/trust Allow de `cloud_actions`, conservado para auditoría. Son observaciones fechadas, no una afirmación de estado en vivo.

## Decisiones y costos

El contenido estático reduce dependencias runtime pero exige rebuilds. Separar API/cloud aclara contratos pero requiere releases compatibles. Los suscriptores privados reducen exposición pero necesitan migración controlada. Los reintentos por etapa mejoran recuperación sin deduplicar correos por destinatario. [Evidencia y recuperación](04-evidence.es.md).

[English](02-architecture.md).
