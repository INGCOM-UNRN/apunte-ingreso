---
title: Pruebas de Escritorio en Python
description: Ejercicios para practicar la lectura y seguimiento de código Python básico
---

# Pruebas de Escritorio en Python

## Introducción

Las **pruebas de escritorio** son una técnica fundamental para verificar el comportamiento de un programa sin ejecutarlo en la computadora. Consisten en seguir manualmente la ejecución del código, registrando el valor de cada variable en cada paso.

### ¿Por qué son importantes?

:::{important}
Hacer pruebas de escritorio desarrolla habilidades esenciales:

- **Lectura de código:** Comprender qué hace cada línea
- **Pensamiento algorítmico:** Seguir el flujo de ejecución
- **Detección de errores:** Encontrar bugs antes de ejecutar
- **Depuración:** Identificar dónde falla un programa
:::

### ¿Cómo hacer una prueba de escritorio?

1. **Crear una tabla** con columnas para:
   - Número de línea ejecutada
   - Variables (una columna por variable)
   - Salida (output) si hay `print()`
   - Condiciones evaluadas

2. **Seguir la ejecución** línea por línea:
   - Actualizar valores de variables
   - Evaluar condiciones (`True`/`False`)
   - Registrar salidas
   - Seguir el flujo (if/else, lazos)

3. **Anotar el resultado final**

### Ejemplo Completo

```python
x = 5
y = 10
if x < y:
    z = x + y
else:
    z = x - y
print(z)
```

**Tabla de seguimiento:**

| Línea | x | y | z | Condición | Salida |
|-------|---|---|---|-----------|--------|
| 1     | 5 | - | - | - | - |
| 2     | 5 | 10 | - | - | - |
| 3     | 5 | 10 | - | `5 < 10` → `True` | - |
| 4     | 5 | 10 | 15 | - | - |
| 7     | 5 | 10 | 15 | - | `15` |

**Resultado:** El programa imprime `15`

---

## Ejercicios de Pruebas de Escritorio

Los siguientes ejercicios están ordenados por **dificultad creciente**, comenzando con código secuencial simple y avanzando hacia lazos anidados con listas.

:::{tip}
Para cada ejercicio:
1. Copiá la tabla proporcionada
2. Completala mientras seguís el código
3. Anotá el resultado final
4. Compará con la solución
:::

---

## Nivel 1: Secuenciales Simples

### Ejercicio 1: Intercambio de Valores

Seguí la ejecución del siguiente código y determiná qué se imprime:

```python
a = 7
b = 3
temp = a
a = b
b = temp
print(a, b)
```

**Tabla para completar:**

| Línea | a | b | temp | Salida |
|-------|---|---|------|--------|
| 1     |   |   |      |        |
| 2     |   |   |      |        |
| 3     |   |   |      |        |
| 4     |   |   |      |        |
| 5     |   |   |      |        |
| 6     |   |   |      |        |

**¿Qué imprime el programa?**

---

### Ejercicio 2: Operaciones Aritméticas

Seguí la ejecución y determiná el valor final de `resultado`:

```python
x = 10
y = 3
cociente = x // y
resto = x % y
resultado = cociente * 10 + resto
print(resultado)
```

**Tabla para completar:**

| Línea | x | y | cociente | resto | resultado | Salida |
|-------|---|---|----------|-------|-----------|--------|
| 1     |   |   |          |       |           |        |
| 2     |   |   |          |       |           |        |
| 3     |   |   |          |       |           |        |
| 4     |   |   |          |       |           |        |
| 5     |   |   |          |       |           |        |
| 6     |   |   |          |       |           |        |

**¿Qué imprime el programa?**

---

## Nivel 2: Con Decisiones

### Ejercicio 3: Número Mayor

Seguí la ejecución y determiná qué se imprime:

```python
a = 15
b = 20
if a > b:
    mayor = a
else:
    mayor = b
print("El mayor es:", mayor)
```

**Tabla para completar:**

| Línea | a | b | mayor | Condición | Salida |
|-------|---|---|-------|-----------|--------|
| 1     |   |   |       |           |        |
| 2     |   |   |       |           |        |
| 3     |   |   |       |           |        |
| 4 ó 6 |   |   |       |           |        |
| 7     |   |   |       |           |        |

**¿Qué imprime el programa?**

