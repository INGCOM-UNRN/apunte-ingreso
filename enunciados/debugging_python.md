# Ejercicios de Debugging - Python

## Introducción

El **debugging** (depuración) es una habilidad fundamental en programación. Estos ejercicios te ayudarán a desarrollar tu capacidad para:

- Identificar errores de sintaxis
- Detectar errores lógicos
- Corregir problemas de tipos de datos
- Resolver errores comunes de Python

:::{important} Metodología
Para cada ejercicio:

1. **Lee el código** cuidadosamente
2. **Identifica el error** (puede haber más de uno)
3. **Explica** qué está mal
4. **Corrige** el código
5. **Verifica** que funciona correctamente
:::

---

## Ejercicio 1: Error de Indentación

**Código con error:**

```python
def saludar(nombre):
print(f"Hola, {nombre}!")
    return True
```

**Tarea:** Encuentra y corrige el error de indentación.

**Pista:** Python usa indentación para definir bloques de código.

---

## Ejercicio 2: Variable No Definida

**Código con error:**

```python
edad = 18
if edad >= 18:
    mensaje = "Sos mayor de edad"
else:
    mensaje = "Sos menor de edad"

print(Mensaje)  # ¿Qué está mal aquí?
```

**Tarea:** El código da error de `NameError`. ¿Por qué?

**Pista:** Python distingue entre mayúsculas y minúsculas.

---

## Ejercicio 3: División por Cero

**Código con error:**

```python
def calcular_promedio(suma, cantidad):
    return suma / cantidad

total = 100
cant = 0
promedio = calcular_promedio(total, cant)
print(f"Promedio: {promedio}")
```

**Tarea:** El código causa un `ZeroDivisionError`. Modifica la función para manejar este caso.

**Pista:** Valida que `cantidad` no sea cero antes de dividir.

---

## Ejercicio 4: Error de Tipo

**Código con error:**

```python
edad = input("¿Cuántos años tenés? ")

if edad >= 18:
    print("Podés votar")
else:
    print("No podés votar todavía")
```

**Tarea:** El código da `TypeError`. ¿Por qué?

**Pista:** `input()` siempre devuelve un string.

---

## Ejercicio 5: Índice Fuera de Rango

**Código con error:**

```python
frutas = ["manzana", "banana", "naranja"]

print(f"Primera fruta: {frutas[0]}")
print(f"Segunda fruta: {frutas[1]}")
print(f"Tercera fruta: {frutas[2]}")
print(f"Cuarta fruta: {frutas[3]}")
```

**Tarea:** El código causa `IndexError`. ¿Cómo lo solucionás?

**Pista:** Los índices válidos para esta lista son 0, 1 y 2.

---

## Ejercicio 6: Error en Bucle Infinito

**Código con error:**

```python
contador = 1
while contador <= 5:
    print(f"Iteración {contador}")
    # Falta algo aquí...

print("Terminado!")
```

**Tarea:** Este código crea un bucle infinito. ¿Qué falta?

**Pista:** La variable de control debe cambiar en cada iteración.

---

## Ejercicio 7: Parámetros Faltantes

**Código con error:**

```python
def calcular_area_rectangulo(base, altura):
    return base * altura

# Intentamos calcular el área
area = calcular_area_rectangulo(5)
print(f"Área: {area}")
```

**Tarea:** El código da `TypeError`. ¿Qué parámetro falta?

**Pista:** La función requiere dos argumentos.

---

## Ejercicio 8: Comparación vs Asignación

**Código con error:**

```python
numero = 10

if numero = 10:
    print("El número es 10")
else:
    print("El número no es 10")
```

**Tarea:** Error de sintaxis. ¿Qué operador debería usarse?

**Pista:** `=` es asignación, `==` es comparación.

---

## Ejercicio 9: Concatenación de Tipos Incompatibles

**Código con error:**

```python
nombre = "Juan"
edad = 25

mensaje = "Hola, me llamo " + nombre + " y tengo " + edad + " años"
print(mensaje)
```

