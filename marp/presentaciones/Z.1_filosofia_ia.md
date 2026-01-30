---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'IA - Parte 1/3' -->

# <!-- fit --> IA como Herramienta
## Aprender con inteligencia artificial
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Nueva realidad' -->

# La IA está aquí

**Herramientas disponibles:**
* ChatGPT, Claude, Gemini
* GitHub Copilot
* Cursor, Codeium
* Y muchas más...

**No se trata de si usar IA:**
**Se trata de CÓMO usarla bien**

---

<!-- _header: 'Filosofía' -->

# IA: herramienta, no muleta

**✅ IA como:**
* Tutor personal 24/7
* Generador de explicaciones
* Verificador de ideas
* Fuente de ejemplos

**❌ IA NO como:**
* Reemplazo de aprender
* Copiadora de código
* Excusa para no pensar

---

<!-- _header: 'Principio fundamental' -->

# Entender lo que copias

**Regla de oro:**
> No uses código que no entiendes

**Si la IA te da código:**
1. Léelo línea por línea
2. Explica qué hace cada parte
3. Modifícalo para probarlo
4. Pregunta lo que no entiendas

**Si no puedes explicarlo, no lo uses**

---

<!-- _header: 'Usos apropiados' -->

# ✅ Cuándo usar IA

**Explicaciones:**
```
"Explicá cómo funcionan las listas en Python"
"¿Qué diferencia hay entre append y extend?"
```

**Debugging:**
```
"Este código me da error [pegar código]. 
¿Por qué falla?"
```

**Alternativas:**
```
"Tengo este código [pegar].
¿Hay una forma más simple de hacer esto?"
```

---

<!-- _header: 'Usos apropiados' -->

# ✅ Cuándo usar IA (cont.)

**Generar tests:**
```
"Dame casos de prueba para esta función:
[pegar función]"
```

**Conceptos:**
```
"Explicá qué es la recursividad con un ejemplo
simple"
```

**Refactoring:**
```
"Este código funciona pero es confuso.
¿Cómo mejorarlo? [pegar código]"
```

---

<!-- _header: 'Usos inapropiados' -->

# ❌ Cuándo NO usar IA

**Generar tarea completa:**
```
❌ "Resolvé el ejercicio 3 del TP"
❌ "Dame el código para [enunciado completo]"
```

**Copiar sin entender:**
```
❌ Pedir código y entregar tal cual
❌ Usar sin modificar
❌ No saber explicarlo
```

---

<!-- _header: 'Usos inapropiados' -->

# ❌ Cuándo NO usar IA (cont.)

**Reemplazo de práctica:**
```
❌ Evitar programar uno mismo
❌ No hacer ejercicios por pereza
❌ Usar IA para cada pequeño detalle
```

**Sin verificación:**
```
❌ Confiar ciegamente en output
❌ No probar el código
❌ No leer documentación oficial
```

---

<!-- _header: 'Flujo recomendado' -->

# Proceso de trabajo con IA

**1. Intentá solo primero**
* Programa tu solución
* Llegá lo más lejos posible

**2. Identifica obstáculo**
* ¿Qué específicamente no sabés?
* Formula pregunta precisa

**3. Consulta IA**
* Pregunta específica
* Pide explicación, no solo código

**4. Comprende respuesta**
* Lee y analiza
* Experimenta modificando

**5. Aplica e integra**
* Adapta a tu código
* Verifica que funcione

---

<!-- _header: 'Ejemplo bueno' -->

# Uso correcto de IA

**Tu código:**
```python
# Funciona pero es lento
def es_primo(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True
```

**Pregunta a IA:**
```
"Tengo esta función que verifica si un número es primo.
Funciona pero es lenta con números grandes.
¿Cómo puedo optimizarla? Explicá la mejora."
```

**Analizas respuesta, entiendes optimización,
aplicas a tu código**

---

<!-- _header: 'Ejemplo malo' -->

# Uso incorrecto de IA

**Enunciado:**
> Crear programa que calcule factorial recursivo

**❌ Mal uso:**
```
Prompt: "Dame código en Python para calcular
factorial recursivo"

[Copiar respuesta directamente sin leer]
[Entregar como propia]
```

**Problemas:**
* No aprendiste recursividad
* No entiendes el código
* No podrás explicarlo
* Fraude académico