---

### Ejercicio 4: Clasificación de Nota

Seguí la ejecución con `nota = 75`:

```python
nota = 75
if nota >= 90:
    mensaje = "Excelente"
elif nota >= 70:
    mensaje = "Aprobado"
else:
    mensaje = "Insuficiente"
print(mensaje)
```

**Tabla para completar:**

| Línea | nota | mensaje | Condición | Salida |
|-------|------|---------|-----------|--------|
| 1     |      |         |           |        |
| 2     |      |         |           |        |
| 4     |      |         |           |        |
| 5 ó 7 |      |         |           |        |
| 8     |      |         |           |        |

**¿Qué imprime el programa?**

---

## Nivel 3: Lazos Simples

### Ejercicio 5: Acumulador

Seguí la ejecución y determiná el valor final de `suma`:

```python
suma = 0
i = 1
while i <= 4:
    suma = suma + i
    i = i + 1
print(suma)
```

**Tabla para completar:**

| Línea | suma | i | Condición `i <= 4` | Salida |
|-------|------|---|-------------------|--------|
| 1     |      |   |                   |        |
| 2     |      |   |                   |        |
| 3     |      |   |                   |        |
| 4     |      |   |                   |        |
| 5     |      |   |                   |        |
| 3     |      |   |                   |        |
| ...   |      |   |                   |        |

**Pista:** El lazo se repite mientras `i <= 4` sea verdadero. Continuá la tabla hasta que la condición sea falsa.

**¿Qué imprime el programa?**

---

### Ejercicio 6: Lazo For con Range

Seguí la ejecución y determiná qué se imprime:

```python
total = 0
for n in range(2, 7, 2):
    total = total + n
    print(n)
print("Total:", total)
```

**Tabla para completar:**

| Iteración | n | total | Salida |
|-----------|---|-------|--------|
| Inicial   | - |       |        |
| 1         |   |       |        |
| 2         |   |       |        |
| 3         |   |       |        |
| Final     | - |       |        |

**Recordá:** `range(2, 7, 2)` genera: 2, 4, 6

**¿Qué imprime el programa?**

---

## Nivel 4: Con Listas

### Ejercicio 7: Recorrido de Lista

Seguí la ejecución y determiná qué se imprime:

```python
numeros = [10, 20, 30]
i = 0
while i < len(numeros):
    print(numeros[i])
    i = i + 1
```

**Tabla para completar:**

| Línea | numeros | i | len(numeros) | Condición | numeros[i] | Salida |
|-------|---------|---|--------------|-----------|------------|--------|
| 1     |         |   |              |           |            |        |
| 2     |         |   |              |           |            |        |
| 3     |         |   |              |           |            |        |
| 4     |         |   |              |           |            |        |
| 5     |         |   |              |           |            |        |
| 3     |         |   |              |           |            |        |
| ...   |         |   |              |           |            |        |

**¿Qué imprime el programa? (línea por línea)**

---

### Ejercicio 8: Modificar Lista

Seguí la ejecución y determiná el contenido final de `valores`:

```python
valores = [5, 10, 15]
for i in range(len(valores)):
    valores[i] = valores[i] * 2
print(valores)
```

**Tabla para completar:**

| Iteración | i | valores (estado actual) | valores[i] antes | valores[i] después | Salida |
|-----------|---|-------------------------|------------------|-------------------|--------|
| Inicial   | - |                         |                  |                   |        |
| 1         |   |                         |                  |                   |        |
| 2         |   |                         |                  |                   |        |
| 3         |   |                         |                  |                   |        |
| Final     | - |                         |                  |                   |        |

**¿Qué imprime el programa?**

---

## Nivel 5: Listas con Decisiones

### Ejercicio 9: Contar Pares

Seguí la ejecución y determiná el valor final de `contador`:

```python
numeros = [7, 12, 5, 8, 3]
contador = 0
for num in numeros:
    if num % 2 == 0:
        contador = contador + 1
print("Pares:", contador)
```

**Tabla para completar:**

| Iteración | num | num % 2 | Condición `== 0` | contador | Salida |
|-----------|-----|---------|------------------|----------|--------|
| Inicial   | -   | -       | -                |          |        |
| 1         |     |         |                  |          |        |
| 2         |     |         |                  |          |        |
| 3         |     |         |                  |          |        |
| 4         |     |         |                  |          |        |
| 5         |     |         |                  |          |        |
| Final     | -   | -       | -                |          |        |

