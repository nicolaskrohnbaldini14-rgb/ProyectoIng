# Informe de Diseño de Skills Arquitectónicas (SEI) 


## 1. Contexto y Objetivos
El objetivo principal de este trabajo fue desarrollar un conjunto de asistentes basados en Inteligencia Artificial (llamados **Skills**) especializados en metodologías del **Software Engineering Institute (SEI)** para la definición, auditoría y priorización de atributos de calidad de software. 

Las tres skills diseñadas son:
1. **Generador de Escenarios SEI (6 partes):** Traduce requerimientos informales del usuario en escenarios de calidad estructurados formalmente bajo el estándar de 6 partes del SEI, incluyendo análisis de conflictos y tradeoffs de diseño.
2. **Auditor y Complementador de Escenarios:** Realiza una validación binaria de completitud, detecta inconsistencias conceptuales graves (como la fase del ambiente respecto al atributo de calidad) y genera preguntas de elicitación basadas en QAW para poder completar la información faltante.
3. **Constructor de Árbol de Utilidad (ATAM):** Estructura jerárquicamente las metas de calidad y de negocio del sistema, priorizando los escenarios finales utilizando la matriz bidimensional estándar del SEI.

**ACLARACIÓN:** Es necesario solicitar en el prompt que se prueben las 3 skills para el escenario. 

---

## 2. Bibliografía y Fuentes de Grounding
Las skills fueron validadas utilizando estrictamente el material teórico y práctico provisto en la cátedra:
* **"Software Architecture in Practice (4th Edition)"** (Bass, Clements, Kazman): Fuente de referencia para las taxonomías oficiales de los atributos de calidad (Disponibilidad, Modificabilidad, Performance, Seguridad, Usabilidad) y las definiciones de escenarios de 6 partes.
* **"clase5-diseño-atributos-calidad.pdf"**: Diapositivas de soporte con foco en las mecánicas de elicitación de escenarios, diferencias clave entre escalabilidad y otros atributos, y talleres de diseño colaborativo (QAW).
* **"TP3-diseno.pdf" (Consigna Oficial)**: Base para estructurar el alcance de las tareas i, ii y iii, y marco para el análisis del sistema funcional vs. atributos de calidad.

---

## 3. Metodología de Desarrollo y Refinamiento
El proceso de diseño de prompts se realizó de forma iterativa:
1. **Estructuración Teórica:** Se tradujeron las reglas de negocio y arquitectónicas de la bibliografía en instrucciones de sistema rígidas (System Prompts).
2. **Definición de Roles:** Se asignaron identidades de agentes expertos (p. ej. *Auditor de Arquitectura y Especialista en Evaluaciones ATAM*) para condicionar el tono y rigor técnico de la IA.
3. **Correción de asistente:** Mediante la comparación y la lectura profunda de las skills arrojadas, se las refinó en inexactitudes técnicas y fallas en el modelo generadas por ambigüedad y por decisiones autónomas de los agentes.

---

## 4. Agentes de IA Utilizados para la Prueba y Validación
Para evaluar la robustez, consistencia y portabilidad de las tres Skills, se realizaron diversas pruebas utilizando los siguientes agentes de Inteligencia Artificial:

Claude 
OpenCode 
NotebookLM 

Los casos de prueba utilizados se encuentran documentados en el archivo test.md. Para cada Skill se definieron diversos ejemplos correspondientes a los distintos atributos de calidad evaluados en la materia, con el objetivo de comprobar que las Skills fueran capaces de identificar y procesar correctamente cada uno de ellos.

Asimismo, en los archivos resultados_claude, resultados_notebook y resultados_opencode se pueden observar las respuestas obtenidas por cada agente de IA a partir de las Skills y los casos de prueba correspondientes.

A modo de ejemplo, y con el objetivo de mostrar el comportamiento de los distintos agentes frente a un mismo escenario, se presentan a continuación los resultados obtenidos para la Skill 2, utilizando como referencia el ejercicio 2b del Trabajo Práctico N.º 3.
<img width="609" height="458" alt="claude" src="https://github.com/user-attachments/assets/efbfcae7-17bc-428f-b2d7-ba2805b19052" />


### B. Open Code (Modelos Abiertos / Locales)
<img width="781" height="480" alt="opencode" src="https://github.com/user-attachments/assets/05694c07-d6ac-48ba-9d85-e71cabf9cfaf" />


### C. Gemini Notebook (Google)
<img width="1216" height="345" alt="notebooklm" src="https://github.com/user-attachments/assets/c4412293-79f5-4c72-ae8a-0ce7756b252b" />

---


