# Overview

Portfolio Platform is a three-repository system for a public personal platform. It is shaped around one constraint: most of the product should behave like publishable content, while only a small part should behave like a traditional application.

That leads to a static-first frontend for pages and editorial material, a narrow API for truly runtime features, and a cloud layer that owns the operational work that should not leak into the public site.

## Components

- Public frontend: Angular standalone app with blog, landing pages, content rendering, and dynamic entrypoints.
- Dynamic API: NestJS service for contact, chat, health checks, and public subscription facade flows.
- Cloud automation: AWS Lambda-based services for release tasks, OG generation, subscription lifecycle, and artifact publication.
- Shared artifacts: generated editorial JSON, release manifests, and chat knowledge objects consumed across repos.

## Why The Split Matters

The frontend is optimized for publishing and presentation.
The API is optimized for interaction boundaries.
The cloud layer is optimized for ownership of asynchronous and operational workflows.

This split is less about scale than about discipline: keeping each repository small enough to defend its purpose.

## Data Model

The platform uses a mixed data model:

- Editorial content is versioned in the frontend repository as Markdown and transformed into static artifacts during build time.
- Runtime interaction data includes contact submissions, chat requests, and subscription events.
- Cloud-owned operational data includes subscriber records, release metadata, and published knowledge artifacts.

There is no central public content database in the current architecture.
