# Ejercicios Parsons - Ordenar Código Python

## ¿Qué son los Problemas Parsons en Python?

Los **problemas Parsons** son ejercicios donde te dan todas las líneas de un programa en Python **desordenadas**, y tu tarea es **ordenarlas correctamente**. Es como armar un rompecabezas, pero con código real.

:::{tip} ¿Por Qué Practicar con Python Real?

Estos ejercicios te ayudan a:
- **Aprender la sintaxis** de Python sin escribir desde cero
- **Reconocer patrones** comunes en programación real
- **Entender la estructura** de programas Python
- **Practicar la indentación** correcta (fundamental en Python)
- **Prepararte para escribir** tus propios programas
- **Familiarizarte con nombres** de variables y funciones comunes

**Es el paso intermedio perfecto entre pseudocódigo y programar desde cero.**
:::

---

## Cómo Resolver un Problema Parsons en Python

**Proceso paso a paso:**

1. **Leer el enunciado** y entender qué debe hacer el programa
2. **Identificar la estructura general:**
   - ¿Usa `input()` para entrada?
   - ¿Usa `print()` para salida?
   - ¿Tiene `if`/`else`?
   - ¿Tiene `while` o `for`?
   - ¿Define funciones con `def`?
3. **Buscar las entradas primero** - generalmente van al principio
4. **Agrupar bloques relacionados:**
   - La indentación es **crucial** en Python
   - Bloques `if`, `while`, `for`, `def` tienen líneas indentadas
5. **Verificar el orden lógico:**
   - Variables usadas después de ser creadas
   - Funciones definidas antes de ser llamadas
   - `print()` generalmente al final

---

## Sintaxis de Python Usada

Esta es la sintaxis que usamos en estos ejercicios:

| Elemento | Sintaxis | Ejemplo |
|:---------|:---------|:--------|
| Comentario | `# texto` | `# Calcular el total` |
| Entrada | `input()` | `nombre = input("Tu nombre: ")` |
| Entrada numérica | `int(input())` | `edad = int(input("Edad: "))` |
| Salida | `print()` | `print("Hola", nombre)` |
| Asignación | `variable = valor` | `suma = a + b` |
| Condición | `if condicion:` | `if edad >= 18:` |
| Sino | `else:` | `else:` |
| Sino si | `elif condicion:` | `elif nota >= 6:` |
| Lazo while | `while condicion:` | `while i <= 10:` |
| Lazo for | `for var in range():` | `for i in range(1, 11):` |
| Función | `def nombre():` | `def saludar():` |
| Retorno | `return valor` | `return resultado` |
| Llamada | `nombre()` | `saludar()` |

:::{important} Indentación en Python

En Python, la **indentación** (espacios al inicio) no es opcional:
- Usa **4 espacios** para cada nivel de indentación
- Todo lo que va "dentro" de un bloque (`if`, `while`, `for`, `def`) debe estar indentado
- Si la indentación está mal, **el programa no funciona**

```python
# ✅ Correcto
if edad >= 18:
    print("Mayor de edad")
    print("Puede votar")

# ❌ Incorrecto (sin indentación)
if edad >= 18:
print("Mayor de edad")
```
:::

---

## Ejercicios

Los ejercicios están ordenados por **dificultad creciente** y **longitud creciente**:

- **Ejercicios 1-4:** Secuenciales simples (3-5 líneas)
- **Ejercicios 5-8:** Con decisiones (`if`/`else`) (5-8 líneas)
- **Ejercicios 9-12:** Con lazos simples (`while`/`for`) (6-10 líneas)
- **Ejercicios 13-16:** Decisiones y lazos combinados (8-12 líneas)
- **Ejercicios 17-20:** Con funciones (`def`/`return`) (10-15 líneas)

---

## Nivel 1: Secuenciales Simples (Ejercicios 1-4)

---

### Ejercicio 1: Saludo Simple