**¿Qué imprime el programa?**

---

### Ejercicio 10: Búsqueda del Mayor

Seguí la ejecución y determiná el valor final de `maximo`:

```python
datos = [23, 45, 12, 67, 34]
maximo = datos[0]
for i in range(1, len(datos)):
    if datos[i] > maximo:
        maximo = datos[i]
print("Máximo:", maximo)
```

**Tabla para completar:**

| Iteración | i | datos[i] | maximo (antes) | Condición | maximo (después) | Salida |
|-----------|---|----------|----------------|-----------|------------------|--------|
| Inicial   | - | -        |                | -         |                  |        |
| 1         |   |          |                |           |                  |        |
| 2         |   |          |                |           |                  |        |
| 3         |   |          |                |           |                  |        |
| 4         |   |          |                |           |                  |        |
| Final     | - | -        | -              | -         |                  |        |

**Recordá:** `range(1, len(datos))` genera: 1, 2, 3, 4

**¿Qué imprime el programa?**

---

## Soluciones

:::{note}
Intentá resolver cada ejercicio antes de ver las soluciones. Las pruebas de escritorio requieren práctica y paciencia.
:::

### Solución Ejercicio 1: Intercambio de Valores

**Tabla completa:**

| Línea | a | b | temp | Salida |
|-------|---|---|------|--------|
| 1     | 7 | - | -    | -      |
| 2     | 7 | 3 | -    | -      |
| 3     | 7 | 3 | 7    | -      |
| 4     | 3 | 3 | 7    | -      |
| 5     | 3 | 7 | 7    | -      |
| 6     | 3 | 7 | 7    | `3 7`  |

**Respuesta:** El programa imprime `3 7`

**Explicación:**
Este es el algoritmo clásico de intercambio de valores usando una variable temporal:
1. Guardamos el valor de `a` (7) en `temp`
2. Asignamos el valor de `b` (3) a `a`
3. Asignamos el valor de `temp` (7) a `b`
4. Resultado: `a` tiene 3 y `b` tiene 7 (valores intercambiados)

---

### Solución Ejercicio 2: Operaciones Aritméticas

**Tabla completa:**

| Línea | x | y | cociente | resto | resultado | Salida |
|-------|---|---|----------|-------|-----------|--------|
| 1     | 10 | - | -        | -     | -         | -      |
| 2     | 10 | 3 | -        | -     | -         | -      |
| 3     | 10 | 3 | 3        | -     | -         | -      |
| 4     | 10 | 3 | 3        | 1     | -         | -      |
| 5     | 10 | 3 | 3        | 1     | 31        | -      |
| 6     | 10 | 3 | 3        | 1     | 31        | `31`   |

**Respuesta:** El programa imprime `31`

**Explicación:**
- División entera: `10 // 3 = 3` (cociente sin decimales)
- Módulo: `10 % 3 = 1` (resto de la división)
- Cálculo: `3 * 10 + 1 = 30 + 1 = 31`

---

### Solución Ejercicio 3: Número Mayor

**Tabla completa:**

| Línea | a | b | mayor | Condición | Salida |
|-------|---|---|-------|-----------|--------|
| 1     | 15 | - | -     | -         | -      |
| 2     | 15 | 20 | -    | -         | -      |
| 3     | 15 | 20 | -    | `15 > 20` → `False` | - |
| 6     | 15 | 20 | 20   | -         | -      |
| 7     | 15 | 20 | 20   | -         | `El mayor es: 20` |

**Respuesta:** El programa imprime `El mayor es: 20`

**Explicación:**
- La condición `a > b` es `15 > 20`, que es `False`
- Se ejecuta el bloque `else`
- Se asigna `mayor = b = 20`

---

### Solución Ejercicio 4: Clasificación de Nota

**Tabla completa:**

| Línea | nota | mensaje | Condición | Salida |
|-------|------|---------|-----------|--------|
| 1     | 75   | -       | -         | -      |
| 2     | 75   | -       | `75 >= 90` → `False` | - |
| 4     | 75   | -       | `75 >= 70` → `True` | - |
| 5     | 75   | "Aprobado" | -      | -      |
| 8     | 75   | "Aprobado" | -      | `Aprobado` |

