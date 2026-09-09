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
* **Entrada del Usuario:** *"El sistema de reservas debe estar disponible para los usuarios prácticamente todo el tiempo y debe recuperarse rápidamente ante una falla."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA). Califica la continuidad operacional y la resiliencia del sistema.
* **2. Clasificación del Atributo:** **Disponibilidad** (Availability / Resiliencia).
* **3. Escenario de 6 Partes (con Supuestos):**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Falla interna de componente (hardware, red o excepción de software). |
| **Estímulo (*Stimulus*)** | Ocurrencia de un fallo de sistema / Caída del servicio. |
| **Artefacto (*Artifact*)** | Sistema de reservas. |
| **Ambiente (*Environment*)** | Tiempo de ejecución (*runtime*), bajo operación normal. |
| **Respuesta (*Response*)** | El sistema activa la conmutación por error (*failover*) o reinicia el servicio afectado para restablecer la operación. |
| **Medida de Respuesta (*Response Measure*)** | **[SUPUESTO]** Disponibilidad operacional del **99.9%** (Uptime anual) y tiempo de recuperación (**MTTR < 30 segundos**). |

* **Detección de Datos Faltantes y Supuestos:** Las expresiones *"prácticamente todo el tiempo"* y *"rápidamente"* son cualitativas e ambiguas. Se establecieron supuestos cuantitativos concretos (99.9% y < 30s) para hacer testeable el escenario.

---

### 📌 Test 3
* **Entrada del Usuario:** *"Cuando un usuario intenta acceder a información privada de otro usuario, el sistema debe impedir el acceso y registrar el intento."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA). Define restricciones de acceso, confidencialidad y auditabilidad.
* **2. Clasificación del Atributo:** **Seguridad** (Security / Control de Acceso y Auditoría).
* **3. Escenario de 6 Partes:**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Usuario autenticado no autorizado (o atacante interno). |
| **Estímulo (*Stimulus*)** | Intento no autorizado de lectura/acceso a información de carácter privado pertenecientes a otro usuario. |
| **Artefacto (*Artifact*)** | Módulo de autenticación/autorización y servicio de logs de auditoría. |
| **Ambiente (*Environment*)** | Tiempo de ejecución (*runtime*), en operación normal. |
| **Respuesta (*Response*)** | El sistema deniega el acceso (retorna error de acceso prohibido) y genera un registro de auditoría con la marca de tiempo e identificador de usuario. |
| **Medida de Respuesta (*Response Measure*)** | **[SUPUESTO]** **100% de los intentos no autorizados son bloqueados** (0% de fuga de datos) y la entrada de registro se almacena en el log en **< 100 milisegundos**. |

* **Observaciones:** Se diferenció claramente el estímulo (intento de acceso) de la respuesta (bloqueo y registro) y se definió la medida cuantitativa.

---

### 📌 Test 4
* **Entrada del Usuario:** *"Cuando se necesita agregar un nuevo método de pago, el cambio debería poder realizarse sin modificar el resto del sistema y debería completarse en poco tiempo."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA). Evalúa la facilidad y costo de modificar la arquitectura de software.
* **2. Clasificación del Atributo:** **Modificabilidad** (Modifiability / Extensibilidad).
* **3. Escenario de 6 Partes:**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Desarrollador de software / Equipo de TI. |
| **Estímulo (*Stimulus*)** | Solicitud de incorporación de un nuevo método o pasarela de pago en el sistema. |
| **Artefacto (*Artifact*)** | Módulo de integración de pagos / Capa de procesamiento de pagos. |
| **Ambiente (*Environment*)** | Tiempo de desarrollo / diseño (*design & build time*). |
| **Respuesta (*Response*)** | Se programa e integra la nueva pasarela mediante componentes modulares (ej. Patrón *Adapter*) sin alterar el código existente. |
| **Medida de Respuesta (*Response Measure*)** | **[SUPUESTO]** Esfuerzo de implementación **<= 2 personas-día**, afectando a **1 solo módulo local** y con **0% de fallos de regresión** en los métodos existentes. |

* **Detección de Datos Faltantes:** Expresiones como *"sin modificar el resto del sistema"* y *"poco tiempo"* fueron cuantificadas mediante supuestos de esfuerzo (personas-día) y alcance de módulos modificados.

---

### 📌 Test 5
* **Entrada del Usuario:** *"Un usuario nuevo debe poder realizar una compra sin capacitación previa y cometer la menor cantidad posible de errores."*
* **1. Análisis de Naturaleza (F vs. QA):** Atributo de Calidad (QA). Califica la facilidad de uso y tasa de errores de la interfaz.
* **2. Clasificación del Atributo:** **Usabilidad** (Usability / Aprendibilidad y Tolerancia a Errores).
* **3. Escenario de 6 Partes:**

