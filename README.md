# Informe de Diseño de Skills Arquitectónicas (SEI) - TP3 Consigna 4


## 1. Contexto y Objetivos
El objetivo principal de este trabajo fue desarrollar un conjunto de asistentes basados en Inteligencia Artificial (llamados **Skills**) especializados en metodologías del **Software Engineering Institute (SEI)** para la definición, auditoría y priorización de atributos de calidad de software. 

Las tres skills diseñadas son:
1. **Generador de Escenarios SEI (6 partes):** Traduce requerimientos informales del usuario en escenarios de calidad estructurados formalmente bajo el estándar de 6 partes del SEI, incluyendo análisis de conflictos y tradeoffs de diseño.
2. **Auditor y Complementador de Escenarios:** Realiza una validación binaria de completitud, detecta inconsistencias conceptuales graves (como la fase del ambiente respecto al atributo de calidad) y genera preguntas de elicitación basadas en QAW para completar la información faltante.
3. **Constructor de Árbol de Utilidad (ATAM):** Estructura jerárquicamente las metas de calidad y de negocio del sistema, priorizando los escenarios finales utilizando la matriz bidimensional estándar del SEI `(Importancia para el negocio, Dificultad de implementación)`.

**ACLARACIÓN:** Es necesario solicitar que se prueben las 3 skills para el escenario.

---

## 2. Bibliografía y Fuentes de Grounding
Las skills fueron calibradas y validadas utilizando estrictamente el material teórico y práctico provisto en la cátedra:
* **"Software Architecture in Practice (4th Edition)"** (Bass, Clements, Kazman): Fuente de referencia para las taxonomías oficiales de los atributos de calidad (Disponibilidad, Modificabilidad, Performance, Seguridad, Usabilidad), las tácticas de diseño de arquitectura y las definiciones de escenarios de 6 partes.
* **"clase5-diseño-atributos-calidad.pdf"**: Diapositivas de soporte con foco en las mecánicas de elicitación de escenarios, diferencias clave entre escalabilidad y otros atributos, y talleres de diseño colaborativo (QAW).
* **"TP3-diseno.pdf" (Consigna Oficial)**: Base para estructurar el alcance de las tareas i, ii y iii, y marco para el análisis del sistema funcional vs. atributos de calidad.

---

## 3. Metodología de Desarrollo y Refinamiento
El proceso de diseño de prompts se realizó de forma iterativa:
1. **Estructuración Teórica:** Se tradujeron las reglas de negocio y arquitectónicas de la bibliografía en instrucciones de sistema rígidas (System Prompts).
2. **Definición de Roles:** Se asignaron identidades de agentes expertos (p. ej. *Auditor de Arquitectura y Especialista en Evaluaciones ATAM*) para condicionar el tono y rigor técnico de la IA.
3. **Guardrails y Reglas de Validación:** Se introdujeron validaciones explícitas en las instrucciones para evitar errores recurrentes de los alumnos, como confundir un escenario de modificabilidad en tiempo de diseño con uno de tiempo de ejecución (operación).

---

## 4. Agentes de IA Utilizados para la Prueba y Validación
Para evaluar la robustez, consistencia y portabilidad de las tres *skills*, se ejecutaron pruebas de estrés con los siguientes agentes de IA:

### A. Claude (Anthropic)

### B. Open Code (Modelos Abiertos / Locales)

### C. Gemini Notebook (Google)

---


