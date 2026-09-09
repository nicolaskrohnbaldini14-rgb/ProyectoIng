# Casos de prueba — Generador de atributos de calidad SEI para la skill 1

## Test 1 

### Entrada

> El sistema debe responder las consultas de los usuarios en menos de 2 segundos durante condiciones normales de operación.

### Resultado esperado

- Identificar el atributo de calidad correspondiente.
- Completar las 6 partes del escenario SEI.
- No inventar información que no esté especificada; cuando falte, indicar un supuesto.
- La medida de respuesta es cuantificable.
- Existe coherencia entre estímulo y respuesta.


----

## Test 2

### Entrada

> La aplicación debe ser rápida, segura y fácil de usar.

### Resultado esperado

- Detectar que la entrada contiene **varios atributos de calidad**.
- No generar un único escenario mezclando todo.
- Separar los atributos.
- Indicar que faltan datos para construir escenarios SEI completos.
- Proponer qué información sería necesaria para completar cada escenario.

---

## Test 3

### Entrada

> Cuando un servidor deja de funcionar, otro servidor debe comenzar a atender las solicitudes automáticamente en un máximo de 30 segundos, sin que el usuario tenga que realizar ninguna acción.

### Resultado esperado

- La skill debe inferir el atributo correspondiente.
- No se proporciona explícitamente el nombre del atributo.
- El escenario debe contener las 6 partes.


---

## Test 4

### Entrada

> El sistema tiene que soportar muchos usuarios al mismo tiempo sin que se vuelva lento.

### Resultado esperado

- Identificar el atributo probable.
- Indicar que "muchos usuarios" y "lento" son ambiguos.
- Proponer valores concretos como **supuestos**, no como información dada.
- Generar el escenario SEI diferenciando claramente datos originales y supuestos.


## Casos de prueba — Skill 2: Validador de escenarios de atributos de calidad

## Test 1 

Entrada

Atributo: Performance
Fuente del estímulo: Usuario
Estímulo: El usuario realiza una consulta.
Entorno: Operación normal.
Artefacto: Servidor de aplicación.
Respuesta: El sistema procesa la consulta y devuelve el resultado.
Medida de respuesta: El resultado debe devolverse en menos de 2 segundos.

Resultado esperado

Indicar que el escenario está completo.

Reconocer las 6 partes del escenario SEI.

No solicitar información adicional.

indicar el resultado 

---


## Test 2

Entrada

El sistema debe ser seguro cuando un usuario intenta acceder a información privada de otro usuario.

Resultado esperado

Detectar que la descripción no contiene claramente las 6 partes.

Identificar qué información puede extraerse de la entrada.

Indicar qué partes faltan.

Sugerir información concreta para completar el escenario.

No inventar valores como si hubieran sido proporcionados por el usuario.



## Casos de prueba — Skill 3: Generador de árbol de utilidad ATAM

## Test 1 

Entrada

Crear un árbol de utilidad para un sistema de comercio electrónico.

Atributos prioritarios:

Performance

Disponibilidad

Escenarios:

El sistema debe responder las consultas en menos de 2 segundos.

El sistema debe recuperarse de una falla del servidor en menos de 30 segundos.

Resultado esperado

Crear una raíz correspondiente a la utilidad/calidad del sistema.

Incorporar Performance y Disponibilidad como atributos de calidad.

Asociar cada escenario con su atributo correspondiente.

Representar correctamente la jerarquía del árbol.

Priorizar los escenarios según los datos disponibles o indicar que falta información para establecer prioridad.


## Test 2 

Entrada

Construir un árbol de utilidad ATAM para una aplicación bancaria.

Atributos:

Seguridad

Disponibilidad

Performance

Escenarios:

Un intento de acceso no autorizado debe ser bloqueado siempre.

El sistema debe estar disponible el 99,99% del tiempo.

Las consultas deben responder en menos de 2 segundos.

Prioridad:

Seguridad: alta.

Disponibilidad: alta.

Performance: media.

Resultado esperado

Construir la jerarquía del árbol.

Incluir los tres atributos.

Colocar los escenarios bajo el atributo correspondiente.

Reflejar correctamente las prioridades indicadas.

No cambiar las prioridades proporcionadas.


