# Resolución de casos de prueba — Skills de Atributos de Calidad (SEI/ATAM)

> **Nota:** `skills.md` no pudo leerse (el archivo subido era una página de error 503 del servidor de origen, no la definición de las skills). Las resoluciones siguientes se basan en el comportamiento descrito implícitamente en `casos_de_prueba.md` para cada skill:
> - **Skill 1:** genera un escenario SEI de 6 partes a partir de un requisito en lenguaje natural, identificando el atributo de calidad y marcando explícitamente los supuestos.
> - **Skill 2:** valida si un escenario SEI (dado en cualquier formato) está completo, coherente y cuantificable, sin inventar datos.
> - **Skill 3:** construye un árbol de utilidad ATAM a partir de atributos y escenarios, respetando prioridades dadas.

---

# Skill 1 — Generador de atributos de calidad SEI

## Test 1

**Entrada:** *"El sistema debe responder las consultas de los usuarios en menos de 2 segundos durante condiciones normales de operación."*

**Atributo de calidad identificado:** Performance (Rendimiento)

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Usuario | Dado |
| Estímulo | El usuario envía una consulta al sistema | Dado |
| Entorno | Condiciones normales de operación | Dado |
| Artefacto | Sistema (no se especifica módulo o componente) | **Supuesto** |
| Respuesta | El sistema procesa la consulta y devuelve el resultado | **Supuesto** (inferido, no explicitado) |
| Medida de respuesta | En menos de 2 segundos | Dado |

**Supuestos declarados:**
- Se asume que "el sistema" refiere al servidor/backend de aplicación, ya que no se especifica el artefacto exacto.
- Se infiere que la respuesta consiste en "procesar y devolver el resultado", porque el enunciado solo da la medida de tiempo, no describe la acción.

**Coherencia estímulo–respuesta:** Sí — el estímulo (consulta) tiene una respuesta directamente asociada (procesamiento y devolución del resultado) y la medida es cuantificable (2 segundos).

---

## Test 2

**Entrada:** *"El sistema de reservas debe estar disponible para los usuarios prácticamente todo el tiempo y debe recuperarse rápidamente ante una falla."*

**Atributo de calidad identificado:** Disponibilidad

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Falla de hardware o software del servidor | **Supuesto** |
| Estímulo | Se produce una falla en el sistema | **Supuesto** (no se especifica el tipo de falla) |
| Entorno | Operación normal | **Supuesto** |
| Artefacto | Sistema de reservas | Dado |
| Respuesta | El sistema detecta la falla y se recupera, continuando el servicio a los usuarios | Dado (parcial) |
| Medida de respuesta | Disponibilidad del **99,9%** del tiempo; recuperación en menos de **60 segundos** | **Supuesto** (cuantificación de "prácticamente todo el tiempo" y "rápidamente") |

**Datos faltantes detectados:** el enunciado no cuantifica "prácticamente todo el tiempo" ni "rápidamente"; se proponen valores típicos de referencia como supuestos, claramente marcados, no como datos dados por el usuario.

---

## Test 3

**Entrada:** *"Cuando un usuario intenta acceder a información privada de otro usuario, el sistema debe impedir el acceso y registrar el intento."*

**Atributo de calidad identificado:** Seguridad

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Usuario no autorizado | Dado (implícito) |
| Estímulo | Intento de acceso a información privada de otro usuario | Dado |
| Entorno | Operación normal | **Supuesto** |
| Artefacto | Sistema / módulo de control de acceso | **Supuesto** |
| Respuesta | El sistema impide el acceso y registra el intento | Dado |
| Medida de respuesta | El 100% de los intentos no autorizados son bloqueados y registrados de forma inmediata | **Supuesto** |

**Diferenciación:**
- **Estímulo:** intento de acceso indebido.
- **Fuente:** el usuario que realiza el intento.
- **Entorno:** contexto de operación en que ocurre.
- **Artefacto:** componente del sistema que recibe el estímulo (control de acceso).
- **Respuesta:** acciones del sistema (bloquear + registrar).
- **Medida de respuesta:** grado de cumplimiento cuantificado (100%, inmediato).

---

## Test 4

**Entrada:** *"Cuando se necesita agregar un nuevo método de pago, el cambio debería poder realizarse sin modificar el resto del sistema y debería completarse en poco tiempo."*

**Atributo de calidad identificado:** Modificabilidad

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Equipo de desarrollo | **Supuesto** |
| Estímulo | Solicitud de agregar un nuevo método de pago | Dado |
| Entorno | Sistema en desarrollo o producción | **Supuesto** |
| Artefacto | Módulo de pagos | **Supuesto** (inferido del contexto) |
| Respuesta | El nuevo método se incorpora sin afectar otros módulos del sistema | Dado (parcial) |
| Medida de respuesta | El cambio no requiere modificar archivos fuera del módulo de pagos y se completa en un máximo de **3 días-persona** | **Supuesto** (cuantificación de "sin modificar el resto" y "poco tiempo") |

