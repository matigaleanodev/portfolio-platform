# Overview

Portfolio has three logical layers across four code repositories:

- `portfolio`: Angular frontend, editorial content and static Firebase hosting.
- **One runtime API**: `portfolio-api-cloud` is the active TypeScript/CDK/Lambda implementation; `portfolio-api` retains the NestJS/EC2 mirror. Both provide the same six health, contact, chat and subscription-facade contracts.
- `portfolio-cloud`: AWS SAM automation, knowledge publication and subscription/notification ownership.

The browser uses `https://api.matiasgaleano.dev/api`. Cloudflare routes that hostname to the active CDK implementation's API Gateway. NestJS remains available for recovery by changing routing, without rewriting clients or duplicating writes.

API cloud 1.0.0 retains one Lambda. Middy and responsibility-based internal organization are planned for 1.1.0; editorial automation remains separate from the public API.

See [architecture](02-architecture.md), [roadmap](03-roadmap.md) and [evidence](04-evidence.md).

[Español](01-overview.es.md).
