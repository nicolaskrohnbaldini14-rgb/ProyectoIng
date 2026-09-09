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

**Entrada:** El sistema de reservas debe estar disponible para los usuarios prácticamente todo el tiempo y debe recuperarse rápidamente ante una falla.

**Atributo de calidad:** Disponibilidad

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Sistema interno / hardware / componente externo |
| **Estímulo** | Se produce una falla |
| **Entorno** | Operación normal |
| **Artefacto** | Sistema de reservas |
| **Respuesta** | El sistema continúa funcionando / se recupera |
| **Medida de respuesta** | *No especificada* |

**Supuestos necesarios:**
- "Prácticamente todo el tiempo" → Supuesto: 99.9% de disponibilidad (máximo ~8.76 horas de downtime al año).
- "Rápidamente" → Supuesto: el sistema se recupera en un máximo de 30 segundos.
- No se aclara el tipo de falla (hardware, software, red). Se asume falla en un componente del sistema.

---

## Test 3

**Entrada:** Cuando un usuario intenta acceder a información privada de otro usuario, el sistema debe impedir el acceso y registrar el intento.

**Atributo de calidad:** Seguridad

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Usuario (potencialmente malicioso o sin permisos) |
| **Estímulo** | Intenta acceder a información privada de otro usuario |
| **Entorno** | Operación normal |
| **Artefacto** | Sistema (módulo de control de acceso) |
| **Respuesta** | El sistema impide el acceso y registra el intento |
| **Medida de respuesta** | El acceso se bloquea el 100% de las veces; el registro se completa antes de retornar la respuesta |

**Supuestos:**
- Se asume que el sistema tiene un mecanismo de autenticación y autorización.
- Se asume que el registro del intento se almacena de forma persistente (no solo en memoria).
- No se especifica qué debe contener el registro. Supuesto: usuario fuente, usuario destino, timestamp, tipo de acceso intentado.

---

## Test 4

**Entrada:** Cuando se necesita agregar un nuevo método de pago, el cambio debería poder realizarse sin modificar el resto del sistema y debería completarse en poco tiempo.

**Atributo de calidad:** Modificabilidad

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Desarrollador / equipo de desarrollo |
| **Estímulo** | Se solicita agregar un nuevo método de pago |
| **Entorno** | Desarrollo / sistema en producción |
| **Artefacto** | Módulo de pagos del sistema |
| **Respuesta** | El cambio se implementa sin afectar otros módulos |
| **Medida de respuesta** | *No especificada cuantitativamente* |

**Información incompleta:**
- "Poco tiempo" es ambiguo. **Supuesto:** el cambio se completa en un máximo de 2 días-hombre de desarrollo.
- No se especifica si el cambio se despliega en producción o solo se desarrolla. **Supuesto:** el cambio se implementa y despliega en producción.
- No se aclara si se requieren pruebas. **Supuesto:** el cambio debe pasar las pruebas automatizadas existentes sin modificaciones.

---

## Test 5

**Entrada:** Un usuario nuevo debe poder realizar una compra sin capacitación previa y cometer la menor cantidad posible de errores.

**Atributo de calidad:** Usabilidad

| Parte | Valor |
|---|---|
| **Fuente del estímulo** | Usuario nuevo (sin experiencia previa con el sistema) |
| **Estímulo** | Intenta realizar una compra |
| **Entorno** | Operación normal |
| **Artefacto** | Interfaz de usuario / sistema de compras |
| **Respuesta** | El usuario completa el proceso de compra |
| **Medida de respuesta** | *No especificada cuantitativamente* |

**Supuestos necesarios:**
- "Menor cantidad posible de errores" → **Supuesto:** el usuario comete como máximo 1 error en el proceso de compra.
- No se especifica un tiempo máximo. **Supuesto:** el usuario completa la compra en menos de 5 minutos.
- No se define qué es "capacitación previa". **Supuesto:** el usuario no ha recibido instrucciones ni tutorial; accede por primera vez al sistema.

---

## Test 6

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

## Test 7

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

## Test 8

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