**Tarea:** `TypeError` al intentar concatenar. ¿Cómo lo solucionás?

**Pista:** No podés concatenar strings con números directamente.

---

## Ejercicio 10: Error en Diccionario

**Código con error:**

```python
estudiante = {
    "nombre": "María",
    "edad": 20,
    "carrera": "Ingeniería"
}

print(f"Nombre: {estudiante['nombre']}")
print(f"Promedio: {estudiante['promedio']}")
```

**Tarea:** `KeyError` al acceder al diccionario. ¿Por qué?

**Pista:** Estás intentando acceder a una clave que no existe.

---

## Ejercicio 11: Modificación de String

**Código con error:**

```python
texto = "hola mundo"
texto[0] = "H"  # Intentamos cambiar la primera letra
print(texto)
```

**Tarea:** `TypeError`. ¿Por qué no funciona?

**Pista:** Los strings en Python son inmutables.

---

## Ejercicio 12: Return en el Lugar Incorrecto

**Código con error:**

```python
def sumar_lista(numeros):
    total = 0
    for num in numeros:
        total += num
        return total  # ¿Está bien ubicado?

resultado = sumar_lista([1, 2, 3, 4, 5])
print(f"Suma: {resultado}")
```

**Tarea:** El código solo suma el primer número. ¿Por qué?

**Pista:** ¿Cuándo debe ejecutarse el `return`?

---

## Ejercicio 13: Scope de Variables

**Código con error:**

```python
def incrementar():
    contador = contador + 1
    return contador

contador = 0
print(incrementar())
```

**Tarea:** `UnboundLocalError`. ¿Qué está pasando?

**Pista:** El problema está relacionado con el scope de la variable.

---

## Ejercicio 14: Error Lógico en Condición

**Código con error:**

```python
def es_par(numero):
    if numero % 2 == 1:
        return True
    else:
        return False

print(f"¿4 es par? {es_par(4)}")
print(f"¿7 es par? {es_par(7)}")
```

**Tarea:** El código funciona pero da resultados incorrectos. ¿Cuál es el error lógico?

**Pista:** Un número es par cuando el resto es 0, no 1.

---

## Ejercicio 15: Lista Mutada en Bucle

**Código con error:**

```python
numeros = [1, 2, 3, 4, 5]

for num in numeros:
    if num % 2 == 0:
        numeros.remove(num)

print(f"Números impares: {numeros}")
```

**Tarea:** El código no elimina todos los pares. ¿Por qué?

**Pista:** Modificar una lista mientras la iterás puede causar problemas.

---

## Soluciones

:::{admonition} 💡 Antes de Ver las Soluciones
:class: warning

Intentá resolver cada ejercicio por tu cuenta primero. El aprendizaje real viene de:

1. Identificar el problema
2. Pensar en la solución
3. Implementar la corrección
4. Verificar que funciona

Solo consultá las soluciones después de intentarlo.
:::

### Solución 1: Error de Indentación

```python
def saludar(nombre):
    print(f"Hola, {nombre}!")  # ✓ Indentación correcta
    return True
```

**Explicación:** Todas las líneas dentro de la función deben tener la misma indentación (4 espacios).

---

### Solución 2: Variable No Definida

```python
edad = 18
if edad >= 18:
    mensaje = "Sos mayor de edad"
else:
    mensaje = "Sos menor de edad"

print(mensaje)  # ✓ Minúscula correcta
```

**Explicación:** Python es case-sensitive. `Mensaje` ≠ `mensaje`.

---

### Solución 3: División por Cero

```python
def calcular_promedio(suma, cantidad):
    if cantidad == 0:
        return 0  # O podríamos retornar None o lanzar una excepción
    return suma / cantidad

total = 100
cant = 0
promedio = calcular_promedio(total, cant)
print(f"Promedio: {promedio}")
```

**Explicación:** Siempre validá divisiones por cero antes de ejecutarlas.

---

### Solución 4: Error de Tipo

