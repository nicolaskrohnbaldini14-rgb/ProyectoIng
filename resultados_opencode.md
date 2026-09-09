# Casos de prueba resueltos — Skills de atributos de calidad

---

# SKILL 1: Generador de atributos de calidad SEI

---

## Test 1

**Entrada:** El sistema debe responder las consultas de los usuarios en menos de 2 segundos durante condiciones normales de operación.

**Atributo de calidad:** Performance (Rendimiento)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Usuario del sistema |
| **Estímulo** | Realiza una consulta |
| **Entorno** | Operación normal |
| **Artefacto** | Sistema (componente que procesa la consulta) |
| **Respuesta** | El sistema procesa la consulta y devuelve el resultado |
| **Medida de respuesta** | El resultado se devuelve en menos de 2 segundos |

**Supuestos:** Se asume que "condiciones normales de operación" implica un volumen de usuarios dentro de la capacidad nominal del sistema. No se especifica qué tipo de consulta, se asume que aplica a consultas genéricas.

---

## Test 2

**Entrada:** La aplicación debe ser rápida, segura y fácil de usar.

**Análisis:** Esta entrada contiene **tres atributos de calidad distintos**. No se debe generar un único escenario mezclándolos.

### Atributo 1: Performance (rápida)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | *Falta* |
| **Estímulo** | *Falta* |
| **Entorno** | *Falta* |
| **Artefacto** | Aplicación |
| **Respuesta** | *Falta* |
| **Medida de respuesta** | *Falta* |

**Información necesaria:** ¿Quién realiza la acción? ¿Qué operación debe ser rápida? ¿Bajo qué condiciones? ¿Cuánto tiempo se considera "rápido"?

### Atributo 2: Seguridad (segura)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | *Falta* |
| **Estímulo** | *Falta* |
| **Entorno** | *Falta* |
| **Artefacto** | Aplicación |
| **Respuesta** | *Falta* |
| **Medida de respuesta** | *Falta* |

**Información necesaria:** ¿Qué amenaza se debe mitigar? ¿Qué datos se protegen? ¿Qué tipo de ataque se debe prevenir?

### Atributo 3: Usabilidad (fácil de usar)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | *Falta* |
| **Estímulo** | *Falta* |
| **Entorno** | *Falta* |
| **Artefacto** | Aplicación |
| **Respuesta** | *Falta* |
| **Medida de respuesta** | *Falta* |

**Información necesaria:** ¿Qué tipo de usuario? ¿Qué tarea debe realizar? ¿Cuántos errores son aceptables? ¿En cuánto tiempo debe completarse la tarea?

---

## Test 3

**Entrada:** Cuando un servidor deja de funcionar, otro servidor debe comenzar a atender las solicitudes automáticamente en un máximo de 30 segundos, sin que el usuario tenga que realizar ninguna acción.

**Atributo de calidad inferido:** Disponibilidad (tolerancia a fallos / failover)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Componente interno (servidor que falla) |
| **Estímulo** | Un servidor deja de funcionar |
| **Entorno** | Operación normal (sistema desplegado en un entorno con múltiples servidores) |
| **Artefacto** | Sistema de servidores / infraestructura |
| **Respuesta** | Otro servidor comienza a atender las solicitudes automáticamente |
| **Medida de respuesta** | El failover se completa en un máximo de 30 segundos; el usuario no realiza ninguna acción |

**Nota:** El atributo no se menciona explícitamente en la entrada, pero se infiere claramente como **Disponibilidad** (más específicamente, tolerancia a fallos con failover automático).

---

## Test 4

**Entrada:** El sistema tiene que soportar muchos usuarios al mismo tiempo sin que se vuelva lento.

**Atributo de calidad inferido:** Capacidad (bajo la categoría de Performance) o Scalability (Escalabilidad)

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Usuarios simultáneos |
| **Estímulo** | Realizan solicitudes al mismo tiempo |
| **Entorno** | Operación normal / alta demanda |
| **Artefacto** | Sistema |
| **Respuesta** | El sistema procesa todas las solicitudes manteniendo tiempos de respuesta aceptables |
| **Medida de respuesta** | *Ambigua* |

