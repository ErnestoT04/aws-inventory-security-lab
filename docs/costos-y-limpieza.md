# Costos y cierre del laboratorio

[Volver al índice](../README.md)

## Ejemplo de presupuesto mensual

**Consulta de fuentes: 25 de noviembre de 2026. Moneda: USD.** Ejemplo hipotético en **US East (N. Virginia), `us-east-1`**, elegido para que las referencias regionales coincidan. No representa la región original del laboratorio, un cargo observado ni una cotización. Mes estimado de 730 horas; una instancia Linux EC2, una base RDS MySQL Single-AZ, almacenamiento básico y poco tráfico. Sin créditos, promociones ni impuestos. La hora de RDS requiere cotización actual.

| Rubro | Supuesto y fórmula | USD/mes |
| --- | --- | ---: |
| [EC2 T3 Linux](https://aws.amazon.com/ec2/instance-types/t3/) | 1 `t3.micro` × 730 h × 0.0104 USD/h | 7.592 |
| [EBS gp3](https://docs.aws.amazon.com/en_en/emr/latest/ManagementGuide/emr-plan-storage-compare-volume-types.html) | 10 GiB × 0.08 USD/GiB-mes, sin rendimiento extra aprovisionado | 0.800 |
| [IPv4 pública de la aplicación](https://aws.amazon.com/vpc/pricing/) | 1 IPv4 × 730 h × 0.005 USD/h; excluir si el diseño no la usa | 3.650 |
| [RDS MySQL, almacenamiento](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithReservedDBInstances.html) | 20 GiB gp2 × 0.115 USD/GiB-mes como referencia regional | 2.300 |
| [S3 Standard](https://docs.aws.amazon.com/solutions/latest/automated-security-response-on-aws/cost.html) | 1 GB × 0.023, 1,000 PUT/COPY/POST/LIST × 0.005 por mil, 1,000 GET × 0.0004 por mil | 0.0284 |
| [Secrets Manager](https://aws.amazon.com/secrets-manager/pricing/) | 1 secreto × 0.40 USD/mes + 1,000 llamadas × 0.05 USD por 10,000 | 0.405 |
| [KMS](https://aws.amazon.com/kms/pricing/) | 1 clave administrada por el cliente × 1 USD/mes + 1,000 solicitudes simétricas al precio de 0.03 por 10,000, antes de la franquicia aplicable de KMS | 1.003 |
| **Subtotal sin horas de RDS** | Suma de los rubros anteriores, incluidos 20 GiB de RDS | **15.7784** |

**Fórmula total:** 15.7784 USD + 730 × tarifa horaria vigente de RDS. Por ejemplo, **si** la calculadora devolviera 0.020 USD/h, el cómputo RDS sería 14.60 USD y el total, **30.38 USD/mes** (o **26.73 USD/mes** sin IPv4 pública). El importe horario se eligió solo para mostrar la fórmula: no es una tarifa consultada ni una previsión de cargos. Para un presupuesto real, introduce clase, región, motor y almacenamiento en [AWS Pricing Calculator](https://calculator.aws/) y consulta [los cargos de RDS MySQL](https://aws.amazon.com/rds/mysql/pricing/).

No se incluyen ALB, NAT Gateway, EFS, endpoints de VPC, transferencia de datos, respaldo adicional, retención de registros, soporte ampliado de MySQL, rotación ni cargos por créditos de CPU. Añadir únicamente las partidas que utilice el diseño. El escenario contiene una IPv4 por simplicidad del cálculo, no como requisito para exponer el laboratorio a internet. La franquicia de solicitudes KMS depende del uso agregado de la cuenta, así que el ejemplo no la descuenta. Antes de iniciar, usar un presupuesto y confirmar qué recursos permanecen facturables si se detienen; una alerta no sustituye el cierre del laboratorio.

## Lista de cierre

Aplicar solo sobre recursos propios del laboratorio y con autorización. Conservar primero la evidencia sanitizada y acordar qué datos o respaldos deben mantenerse.

1. Quitar acceso de usuarios de prueba y detener la aplicación. Verificar que no haya dependencias externas.
2. Revisar EC2, volúmenes, snapshots y direcciones públicas o elásticas; confirmar qué recursos son exclusivos de esta práctica antes de retirarlos.
3. Revisar RDS, copias manuales y respaldos retenidos. Detener RDS elimina el cargo de horas de instancia durante la detención, pero no necesariamente los de almacenamiento y respaldos. Una eliminación de la base o sus respaldos requiere una decisión explícita sobre retención.
4. Revisar S3: objetos, versiones, marcadores de eliminación y cargas incompletas. No retirar archivos fuera del alcance del laboratorio.
5. Revisar Secrets Manager y permisos IAM. Mantener el plazo de recuperación adecuado para un secreto que no deba borrarse de inmediato y no retirar permisos compartidos sin revisar dependencias.
6. **No retirar una clave KMS hasta confirmar que no protege ningún dato, copia o registro necesario.** Si se elimina, los datos cifrados con ella pueden resultar irrecuperables.
7. Revisar al final recursos residuales, Cost Explorer y alertas. Confirmar en una revisión posterior si dejaron de aparecer cargos nuevos; puede existir retraso de facturación.

Fuentes: [cargos de RDS y recursos detenidos](https://aws.amazon.com/rds/mysql/pricing/), [costos de IPv4](https://aws.amazon.com/vpc/pricing/) y [eliminación de claves KMS](https://docs.aws.amazon.com/kms/latest/developerguide/deleting-keys.html).
