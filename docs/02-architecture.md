# Architecture

[Español](02-architecture.es.md) · [System diagram](../README.md#architecture)

## Content and publication

`portfolio` builds Markdown posts and project content into a static site, prerendered routes, feeds and editorial artifacts. GitHub Actions publishes the frontend on Firebase Hosting and invokes `process-release` followed by `publish-chat-knowledge`. The first coordinates OG image generation and subscriber notifications. The second writes editorial chat knowledge to Cloudflare R2.

## Dynamic API

The browser calls the public API through Cloudflare and API Gateway HTTP API. `portfolio-api-cloud` defines six Lambda functions in CDK. The `api` and `chat` functions serve HTTP. The four editorial functions are invoked independently of browser requests. DynamoDB coordinates shared quotas, SSM Parameter Store supplies sensitive runtime configuration, and Resend handles contact and notification email.

## Storage and recovery

R2 stores editorial artifacts and chat knowledge. Subscriber records live in a separate private bucket. Chat uses local FAQs and approved editorial context, with model use subject to shared controls.

The same HTTP contract can be restored through the NestJS/EC2 implementation by routing the public API hostname to that backend. The editorial workflow can independently select the retained AWS SAM functions. Each path selects one implementation per request or invocation.
