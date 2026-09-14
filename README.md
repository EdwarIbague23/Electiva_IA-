
# MindFlow AI — Copiloto de Triaje y Análisis Emocional para Terapeutas

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Estado](https://img.shields.io/badge/Estado-En_Desarrollo-yellow)](https://github.com/EdwarIbague23/Electiva_IA-/graphs/activity)
[![Curso](https://img.shields.io/badge/UNIMINUTO-Electiva_IA_2026--2-green)](https://uniminuto.edu)
[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115.0-009688.svg)](https://fastapi.tiangolo.com/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3.15-orange.svg)](https://python.langchain.com/)
[![SpaCy](https://img.shields.io/badge/SpaCy-3.7.2-green.svg)](https://spacy.io/)
[![React](https://img.shields.io/badge/React-18.3-61DAFB.svg)](https://reactjs.org/)

---

## 📌 Visión del Proyecto
**MindFlow AI** es un framework y copiloto inteligente diseñado para optimizar el análisis de notas clínicas en salud mental y triaje emocional. Mediante modelos avanzados de Procesamiento de Lenguaje Natural (NLP), la plataforma transforma transcripciones en mapas visuales de emociones, detecta distorsiones cognitivas y sugiere enfoques terapéuticos. Proyecto desarrollado para la **Electiva CPC Integración IA** (UNIMINUTO Ibagué, 2026‑2). **Esta herramienta actúa exclusivamente como apoyo analítico y no sustituye el juicio profesional.**

---

## 🎯 Alcance del MVP

| Lo que **SE DEMUESTRA** en el MVP | Lo que queda **EXPLÍCITAMENTE FUERA** |
| :--- | :--- |
| **Entrada:** Carga/pegado de notas clínicas o transcripción anónima de consulta. | Diagnóstico clínico automatizado o emisión de recetas médicas. |
| **Procesamiento:** Extracción en tiempo real de estados de ánimo y distorsiones cognitivas (*pensamiento todo‑o‑nada*, *catastrofismo*). | Chat en vivo de interacción directa con el paciente o terapia presencial. |
| **Salida:** Dashboard con gráfico de emociones, hallazgos clave y preguntas sugeridas para la próxima sesión. | Integración con sistemas complejos de historias clínicas (EHR). |

---

## 🗂️ Estructura del Repositorio (`mi-framework-ia`)

El proyecto está organizado bajo una arquitectura modular y escalable de framework de IA:

```text
mi-framework-ia/
├── agents/              # Definición de agentes especializados y lógica de ejecución
├── config/              # Configuraciones del framework
│   ├── environments/    # Variables de entorno y ajustes por ambiente
│   ├── agents.yaml      # Manifiesto de configuración de agentes
│   └── skills.yaml      # Manifiesto de configuración de habilidades
├── core/                # Núcleo del framework (orquestador, gestión de memoria, LLM gateway)
├── docs/                # Documentación técnica (architecture.md, manifest_schema.md)
├── evaluations/         # Pruebas de rendimiento, precisión y casos de validación
├── interfaces/          # Capas de presentación y puntos de entrada (API / Frontend)
├── skills/              # Habilidades modulares atómicas
│   ├── code_executor/   # Ejecución segura de código
│   ├── db_query/        # Consultas estructuradas
│   ├── document_generator/ # Generación de reportes clínicos
│   └── web_search/      # Búsqueda y recuperación de información externa
├── tools/               # Utilidades externas e integraciones
│   ├── github_client.py # Cliente para automatización y control de versiones
│   └── slack_client.py  # Cliente de notificaciones y alertas
├── .gitignore           # Archivos excluidos del control de versiones
├── Proyecto_MindFlow_AI.pdf # Documento oficial del proyecto técnico
└── README.md            # Descripción principal del proyecto
