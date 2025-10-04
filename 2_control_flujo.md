---
title: Control de Flujo
short_title: Control de Flujo
subtitle: Condicionales y estructuras de repetición en Python.
---

(control-flujo)=
# Control de Flujo

## Introducción y Motivación

Hasta ahora has escrito programas que ejecutan instrucciones de forma secuencial, una tras otra. Sin embargo, los programas reales necesitan tomar decisiones y repetir acciones. El **control de flujo** te permite hacer exactamente eso: que tu programa tome diferentes caminos según las condiciones que encuentre, y que repita tareas sin escribir el mismo código una y otra vez.

Imagina un cajero automático: debe verificar si el PIN es correcto antes de continuar, debe permitir múltiples intentos, y debe repetir el menú hasta que el usuario elija salir. Todas estas acciones requieren control de flujo.

:::{important} ¿Por qué es importante el control de flujo?
El control de flujo es lo que convierte un programa simple en una herramienta poderosa y flexible. Te permite:
- **Tomar decisiones** basadas en datos
- **Evitar repetición de código** mediante loops
- **Crear programas interactivos** que responden al usuario
- **Manejar diferentes escenarios** en un mismo programa
:::

En este capítulo aprenderás:
- Estructuras condicionales (`if`, `elif`, `else`)
- Loops con `while`
- Loops con `for`
- Control de loops con banderas
- Patrones comunes de programación

---

(condicionales)=
## Estructuras Condicionales

Las **estructuras condicionales** permiten que tu programa ejecute diferentes bloques de código según si una condición es verdadera o falsa.

### La Estructura `if`

La forma más básica de tomar una decisión es con `if`:

```python
edad = 18

if edad >= 18:
    print("Sos mayor de edad")
    print("Podés votar")
```

**Sintaxis:**
```python
if condicion:
    # Bloque de código que se ejecuta si la condición es True
    instruccion1
    instruccion2
```

:::{important} Indentación en Python
Python usa la **indentación** (espacios al inicio de la línea) para definir bloques de código. Según la {ref}`0x0005h`, debés usar **4 espacios** para cada nivel de indentación.

```python
# ✓ Correcto
if edad >= 18:
    print("Mayor de edad")  # 4 espacios de indentación

# ❌ Incorrecto - Error de sintaxis
if edad >= 18:
print("Mayor de edad")  # Sin indentación
```
:::

### La Estructura `if-else`

Cuando querés ejecutar un código si la condición es verdadera, y otro código si es falsa:

```python
edad = 16

if edad >= 18:
    print("Sos mayor de edad")
else:
    print("Sos menor de edad")
```

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    A[Inicio] --> B{edad >= 18?}
    B -->|True| C[print: Mayor de edad]
    B -->|False| D[print: Menor de edad]
    C --> E[Fin]
    D --> E
```

### La Estructura `if-elif-else`

Para manejar múltiples condiciones, usá `elif` (else if):

```python
nota = 85

if nota >= 90:
    print("Excelente")
elif nota >= 70:
    print("Muy Bueno")
elif nota >= 60:
    print("Bueno")
else:
    print("Necesitás mejorar")
```

**Flujo de evaluación:**
1. Se evalúa la primera condición (`nota >= 90`)
2. Si es `False`, se evalúa la siguiente (`nota >= 70`)
3. Si alguna es `True`, se ejecuta su bloque y se sale
4. Si todas son `False`, se ejecuta el bloque `else` (si existe)

:::{warning} Las condiciones se evalúan en orden
Python evalúa las condiciones de arriba hacia abajo y ejecuta **solo el primer bloque** cuya condición sea verdadera:

```python
numero = 85

# ✓ Correcto - orden de más restrictivo a menos restrictivo
if numero >= 90:
    print("A")
elif numero >= 80:
    print("B")  # Esta se ejecuta
elif numero >= 70:
    print("C")

# ❌ Problemático - la primera condición captura todo
if numero >= 70:
    print("C o mejor")  # Siempre se ejecuta si numero >= 70
elif numero >= 80:
    print("B o mejor")  # Nunca se alcanza
elif numero >= 90:
    print("A")  # Nunca se alcanza
```
:::

### Condiciones Anidadas

Podés colocar estructuras `if` dentro de otras estructuras `if`:

```python
edad = 20
tiene_licencia = True

if edad >= 18:
    if tiene_licencia:
        print("Podés conducir")
    else:
        print("Necesitás obtener la licencia")
else:
    print("Sos muy joven para conducir")
```

**Simplificación con operadores lógicos:**

Según la {ref}`0x000Dh`, las condiciones complejas deben simplificarse. Muchas veces podés evitar anidación usando `and`:

```python
# Más simple y claro
if edad >= 18 and tiene_licencia:
    print("Podés conducir")
else:
    print("No podés conducir")
