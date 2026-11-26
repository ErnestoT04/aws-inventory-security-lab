# Implementación en un entorno propio

[Volver al índice](../README.md)

Usar una cuenta de práctica autorizada, un conjunto de datos ficticio y recursos de prueba. Antes de crear recursos, revisar los cobros y anotar el plan de limpieza.

1. **Preparar la aplicación.** Instalar PHP y sus dependencias de Composer. Usar la configuración de ejemplo con referencias ficticias; mantener cualquier archivo de configuración local fuera de Git. Importar solo un esquema y datos de prueba. No reutilizar cuentas de demostración ni contraseñas predeterminadas.
2. **Separar aplicación y datos.** Desplegar la aplicación en EC2 y crear RDS MySQL sin acceso público. Permitir MySQL desde el grupo de seguridad de la aplicación, no desde internet. Probar la conexión con datos ficticios.
3. **Configurar identidad y secreto.** Asociar a EC2 un rol de ejecución con los permisos mínimos para leer el secreto autorizado y trabajar con los objetos necesarios. Configurar la referencia al secreto como variable del entorno sin registrar su valor.
4. **Separar los archivos.** Mantener el bucket privado y acotar el acceso a los prefijos de trabajo. Configurar SSE-KMS en el laboratorio y revisar el comportamiento del código que realiza cada carga: productos y reportes deben comprobarse por separado. Un ajuste de cifrado por defecto no sustituye la comprobación de una carga que solicita cifrado distinto.
5. **Validar con objetos nuevos.** Ejecutar una prueba de conexión a RDS, crear un producto ficticio, generar un reporte ficticio y consultar los metadatos de cada objeto recién creado. Anotar solo el modo de cifrado devuelto. No copiar la salida completa del proveedor.
6. **Documentar y limpiar.** Guardar el resultado redactado de cada prueba, cerrar el acceso del entorno temporal y seguir la lista de limpieza.
