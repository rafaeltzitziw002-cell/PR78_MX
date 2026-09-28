# 📊 CONSOLIDADO JERÁRQUICO - WORK ITEM #68046

## Resumen Ejecutivo
- **Total Elementos Analizados:** 16
- **Desglose por Tipo:**
- **Epics:** 1
- **Tasks:** 10
- **User Storys:** 5

### ⏱️ Esfuerzo Total Acumulado
- **Horas Estimadas (Original Estimate):** 64 hrs
- **Horas Restantes (Remaining Work):** 64 hrs
- **Horas Completadas (Completed Work):** 0 hrs
- **Story Points Totales:** 0
- **Effort Total:** 0

---
## 🌳 Estructura Jerárquica del Árbol
- [Epic] #68046 - Transferencias de ASNs a Tienda (Por iniciar | Est: 0h / SP:0)
  - [User Story] #68048 - WS Para la actualización de Estatus en POS_OUTBOUND_DOCS (Por iniciar | Est: 0h / SP:0)
    - [Task] #68998 - [DEV] Exposición (WSD / REST API Descriptor), Alias de URL y Manejo de Errores Corporativo (To Do | Est: 6h / SP:0)
    - [Task] #69001 - [DEV] Paquete de Entregables de Change Order (CHO) y Documentación Técnica (FCTI_EstructuraSP) (To Do | Est: 8h / SP:0)
    - [Task] #68989 - [DEV] Modelado de Document Types, Schemas y Contratos de Datos (To Do | Est: 5h / SP:0)
    - [Task] #68991 - [DEV] Construcción de Lógica de Negocio en Flow Services (Pipeline, Validaciones, Mappings) (To Do | Est: 9h / SP:0)
    - [Task] #69000 - [QA/DEV] Matriz de Pruebas Unitarias/Integración (Perímetro WAF / API Gateway) (To Do | Est: 10h / SP:0)
  - [User Story] #68050 - WS para Consultar el ASN de OATP (Por iniciar | Est: 0h / SP:0)
  - [User Story] #68049 - WS Para la mover el XML de carpeta en el buzón de Tienda (Por iniciar | Est: 0h / SP:0)
    - [Task] #68666 - [DEV] Exposición REST Descriptor, Alias de URL y Manejo de Errores TPE (To Do | Est: 4h / SP:0)
    - [Task] #68610 - [DEV] Modelado de Contratos,  Document Types y Schemas REST (To Do | Est: 4h / SP:0)
    - [Task] #68836 - [DEV] Generación de Entregables de Change Order y Documentación Técnica (To Do | Est: 5h / SP:0)
    - [Task] #68602 - [DEV] Lógica de Negocio en Flow Service y Manejo de Buzón (To Do | Est: 8h / SP:0)
    - [Task] #68667 - [QA/DEV] Matriz de Pruebas Unitarias, Invocación API Gateway y Ejecución en OpenShift Dev (To Do | Est: 5h / SP:0)
  - [User Story] #68047 - WS para consulta de CEDIS Migrado WMS (Por iniciar | Est: 0h / SP:0)
  - [User Story] #68051 - Reingeniería de ASN vía Cometa (Por iniciar | Est: 0h / SP:0)

---
## 📑 Detalle Completo de Elementos
## [Epic] #68046 - Transferencias de ASNs a Tienda
- **Estado:** Por iniciar | **Asignado:** José Eduardo González Soto | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #67980
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---

### [User Story] #68048 - WS Para la actualización de Estatus en POS_OUTBOUND_DOCS
- **Estado:** Por iniciar | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68046
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---

#### [Task] #68998 - [DEV] Exposición (WSD / REST API Descriptor), Alias de URL y Manejo de Errores Corporativo
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68048
- **Horas Estimadas:** 6h | **Restantes:** 6h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
Exponer el servicio mediante un REST API Descriptor (RAD), configurar el URL Alias corporativo en el Integration Server y canalizar las excepciones capturadas hacia la bitácora LOGTPE en base de datos.

