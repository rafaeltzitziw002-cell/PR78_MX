# [Task] 68610 -[DEV] Modelado de Contratos,  Document Types y Schemas REST

- **Tipo:** Task
- **ID:** 68610
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