```

### Expresiones Booleanas en Condiciones

Recordá que las condiciones deben evaluar a `True` o `False`:

```python
# Comparaciones
if temperatura > 30:
    print("Hace calor")

# Variables booleanas
if esta_lloviendo:
    print("Llevá paraguas")

# Operadores lógicos
if edad >= 18 and tiene_dni:
    print("Podés votar")

# Negación
if not esta_ocupado:
    print("Disponible")
```

### Valores "Truthy" y "Falsy"

En Python, ciertos valores se consideran "falsos" en un contexto booleano:
- `False`, `None`, `0`, `0.0`
- Secuencias vacías: `""`, `[]`, `{}`, `()`

Todos los demás valores se consideran "verdaderos". Sin embargo, según las buenas prácticas, es preferible ser **explícito**:

```python
lista = []

# ❌ Menos claro (aunque funciona)
if lista:
    print("Tiene elementos")

# ✓ Más claro y explícito
if len(lista) > 0:
    print("Tiene elementos")

# O mejor aún
if lista:  # Aceptable para listas
    print("Tiene elementos")
# Pero documentalo si no es obvio
```

---

(ejemplos-condicionales)=
## Ejemplos Prácticos con Condicionales

### Ejemplo 1: Calculadora de Descuento

```python
"""Programa que calcula descuento según el monto de compra."""

DESCUENTO_BASICO = 0.05      # 5%
DESCUENTO_INTERMEDIO = 0.10  # 10%
DESCUENTO_PREMIUM = 0.15     # 15%

monto = float(input("Ingrese el monto de compra: $"))

if monto >= 10000:
    descuento = monto * DESCUENTO_PREMIUM
    print(f"Descuento Premium: {DESCUENTO_PREMIUM * 100}%")
elif monto >= 5000:
    descuento = monto * DESCUENTO_INTERMEDIO
    print(f"Descuento Intermedio: {DESCUENTO_INTERMEDIO * 100}%")
elif monto >= 1000:
    descuento = monto * DESCUENTO_BASICO
    print(f"Descuento Básico: {DESCUENTO_BASICO * 100}%")
else:
    descuento = 0
    print("No hay descuento para este monto")

total = monto - descuento
print(f"Monto original: ${monto:.2f}")
print(f"Descuento: ${descuento:.2f}")
print(f"Total a pagar: ${total:.2f}")
```

### Ejemplo 2: Clasificación de Temperatura

```python
"""Clasifica la temperatura y da recomendaciones."""

temperatura = float(input("Ingrese la temperatura en °C: "))

if temperatura >= 35:
    print("Extremadamente caluroso - Evitá la exposición al sol")
elif temperatura >= 25:
    print("Caluroso - Mantenete hidratado")
elif temperatura >= 15:
    print("Agradable - Clima ideal")
elif temperatura >= 5:
    print("Fresco - Llevá una campera")
else:
    print("Frío - Abrigate bien")
```

### Ejemplo 3: Validación de Edad

```python
"""Valida si una persona puede acceder a cierto contenido."""

edad = int(input("Ingrese su edad: "))

if edad < 0 or edad > 120:
    print("Error: Edad inválida")
elif edad < 13:
    print("Contenido no disponible para menores de 13 años")
elif edad < 18:
    print("Acceso permitido con supervisión de un adulto")
else:
    print("Acceso completo permitido")
```

---

(while-loops)=
## Loops con `while`

Un **loop** (bucle o lazo) permite ejecutar un bloque de código repetidamente. El loop `while` continúa ejecutándose mientras una condición sea verdadera.

### Sintaxis Básica

```python
while condicion:
    # Bloque de código que se repite
    # mientras la condición sea True
```

### Ejemplo Simple

```python
contador = 1

while contador <= 5:
    print(f"Contador: {contador}")
    contador += 1

print("Fin del loop")
```

**Salida:**
```
Contador: 1
Contador: 2
Contador: 3
Contador: 4
Contador: 5
Fin del loop
```

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    A[contador = 1] --> B{contador <= 5?}
    B -->|True| C[print contador]
    C --> D[contador += 1]
    D --> B
    B -->|False| E[Fin del loop]
```

:::{danger} Loops infinitos
Si la condición nunca se vuelve `False`, el loop se ejecutará infinitamente:

```python
# ❌ Loop infinito - nunca termina
contador = 1
while contador <= 5:
    print(contador)
    # Olvidamos incrementar contador!

# Para detenerlo: Ctrl+C en la terminal
```

**Siempre asegurate de que:**
1. La condición eventualmente se vuelva `False`
2. Las variables usadas en la condición se modifiquen dentro del loop
:::

### Inicialización de Variables en Loops

Según la {ref}`0x0003h`, debés inicializar las variables antes de usarlas:

