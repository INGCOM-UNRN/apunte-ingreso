---
title: Ejercicios - Uso Responsable de IA
description: Ejercicios prácticos para aprender a usar la IA como herramienta de aprendizaje efectiva
---

# Ejercicios: Uso Responsable de IA

Estos ejercicios están diseñados para que practiques el uso efectivo de la IA como herramienta de aprendizaje. El objetivo no es obtener respuestas, sino desarrollar habilidades de comunicación con asistentes de IA que potencien tu comprensión.

---

## Sección 1: Construcción de Prompts Efectivos

### Ejercicio 1.1: Identificar prompts deficientes

A continuación se presentan prompts mal formulados. Para cada uno, identificá qué componente falta (contexto, objetivo, restricciones o formato) y reescribilo de forma efectiva.

```{exercise}
:label: prompt-deficiente-1

**Prompt original:** "no me funciona el codigo"

Identificá qué falta y reescribí el prompt siguiendo la estructura: contexto + objetivo + restricciones + formato.
```

```{exercise}
:label: prompt-deficiente-2

**Prompt original:** "explicame listas"

Identificá qué falta y reescribí el prompt para obtener una explicación útil para tu nivel.
```

```{exercise}
:label: prompt-deficiente-3

**Prompt original:** "dame codigo para ordenar numeros"

Identificá qué falta y reescribí el prompt de manera que la IA te guíe sin resolver el problema por vos.
```

### Ejercicio 1.2: Completar prompts parciales

Cada prompt tiene algunos componentes pero le faltan otros. Completalos para que sean efectivos.

```{exercise}
:label: prompt-parcial-1

**Prompt parcial:** "Estoy aprendiendo Python en el curso de ingreso. [FALTA OBJETIVO, RESTRICCIONES Y FORMATO]"

Completá el prompt para pedir ayuda con el concepto de funciones.
```

```{exercise}
:label: prompt-parcial-2

**Prompt parcial:** "[FALTA CONTEXTO] Necesito entender por qué mi lazo `while` nunca termina. [FALTA RESTRICCIONES Y FORMATO]"

Completá el prompt agregando contexto apropiado y restricciones que eviten que te den la solución directa.
```

---

## Sección 2: Técnicas de Prompting

### Ejercicio 2.1: Prompting Socrático

```{exercise}
:label: socratico-1

Querés aprender a escribir una función que cuente cuántas vocales tiene una cadena de texto. 

Escribí un prompt usando la técnica socrática para que la IA te guíe con preguntas en lugar de darte la solución.
```

```{exercise}
:label: socratico-2

Necesitás entender cómo funciona el algoritmo de búsqueda binaria.

Formulá un prompt socrático que te ayude a descubrir el algoritmo paso a paso.
```

### Ejercicio 2.2: Explicación por Capas

```{exercise}
:label: capas-1

Querés entender qué es una variable en programación.

Escribí un prompt que pida una explicación en tres niveles de complejidad.
```

```{exercise}
:label: capas-2

Necesitás comprender el concepto de "scope" (alcance) de las variables.

Formulá un prompt que solicite la explicación en capas progresivas.
```

### Ejercicio 2.3: Debugging Guiado

```{exercise}
:label: debugging-1

El siguiente código debería calcular el factorial de un número, pero siempre devuelve 0:

```python
def factorial(n):
    resultado = 0
    for i in range(1, n + 1):
        resultado = resultado * i
    return resultado
```

Escribí un prompt para pedir ayuda con debugging **sin que te corrijan el código directamente**.
```

```{exercise}
:label: debugging-2

Este código debería encontrar el número más grande en una lista, pero da error:

```python
def maximo(lista):
    max_valor = 0
    for num in lista:
        if num > max_valor
            max_valor = num
    return max_valor
```

Formulá un prompt de debugging guiado que te ayude a encontrar el problema.
```

### Ejercicio 2.4: Método de Feynman Inverso

```{exercise}
:label: feynman-1

Creés que entendés cómo funcionan los lazos `for` en Python.

Escribí un prompt para explicarle el concepto a la IA (actuando como estudiante) y que te haga preguntas para verificar tu comprensión.
```

```{exercise}
:label: feynman-2

Querés verificar tu comprensión sobre la diferencia entre parámetros y argumentos en funciones.

Formulá un prompt usando el método de Feynman inverso.
```

---

## Sección 3: Escenarios de Uso

### Ejercicio 3.1: Preparación para Ejercicios

```{exercise}
:label: preparacion-1

Mañana vas a practicar ejercicios sobre listas en Python. 

Escribí un prompt para prepararte mentalmente antes de empezar, pidiendo conceptos clave, errores comunes y estrategias de validación.
```

### Ejercicio 3.2: Exploración de Alternativas

```{exercise}
:label: alternativas-1

Resolviste el problema de invertir una cadena de texto así:

```python
def invertir(cadena):
    resultado = ""
    for i in range(len(cadena) - 1, -1, -1):
        resultado += cadena[i]
    return resultado
