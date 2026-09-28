# [Task] 68998 -[DEV] Exposición (WSD / REST API Descriptor), Alias de URL y Manejo de Errores Corporativo

- **Tipo:** Task
- **ID:** 68998
- **Estado:** To Do
- **Asignado a:** Rafael Cuahtepitzi Cuahtlapantzi
- **Sprint / Iteracion:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS
- **Padre:** #68048

## Estimaciones
- **Original Estimate:** 6 hrs
- **Remaining Work:** 6 hrs
- **Completed Work:** 0 hrs
- **Story Points:** 0
- **Effort:** 0

## Descripcion
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