**Enunciado:** Pedir el nombre del usuario y saludarlo.

**Líneas desordenadas:**

```python
nombre = input("¿Cómo te llamas? ")
print("¡Hola,", nombre, "!")
```

**Pistas:**
- Primero leer, después mostrar
- `input()` siempre devuelve texto (string)

---

### Ejercicio 2: Sumar Dos Números

**Enunciado:** Pedir dos números y mostrar su suma.

**Líneas desordenadas:**

```python
num1 = int(input("Primer número: "))
print("La suma es:", suma)
num2 = int(input("Segundo número: "))
suma = num1 + num2
```

**Pistas:**
- `int(input())` convierte el texto a número entero
- Necesitamos ambos números antes de sumar
- Calcular antes de mostrar

---

### Ejercicio 3: Calcular Promedio

**Enunciado:** Pedir tres notas y calcular el promedio.

**Líneas desordenadas:**

```python
nota2 = int(input("Segunda nota: "))
promedio = suma / 3
print("El promedio es:", promedio)
suma = nota1 + nota2 + nota3
nota1 = int(input("Primera nota: "))
nota3 = int(input("Tercera nota: "))
```

**Pistas:**
- Leer las tres notas primero
- Sumarlas, después dividir por 3
- El orden de lectura debe ser lógico

---

### Ejercicio 4: Área de Rectángulo

**Enunciado:** Pedir base y altura, calcular el área de un rectángulo.

**Líneas desordenadas:**

```python
area = base * altura
base = int(input("Base: "))
altura = int(input("Altura: "))
print("El área es:", area)
```

**Pistas:**
- Área = base × altura
- Necesitamos ambos valores antes de calcular

---

## Nivel 2: Con Decisiones (Ejercicios 5-8)

---

### Ejercicio 5: Mayor de Edad

**Enunciado:** Pedir la edad y decir si es mayor o menor de edad.

**Líneas desordenadas:**

```python
edad = int(input("Tu edad: "))
else:
    print("Sos menor de edad")
if edad >= 18:
    print("Sos mayor de edad")
```

**Pistas:**
- El `if` termina con `:`
- Lo indentado va dentro del `if`
- El `else` va al mismo nivel que el `if`

---

### Ejercicio 6: Número Par o Impar

**Enunciado:** Pedir un número y decir si es par o impar.

**Líneas desordenadas:**

```python
numero = int(input("Ingrese un número: "))
    print("Es par")
if numero % 2 == 0:
else:
    print("Es impar")
```

**Pistas:**
- `%` es el operador módulo (resto de la división)
- Si el resto al dividir por 2 es 0, es par
- Cuidado con la indentación

---

### Ejercicio 7: Calificación

**Enunciado:** Pedir una nota (0-10) y mostrar: "Excelente" (9-10), "Aprobado" (6-8), "Desaprobado" (0-5).

**Líneas desordenadas:**

```python
elif nota >= 6:
    print("Excelente")
nota = int(input("Nota: "))
    print("Desaprobado")
if nota >= 9:
else:
    print("Aprobado")
```

**Pistas:**
- Usar `if`, `elif`, `else` en ese orden
- Verificar primero la nota más alta
- Cuidado con la indentación de cada bloque

---

### Ejercicio 8: Descuento por Monto

**Enunciado:** Si la compra es mayor a 1000, aplicar 10% de descuento. Mostrar el total final.

**Líneas desordenadas:**

```python
monto = int(input("Monto de compra: "))
    total = monto - descuento
if monto > 1000:
print("Total a pagar:", total)
else:
    descuento = monto * 0.10
    total = monto
```

**Pistas:**
- Si hay descuento, calcular y restar
- Si no, el total es el monto original
- Ambas ramas calculan `total`

---

## Nivel 3: Con Lazos Simples (Ejercicios 9-12)

---

### Ejercicio 9: Contar del 1 al 5

**Enunciado:** Mostrar los números del 1 al 5 usando `while`.

