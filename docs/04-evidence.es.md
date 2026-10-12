# Evidencia y alcance

Revisión documental del 12/10/2026. Se contrastaron código/documentación local y SHA de main consultados en GitHub. Los commits locales de controles de identidad se cotejaron con workflows actuales de main. Esta tarea no accedió a AWS, ejecutó despliegues ni validó flujos de usuarios en producción.

## Revisiones de main

- [portfolio @ 34856adee211](https://github.com/matigaleanodev/portfolio/tree/34856adee211f57ddb32a8573b9af9578d73235b)
- [portfolio-api @ 7d535b571380](https://github.com/matigaleanodev/portfolio-api/tree/7d535b5713807a28081523c573445320bf1ad42e)
- [portfolio-cloud @ bdc1510dbc8d](https://github.com/matigaleanodev/portfolio-cloud/tree/bdc1510dbc8dca8765a69d278f65aa3ce6e7902b)

## Fuentes

- [portfolio/Docs/scheduled-publication.es.md](https://github.com/matigaleanodev/portfolio/blob/34856adee211f57ddb32a8573b9af9578d73235b/Docs/scheduled-publication.es.md)
- [portfolio/Docs/architecture-diagrams.es.md](https://github.com/matigaleanodev/portfolio/blob/34856adee211f57ddb32a8573b9af9578d73235b/Docs/architecture-diagrams.es.md)
- [portfolio-api/docs/assistant-profile-audit.es.md](https://github.com/matigaleanodev/portfolio-api/blob/7d535b5713807a28081523c573445320bf1ad42e/docs/assistant-profile-audit.es.md)
- [portfolio-api/docs/chat-audit.es.md](https://github.com/matigaleanodev/portfolio-api/blob/7d535b5713807a28081523c573445320bf1ad42e/docs/chat-audit.es.md)
- [portfolio-cloud/Docs/architecture.es.md](https://github.com/matigaleanodev/portfolio-cloud/blob/bdc1510dbc8dca8765a69d278f65aa3ce6e7902b/Docs/architecture.es.md)
- [portfolio-cloud/Docs/subscriber-migration.es.md](https://github.com/matigaleanodev/portfolio-cloud/blob/bdc1510dbc8dca8765a69d278f65aa3ce6e7902b/Docs/subscriber-migration.es.md)
- [portfolio-cloud/.github/workflows/deploy.yml](https://github.com/matigaleanodev/portfolio-cloud/blob/bdc1510dbc8dca8765a69d278f65aa3ce6e7902b/.github/workflows/deploy.yml)
- [Workspace: AWS 2026-10-11](https://github.com/matigaleanodev/workspace/blob/2d808eb/Docs/operations/aws-access-2026-10-11.es.md)
- [Workspace: architecture](https://github.com/matigaleanodev/workspace/blob/2d808eb/Docs/architecture.es.md)

## Límites y mantenimiento

Los reportes operativos del workspace son evidencia histórica fechada; no certifican el estado vivo actual. Los diagramas conservan las revisiones originales en manifest.json, anteriores a esta revisión de documentación. Se verificaron hashes de JSON/HTML/PNG, enlaces locales y ausencia de Mermaid; se inspeccionaron visualmente ambas vistas previas. No se regeneraron diagramas ni se repitieron pruebas de las aplicaciones.

[English](04-evidence.md).
