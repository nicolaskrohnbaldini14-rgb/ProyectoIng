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


---

## Test 2 

### Entrada

> El sistema de reservas debe estar disponible para los usuarios prácticamente todo el tiempo y debe recuperarse rápidamente ante una falla.

### Resultado esperado

- Identificar **Disponibilidad** como atributo.
- Construir el escenario con las 6 partes.
- Detectar que faltan datos cuantitativos y proponer valores como supuestos claramente identificados.

---

## Test 3 

### Entrada

> Cuando un usuario intenta acceder a información privada de otro usuario, el sistema debe impedir el acceso y registrar el intento.

### Resultado esperado


- Completar las 6 partes del escenario.
- Diferenciar correctamente el estímulo, fuente, entorno, artefacto, respuesta y medida de respuesta.

---

## Test 4 

### Entrada

> Cuando se necesita agregar un nuevo método de pago, el cambio debería poder realizarse sin modificar el resto del sistema y debería completarse en poco tiempo.

### Resultado esperado


- Completar las 6 partes.
- Señalar qué información está incompleta.
- Proponer supuestos razonables para cuantificar el escenario.

---

## Test 5 

### Entrada

> Un usuario nuevo debe poder realizar una compra sin capacitación previa y cometer la menor cantidad posible de errores.

### Resultado esperado

- Identificar el atributo de calidad correspondiente.
- Completar las 6 partes del escenario SEI.
- No inventar información que no esté especificada; cuando falte, indicar un supuesto.
- La medida de respuesta es cuantificable.
- Existe coherencia entre estímulo y respuesta.

---

## Test 6 

### Entrada

> La aplicación debe ser rápida, segura y fácil de usar.

### Resultado esperado

- Detectar que la entrada contiene **varios atributos de calidad**.
- No generar un único escenario mezclando todo.
- Separar los atributos.
- Indicar que faltan datos para construir escenarios SEI completos.
- Proponer qué información sería necesaria para completar cada escenario.

---

## Test 7 

### Entrada

> Cuando un servidor deja de funcionar, otro servidor debe comenzar a atender las solicitudes automáticamente en un máximo de 30 segundos, sin que el usuario tenga que realizar ninguna acción.

### Resultado esperado

- La skill debe inferir el atributo correspondiente.
- No se proporciona explícitamente el nombre del atributo.
- El escenario debe contener las 6 partes.


---

## Test 8 

### Entrada

> El sistema tiene que soportar muchos usuarios al mismo tiempo sin que se vuelva lento.

### Resultado esperado

- Identificar el atributo probable.
- Indicar que "muchos usuarios" y "lento" son ambiguos.
- Proponer valores concretos como **supuestos**, no como información dada.
- Generar el escenario SEI diferenciando claramente datos originales y supuestos.


Casos de prueba — Skill 2: Validador de escenarios de atributos de calidad

Test 1 

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

Test 2 

Entrada

Atributo: Disponibilidad
Fuente del estímulo: Administrador
Estímulo: Se produce una falla en el servidor.
Entorno: Operación normal.
Artefacto: Sistema de reservas.
Respuesta: El sistema debe continuar funcionando.

Resultado esperado

Detectar que falta la medida de respuesta.

Indicar explícitamente qué parte falta.

Sugerir cómo completar la medida, por ejemplo con un porcentaje de disponibilidad o un tiempo máximo de recuperación.

No afirmar que el escenario está completo.


Test 3 

Entrada

El sistema debe ser seguro cuando un usuario intenta acceder a información privada de otro usuario.

Resultado esperado

Detectar que la descripción no contiene claramente las 6 partes.

Identificar qué información puede extraerse de la entrada.

Indicar qué partes faltan.

Sugerir información concreta para completar el escenario.

No inventar valores como si hubieran sido proporcionados por el usuario.


Test 4 

Entrada

Atributo: Performance
Fuente: Muchos usuarios
Estímulo: El sistema recibe muchas solicitudes.
Entorno: Situaciones de alta demanda.
Artefacto: Aplicación web.
Respuesta: El sistema debe ser rápido.
Medida: Debe responder rápidamente.

Resultado esperado

Detectar que varias partes son demasiado ambiguas.

Señalar especialmente la falta de una medida cuantificable.

Sugerir reemplazar expresiones como "muchas solicitudes" y "rápidamente" por valores concretos.

No considerar el escenario completo solamente porque aparecen las 6 etiquetas.

Test 5 

Entrada

Atributo: Modificabilidad
Fuente: Equipo de desarrollo.
Estímulo: Se solicita agregar un nuevo método de pago.
Entorno: Sistema en producción.
Artefacto: Módulo de pagos.
Respuesta: El nuevo método debe incorporarse sin afectar los métodos existentes.
Medida: El cambio debe implementarse en un máximo de 2 días.
Información adicional: El sistema utiliza una arquitectura modular y tiene pruebas automatizadas.

Resultado esperado

Considerar completo el escenario.

Separar las 6 partes de la información adicional.

No marcar como incompleto por contener información que no pertenece directamente a las 6 partes.



Casos de prueba — Skill 3: Generador de árbol de utilidad ATAM

Test 1 

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


Test 2 

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


Test 3 

Entrada

Sistema de reservas de vuelos.

Atributos:

Performance

Disponibilidad

Escenarios:

El sistema debe ser rápido cuando muchos usuarios realizan búsquedas.

El sistema debe funcionar siempre.

Resultado esperado

Crear el árbol de utilidad.

Identificar Performance y Disponibilidad.

Asociar cada escenario con su atributo.

Detectar que los escenarios son poco concretos o carecen de medidas cuantificables.

No inventar las medidas como si fueran datos proporcionados.


Test 4 

Entrada

Crear un árbol de utilidad para una aplicación web.

Atributo: Performance.

Escenarios:

Las búsquedas deben responder en menos de 2 segundos.

La generación de reportes debe finalizar en menos de 10 segundos.

El sistema debe soportar 5.000 usuarios concurrentes manteniendo un tiempo de respuesta menor a 3 segundos.

Otro atributo:

Seguridad: los usuarios no autorizados no deben poder acceder a información privada.

Resultado esperado

Crear el atributo Performance una sola vez.

Colocar debajo de Performance sus tres escenarios.

Crear Seguridad como otro atributo.

Colocar el escenario de acceso no autorizado bajo Seguridad.

Mantener la estructura jerárquica del árbol.


Test 5 

Entrada

Sistema de gestión universitaria.

Atributos de calidad:

Usabilidad

Seguridad

Modificabilidad

Escenarios:

Un estudiante nuevo debe poder inscribirse a una materia sin capacitación.

Un usuario sin permisos no debe poder modificar las notas.

Resultado esperado

Crear los tres atributos.

Asociar el primer escenario con Usabilidad.

Asociar el segundo escenario con Seguridad.

Detectar que Modificabilidad no tiene escenarios asociados.

Indicar que sería necesario agregar al menos un escenario para Modificabilidad si se busca evaluar ese atributo en el árbol.


Test 6 

Entrada

Una aplicación de streaming debe permitir que los usuarios reproduzcan videos sin interrupciones. Cuando aumenta mucho la cantidad de usuarios, el sistema debe continuar funcionando correctamente y las fallas deben recuperarse automáticamente.

Resultado esperado

Inferir los atributos de calidad relevantes a partir de los escenarios.

No depender exclusivamente de que el usuario proporcione el nombre del atributo.

Proponer una estructura de árbol razonable.

Explicar qué información se está infiriendo y qué información debería confirmarse.

No inventar valores cuantitativos sin marcarlos como supuestos.