```python
# ✓ Correcto - inicialización antes del loop
suma = 0
contador = 1

while contador <= 10:
    suma += contador
    contador += 1

print(f"La suma es: {suma}")
```

### Ejemplo: Suma de Números

```python
"""Suma números ingresados por el usuario hasta que ingrese 0."""

suma = 0
numero = int(input("Ingrese un número (0 para terminar): "))

while numero != 0:
    suma += numero
    numero = int(input("Ingrese un número (0 para terminar): "))

print(f"La suma total es: {suma}")
```

### Ejemplo: Contador Regresivo

```python
"""Cuenta regresivamente desde un número dado."""

numero = int(input("Desde qué número quiere contar: "))

while numero > 0:
    print(numero)
    numero -= 1

print("¡Despegue! 🚀")
```

### Loops con Condiciones Complejas

Podés usar operadores lógicos en la condición:

```python
"""Juego de adivinanza con límite de intentos."""

NUMERO_SECRETO = 42
MAX_INTENTOS = 5

intentos = 0
adivinado = False

while intentos < MAX_INTENTOS and not adivinado:
    intento = int(input("Adiviná el número (1-100): "))
    intentos += 1
    
    if intento == NUMERO_SECRETO:
        adivinado = True
        print(f"¡Correcto! Lo adivinaste en {intentos} intentos")
    elif intento < NUMERO_SECRETO:
        print("Muy bajo. Intentá de nuevo.")
    else:
        print("Muy alto. Intentá de nuevo.")

if not adivinado:
    print(f"Se acabaron los intentos. El número era {NUMERO_SECRETO}")
```

---

(banderas-control)=
## Banderas de Control

Según la {ref}`0x0006h`, en lugar de usar `break` y `continue` para loops complejos, es preferible usar **banderas** (variables booleanas) para controlar el flujo.

### Patrón de Bandera Simple

```python
"""Búsqueda con bandera de control."""

numeros = [10, 25, 30, 45, 50]
objetivo = 30
encontrado = False
i = 0

while i < len(numeros) and not encontrado:
    if numeros[i] == objetivo:
        encontrado = True
        print(f"Encontrado en posición {i}")
    i += 1

if not encontrado:
    print("No se encontró el número")
```

### Múltiples Banderas

```python
"""Validación de entrada con múltiples condiciones."""

entrada_valida = False
intentos = 0
MAX_INTENTOS = 3

while not entrada_valida and intentos < MAX_INTENTOS:
    edad = int(input("Ingrese su edad (18-100): "))
    intentos += 1
    
    if edad >= 18 and edad <= 100:
        entrada_valida = True
        print("Edad válida registrada")
    else:
        print(f"Edad inválida. Intentos restantes: {MAX_INTENTOS - intentos}")

if not entrada_valida:
    print("Demasiados intentos inválidos")
```

### Ventajas de las Banderas

1. **Claridad:** El código es más fácil de entender
2. **Mantenibilidad:** Es fácil agregar condiciones adicionales
3. **Debugging:** Podés inspeccionar el estado de las banderas
4. **Testeo:** Las banderas facilitan las pruebas unitarias

:::{tip} Cuándo usar break
Si bien preferimos banderas, `break` es aceptable en Python para casos simples de búsqueda:

```python
# Aceptable para búsquedas simples
for elemento in lista:
    if elemento == objetivo:
        print("Encontrado")
        break
```

Para lógica más compleja, usá banderas.
:::

---

(for-loops)=
## Loops con `for`

El loop `for` se usa para iterar sobre secuencias (listas, strings, rangos, etc.). Según la {ref}`0x0007h`, usá `for` cuando conozcas la secuencia sobre la que iterás.

### Iterando sobre un Rango

```python
# Iterar del 0 al 4
for i in range(5):
    print(i)

# Salida: 0, 1, 2, 3, 4
```

**La función `range()`:**

```python
# range(stop) - desde 0 hasta stop-1
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# range(start, stop) - desde start hasta stop-1
for i in range(2, 6):
    print(i)  # 2, 3, 4, 5

# range(start, stop, step) - con incremento personalizado
for i in range(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8

# Contando hacia atrás
for i in range(5, 0, -1):
    print(i)  # 5, 4, 3, 2, 1
```

### Iterando sobre Strings

```python
mensaje = "Python"

for letra in mensaje:
    print(letra)

# Salida:
# P
# y
# t
# h
# o
# n
```

### Iterando sobre Listas

```python
frutas = ["manzana", "banana", "naranja"]

for fruta in frutas:
    print(f"Me gusta la {fruta}")
```

:::{important} Estilo Pythonic
Según la {ref}`0x0007h`, en Python es preferible iterar directamente sobre elementos en lugar de usar índices:

