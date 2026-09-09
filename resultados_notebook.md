# Casos de Prueba Resueltos — Manual de Skills de Ingeniería de Atributos de Calidad (SEI)

Este documento contiene la resolución completa, rigurosa y formalizada de todos los casos de prueba incluidos en el archivo `casos de prueba.md`, aplicando los principios y estándares del **Software Engineering Institute (SEI)** y las tres habilidades (*Skills*) definidas en `skills.md`.

---

## 🛠️ SKILL 1: Generador de Escenarios de Atributos de Calidad SEI (6 Partes)

### 📌 Test 1
* **Entrada del Usuario:** *"El sistema debe responder las consultas de los usuarios en menos de 2 segundos durante condiciones normales de operación."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA). La frase restringe y califica el comportamiento temporal del sistema durante el procesamiento de consultas.
* **2. Clasificación del Atributo:** **Performance** (Desempeño / Tiempo de Respuesta).
* **3. Escenario de 6 Partes:**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Usuario final de la aplicación. |
| **Estímulo (*Stimulus*)** | Realiza una consulta de datos al sistema. |
| **Artefacto (*Artifact*)** | Servidor de aplicaciones / Sistema. |
| **Ambiente (*Environment*)** | Tiempo de ejecución (*runtime*), bajo condiciones normales de operación. |
| **Respuesta (*Response*)** | El sistema procesa la solicitud y devuelve el resultado esperado. |
| **Medida de Respuesta (*Response Measure*)** | Tiempo de respuesta **< 2 segundos** (Dato cuantitativo original). |

* **Observaciones / Supuestos:** Escenario completo dado por la entrada. No se requirieron supuestos adicionales ya que la medida es explícitamente cuantitativa y existe coherencia directa entre estímulo y respuesta.
  
---

### 📌 Test 2
* **Entrada del Usuario:** *"La aplicación debe ser rápida, segura y fácil de usar."*
* **1. Análisis de Naturaleza:** **Múltiples Atributos de Calidad (QA)** mezclados en un solo enunciado ambiguo.
* **2. Diagnóstico del Escenario:** La entrada es inválida para generar un único escenario SEI ya que combina **Performance**, **Seguridad** y **Usabilidad**. No se deben mezclar atributos heterogéneos.
* **3. Información Necesaria para Completar cada Escenario:**
  * **Performance ("rápida"):** Requiere definir métricas de tiempo de respuesta (ej. < 1.5s) y condiciones de carga de trabajo.
  * **Seguridad ("segura"):** Requiere definir la amenaza específica (ej. ataques de SQL injection, acceso indebido o cifrado) y la respuesta esperada.
  * **Usabilidad ("fácil de usar"):** Requiere definir perfil de usuario, tasa de éxito en tareas y tiempo máximo aceptable para aprender a usar la herramienta.

---

### 📌 Test 3
* **Entrada del Usuario:** *"Cuando un servidor deja de funcionar, otro servidor debe comenzar a atender las solicitudes automáticamente en un máximo de 30 segundos, sin que el usuario tenga que realizar ninguna acción."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA).
* **2. Clasificación del Atributo (Inferido):** **Disponibilidad** (Availability / Failover automático). *El nombre del atributo no fue provisto explícitamente y fue inferido.*
* **3. Escenario de 6 Partes:**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Falla del servidor primario de aplicaciones. |
| **Estímulo (*Stimulus*)** | Caída o interrupción completa de servicio en el nodo primario. |
| **Artefacto (*Artifact*)** | Cluster de servidores / Balanceador de carga y servidor secundario. |
| **Ambiente (*Environment*)** | Tiempo de ejecución (*runtime*). |
| **Respuesta (*Response*)** | El balanceador detecta la falla y conmuta automáticamente el tráfico entrante hacia el servidor secundario. |
| **Medida de Respuesta (*Response Measure*)** | Tiempo de conmutación (*Failover*) **<= 30 segundos**, con **0 intervención requerida** por el usuario. |

---

### 📌 Test 4
* **Entrada del Usuario:** *"El sistema tiene que soportar muchos usuarios al mismo tiempo sin que se vuelva lento."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA).
* **2. Clasificación del Atributo:** **Escalabilidad / Performance** (Rendimiento bajo alta concurrencia).
* **3. Escenario de 6 Partes (Diferenciando Datos de Supuestos):**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Múltiples usuarios finales concurrentes. |
| **Estímulo (*Stimulus*)** | Incremento masivo y simultáneo de peticiones HTTP al sistema. |
| **Artefacto (*Artifact*)** | Servidores de aplicación, base de datos y balanceadores de carga. |
| **Ambiente (*Environment*)** | Condición de carga pico en tiempo de ejecución (*runtime peak*). |
| **Respuesta (*Response*)** | El sistema atiende el tráfico manteniendo la estabilidad y procesando las solicitudes en cola. |
| **Medida de Respuesta (*Response Measure*)** | **[SUPUESTO]** Soporta **5.000 usuarios concurrentes** mantieniendo un tiempo de respuesta **<= 2.0 segundos** (percentil 95) y **0% de peticiones rechazadas**. |

