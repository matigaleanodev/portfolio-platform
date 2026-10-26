# Evidencia y alcance

Actualización documental del 26/10/2026. Se contrastaron código local y documentos productivos versionados; las revisiones inspeccionadas existen en GitHub. No se ejecutaron despliegues ni una auditoría nueva de AWS.

## Revisiones inspeccionadas

- [portfolio @ 3893a5d0ae03](https://github.com/matigaleanodev/portfolio/tree/3893a5d0ae036b152762975e8ae2a91a40d4d693)
- [portfolio-api @ a0ef80fa9f82](https://github.com/matigaleanodev/portfolio-api/tree/a0ef80fa9f82d1cea5a31425a63ab0a344338c56)
- [portfolio-api-cloud @ 17d4af9c40e2](https://github.com/matigaleanodev/portfolio-api-cloud/tree/17d4af9c40e217797122f3bb7c11968959daf720)
- [portfolio-cloud @ 4c0b1735dde0](https://github.com/matigaleanodev/portfolio-cloud/tree/4c0b1735dde0759a9dbef5625aae7788386e9210)

## Implementaciones de la misma API

La [configuración productiva](https://github.com/matigaleanodev/portfolio-api-cloud/blob/17d4af9c40e217797122f3bb7c11968959daf720/Docs/production.es.md), el [registro de producción](https://github.com/matigaleanodev/portfolio-api-cloud/blob/17d4af9c40e217797122f3bb7c11968959daf720/Docs/production-rollout.es.md) y la release [v1.0.0](https://github.com/matigaleanodev/portfolio-api-cloud/releases/tag/v1.0.0) documentan Lambda activa, seis contratos compatibles, corte del dominio y conservación de NestJS/EC2.

El esquema usa un nodo de API para las implementaciones intercambiables, con CDK/Lambda activa. Las fuentes del visor están fijadas a `portfolio-api-cloud` en `17d4af9c40e217797122f3bb7c11968959daf720`. `manifest.json` identifica JSON, HTML y PNG exactos y sus controles. Regenerar localmente no implica publicar la versión nueva en el sitio.

La regeneración pasó los nueve controles showcase de Archify sin errores ni advertencias y la comprobación en Chromium. La vista previa PNG fue inspeccionada visualmente; esa revisión es distinta del campo `visualReview` del recibo automático.

## Mantenimiento

Regenerar desde `portfolio/content/diagrams` y sincronizar especificación, HTML, PNG y manifest. Mantener una API lógica sin tráfico duplicado ni ampliar el ownership de cloud. El roadmap distingue Middy 1.1.0 pendiente de la arquitectura actual.

[English](04-evidence.md).
