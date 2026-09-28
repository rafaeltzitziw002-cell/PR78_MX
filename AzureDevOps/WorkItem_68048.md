# Historia de Usuario

**ID / Clave:** HU-68048  
**Título:** WS Para la actualización de Estatus en POS_OUTBOUND_DOCS  
**Iniciativa / Contexto:** Recibo en Tienda CEDIS / Proceso Fallback (Paso 2)  

---

### Descripción / Narrativa

* **Como:** Sistema XPOS (a través de la aplicación Oxxo al Día)
* **Quiero:** Consumir un servicio web REST que identifique los documentos ASN pendientes (estatus 'L'), bloquee su procesamiento actualizándolos a estatus 'D' en `POS_OUTBOUND_DOCS` y retorne la lista de archivos XML asociados para la tienda solicitante.
* **Para:** Bloquear los documentos en cola y obtener la referencia de los archivos a mover del buzón, habilitando el mecanismo de fallback que permite a la tienda recibir la mercancía del camión CEDIS sin generar duplicidad operativa ni desfases de inventario.

---

### Criterios de Aceptación (Gherkin)

#### Escenario 1: Actualización exitosa de estatus y retorno de lista de archivos XML
* **Dado** que la aplicación Oxxo al Día envía una petición HTTP POST válida al endpoint REST con los parámetros `crPlaza` y `crTienda` (y fecha de corte en caso de aplicar),
* **Cuando** el servicio valida la estructura del payload entrante y localiza registros de tipo ASN en la tabla `POS_OUTBOUND_DOCS` con estatus `'L'` (Pendiente de procesar),
* **Entonces** debe actualizar dichos registros a estatus `'D'` (Bloqueado por fallback) dentro de una transacción JDBC controlada (Commit),
* **Y** responder con un código HTTP `200 OK`, cabecera/cuerpo estándar de éxito (`wmCode: "P200101"`, `wmDescription: "Success"` o estándar corporativo aplicable),
* **Y** retornar en el payload JSON el arreglo con los nombres de los archivos XML detectados en buzón (ejemplo: `["ASN10GUD50B0H240808165119.xml"]`).

#### Escenario 2: Parámetros obligatorios faltantes o con formato inválido
* **Dado** que la petición omite parámetros obligatorios (`crPlaza` o `crTienda`) o exceden/no cumplen la longitud y formato estipulados (5 posiciones alfanuméricas),
* **Cuando** el motor de integración valida el input contra el esquema/contrato JSON (estrategia fail-fast),
* **Entonces** se debe detener la ejecución inmediatamente sin invocar la base de datos,
* **Y** responder con un código HTTP `400 Bad Request` indicando el error de validación sin exponer trazas técnicas internas.

#### Escenario 3: No existen documentos pendientes para la tienda
* **Dado** que se realiza la consulta para un `crPlaza` y `crTienda` válidos,
* **Cuando** no se encuentran registros en estatus `'L'` en `POS_OUTBOUND_DOCS`,
* **Entonces** el servicio debe responder de manera exitosa y controlada con una lista vacía de archivos (`"files": []`),
* **Y** retornar un código/mensaje de negocio descriptivo sin generar excepciones en Integration Server.

#### Escenario 4: Falla de comunicación o excepción en Base de Datos (Manejo de Errores)
* **Dado** que la conexión JDBC no está disponible o la sentencia SQL falla durante la actualización,
* **Cuando** la excepción es interceptada por el bloque CATCH del Flow Service,
* **Entonces** se debe ejecutar un Rollback transaccional inmediato,
* **Y** registrar el error mediante el servicio común `FEMSA_OXXO_MS:pub:logTPEError` en la tabla `WM_LOG_ERROR_TPE` (omitiendo el uso de `wm_log_run` por ser un servicio síncrono en línea),
* **Y** responder al cliente con un código HTTP `500 Internal Server Error` con mensaje sanitizado.

---

### Requerimientos Técnicos y de Integración

1. **Protocolo y Método:** REST / HTTP POST expuesto bajo alias y puerto configurado en Integration Server (con Execute ACL = Anonymous / validado por lista blanca IP si aplica).
2. **Acceso a Datos:**
   - Invocación mediante **JDBC Adapter Service** con sentencia parametrizada (sin concatenación de SQL).
   - Manejo transaccional explícito (`startTransaction`, `commitTransaction`, `rollbackTransaction`).
3. **Gobierno de Pipeline:** Liberación obligatoria de variables en memoria (*Drop Variables*) de objetos temporales, cursores y estructuras intermedias.
4. **Nomenclatura de Archivos Salida:** El formato retornado debe cumplir con el patrón `ASN{crPlaza}{crTienda}{Timestamp}.xml`.