| Parte del Escenario | Definición Formal |
| :--- | :--- |
| **Fuente (*Source*)** | Usuario nuevo (sin capacitación ni experiencia previa en la plataforma). |
| **Estímulo (*Stimulus*)** | Intenta realizar la compra de un producto en la plataforma. |
| **Artefacto (*Artifact*)** | Interfaz de Usuario (UI) y Flujo de Checkout del sistema. |
| **Ambiente (*Environment*)** | Tiempo de ejecución (*runtime*), operación normal. |
| **Respuesta (*Response*)** | La interfaz presenta un flujo intuitivo, validaciones en tiempo real y guías explícitas paso a paso. |
| **Medida de Respuesta (*Response Measure*)** | **[SUPUESTO]** **>= 90% de los usuarios nuevos** completan la compra al primer intento sin asistencia, con un promedio de **< 1 error por transacción** y en un tiempo total **< 3 minutos**. |

---

### 📌 Test 6
* **Entrada del Usuario:** *"La aplicación debe ser rápida, segura y fácil de usar."*
* **1. Análisis de Naturaleza:** **Múltiples Atributos de Calidad (QA)** mezclados en un solo enunciado ambiguo.
* **2. Diagnóstico del Escenario:** La entrada es inválida para generar un único escenario SEI ya que combina **Performance**, **Seguridad** y **Usabilidad**. No se deben mezclar atributos heterogéneos.
* **3. Información Necesaria para Completar cada Escenario:**
  * **Performance ("rápida"):** Requiere definir métricas de tiempo de respuesta (ej. < 1.5s) y condiciones de carga de trabajo.
  * **Seguridad ("segura"):** Requiere definir la amenaza específica (ej. ataques de SQL injection, acceso indebido o cifrado) y la respuesta esperada.
  * **Usabilidad ("fácil de usar"):** Requiere definir perfil de usuario, tasa de éxito en tareas y tiempo máximo aceptable para aprender a usar la herramienta.

---

### 📌 Test 7
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

### 📌 Test 8
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
* **Entrada Analizada:**
  * *Atributo:* Disponibilidad
  * *Fuente:* Administrador
  * *Estímulo:* Se produce una falla en el servidor.
  * *Entorno:* Operación normal.
  * *Artefacto:* Sistema de reservas.
  * *Respuesta:* El sistema debe continuar funcionando.

* **1. Tabla de Auditoría de Completitud:**

| Parte del Escenario | Estado | Comentario Crítico |
| :--- | :--- | :--- |
| **Fuente** | Completo | Especifica al administrador. |
| **Estímulo** | Completo | Evento de falla en el servidor. |
| **Artefacto** | Completo | Sistema de reservas. |
| **Ambiente** | Completo | Operación normal. |
| **Respuesta** | Completo | Continuidad del funcionamiento. |
| **Medida** | **FALTANTE** | **No se proporciona ninguna medida de respuesta.** |

* **2. Dictamen Final:** **Escenario INCOMPLETO.** Falta la Medida de Respuesta.
* **3. Guía para Completar la Medida:** Se sugiere añadir un valor cuantitativo de recuperación como: *"El sistema restablece el servicio en un tiempo máximo de recuperación (MTTR) < 45 segundos, alcanzando una disponibilidad del 99.9%."*

---

### 📌 Test 3
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

---

### 📌 Test 4
* **Entrada Analizada:**
  * *Atributo:* Performance
  * *Fuente:* Muchos usuarios
  * *Estímulo:* El sistema recibe muchas solicitudes.
  * *Entorno:* Situaciones de alta demanda.
  * *Artefacto:* Aplicación web.
  * *Respuesta:* El sistema debe ser rápido.
  * *Medida:* Debe responder rápidamente.

* **1. Tabla de Auditoría de Completitud:**

| Parte del Escenario | Estado | Comentario Crítico |
| :--- | :--- | :--- |
| **Fuente** | Ambiguo | "Muchos usuarios" no especifica cantidad. |
| **Estímulo** | Ambiguo | "Muchas solicitudes" carece de tasa numérica. |
| **Artefacto** | Completo | Aplicación web. |
| **Ambiente** | Completo | Alta demanda. |
| **Respuesta** | Ambiguo | "Debe ser rápido" no indica la acción técnica. |
| **Medida** | **INVÁLIDO** | **"Rápidamente" es cualitativo y no testeable.** |

* **2. Dictamen Final:** **Escenario INCOMPLETO / AMBIGUO.** El uso de etiquetas no valida un escenario si los contenidos son imprecisos.
* **3. Sugerencia de Reemplazo:** Reemplazar *"muchas solicitudes"* por **10.000 req/seg** y *"rápidamente"* por **tiempo de respuesta < 500 ms**.

---

### 📌 Test 5
* **Entrada Analizada:**
  * *Atributo:* Modificabilidad
  * *Fuente:* Equipo de desarrollo.
  * *Estímulo:* Se solicita agregar un nuevo método de pago.
  * *Entorno:* Sistema en producción / Tiempo de desarrollo.
  * *Artefacto:* Módulo de pagos.
  * *Respuesta:* El nuevo método debe incorporarse sin afectar los métodos existentes.
  * *Medida:* El cambio debe implementarse en un máximo de 2 días.
  * *Información adicional:* El sistema utiliza una arquitectura modular y tiene pruebas automatizadas.

