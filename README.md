# Portfolio Platform

[🇬🇧 English](README.md) | [🇪🇸 Español](README.es.md)

Portfolio Platform documents how the portfolio works as a product system, not just as a website: static editorial content, a deliberately narrow runtime API, and cloud workflows that automate release and subscriber operations.

![Angular](https://img.shields.io/badge/Angular-Standalone-DD0031?style=flat-square&logo=angular&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-API-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Cloud-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Serverless](https://img.shields.io/badge/Serverless-Automation-FD5750?style=flat-square&logo=serverless&logoColor=white)
![OpenAI API](https://img.shields.io/badge/OpenAI-API-412991?style=flat-square&logo=openai&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)

## Code Repositories

- [`portfolio`](https://github.com/matigaleanodev/portfolio) -> Angular standalone frontend and blog
- [`portfolio-api-cloud`](https://github.com/matigaleanodev/portfolio-api-cloud) -> active CDK/Lambda implementation
- [`portfolio-api`](https://github.com/matigaleanodev/portfolio-api) -> interchangeable NestJS/EC2 recovery mirror
- [`portfolio-cloud`](https://github.com/matigaleanodev/portfolio-cloud) -> AWS serverless services for release automation and subscription ownership

The public API is one logical component with two implementations sharing the same six contracts. **CDK/Lambda is active** at `api.matiasgaleano.dev`; NestJS/EC2 remains its recovery mirror. The diagram represents that single component, without duplicate traffic.

## Why This Repo Exists

This repository exists to show the system boundary between content, runtime behavior, and cloud-owned automation.

If you open the code repositories independently, each one is understandable. What this repo adds is the higher-level rationale: why the site is static-first, why the API stays intentionally small, and why release and subscription workflows live outside the frontend.

## Current Focus

- keep editorial content versioned in the frontend repository
- keep runtime backend scope narrow and explicit
- make cloud automation the owner of release and subscriber workflows
- document the contracts between repositories clearly enough to evolve them safely

## Architecture

[![Architecture / Arquitectura](diagrams/rendered/portfolio-ecosystem.543aa6e04718.png)](diagrams/rendered/portfolio-ecosystem.html)

## Docs

- [Overview](docs/01-overview.md)
- [Architecture](docs/02-architecture.md)
- [Roadmap](docs/03-roadmap.md)

[Sources and maintenance](diagrams/README.md) · [Evidence](docs/04-evidence.md)