**Información incompleta señalada:** no se indica en qué entorno se realiza el cambio, ni el artefacto exacto, ni qué se considera "poco tiempo"; todos estos puntos requieren confirmación del usuario.

---

## Test 5

**Entrada:** *"Un usuario nuevo debe poder realizar una compra sin capacitación previa y cometer la menor cantidad posible de errores."*

**Atributo de calidad identificado:** Usabilidad

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Usuario nuevo (sin experiencia previa) | Dado |
| Estímulo | Intenta realizar una compra sin capacitación previa | Dado |
| Entorno | Primer uso del sistema | **Supuesto** |
| Artefacto | Interfaz de usuario / flujo de compra | **Supuesto** |
| Respuesta | El usuario completa la compra guiado por la interfaz, cometiendo pocos errores | Dado (parcial) |
| Medida de respuesta | Completa la compra en menos de **5 minutos**, con **máximo 1 error** durante el proceso | **Supuesto** (cuantificación de "la menor cantidad posible de errores") |

**Coherencia:** el estímulo (usuario sin capacitación) se corresponde con una respuesta de usabilidad (bajo esfuerzo/errores), y la medida propuesta es cuantificable.

---

## Test 6

**Entrada:** *"La aplicación debe ser rápida, segura y fácil de usar."*

**Detección:** la entrada mezcla **tres atributos de calidad distintos**: Performance, Seguridad y Usabilidad. No se genera un único escenario combinado; se separan y se indica, para cada uno, qué falta para completar el escenario SEI.

### Performance ("rápida")
- Dado: ninguna de las 6 partes está explícita.
- Falta: fuente del estímulo, tipo de estímulo (¿qué operación debe ser rápida?), entorno, artefacto, y sobre todo una medida cuantificable de "rápida" (ej. tiempo de respuesta en segundos).
- Información necesaria: ¿qué operación se evalúa? ¿bajo qué carga? ¿cuál es el tiempo máximo aceptable?

### Seguridad ("segura")
- Dado: ninguna de las 6 partes está explícita.
- Falta: qué tipo de amenaza o estímulo se contempla (acceso no autorizado, ataque, fuga de datos), artefacto afectado, y medida de respuesta cuantificable.
- Información necesaria: ¿contra qué tipo de amenaza? ¿qué se considera una respuesta exitosa (bloqueo, cifrado, registro)?

### Usabilidad ("fácil de usar")
- Dado: ninguna de las 6 partes está explícita.
- Falta: perfil del usuario, tarea concreta, entorno, y medida cuantificable (tiempo, cantidad de errores, pasos).
- Información necesaria: ¿qué tarea debe poder realizar el usuario? ¿con qué nivel de experiencia? ¿qué se mide (tiempo, errores, satisfacción)?

**Conclusión:** no es posible construir escenarios SEI completos con la información dada; se requiere una entrada específica por atributo.

---

## Test 7

**Entrada:** *"Cuando un servidor deja de funcionar, otro servidor debe comenzar a atender las solicitudes automáticamente en un máximo de 30 segundos, sin que el usuario tenga que realizar ninguna acción."*

**Atributo de calidad inferido:** Disponibilidad *(no se nombra explícitamente; se infiere del patrón de falla + recuperación automática típico de este atributo)*

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Falla de hardware/software en un servidor | Dado (implícito) |
| Estímulo | Un servidor deja de funcionar | Dado |
| Entorno | Operación normal | **Supuesto** |
| Artefacto | Clúster de servidores / sistema | **Supuesto** |
| Respuesta | Otro servidor asume automáticamente el procesamiento de las solicitudes (failover), sin intervención del usuario | Dado |
| Medida de respuesta | En un máximo de 30 segundos | Dado |

---

## Test 8

**Entrada:** *"El sistema tiene que soportar muchos usuarios al mismo tiempo sin que se vuelva lento."*

**Atributo de calidad identificado:** Performance (con componente de escalabilidad)

**Ambigüedades detectadas:** "muchos usuarios" y "lento" son términos ambiguos, no cuantificados en la entrada.

| Parte | Contenido | Origen |
|---|---|---|
| Fuente del estímulo | Múltiples usuarios concurrentes | Dado (ambiguo) |
| Estímulo | Los usuarios realizan solicitudes simultáneamente | Dado (implícito) |
| Entorno | Condiciones de alta demanda | **Supuesto** |
| Artefacto | Servidor de aplicaciones | **Supuesto** |
| Respuesta | El sistema procesa las solicitudes manteniendo el nivel de servicio | Dado (parcial) |
| Medida de respuesta | Soporta **10.000 usuarios concurrentes** con tiempo de respuesta **menor a 3 segundos** en el percentil 95 | **Supuesto** (cuantificación de "muchos" y "lento") |

