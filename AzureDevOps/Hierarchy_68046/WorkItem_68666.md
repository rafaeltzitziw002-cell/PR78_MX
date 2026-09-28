# [Task] 68666 -[DEV] Exposición REST Descriptor, Alias de URL y Manejo de Errores TPE

- **Tipo:** Task
- **ID:** 68666
- **Estado:** To Do
- **Asignado a:** Rafael Cuahtepitzi Cuahtlapantzi
- **Sprint / Iteracion:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS
- **Padre:** #68049

## Estimaciones
- **Original Estimate:** 4 hrs
- **Remaining Work:** 4 hrs
- **Completed Work:** 0 hrs
- **Story Points:** 0
- **Effort:** 0

## Descripcion
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
