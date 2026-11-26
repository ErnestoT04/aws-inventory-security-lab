# Controles y verificación

[Volver al índice](../README.md)

| Control | Evidencia disponible | Qué falta para mostrarlo en el portafolio |
| --- | --- | --- |
| Almacenamiento de archivos y sesiones | El PR #1 muestra la integración con S3 y sesiones en MySQL. | Captura sanitizada de un flujo con un producto ficticio y una sesión verificable. |
| Contraseña fuera del código | El PR #3 muestra la recuperación desde Secrets Manager. En el laboratorio se reportó acceso de la aplicación a RDS tras configurar el secreto. | Resultado redactado de la conexión, sin mostrar la contraseña, el nombre del secreto ni la cadena de conexión. |
| Acceso de red a RDS | Se reportó conexión correcta desde EC2 con acceso configurado por grupo de seguridad. | Registrar también una prueba negativa desde otro recurso de un laboratorio autorizado. No afirmar que ya se ejecutó. |
| Permisos acotados | Se reportó configuración del rol de EC2 para los objetos necesarios. | Comparar por separado una operación permitida y otra no permitida con datos ficticios. |
| Cifrado SSE-KMS en S3 | En la comprobación documentada el 2 de noviembre de 2026, los metadatos de un objeto de prueba devolvieron `aws:kms` y Bucket Key habilitado. También consta una descarga autorizada, registrada por separado. El código público aún fija `AES256` en ambas rutas de carga. | Mostrar evidencia redactada de una carga de producto y de un reporte, con objetos nuevos y versión del código identificada. No extrapolar a objetos previos. |

Este caso no demuestra rotación del secreto, auditoría con CloudTrail, alta disponibilidad, uso en producción ni cifrado de RDS. No deben presentarse como resultados verificados.