**Líneas desordenadas:**

```python
    print(i)
i = 1
    i = i + 1
while i <= 5:
```

**Pistas:**
- Inicializar `i` antes del lazo
- Condición: `i <= 5`
- Incrementar `i` dentro del lazo

---

### Ejercicio 10: Tabla de Multiplicar

**Enunciado:** Pedir un número y mostrar su tabla del 1 al 10 usando `for`.

**Líneas desordenadas:**

```python
    print(numero, "x", i, "=", numero * i)
numero = int(input("Número: "))
for i in range(1, 11):
```

**Pistas:**
- `range(1, 11)` genera números del 1 al 10
- `for` itera automáticamente
- Dentro del `for`, calcular y mostrar

---

### Ejercicio 11: Sumar Números Hasta N

**Enunciado:** Pedir N y calcular la suma de 1 hasta N usando `while`.

**Líneas desordenadas:**

```python
suma = 0
while i <= n:
i = 1
    suma = suma + i
print("La suma es:", suma)
    i = i + 1
n = int(input("N: "))
```

**Pistas:**
- Inicializar `suma` en 0 (acumulador)
- Inicializar `i` en 1 (contador)
- Acumular dentro del lazo
- Incrementar `i`

---

### Ejercicio 12: Contar Pares Hasta N

**Enunciado:** Pedir N y mostrar todos los números pares del 2 hasta N usando `for`.

**Líneas desordenadas:**

```python
    print(i)
for i in range(2, n + 1, 2):
n = int(input("N: "))
```

**Pistas:**
- `range(2, n + 1, 2)` genera pares: 2, 4, 6, ...
- El tercer parámetro (2) es el "paso"
- `n + 1` porque `range` no incluye el final

---

## Nivel 4: Combinados (Ejercicios 13-16)

---

### Ejercicio 13: Validar Entrada

**Enunciado:** Pedir un número entre 1 y 10. Si no es válido, seguir pidiendo hasta que lo sea.

**Líneas desordenadas:**

```python
while numero < 1 or numero > 10:
numero = int(input("Número (1-10): "))
    numero = int(input("Error. Número (1-10): "))
print("Número válido:", numero)
```

**Pistas:**
- Leer una vez antes del `while`
- Si no es válido, leer de nuevo dentro del lazo
- Salir cuando sea válido

---

### Ejercicio 14: Sumar Pares e Impares

**Enunciado:** Pedir N números y mostrar la suma de los pares y la suma de los impares por separado.

**Líneas desordenadas:**

```python
    if num % 2 == 0:
n = int(input("Cantidad de números: "))
for i in range(n):
        suma_impares = suma_impares + num
    else:
suma_pares = 0
print("Suma de pares:", suma_pares)
suma_impares = 0
        suma_pares = suma_pares + num
print("Suma de impares:", suma_impares)
    num = int(input("Número: "))
```

**Pistas:**
- Inicializar dos acumuladores
- Usar `for` para repetir N veces
- Dentro del `for`, leer y decidir si es par
- Sumar al acumulador correspondiente

---

### Ejercicio 15: Encontrar el Mayor

**Enunciado:** Pedir N números y encontrar cuál es el mayor.

**Líneas desordenadas:**

```python
for i in range(n):
n = int(input("Cantidad de números: "))
mayor = -999999
    if num > mayor:
print("El mayor es:", mayor)
        mayor = num
    num = int(input("Número: "))
```

**Pistas:**
- Inicializar `mayor` con un valor muy pequeño
- Usar `for` para leer N números
- Comparar cada número con el mayor actual
- Actualizar si encontramos uno más grande

---

### Ejercicio 16: Contar Dígitos

**Enunciado:** Pedir un número y contar cuántos dígitos tiene.

**Líneas desordenadas:**

```python
while numero > 0:
numero = int(input("Número: "))
print("Tiene", contador, "dígitos")
    numero = numero // 10
contador = 0
    contador = contador + 1
```