**Respuesta:** El programa imprime `Aprobado`

**Explicación:**
- Primera condición: `75 >= 90` es `False`, se evalúa el `elif`
- Segunda condición: `75 >= 70` es `True`, se ejecuta ese bloque
- Se asigna `mensaje = "Aprobado"` y se salta el `else`

---

### Solución Ejercicio 5: Acumulador

**Tabla completa:**

| Línea | suma | i | Condición `i <= 4` | Salida |
|-------|------|---|-------------------|--------|
| 1     | 0    | - | -                 | -      |
| 2     | 0    | 1 | -                 | -      |
| 3     | 0    | 1 | `True`            | -      |
| 4     | 1    | 1 | -                 | -      |
| 5     | 1    | 2 | -                 | -      |
| 3     | 1    | 2 | `True`            | -      |
| 4     | 3    | 2 | -                 | -      |
| 5     | 3    | 3 | -                 | -      |
| 3     | 3    | 3 | `True`            | -      |
| 4     | 6    | 3 | -                 | -      |
| 5     | 6    | 4 | -                 | -      |
| 3     | 6    | 4 | `True`            | -      |
| 4     | 10   | 4 | -                 | -      |
| 5     | 10   | 5 | -                 | -      |
| 3     | 10   | 5 | `False`           | -      |
| 6     | 10   | 5 | -                 | `10`   |

**Respuesta:** El programa imprime `10`

**Explicación:**
El lazo suma los números del 1 al 4:
- Iteración 1: `suma = 0 + 1 = 1`
- Iteración 2: `suma = 1 + 2 = 3`
- Iteración 3: `suma = 3 + 3 = 6`
- Iteración 4: `suma = 6 + 4 = 10`
- Cuando `i = 5`, la condición `5 <= 4` es `False`, termina el lazo

---

### Solución Ejercicio 6: Lazo For con Range

**Tabla completa:**

| Iteración | n | total | Salida |
|-----------|---|-------|--------|
| Inicial   | - | 0     | -      |
| 1         | 2 | 2     | `2`    |
| 2         | 4 | 6     | `4`    |
| 3         | 6 | 12    | `6`    |
| Final     | - | 12    | `Total: 12` |

**Respuesta:** El programa imprime:
```
2
4
6
Total: 12
```

**Explicación:**
- `range(2, 7, 2)` genera los valores: 2, 4, 6
  - Comienza en 2
  - Termina antes de 7
  - Incrementa de 2 en 2
- En cada iteración se imprime `n` y se suma a `total`
- Al final: `total = 2 + 4 + 6 = 12`

---

### Solución Ejercicio 7: Recorrido de Lista

**Tabla completa:**

| Línea | numeros | i | len(numeros) | Condición | numeros[i] | Salida |
|-------|---------|---|--------------|-----------|------------|--------|
| 1     | [10,20,30] | - | 3         | -         | -          | -      |
| 2     | [10,20,30] | 0 | 3         | -         | -          | -      |
| 3     | [10,20,30] | 0 | 3         | `True`    | 10         | -      |
| 4     | [10,20,30] | 0 | 3         | -         | 10         | `10`   |
| 5     | [10,20,30] | 1 | 3         | -         | -          | -      |
| 3     | [10,20,30] | 1 | 3         | `True`    | 20         | -      |
| 4     | [10,20,30] | 1 | 3         | -         | 20         | `20`   |
| 5     | [10,20,30] | 2 | 3         | -         | -          | -      |
| 3     | [10,20,30] | 2 | 3         | `True`    | 30         | -      |
| 4     | [10,20,30] | 2 | 3         | -         | 30         | `30`   |
| 5     | [10,20,30] | 3 | 3         | -         | -          | -      |
| 3     | [10,20,30] | 3 | 3         | `False`   | -          | -      |

**Respuesta:** El programa imprime (línea por línea):
```
10
20
30
```

**Explicación:**
- `len(numeros)` es 3 (la lista tiene 3 elementos)
- El lazo recorre los índices 0, 1, 2
- En cada iteración imprime el elemento en esa posición
- Cuando `i = 3`, la condición `3 < 3` es `False`, termina

---

### Solución Ejercicio 8: Modificar Lista

**Tabla completa:**

