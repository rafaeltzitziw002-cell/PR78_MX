# USER STORY 68050: WS para Consultar el ASN de OATP

## 1. Descripción
**Como:** Sistema XPOS / Aplicación en Tienda  
**Quiero:** Consultar en línea la información del ASN (*Advanced Shipping Notice*) de OATP a través de un servicio REST expuesto en webMethods  
**Para:** Disponer del detalle estructurado de cabecera y partidas de los contenedores y mercancía surtida por CEDIS para el control y recepción operativa en tienda.

---

## 2. Criterios de Aceptación (Gherkin)

### Escenario 1: Consulta exitosa de ASN (Código 101 - Happy Path)
- **Dado** que la tienda/XPOS envía los parámetros obligatorios válidos (`crPlaza`, `crTienda`, `asnNumber`) a través del API Gateway con cabecera `x-api-key` y desde una IP autorizada en la lista blanca de AWS WAF (`Oxwipsetintnprd01`)
- **Cuando** el servicio `PR78_MX_V2.Pub:runGetASN` procesa la petición y ejecuta la consulta contra la base de datos de OATP
- **Entonces** webMethods retorna código HTTP 200 con `wmCode = "101"` y `wmDescription = "Transaccion exitosa"`, devolviendo el objeto de cabecera (`asnHeader`) y la lista de detalle (`asnDetails`).

### Escenario 2: Parámetros obligatorios faltantes o con longitud inválida (Código 199)
- **Dado** que la solicitud omite alguno de los campos requeridos (`crPlaza`, `crTienda`, `asnNumber`) o viola los tipos/longitudes del contrato de entrada
- **Cuando** el servicio valida la estructura (`validate input` activo en el Document Type)
- **Entonces** webMethods retorna `wmCode = "199"` y `wmDescription = "Error de excepcion general / Parametros invalidos"`, interrumpiendo el flujo sin realizar llamadas a la base de datos.

### Escenario 3: ASN inexistente en OATP (Código 120)
- **Dado** que los parámetros enviados son válidos pero el `asnNumber` no cuenta con registros asociados para la plaza y tienda especificadas
- **Cuando** el Adapter Service ejecuta la consulta en la BD de OATP y retorna un arreglo vacío / nulo
- **Entonces** webMethods responde con `wmCode = "120"` y `wmDescription = "No se encontraron registros para el ASN consultado"`.

### Escenario 4: Falla de conexión a base de datos OATP (Código 131)
- **Dado** que el servicio intenta establecer conexión hacia la base de datos de OATP
- **Cuando** se suscita una falla en el pool JDBC, timeout o caída del backend
- **Entonces** el bloque `CATCH` intercepta la excepción, registra el incidente en la tabla corporativa `WMLOG.WM_LOG_ERROR_TPE` mediante `FEMSA_OXXO_MS.Pub:logTPEError` (especificando `TPE_TYPE = 'PR78_MX_V2'`), y retorna `wmCode = "131"`.

---

## 3. Especificación Técnica de Interfaz

- **Paquete:** `FEMSA_PR78_MX_V2`
- **Servicio Público de Entrada:** `PR78_MX_V2.Pub:runGetASN`
- **Método HTTP:** `POST`
- **Protocolo y Formato:** REST / JSON (UTF-8)
- **Puerto de Ejecución:** `8525` (HTTP interno en MSR Red Hat OpenShift / ROSA AWS)
- **Seguridad y Perímetro:**
  - AWS WAF: Validación de IP Set (`Oxwipsetintnprd01`)
  - AWS API Gateway V2: Cabecera obligatoria `x-api-key`
  - IS ACL: `Anonymous` en servicio Pub, recurso asignado a *Allow List* bajo política *Deny by Default*.

### 3.1. Contrato Request (JSON)
```json
{
  "crPlaza": "10MON",
  "crTienda": "50EDI",
  "asnNumber": "3108604169"
}
```

| Campo | Tipo de Dato | Longitud (Min - Max) | Obligatorio | Nulable | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `crPlaza` | String | 5 - 5 | M | N | Identificador alfanumérico de la plaza |
| `crTienda` | String | 5 - 5 | M | N | Identificador alfanumérico de la tienda |
| `asnNumber` | String | 1 - 20 | M | N | Número identificador del ASN / Embarque |

### 3.2. Contrato Response (JSON - Exitoso 101)
```json
{
  "wmCode": "101",
  "wmDescription": "Transaccion exitosa",
  "crPlaza": "10MON",
  "crTienda": "50EDI",
  "asnNumber": "3108604169",
  "asnHeader": {
    "creationDate": "2026-09-28T16:00:00",
    "totalUnits": 120,
    "status": "LOADED"
  },
  "asnDetails": [
    {
      "itemSku": "7502285034891",
      "containerId": "00001118000080160361",
      "quantity": 2
    }
  ]
}
```

---

## 4. Lineamientos de Implementación y Gobernanza
- **Manejo de Pipeline:** Implementación estricta de `Drop Variables` después de transformaciones y llamadas JDBC; evitar retención de estructuras temporales en memoria.
- **Transaccionalidad:** Conexiones JDBC Adapter configuradas con tipo de transacción no transaccional (`NT - No Transaction`) al tratarse de servicios de consulta directa.
- **Trazabilidad y Auditoría:** Prohibido el uso de `wm_log_run` por ser interfaz transaccional en línea. Todo error no controlado o de infraestructura debe invocar `FEMSA_OXXO_MS.Pub:logTPEError` para su persistencia en el esquema `WMLOG` (Aurora PostgreSQL).
- **Entregables Requeridos (DoD):** Matriz de Pruebas Unitarias (+80% cobertura en Azure Test Plans), especificación técnica actualizada en SharePoint (`FCTI_EstructuraSP`), y paquete de Change Order (CHO).