### Criterios de Aceptación
- [ ] REST API Descriptor (RAD) configurado exponiendo la operación vía método HTTP `POST` o `PUT`.
- [ ] Configuración del URL Alias corporativo asociado al recurso REST y asignado a puerto seguro.
- [ ] Cumplimiento de directivas de seguridad (ACL Anonymous / verificación de puerto).
- [ ] Integración en el bloque Catch con `pub.flow:getLastError` e invocación a `FEMSA_OXXO_MS.Pub:logTPEError` / `LOG.Pub:logTPEError`.
- [ ] Persistencia de fallos técnicos y funcionales en la tabla `WMLOG.WM_LOG_ERROR_TPE` con trazabilidad completa (servicio, fecha, mensaje, payload).
- [ ] Prohibido el uso de `wm_log_run` por ser un servicio en línea.

### Entregables Tangibles
- REST API Descriptor: `restv2/PR78_MX_V2.WS:ws/ws/PR78_MX_V2/runUpdPOD`
- Configuración documentada de URL Alias: `api/v2/statusPOD`
- Bloque Catch integrado con trazabilidad a `WMLOG.WM_LOG_ERROR_TPE`



---

#### [Task] #69001 - [DEV] Paquete de Entregables de Change Order (CHO) y Documentación Técnica (FCTI_EstructuraSP)
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68048
- **Horas Estimadas:** 8h | **Restantes:** 8h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
Exportar el paquete de despliegue de la solución, completar las listas de verificación requeridas por Aseguramiento de Calidad/Auditoría y generar la documentación operativa bajo la estructura estandarizada FCTI_EstructuraSP para la gestión del Change Order.

### Criterios de Aceptación
- [ ] Documento de migración (`DocMigracion_[NUM_CHO]_QA.xlsx` y `DocMigracion_[NUM_CHO]_PRD.xlsx`) con detalle de Inbound, URL Aliases, Allow List de puertos y reinicio de pods.
- [ ] Lista de Verificación de Código (`LV_Codigo_[Interfaz]_[NUM_CHO].xlsx`) completada y aprobada al 100%.
- [ ] Lista de Verificación de Diseño (`LV_Diseño_[Interfaz]_[NUM_CHO].xlsx`) completada y aprobada al 100%.
- [ ] Especificación técnica y Runbook actualizados con endpoints, parámetros y matriz de escalación.
- [ ] Archivo Exportado de instalación (`.zip` del paquete IS) generado y ubicado en la estructura documental de SharePoint.

### Entregables Tangibles
- Paquete de despliegue: `FEMSA_PR78_MX_V2.zip`
- Documentos de Migración para QA y PRD en carpeta `Doc Migración`
- Listas de verificación aprobadas: `LV_Codigo` y `LV_Diseño`
- Estructura completa de carpetas organizada en SharePoint bajo `FCTI_EstructuraSP`



---

#### [Task] #68989 - [DEV] Modelado de Document Types, Schemas y Contratos de Datos
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68048
- **Horas Estimadas:** 5h | **Restantes:** 5h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
Definir y versionar en Software AG Designer los contratos de datos de entrada y salida para el servicio de actualización de estatus en la tabla POS_OUTBOUND_DOCS, aplicando validaciones estrictas de tipado y restricciones del estándar FEMCO.


### Criterios de Aceptación
- [ ] Document Type de Request modelado con restricciones estrictas (`Required=True`, `Allow null=False`) para llaves operativas (documentId, crPlaza, crTienda, status).
- [ ] Document Type de Response estructurado bajo el estándar corporativo (`wmCode`, `wmDescription`).
- [ ] Validación de tipos de datos alineada con las columnas de `POS_OUTBOUND_DOCS`.
- [ ] Artefactos ubicados en el namespace `PR78_MX_V2/Docs/...` .

### Entregables Tangibles
- Document Type de Request: `PR78_MX_V2.Docs:docStatusUpdateRequest`
- Document Type de Response: `PR78_MX_V2.Docs:docStatusUpdateResponse`
- Schemas JSON / IS Document Types.



---