```python
nombres = ["Ana", "Bruno", "Carlos"]

# ❌ Menos Pythonic
for i in range(len(nombres)):
    print(nombres[i])

# ✓ Pythonic
for nombre in nombres:
    print(nombre)
```
:::

### Usando `enumerate()` cuando necesitás índices

Si necesitás tanto el índice como el elemento, usá `enumerate()`:

```python
colores = ["rojo", "verde", "azul"]

for indice, color in enumerate(colores):
    print(f"Color {indice}: {color}")

# Salida:
# Color 0: rojo
# Color 1: verde
# Color 2: azul
```

**Empezar desde un índice diferente:**

```python
colores = ["rojo", "verde", "azul"]

for indice, color in enumerate(colores, start=1):
    print(f"Color {indice}: {color}")

# Salida:
# Color 1: rojo
# Color 2: verde
# Color 3: azul
```

### Ejemplo: Tabla de Multiplicar

```python
"""Genera la tabla de multiplicar de un número."""

numero = int(input("Ingrese un número: "))

print(f"\nTabla de multiplicar del {numero}:")
print("-" * 30)

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i:2d} = {resultado:3d}")
```

### Ejemplo: Suma de Lista

```python
"""Calcula la suma de una lista de números."""

numeros = [10, 20, 30, 40, 50]
suma = 0

for numero in numeros:
    suma += numero

print(f"La suma es: {suma}")

# Nota: En Python real usarías: suma = sum(numeros)
```

---

(while-vs-for)=
## `while` vs `for`: ¿Cuándo usar cada uno?

### Usar `while` cuando:

1. **No conocés de antemano cuántas iteraciones necesitás**
   ```python
   # Esperar entrada válida
   edad = -1
   while edad < 0 or edad > 120:
       edad = int(input("Edad (0-120): "))
   ```

2. **La condición de parada es compleja**
   ```python
   intentos = 0
   exito = False
   MAX_INTENTOS = 5
   
   while intentos < MAX_INTENTOS and not exito:
       # ... lógica ...
   ```

3. **El loop puede no ejecutarse ninguna vez**
   ```python
   while hay_mas_datos():
       procesar_datos()
   ```

### Usar `for` cuando:

1. **Iterás sobre una secuencia conocida**
   ```python
   for nombre in lista_nombres:
       print(nombre)
   ```

2. **Conocés exactamente cuántas iteraciones necesitás**
   ```python
   for i in range(10):
       print(i)
   ```

3. **Necesitás procesar cada elemento de una colección**
   ```python
   for estudiante in estudiantes:
       calcular_promedio(estudiante)
   ```

### Tabla Comparativa

| Aspecto | `while` | `for` |
|---------|---------|-------|
| **Iteraciones** | Número desconocido | Número conocido o secuencia |
| **Condición** | Puede ser compleja | Implícita (hasta terminar secuencia) |
| **Uso típico** | Validaciones, menús | Procesar colecciones, rangos |
| **Riesgo** | Loop infinito si no hay cuidado | Menor riesgo |

---

(loops-anidados)=
## Loops Anidados

Podés colocar loops dentro de otros loops. Cada iteración del loop externo ejecuta completamente el loop interno.

### Ejemplo: Tabla de Multiplicar Completa

```python
"""Genera tablas de multiplicar del 1 al 5."""

for numero in range(1, 6):
    print(f"\nTabla del {numero}:")
    for multiplicador in range(1, 11):
        resultado = numero * multiplicador
        print(f"{numero} x {multiplicador:2d} = {resultado:3d}")
```

### Ejemplo: Patrón de Asteriscos

```python
"""Imprime un triángulo de asteriscos."""

altura = 5

for fila in range(1, altura + 1):
    for columna in range(fila):
        print("*", end="")
    print()  # Nueva línea

# Salida:
# *
# **
# ***
# ****
# *****
```

### Ejemplo: Verificación de Matriz

```python
"""Busca un valor en una matriz (lista de listas)."""

matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

objetivo = 5
encontrado = False
fila_encontrada = -1
columna_encontrada = -1

for i in range(len(matriz)):
    for j in range(len(matriz[i])):
        if matriz[i][j] == objetivo:
            encontrado = True
            fila_encontrada = i
            columna_encontrada = j

if encontrado:
    print(f"Encontrado en fila {fila_encontrada}, columna {columna_encontrada}")
else:
    print("No encontrado")
```

:::{warning} Cuidado con la complejidad
Loops anidados pueden hacer que tu código sea lento. Un loop dentro de otro multiplica las iteraciones:
- Loop externo: 100 iteraciones
- Loop interno: 100 iteraciones
- Total: 100 × 100 = 10,000 iteraciones

Usá loops anidados solo cuando sea necesario.
:::

---

(patrones-comunes)=
## Patrones Comunes de Programación

### Patrón 1: Acumulador