**Pistas:**
- `//` es división entera (descarta decimales)
- Dividir por 10 elimina el último dígito
- Contar cuántas veces se puede dividir

---

## Nivel 5: Con Funciones (Ejercicios 17-20)

---

### Ejercicio 17: Función Saludo

**Enunciado:** Definir una función que reciba un nombre y lo salude. Luego llamarla.

**Líneas desordenadas:**

```python
def saludar(nombre):
    print("¡Hola,", nombre, "!")

usuario = input("Tu nombre: ")
saludar(usuario)
```

**Pistas:**
- Primero definir la función con `def`
- La función tiene un parámetro `nombre`
- Después del `def`, leer y llamar

---

### Ejercicio 18: Función Calcular Área

**Enunciado:** Definir una función que calcule el área de un rectángulo y retorne el resultado. Luego usarla.

**Líneas desordenadas:**

```python
base = int(input("Base: "))
def calcular_area(base, altura):
    return base * altura

resultado = calcular_area(base, altura)
altura = int(input("Altura: "))
print("El área es:", resultado)
```

**Pistas:**
- Definir la función primero
- `return` devuelve el resultado
- Leer los datos
- Llamar a la función con los datos
- Guardar el resultado y mostrarlo

---

### Ejercicio 19: Función Par o Impar

**Enunciado:** Definir una función que determine si un número es par. Usarla en un programa que pide un número.

**Líneas desordenadas:**

```python
    return True
def es_par(numero):
numero = int(input("Número: "))
else:
    print("Es impar")
    return False
if es_par(numero):
if numero % 2 == 0:
    print("Es par")
```

**Pistas:**
- La función retorna `True` o `False`
- Definir la función primero
- Después, leer el número
- Llamar a la función en el `if`

---

### Ejercicio 20: Función Factorial

**Enunciado:** Definir una función que calcule el factorial de un número. Usarla después de validar que el número no sea negativo.

**Líneas desordenadas:**

```python
n = int(input("Número: "))
    for i in range(1, n + 1):
def factorial(n):
    resultado = 1
    return resultado
        resultado = resultado * i

if n < 0:
else:
    print("El factorial es:", factorial(n))
    print("Error: no existe factorial de negativos")
```

**Pistas:**
- Definir la función primero
- Inicializar `resultado` en 1
- Usar `for` para multiplicar
- Retornar el resultado
- Después, leer N, validar y llamar

---

## Soluciones

:::{admonition} 💡 Antes de Ver las Soluciones
:class: warning

**¡Intentá resolver los ejercicios vos mismo primero!**

Estos ejercicios son para **practicar reconocer la estructura** de programas Python reales.

Solo mirá las soluciones si:
- Ya lo intentaste varias veces
- Querés verificar tu respuesta
- No entendés por qué va en ese orden

:::

---

## Soluciones Nivel 1 (1-4)

### Solución Ejercicio 1: Saludo Simple

```python
nombre = input("¿Cómo te llamas? ")
print("¡Hola,", nombre, "!")
```

**Explicación:**
- `input()` lee texto del usuario y lo guarda en `nombre`
- `print()` muestra el mensaje usando la variable `nombre`

---

### Solución Ejercicio 2: Sumar Dos Números

```python
num1 = int(input("Primer número: "))
num2 = int(input("Segundo número: "))
suma = num1 + num2
print("La suma es:", suma)
```

**Explicación:**
- `int(input())` lee y convierte a entero
- Primero leemos ambos números
- Después calculamos la suma
- Finalmente mostramos el resultado

---

### Solución Ejercicio 3: Calcular Promedio

```python
nota1 = int(input("Primera nota: "))
nota2 = int(input("Segunda nota: "))
nota3 = int(input("Tercera nota: "))
suma = nota1 + nota2 + nota3
promedio = suma / 3
print("El promedio es:", promedio)
```