| Iteración | i | valores (estado actual) | valores[i] antes | valores[i] después | Salida |
|-----------|---|-------------------------|------------------|-------------------|--------|
| Inicial   | - | [5, 10, 15]             | -                | -                 | -      |
| 1         | 0 | [5, 10, 15]             | 5                | 10                | -      |
| 1         | 0 | [10, 10, 15]            | -                | -                 | -      |
| 2         | 1 | [10, 10, 15]            | 10               | 20                | -      |
| 2         | 1 | [10, 20, 15]            | -                | -                 | -      |
| 3         | 2 | [10, 20, 15]            | 15               | 30                | -      |
| 3         | 2 | [10, 20, 30]            | -                | -                 | -      |
| Final     | - | [10, 20, 30]            | -                | -                 | `[10, 20, 30]` |

**Respuesta:** El programa imprime `[10, 20, 30]`

**Explicación:**
El lazo recorre cada posición de la lista y duplica su valor:
- Iteración 1 (`i=0`): `valores[0] = 5 * 2 = 10` → lista: `[10, 10, 15]`
- Iteración 2 (`i=1`): `valores[1] = 10 * 2 = 20` → lista: `[10, 20, 15]`
- Iteración 3 (`i=2`): `valores[2] = 15 * 2 = 30` → lista: `[10, 20, 30]`

:::{warning}
Es crucial entender que la lista se modifica **durante** el recorrido. Cada cambio es permanente.
:::

---

### Solución Ejercicio 9: Contar Pares

**Tabla completa:**

| Iteración | num | num % 2 | Condición `== 0` | contador | Salida |
|-----------|-----|---------|------------------|----------|--------|
| Inicial   | -   | -       | -                | 0        | -      |
| 1         | 7   | 1       | `False`          | 0        | -      |
| 2         | 12  | 0       | `True`           | 1        | -      |
| 3         | 5   | 1       | `False`          | 1        | -      |
| 4         | 8   | 0       | `True`           | 2        | -      |
| 5         | 3   | 1       | `False`          | 2        | -      |
| Final     | -   | -       | -                | 2        | `Pares: 2` |

**Respuesta:** El programa imprime `Pares: 2`

**Explicación:**
El lazo examina cada número y cuenta cuántos son pares:
- `7 % 2 = 1` → impar, no cuenta
- `12 % 2 = 0` → par, `contador = 1`
- `5 % 2 = 1` → impar, no cuenta
- `8 % 2 = 0` → par, `contador = 2`
- `3 % 2 = 1` → impar, no cuenta
- Total de pares: 2 (los números 12 y 8)

---

### Solución Ejercicio 10: Búsqueda del Mayor

**Tabla completa:**

| Iteración | i | datos[i] | maximo (antes) | Condición | maximo (después) | Salida |
|-----------|---|----------|----------------|-----------|------------------|--------|
| Inicial   | - | 23       | 23             | -         | 23               | -      |
| 1         | 1 | 45       | 23             | `45 > 23` → `True` | 45    | -      |
| 2         | 2 | 12       | 45             | `12 > 45` → `False` | 45   | -      |
| 3         | 3 | 67       | 45             | `67 > 45` → `True` | 67    | -      |
| 4         | 4 | 34       | 67             | `34 > 67` → `False` | 67   | -      |
| Final     | - | -        | 67             | -         | 67               | `Máximo: 67` |

**Respuesta:** El programa imprime `Máximo: 67`

**Explicación:**
Este es el algoritmo de búsqueda del máximo:
1. Inicializamos `maximo` con el primer elemento: 23
2. Recorremos el resto de la lista (desde índice 1):
   - Comparamos 45 con 23: 45 es mayor, actualizamos `maximo = 45`
   - Comparamos 12 con 45: 12 no es mayor, mantenemos `maximo = 45`
   - Comparamos 67 con 45: 67 es mayor, actualizamos `maximo = 67`
   - Comparamos 34 con 67: 34 no es mayor, mantenemos `maximo = 67`
3. El valor máximo encontrado es 67

:::{tip}
Este patrón es fundamental: siempre comenzamos con el primer elemento como "candidato" y luego lo comparamos con los demás.
:::

---

## Consejos para Hacer Pruebas de Escritorio

### Durante el Proceso