Sumar o acumular valores:

```python
# Suma de números del 1 al 100
suma = 0
for i in range(1, 101):
    suma += i
print(f"Suma: {suma}")
```

### Patrón 2: Contador

Contar cuántas veces ocurre algo:

```python
# Contar números pares en una lista
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
contador_pares = 0

for numero in numeros:
    if numero % 2 == 0:
        contador_pares += 1

print(f"Hay {contador_pares} números pares")
```

### Patrón 3: Búsqueda

Encontrar un elemento:

```python
# Buscar un nombre en una lista
nombres = ["Ana", "Bruno", "Carlos", "Diana"]
buscar = "Carlos"
encontrado = False

for nombre in nombres:
    if nombre == buscar:
        encontrado = True

if encontrado:
    print(f"{buscar} está en la lista")
else:
    print(f"{buscar} no está en la lista")
```

### Patrón 4: Máximo/Mínimo

Encontrar el valor máximo o mínimo:

```python
# Encontrar el número mayor
numeros = [45, 23, 67, 12, 89, 34]
maximo = numeros[0]

for numero in numeros:
    if numero > maximo:
        maximo = numero

print(f"El máximo es: {maximo}")
```

### Patrón 5: Validación de Entrada

Repetir hasta obtener entrada válida:

```python
# Validar entrada numérica positiva
numero_valido = False

while not numero_valido:
    try:
        numero = float(input("Ingrese un número positivo: "))
        if numero > 0:
            numero_valido = True
            print(f"Número válido: {numero}")
        else:
            print("El número debe ser positivo")
    except ValueError:
        print("Debe ingresar un número")
```

### Patrón 6: Menú de Opciones

```python
"""Menú interactivo."""

continuar = True

while continuar:
    print("\n=== MENÚ ===")
    print("1. Opción A")
    print("2. Opción B")
    print("3. Opción C")
    print("4. Salir")
    
    opcion = input("Seleccione una opción (1-4): ")
    
    if opcion == "1":
        print("Ejecutando opción A...")
    elif opcion == "2":
        print("Ejecutando opción B...")
    elif opcion == "3":
        print("Ejecutando opción C...")
    elif opcion == "4":
        continuar = False
        print("¡Hasta luego!")
    else:
        print("Opción inválida")
```

---

(errores-comunes-control)=
## Errores Comunes

### 1. Olvidar la indentación

```python
# ❌ Error de sintaxis
if edad >= 18:
print("Mayor de edad")  # IndentationError

# ✓ Correcto
if edad >= 18:
    print("Mayor de edad")
```

### 2. Usar `=` en lugar de `==`

```python
# ❌ Asignación en lugar de comparación
if edad = 18:  # SyntaxError
    print("Tiene 18")

# ✓ Correcto
if edad == 18:
    print("Tiene 18")
```

### 3. Loop infinito

```python
# ❌ Loop infinito
contador = 0
while contador < 10:
    print(contador)
    # Olvidamos incrementar contador

# ✓ Correcto
contador = 0
while contador < 10:
    print(contador)
    contador += 1
```

### 4. Condiciones incorrectas en rangos

```python
# ❌ Lógica incorrecta
nota = 85
if nota >= 60 and nota < 90:  # No captura 60-69
    print("Bueno")
elif nota >= 70 and nota < 90:  # Nunca se alcanza
    print("Muy Bueno")

# ✓ Correcto - orden de más específico a general
if nota >= 90:
    print("Excelente")
elif nota >= 70:
    print("Muy Bueno")
elif nota >= 60:
    print("Bueno")
```

### 5. Modificar lista mientras se itera

```python
# ❌ Problemático
numeros = [1, 2, 3, 4, 5]
for numero in numeros:
    if numero % 2 == 0:
        numeros.remove(numero)  # Puede causar problemas

# ✓ Mejor - crear nueva lista
numeros = [1, 2, 3, 4, 5]
impares = []
for numero in numeros:
    if numero % 2 != 0:
        impares.append(numero)
```

---

(buenas-practicas-control)=
## Buenas Prácticas

### 1. Nombres Descriptivos para Banderas

```python
# ❌ Poco claro
flag = True
x = False

# ✓ Descriptivo
usuario_autenticado = True
datos_validos = False
```

### 2. Condiciones Legibles

```python
# ❌ Difícil de leer
if a > 18 and b == True and c != 0 and (d == "admin" or d == "superuser"):
    hacer_algo()

# ✓ Más claro
es_mayor_edad = a > 18
esta_activo = b == True
tiene_saldo = c != 0
es_administrador = d == "admin" or d == "superuser"

if es_mayor_edad and esta_activo and tiene_saldo and es_administrador:
    hacer_algo()
```

### 3. Evitar Anidación Excesiva