* **1. Tabla de Auditoría de Completitud:**
  * El escenario contiene las 6 partes con una medida totalmente cuantitativa (**máximo de 2 días**).
  * La presencia de datos adicionales de arquitectura (*arquitectura modular y pruebas automatizadas*) enriquece el contexto sin invalidar el formato.
* **2. Dictamen Final:** **Escenario COMPLETO.** La información contextual adicional se separa formalmente de las 6 partes principales.

---

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
```
* **Observaciones:** Se estructuraron los 3 atributos respetando estrictamente las prioridades indicadas por el usuario sin modificarlas.

---

### 📌 Test 3
* **Entrada:** Sistema de reservas de vuelos. Atributos: Performance, Disponibilidad. Escenarios:
  1. El sistema debe ser rápido cuando muchos usuarios realizan búsquedas.
  2. El sistema debe funcionar siempre.

#### 1. Estructura del Árbol de Utilidad y Alertas de Calidad:
```markdown
Utility
├── Performance
│   └── Búsquedas bajo Carga
│       └── El sistema procesa búsquedas cuando hay alta concurrencia de usuarios. [Alerta: Poco concreto / Sin métrica] (M, M)
└── Disponibilidad
    └── Continuidad Operativa
        └── El sistema funciona de manera ininterrumpida. [Alerta: Poco concreto / Sin métrica] (H, H)
```
* **Observación Crítica:** Los escenarios fueron agrupados correctamente bajo sus atributos, pero se identificó y reportó explícitamente que carecen de medidas cuantitativas. Se evitó inventar números ficticios presentándolos como si hubiesen sido proporcionados por el usuario.

---

### 📌 Test 4
* **Entrada:** Aplicación web. Atributo: Performance (Búsquedas < 2s; Reportes < 10s; 5.000 usuarios concurrentes < 3s). Atributo: Seguridad (Usuarios no autorizados no acceden a información privada).

#### 1. Estructura del Árbol de Utilidad:
```markdown
Utility
├── Performance
│   ├── Latencia de Búsqueda
│   │   └── Las búsquedas simples responden en menos de 2 segundos. (M, L)
│   ├── Generación de Reportes
│   │   └── La generación de reportes complejos finaliza en menos de 10 segundos. (M, M)
│   └── Alta Concurrencia
│       └── El sistema soporta 5.000 usuarios concurrentes con tiempos de respuesta < 3 segundos. (H, H)
└── Seguridad
    └── Confidencialidad de Datos
        └── Los usuarios no autorizados no pueden acceder a información privada de otros usuarios. (H, M)
```
* **Observación de Jerarquía:** El atributo **Performance** se creó una única vez en el Nivel 1 del árbol, colgando de él sus tres escenarios correspondientes.

---

### 📌 Test 5
* **Entrada:** Sistema de gestión universitaria. Atributos: Usabilidad, Seguridad, Modificabilidad. Escenarios:
  1. Un estudiante nuevo debe poder inscribirse a una materia sin capacitación.
  2. Un usuario sin permisos no debe poder modificar las notas.

#### 1. Estructura del Árbol de Utilidad:
```markdown
Utility
├── Usabilidad
│   └── Autogestión de Inscripciones
│       └── Un estudiante nuevo se inscribe a una materia sin capacitación previa y sin cometer errores. (H, M)
├── Seguridad
│   └── Integridad de Calificaciones
│       └── Un usuario sin permisos no puede modificar las notas registradas en el sistema. (H, H)
└── Modificabilidad
    └── [SIN ESCENARIOS ASOCIADOS]
        └── ⚠️ ALERTA ATAM: No se proporcionó ningún escenario para el atributo Modificabilidad. Se requiere agregar al menos un escenario concreto de cambio o evolución para evaluar este atributo en el árbol.
```

---

### 📌 Test 6
* **Entrada:** Aplicación de streaming. *"Debe permitir que los usuarios reproduzcan videos sin interrupciones. Cuando aumenta mucho la cantidad de usuarios, el sistema debe continuar funcionando correctamente y las fallas deben recuperarse automáticamente."*

#### 1. Estructura del Árbol de Utilidad (Inferida a partir de la entrada):
```markdown
Utility
├── Disponibilidad
│   ├── Calidad de Reproducción (Streaming continuo)
│   │   └── Los usuarios reproducen video sin interrupciones ni pausas de bufferización. [Inferido - Requiere definir % máx de re-buffering] (H, H)
│   └── Auto-recuperación de Fallas
│       └── Las fallas de nodos de transmisión se recuperan automáticamente sin degradación perceptible. [Inferido - Requiere definir MTTR] (H, M)
└── Escalabilidad / Performance
    └── Carga Masiva Concurrentes
        └── Cuando aumenta la cantidad de usuarios, el sistema mantiene el servicio activo. [Inferido - Requiere definir volumen de usuarios] (H, H)
```

#### 2. Explicación de Inferencias:
* Se dedujeron los atributos de **Disponibilidad** (por reproducción sin interrupción y auto-recuperación) y **Escalabilidad/Performance** (por incremento de usuarios).
* Se marcó de forma transparente que las métricas cuantitativas deben ser confirmadas por los *stakeholders* en el taller ATAM.
