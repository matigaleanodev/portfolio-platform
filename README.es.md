# Portfolio Platform

[🇬🇧 English](README.md) | [🇪🇸 Español](README.es.md)

Portfolio Platform documenta cómo funciona el portfolio como sistema de producto, no solo como sitio web: contenido editorial estático, una API runtime deliberadamente acotada y workflows cloud que automatizan releases y operaciones de suscriptores.

![Angular](https://img.shields.io/badge/Angular-Standalone-DD0031?style=flat-square&logo=angular&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-API-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Cloud-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Serverless](https://img.shields.io/badge/Serverless-Automation-FD5750?style=flat-square&logo=serverless&logoColor=white)
![OpenAI API](https://img.shields.io/badge/OpenAI-API-412991?style=flat-square&logo=openai&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)

## Repositorios de Código

- [`portfolio`](https://github.com/matigaleanodev/portfolio) -> frontend Angular standalone y blog
- [`portfolio-api`](https://github.com/matigaleanodev/portfolio-api) -> API NestJS para contacto, chat y fachada de suscripciones
- [`portfolio-cloud`](https://github.com/matigaleanodev/portfolio-cloud) -> servicios serverless en AWS para automatizacion de releases y ownership de suscripciones

## Por Qué Existe Este Repo

Este repositorio existe para mostrar el límite del sistema entre contenido, comportamiento runtime y automatización cloud.

Si abrís los repos de código por separado, cada uno se entiende. Lo que agrega este repo es la razón de más alto nivel: por qué el sitio es static-first, por qué la API se mantiene intencionalmente pequeña y por qué los workflows de release y suscripciones viven fuera del frontend.

## Foco Actual

- mantener el contenido editorial versionado en el repo frontend
- mantener el backend runtime chico y explícito
- hacer que la automatización cloud sea dueña de los workflows de releases y suscriptores
- documentar los contratos entre repos con suficiente claridad para poder evolucionarlos sin romperlos

## Arquitectura

```mermaid
flowchart LR
  User --> Frontend[portfolio]
  Frontend --> API[portfolio-api]
  Frontend --> Cloud[portfolio-cloud]
  API --> Cloud
  Cloud --> R2[Cloud Storage / Artifacts]
```

## Docs

- [Overview](docs/01-overview.md)
- [Architecture](docs/02-architecture.md)
- [Roadmap](docs/03-roadmap.md)