* **Análisis de Ambigüedad:** Se identificó que *"muchos usuarios"* y *"sin que se vuelva lento"* son expresiones no cuantitativas y se marcaron explícitamente los valores asignados como **supuestos**.

---

## 🔍 SKILL 2: Validador y Auditor de Escenarios de Atributos de Calidad

### 📌 Test 1
* **Entrada Analizada:**
  * *Atributo:* Performance
  * *Fuente:* Usuario
  * *Estímulo:* El usuario realiza una consulta.
  * *Entorno:* Operación normal.
  * *Artefacto:* Servidor de aplicación.
  * *Respuesta:* El sistema procesa la consulta y devuelve el resultado.
  * *Medida:* El resultado debe devolverse en menos de 2 segundos.

* **1. Tabla de Auditoría de Completitud:**

| Parte del Escenario | Estado | Comentario Crítico |
| :--- | :--- | :--- |
| **Fuente** | Completo | Identifica al usuario final. |
| **Estímulo** | Completo | Describe la acción de consulta. |
| **Artefacto** | Completo | Especifica el servidor de aplicación. |
| **Ambiente** | Completo | Define operación normal en runtime. |
| **Respuesta** | Completo | Procesa y retorna la respuesta. |
| **Medida** | Completo | Métrica cuantitativa y testeable (< 2 segundos). |

* **2. Inconsistencias de Fase:** Ninguna. Coherencia total entre entorno de operación y atributo.
* **3. Dictamen Final:** **Escenario COMPLETO.** Reconoce correctamente las 6 partes, la medida es probatoria y no requiere información ni preguntas adicionales.

---


### 📌 Test 2
* **Entrada Analizada:** *"El sistema debe ser seguro cuando un usuario intenta acceder a información privada de otro usuario."*

* **1. Tabla de Auditoría de Completitud:**

| Parte del Escenario | Estado | Evaluación del Fragmento |
| :--- | :--- | :--- |
| **Fuente** | Incompleto | Inferible: Usuario no autorizado. |
| **Estímulo** | **Completo** | Extraído: Intento de acceso a información privada de otro usuario. |
| **Artefacto** | Incompleto | Sugerido: Módulo de seguridad / Base de datos. |
| **Ambiente** | Incompleto | Sugerido: Operación normal (runtime). |
| **Respuesta** | Incompleto | Sugerido: Denegar acceso e informar error de permisos. |
| **Medida** | Incompleto | Sugerido: 100% de los accesos no autorizados bloqueados. |

* **2. Propuesta de Escenario Refinado (Separando Extraído vs. Sugerido):**
  * **Fuente (Sugerida):** Usuario autenticado no autorizado.
  * **Estímulo (Extraído):** Intenta acceder a información privada perteneciente a otro usuario.
  * **Artefacto (Sugerido):** Módulo de control de accesos y seguridad.
  * **Ambiente (Sugerido):** Operación normal en tiempo de ejecución.
  * **Respuesta (Sugerida):** El sistema rechaza la solicitud y registra el evento no autorizado.
  * **Medida (Sugerida):** **100% de las solicitudes no autorizadas son bloqueadas**, con cero exposición de datos.



## 🌳 SKILL 3: Generador de Árbol de Utilidad ATAM

### 📌 Test 1
* **Entrada:** Sistema de comercio electrónico. Atributos: Performance, Disponibilidad. Escenarios:
  1. El sistema debe responder las consultas en menos de 2 segundos.
  2. El sistema debe recuperarse de una falla del servidor en menos de 30 segundos.

#### 1. Estructura del Árbol de Utilidad:
```markdown
Utility
├── Performance
│   └── Tiempo de Respuesta de Consultas
│       └── El sistema responde las consultas de catálogo y búsqueda en < 2 segundos. (Prioridad no provista - Pendiente)
└── Disponibilidad
    └── Recuperación ante Fallas
        └── El sistema se recupera de una caída del servidor en < 30 segundos. (Prioridad no provista - Pendiente)
```
* **Observación:** Se creó la raíz "Utility", se incorporaron Performance y Disponibilidad como atributos de Nivel 1 y se asociaron sus respectivos escenarios. Se advierte la falta de datos de negocio para asignar prioridades `(Importancia, Dificultad)`.

---

### 📌 Test 2
* **Entrada:** Aplicación bancaria. Atributos y Prioridades: Seguridad (Alta), Disponibilidad (Alta), Performance (Media). Escenarios provistos con sus metas.

#### 1. Estructura del Árbol de Utilidad:
```markdown
Utility
├── Seguridad
│   └── Control de Acceso
│       └── Un intento de acceso no autorizado es bloqueado en el 100% de los casos. (H, M)
├── Disponibilidad
│   └── Continuidad del Servicio
│       └── El sistema mantiene una disponibilidad operativa del 99,99% del tiempo. (H, H)
└── Performance
    └── Latencia de Consultas
        └── Las consultas de información responden en menos de 2 segundos. (M, L)

* **Observaciones:** Se estructuraron los 3 atributos respetando estrictamente las prioridades indicadas por el usuario sin modificarlas.

