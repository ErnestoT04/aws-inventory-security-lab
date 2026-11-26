# Decisiones y aprendizajes

[Volver al índice](../README.md)

- Usé una aplicación pequeña para poder seguir la ruta completa de los datos: formulario, base de datos y almacenamiento de archivos.
- Aprendí que dejar RDS fuera de internet y limitar qué puede leer el rol de la aplicación resuelven problemas distintos. El primero reduce el acceso por red; el segundo limita permisos de AWS.
- La diferencia entre la configuración de S3 y la solicitud del código me enseñó a revisar los metadatos del objeto final, en vez de asumir el resultado desde la configuración del bucket.
- Separé la prueba académica de una versión lista para operar. Antes de un despliegue real habría que revisar, entre otros puntos, el manejo de cuentas de demostración, las pruebas automatizadas y los flujos de respaldo.