#### [Task] #68991 - [DEV] Construcción de Lógica de Negocio en Flow Services (Pipeline, Validaciones, Mappings)
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68048
- **Horas Estimadas:** 9h | **Restantes:** 9h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
Implementar el servicio principal de integración, ejecutando la validación del contrato de entrada, el mapeo de datos y la invocación al JDBC Adapter Service para actualizar el estatus del documento en la tabla POS_OUTBOUND_DOCS.

### Criterios de Aceptación

- [ ] Validación de parámetros de entrada obligatorios con manejo de excepciones controladas.
- [ ] Construcción e invocación del JDBC Adapter Service (`adpUpdateStatusOutboundDocs`) sobre la conexión correspondiente.
- [ ] Cero uso de servicios de depuración (`pub.flow:savePipeline`, `restorePipeline`).

### Entregables Tangibles
- Flow Service Orquestador: `PR78_MX_V2.Mappings:main`
- Flow Service de Carga: `PR78_MX_V2.Mappings.Load:updateOutboundDocStatus`
- JDBC Adapter Service: `PR78_MX_V2.DB.&lt;CONNECTION&gt;:adpUpdateStatusOutboundDocs`



---

#### [Task] #69000 - [QA/DEV] Matriz de Pruebas Unitarias/Integración (Perímetro WAF / API Gateway)
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68048
- **Horas Estimadas:** 10h | **Restantes:** 10h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
Diseñar, ejecutar y documentar la matriz de pruebas unitarias y de integración perimetral para validar la lógica funcional, controles de seguridad y persistencia de errores, asegurando una cobertura superior al 80% requerida por el rol Developer Cross-Stack.

### Esfuerzo Estimado
- **Esfuerzo Base:** 8.0 h
- **Colchón de Contingencia:** +2.5 h (Validaciones de cabeceras de seguridad perimetral, armado de colecciones y consultas SQL de respaldo)
- **Total Comprometido (Original Estimate):** 10.5 h
- **Remaining Work:** 10.5 h

### Criterios de Aceptación
- [ ] Cobertura de pruebas unitarias y de integración &gt;= 80%.
- [ ] Escenarios de Happy Path documentados: Payload válido, cabecera `x-api-key` correcta, IP autorizada y actualización exitosa en BD (`wmCode = '101'`).
- [ ] Escenarios de Edge Cases documentados:
  - Faltante de parámetros obligatorios o JSON malformado (`wmCode = '112'`).
  - Identificador de documento inexistente en `POS_OUTBOUND_DOCS`.
  - Peticiones sin cabecera `x-api-key` (HTTP 403 vía API Gateway).
  - Peticiones desde IPs no registradas en la lista permitida de WAF (HTTP 403).
  - Caída/timeout de base de datos capturada en `WMLOG.WM_LOG_ERROR_TPE` (`wmCode = '199'`).
- [ ] Resultados y evidencias (capturas de pantalla con fecha/hora completa, request, response y querys SQL) cargados en Azure Test Plans vinculados a la HU-68048.

### Entregables Tangibles
- Colección de Postman y Environment con Happy Path y Edge Cases.
- Matriz de Pruebas Unitarias en formato Excel (`Matriz_Pruebas_Unitarias_PR78_MX_V2.xlsx`).



---

### [User Story] #68050 - WS para Consultar el ASN de OATP
- **Estado:** Por iniciar | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68046
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---

### [User Story] #68049 - WS Para la mover el XML de carpeta en el buzón de Tienda
- **Estado:** Por iniciar | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68046
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---

#### [Task] #68666 - [DEV] Exposición REST Descriptor, Alias de URL y Manejo de Errores TPE
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68049
- **Horas Estimadas:** 4h | **Restantes:** 4h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
### &#128203; Descripción Técnica de la Tarea
Publicar el servicio como endpoint REST POST mediante REST API Descriptor/WSD y canalizar las excepciones en línea a través del framework de errores `WM_LOG_ERROR_TPE` sin persistir trazas de error al cliente.

