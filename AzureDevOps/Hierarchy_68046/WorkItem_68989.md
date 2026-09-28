# [Task] 68989 -[DEV] Modelado de Document Types, Schemas y Contratos de Datos

- **Tipo:** Task
- **ID:** 68989
- **Estado:** To Do
- **Asignado a:** Rafael Cuahtepitzi Cuahtlapantzi
- **Sprint / Iteracion:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS
- **Padre:** #68048

## Estimaciones
- **Original Estimate:** 5 hrs
- **Remaining Work:** 5 hrs
- **Completed Work:** 0 hrs
- **Story Points:** 0
- **Effort:** 0

## Descripcion
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
