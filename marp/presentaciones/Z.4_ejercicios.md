---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'IA - Parte 4' -->

# <!-- fit --> Ejercicios con IA
## Práctica guiada de prompting
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Objetivo' -->

# ¿Qué vamos a hacer?

**Practicar el uso de IA como herramienta de aprendizaje**

* Formular buenos prompts
* Comparar respuestas de diferentes LLMs
* Verificar y cuestionar las respuestas
* Aprender a iterar y mejorar

**Herramientas sugeridas:**
* ChatGPT (OpenAI)
* Claude (Anthropic)
* Gemini (Google)

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 1
## Comparar explicaciones

---

<!-- _header: 'Ejercicio 1' -->

# Mismo prompt, diferentes LLMs

**Prompt a usar:**
```
Soy estudiante de primer año de programación.
Explicame qué es una variable en Python.
Usá una analogía simple y un ejemplo de código.
```

**Tu tarea:**
1. Enviá este prompt a ChatGPT
2. Enviá el mismo prompt a Claude
3. Enviá el mismo prompt a Gemini

---

<!-- _header: 'Ejercicio 1' -->

# Analizá las respuestas

**Compará:**
* ¿Qué analogía usa cada uno?
* ¿Qué ejemplo de código dan?
* ¿Cuál te resultó más claro?
* ¿Alguno tiene errores?

**Pregunta reflexiva:**
¿Por qué las respuestas son diferentes si el prompt fue el mismo?

---

<!-- _header: 'Ejercicio 1' -->

# Registro de respuestas

| Aspecto | ChatGPT | Claude | Gemini |
|:--------|:--------|:-------|:-------|
| Analogía usada | | | |
| Ejemplo de código | | | |
| Claridad (1-5) | | | |
| ¿Errores? | | | |

**Completá esta tabla con tus observaciones**

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 2
## Mejorar un prompt malo

---

<!-- _header: 'Ejercicio 2' -->

# Prompt inicial (malo)

**Enviá este prompt:**
```
explicame los loops
```

**Observá la respuesta:**
* ¿Es útil?
* ¿Es específica para Python?
* ¿Sabés qué nivel asume?

---

<!-- _header: 'Ejercicio 2' -->

# Mejorá el prompt

**Agregá:**
1. **Contexto:** Tu nivel, qué estás estudiando
2. **Especificidad:** ¿Qué tipo de loops?
3. **Formato:** ¿Cómo querés la explicación?
4. **Restricciones:** ¿Qué evitar?

**Ejemplo mejorado:**
```
Soy principiante en Python (curso de ingreso).
Explicame la diferencia entre while y for.
Usá ejemplos simples con números del 1 al 5.
Explicá paso a paso qué hace cada línea.
No uses conceptos avanzados.
```

---

<!-- _header: 'Ejercicio 2' -->

# Compará los resultados

**Antes (prompt malo):**
* Respuesta vaga/genérica
* Quizás mezcla lenguajes
* Nivel inadecuado

**Después (prompt mejorado):**
* Respuesta específica
* Ejemplos claros
* Nivel apropiado

**Conclusión:**
Mejor prompt → mejor respuesta

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 3
## Verificar código de IA

---

<!-- _header: 'Ejercicio 3' -->

# Pedí código a la IA

**Prompt:**
```
Escribí una función en Python que reciba
una lista de números y devuelva la suma
de los números pares. Explicá cada línea.
```

**Cuando recibas el código:**
1. Leé cada línea
2. ¿Entendés todo?
3. Copialo a Python y ejecutalo

---

<!-- _header: 'Ejercicio 3' -->

# Casos de prueba

**Probá con estos datos:**

```python
# Caso 1: Lista normal
suma_pares([1, 2, 3, 4, 5, 6])  # Esperado: 12

# Caso 2: Lista vacía
suma_pares([])  # Esperado: 0

# Caso 3: Solo impares
suma_pares([1, 3, 5, 7])  # Esperado: 0

# Caso 4: Números negativos
suma_pares([-2, -4, 3])  # Esperado: -6

# Caso 5: Un solo elemento
suma_pares([4])  # Esperado: 4
```

---

<!-- _header: 'Ejercicio 3' -->

# Checklist de verificación

**Marcá lo que verificaste:**

- [ ] ¿El código funciona con lista normal?
- [ ] ¿Maneja lista vacía sin error?
- [ ] ¿Funciona con números negativos?
- [ ] ¿Tiene nombre descriptivo?
- [ ] ¿Tiene docstring o comentarios?
- [ ] ¿Entendés cada línea?

**Si alguno falla:** Pedí a la IA que corrija

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 4
## Iterar con la IA

---

<!-- _header: 'Ejercicio 4' -->

# Conversación iterativa

**Prompt inicial:**
```
Explicame qué es una lista en Python.
```

**Después de la respuesta, seguí preguntando:**
```
¿Cómo agrego un elemento al final?
```

```
¿Y si quiero agregar varios elementos?
```

```
¿Cuál es la diferencia entre append y extend?
```

---

<!-- _header: 'Ejercicio 4' -->

# Profundizá con preguntas

**Preguntas de seguimiento útiles:**

* "¿Podés darme un ejemplo más simple?"
* "¿Qué pasa si hago X en vez de Y?"
* "¿Por qué usaste esa forma y no otra?"
* "¿Hay algún caso donde esto falle?"
* "¿Cómo verifico que entendí bien?"