---
### &#128736;️ Actividades a Realizar
- [ ] Crear el Flow Service público `PR78_MX_V2.Pub:runMovDocAsn` con bloque estandarizado `TRY-CATCH`:
  - **TRY**: Invocación al servicio `PR78_MX_V2.Mappings.Load:moveDocAsnFile`.
  - **CATCH**: Captura con `pub.flow:getLastError`, ejecución del logging transversal hacia `FEMSA_OXXO_MS.Pub:logTPEError` (registrando en `WM_LOG_ERROR_TPE` con `TPE_TYPE = 'PR78_MX_V2'`), y retorno controlado de códigos seguros (`199 - Error en ejecución`).
- [ ] Configurar el descriptor RESTv2 en `PR78_MX_V2.WS:ws` asociando el verbo `POST` con la operación `runMovDocAsn`.
- [ ] Configurar URL Alias para el Microservice Runtime:
  - **Alias:** `api/v2/movdocasn`
  - **Target:** `restv2/PR78_MX_V2.WS:ws/ws/PR78_MX_V2/runMovDocAsn`
- [ ] Documentar la regla de acceso en el puerto 8525 (`Allow List` con directriz *Deny by Default*).
- [ ] Configurar el catálogo y mapeo de nuevos códigos de respuesta/error en `PR78_MX_V2.Public:setResponseCode` y en la especificación técnica (Sección 3.2.2):

&nbsp; - **132:** *Ocurrió un error al buscar registros de conexión de buzón en WM* (Acción: Enviar notificación / Rol Receptor: `WMADMIN`).

&nbsp; - **133:** *Ocurrió un error al mover ASN de directorio en Buzón* (Acción: Enviar notificación / Rol Receptor: `WMADMIN`).

---
### &#128230; Entregables Tangibles
- `PR78_MX_V2.Pub:runMovDocAsn`
- Descriptor RESTv2 actualizado en `PR78_MX_V2.WS:ws`
- URL Alias `/api/v2/movdocasn` configurado

---
### ⏱️ Estimación
- **Tiempo estimado:** 4 horas
- **Rol ejecutor:** Developer Cross-Stack (Dev+QA)



---

#### [Task] #68610 - [DEV] Modelado de Contratos,  Document Types y Schemas REST
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68049
- **Horas Estimadas:** 4h | **Restantes:** 4h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
### &#128203; Descripción Técnica de la Tarea
Diseñar y modelar los esquemas de datos y documentos requeridos para la operación REST POST `movdocasn` dentro del paquete `FEMSA_PR78_MX_V2`, asegurando validaciones de entrada conforme al estándar de codificación y arquitectura FEMCO.

---
### &#128736;️ Actividades a Realizar
- [ ] Crear el Document Type de entrada en `PR78_MX_V2.Docs:wsMovDocAsnRequest`.
  - Definir campos obligatorios: `crPlaza`, `crTienda`, `transferNumber`, `fileName`.
  - Configurar constraints y restricciones: `Required=True`, `Allow null=False`, longitud mínima/máxima y tipos de datos `String`.
- [ ] Crear el Document Type de salida estándar en `PR78_MX_V2.Docs:wsMovDocAsnResponse`.
  - Incluir los campos de respuesta: `wmCode` (String) y `wmDescription` (String).
- [ ] Modularizar sub-estructuras si aplica para permitir reusabilidad y flexibilidad en el esquema.

---
### &#128230; Entregables Tangibles
- `PR78_MX_V2.Docs:wsMovDocAsnRequest`
- `PR78_MX_V2.Docs:wsMovDocAsnResponse`

---
### ⏱️ Estimación
- **Tiempo estimado:** 4 horas
- **Rol ejecutor:** Developer Cross-Stack (Dev+QA)



---

#### [Task] #68836 - [DEV] Generación de Entregables de Change Order y Documentación Técnica
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68049
- **Horas Estimadas:** 5h | **Restantes:** 5h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
### &#128203; Descripción Técnica de la Tarea
Elaborar y actualizar documentación técnica y artefactos para el Change Order (CHO) de la interfaz `FEMSA_PR78_MX_V2` conforme a la estructura oficial de SharePoint.

---
### &#128736;️ Actividades a Realizar