```

Escribí un prompt para explorar otras formas de resolver el mismo problema y entender cuándo usar cada una.
```

### Ejercicio 3.3: Conexión de Conceptos

```{exercise}
:label: conexion-1

Acabás de aprender sobre funciones y antes habías estudiado condicionales (`if`/`else`).

Escribí un prompt para entender cómo se relacionan estos conceptos y cuándo usarlos juntos.
```

---

## Sección 4: Ética y Responsabilidad

### Ejercicio 4.1: Casos Éticos

Analizá cada situación y decidí si el uso de IA es apropiado. Justificá tu respuesta.

```{exercise}
:label: etica-1

**Situación:** Tenés un examen parcial mañana. Usás ChatGPT para estudiar, pidiéndole que te explique conceptos y te genere ejercicios de práctica. Al día siguiente, rendís el examen sin usar IA.

¿Es un uso apropiado? ¿Por qué?
```

```{exercise}
:label: etica-2

**Situación:** Durante un trabajo práctico grupal (donde está permitido usar IA con documentación), usás GitHub Copilot para autocompletar algunas funciones. Incluís en el informe una declaración de uso de IA detallando qué partes fueron asistidas.

¿Es un uso apropiado? ¿Por qué?
```

```{exercise}
:label: etica-3

**Situación:** Estás haciendo un ejercicio obligatorio para entregar. Te trabás y le pedís a ChatGPT que te dé "solo una pista" sobre cómo empezar. La IA te sugiere usar un lazo `while` con una condición específica.

¿Es un uso apropiado? ¿Depende del contexto? ¿Qué harías vos?
```

### Ejercicio 4.2: Declaración de Uso

```{exercise}
:label: declaracion-1

Imaginá que usaste IA de las siguientes formas en un trabajo práctico donde está permitido con documentación:

- ChatGPT te explicó qué es una lista de comprensión
- GitHub Copilot sugirió el nombre de una variable
- Le pediste a Claude que revise tu código y te dijo que olvidaste manejar el caso de lista vacía

Escribí una declaración de uso de IA completa y honesta para incluir en tu trabajo.
```

---

## Sección 5: Auto-Evaluación

### Ejercicio 5.1: Checklist de Uso Responsable

```{exercise}
:label: autoevaluacion-1

Pensá en la última vez que usaste IA para ayudarte con programación. Respondé honestamente:

1. ¿Intentaste resolver el problema solo antes de consultar la IA?
2. ¿Tenías una pregunta específica o simplemente pediste "la solución"?
3. ¿Leíste y entendiste completamente la respuesta?
4. ¿Podrías explicar el código resultante sin consultar la IA?
5. ¿Probaste el código con casos adicionales propios?

Para cada "No", escribí qué harías diferente la próxima vez.
```

### Ejercicio 5.2: Señales de Alerta

```{exercise}
:label: autoevaluacion-2

Leé las siguientes afirmaciones y marcá las que te identifican:

- [ ] Cuando tengo un error, mi primer instinto es preguntarle a la IA
- [ ] A veces copio código de la IA sin leer todas las líneas
- [ ] Me cuesta explicar mi propio código cuando me preguntan
- [ ] Rara vez intento resolver algo solo antes de consultar la IA
- [ ] Me siento ansioso cuando no tengo acceso a la IA para programar

Si marcaste alguna, escribí un plan concreto para desarrollar más independencia.
```

---

## Sección 6: Práctica Integrada

### Ejercicio 6.1: Sesión Completa de Aprendizaje

```{exercise}
:label: practica-integrada-1

Elegí un concepto de Python que te cueste (por ejemplo: recursión, diccionarios, manejo de excepciones). 

Diseñá una secuencia de 4 prompts que usarías para aprenderlo efectivamente:

1. Un prompt para entender el concepto (explicación por capas)
2. Un prompt para verificar tu comprensión (Feynman inverso)
3. Un prompt para practicar (generación de ejercicios)
4. Un prompt para profundizar (conexión con otros conceptos)
```

### Ejercicio 6.2: Simulación de Debugging

:::{exercise}
:label: practica-integrada-2

El siguiente código tiene un error. **Sin ejecutarlo ni pedir ayuda**, intentá encontrar el error vos mismo durante 10 minutos. Anotá tu proceso de pensamiento.

```python
def promedio(numeros):
    suma = 0
    for num in numeros:
        suma += num
    return suma / len(numeros)

# Test
print(promedio([]))  # Debería manejar lista vacía
```

Después de intentarlo, escribí el prompt que usarías para pedir ayuda de debugging guiado si no hubieras encontrado el error.
:::

---

## Reflexión Final

```{exercise}
:label: reflexion-final

Después de completar estos ejercicios, respondé:

1. ¿Qué técnica de prompting te pareció más útil? ¿Por qué?
2. ¿En qué situaciones te sentirías cómodo usando IA para aprender?
3. ¿En qué situaciones preferirías no usar IA?
4. ¿Cómo cambió tu perspectiva sobre el uso de IA después de estos ejercicios?
```