**Explicación:**
- Leer las tres notas en orden
- Sumarlas
- Dividir por 3 para obtener el promedio
- Mostrar el resultado

---

### Solución Ejercicio 4: Área de Rectángulo

```python
base = int(input("Base: "))
altura = int(input("Altura: "))
area = base * altura
print("El área es:", area)
```

**Explicación:**
- Fórmula: área = base × altura
- Leer ambos valores
- Calcular
- Mostrar

---

## Soluciones Nivel 2 (5-8)

### Solución Ejercicio 5: Mayor de Edad

```python
edad = int(input("Tu edad: "))
if edad >= 18:
    print("Sos mayor de edad")
else:
    print("Sos menor de edad")
```

**Explicación:**
- Leer la edad
- `if edad >= 18:` verifica la condición
- Las líneas indentadas se ejecutan si es verdadero
- `else:` cubre el caso contrario
- También necesita indentación

---

### Solución Ejercicio 6: Número Par o Impar

```python
numero = int(input("Ingrese un número: "))
if numero % 2 == 0:
    print("Es par")
else:
    print("Es impar")
```

**Explicación:**
- `%` da el resto de la división
- Si el resto al dividir por 2 es 0, es par
- Si no, es impar

---

### Solución Ejercicio 7: Calificación

```python
nota = int(input("Nota: "))
if nota >= 9:
    print("Excelente")
elif nota >= 6:
    print("Aprobado")
else:
    print("Desaprobado")
```

**Explicación:**
- `if` para la primera condición (9-10)
- `elif` para la segunda condición (6-8)
- `else` para el resto (0-5)
- Verificamos de mayor a menor

---

### Solución Ejercicio 8: Descuento por Monto

```python
monto = int(input("Monto de compra: "))
if monto > 1000:
    descuento = monto * 0.10
    total = monto - descuento
else:
    total = monto
print("Total a pagar:", total)
```

**Explicación:**
- Si monto > 1000: calcular descuento (10%) y restar
- Si no: el total es el monto sin cambios
- En ambos casos, creamos la variable `total`
- La mostramos después del `if`/`else`

---

## Soluciones Nivel 3 (9-12)

### Solución Ejercicio 9: Contar del 1 al 5

```python
i = 1
while i <= 5:
    print(i)
    i = i + 1
```

**Explicación:**
- Inicializar `i` en 1
- `while i <= 5:` verifica la condición
- Dentro: mostrar `i` e incrementarlo
- El lazo se repite 5 veces (i = 1, 2, 3, 4, 5)

---

### Solución Ejercicio 10: Tabla de Multiplicar

```python
numero = int(input("Número: "))
for i in range(1, 11):
    print(numero, "x", i, "=", numero * i)
```

**Explicación:**
- Leer el número de la tabla
- `range(1, 11)` genera 1, 2, 3, ..., 10
- `for i in range(...)` itera sobre cada valor
- Dentro: calcular y mostrar resultado

---

### Solución Ejercicio 11: Sumar Números Hasta N

```python
n = int(input("N: "))
suma = 0
i = 1
while i <= n:
    suma = suma + i
    i = i + 1
print("La suma es:", suma)
```

**Explicación:**
- Leer N
- Inicializar `suma` en 0 (acumulador)
- Inicializar `i` en 1 (contador)
- Mientras `i <= n`: sumar `i` a `suma` e incrementar `i`
- Resultado: 1 + 2 + 3 + ... + N

---

### Solución Ejercicio 12: Contar Pares Hasta N

```python
n = int(input("N: "))
for i in range(2, n + 1, 2):
    print(i)
```

**Explicación:**
- `range(2, n + 1, 2)` genera: 2, 4, 6, 8, ...
- El 2 inicial es el inicio
- El `n + 1` porque range no incluye el final
- El 2 final es el "paso" (incremento)

---

## Soluciones Nivel 4 (13-16)

### Solución Ejercicio 13: Validar Entrada

