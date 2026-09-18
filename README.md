# token-argus-updates

Canal de actualizaciones de **Token Argus**, la aplicación de bandeja que vigila
el consumo de GitHub Copilot.

Este repositorio existe por un motivo concreto: el proyecto vive en un
repositorio privado, y la API de releases de GitHub exige autenticación para
leer un repo privado. La aplicación no tiene ningún token con permisos de repo,
así que no puede consultarla.

La solución es este manifiesto público, que contiene **únicamente** un número de
versión y un enlace:

```json
{
  "version": "1.0.2",
  "url": "https://github.com/MiguelAlberola/token-argus/releases/latest",
  "notes": "Descripción corta del cambio."
}
```

La aplicación lo lee sin autenticación desde `raw.githubusercontent.com` y, si
la versión publicada es mayor que la instalada, avisa con una notificación. La
descarga sigue siendo manual y contra el repositorio privado, así que el acceso
al binario no cambia.

Aquí no hay código, ni binarios, ni nada relativo a la infraestructura interna.

## Publicar una versión nueva

Actualiza `latest.json` con la versión y un resumen de una línea, y haz push. Los
clientes lo comprueban al arrancar y cada seis horas, así que el aviso puede
tardar un rato en llegar a quien ya lo tenga abierto.