**Ambigüedades detectadas:**
- "Muchos usuarios" → **Supuesto:** 10.000 usuarios concurrentes.
- "Lento" → **Supuesto:** tiempo de respuesta mayor a 3 segundos se considera lento.

**Escenario con supuestos:**

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | 10.000 usuarios concurrentes *(supuesto)* |
| **Estímulo** | Realizan solicitudes simultáneas al sistema |
| **Entorno** | Operación normal con alta demanda |
| **Artefacto** | Sistema |
| **Respuesta** | El sistema procesa todas las solicitudes |
| **Medida de respuesta** | El tiempo de respuesta se mantiene por debajo de 3 segundos *(supuesto)* para el 95% de las solicitudes |

---

---

# SKILL 2: Validador de escenarios de atributos de calidad

---

## Test 1

**Entrada:**

| Parte | Valor |
|---|---|
| Atributo | Performance |
| Fuente del estímulo | Usuario |
| Estímulo | El usuario realiza una consulta |
| Entorno | Operación normal |
| Artefacto | Servidor de aplicación |
| Respuesta | El sistema procesa la consulta y devuelve el resultado |
| Medida de respuesta | El resultado debe devolverse en menos de 2 segundos |

**Resultado: El escenario está COMPLETO.**

Las 6 partes del escenario SEI están presentes y correctamente definidas. La medida de respuesta es cuantificable (< 2 segundos). El estímulo es coherente con la respuesta. No se solicita información adicional.

---

## Test 2

**Entrada:** El sistema debe ser seguro cuando un usuario intenta acceder a información privada de otro usuario.

**Resultado: El escenario está INCOMPLETO.**

La entrada es una descripción informal, no un escenario SEI estructurado. **No contiene las 6 partes claramente diferenciadas.**

**Información que puede extraerse:**

| Parte | Valor inferido |
|---|---|
| Atributo | Seguridad |
| Estímulo | Un usuario intenta acceder a información privada de otro usuario |
| Artefacto | Sistema (implícito) |

**Partes que faltan:**

| Parte faltante | Sugerencia |
|---|---|
| Fuente del estímulo | El usuario que intenta el acceso no autorizado |
| Entorno | Operación normal (o producción) |
| Respuesta | El sistema debe bloquear el acceso y registrar el intento |
| Medida de respuesta | El acceso se bloquea el 100% de las veces; el intento se registra con timestamp y detalles |

**No se inventan valores como si hubieran sido proporcionados por el usuario.** Las sugerencias son claramente identificadas como propuestas para completar el escenario.



# SKILL 3: Generador de árbol de utilidad ATAM

---

## Test 1

**Entrada:** Sistema de comercio electrónico.
- Atributos: Performance, Disponibilidad
- Escenarios: (1) Consultas en < 2s, (2) Recuperación de falla en < 30s

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Performance
│   └── S1: El sistema debe responder las consultas en menos de 2 segundos
└── Disponibilidad
    └── S2: El sistema debe recuperarse de una falla del servidor en menos de 30 segundos
```

**Priorización:** No se proporciona información suficiente para establecer prioridad relativa entre los escenarios. Se recomienda solicitar al stakeholder qué atributo es más crítico para el negocio.

---

## Test 2

**Entrada:** Aplicación bancaria.
- Atributos: Seguridad, Disponibilidad, Performance
- Prioridad: Seguridad (alta), Disponibilidad (alta), Performance (media)

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Seguridad [Prioridad: ALTA]
│   └── S1: Un intento de acceso no autorizado debe ser bloqueado siempre
├── Disponibilidad [Prioridad: ALTA]
│   └── S2: El sistema debe estar disponible el 99,99% del tiempo
└── Performance [Prioridad: MEDIA]
    └── S3: Las consultas deben responder en menos de 2 segundos
```

Las prioridades se reflejan tal cual fueron proporcionadas. No se modifican.

