# Resolución de casos de prueba — Skills de Atributos de Calidad (SEI/ATAM)

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

--

## Test 2

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

## Test 3

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

## Test 4

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


