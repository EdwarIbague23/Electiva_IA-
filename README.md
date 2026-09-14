<div align="center">

# 🧠 Proyecto de IA — MindFlow AI

**Bitácora técnica del proyecto** · Batería de prompts para desarrollo asistido por IA + Anexo de requerimientos de salud digital

![Status](https://img.shields.io/badge/status-en%20progreso-yellow)
![Docs](https://img.shields.io/badge/docs-Word%20%2F%20Markdown-blue)
![Domain](https://img.shields.io/badge/dominio-salud%20mental%20digital-9cf)
![Lang](https://img.shields.io/badge/idiomas-ES%20%2F%20EN-lightgrey)

</div>

---

## 📋 Tabla de contenido

- [Resumen del proyecto](#-resumen-del-proyecto)
- [Sesión 1 — Traducción de la batería de prompts](#-sesión-1--traducción-de-la-batería-de-prompts-al-inglés)
- [Sesión 2 — Anexo de requerimientos (app Ibagué)](#-sesión-2--anexo-de-requerimientos-app-de-apoyo-psicológico-ibagué)
- [Sesión 3 — Arquitectura de agentes (`mi-framework-in`)](#-sesión-3--arquitectura-de-agentes-mi-framework-in)
- [Regla de trabajo](#-regla-de-trabajo-para-este-proyecto)
- [Estado actual y próximos pasos](#-estado-actual-y-próximos-pasos)

---

## 🎯 Resumen del proyecto

**MindFlow AI** es una plataforma SaaS que recibe notas clínicas, protege/anonimiza información sensible (PII), analiza el contenido mediante un LLM y devuelve resultados estructurados para que un terapeuta los revise.

El insumo central del proyecto es un documento Word:

> **`MindFlow_AI_Bateria_de_Prompts_EN.docx`**

Este documento contiene:

| Bloque | Tema | Prompts |
|:---:|---|---|
| A | Arquitectura & Datos | #01–#04 |
| B | Seguridad & PII | #05–#07 |
| C | Pipeline IA / LangChain | #08–#11 |
| D | Backend API REST | #12–#16 |
| E | Frontend Components | #17–#20 |
| F | Testing & DevOps | #21–#25 |
| — | Auditoría Final | Prompt Maestro |
| — | **Anexo** | Requerimientos app de apoyo psicológico (Ibagué) |

Cada prompt está diseñado para copiarse y pegarse directamente en **Cursor, Claude Code o GitHub Copilot**.

---

## 🌐 Sesión 1 — Traducción de la batería de prompts al inglés

### Solicitud
Traducir al inglés **únicamente** el contenido de las 26 cajas "PROMPT COMPLETO LISTO PARA EJECUTAR" (25 prompts + Prompt Maestro), sin tocar el resto del documento (tablas de contexto en español, índice, encabezados de bloque).

### Qué se hizo

1. **Análisis de estructura** — Se identificó que cada prompt vive dentro de una tabla independiente en el XML del `.docx` (`word/document.xml`), localizada mediante el marcador `PROMPT COMPLETO LISTO PARA EJECUTAR`.
2. **Extracción preservando formato** — Se extrajeron los fragmentos de texto (`<w:t>`) de cada tabla respetando el formato original: negrita/color naranja para etiquetas (*Actúa como*, *Contexto*, *Tarea*, *Restricciones*, etc.), texto plano para el cuerpo, verde para "salida esperada", y código/JSON/números sin tocar.
3. **Traducción manual y consistente** — Terminología unificada en las 26 cajas:

   | Español | Inglés |
   |---|---|
   | Actúa como | Act as |
   | Contexto | Context |
   | Tarea | Task |
   | Considerar | Consider |
   | Formato | Format |
   | Restricciones | Constraints |
   | BLOQUE | BLOCK |
   | FASE | PHASE |
   | PROMPT MAESTRO | MASTER PROMPT |

   Marcadores de anonimización traducidos de forma consistente: `[PERSONA]`→`[PERSON]`, `[TELEFONO]`→`[PHONE]`, `[DIRECCION]`→`[ADDRESS]`, `[EMAIL]`→`[EMAIL]`.

4. **Reinserción quirúrgica en el XML** — Cada fragmento traducido se reinsertó en su posición exacta dentro del XML, preservando formato y espacios (`xml:space="preserve"`), sin alterar ninguna otra parte del documento.
5. **Verificación** — Validación estructural automática (1371 → 1371 párrafos, sin cambios estructurales) + inspección visual renderizando el documento a PDF.

### Resultado
✅ Las 26 cajas de prompt quedaron 100% en inglés.
✅ El resto del documento permanece en español, tal como se pidió.

---

## 🏥 Sesión 2 — Anexo de requerimientos (app de apoyo psicológico, Ibagué)

### Solicitud
Ejecutar un prompt de rol (*Arquitecto de Software / Analista de Requisitos Senior, especializado en sistemas de salud digital*) para levantar requerimientos de una app móvil/web de apoyo psicológico en **Ibagué**, y anexar el resultado al mismo Word del proyecto.

### Qué se generó

**1. Entrevista simulada** (Analista ↔ Psicólogo clínico experto) — 12 preguntas y respuestas que justifican decisiones clínicas y técnicas: consentimiento informado, estructura de la historia clínica, protocolo de riesgo/crisis suicida, disponibilidad de profesionales, verificación de tarjeta profesional, cumplimiento de la **Ley 1581 de 2012** y el **Decreto 1377 de 2013** (Colombia), política de cancelaciones, videollamada integrada, seguimiento del paciente, contexto local de Ibagué, pagos/facturación y auditoría de accesos.

**2. Requisitos Funcionales y No Funcionales** — 27 requisitos atómicos (17 RF + 10 RNF), priorizados con MoSCoW:

| ID | Tipo | Prioridad | Descripción técnica y medible |
|---|:---:|:---:|---|
| RF-01 | RF | Must | El sistema permite al paciente registrarse y autenticarse mediante 2FA antes de acceder a cualquier funcionalidad clínica. |
| RF-09 | RF | Must | El sistema activa un protocolo de alerta ante indicadores de riesgo (ideación suicida/autolesión), notificando de inmediato al profesional tratante. |
| RF-11 | RF | Should | El sistema ofrece videollamada integrada y cifrada. `[SUPUESTO: proveedor no especificado]` |
| RNF-01 | RNF | Must | Cifrado AES-256 en reposo y TLS 1.3 en tránsito para datos clínicos. |
| RNF-04 | RNF | Must | Disponibilidad mínima del 99.5% mensual para agenda y videollamada. |

*(tabla completa de 27 filas disponible en el Word)*

Los supuestos no confirmados por el experto quedan marcados explícitamente con `[SUPUESTO]`.

**3. Historias de Usuario en formato BDD** — 8 HU cubriendo: registro/autenticación, búsqueda de profesionales, agendamiento de citas, notas clínicas cifradas, historial del paciente, alertas de crisis, verificación de profesionales y gestión de disponibilidad.

```gherkin
HU-01: Como paciente nuevo, quiero registrarme y autenticarme de forma segura
       para acceder a los servicios de la plataforma con confianza.

  Dado que un usuario nuevo completa el registro con datos válidos
  Cuando envía la solicitud
  Entonces el sistema crea la cuenta y envía un código 2FA al correo/teléfono
```

### Cómo se integró al Word (sin recrearlo desde cero)

1. Se desempaquetó el `.docx` (`unzip` → `word/document.xml`).
2. Se reutilizaron los **estilos ya existentes** en el documento (títulos, subtítulos con línea inferior azul, listas con viñeta, tabla con encabezado azul `#1F4E79` y filas gris claro `#F2F2F2`), para que el anexo se vea nativo y no "pegado".
3. Se construyó el anexo como fragmentos OOXML y se insertó antes del cierre del documento, precedido de un salto de página.
4. Se validó la estructura (1371 → 1546 párrafos, sin romper nada) y se verificó visualmente vía PDF.

### Resultado
✅ El mismo archivo `MindFlow_AI_Bateria_de_Prompts_EN.docx` ahora tiene **47 páginas**, con el anexo completo integrado visualmente al 100% con el resto del documento.

---

## ⚙️ Sesión 3 — Arquitectura de agentes (`mi-framework-in`)

### Solicitud
Ejecutar un prompt de rol (*Arquitecto de Software Senior / Experto en Ingeniería de Prompts bajo metodologías basadas en agentes*) para documentar formalmente la arquitectura de MindFlow AI sobre un framework propio de agentes (`mi-framework-in`), generando el contenido de dos archivos que estaban vacíos: `docs/architecture.md` y `docs/manifest_schema.md`.

### Qué se generó

**1. `architecture.md`** — Documento de arquitectura completo con:
- **Principios de diseño** (aislamiento de PII por defecto, soporte no sustitución clínica, proveedor de LLM reemplazable, trazabilidad total, mínimo privilegio).
- **4 capas del sistema**: Interfaces (`interfaces/`), Orquestador (`core/`), Agentes (`agents/`: `triage_agent`, `emotion_analysis_agent`, `report_generation_agent`, `audit_agent`) y Skills (`skills/`: `code_executor`, `db_query`, `document_generator`, `web_search`, `tools/`).
- **Infraestructura compartida**: Memoria (sesión + histórico de análisis), LLM Gateway (abstracción de proveedor, filtrado obligatorio de salida), Seguridad (AES-256-GCM, TLS 1.3, RBAC, mínimo privilegio) y Observabilidad (logging estructurado sin PII, tracing con `request_id`, auditoría de manifiestos).
- **Diagrama de flujo de datos en Mermaid**, desde la captura de la nota clínica hasta el reporte final, marcando los puntos de control críticos (anonimización no omitible, LLM Gateway único, validación de `output_schema`, verificación de `ownership`).

**2. `manifest_schema.md`** — Especificación técnica formal para `config/agents.yaml` y `config/skills.yaml`:
- Campos obligatorios y opcionales para **agentes** (`name`, `version`, `role`, `input_schema`, `output_schema`, `permissions`, `model_policy`, `pii_policy`, etc.), incluyendo el objeto `permissions` (`allowed_skills`, `data_scope`, `network_access`, `pii_access`).
- Campos obligatorios y opcionales para **skills** (`category`, `entrypoint`, `sandboxed`, `permissions` con `requires_network`, `pii_access`, `allowed_domains`).
- Ejemplos YAML completos y realistas: `emotion_analysis_agent`, y las skills `pii_pipeline`, `document_generator` y `web_search`.
- **Reglas de validación del Orquestador** (7 reglas), incluyendo la prohibición explícita de campos `diagnosis`/`prescription`/`treatment_plan` en cualquier `output_schema` de agente — coherente con el rol de soporte analítico (no diagnóstico) del sistema.

### Coherencia con el dominio de salud mental
Ambos documentos refuerzan de forma transversal las restricciones ya establecidas en el proyecto:
- Ningún agente recibe texto clínico sin pasar antes por el pipeline de anonimización (`pii_pipeline`).
- Ningún agente puede declarar salidas con intención diagnóstica (bloqueado a nivel de esquema y de validación del Orquestador).
- Toda llamada al LLM pasa por un Gateway único, reemplazable, que exige el flag `anonymized: true`.
- Los logs y trazas nunca contienen contenido clínico, solo metadata técnica.

### Resultado
Se entregaron dos archivos Markdown listos para colocarse en `docs/` del repositorio:
- **`architecture.md`**
- **`manifest_schema.md`**

Ambos con referencias cruzadas entre sí y con tono técnico de ingeniería de software listo para producción, sin texto de relleno ni placeholders genéricos.

---

## 🔁 Regla de trabajo para este proyecto

> **A partir de ahora, cada vez que se genere algo nuevo en el proyecto, este archivo `Proyecto_de_IA.md` se actualiza** con un resumen de lo hecho, para mantener la bitácora completa y sincronizada con el repositorio de Git.

---

## 📌 Estado actual y próximos pasos

**Estado actual:**
- [x] Batería de 25 prompts + Prompt Maestro traducidos al inglés
- [x] Anexo de requerimientos (entrevista + RF/RNF + HU/BDD) para app de Ibagué
- [x] `architecture.md` — documentación de capas del sistema de agentes (`mi-framework-in`)
- [x] `manifest_schema.md` — especificación formal de `agents.yaml` y `skills.yaml`

**Próximos pasos posibles:**
- [ ] Definir si la app de Ibagué es parte de MindFlow AI o un proyecto paralelo relacionado
- [ ] Profundizar flujos no cubiertos (reportes institucionales, convenios, panel admin)
- [ ] Traducir el anexo al inglés para una versión bilingüe consistente
- [ ] Generar versión "solo prompts" sin el resto del documento, para copiar/pegar más rápido
- [ ] Implementar `core/manifest_validator.py` según lo especificado en `manifest_schema.md`
- [ ] Definir los manifiestos reales de `triage_agent`, `report_generation_agent` y `audit_agent` en `config/agents.yaml`

---

<div align="center">

*Bitácora generada y mantenida con ayuda de Claude — se actualiza en cada sesión de trabajo.*

</div>