```python
edad = int(input("¿Cuántos años tenés? "))  # ✓ Convertir a int

if edad >= 18:
    print("Podés votar")
else:
    print("No podés votar todavía")
```

**Explicación:** `input()` devuelve un string. Usá `int()` para convertirlo a número.

---

### Solución 5: Índice Fuera de Rango

```python
frutas = ["manzana", "banana", "naranja"]

print(f"Primera fruta: {frutas[0]}")
print(f"Segunda fruta: {frutas[1]}")
print(f"Tercera fruta: {frutas[2]}")
# print(f"Cuarta fruta: {frutas[3]}")  # ✗ Eliminado o corregido

# Alternativa segura:
if len(frutas) > 3:
    print(f"Cuarta fruta: {frutas[3]}")
else:
    print("No hay cuarta fruta")
```

**Explicación:** Los índices válidos van de 0 a `len(lista) - 1`.

---

### Solución 6: Error en Bucle Infinito

```python
contador = 1
while contador <= 5:
    print(f"Iteración {contador}")
    contador += 1  # ✓ Incrementar el contador

print("Terminado!")
```

**Explicación:** La variable de control debe modificarse para que el bucle termine.

---

### Solución 7: Parámetros Faltantes

```python
def calcular_area_rectangulo(base, altura):
    return base * altura

# ✓ Pasar ambos argumentos
area = calcular_area_rectangulo(5, 10)
print(f"Área: {area}")
```

**Explicación:** La función espera dos parámetros: `base` y `altura`.

---

### Solución 8: Comparación vs Asignación

```python
numero = 10

if numero == 10:  # ✓ Operador de comparación
    print("El número es 10")
else:
    print("El número no es 10")
```

**Explicación:** Usá `==` para comparar, `=` es solo para asignar valores.

---

### Solución 9: Concatenación de Tipos Incompatibles

```python
nombre = "Juan"
edad = 25

# Opción 1: Convertir a string
mensaje = "Hola, me llamo " + nombre + " y tengo " + str(edad) + " años"

# Opción 2: Usar f-strings (mejor práctica)
mensaje = f"Hola, me llamo {nombre} y tengo {edad} años"

print(mensaje)
```

**Explicación:** Convertí números a strings con `str()` o usá f-strings.

---

### Solución 10: Error en Diccionario

```python
estudiante = {
    "nombre": "María",
    "edad": 20,
    "carrera": "Ingeniería"
}

print(f"Nombre: {estudiante['nombre']}")

# Opción 1: Verificar si existe
if 'promedio' in estudiante:
    print(f"Promedio: {estudiante['promedio']}")
else:
    print("Promedio: No disponible")

# Opción 2: Usar .get() con valor por defecto
print(f"Promedio: {estudiante.get('promedio', 'No disponible')}")
```

**Explicación:** Verificá que la clave existe antes de accederla.

---

### Solución 11: Modificación de String

```python
texto = "hola mundo"
# Los strings son inmutables, creá uno nuevo
texto = "H" + texto[1:]  # ✓ Crear nuevo string
print(texto)

# O usar métodos de string
texto = "hola mundo"
texto = texto.capitalize()  # "Hola mundo"
print(texto)
```

**Explicación:** Los strings son inmutables. Creá un nuevo string en vez de modificarlo.

---

### Solución 12: Return en el Lugar Incorrecto

```python
def sumar_lista(numeros):
    total = 0
    for num in numeros:
        total += num
    return total  # ✓ Fuera del bucle

resultado = sumar_lista([1, 2, 3, 4, 5])
print(f"Suma: {resultado}")
```

**Explicación:** El `return` debe estar fuera del bucle para que sume todos los números.

---

### Solución 13: Scope de Variables

```python
# Opción 1: Usar global (no recomendado)
def incrementar():
    global contador
    contador = contador + 1
    return contador

# Opción 2: Pasar como parámetro (mejor práctica)
def incrementar(valor):
    return valor + 1

contador = 0
contador = incrementar(contador)
print(contador)
```

