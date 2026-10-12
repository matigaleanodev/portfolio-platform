# Resumen

Portfolio Platform documenta tres repositorios mantenidos de forma independiente. No agrega un servicio runtime.

- `portfolio` (v1.3.0): frontend Angular 21 standalone, páginas prerenderizadas, blog y proyectos generados desde Markdown/JSON versionados; hosting estático en Firebase.
- `portfolio-api` (v1.3.0): API NestJS 11 para contacto, chat, salud y fachada de suscripciones. No sirve contenido editorial.
- `portfolio-cloud` (v1.3.0): TypeScript y AWS SAM; seis Lambdas administran releases, OG, notificaciones, suscripciones y publicación canónica del conocimiento editorial.

## Cambios recientes

El frontend incorpora visores y vistas previas Archify validados, publicación editorial programada e historial acotado del chat. El chat de la API separa hechos profesionales locales del contexto editorial cloud y emite métricas operativas sin texto de conversaciones. Cloud valida fechas de publicación y separa suscriptores privados de media y artefactos públicos.

El pipeline SAM migró a identidades dedicadas de GitHub OIDC y ejecución CloudFormation con seis permissions boundaries de runtime. El registro operativo fechado informa que el corte de producción terminó el 11 de octubre; esta actualización documental no realiza una nueva auditoría AWS.

Ver [arquitectura](02-architecture.es.md), [pendientes](03-roadmap.es.md) y [evidencia](04-evidence.es.md).

[English](01-overview.md).