```python
numero = int(input("Número (1-10): "))
while numero < 1 or numero > 10:
    numero = int(input("Error. Número (1-10): "))
print("Número válido:", numero)
```

**Explicación:**
- Leer una vez antes del `while`
- Si no está en [1, 10], entra al lazo
- Dentro: mostrar error y leer de nuevo
- Sale cuando el número sea válido

---

### Solución Ejercicio 14: Sumar Pares e Impares

```python
n = int(input("Cantidad de números: "))
suma_pares = 0
suma_impares = 0
for i in range(n):
    num = int(input("Número: "))
    if num % 2 == 0:
        suma_pares = suma_pares + num
    else:
        suma_impares = suma_impares + num
print("Suma de pares:", suma_pares)
print("Suma de impares:", suma_impares)
```

**Explicación:**
- Inicializar dos acumuladores en 0
- `for i in range(n)` repite N veces
- Dentro: leer cada número
- Verificar si es par (`% 2 == 0`)
- Sumar al acumulador correspondiente
- Mostrar ambas sumas al final

---

### Solución Ejercicio 15: Encontrar el Mayor

```python
n = int(input("Cantidad de números: "))
mayor = -999999
for i in range(n):
    num = int(input("Número: "))
    if num > mayor:
        mayor = num
print("El mayor es:", mayor)
```

**Explicación:**
- Inicializar `mayor` con un valor muy bajo
- Leer N números
- Para cada uno: si es mayor que el actual, actualizarlo
- Al final, `mayor` tiene el valor más grande

---

### Solución Ejercicio 16: Contar Dígitos

```python
numero = int(input("Número: "))
contador = 0
while numero > 0:
    numero = numero // 10
    contador = contador + 1
print("Tiene", contador, "dígitos")
```

**Explicación:**
- `//` es división entera (sin decimales)
- Dividir por 10 elimina el último dígito
- Ejemplo: 12345 → 1234 → 123 → 12 → 1 → 0
- Contar cuántas divisiones se hacen
- Ese es el número de dígitos

---

## Soluciones Nivel 5 (17-20)

### Solución Ejercicio 17: Función Saludo

```python
def saludar(nombre):
    print("¡Hola,", nombre, "!")

usuario = input("Tu nombre: ")
saludar(usuario)
```

**Explicación:**
- `def saludar(nombre):` define la función con un parámetro
- Dentro de la función: usar el parámetro
- Después: leer el dato
- Llamar a la función pasando el dato

---

### Solución Ejercicio 18: Función Calcular Área

```python
def calcular_area(base, altura):
    return base * altura

base = int(input("Base: "))
altura = int(input("Altura: "))
resultado = calcular_area(base, altura)
print("El área es:", resultado)
```

**Explicación:**
- Definir la función con dos parámetros
- `return` devuelve el resultado del cálculo
- Leer los datos necesarios
- Llamar a la función con esos datos
- Guardar el resultado en una variable
- Mostrarlo

---

### Solución Ejercicio 19: Función Par o Impar

```python
def es_par(numero):
    if numero % 2 == 0:
        return True
    else:
        return False

numero = int(input("Número: "))
if es_par(numero):
    print("Es par")
else:
    print("Es impar")
```

**Explicación:**
- La función retorna `True` si es par, `False` si no
- Definir la función primero
- Leer el número
- Usar la función en el `if`: si retorna `True`, imprime "Es par"
- Si retorna `False`, imprime "Es impar"

**Nota alternativa:** Esta función se puede simplificar a `return numero % 2 == 0`, pero usamos la forma explícita para claridad.

---

### Solución Ejercicio 20: Función Factorial

```python
def factorial(n):
    resultado = 1
    for i in range(1, n + 1):
        resultado = resultado * i
    return resultado

n = int(input("Número: "))
if n < 0:
    print("Error: no existe factorial de negativos")
else:
    print("El factorial es:", factorial(n))
```

