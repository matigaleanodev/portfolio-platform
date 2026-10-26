# Roadmap

## Delivered baseline

Version 1.3.0 includes editorial Archify diagrams, scheduled publication with date guards, bounded chat history, curated professional context and text-free operational metrics. Private subscriber storage and migration tooling are implemented. The dated operations record reports the SAM OIDC production cutover and legacy-role retirement completed.

## API cloud and next 1.1.0

The active public API is `portfolio-api-cloud` 1.0.0; NestJS/EC2 remains an interchangeable recovery mirror. For 1.1.0: organize `src` by domain, HTTP and runtime, then introduce Middy to declare the six operations and compose middleware. Retain CDK, one Lambda, separate `infra/` and current contracts/controls. Powertools remains optional. This evolution is planned, not implemented.

## Remaining work

API backlog is handled in `portfolio-api-cloud` after the remaining migrations are complete, never before or in parallel on NestJS/EC2. Original implementations stay frozen.

- Validate the first scheduled publication through public page/index/RSS, cloud results and recovery behavior; configured scheduling is not proof of a completed daily run.
- Keep API/cloud/frontend release and knowledge contracts covered together; monitor knowledge freshness, cache TTL and fallback behavior using the existing API documentation.
- Track the private-subscriber migration outcome separately from code readiness; preserve verified copies and recovery until cutover is confirmed.
- Improve notification recovery without claiming per-recipient idempotency; partial sends can still duplicate emails.
- Keep diagram receipts and bilingual docs aligned with source updates; continue UX/editorial refinement within existing boundaries.

[Español](03-roadmap.es.md).