```python
# ❌ Muy anidado
if condicion1:
    if condicion2:
        if condicion3:
            if condicion4:
                hacer_algo()

# ✓ Retorno temprano o condiciones combinadas
if not condicion1:
    return

if not condicion2:
    return

if not condicion3:
    return

if condicion4:
    hacer_algo()
```

### 4. Constantes para Valores Mágicos

```python
# ❌ "Números mágicos"
if edad >= 18 and edad <= 65:
    calcular_descuento()

# ✓ Constantes descriptivas
EDAD_MINIMA = 18
EDAD_MAXIMA = 65

if edad >= EDAD_MINIMA and edad <= EDAD_MAXIMA:
    calcular_descuento()
```

### 5. Comentarios en Condiciones Complejas

```python
# Verificar si el usuario puede acceder al sistema
# Debe ser mayor de edad, tener cuenta activa y no estar suspendido
if edad >= 18 and cuenta_activa and not suspendido:
    permitir_acceso()
```

---

(ejercicios-control-flujo)=
## Ejercicios

(ejercicio-2-1)=
### Ejercicio 2.1: Calculadora de IMC con Clasificación

Ampliá el ejercicio del IMC del capítulo anterior. Calculá el IMC y clasificalo según la tabla de la OMS:

| IMC | Clasificación |
|-----|---------------|
| < 18.5 | Bajo peso |
| 18.5 - 24.9 | Peso normal |
| 25.0 - 29.9 | Sobrepeso |
| ≥ 30.0 | Obesidad |

**Entrada:**
- Peso en kg (float)
- Altura en metros (float)

**Salida:**
- IMC calculado
- Clasificación según la tabla

**Ejemplo:**
```
Ingrese su peso en kg: 70
Ingrese su altura en metros: 1.75

Su IMC es: 22.86
Clasificación: Peso normal
```

---

(ejercicio-2-2)=
### Ejercicio 2.2: Año Bisiesto

Un año es bisiesto si:
- Es divisible por 4, PERO
- Si es divisible por 100, también debe ser divisible por 400

Escribí un programa que determine si un año es bisiesto.

**Entrada:**
- Año (int)

**Salida:**
- Si es bisiesto o no

**Ejemplo:**
```
Ingrese un año: 2024
2024 es un año bisiesto

Ingrese un año: 1900
1900 NO es un año bisiesto

Ingrese un año: 2000
2000 es un año bisiesto
```

:::{tip}
Usá el operador módulo `%` para verificar divisibilidad.
Un número es divisible por otro si el resto es 0.
:::

---

(ejercicio-2-3)=
### Ejercicio 2.3: Calculadora de Notas

Escribí un programa que calcule el promedio de un estudiante y determine si aprobó.

**Reglas:**
- Se ingresan 3 notas (0-10)
- El promedio debe ser ≥ 6 para aprobar
- Si alguna nota es < 4, desaprueba automáticamente (aplazo)

**Entrada:**
- Tres notas (float)

**Salida:**
- Promedio
- Estado (Aprobado/Desaprobado/Aplazado)

**Ejemplo:**
```
Ingrese nota 1: 7
Ingrese nota 2: 8
Ingrese nota 3: 6

Promedio: 7.00
Estado: Aprobado
```

---

(ejercicio-2-4)=
### Ejercicio 2.4: Contador de Dígitos

Escribí un programa que cuente cuántos dígitos tiene un número entero positivo.

**Entrada:**
- Número entero positivo

**Salida:**
- Cantidad de dígitos

**Ejemplo:**
```
Ingrese un número: 12345
El número tiene 5 dígitos
```

:::{tip}
Podés dividir el número por 10 repetidamente hasta que llegue a 0, contando las veces que dividiste.
:::

---

(ejercicio-2-5)=
### Ejercicio 2.5: Suma de Pares

Escribí un programa que sume todos los números pares entre 1 y un número N ingresado por el usuario.

**Entrada:**
- Número N (int)

**Salida:**
- Suma de todos los pares entre 1 y N

**Ejemplo:**
```
Ingrese un número: 10
La suma de los pares entre 1 y 10 es: 30
(2 + 4 + 6 + 8 + 10 = 30)
```

---

(ejercicio-2-6)=
### Ejercicio 2.6: Factorial

El factorial de un número n (escrito n!) es el producto de todos los enteros positivos desde 1 hasta n:

$$
n! = 1 \times 2 \times 3 \times ... \times n
$$

Por ejemplo: $5! = 1 \times 2 \times 3 \times 4 \times 5 = 120$

Escribí un programa que calcule el factorial de un número.

**Entrada:**
- Número entero positivo

**Salida:**
- Factorial del número

**Ejemplo:**
```
Ingrese un número: 5
5! = 120
```

---

(ejercicio-2-7)=
### Ejercicio 2.7: Números Primos