**Explicación:**
- Función `factorial(n)`:
  - Inicializar `resultado` en 1
  - Multiplicar por cada número de 1 a n
  - Retornar el resultado
- Programa principal:
  - Leer N
  - Validar que no sea negativo
  - Si es válido, llamar a la función y mostrar
  - Si no, mostrar error

**Casos especiales:**
- `factorial(0)` = 1 (el `for` no se ejecuta)
- `factorial(1)` = 1 (el `for` ejecuta una vez: 1 × 1)
- `factorial(5)` = 120 (1 × 2 × 3 × 4 × 5)

---

## Consejos para Resolver Problemas Parsons en Python

:::{tip} Estrategias Efectivas

**1. La indentación es crucial:**
   - Python usa indentación para definir bloques
   - Todo después de `:` debe estar indentado (4 espacios)
   - Bloques: `if`, `else`, `elif`, `while`, `for`, `def`

**2. Orden típico de un programa:**
   - Definiciones de funciones (si hay)
   - Entradas (`input`)
   - Procesos (cálculos, decisiones, lazos)
   - Salidas (`print`)

**3. Reconoce patrones comunes:**
   - `int(input())` para números
   - `if ... else:` para decisiones
   - `while` con incremento dentro
   - `for` con `range()`
   - `def` al principio, llamada después

**4. Variables antes de uso:**
   - Una variable debe existir antes de usarse
   - Acumuladores se inicializan en 0
   - Contadores se inicializan según el problema

**5. Funciones:**
   - Definir (`def`) antes de llamar
   - Parámetros en la definición, argumentos en la llamada
   - `return` devuelve el resultado

:::

:::{important} Errores Comunes en Python

❌ **Olvidar los dos puntos (`:`):**
   ```python
   if edad >= 18  # ❌ Falta :
       print("Mayor")
   ```

❌ **Indentación incorrecta:**
   ```python
   if edad >= 18:
   print("Mayor")  # ❌ No está indentado
   ```

❌ **Usar `input()` sin `int()` para números:**
   ```python
   edad = input("Edad: ")  # Esto es texto
   if edad >= 18:  # ❌ No se puede comparar texto con número
   ```

❌ **Olvidar incrementar en `while`:**
   ```python
   i = 1
   while i <= 5:
       print(i)
       # ❌ Falta: i = i + 1 → Lazo infinito
   ```

❌ **Llamar función antes de definirla:**
   ```python
   saludar("Ana")  # ❌ Error: saludar no está definida aún
   def saludar(nombre):
       print("Hola", nombre)
   ```

❌ **Confundir `=` con `==`:**
   ```python
   if edad = 18:  # ❌ = es asignación
   if edad == 18:  # ✅ == es comparación
   ```

:::

---

## Tabla de Equivalencias: Pseudocódigo vs Python

Para quienes vienen del pseudocódigo, esta tabla ayuda:

| Pseudocódigo | Python | Notas |
|:-------------|:-------|:------|
| `INICIO Algoritmo` | *(no se usa)* | Python no necesita marca de inicio |
| `FIN` | *(no se usa)* | Python termina al acabar el archivo |
| `LEER variable` | `variable = input()` | Para texto |
| `LEER numero` | `numero = int(input())` | Para números |
| `MOSTRAR mensaje` | `print(mensaje)` | Salida en pantalla |
| `variable ⟸ valor` | `variable = valor` | Asignación |
| `SI condicion ENTONCES` | `if condicion:` | Requiere `:` |
| `SINO` | `else:` | Requiere `:` |
| `FIN_SI` | *(indentación)* | El bloque termina al volver a nivel anterior |
| `MIENTRAS condicion HACER` | `while condicion:` | Requiere `:` |
| `FIN_MIENTRAS` | *(indentación)* | El bloque termina al volver a nivel anterior |
| `PARA i DESDE 1 HASTA 10` | `for i in range(1, 11):` | `range` no incluye el final |
| `FIN_PARA` | *(indentación)* | El bloque termina al volver a nivel anterior |
| `# comentario` | `# comentario` | ¡Igual! |

