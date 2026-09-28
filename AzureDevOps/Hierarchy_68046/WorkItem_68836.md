# [Task] 68836 -[DEV] Generación de Entregables de Change Order y Documentación Técnica

- **Tipo:** Task
- **ID:** 68836
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

## Criterios de Aceptacion


## Sub-elementos / Hijos directos
Ninguno

---