1. **Sé metódico:** No te saltés pasos, seguí línea por línea
2. **Actualizá siempre:** Cada vez que una variable cambia, anotalo
3. **Evaluá condiciones:** Escribí explícitamente `True` o `False`
4. **Marcá el flujo:** En lazos, indicá cuándo se repite o termina
5. **Verificá índices:** En listas, asegurate de que los índices sean válidos

### Errores Comunes a Evitar

:::{warning}
**Errores frecuentes al hacer pruebas de escritorio:**

- Olvidar actualizar una variable después de una asignación
- No seguir el flujo correcto en `if`/`else`
- Confundir el número de iteraciones en lazos
- Olvidar que los índices de listas empiezan en 0
- No verificar la condición del lazo antes de cada iteración
- Asumir valores en lugar de calcularlos paso a paso
:::

### Cómo Verificar tu Trabajo

1. **Ejecutá mentalmente:** Después de completar la tabla, relee el código con tus valores
2. **Verificá coherencia:** Los valores deben tener sentido lógico
3. **Comprobá con Python:** Si tenés dudas, ejecutá el código real
4. **Revisá lazos:** Contá manualmente las iteraciones esperadas

---

## Práctica Adicional

### Ejercicios Extra (sin solución)

Para seguir practicando, intentá resolver estos ejercicios por tu cuenta:

#### Extra 1: Lista Invertida

```python
original = [10, 20, 30, 40]
invertida = []
for i in range(len(original) - 1, -1, -1):
    invertida.append(original[i])
print(invertida)
```

#### Extra 2: Sumar Posiciones Pares

```python
numeros = [5, 8, 3, 12, 7, 6]
suma = 0
for i in range(0, len(numeros), 2):
    suma = suma + numeros[i]
print("Suma:", suma)
```

#### Extra 3: Reemplazar Negativos

```python
valores = [5, -3, 8, -1, 0, 4]
for i in range(len(valores)):
    if valores[i] < 0:
        valores[i] = 0
print(valores)
```

---

## Recursos para Seguir Aprendiendo

### Conceptos Clave Practicados

En estos ejercicios trabajaste con:

- ✅ **Variables:** Asignación y actualización de valores
- ✅ **Operadores:** Aritméticos (`+`, `-`, `*`, `//`, `%`) y de comparación (`>`, `<`, `>=`, `==`)
- ✅ **Estructuras de decisión:** `if`, `elif`, `else`
- ✅ **Lazos:** `while` y `for` con `range()`
- ✅ **Listas:** Acceso por índice, modificación, recorrido
- ✅ **Patrones:** Acumuladores, contadores, búsqueda

### Próximos Pasos

:::{tip}
Ahora que dominás las pruebas de escritorio en Python básico:

1. **Practicá con código más largo:** 15-20 líneas
2. **Agregá complejidad:** Listas anidadas (pero sin funciones aún)
3. **Depurá código con errores:** Buscá bugs usando pruebas de escritorio
4. **Combiná con `algo_python.md`:** Ordená código y verificalo con pruebas
5. **Escribí tus propios programas:** Verificalos antes de ejecutarlos
:::

### Relación con Otros Materiales

```
00_primeros_pasos.md (teoría) 
         ↓
programacion.md (Parte A: pruebas con diagramas/pseudo)
         ↓
escritorio_python.md (pruebas con Python) ← ESTÁS AQUÍ
         ↓
algo_python.md (ordenar código Python)
         ↓
programacion.md (Parte B: programar en Python)
```

---

## Conclusión

Las pruebas de escritorio son una herramienta poderosa para:

- 🔍 **Entender código** antes de ejecutarlo
- 🐛 **Encontrar errores** de lógica
- 🧠 **Desarrollar pensamiento algorítmico**
- ✍️ **Prepararte para exámenes** (muchos incluyen este tipo de ejercicios)
- 🎯 **Mejorar como programador** (lectura de código es fundamental)

:::{important}
**La clave está en la práctica constante.** No se trata de hacerlo rápido, sino de hacerlo correctamente. Con el tiempo, esta habilidad se vuelve automática y te ayudará enormemente en la programación real.
:::

---

**Total de ejercicios:** 10 principales + 3 extras  
**Dificultad:** Creciente (secuencial → lazos → listas)  
**Tiempo estimado:** 4-6 horas de práctica

¡Ahora es tu turno de practicar! 🚀
