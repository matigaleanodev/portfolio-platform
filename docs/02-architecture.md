# Architecture

[System overview and interactive viewer](../README.md#architecture).

## Content and publication

Markdown posts and project data belong to `portfolio`. Build-time content generation produces editorial JSON, prerender inputs, RSS, sitemap, `.generated/release-manifest.json` and `.generated/chat/knowledge.json`. Drafts and future dates are excluded using `America/Argentina/Buenos_Aires`; generated detail files are cleared to prevent stale publication.

GitHub Actions publishes Firebase on main pushes, manual runs and a daily schedule at 09:17 Argentina. The daily run compares the live publication-state hash and source commit to skip an unchanged frontend deployment. Cloud stages still run after successful deployment or verification of matching live content, allowing failed handoffs to retry. Scheduling is subject to GitHub delays.

The order is build → Firebase → `process-release` → `publish-chat-knowledge`. These are CI handoffs, not browser calls to release Lambdas. `process-release` invokes `generate-og` and `notify-post`; the independent publisher writes canonical editorial knowledge to R2. All three layers reject invalid/future editorial dates. Partial recipient delivery can still cause duplicate notification emails on retry.

## Dynamic contract

The browser calls one logical API at `https://api.matiasgaleano.dev/api`: `GET /api/health`, `POST /api/contact`, `GET /api/chat/starters`, `POST /api/chat`, `POST /api/subscriptions` and `DELETE /api/subscriptions`. Subscription persistence belongs to cloud behind its facade. Contact uses Resend with validation and anti-spam controls.

Chat uses curated professional facts locally and canonical editorial knowledge from R2 for projects/posts. Exclusively professional questions bypass editorial loading. Editorial requests retain an unavailable response when no valid source exists. Knowledge envelopes validate content integrity; cache/TTL and contingency behavior are documented in the API. The frontend sends at most six prior turns within payload limits; the API adds no persistent conversation store. Operational metrics omit questions, answers, history and identities.

## Storage and deployment

Editorial source stays in Git. Public R2 media/artifacts and private `SUBSCRIBERS_BUCKET` are distinct; equal bucket names are rejected. Existing public subscriber records require the documented verified-copy/cutover/cleanup migration, not just an environment change.

The active implementation is `portfolio-api-cloud`: TypeScript CDK defines API Gateway HTTP API, one ARM64 Lambda, DynamoDB for quotas and Secrets Manager for configuration. Cloudflare preserves the public hostname and ingress verifies its origin. Deployments use Actions, OIDC and reviewed change sets. FAQs do not use AI; generation uses GPT-6 Luna with shared controls.

`portfolio-api` retains NestJS/Docker on EC2 behind Cloudflare Tunnel and Traefik. It is a functional mirror of the same API, not another service in the chain. Recovery routes back to the retained tunnel; all six contracts and clients remain unchanged. Each request selects one implementation, avoiding duplicate emails or subscriptions. Recovery does not undo shared-provider writes.

The diagram represents both implementations with one node: **Portfolio API**, marking CDK/Lambda active and NestJS/EC2 its mirror. Version 1.1.0 will organize `src` and introduce Middy, retaining one Lambda, CDK and `infra/` separate from the runtime.

Cloud remains AWS SAM. `PortfolioCloudGitHubDeployRole` passes the dedicated `PortfolioCloudCloudFormationExecutionRole`; six runtime roles use `PortfolioCloudRuntimeBoundary`. Production deployment validates account/role/region and supports reviewed changesets. The October 11 record reports UPDATE_COMPLETE, removal of the migration gate and retirement of `cloud_actions` permissions/trust Allow while retaining the role for audit. These are dated observations, not a live-state assertion.

## Decisions and tradeoffs

Static content reduces runtime dependencies but needs rebuilds. Separate API/cloud ownership keeps contracts explicit but requires compatible releases. Private subscriber storage reduces exposure but needs a controlled migration. Retryable release stages improve recovery but do not provide per-recipient email deduplication. [Evidence and recovery references](04-evidence.md).

[Español](02-architecture.es.md).