**Entrada:**

| Parte | Valor |
|---|---|
| Atributo | Disponibilidad |
| Fuente del estímulo | Administrador |
| Estímulo | Se produce una falla en el servidor |
| Entorno | Operación normal |
| Artefacto | Sistema de reservas |
| Respuesta | El sistema debe continuar funcionando |
| Medida de respuesta | **(NO PRESENTE)** |

**Resultado: El escenario está INCOMPLETO.**

**Parte faltante:** Medida de respuesta.

**Observación adicional:** La fuente del estímulo es "Administrador", lo cual es inusual para una falla de disponibilidad. Normalmente la fuente sería un componente del sistema, hardware o un evento externo. Podría considerarse válido si la falla es provocada por una acción del administrador (ej: mantenimiento), pero en ese caso el entorno debería indicarlo.

**Sugerencia para completar la medida de respuesta:**
- "El sistema debe recuperarse y estar disponible nuevamente en un máximo de 30 segundos."
- O bien: "El sistema debe mantener al menos el 99.9% de disponibilidad anual."

---

## Test 3

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

---

## Test 4

**Entrada:**

| Parte | Valor |
|---|---|
| Atributo | Performance |
| Fuente | Muchos usuarios |
| Estímulo | El sistema recibe muchas solicitudes |
| Entorno | Situaciones de alta demanda |
| Artefacto | Aplicación web |
| Respuesta | El sistema debe ser rápido |
| Medida | Debe responder rápidamente |

**Resultado: El escenario es DEFICIENTE, aunque aparecen las 6 etiquetas.**

No se considera completo solo porque las 6 etiquetas estén presentes. **Problemas detectados:**

| Parte | Problema |
|---|---|
| Fuente | "Muchos usuarios" es ambiguo. ¿Cuántos? |
| Estímulo | "Muchas solicitudes" es ambiguo. ¿Qué tipo de solicitudes? ¿Cuántas por segundo? |
| Respuesta | "El sistema debe ser rápido" no es una respuesta descriptiva. ¿Qué acción realiza el sistema? |
| Medida | "Debe responder rápidamente" **no es cuantificable**. No define un valor concreto. |

**Sugerencias de mejora:**
- Fuente: "5.000 usuarios concurrentes"
- Estímulo: "Realizan consultas simultáneas al sistema"
- Respuesta: "El sistema procesa cada consulta y devuelve el resultado"
- Medida: "El 95% de las respuestas se devuelven en menos de 2 segundos"

---

## Test 5

**Entrada:**

| Parte | Valor |
|---|---|
| Atributo | Modificabilidad |
| Fuente | Equipo de desarrollo |
| Estímulo | Se solicita agregar un nuevo método de pago |
| Entorno | Sistema en producción |
| Artefacto | Módulo de pagos |
| Respuesta | El nuevo método debe incorporarse sin afectar los métodos existentes |
| Medida | El cambio debe implementarse en un máximo de 2 días |
| Info adicional | El sistema utiliza una arquitectura modular y tiene pruebas automatizadas |

**Resultado: El escenario está COMPLETO.**

Las 6 partes del escenario SEI están correctamente definidas y la medida es cuantificable (máximo 2 días).

**La información adicional** (arquitectura modular y pruebas automatizadas) **se separa correctamente de las 6 partes** del escenario. Esta información es contexto valioso para evaluar la viabilidad del escenario, pero no forma parte de la estructura SEI. No se marca como incompleto por contener esta información extra.

---

---

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

---

## Test 3

**Entrada:** Sistema de reservas de vuelos.
- Atributos: Performance, Disponibilidad
- Escenarios: (1) "rápido cuando muchos usuarios realizan búsquedas", (2) "funcionar siempre"

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Performance
│   └── S1: El sistema debe ser rápido cuando muchos usuarios realizan búsquedas
└── Disponibilidad
    └── S2: El sistema debe funcionar siempre