Un número primo es aquel que solo es divisible por 1 y por sí mismo. Escribí un programa que determine si un número es primo.

**Entrada:**
- Número entero mayor que 1

**Salida:**
- Si el número es primo o no

**Ejemplo:**
```
Ingrese un número: 17
17 es un número primo

Ingrese un número: 12
12 NO es un número primo
```

:::{tip}
Para verificar si n es primo, probá dividirlo por todos los números desde 2 hasta n-1. Si alguno lo divide exactamente (resto 0), no es primo.
:::

---

(ejercicio-2-8)=
### Ejercicio 2.8: Secuencia de Fibonacci

La secuencia de Fibonacci comienza con 0 y 1, y cada número siguiente es la suma de los dos anteriores:

$$
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
$$

Escribí un programa que muestre los primeros N números de la secuencia de Fibonacci.

**Entrada:**
- Cantidad de números a mostrar (int)

**Salida:**
- Los primeros N números de Fibonacci

**Ejemplo:**
```
¿Cuántos números de Fibonacci desea ver? 8
0, 1, 1, 2, 3, 5, 8, 13
```

---

(ejercicio-2-9)=
### Ejercicio 2.9: Pirámide de Números

Escribí un programa que imprima una pirámide de números de altura N.

**Entrada:**
- Altura de la pirámide (int)

**Salida:**
- Pirámide de números

**Ejemplo:**
```
Ingrese la altura: 5

    1
   121
  12321
 1234321
123454321
```

:::{tip}
Para cada fila i:
1. Imprimí (N - i) espacios
2. Imprimí números ascendentes de 1 a i
3. Imprimí números descendentes de i-1 a 1
:::

---

(ejercicio-2-10)=
### Ejercicio 2.10: Juego de Adivinanza

Implementá un juego donde la computadora "piensa" un número aleatorio entre 1 y 100, y el usuario debe adivinarlo. El programa debe dar pistas ("muy alto" o "muy bajo") y contar los intentos.

**Entrada:**
- Intentos del usuario (int)

**Salida:**
- Pistas hasta que adivine
- Cantidad de intentos necesarios

**Ejemplo:**
```
¡Adivina el número entre 1 y 100!

Intento 1: 50
Muy alto

Intento 2: 25
Muy bajo

Intento 3: 37
Muy bajo

Intento 4: 43
¡Correcto! Adivinaste en 4 intentos.
```

:::{tip}
Para generar un número aleatorio:
```python
import random
numero_secreto = random.randint(1, 100)
```
:::

---

(ejercicio-2-11)=
### Ejercicio 2.11: Validación de Contraseña

Escribí un programa que valide una contraseña según estos criterios:
- Longitud mínima: 8 caracteres
- Debe contener al menos una letra mayúscula
- Debe contener al menos una letra minúscula
- Debe contener al menos un dígito

**Entrada:**
- Contraseña (string)

**Salida:**
- Si la contraseña es válida o no
- Lista de criterios que no cumple

**Ejemplo:**
```
Ingrese una contraseña: hola123

Contraseña inválida. Problemas:
- Debe tener al menos 8 caracteres
- Debe contener al menos una mayúscula
```

:::{tip}
Usá los métodos de strings:
- `str.isupper()` - verifica si es mayúscula
- `str.islower()` - verifica si es minúscula
- `str.isdigit()` - verifica si es dígito
- `len(str)` - longitud del string
:::

---

(ejercicio-2-12)=
### Ejercicio 2.12: Cajero Automático (Menú)

Simulá un cajero automático con las siguientes opciones:
1. Consultar saldo
2. Depositar dinero
3. Retirar dinero
4. Salir

**Reglas:**
- Saldo inicial: $10,000
- No se puede retirar más del saldo disponible
- Los depósitos y retiros deben ser montos positivos

**Entrada:**
- Opción del menú
- Montos según la operación

**Salida:**
- Menú interactivo
- Confirmación de operaciones
- Saldo actualizado

**Ejemplo:**
```
=== CAJERO AUTOMÁTICO ===
1. Consultar Saldo
2. Depositar
3. Retirar
4. Salir

Opción: 1
Saldo actual: $10000.00

Opción: 2
Monto a depositar: $500
Depósito exitoso. Nuevo saldo: $10500.00

Opción: 3
Monto a retirar: $2000
Retiro exitoso. Nuevo saldo: $8500.00

Opción: 4
¡Gracias por usar nuestro cajero!
```


---

(uso-ia-control-flujo)=
## Uso Ético y Efectivo de la IA en Control de Flujo

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Aprender control de flujo es aprender a **pensar algorítmicamente**. La IA puede ayudarte a refinar tu lógica, pero no puede desarrollar esta habilidad por vos. **Vos debés ser quien diseñe la solución.**
:::

### Buenas Prácticas para Control de Flujo