#### 1. Entregables en Carpeta Documentos
- [ ] **Actualización de Especificación Técnica (`FCTI_CNF_Especificación Técnica_PR78_MX_NUBE_V2.docx`):**
  - Actualizar el objetivo y alcance documentando la operación REST POST `movdocasn`.
  - Actualizar la tabla *3.2.2 Errores, advertencias y avisos* incorporando los códigos **132** (*Ocurrió un error al buscar registros de conexión de buzón en WM*) y **133** (*Ocurrió un error al mover ASN de directorio en Buzón*) dirigidos al rol `WMADMIN`.
  - Agregar diagrama de actividad para el flujo de `PR78_MX_V2.Pub:runMovDoc` / `runMovDocAsn`.
  - Agregar diagrama de secuencia y narrativa funcional/técnica paso a paso para `PR78_MX_V2.Pub:runMovDoc`.
  - Actualizar el Modelo Entidad-Relación (DER) reflejando las tablas o vistas involucradas y el esquema de auditoría en `WM_LOG_ERROR_TPE`.
- [ ] **Documento de Mapeo de Datos (`Mapeo de entrada y salida JSON - FEMSA_PR78_MX_V2.xlsx`):**
  - Incorporar los contratos `REQUEST - MOVDOCASN` y `RESPONSE - MOVDOCASN` con tipado, obligatoriedad, longitudes (min/max), constraints y ejemplos JSON de entrada/salida.
- [ ] **Actualización de Runbook (`FCTI_CNF_Runbook_FEMSA_PR78_MX_NUBE_V2.docx`):**
  - Incorporar la nueva operación `movdocasn`, sus variables operativas, parámetros de buzón y dependencias de ejecución.

---

#### 2. Entregables en Carpeta Change Order (`[ID] - CHO [NUM_CHO]`)
- [ ] **Subcarpeta Doc Migración:**
  - Generar `DocMigracion_[NUM_CHO]_QA.xlsx` y `DocMigracion_[NUM_CHO]_PRD.xlsx` detallando:
    - *IntegrationServer:* Instalación de `FEMSA_PR78_MX_V2.zip` en `/opt/softwareag/IntegrationServer/replicate/inbound` y reload de package.
    - *AccionesPosteriores:* Configuración del URL Alias `api/v2/movdocasn`, inclusión en `Allow List` del puerto 8525 (`Deny by Default`) y Execute ACL = `Anonymous` para `PR78_MX_V2.Pub:runMovDoc`.
- [ ] **Checklist de Diseño:**
  - Diligenciar y adjuntar el formato `LV_Diseño_FEMSA_PR78_MX_V2_[NUM_CHO].xlsx` validando el cumplimiento de arquitectura y principios de diseño seguro.
- [ ] **Checklist de Código:**
  - Diligenciar y adjuntar el formato `LV_Codigo_FEMSA_PR78_MX_V2_[NUM_CHO].xlsx` validando convenciones de nomenclatura, manejo de pipeline (drop/clear), try-catch y compilación correcta.
- [ ] **Consolidación de Evidencia de Pruebas Unitarias:**
  - Colocar en la subcarpeta `Evidencias de Pruebas Unitarias` la matriz ejecutada en la Task 4 (`Matriz_Pruebas_Unitarias_FEMSA_PR78_MX_V2_movdocasn.xlsx`) con su liga a SharePoint.
- [ ] **Estructuración y Registro en Service Desk:**
  - Organizar el directorio en SharePoint siguiendo la jerarquía estándar:
    ```text
    FEMSA_PR78_MX_V2/
    ├── Documentos/
    │   ├── FCTI_CNF_Especificación Técnica_PR78_MX_NUBE_V2.docx
    │   ├── Documento de mapeo de datos FEMSA_PR78_MX_V2.xlsx
    │   └── FCTI_CNF_Runbook_FEMSA_PR78_MX_NUBE_V2.docx
    └── Change Request/
        └── [ID] - CHO [NUM_CHO]/
            ├── Doc Migración/
            │   ├── DocMigracion_[NUM_CHO]_QA.xlsx
            │   └── DocMigracion_[NUM_CHO]_PRD.xlsx
            ├── Pruebas Unitarias/
            │   └── Matriz_Pruebas_Unitarias_FEMSA_PR78_MX_V2_movdocasn.xlsx
            ├── LV_Diseño_FEMSA_PR78_MX_V2_[NUM_CHO].xlsx
            └── LV_Codigo_FEMSA_PR78_MX_V2_[NUM_CHO].xlsx
    ```