**Nota:** los valores numéricos (10.000 usuarios, 3 segundos) son supuestos propuestos como referencia, no datos provistos por el usuario.

---

# Skill 2 — Validador de escenarios de atributos de calidad

## Test 1

**Entrada:** escenario completo con las 6 partes (Performance, respuesta < 2 segundos).

**Resultado:**
- **Estado: COMPLETO.**
- Las 6 partes del escenario SEI están presentes: fuente (Usuario), estímulo (consulta), entorno (operación normal), artefacto (servidor de aplicación), respuesta (procesa y devuelve resultado), medida de respuesta (< 2 segundos).
- La medida de respuesta es cuantificable y coherente con el estímulo.
- No se requiere información adicional.

---

## Test 2

**Entrada:** escenario de Disponibilidad sin medida de respuesta.

**Resultado:**
- **Estado: INCOMPLETO.**
- Falta la parte: **Medida de respuesta.**
- El resto de las partes está presente y es coherente (fuente: Administrador; estímulo: falla del servidor; entorno: operación normal; artefacto: sistema de reservas; respuesta: continuar funcionando).
- **Sugerencia para completar:** cuantificar mediante, por ejemplo, un porcentaje de disponibilidad objetivo (p. ej. 99,9%) o un tiempo máximo de recuperación (p. ej. menos de 60 segundos).
- No se afirma que el escenario esté completo hasta que se agregue esta medida.

---

## Test 3

**Entrada:** *"El sistema debe ser seguro cuando un usuario intenta acceder a información privada de otro usuario."* (texto libre, sin las 6 partes etiquetadas)

**Resultado:**
- **Estado: INCOMPLETO — formato no estructurado.**
- Información que puede extraerse de la entrada:
  - Estímulo: intento de acceso a información privada de otro usuario.
  - Fuente (implícita): usuario que realiza el intento.
- Partes que faltan explícitamente:
  - Entorno.
  - Artefacto (¿qué componente del sistema recibe el estímulo?).
  - Respuesta (¿qué debe hacer el sistema exactamente: bloquear, registrar, notificar?).
  - Medida de respuesta (¿con qué grado de efectividad o en qué tiempo?).
- **Sugerencia:** solicitar al usuario que especifique el componente afectado, la acción esperada del sistema y un criterio cuantificable (p. ej. "bloquear el 100% de los accesos no autorizados y registrar el intento en menos de 1 segundo").
- No se inventan valores como si hubieran sido provistos.

---

## Test 4

**Entrada:** escenario de Performance con las 6 etiquetas presentes pero con contenido ambiguo ("muchas solicitudes", "rápidamente").

**Resultado:**
- **Estado: INCOMPLETO pese a tener las 6 etiquetas.**
- Partes ambiguas detectadas:
  - Fuente: "Muchos usuarios" — no cuantificado.
  - Estímulo: "El sistema recibe muchas solicitudes" — no cuantificado.
  - Respuesta / Medida: "debe ser rápido" / "debe responder rápidamente" — no es una medida cuantificable, es una repetición de la respuesta.
- **Falta especialmente:** una medida de respuesta cuantificable real (tiempo máximo, percentil, throughput).
- **Sugerencia:** reemplazar "muchas solicitudes" por un número concreto (p. ej. 1.000 solicitudes/segundo) y "rápidamente" por un tiempo máximo (p. ej. menos de 2 segundos).
- **Conclusión:** tener las 6 etiquetas presentes no implica que el escenario esté completo; el contenido debe ser específico y medible.

---

## Test 5

**Entrada:** escenario de Modificabilidad completo, con un campo adicional "Información adicional" fuera de las 6 partes.

**Resultado:**
- **Estado: COMPLETO.**
- Las 6 partes están presentes y son coherentes: fuente (equipo de desarrollo), estímulo (agregar método de pago), entorno (sistema en producción), artefacto (módulo de pagos), respuesta (incorporar sin afectar otros métodos), medida (máximo 2 días).
- El campo "Información adicional" (arquitectura modular, pruebas automatizadas) **no forma parte de las 6 partes del escenario SEI**; se registra como contexto complementario, pero no afecta la evaluación de completitud.
- No se marca como incompleto por la presencia de esta información extra.

---

# Skill 3 — Generador de árbol de utilidad ATAM

## Test 1 — Sistema de comercio electrónico