---

<!-- _header: 'Ejemplo bueno recursión' -->

# Uso correcto para recursión

**Proceso apropiado:**

**1. Preguntar concepto:**
```
"¿Qué es recursividad? Dame un ejemplo simple"
```

**2. Intentar implementar:**
```python
# Tu intento
def factorial(n):
    # ¿Cómo hacer que se llame a sí misma?
    pass
```

**3. Preguntar específico:**
```
"Intenté hacer factorial recursivo pero no sé
cómo hacer el caso base. ¿Qué me falta?"
```

**4. Completar con tu entendimiento**

---

<!-- _header: 'IA como tutor' -->

# Diálogo socrático

**En lugar de pedir respuesta:**
```
❌ "Dame el código completo"
```

**Pedir guía:**
```
✅ "Estoy trabado en [problema].
Dame una pista, no la solución completa.
¿Cuál sería el primer paso?"
```

**Construcción iterativa:**
1. Pista inicial
2. Tu intento
3. Siguiente pista
4. Iterar hasta resolver

---

<!-- _header: 'Verificación' -->

# No confiar ciegamente

**La IA puede equivocarse:**
* Código con bugs
* Explicaciones incorrectas
* Soluciones complejas innecesariamente

**Siempre verifica:**
1. **Ejecutar código** - ¿funciona?
2. **Probar casos** - ¿todos los casos?
3. **Leer docs** - ¿coincide con oficial?
4. **Preguntar a humanos** - ¿docente, compañeros?

---

<!-- _header: 'Comparar fuentes' -->

# Triangular información

**No confiar en una sola fuente:**
```
1. IA te explica concepto
2. Lees documentación oficial
3. Ves video tutorial
4. Preguntas en clase
```

**Si todas coinciden → probablemente correcto**
**Si difieren → investigar más**

---

<!-- _header: 'Integridad académica' -->

# Honestidad y ética

**En este curso:**
* **Permitido:** Usar IA para aprender
* **Permitido:** Pedir explicaciones
* **Permitido:** Debugging con ayuda IA

**NO permitido:**
* Copiar código completo de IA
* Entregar sin entender
* Usar IA para exámenes (salvo indicación)

**Cuando dudes, pregunta al docente**

---

<!-- _header: 'Declarar uso' -->

# Transparencia

**Si usas IA para algo entregable:**
```python
"""
Módulo calculadora.

Nota: Usé ChatGPT para entender cómo manejar
excepciones en división. Adapté el código a
mi solución.
"""
```

**Ser transparente:**
* Muestra integridad
* Permite feedback apropiado
* Evita malentendidos

---

<!-- _header: 'Crecimiento' -->

# Aprender progresivamente

**Mes 1:** IA para conceptos básicos
**Mes 2:** Menos dependencia, más autonomía
**Mes 3:** IA solo para verificar ideas propias

**Meta:** Ser programador independiente
**IA:** Herramienta que potencia, no que reemplaza

---

<!-- _header: 'Señales de mal uso' -->

# Autoevaluación

**🚨 Alerta si:**
* Usas IA para cada línea de código
* No puedes explicar tu código
* Entregas sin probar
* Copias sin modificar
* Evitas pensar por ti mismo

**✅ Buen uso si:**
* Entiendes todo tu código
* Puedes explicarlo
* Modificas y adaptas
* IA complementa tu aprendizaje

---

<!-- _header: 'Desarrollar criterio' -->

# Pensamiento crítico

**Ante output de IA pregunta:**
* ¿Es correcto?
* ¿Es eficiente?
* ¿Es legible?
* ¿Hay forma más simple?
* ¿Aprendí algo nuevo?

**No aceptes ciegamente**
**Cuestiona, experimenta, verifica**

---

<!-- _header: 'Resumen' -->

# Para recordar

**IA como herramienta de aprendizaje:**
* ✅ Pedir explicaciones
* ✅ Debugging asistido
* ✅ Verificar ideas
* ❌ Copiar código entero
* ❌ Evitar pensar
* ❌ Usar sin entender

**Regla de oro:**
> Si no puedes explicarlo,
> no lo entiendes.
> Si no lo entiendes,
> no lo uses.

**Próximo:** Técnicas de prompting

---

<!-- _class: centered -->

# ¿Preguntas?
