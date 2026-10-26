# Evidence and scope

Documentation update on 2026-10-26. Local code and versioned production records were checked; the inspected revisions exist on GitHub. No deployments or new AWS audit were performed.

## Inspected revisions

- [portfolio @ 3893a5d0ae03](https://github.com/matigaleanodev/portfolio/tree/3893a5d0ae036b152762975e8ae2a91a40d4d693)
- [portfolio-api @ a0ef80fa9f82](https://github.com/matigaleanodev/portfolio-api/tree/a0ef80fa9f82d1cea5a31425a63ab0a344338c56)
- [portfolio-api-cloud @ 17d4af9c40e2](https://github.com/matigaleanodev/portfolio-api-cloud/tree/17d4af9c40e217797122f3bb7c11968959daf720)
- [portfolio-cloud @ 4c0b1735dde0](https://github.com/matigaleanodev/portfolio-cloud/tree/4c0b1735dde0759a9dbef5625aae7788386e9210)

## Implementations of the same API

[Production configuration](https://github.com/matigaleanodev/portfolio-api-cloud/blob/17d4af9c40e217797122f3bb7c11968959daf720/Docs/production.md), the [production record](https://github.com/matigaleanodev/portfolio-api-cloud/blob/17d4af9c40e217797122f3bb7c11968959daf720/Docs/production-rollout.md) and release [v1.0.0](https://github.com/matigaleanodev/portfolio-api-cloud/releases/tag/v1.0.0) document the active Lambda, six compatible contracts, domain cutover and retained NestJS/EC2 implementation.

The diagram uses one API node for the interchangeable implementations, marking CDK/Lambda active. Viewer sources are pinned to `portfolio-api-cloud` at `17d4af9c40e217797122f3bb7c11968959daf720`. `manifest.json` identifies the exact JSON, HTML and PNG and their checks. Local regeneration does not imply publishing the new version on the website.

Regeneration passed all nine Archify showcase checks without errors or warnings and the Chromium check. The PNG preview was visually inspected; that review is separate from the automatic receipt's `visualReview` field.

## Maintenance

Regenerate from `portfolio/content/diagrams` and synchronize specification, HTML, PNG and manifest. Retain one logical API without duplicate traffic or expanded cloud ownership. The roadmap distinguishes pending Middy 1.1.0 work from current architecture.

[Español](04-evidence.es.md).