**La IA recuerda el contexto de la conversación**

---

<!-- _header: 'Ejercicio 4' -->

# Registrá tu aprendizaje

**Al final de la conversación:**

1. ¿Qué conceptos nuevos aprendiste?
2. ¿Qué ejemplos te resultaron útiles?
3. ¿Alguna respuesta te confundió?
4. ¿Pudiste aclarar las dudas?

**Tip:** Guardá las conversaciones útiles

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 5
## Detectar errores de IA

---

<!-- _header: 'Ejercicio 5' -->

# Pedí algo que puede fallar

**Prompt (intencionalmente ambiguo):**
```
Dame código para ordenar una lista.
```

**Analizá la respuesta:**
* ¿Ordena ascendente o descendente?
* ¿Modifica la lista original o crea una nueva?
* ¿Funciona con cualquier tipo de dato?

---

<!-- _header: 'Ejercicio 5' -->

# Identificá problemas comunes

**Cosas que la IA puede hacer mal:**

1. **Asumir cosas no dichas**
   * "Seguro quiere orden ascendente"

2. **Usar funciones que no existen**
   * `lista.ordenar()` ← No existe en Python

3. **Mezclar versiones**
   * Usar f-strings en ejemplo "compatible con Python 2"

4. **Dar código sin explicar**
   * Funciona pero no entendés por qué

---

<!-- _header: 'Ejercicio 5' -->

# Corregí y mejorá

**Si encontrás un error:**

```
Tu código tiene un problema: [descripción].
¿Podés corregirlo y explicar por qué
la versión anterior estaba mal?
```

**Esto te ayuda a:**
* Verificar que entendés el error
* Ver cómo la IA se autocorrige
* Aprender de los errores

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 6
## Crear tu propia explicación

---

<!-- _header: 'Ejercicio 6' -->

# De receptor a creador

**Paso 1:** Pedí a la IA que explique `if-elif-else`

**Paso 2:** Leé y entendé la explicación

**Paso 3:** Escribí TU PROPIA explicación
* Con tus palabras
* Con tus ejemplos
* Como si le explicaras a un compañero

---

<!-- _header: 'Ejercicio 6' -->

# Compará tu explicación

**Paso 4:** Pedí a la IA que evalúe tu explicación

```
Escribí esta explicación de if-elif-else para
un compañero principiante. ¿Es correcta?
¿Qué puedo mejorar?

[Pegá tu explicación aquí]
```

**Esto verifica que realmente entendiste**

---

<!-- _header: 'Ejercicio 6' -->

# ¿Por qué este ejercicio?

**Objetivo:** Transformar conocimiento pasivo en activo

* **Pasivo:** Leer y entender explicación de IA
* **Activo:** Crear tu propia explicación

**Si podés explicarlo, lo entendés**

**Si no podés explicarlo, volvé a estudiar**

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio Integrador
## Resolver un problema completo

---

<!-- _header: 'Ejercicio integrador' -->

# El problema

**Crear un programa que:**
1. Pida al usuario N números
2. Calcule el promedio
3. Muestre cuántos están arriba del promedio
4. Muestre cuántos están abajo del promedio

**NO pidas el código completo a la IA**

---

<!-- _header: 'Ejercicio integrador' -->

# Usá la IA estratégicamente

**Preguntas permitidas:**
* "¿Cómo pido varios números al usuario?"
* "¿Cómo calculo el promedio de una lista?"
* "¿Cómo cuento elementos que cumplen condición?"

**NO permitido:**
* "Haceme el programa completo"
* "Resolvé este problema por mí"

---

<!-- _header: 'Ejercicio integrador' -->

# Proceso recomendado

1. **Diseñá el algoritmo** (pseudocódigo)
2. **Identificá qué no sabés**
3. **Preguntá puntualmente** a la IA
4. **Integrá las respuestas** en tu código
5. **Probá con casos** de prueba
6. **Verificá** que funciona

---

<!-- _header: 'Ejercicio integrador' -->

# Autoevaluación

**Al terminar, preguntate:**

- [ ] ¿Puedo explicar cada línea de mi código?
- [ ] ¿Usé la IA para aprender o para copiar?
- [ ] ¿Podría resolver algo similar sin IA?
- [ ] ¿Qué conceptos reforcé?
- [ ] ¿Qué me falta practicar más?

---

<!-- _class: inverse -->

# <!-- fit --> Resumen
## Buenas prácticas con IA

---

<!-- _header: 'Resumen' -->

# Lo que aprendimos

**Prompting:**
* Dar contexto y ser específico
* Pedir formato y nivel apropiado
* Iterar y profundizar

**Verificación:**
* Siempre probar el código
* Cuestionar las respuestas
* Comparar con documentación oficial

---

<!-- _header: 'Resumen' -->

# Uso responsable

**La IA es herramienta, no muleta**

* **Usala para aprender**, no para copiar
* **Verificá siempre** las respuestas
* **Experimentá** con el código
* **Explicá** lo que aprendiste

**Si no podés explicarlo, no lo entendés**

---

<!-- _header: 'Próximos pasos' -->

# Seguí practicando

**En cada tema nuevo:**
1. Intentá primero sin IA
2. Si te trabás, preguntá puntualmente
3. Verificá las respuestas
4. Creá tu propia explicación

**La práctica hace al maestro**

---

<!-- _class: centered -->

# ¿Preguntas?
