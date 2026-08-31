# MindFlow AI — Copiloto de Triaje y Análisis Emocional para Terapeutas

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Estado](https://img.shields.io/badge/Estado-En_Desarrollo-yellow)](https://github.com/EdwarIbague23/Electiva_IA-/graphs/activity)
[![Curso](https://img.shields.io/badge/UNIMINUTO-Electiva_IA_2026--2-green)](https://uniminuto.edu)
[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115.0-009688.svg)](https://fastapi.tiangolo.com/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3.15-orange.svg)](https://python.langchain.com/)
[![SpaCy](https://img.shields.io/badge/SpaCy-3.7.2-green.svg)](https://spacy.io/)
[![React](https://img.shields.io/badge/React-18.3-61DAFB.svg)](https://reactjs.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.38.0-FF5A5F.svg)](https://streamlit.io/)

---

## 📌 Visión del Proyecto
MindFlow AI es un copiloto inteligente diseñado para optimizar el análisis de notas clínicas en salud mental. Mediante modelos avanzados de Procesamiento de Lenguaje Natural (NLP), la plataforma transforma transcripciones en mapas visuales de emociones, detecta distorsiones cognitivas y sugiere enfoques para la siguiente consulta. Proyecto desarrollado para la **Electiva CPC Integración IA** (UNIMINUTO Ibagué, 2026‑2). **Esta herramienta actúa exclusivamente como apoyo analítico y no sustituye el juicio profesional.**

---

## 🎯 Alcance del MVP (Demostración Sesión 16)

| Lo que **SE DEMUESTRA** en 3 minutos | Lo que queda **EXPLÍCITAMENTE FUERA** |
| :--- | :--- |
| **Entrada:** Carga/pegado de notas clínicas o transcripción anónima de consulta. | Diagnóstico clínico automatizado o emisión de recetas médicas. |
| **Procesamiento:** Extracción en tiempo real de estados de ánimo y distorsiones cognitivas (*pensamiento todo‑o‑nada*, *catastrofismo*). | Chat en vivo de interacción directa con el paciente o terapia presencial. |
| **Salida:** Dashboard con gráfico de emociones, hallazgos clave y 3 preguntas sugeridas para la próxima sesión. | Integración con sistemas de historias clínicas complejas (EHR). |

---

## 🗺️ Matriz de Integración de IA (7 Fases del SDLC)

| Fase del Proyecto | Tarea Concreta | Herramienta Candidata | Riesgo a Vigilar |
| :--- | :--- | :--- | :--- |
| **1. Ideación y Diseño** | Definición de prompts de análisis psicológico y taxonomía de distorsiones | Claude 3.5 Sonnet / GPT‑4o | Respuestas ambiguas o diagnósticos clínicos no solicitados |
| **2. Datos / Conocimiento** | Ingestión de texto clínico y anonimización de datos personales (PII) | Python / Regex / SpaCy | Infiltración de datos personales o sensibles del paciente |
| **3. Desarrollo Core** | API de extracción de entidades emocionales y estructuración JSON | FastAPI / LangChain | Latencia en el procesamiento de textos largos |
| **4. Interfaz / UX** | Dashboard visual con gráficos de radar de emociones y métricas | v0.dev / Streamlit / React | Visualización confusa para el terapeuta |
| **5. Testing y Validación** | Pruebas con notas clínicas ficticias y casos de prueba | PyTest / GitHub Copilot | Falsos positivos en la detección de distorsiones cognitivas |
| **6. Despliegue / Ops** | Despliegue en la nube con cifrado de datos | Vercel / Render | Vulnerabilidades de privacidad/seguridad de datos de salud |
| **7. Documentación** | Guion del pitch y estructuración del README inicial | Gamma / Claude | No enfatizar el disclaimer ético de asistencia al profesional |

---

## 📂 Estructura del Repositorio

```text
mindflow-ai/
├── docs/                # Documentación del proyecto y acta de nacimiento
├── backend/             # API en Python (FastAPI + LangChain)
├── frontend/            # Interfaz de usuario (Streamlit / React)
├── prompts/             # Plantillas de prompts y taxonomía de distorsiones
├── .gitignore           # Archivos excluidos del control de versiones
└── README.md            # Descripción principal del proyecto
```

---

## 👥 Roles del Equipo

- **Product Owner / Lead AI Architect** – Edwar Ibagué  
- **Full‑Stack Developer** – (Daniel Felipe Andrade)  
- **NLP Engineer** – Nicol Sneider Murillo 
- **Frontend Developer** – Interfaz Streamlit / React  
- **QA / Tester** – Validación de prompts y casos clínicos  
- **DevOps** – Despliegue Docker, Render / Vercel  

---


## ⚠️ Disclaimer Ético

> **MindFlow AI es una herramienta de apoyo analítico para profesionales de la salud mental.**  
> - **No emite diagnósticos clínicos** ni sustituye la evaluación profesional.  
> - **No almacena datos de identificación personal (PII)** sin el consentimiento explícito del paciente y el cumplimiento de normativas locales (HIPAA, LGPD, etc.).  
> - Los resultados (emociones, distorsiones cognitivas, preguntas sugeridas) deben ser **validados y reinterpretados por el terapeuta** antes de ser incorporados a la historia clínica.  
> - El uso indebido de la herramienta para tomar decisiones médicas por cuenta propia está **estrictamente prohibido**.

---

*¿Tienes dudas? Revisa la sección de [Issues](https://github.com/EdwarIbague23/Electiva_IA-/issues) o abre un nuevo reporte.*