---
### &#128230; Entregables Tangibles
- Documentación técnica actualizada (`Especificación Técnica`, `Mapeo JSON`, `Runbook`).
- Documentos de migración para QA y PRD en formato estándar.
- Checklists de calidad validados (`LV_Diseño` y `LV_Codigo`).
- Carpeta CHO en SharePoint con estructura `FCTI_EstructuraSP` y enlace listo para Service Desk.

---
### ⏱️ Estimación
- **Tiempo estimado:** 5 horas
- **Rol ejecutor:** Developer Cross-Stack (Dev+QA)



---

#### [Task] #68602 - [DEV] Lógica de Negocio en Flow Service y Manejo de Buzón
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68049
- **Horas Estimadas:** 8h | **Restantes:** 8h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
### &#128203; Descripción Técnica de la Tarea
Construir el servicio central de procesamiento para mover el archivo XML dentro del buzón de tienda.

---
### &#128736;️ Actividades a Realizar
- [ ] Crear el Flow Service de negocio: `PR78_MX_V2.Mappings.Load:moveDocAsnFile`.
- [ ] Implementar la validación de presencia del archivo XML en el directorio origen del buzón de la tienda solicitada.
- [ ] Ejecutar el traslado del archivo hacia el subdirectorio de destino parametrizado.
- [ ] Asegurar buenas prácticas de pipeline:
  - Respetar los mismos nombres en mapeos de entrada/salida para evitar copias residuales en el pipeline.
  - Agrupar transformaciones en una sola operación de MAP donde sea viable.
  - Ejecutar **Drop Variables** inmediatos de objetos temporales.
  - Finalizar el flujo invocando `pub.flow:clearPipeline` para optimizar memoria en runtime.
- [ ] Documentar cada paso del servicio con comentarios claros indicando la operación y el identificador de la US 68049.

---
### &#128230; Entregables Tangibles
- `PR78_MX_V2.Mappings.Load:moveDocAsnFile` (Flow Service completo y comentado)

---
### ⏱️ Estimación
- **Tiempo estimado:** 8 horas
- **Rol ejecutor:** Developer Cross-Stack (Dev+QA)



---

#### [Task] #68667 - [QA/DEV] Matriz de Pruebas Unitarias, Invocación API Gateway y Ejecución en OpenShift Dev
- **Estado:** To Do | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68049
- **Horas Estimadas:** 5h | **Restantes:** 5h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**
### &#128203; Descripción Técnica de la Tarea
Diseñar, estructurar y ejecutar la matriz de pruebas unitarias y de integración end-to-end para la nueva operación REST POST `movdocasn`. La validación se realizará en **AWS API Gateway** y filtrado perimetral por **WAF**, comprobando los códigos de negocio (101, 132, 133, 199) y la inserción de errores en `WM_LOG_ERROR_TPE`.

---
### &#128736;️ Actividades a Realizar

#### 1. Pruebas de Integración a través de AWS API Gateway (V2)
- [ ] Configurar Postman con el endpoint del API Gateway de desarrollo:  
  `POST https://94olw5z82h.execute-api.us-east-1.amazonaws.com/dev/api/v2/movdocasn`
- [ ] **CP01 (Happy Path - Código 101):**
  - *Precondición:* Header de autenticación (`x-api-key` / `x-Gateway-APIKey`), IP origen autorizada en WAF (`Oxwipsetintnprd01`), XML existente en buzón de tienda.
  - *Resultado:* Tráfico admitido por WAF/API Gateway, traslado físico del archivo en buzón y retorno HTTP 200 con `wmCode = '101'` y `wmDescription = 'Transaccion exitosa'`.
