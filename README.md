# Inventario en AWS | AWS Inventory Security Lab

[Español](#español) · [English](#english)

Caso de estudio académico de infraestructura y seguridad. Este repositorio documenta el laboratorio y enlaza al proyecto original del equipo; no redistribuye su código, datos ni acceso al entorno.

## Español

Soy Ernesto Mendoza. En este proyecto académico en equipo trabajé sobre una aplicación PHP/MySQL de inventario y la usé para practicar infraestructura y seguridad en AWS. El laboratorio describe EC2, RDS, un bucket privado de S3, un rol IAM de ejecución, Secrets Manager y cifrado SSE-KMS. No es un servicio en producción.

**Mis aportes verificables:** [integración de S3, sesiones en MySQL y configuración por entorno (PR #1)](https://github.com/LuisS-byte/inventario-camisas/pull/1), [reporte de inventario y mejoras de interfaz (PR #2)](https://github.com/LuisS-byte/inventario-camisas/pull/2) y [lectura de la contraseña de RDS desde Secrets Manager (PR #3)](https://github.com/LuisS-byte/inventario-camisas/pull/3).

**Límite de lo demostrado:** el código público aún solicita `AES256` al cargar productos y reportes. El 2 de noviembre de 2026, los metadatos de **un objeto de prueba** en el laboratorio posterior mostraron `aws:kms` y S3 Bucket Key habilitada. [Resultado saneado](evidencias/README.md). Esto no verifica las dos rutas de carga de la aplicación.

| Documento | Contenido |
| --- | --- |
| [Arquitectura](docs/arquitectura.md) | Diagrama Mermaid, red, identidad y flujo de datos. |
| [Implementación](docs/implementacion.md) | Secuencia de reconstrucción para un entorno autorizado. |
| [Controles y verificación](docs/verificacion.md) | Código verificable, resultado saneado del laboratorio y pruebas pendientes. |
| [Decisiones](docs/decisiones.md) | Alcance, decisiones de diseño y aprendizajes. |
| [Costos y cierre del laboratorio](docs/costos-y-limpieza.md) | Ejemplo fechado, supuestos, fuentes de AWS y lista de recursos residuales. |
| [Evidencias](evidencias/README.md) | Resultado saneado de un objeto de prueba. No incluye capturas de consola. |

## English

I'm Ernesto Mendoza. In this academic team project, I used a PHP/MySQL inventory app to practice cloud infrastructure and security. The lab covers EC2, RDS, a private S3 bucket, an IAM instance role, Secrets Manager, and SSE-KMS encryption. It is not a production service.

**Verified contributions:** [S3 integration, MySQL-backed sessions, and environment-based configuration (PR #1)](https://github.com/LuisS-byte/inventario-camisas/pull/1), [inventory reporting and UI improvements (PR #2)](https://github.com/LuisS-byte/inventario-camisas/pull/2), and [retrieval of the RDS database password from Secrets Manager (PR #3)](https://github.com/LuisS-byte/inventario-camisas/pull/3).

**Evidence boundary:** the public code still requests `AES256` on product and report uploads. On November 2, 2026, metadata for **one test object** in the later lab showed `aws:kms` and an enabled S3 Bucket Key. See the [sanitized result](evidencias/README.md). This does not verify both application upload paths.

The supporting documents are in Spanish: [architecture](docs/arquitectura.md), [implementation](docs/implementacion.md), [verification](docs/verificacion.md), [design decisions](docs/decisiones.md), [costs and cleanup](docs/costos-y-limpieza.md), and [sanitized evidence](evidencias/README.md).