#### Generar Ejercicios Adicionales

- *"Genera cinco ejercicios sobre condicionales `if-elif-else` que involucren validación de rangos de números"*
- *"Crea ejercicios de loops `while` que requieran el uso de banderas de control"*
- *"Dame problemas de práctica sobre loops `for` con `range()` de diferente complejidad"*

#### Obtener Pistas sobre Lógica

Si tu condición no funciona correctamente:

- *"Tengo un programa que debe verificar si un número está entre 10 y 20. Mi condición es `if numero > 10 and numero < 20:` pero falla con 10 y 20. ¿Por qué?"*
- *"Estoy escribiendo un loop para pedir números hasta que el usuario ingrese 0, pero no sé cómo estructurarlo. ¿Cuál sería el esqueleto básico?"*
- *"¿Cómo puedo salir de un loop `while` cuando se cumpla cierta condición sin usar `break`?"*

#### Refactorizar Condiciones Complejas

- *"Esta condición es muy larga y difícil de leer: `if (edad >= 18 and tiene_dni and (es_estudiante or es_empleado)) or es_admin:`. ¿Cómo puedo mejorarla?"*
- *"Tengo cuatro `if` anidados. ¿Hay una forma más clara de escribir esto?"*

#### Debugging de Lógica

- *"Mi loop infinito no se detiene. Aquí está mi código: [código]. ¿Qué estoy haciendo mal?"*
- *"Mi condición siempre evalúa `True` incluso cuando debería ser `False`. ¿Cuál podría ser el problema?"*

#### Explorar Alternativas

- *"Resolví este problema con un `while`. ¿Podrías mostrarme cómo se vería con un `for`?"*
- *"¿Cuál es la diferencia práctica entre usar un `for` con `range()` y un `while` con contador manual?"*

### Ejemplos Específicos de este Módulo

**Situación 1**: Validación de entrada

❌ **Incorrecto**:
```
Prompt: "Dame el código para validar que un número esté entre 1 y 100"
```

✅ **Correcto**:
```
Prompt: "Estoy validando un número entre 1 y 100. Escribí esto:
if numero > 1 and numero < 100:
¿Está correcto o debería usar >= y <=?"
```

**Situación 2**: Loop con acumulador

❌ **Incorrecto**:
```
Prompt: "Escribe un programa que sume números hasta que el usuario ingrese 0"
```

✅ **Correcto**:
```
Prompt: "Estoy sumando números en un loop while. Inicialicé suma = 0 
y tengo el loop, pero no sé dónde hacer la suma. ¿Dentro o fuera del loop?"
```

### Errores Comunes en este Módulo

:::{warning} No pidas que la IA diseñe tu algoritmo
El diseño del algoritmo (decidir qué condiciones usar, cómo estructurar el loop, cuándo terminar) es **la habilidad que estás aprendiendo**. Si la IA lo hace por vos, no estás aprendiendo nada.

**Desarrollá tu algoritmo primero**, luego pedí ayuda para refinarlo.
:::

### Ejercicio de Reflexión

Antes de pedir ayuda a la IA sobre un ejercicio de control de flujo, preguntate:

1. ¿Cuál es la condición que quiero verificar?
2. ¿Qué debe pasar si es verdadera? ¿Y si es falsa?
3. ¿Necesito repetir algo? ¿Cuántas veces? ¿Hasta cuándo?
4. ¿Qué variables necesito para controlar el flujo?

Si podés responder estas preguntas, **ya sabés cómo resolver el ejercicio**. La IA solo debería ayudarte con detalles de sintaxis o refinamiento.

---


---

## Resumen

En este capítulo aprendiste sobre control de flujo en Python:

✓ **Condicionales**: `if`, `elif`, `else` para tomar decisiones  
✓ **Loops `while`**: Repetir mientras una condición sea verdadera  
✓ **Loops `for`**: Iterar sobre secuencias y rangos  
✓ **Banderas de control**: Alternativa clara a `break` y `continue`  
✓ **Loops anidados**: Loops dentro de otros loops  
✓ **Patrones comunes**: Acumuladores, contadores, búsqueda, validación  
✓ **Buenas prácticas**: Código claro, mantenible y eficiente  

Estos conceptos te permiten crear programas dinámicos e interactivos que responden a diferentes situaciones. El control de flujo es fundamental para resolver problemas complejos dividiéndolos en partes más pequeñas y manejables.

:::{important} Práctica y experimentación
Los loops y condicionales requieren práctica para dominarlos. Resolvé los ejercicios, experimentá con diferentes condiciones, y no tengas miedo de cometer errores. Cada error es una oportunidad de aprendizaje.
:::

En el próximo capítulo, aprenderás sobre estructuras de datos que te permitirán organizar y manipular colecciones de información de forma eficiente.