```
Utilidad del sistema (Comercio electrónico)
├── Performance
│   └── El sistema debe responder las consultas en menos de 2 segundos.
│       [Prioridad: no especificada — falta información para priorizar]
└── Disponibilidad
    └── El sistema debe recuperarse de una falla del servidor en menos de 30 segundos.
        [Prioridad: no especificada — falta información para priorizar]
```
**Nota:** ambos atributos y escenarios fueron incorporados correctamente bajo la raíz de utilidad. No se proveyeron datos de prioridad (impacto de negocio / riesgo técnico), por lo que se indica explícitamente que falta esa información en lugar de asignar prioridades arbitrarias.

---

## Test 2 — Aplicación bancaria

```
Utilidad del sistema (Aplicación bancaria)
├── Seguridad [Prioridad: Alta]
│   └── Un intento de acceso no autorizado debe ser bloqueado siempre.
├── Disponibilidad [Prioridad: Alta]
│   └── El sistema debe estar disponible el 99,99% del tiempo.
└── Performance [Prioridad: Media]
    └── Las consultas deben responder en menos de 2 segundos.
```
Las prioridades indicadas por el usuario (Seguridad: alta, Disponibilidad: alta, Performance: media) se mantienen tal cual, sin modificarlas.

---

## Test 3 — Sistema de reservas de vuelos

```
Utilidad del sistema (Reservas de vuelos)
├── Performance
│   └── El sistema debe ser rápido cuando muchos usuarios realizan búsquedas.
│       [⚠ Escenario poco concreto: no define una medida cuantificable
│        ni cuántos usuarios se consideran "muchos". No se inventa un valor.]
└── Disponibilidad
    └── El sistema debe funcionar siempre.
        [⚠ Escenario poco concreto: "siempre" no está cuantificado
         (ej. % de disponibilidad). No se inventa un valor.]
```
Ambos atributos y escenarios fueron asociados correctamente, pero se señala que los escenarios carecen de medidas cuantificables reales y se recomienda solicitarlas al usuario antes de usarlos en una evaluación ATAM formal.

---

## Test 4 — Aplicación web

```
Utilidad del sistema (Aplicación web)
├── Performance
│   ├── Las búsquedas deben responder en menos de 2 segundos.
│   ├── La generación de reportes debe finalizar en menos de 10 segundos.
│   └── El sistema debe soportar 5.000 usuarios concurrentes manteniendo
│       un tiempo de respuesta menor a 3 segundos.
└── Seguridad
    └── Los usuarios no autorizados no deben poder acceder a información privada.
```
Performance se creó una única vez, con sus tres escenarios agrupados debajo. Seguridad se agregó como atributo independiente, con su escenario correspondiente.

---

## Test 5 — Sistema de gestión universitaria

```
Utilidad del sistema (Gestión universitaria)
├── Usabilidad
│   └── Un estudiante nuevo debe poder inscribirse a una materia sin capacitación.
├── Seguridad
│   └── Un usuario sin permisos no debe poder modificar las notas.
└── Modificabilidad
    └── (sin escenarios asociados)
        [⚠ Se recomienda agregar al menos un escenario para poder
         evaluar Modificabilidad dentro del árbol de utilidad.]
```

---

## Test 6 — Aplicación de streaming

**Entrada en texto libre, sin atributos ni escenarios etiquetados explícitamente.**

**Atributos inferidos a partir del texto** *(inferencia, a confirmar con el usuario)*:
- **Performance** — inferido de "reproduzcan videos sin interrupciones".
- **Escalabilidad / Performance bajo carga** — inferido de "cuando aumenta mucho la cantidad de usuarios... continuar funcionando correctamente".
- **Disponibilidad** — inferido de "las fallas deben recuperarse automáticamente".

```
Utilidad del sistema (Aplicación de streaming)
├── Performance
│   └── Los usuarios deben poder reproducir videos sin interrupciones.
│       [Inferido del texto; falta una medida cuantificable, ej. % de
│        buffering o tiempo de carga inicial.]
├── Performance / Escalabilidad
│   └── El sistema debe seguir funcionando correctamente ante un aumento
│       importante de usuarios.
│       [Inferido; "aumenta mucho" no está cuantificado — no se asume
│        un número de usuarios sin marcarlo como supuesto.]
└── Disponibilidad
    └── Las fallas deben recuperarse automáticamente.
        [Inferido; falta un tiempo máximo de recuperación.]
```
**Aclaración:** los tres atributos y sus escenarios fueron inferidos del texto, ya que el usuario no los nombró explícitamente. Se recomienda confirmar con el usuario: (1) si la agrupación Performance/Escalabilidad es correcta o deben separarse, y (2) las medidas cuantitativas faltantes en cada escenario, ninguna de las cuales fue inventada.