**Explicación:** Para modificar una variable global, usá `global` o mejor aún, pasala como parámetro.

---

### Solución 14: Error Lógico en Condición

```python
def es_par(numero):
    if numero % 2 == 0:  # ✓ Cambiar 1 por 0
        return True
    else:
        return False

# O más simple:
def es_par(numero):
    return numero % 2 == 0  # ✓ Retornar directamente

print(f"¿4 es par? {es_par(4)}")
print(f"¿7 es par? {es_par(7)}")
```

**Explicación:** Un número es par cuando `numero % 2 == 0`, no cuando es 1.

---

### Solución 15: Lista Mutada en Bucle

```python
numeros = [1, 2, 3, 4, 5]

# Opción 1: Crear una nueva lista
impares = [num for num in numeros if num % 2 != 0]

# Opción 2: Iterar sobre una copia
for num in numeros[:]:  # [:] crea una copia
    if num % 2 == 0:
        numeros.remove(num)

print(f"Números impares: {impares}")
```

**Explicación:** No modifiques una lista mientras la iterás. Usá una copia o crea una nueva lista.

---

## Consejos para Debugging

:::{tip} Estrategias Efectivas

1. **Lee el error completo:** Python te dice exactamente qué falló y en qué línea
2. **Usa print():** Agrega prints para ver qué valores tienen las variables
3. **Divide y conquista:** Comentá partes del código para aislar el problema
4. **Verificá tipos:** Usá `type()` para confirmar los tipos de datos
5. **Lee el código en voz alta:** A veces ayuda explicarle a alguien (o a un patito de goma)
6. **Tomá un descanso:** A veces la solución aparece cuando dejás de mirar el código
:::

:::{admonition} Errores Comunes en Python
:class: note

**Sintaxis:**
- Olvidar dos puntos `:` después de `if`, `for`, `while`, `def`
- Indentación incorrecta o mezclada (tabs vs espacios)
- Paréntesis o corchetes sin cerrar

**Tipos:**
- Comparar strings con números
- Olvidar convertir `input()` a `int()` o `float()`
- Intentar modificar strings (son inmutables)

**Lógica:**
- Usar `=` en vez de `==`
- Return dentro de un bucle
- Modificar una lista mientras la iterás

**Variables:**
- Mayúsculas vs minúsculas
- Variables no definidas
- Scope (local vs global)
:::

---

## Ejercicios Adicionales (Desafíos)

Si completaste los 15 ejercicios, intentá estos desafíos más complejos:

### Desafío 1: Múltiples Errores

```python
def calcular_promedio(numeros)
    total = 0
    for num in numeros
        total = total + num
    promedio = total / len(numeros)
return promedio

notas = ["7", "8", "9", "10"]
resultado = calcular_promedio(notas)
print(f"Promedio: {resultado}")
```

**Encuentra todos los errores** (hay al menos 5).

---

### Desafío 2: Error Sutil de Lógica

```python
def contar_vocales(texto):
    vocales = "aeiou"
    contador = 0
    for letra in texto:
        if letra in vocales:
            contador += 1
    return contador

frase = "Hola Mundo"
print(f"Vocales: {contar_vocales(frase)}")
```

**¿Cuenta correctamente?** ¿Qué pasa con las mayúsculas?

---

## Recursos Adicionales

- **Documentación oficial:** [docs.python.org](https://docs.python.org/)
- **Python Tutor:** Visualiza la ejecución del código paso a paso
- **Stack Overflow:** Comunidad para resolver dudas
- **ChatGPT/Copilot:** Herramientas de IA para explicar errores

:::{important} Aprendiendo de los errores
Los errores son parte natural del proceso de programación. No te frustres:

- Los programadores experimentados también cometen errores
- Cada error es una oportunidad de aprendizaje
- Con práctica, reconocerás patrones de errores más rápidamente
- El debugging es una habilidad que mejora con el tiempo
:::

---

**¡Éxitos con los ejercicios! 🚀**
