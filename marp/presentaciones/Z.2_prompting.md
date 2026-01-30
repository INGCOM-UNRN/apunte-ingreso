---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'IA - Parte 2/3' -->

# <!-- fit --> Prompting Efectivo
## Cómo preguntar a la IA
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Prompting' -->

# El arte de preguntar

**Prompt = instrucción a la IA**

**Prompt malo:**
```
"dame codigo"
```

**Prompt bueno:**
```
"Necesito una función en Python que valide
si un email tiene formato correcto. Debe verificar
que tenga @ y al menos un punto después del @.
Explicá la lógica paso a paso."
```

**Mejor prompt → mejor respuesta**

---

<!-- _header: 'Estructura' -->

# Anatomía de un buen prompt

**1. Contexto:**
"Estoy aprendiendo Python en curso de ingreso"

**2. Tarea específica:**
"Necesito entender cómo funcionan los ciclos for"

**3. Formato deseado:**
"Explicá con ejemplos simples, paso a paso"

**4. Restricciones:**
"Usa solo conceptos básicos, sin librerías externas"

---

<!-- _header: 'Ser específico' -->

# Especificidad es clave

**❌ Vago:**
```
"explicame las listas"
```

**✅ Específico:**
```
"Explicá la diferencia entre list.append()
y list.extend() con ejemplos que muestren
claramente cómo difiere el resultado"
```

**Más específico → respuesta más útil**

---

<!-- _header: 'Contexto' -->

# Dar contexto apropiado

**Sin contexto:**
```
"¿Cómo ordeno una lista?"
```

**Con contexto:**
```
"Soy principiante en Python. Tengo una lista
de números [5, 2, 8, 1] y quiero ordenarla
de menor a mayor. ¿Cuál es la forma más simple?
Explicá qué hace cada parte del código."
```

**Contexto ayuda a la IA a ajustar nivel**

---

<!-- _header: 'Ejemplos' -->

# Dar ejemplos (Few-shot)

**Técnica efectiva:**
```
"Quiero una función que valide emails.

Ejemplos válidos:
- usuario@dominio.com
- nombre.apellido@empresa.com.ar

Ejemplos inválidos:
- usuario@dominio (sin extensión)
- @dominio.com (sin usuario)
- usuario.dominio.com (sin @)

Implementá la validación en Python."
```

**Ejemplos clarifican expectativas**

---

<!-- _header: 'Formato de salida' -->

# Especificar formato

**Pedir formato específico:**
```
"Explicá recursividad en Python.

Formato:
1. Definición en 2-3 líneas
2. Ejemplo muy simple (factorial)
3. Diagrama de las llamadas recursivas
4. Cuándo usar vs cuándo no usar
5. Un error común a evitar"
```

**Estructura la respuesta como necesitas**

---

<!-- _header: 'Nivel de detalle' -->

# Controlar profundidad

**Para aprender:**
```
"Explicá comprehensions de listas como si fuera
mi primera semana programando. Empezá con un
for normal y mostrá paso a paso cómo convertirlo
a comprehension."
```

**Para referencia:**
```
"Explicá comprehensions de listas brevemente
y dame 3 ejemplos: básico, con filtro, anidado."
```

---

<!-- _header: 'Prompting iterativo' -->

# Conversación, no pregunta única

**Primera interacción:**
```
"Explicá qué es una función en Python"
```

**Segunda:**
```
"Ahora explicá parámetros y argumentos"
```

**Tercera:**
```
"Dame un ejemplo de función con parámetros
opcionales (valores por defecto)"
```

**Construye conocimiento gradualmente**

---

<!-- _header: 'Chain-of-thought' -->

# Pedir razonamiento paso a paso

**Técnica poderosa:**
```
"Tengo que escribir función que verifique
si palabra es palíndromo.

No me des código todavía. Primero:
1. ¿Qué pasos necesito?
2. ¿Qué casos especiales considerar?
3. ¿Qué estructuras Python son útiles?

Luego mostrame el código."
```

**Entiendes el proceso, no solo resultado**

---

<!-- _header: 'Pedir explicaciones' -->

# No solo código

**❌ Solo código:**
```
"Dame función para calcular factorial"
```

**✅ Código + explicación:**
```
"Dame función para calcular factorial.
Explicá:
- Por qué usas ese enfoque
- Qué hace cada línea
- Qué casos especiales maneja
- Cómo probarla"
```

---

<!-- _header: 'Verificación' -->

# Pedir crítica

**Técnica útil:**
```
"Escribí este código:
[pegar tu código]

Analizalo y decime:
1. ¿Está correcto?
2. ¿Hay bugs?
3. ¿Se puede mejorar?
4. ¿Sigue buenas prácticas?
5. ¿Casos que no maneja?"
```

