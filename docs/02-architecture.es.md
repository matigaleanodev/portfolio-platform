# Arquitectura

[Vista del sistema y visor interactivo](../README.es.md#arquitectura).

## Contenido y publicación

Los posts Markdown y los proyectos pertenecen a `portfolio`. La generación durante el build produce JSON editorial, entradas para prerender, RSS, sitemap, `.generated/release-manifest.json` y `.generated/chat/knowledge.json`. Se excluyen borradores y fechas futuras con `America/Argentina/Buenos_Aires`; se limpian detalles generados para evitar publicaciones residuales.

GitHub Actions publica en Firebase ante pushes a main, ejecución manual y una programación diaria a las 09:17 de Argentina. El run diario compara el hash del estado publicado y el commit para omitir un despliegue frontend sin cambios. Las etapas cloud siguen ejecutándose después de desplegar o verificar contenido idéntico en vivo, permitiendo reintentar handoffs fallidos. La programación puede demorarse en GitHub.

El orden es build → Firebase → `process-release` → `publish-chat-knowledge`. Son handoffs de CI, no llamadas del navegador a Lambdas de release. `process-release` invoca `generate-og` y `notify-post`; el publicador independiente escribe el conocimiento editorial canónico en R2. Las tres capas rechazan fechas editoriales inválidas o futuras. Una entrega parcial de correo todavía puede duplicar notificaciones al reintentar.

## Contrato dinámico

El navegador consume `portfolio-api`: `GET /api/health`, `POST /api/contact`, `GET /api/chat/starters`, `POST /api/chat`, `POST /api/subscriptions` y `DELETE /api/subscriptions`. La persistencia de suscripciones pertenece a cloud detrás de su fachada. Contacto usa Resend con validación y controles antispam.

El chat usa hechos profesionales curados locales y conocimiento editorial canónico de R2 para proyectos/posts. Las preguntas exclusivamente profesionales no cargan contenido editorial. Las peticiones editoriales conservan una respuesta de indisponibilidad cuando no existe una fuente válida. Los envelopes validan integridad; caché, TTL y contingencia están documentados en la API. El frontend envía hasta seis turnos previos dentro de los límites del payload; la API no agrega persistencia de conversaciones. Las métricas omiten preguntas, respuestas, historial e identidades.

## Almacenamiento y despliegue

La fuente editorial permanece en Git. Media/artefactos públicos de R2 y `SUBSCRIBERS_BUCKET` privado están separados; se rechazan nombres iguales. Los suscriptores existentes en almacenamiento público requieren la migración documentada de copia verificada, corte y limpieza; no basta cambiar una variable.

La API corre en Docker sobre EC2 compartido detrás de Cloudflare Tunnel y un entrypoint Traefik sin publicación en el host. GitHub genera imágenes GHCR por SHA y despliega con OIDC, SSM y un script permitido que comprueba salud. SSH es una vía de recuperación, no el contrato de despliegue CI.

Cloud conserva AWS SAM. `PortfolioCloudGitHubDeployRole` pasa el ejecutor dedicado `PortfolioCloudCloudFormationExecutionRole`; seis roles runtime usan `PortfolioCloudRuntimeBoundary`. El deploy de producción valida cuenta, rol y región y admite changesets revisados. El registro del 11 de octubre informa UPDATE_COMPLETE, retiro del gate de migración y de los permisos/trust Allow de `cloud_actions`, conservado para auditoría. Son observaciones fechadas, no una afirmación de estado en vivo.

## Decisiones y costos

El contenido estático reduce dependencias runtime pero exige rebuilds. Separar API/cloud aclara contratos pero requiere releases compatibles. Los suscriptores privados reducen exposición pero necesitan migración controlada. Los reintentos por etapa mejoran recuperación sin deduplicar correos por destinatario. [Evidencia y recuperación](04-evidence.es.md).

[English](02-architecture.md).
