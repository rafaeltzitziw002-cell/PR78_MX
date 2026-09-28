# [Task] 69000 -[QA/DEV] Matriz de Pruebas Unitarias/Integración (Perímetro WAF / API Gateway)

- **Tipo:** Task
- **ID:** 69000
- **Estado:** To Do
- **Asignado a:** Rafael Cuahtepitzi Cuahtlapantzi
- **Sprint / Iteracion:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS
- **Padre:** #68048

## Estimaciones
- **Original Estimate:** 10 hrs
- **Remaining Work:** 10 hrs
- **Completed Work:** 0 hrs
- **Story Points:** 0
- **Effort:** 0

## Descripcion
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
