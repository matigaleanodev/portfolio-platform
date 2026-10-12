# Overview

Portfolio Platform documents three independently maintained repositories. It adds no runtime service.

- `portfolio` (v1.3.0): Angular 21 standalone frontend, prerendered pages, blog and projects built from versioned Markdown/JSON; static hosting on Firebase.
- `portfolio-api` (v1.3.0): NestJS 11 API for contact, chat, health and the subscription facade. It does not serve editorial content.
- `portfolio-cloud` (v1.3.0): TypeScript and AWS SAM; six Lambdas own release processing, OG generation, notifications, subscriptions and canonical editorial knowledge publication.

## Recent changes

The frontend now includes validated Archify viewers and previews, scheduled editorial publication and bounded chat history. API chat separates local professional facts from cloud editorial context and emits operational metrics without conversation text. Cloud guards publication dates and separates private subscriber records from public media/artifacts.

The SAM pipeline moved to dedicated GitHub OIDC and CloudFormation execution identities with six runtime permissions boundaries. The dated operations record reports the production cutover completed on October 11; this documentation update does not perform a fresh AWS audit.

See [architecture](02-architecture.md), [remaining work](03-roadmap.md) and [evidence](04-evidence.md).

[Español](01-overview.es.md).