**IA como revisor de código**

---

<!-- _header: 'Debugging asistido' -->

# Debugging con IA

**Estructura efectiva:**
```
"Este código me da error:
[pegar código]

Error:
[pegar mensaje de error]

Lo que intento hacer:
[explicar objetivo]

¿Qué está mal y por qué?"
```

**Da contexto completo del problema**

---

<!-- _header: 'Comparar enfoques' -->

# Explorar alternativas

**Pregunta comparativa:**
```
"Dame 3 formas diferentes de invertir una lista
en Python:
1. Usando slicing
2. Usando .reverse()
3. Usando comprehension

Para cada una explica:
- Cuándo usarla
- Pros y contras
- Performance"
```

**Aprende múltiples soluciones**

---

<!-- _header: 'Restricciones' -->

# Limitar herramientas

**Para aprender fundamentos:**
```
"Explica cómo ordenar lista sin usar .sort()
ni sorted(). Solo con for, if y comparaciones.
Quiero entender el algoritmo básico."
```

**Restricciones fuerzan comprensión profunda**

---

<!-- _header: 'Ejemplo completo' -->

# Prompt bien estructurado

```
CONTEXTO:
Soy estudiante de ingreso, primera semana con Python.

OBJETIVO:
Entender diccionarios.

FORMATO DESEADO:
1. ¿Qué es un diccionario? (máx 2 líneas)
2. Ejemplo simple de crear uno
3. Cómo agregar elementos
4. Cómo acceder a valores
5. Qué pasa si clave no existe
6. Diferencia con lista

RESTRICCIONES:
- Explicaciones simples
- Ejemplos con datos del mundo real (no foo/bar)
- Sin conceptos avanzados (no menciones métodos
  como .get() todavía)
```

---

<!-- _header: 'Errores comunes' -->

# Qué evitar

**❌ Muy vago:**
```
"ayuda con python"
```

**❌ Sin contexto:**
```
"como hago esto: [código sin explicar qué busca]"
```

**❌ Esperar magia:**
```
"hace mi tarea"
```

**❌ No verificar:**
```
[Copiar respuesta sin probar]
```

---

<!-- _header: 'Mejores prácticas' -->

# Tips de prompting

**1. Sé específico y claro**
**2. Da contexto de tu nivel**
**3. Usa ejemplos cuando ayude**
**4. Pide explicaciones, no solo código**
**5. Estructura tu prompt**
**6. Itera y refina**
**7. Verifica siempre la respuesta**

---

<!-- _header: 'Plantilla reutilizable' -->

# Template para prompts

```
ROL: [Estudiante de ingreso / programador junior]

CONTEXTO: [Qué estás haciendo]

PROBLEMA: [Qué no entiendes o no funciona]

INTENTOS: [Qué probaste ya]

PREGUNTA ESPECÍFICA: [Qué necesitas saber]

FORMATO: [Cómo quieres la respuesta]
```

**Adapta según necesidad**

---

<!-- _header: 'Ejercicio' -->

# Practica prompting

**Tarea:**
Necesitas función que cuente vocales en string.

**Escribe prompt que:**
1. Pida explicación del algoritmo primero
2. Luego el código comentado
3. Luego casos de prueba
4. Finalmente variante que cuente cada vocal

---

<!-- _header: 'Ejercicio - Solución' -->

# Ejemplo de prompt

```
CONTEXTO:
Estoy aprendiendo funciones en Python.

TAREA:
Crear función que cuente vocales en string.

PROCESO (no me des código todavía):
1. ¿Qué pasos necesito?
2. ¿Qué estructuras Python usar?
3. ¿Casos especiales (mayúsculas, acentos)?

Luego:
4. Mostrame código muy comentado
5. Dame 5 casos de prueba
6. Variante que cuente cada vocal separadamente

Explicá cada paso para que lo entienda.
```

---

<!-- _header: 'Prompting avanzado' -->

# Técnicas adicionales

**Role-playing:**
```
"Actúa como profesor de programación.
Explicame [tema] usando ejemplos del mundo real."
```

**Contrafácticos:**
```
"¿Qué pasaría si en este código cambio X por Y?"
```

**Simplificación:**
```
"Este código funciona pero es complejo.
Simplificalo manteniendo la funcionalidad."
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**Buen prompt tiene:**
* Contexto claro
* Tarea específica
* Formato deseado
* Restricciones apropiadas

**Técnicas:**
* Few-shot (ejemplos)
* Chain-of-thought (paso a paso)
* Iteración progresiva
* Comparar alternativas

**Siempre:**
* Verifica respuesta
* Experimenta con código
* Pregunta lo que no entiendes

**Próximo:** Ética y verificación

---

<!-- _class: centered -->

# ¿Preguntas?