---

## Diferencias Importantes: Pseudocódigo vs Python

:::{note} Diferencias Clave

**1. Indentación obligatoria:**
   - Pseudocódigo: la indentación es para legibilidad
   - Python: la indentación define la estructura del programa

**2. Palabras clave en inglés:**
   - Pseudocódigo: `SI`, `MIENTRAS`, `LEER`, `MOSTRAR`
   - Python: `if`, `while`, `input`, `print`

**3. Marcadores de inicio/fin:**
   - Pseudocódigo: `INICIO`, `FIN`, `FIN_SI`, `FIN_MIENTRAS`
   - Python: usa `:` e indentación (no necesita marcadores de fin)

**4. Conversión de tipos:**
   - Pseudocódigo: automático
   - Python: explícito (`int()`, `float()`, `str()`)

**5. Funciones:**
   - Pseudocódigo: varía según la notación
   - Python: `def nombre(parametros):` con `return`

:::

---

## Ejemplos Completos Comentados

### Ejemplo 1: Programa Secuencial

```python
# Pedir datos
nombre = input("Tu nombre: ")
edad = int(input("Tu edad: "))

# Calcular
anios_para_100 = 100 - edad

# Mostrar resultado
print(nombre, ", te faltan", anios_para_100, "años para llegar a 100")
```

### Ejemplo 2: Programa con Decisión

```python
# Pedir nota
nota = int(input("Nota (0-10): "))

# Decidir según la nota
if nota >= 6:
    print("Aprobado")
else:
    print("Desaprobado")
```

### Ejemplo 3: Programa con Lazo

```python
# Pedir límite
limite = int(input("Contar hasta: "))

# Inicializar contador
i = 1

# Lazo
while i <= limite:
    print(i)
    i = i + 1

print("¡Terminado!")
```

### Ejemplo 4: Programa con Función

```python
# Definir función
def calcular_cuadrado(numero):
    return numero * numero

# Programa principal
x = int(input("Número: "))
resultado = calcular_cuadrado(x)
print("El cuadrado es:", resultado)
```

---

## Ejercicios Extras para Practicar

Si querés más desafío, intentá ordenar estos programas:

### Extra 1: Promedio con Validación

```python
nota1 = int(input("Nota 1: "))
nota2 = int(input("Nota 2: "))
nota3 = int(input("Nota 3: "))
promedio = (nota1 + nota2 + nota3) / 3
if promedio >= 6:
    print("Aprobado con promedio:", promedio)
else:
    print("Desaprobado con promedio:", promedio)
```

### Extra 2: Fibonacci con Función

```python
def fibonacci(n):
    a = 0
    b = 1
    for i in range(n):
        print(a)
        temp = a
        a = b
        b = temp + b

n = int(input("Cuántos términos: "))
fibonacci(n)
```

### Extra 3: Juego de Adivinanza

```python
secreto = 42
print("Adivina el número (1-100)")
intento = int(input("Tu intento: "))
while intento != secreto:
    if intento < secreto:
        print("Es mayor")
    else:
        print("Es menor")
    intento = int(input("Otro intento: "))
print("¡Correcto!")
```

---

## Recursos Adicionales

:::{tip} Para Seguir Practicando

Una vez que domines estos ejercicios Parsons:

1. **Escribí tus propios programas** desde cero
2. **Modifica los ejercicios:** cambia las condiciones, agrega funcionalidad
3. **Combina conceptos:** usa funciones con lazos, decisiones dentro de funciones
4. **Practica la indentación:** es fundamental en Python
5. **Lee código de otros:** aprende de ejemplos bien escritos

:::

---

**¡Éxitos practicando con Python! 🐍**

*Recordá: estos ejercicios son el puente perfecto entre entender la lógica y escribir código real. La indentación en Python es clave, ¡prestale atención!*