- [ ] **CP02 (Edge Case - Conexión de Buzón - Código 132):**
  - *Precondición:* Solicitud vía API Gateway simulando falla o ausencia de parámetros de conexión al buzón en WM.
  - *Resultado:* Captura en Catch, notificación a `WMADMIN` y retorno con `wmCode = '132'` (*Ocurrió un error al buscar registros de conexión de buzon en WM*).
- [ ] **CP03 (Edge Case - Mover Archivo ASN - Código 133):**
  - *Precondición:* Solicitud vía API Gateway forzando error al mover el archivo (archivo inexistente, permisos insuficientes).
  - *Resultado:* Notificación a `WMADMIN` y retorno con `wmCode = '133'` (*Ocurrio un error al mover ASN de directorio en Buzon*).
- [ ] **CP04 (Error Handling Genérico - Código 199):**
  - *Precondición:* Solicitud vía API Gateway forzando una excepción general no controlada en WM.
  - *Resultado:* Notificación a `WMADMIN` y respuesta con `wmCode = '199'` (*Ocurrió un error en el proceso de WM*).
- [ ] **CP05 (Verificación de Logging Transversal TPE):**
  - *Acción:* Comprobar inserción en la BD Aurora PostgreSQL ante las ejecuciones fallidas:  
    `SELECT * FROM WM_LOG_ERROR_TPE WHERE TPE_TYPE = 'PR78_MX_V2' ORDER BY ERROR_DATE DESC;`

---

#### 2. Pruebas de Seguridad y Filtrado Perimetral (WAF &amp; API Gateway)
- [ ] **CP06 (Seguridad API Gateway - Sin API Key / Key Inválida):**
  - *Precondición:* Enviar petición POST omitiendo el header `x-api-key` o usando un valor incorrecto.
  - *Resultado:* Bloqueo perimetral en API Gateway con código HTTP 403 Forbidden.
- [ ] **CP07 (Seguridad WAF - Restricción por IP / IPSet):**
  - *Precondición:* Enviar petición desde una dirección IP pública no registrada en el IPSet del WAF (`Oxwipsetintnprd01`).
  - *Resultado:* Bloqueo perimetral en la capa WAF (HTTP 403) sin alcanzar el backend de webMethods.
- [ ] **CP08 (Validación de Verbos HTTP No Permitidos):**
  - *Precondición:* Invocar la ruta `/api/v2/movdocasn` mediante métodos GET, PUT o DELETE.
  - *Resultado:* Rechazo inmediato con HTTP 405 Method Not Allowed / 403 según las políticas del API Gateway.

---

#### 3. Formalización y Carga de Evidencias
- [ ] Documentar los resultados y evidencias de cada caso en la plantilla `Matriz_Pruebas_Unitarias_FEMSA_PR78_MX_V2_movdocasn.xlsx` (Request, Response, Headers, Status Code y consultas SQL).
- [ ] Cargar y asociar los resultados en **Azure Test Plans** asignándolos al Work Item 68049.

---
### &#128230; Entregables Tangibles
- `Matriz_Pruebas_Unitarias_FEMSA_PR78_MX_V2_movdocasn.xlsx` con los casos de API Gateway y WAF completados al 100%.
- Ejecución y evidencias de prueba vinculadas en Azure Test Plans.

---
### ⏱️ Estimación
- **Tiempo estimado:** 5 horas
- **Rol ejecutor:** Developer Cross-Stack (Dev+QA)



---

### [User Story] #68047 - WS para consulta de CEDIS Migrado WMS
- **Estado:** Por iniciar | **Asignado:** Rafael Cuahtepitzi Cuahtlapantzi | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68046
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---

### [User Story] #68051 - Reingeniería de ASN vía Cometa
- **Estado:** Por iniciar | **Asignado:** Integracion14 Integracion14 | **Sprint:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS | **Padre:** #68046
- **Horas Estimadas:** 0h | **Restantes:** 0h | **Completadas:** 0h | **Story Points:** 0

**Descripción:**




---
