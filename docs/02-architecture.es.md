# Arquitectura

[English](02-architecture.md) · [Diagrama del sistema](../README.es.md#arquitectura)

## Contenido y publicación

`portfolio` convierte los posts Markdown y los proyectos en un sitio estático, rutas prerenderizadas, feeds y artefactos editoriales. GitHub Actions publica el frontend en Firebase Hosting e invoca `process-release` seguido de `publish-chat-knowledge`. La primera función coordina la generación de imágenes OG y las notificaciones a suscriptores. La segunda guarda el conocimiento editorial del chat en Cloudflare R2.

## API dinámica

El navegador llama a la API pública a través de Cloudflare y API Gateway HTTP API. `portfolio-api-cloud` define seis funciones Lambda con CDK. `api` y `chat` atienden HTTP. Las cuatro funciones editoriales se invocan por separado de las solicitudes del navegador. DynamoDB coordina cuotas compartidas, SSM Parameter Store entrega configuración sensible al runtime y Resend envía correos de contacto y notificaciones.

## Almacenamiento y recuperación

R2 guarda artefactos y conocimiento editorial. Los registros de suscriptores viven en un bucket privado independiente. El chat usa FAQ locales y contexto editorial aprobado, con uso del modelo sujeto a controles compartidos.

El mismo contrato HTTP se puede recuperar a través de NestJS/EC2 al dirigir el hostname de la API pública a esa implementación. El workflow editorial puede seleccionar las funciones AWS SAM conservadas de manera independiente. Cada ruta selecciona una implementación por solicitud o invocación.