```

**Observaciones:**
- **S1** carece de medida cuantificable. "Rápido" y "muchos usuarios" son ambiguos. **No se inventan medidas**, pero se señala que sería necesario definir: ¿cuántos usuarios concurrentes? ¿Tiempo máximo de respuesta?
- **S2** carece de medida cuantificable. "Siempre" no es medible. **No se inventa un porcentaje**, pero se señala que sería necesario definir: ¿qué nivel de disponibilidad se espera (99.9%, 99.99%, 100%)?

---

## Test 4

**Entrada:** Aplicación web.
- Performance con 3 escenarios + Seguridad con 1 escenario

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Performance
│   ├── S1: Las búsquedas deben responder en menos de 2 segundos
│   ├── S2: La generación de reportes debe finalizar en menos de 10 segundos
│   └── S3: El sistema debe soportar 5.000 usuarios concurrentes con tiempo de respuesta < 3 segundos
└── Seguridad
    └── S4: Los usuarios no autorizados no deben poder acceder a información privada
```

**Verificaciones:**
- Performance aparece **una sola vez** como nodo del árbol.
- Los 3 escenarios de Performance están agrupados bajo ese atributo.
- Seguridad es un nodo separado.
- El escenario de acceso no autorizado está bajo Seguridad.
- La estructura jerárquica es correcta.

---

## Test 5

**Entrada:** Sistema de gestión universitaria.
- Atributos: Usabilidad, Seguridad, Modificabilidad
- Escenarios: (1) Inscripción sin capacitación → Usabilidad, (2) Sin permisos no puede modificar notas → Seguridad

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Usabilidad
│   └── S1: Un estudiante nuevo debe poder inscribirse a una materia sin capacitación
├── Seguridad
│   └── S2: Un usuario sin permisos no debe poder modificar las notas
└── Modificabilidad
    └── (SIN ESCENARIOS ASOCIADOS)
```

**Observaciones:**
- Usabilidad y Seguridad tienen sus escenarios correctamente asociados.
- **Modificabilidad no tiene escenarios asociados.** Se detecta y se indica que es necesario agregar al menos un escenario para Modificabilidad si se desea evaluar ese atributo en el árbol de utilidad. Ejemplo de escenario sugerido: "Cuando se necesita agregar una nueva carrera, el cambio debe completarse sin modificar otros módulos del sistema en un máximo de 3 días."

---

## Test 6

**Entrada:** Una aplicación de streaming debe permitir que los usuarios reproduzcan videos sin interrupciones. Cuando aumenta mucho la cantidad de usuarios, el sistema debe continuar funcionando correctamente y las fallas deben recuperarse automáticamente.

**Análisis:** No se proporcionan nombres de atributos explícitamente. Se infieren a partir de los escenarios.

**Atributos inferidos:**
- "Reproducir videos sin interrupciones" → **Performance** (en concreto, calidad de servicio / rendimiento bajo carga)
- "Continuar funcionando correctamente cuando aumentan los usuarios" → **Escalabilidad / Capacidad**
- "Las fallas deben recuperarse automáticamente" → **Disponibilidad** (tolerancia a fallos)

**Árbol de utilidad:**

```
Utilidad / Calidad del Sistema
├── Performance
│   └── S1: Los usuarios deben poder reproducir videos sin interrupciones
│         (inf: durante sesiones normales de uso)
├── Escalabilidad
│   └── S2: El sistema debe continuar funcionando correctamente cuando aumenta
│         la cantidad de usuarios concurrentes
└── Disponibilidad
    └── S3: Las fallas deben recuperarse automáticamente
```

**Información inferida vs. información que debería confirmarse:**
- Se infiere que "sin interrupciones" implica bitrate estable y sin buffering. **Debería confirmarse** qué calidad de video se espera (HD, 4K) y cuántos usuarios simultáneos.
- Se infiere que "muchos usuarios" se refiere a un incremento significativo sobre la carga normal. **Debería confirmarse** el número concreto.
- Se infiere que la recuperación automática implica failover sin intervención humana. **Debería confirmarse** el tiempo máximo de recuperación.

**No se inventan valores cuantitativos sin marcarlos como supuestos.**
