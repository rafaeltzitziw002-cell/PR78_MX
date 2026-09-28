# [Task] 68667 -[QA/DEV] Matriz de Pruebas Unitarias, Invocación API Gateway y Ejecución en OpenShift Dev

- **Tipo:** Task
- **ID:** 68667
- **Estado:** To Do
- **Asignado a:** Rafael Cuahtepitzi Cuahtlapantzi
- **Sprint / Iteracion:** I24048-TDCEDIS WMS\MVP1-TDCEDIS WMS
- **Padre:** #68049

## Estimaciones
- **Original Estimate:** 5 hrs
- **Remaining Work:** 5 hrs
- **Completed Work:** 0 hrs
- **Story Points:** 0
- **Effort:** 0

## Descripcion
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
