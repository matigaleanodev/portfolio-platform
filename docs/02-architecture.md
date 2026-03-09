# Architecture

The platform follows a split architecture:

- `portfolio` serves the public UI, blog rendering, prerendered routes, and generated content artifacts.
- `portfolio-api` handles dynamic requests that cannot be solved statically, mainly contact, chat, health, and subscription facade endpoints.
- `portfolio-cloud` runs event-driven workflows such as release processing, OG image generation, subscriber persistence, and chat knowledge publication.

The architectural direction is static-first. Runtime APIs exist only where interactivity or external integrations require them.

## Infrastructure

The platform spans two delivery modes:

- static hosting for the frontend output
- containerized deployment for the NestJS API
- AWS serverless infrastructure for automation and asynchronous workflows

The cloud layer is infrastructure-as-code driven and remains independent from the frontend deployment lifecycle, even when both participate in the same release process.

## Decisions

- Keep portfolio content static and build-time instead of serving it through a public runtime API.
- Limit `portfolio-api` to dynamic features only, avoiding growth into a generic content backend.
- Make `portfolio-cloud` the owner of subscriptions and release-oriented automation.
- Publish canonical chat knowledge from the cloud layer so runtime consumers use a single artifact source.

## Tradeoffs

- Static content improves simplicity, SEO, and runtime cost, but requires rebuilds for editorial changes.
- A narrow API reduces backend complexity, but pushes stronger discipline on scope boundaries.
- A separate cloud automation layer improves ownership and deployment clarity, but adds cross-repository coordination.
- Canonical artifact publication reduces duplication, but creates dependency on release quality and artifact integrity.
