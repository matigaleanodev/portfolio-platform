# Architecture sources and boundaries

[Español](04-evidence.es.md).

## Technical sources

- [portfolio](https://github.com/matigaleanodev/portfolio)
- [portfolio-api-cloud](https://github.com/matigaleanodev/portfolio-api-cloud)
- [portfolio-api](https://github.com/matigaleanodev/portfolio-api)
- [portfolio-cloud](https://github.com/matigaleanodev/portfolio-cloud)

## Reading and maintenance

The API is one logical component with compatible implementations; the frontend owns static content and the cloud layer automates publishing/subscriptions. Check effective configuration before claiming which implementation receives traffic.

Diagrams describe boundaries and relationships; they do not certify deployments or production tests. Keep sources, HTML, PNG and manifest synchronized using the tools described in diagrams/README. Technical documentation describes the existing system.
