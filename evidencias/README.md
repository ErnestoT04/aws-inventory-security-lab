# Evidencias y plantilla

[Volver al índice](../README.md)

## V-01 · Cifrado de un objeto de prueba en S3

**Fecha:** 2 de noviembre de 2026. **Origen:** resultado registrado por Ernesto en su laboratorio académico; transcripción saneada, no una ejecución nueva ni una salida completa del proveedor.

```text
Modo de cifrado del objeto: aws:kms
S3 Bucket Key: habilitada
```

En un paso separado quedó registrada una descarga autorizada. Este resultado no corresponde a las dos rutas de la aplicación. La versión exacta del código del despliegue no queda acreditada por esta evidencia; no se infiere de ella cifrado de RDS, uso de KMS en todos los objetos ni rotación del secreto.

Las [contribuciones públicas del README](../README.md#español) muestran cambios de código del equipo. Para declarar una prueba adicional como verificada, conserva solo el resultado mínimo y omite credenciales, IDs de cuenta, ARN, IP, endpoints, nombres reales y salidas completas. No se incluyen capturas de consola ni volcados.

Plantilla para cada evidencia:

```text
Evidencia: V-__
Fecha: AAAA-MM-DD
Versión de la aplicación: [commit público o etiqueta del laboratorio]
Control evaluado: [por ejemplo, cifrado de un reporte recién creado]
Datos de prueba: [nombre ficticio sin referencias al entorno]
Resultado esperado: [modo de cifrado, operación permitida/denegada o conexión]
Resultado observado: [anotar solo lo observado, sin identificadores]
Estado: [verificado / pendiente / discrepancia]
Adjunto: [opcional; archivo sanitizado]
```
