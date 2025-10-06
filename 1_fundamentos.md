---
title: Fundamentos de Programación en Python
short_title: 1 - Fundamentos
subtitle: Introducción a la programación, variables, tipos de datos y operadores.
---

(fundamentos)=
# Fundamentos de Programación en Python

## Introducción y Motivación

La programación es el arte de dar instrucciones precisas a una computadora para resolver problemas. A través de este capítulo, aprenderás los conceptos fundamentales que son la base de todo programa: cómo almacenar información, cómo realizar cálculos y cómo comunicarte con el usuario.

Python es un lenguaje de programación moderno, potente y fácil de aprender. Es utilizado en desarrollo web, análisis de datos, inteligencia artificial, automatización y muchos otros campos. Su sintaxis clara y legible lo convierte en una excelente elección para aprender a programar.

:::{important} ¿Por qué estos conceptos son importantes?
Los fundamentos que aprenderás en este capítulo son universales en programación. Una vez que comprendas variables, tipos de datos y operadores, podrás aplicar estos conceptos en cualquier lenguaje de programación.
:::

---

(primer-programa)=
## Tu Primer Programa

Todo viaje de programación comienza con el clásico "Hola Mundo". Este programa simple te introduce a la sintaxis básica de Python.

```{code-cell} ipython3
print("¡Hola Mundo!")
```

**Salida:**
```
¡Hola Mundo!
```

La función `print()` muestra texto en la pantalla. El texto entre comillas (`"..."` o `'...'`) se llama **cadena de texto** o **string**.

:::{tip} Ejecutando código Python
Para ejecutar código Python:
1. Guardá el código en un archivo con extensión `.py` (ejemplo: `hola.py`)
2. Ejecutalo desde la terminal: `python hola.py`
3. O usá el modo interactivo ejecutando simplemente `python` y escribiendo el código línea por línea
4. **¡O probalo directamente aquí abajo!** Hacé clic en "run" para ejecutar el código
:::

**¡Probalo vos mismo!** Modificá el mensaje y hacé clic en "run":

```{code-cell} ipython3
print("¡Hola Mundo!")
print("Esta es mi primera línea de código en Python")
```

---

(variables)=
## Variables: Almacenando Información

Una **variable** es un nombre que le damos a un espacio en la memoria de la computadora donde almacenamos un valor. Pensá en las variables como cajas etiquetadas donde guardás información.

### Crear una Variable

En Python, crear una variable es muy simple: elegís un nombre y le asignás un valor usando el símbolo `=`:

```{code-cell} ipython3
edad = 18
nombre = "Ana"
altura = 1.65
es_estudiante = True
```

**¡Probalo interactivamente!** Creá tus propias variables y mostrá sus valores:

```{code-cell} ipython3
# Creamos variables
edad = 18
nombre = "Ana"
altura = 1.65
es_estudiante = True

# Mostramos los valores
print(f"Nombre: {nombre}")
print(f"Edad: {edad}")
print(f"Altura: {altura}m")
print(f"¿Es estudiante?: {es_estudiante}")
```

:::{note} Nomenclatura de Variables 

Según la {ref}`0x0001h`, los nombres de variables deben ser descriptivos. En Python, se usa `snake_case`: palabras en minúscula separadas por guiones bajos.

**Nombres apropiados:**
- `edad_usuario`
- `precio_total`
- `cantidad_productos`

**Nombres inapropiados:**
- `x`, `a`, `dato` (poco descriptivos)
- `PrecioTotal` (no es snake_case)

:::

### Reglas para Nombres de Variables

1. Deben comenzar con una letra o guión bajo (`_`)
2. Pueden contener letras, números y guiones bajos
3. No pueden contener espacios ni caracteres especiales
4. Son sensibles a mayúsculas y minúsculas (`edad` ≠ `Edad`)
5. No pueden ser palabras reservadas de Python (`if`, `for`, `while`, etc.)

```python
# Válido
nombre = "Carlos"
edad_2023 = 20
_valor_privado = 100

# Inválido
# 2nombre = "Error"      # No puede empezar con número
# mi-variable = 5        # No puede contener guiones
# for = 10               # No puede ser palabra reservada
```

### Reasignación de Variables

Podés cambiar el valor de una variable en cualquier momento:

```{code-cell} ipython3
contador = 0
print(contador)  # Salida: 0

contador = 5
print(contador)  # Salida: 5

contador = contador + 1
print(contador)  # Salida: 6
```

**Experimentá con reasignación:**

```{code-cell} ipython3
# Inicializa el contador
contador = 0
print(f"Valor inicial: {contador}")

# Cambio el valor
contador = 5
print(f"Después de asignar 5: {contador}")

# Incremento en 1
contador = contador + 1
print(f"Después de incrementar: {contador}")

# Experimento: duplicamos el valor
contador = contador * 2
print(f"Después de duplicar: {contador}")
```

:::{important} Inicialización de Variables
Según la {ref}`0x0003h`, siempre debés inicializar las variables antes de usarlas. Python te dará un error si intentás usar una variable que no existe:

```python
# Incorrecto
print(resultado)  # NameError: name 'resultado' is not defined

# Correcto
resultado = 0
print(resultado)  # Salida: 0
```
:::

---

(tipos-datos)=
## Tipos de Datos Básicos

Python maneja diferentes tipos de datos. Cada tipo tiene características y usos específicos.

### Números Enteros (`int`)

Los enteros representan números sin decimales, positivos o negativos.

```{code-cell} ipython3
edad = 18
temperatura = -5
año = 2023
poblacion = 1000000
```

### Números de Punto Flotante (`float`)

Los flotantes representan números con decimales.

```{code-cell} ipython3
altura = 1.75
pi = 3.14159
temperatura = -3.5
precio = 99.99
```

:::{warning} Precisión de flotantes
Los números de punto flotante pueden tener pequeños errores de redondeo:
```{code-cell} ipython3
resultado = 0.1 + 0.2
print(resultado)  # Salida: 0.30000000000000004
```
Para comparaciones de flotantes, no uses `==`. Esto se verá más adelante.
:::

### Cadenas de Texto (`str`)

Las cadenas (strings) representan texto. Se escriben entre comillas simples (`'...'`) o dobles (`"..."`).

```{code-cell} ipython3
nombre = "María"
apellido = 'González'
mensaje = "¡Hola! ¿Cómo estás?"
direccion = 'Calle 123, Ciudad'
```

**Cadenas multilínea:**

```{code-cell} ipython3
texto_largo = """Este es un texto
que ocupa múltiples
líneas."""

print(texto_largo)
```

**Operaciones con strings:**

```{code-cell} ipython3
# Concatenación (unir strings)
nombre = "Juan"
apellido = "Pérez"
nombre_completo = nombre + " " + apellido
print(nombre_completo)  # Salida: Juan Pérez

# Repetición
separador = "-" * 20
print(separador)  # Salida: --------------------

# Longitud
mensaje = "Hola Mundo"
largo = len(mensaje)
print(largo)  # Salida: 10
```

### Booleanos (`bool`)

Los booleanos representan valores de verdad: `True` (verdadero) o `False` (falso).

```{code-cell} ipython3
es_mayor_edad = True
tiene_descuento = False
esta_lloviendo = False
```

Los booleanos son fundamentales para tomar decisiones en el código (que verás en el siguiente capítulo).

### Verificar el Tipo de una Variable

Usá la función `type()` para conocer el tipo de una variable:

```{code-cell} ipython3
edad = 25
print(type(edad))  # Salida: <class 'int'>

altura = 1.75
print(type(altura))  # Salida: <class 'float'>

nombre = "Ana"
print(type(nombre))  # Salida: <class 'str'>

activo = True
print(type(activo))  # Salida: <class 'bool'>
```

**Experimentá con tipos de datos:**

```{code-cell} ipython3
# Diferentes tipos de datos
edad = 25
altura = 1.75
nombre = "Ana"
activo = True

# Verificamos los tipos
print(f"edad es de tipo: {type(edad)}")
print(f"altura es de tipo: {type(altura)}")
print(f"nombre es de tipo: {type(nombre)}")
print(f"activo es de tipo: {type(activo)}")

# Ejemplo: tipo de operaciones
resultado_suma = 5 + 3
resultado_division = 10 / 2
print(f"\n5 + 3 = {resultado_suma}, tipo: {type(resultado_suma)}")
print(f"10 / 2 = {resultado_division}, tipo: {type(resultado_division)}")
```

### Tabla Resumen de Tipos Básicos

| Tipo | Nombre | Ejemplo | Descripción |
|------|--------|---------|-------------|
| `int` | Entero | `42`, `-10`, `0` | Números enteros sin decimales |
| `float` | Flotante | `3.14`, `-0.5`, `2.0` | Números con decimales |
| `str` | Cadena | `"Hola"`, `'Python'` | Texto entre comillas |
| `bool` | Booleano | `True`, `False` | Valores de verdad |

---

(operadores-aritmeticos)=
## Operadores Aritméticos

Python soporta las operaciones matemáticas básicas y algunas adicionales.

### Operadores Básicos

```{code-cell} ipython3
# Suma
resultado = 5 + 3
print(resultado)  # Salida: 8

# Resta
resultado = 10 - 4
print(resultado)  # Salida: 6

# Multiplicación
resultado = 7 * 6
print(resultado)  # Salida: 42

# División (siempre retorna float)
resultado = 15 / 3
print(resultado)  # Salida: 5.0

# División entera (descarta decimales)
resultado = 17 // 5
print(resultado)  # Salida: 3

# Módulo (resto de la división)
resultado = 17 % 5
print(resultado)  # Salida: 2

# Potenciación
resultado = 2 ** 3
print(resultado)  # Salida: 8
```

**¡Experimentá con operadores aritméticos!**

```{code-cell} ipython3
# Operadores aritméticos básicos
print("=== OPERADORES ARITMÉTICOS ===")
print(f"5 + 3 = {5 + 3}")
print(f"10 - 4 = {10 - 4}")
print(f"7 * 6 = {7 * 6}")
print(f"15 / 3 = {15 / 3}")
print(f"17 // 5 = {17 // 5} (división entera)")
print(f"17 % 5 = {17 % 5} (módulo/resto)")
print(f"2 ** 3 = {2 ** 3} (potencia)")

# Ejemplo práctico: cálculo de área
base = 5
altura = 10
area = (base * altura) / 2
print(f"\nÁrea de triángulo (base={base}, altura={altura}): {area}")
```

:::{note} Espaciado en Operadores
Siguiendo la {ref}`0x0004h`, siempre debés colocar un espacio antes y después de cada operador binario:

```python
# Incorrecto
resultado=10+5*2

# Correcto
resultado = 10 + 5 * 2
```
:::

### Orden de Precedencia

Python sigue el orden matemático estándar (PEMDAS):

1. **P**aréntesis
2. **E**xponenciación (`**`)
3. **M**ultiplicación, **D**ivisión, División entera, Módulo (`*`, `/`, `//`, `%`)
4. **S**uma, **R**esta (`+`, `-`)

```{code-cell} ipython3
# Sin paréntesis
resultado = 2 + 3 * 4
print(resultado)  # Salida: 14 (primero 3*4, luego +2)

# Con paréntesis
resultado = (2 + 3) * 4
print(resultado)  # Salida: 20 (primero 2+3, luego *4)
```

:::{tip} Usar paréntesis para claridad
Aunque conozcas la precedencia de operadores, usar paréntesis hace el código más claro:

```{code-cell} ipython3
# Menos claro
total = precio * cantidad + descuento * 0.1

# Más claro
total = (precio * cantidad) + (descuento * 0.1)
```
:::

### Operadores de Asignación Compuesta

Python permite combinar operaciones con asignación:

```{code-cell} ipython3
contador = 10

# Equivalente a: contador = contador + 5
contador += 5
print(contador)  # Salida: 15

# Equivalente a: contador = contador - 3
contador -= 3
print(contador)  # Salida: 12

# Equivalente a: contador = contador * 2
contador *= 2
print(contador)  # Salida: 24

# Equivalente a: contador = contador / 4
contador /= 4
print(contador)  # Salida: 6.0
```

### Tabla Resumen de Operadores Aritméticos

| Operador | Operación | Ejemplo | Resultado |
|----------|-----------|---------|-----------|
| `+` | Suma | `5 + 3` | `8` |
| `-` | Resta | `10 - 4` | `6` |
| `*` | Multiplicación | `7 * 6` | `42` |
| `/` | División | `15 / 3` | `5.0` |
| `//` | División entera | `17 // 5` | `3` |
| `%` | Módulo (resto) | `17 % 5` | `2` |
| `**` | Potenciación | `2 ** 3` | `8` |

---

(operadores-comparacion)=
## Operadores de Comparación

Los operadores de comparación comparan dos valores y retornan un booleano (`True` o `False`).

```{code-cell} ipython3
# Igualdad
print(5 == 5)   # Salida: True
print(5 == 3)   # Salida: False

# Desigualdad
print(5 != 3)   # Salida: True
print(5 != 5)   # Salida: False

# Mayor que
print(8 > 5)    # Salida: True
print(3 > 10)   # Salida: False

# Menor que
print(3 < 10)   # Salida: True
print(8 < 5)    # Salida: False

# Mayor o igual que
print(5 >= 5)   # Salida: True
print(5 >= 3)   # Salida: True
print(3 >= 5)   # Salida: False

# Menor o igual que
print(3 <= 5)   # Salida: True
print(5 <= 5)   # Salida: True
print(8 <= 5)   # Salida: False
```

**Probá operadores de comparación:**

```{code-cell} ipython3
# Operadores de comparación
print("=== OPERADORES DE COMPARACIÓN ===")

edad = 18
print(f"edad = {edad}")
print(f"edad == 18: {edad == 18}")
print(f"edad != 16: {edad != 16}")
print(f"edad > 16: {edad > 16}")
print(f"edad >= 18: {edad >= 18}")
print(f"edad < 21: {edad < 21}")
print(f"edad <= 18: {edad <= 18}")

# Ejemplo práctico
precio = 100
descuento_disponible = precio > 50
print(f"\nPrecio: ${precio}")
print(f"¿Descuento disponible? (precio > 50): {descuento_disponible}")
```

:::{important} Comparación vs Asignación
No confundas el operador de comparación `==` con el de asignación `=`:

```{code-cell} ipython3
# Asignación: guarda un valor en una variable
edad = 18

# Comparación: compara dos valores
es_mayor = edad == 18  # True
```
:::

### Comparando Strings

Los strings se comparan lexicográficamente (orden del diccionario):

```{code-cell} ipython3
print("a" < "b")        # Salida: True
print("manzana" < "pera")  # Salida: True
print("Ana" == "ana")   # Salida: False (sensible a mayúsculas)
```

### Tabla de Operadores de Comparación

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `==` | Igual a | `5 == 5` | `True` |
| `!=` | Diferente de | `5 != 3` | `True` |
| `>` | Mayor que | `8 > 5` | `True` |
| `<` | Menor que | `3 < 10` | `True` |
| `>=` | Mayor o igual que | `5 >= 5` | `True` |
| `<=` | Menor o igual que | `3 <= 5` | `True` |

---

(operadores-logicos)=
## Operadores Lógicos

Los operadores lógicos permiten combinar expresiones booleanas.

### Operador `and` (Y lógico)

Retorna `True` solo si **ambas** condiciones son verdaderas.

```{code-cell} ipython3
edad = 20
tiene_licencia = True

puede_conducir = edad >= 18 and tiene_licencia
print(puede_conducir)  # Salida: True

# Tabla de verdad de and
print(True and True)    # Salida: True
print(True and False)   # Salida: False
print(False and True)   # Salida: False
print(False and False)  # Salida: False
```

### Operador `or` (O lógico)

Retorna `True` si **al menos una** condición es verdadera.

```{code-cell} ipython3
es_fin_semana = True
es_feriado = False

puede_descansar = es_fin_semana or es_feriado
print(puede_descansar)  # Salida: True

# Tabla de verdad de or
print(True or True)     # Salida: True
print(True or False)    # Salida: True
print(False or True)    # Salida: True
print(False or False)   # Salida: False
```

### Operador `not` (Negación)

Invierte el valor booleano.

```{code-cell} ipython3
esta_lloviendo = False
hace_buen_tiempo = not esta_lloviendo
print(hace_buen_tiempo)  # Salida: True

# Tabla de verdad de not
print(not True)   # Salida: False
print(not False)  # Salida: True
```

**Experimentá con operadores lógicos:**

```{code-cell} ipython3
# Operadores lógicos
print("=== OPERADORES LÓGICOS ===")

edad = 20
tiene_licencia = True
tiene_seguro = False

# AND: ambas deben ser verdaderas
puede_conducir = edad >= 18 and tiene_licencia
print(f"Edad: {edad}, Tiene licencia: {tiene_licencia}")
print(f"¿Puede conducir? (edad >= 18 AND tiene_licencia): {puede_conducir}")

# OR: al menos una debe ser verdadera
es_fin_semana = True
es_feriado = False
puede_descansar = es_fin_semana or es_feriado
print(f"\n¿Fin de semana?: {es_fin_semana}, ¿Feriado?: {es_feriado}")
print(f"¿Puede descansar? (fin_semana OR feriado): {puede_descansar}")

# NOT: invierte el valor
esta_lloviendo = False
buen_tiempo = not esta_lloviendo
print(f"\n¿Está lloviendo?: {esta_lloviendo}")
print(f"¿Hace buen tiempo? (NOT lloviendo): {buen_tiempo}")

# Combinación compleja
print(f"\n¿Puede conducir legalmente?")
puede_conducir_legal = edad >= 18 and tiene_licencia and tiene_seguro
print(f"(edad >= 18 AND licencia AND seguro): {puede_conducir_legal}")
```

### Combinando Operadores Lógicos

```{code-cell} ipython3
edad = 25
tiene_experiencia = True
tiene_titulo = False

# Múltiples condiciones
puede_aplicar = edad >= 21 and (tiene_experiencia or tiene_titulo)
print(puede_aplicar)  # Salida: True
```

:::{tip} Claridad en Condiciones Complejas
Según la {ref}`0x000Dh`, las condiciones complejas deben simplificarse:

```{code-cell} ipython3
# Menos claro
if edad >= 18 and tiene_dni and (es_argentino or tiene_residencia) and not esta_inhabilitado:
    print("Puede votar")

# Más claro
cumple_edad = edad >= 18
tiene_documentacion = tiene_dni
es_residente = es_argentino or tiene_residencia
puede_votar = cumple_edad and tiene_documentacion and es_residente and not esta_inhabilitado

if puede_votar:
    print("Puede votar")
```
:::

### Tabla de Operadores Lógicos

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `and` | Y lógico | `True and False` | `False` |
| `or` | O lógico | `True or False` | `True` |
| `not` | Negación | `not True` | `False` |

---

(entrada-salida)=
## Entrada y Salida Básica

Para interactuar con el usuario, necesitamos leer datos de entrada y mostrar resultados.

### Salida: `print()`

La función `print()` muestra información en la pantalla.

```{code-cell} ipython3
# Imprimir texto
print("Hola Mundo")

# Imprimir variables
nombre = "Ana"
print(nombre)

# Imprimir múltiples valores
edad = 20
print("Nombre:", nombre, "Edad:", edad)
```

**F-strings (formateo moderno):**

```{code-cell} ipython3
nombre = "Carlos"
edad = 25

# F-string: coloca f antes de las comillas
print(f"Mi nombre es {nombre} y tengo {edad} años")
# Salida: Mi nombre es Carlos y tengo 25 años

# Formateo de números
precio = 19.99
print(f"El precio es ${precio:.2f}")
# Salida: El precio es $19.99
```

**Experimentá con `print()` y f-strings:**

```{code-cell} ipython3
# Salida con print()
print("=== SALIDA CON PRINT ===")

nombre = "Carlos"
edad = 25
altura = 1.75
precio = 99.99

# Diferentes formas de imprimir
print("Hola Mundo")
print("Nombre:", nombre)
print("Edad:", edad, "años")

# F-strings (preferidos)
print(f"\n=== F-STRINGS ===")
print(f"Mi nombre es {nombre} y tengo {edad} años")
print(f"Mido {altura}m de altura")

# Formateo numérico
print(f"\nPrecio sin formato: ${precio}")
print(f"Precio con 2 decimales: ${precio:.2f}")
print(f"Precio con 0 decimales: ${precio:.0f}")

# Expresiones dentro de f-strings
print(f"\nEl próximo año tendré {edad + 1} años")
print(f"Mi nombre tiene {len(nombre)} letras")

# Alineación y formato
for i in range(1, 6):
    cuadrado = i ** 2
    print(f"{i:2d} al cuadrado es {cuadrado:3d}")
```

:::{tip} F-strings son preferibles
Los f-strings (Python 3.6+) son la forma más legible y Pythonic de formatear strings. Preferílos sobre `%` o `.format()`.
:::

### Entrada: `input()`

La función `input()` lee texto desde el teclado. **Siempre retorna un string**.

```{code-cell} ipython3
# Leer texto
nombre = input("Ingrese su nombre: ")
print(f"Hola, {nombre}!")
```

**Conversión de tipos:**

Como `input()` siempre retorna un string, debés convertir explícitamente a otros tipos:

```{code-cell} ipython3
# Leer un número entero
edad_str = input("Ingrese su edad: ")
edad = int(edad_str)  # Convertir string a int

# O en una línea
edad = int(input("Ingrese su edad: "))

# Leer un número flotante
altura = float(input("Ingrese su altura en metros: "))

print(f"Tiene {edad} años y mide {altura}m")
```

:::{warning} Validación de Entrada
En este capítulo asumimos que el usuario ingresa datos válidos. En capítulos posteriores aprenderás a validar y manejar errores de entrada.

```python
# Esto dará error si el usuario no ingresa un número
edad = int(input("Edad: "))  # Si escribe "veinte" → ValueError
```
:::

### Ejemplo Completo

```{code-cell} ipython3
# Programa que calcula el área de un rectángulo

# Entrada
print("=== Calculadora de Área de Rectángulo ===")
base = float(input("Ingrese la base en metros: "))
altura = float(input("Ingrese la altura en metros: "))

# Procesamiento
area = base * altura

# Salida
print(f"\nEl área del rectángulo es: {area:.2f} m²")
```

---

(conversion-tipos)=
## Conversión de Tipos (Casting)

A veces necesitás convertir un valor de un tipo a otro.

### Funciones de Conversión

```{code-cell} ipython3
# String a int
numero_str = "42"
numero_int = int(numero_str)
print(numero_int + 8)  # Salida: 50

# String a float
precio_str = "19.99"
precio_float = float(precio_str)
print(precio_float * 2)  # Salida: 39.98

# Int/float a string
edad = 25
edad_str = str(edad)
mensaje = "Tengo " + edad_str + " años"
print(mensaje)  # Salida: Tengo 25 años

# Float a int (descarta decimales)
altura = 1.85
altura_int = int(altura)
print(altura_int)  # Salida: 1

# Cualquier valor a bool
print(bool(1))      # Salida: True
print(bool(0))      # Salida: False
print(bool("hola")) # Salida: True
print(bool(""))     # Salida: False
```

**¡Experimentá con conversiones de tipos!**

```{code-cell} ipython3
# Conversión de tipos (casting)
print("=== CONVERSIÓN DE TIPOS ===\n")

# String a número
numero_str = "42"
numero_int = int(numero_str)
print(f"String '{numero_str}' convertido a int: {numero_int}")
print(f"Tipo: {type(numero_int)}")

precio_str = "19.99"
precio_float = float(precio_str)
print(f"\nString '{precio_str}' convertido a float: {precio_float}")
print(f"Tipo: {type(precio_float)}")

# Número a string
edad = 25
edad_str = str(edad)
print(f"\nInt {edad} convertido a string: '{edad_str}'")
print(f"Tipo: {type(edad_str)}")

# Float a int (trunca decimales)
altura = 1.85
altura_int = int(altura)
print(f"\nFloat {altura} convertido a int: {altura_int} (se truncan decimales)")

# Conversiones a bool
print("\n=== CONVERSIÓN A BOOL ===")
print(f"bool(1) = {bool(1)}")
print(f"bool(0) = {bool(0)}")
print(f"bool('hola') = {bool('hola')}")
print(f"bool('') = {bool('')}")
print(f"bool(3.14) = {bool(3.14)}")
print(f"bool(0.0) = {bool(0.0)}")
```

### Conversiones Implícitas

Python realiza algunas conversiones automáticamente:

```{code-cell} ipython3
# int + float → float
resultado = 5 + 3.5
print(resultado)  # Salida: 8.5 (float)
print(type(resultado))  # <class 'float'>

# Operaciones con strings requieren conversión explícita
edad = 25
# print("Tengo " + edad + " años")  # ❌ TypeError
print("Tengo " + str(edad) + " años")  # ✓ Correcto
```

### Tabla de Funciones de Conversión

| Función | Convierte a | Ejemplo |
|---------|-------------|---------|
| `int()` | Entero | `int("42")` → `42` |
| `float()` | Flotante | `float("3.14")` → `3.14` |
| `str()` | String | `str(42)` → `"42"` |
| `bool()` | Booleano | `bool(1)` → `True` |

**Practicá conversiones de tipos:**

```{code-cell} ipython3
# Conversión de tipos (casting)
print("=== CONVERSIÓN DE TIPOS ===")

# String a número
numero_str = "42"
numero_int = int(numero_str)
print(f"String '42' a int: {numero_int}, tipo: {type(numero_int)}")

precio_str = "19.99"
precio_float = float(precio_str)
print(f"String '19.99' a float: {precio_float}, tipo: {type(precio_float)}")

# Número a string
edad = 25
edad_str = str(edad)
print(f"Int 25 a string: '{edad_str}', tipo: {type(edad_str)}")

# Float a int (trunca decimales)
altura = 1.85
altura_int = int(altura)
print(f"\nFloat 1.85 a int: {altura_int} (se truncan decimales)")

# Conversiones implícitas
resultado = 5 + 3.5  # int + float = float
print(f"\n5 (int) + 3.5 (float) = {resultado}, tipo: {type(resultado)}")

# Valores "truthy" y "falsy"
print("\n=== CONVERSIÓN A BOOLEANO ===")
print(f"bool(1): {bool(1)}")
print(f"bool(0): {bool(0)}")
print(f"bool('hola'): {bool('hola')}")
print(f"bool(''): {bool('')}")
print(f"bool([1, 2, 3]): {bool([1, 2, 3])}")
print(f"bool([]): {bool([])}")
```

---

(errores-comunes)=
## Errores Comunes

### 1. Usar una variable sin inicializarla

```{code-cell} ipython3
# ❌ Incorrecto
print(total)  # NameError: name 'total' is not defined

# ✓ Correcto
total = 0
print(total)
```

### 2. Confundir `=` con `==`

```{code-cell} ipython3
# ❌ Incorrecto (asignación en lugar de comparación)
if edad = 18:  # SyntaxError
    print("Mayor de edad")

# ✓ Correcto
if edad == 18:
    print("Tiene 18 años")
```

### 3. Olvidar convertir `input()` a número

```{code-cell} ipython3
# ❌ Incorrecto
numero = input("Ingrese un número: ")
resultado = numero * 2  # Repite el string, no multiplica

# ✓ Correcto
numero = int(input("Ingrese un número: "))
resultado = numero * 2
```

### 4. División por cero

```{code-cell} ipython3
# ❌ Error en ejecución
resultado = 10 / 0  # ZeroDivisionError

# ✓ Validar antes
divisor = int(input("Divisor: "))
if divisor != 0:
    resultado = 10 / divisor
    print(resultado)
else:
    print("No se puede dividir por cero")
```

### 5. Errores de indentación

```{code-cell} ipython3
# ❌ Incorrecto (mezcla de espacios y tabs, o indentación inconsistente)
# Python es muy estricto con la indentación

# ✓ Correcto: siempre 4 espacios por nivel
def saludar():
    nombre = "Ana"
    print(f"Hola {nombre}")
```

---

(buenas-practicas)=
## Buenas Prácticas

:::{important} Principios fundamentales
Estas buenas prácticas están basadas en las reglas de estilo documentadas en el capítulo {ref}`0x0000h`.
:::

### 1. Nombres Descriptivos

Según {ref}`0x0001h`, usá nombres que describan claramente el propósito:

```{code-cell} ipython3
# ❌ Poco descriptivo
x = 25
y = 1.75

# ✓ Descriptivo
edad = 25
altura_metros = 1.75
```

### 2. Inicializar Variables

Según {ref}`0x0003h`, inicializá siempre las variables:

```{code-cell} ipython3
# ✓ Correcto
contador = 0
suma_total = 0
lista_nombres = []
```

### 3. Espaciado en Operadores

Según {ref}`0x0004h`, usá espacios alrededor de operadores:

```{code-cell} ipython3
# ❌ Difícil de leer
resultado=base*altura+10

# ✓ Fácil de leer
resultado = base * altura + 10
```

### 4. Comentarios Útiles

Los comentarios deben explicar **por qué**, no **qué**:

```{code-cell} ipython3
# ❌ Comentario obvio
edad = 18  # Asigna 18 a edad

# ✓ Comentario útil
edad = 18  # Edad mínima para votar en Argentina
```

### 5. Usar Constantes para Valores Fijos

```{code-cell} ipython3
# ✓ Constantes en MAYÚSCULAS
TASA_IVA = 0.21
MAX_INTENTOS = 3
PI = 3.14159

precio_sin_iva = 100
precio_con_iva = precio_sin_iva * (1 + TASA_IVA)
```

---

(ejercicios-fundamentos)=
## Ejercicios

(ejercicio-1-1)=
### Ejercicio 1.1: Presentación Personal

Escribí un programa que solicite al usuario su nombre, edad y ciudad, y luego muestre un mensaje de presentación.

**Entrada:**
- Nombre (string)
- Edad (int)
- Ciudad (string)

**Salida:**
Un mensaje formateado con los datos ingresados.

**Ejemplo:**
```
Ingrese su nombre: María
Ingrese su edad: 22
Ingrese su ciudad: Buenos Aires

Hola, me llamo María, tengo 22 años y vivo en Buenos Aires.
```

:::{tip}
Usá f-strings para formatear el mensaje de salida de forma clara y legible.
:::

---

(ejercicio-1-2)=
### Ejercicio 1.2: Calculadora de IMC

El Índice de Masa Corporal (IMC) se calcula con la siguiente fórmula:

$$
IMC = \frac{peso}{altura^2}
$$

Donde el peso está en kilogramos y la altura en metros.

Escribí un programa que calcule el IMC de una persona.

**Entrada:**
- Peso en kilogramos (float)
- Altura en metros (float)

**Salida:**
El IMC calculado con 2 decimales.

**Ejemplo:**
```
Ingrese su peso en kg: 70
Ingrese su altura en metros: 1.75

Su IMC es: 22.86
```

:::{tip}
Recordá usar el operador `**` para la potenciación, y formateá el resultado con `.2f` en el f-string.
:::

---

(ejercicio-1-3)=
### Ejercicio 1.3: Conversión de Temperatura

Escribí un programa que convierta una temperatura de grados Celsius a Fahrenheit usando la fórmula:

$$
F = C \times \frac{9}{5} + 32
$$

**Entrada:**
- Temperatura en Celsius (float)

**Salida:**
- Temperatura en Fahrenheit (float)

**Ejemplo:**
```
Ingrese temperatura en Celsius: 25

25.0°C equivale a 77.0°F
```

---

(ejercicio-1-4)=
### Ejercicio 1.4: Cálculo de Propina

Escribí un programa que calcule la propina a dejar en un restaurante. El programa debe solicitar el monto de la cuenta y el porcentaje de propina deseado, y mostrar:
- El monto de la propina
- El total a pagar (cuenta + propina)

**Entrada:**
- Monto de la cuenta (float)
- Porcentaje de propina (float)

**Salida:**
- Monto de propina
- Total a pagar

**Ejemplo:**
```
Ingrese el monto de la cuenta: 1000
Ingrese el porcentaje de propina: 10

Propina: $100.00
Total a pagar: $1100.00
```

---

(ejercicio-1-5)=
### Ejercicio 1.5: Calculadora de Descuento

Una tienda ofrece un descuento sobre sus productos. Escribí un programa que calcule el precio final después de aplicar el descuento.

**Entrada:**
- Precio original (float)
- Porcentaje de descuento (float)

**Salida:**
- Monto del descuento
- Precio final

**Ejemplo:**
```
Ingrese el precio original: 500
Ingrese el porcentaje de descuento: 20

Descuento: $100.00
Precio final: $400.00
```

:::{tip}
El monto del descuento se calcula como: `precio * (porcentaje / 100)`
:::

---

(ejercicio-1-6)=
### Ejercicio 1.6: Perímetro y Área de un Círculo

Escribí un programa que calcule el perímetro y el área de un círculo dado su radio.

**Fórmulas:**

$$
\text{Perímetro} = 2 \times \pi \times \text{radio}
$$

$$
\text{Área} = \pi \times \text{radio}^2
$$

**Entrada:**
- Radio del círculo (float)

**Salida:**
- Perímetro del círculo
- Área del círculo

**Ejemplo:**
```
Ingrese el radio del círculo: 5

Perímetro: 31.42
Área: 78.54
```

:::{tip}
Definí una constante `PI = 3.14159` al inicio del programa.
:::

---

(ejercicio-1-7)=
### Ejercicio 1.7: Tiempo de Viaje

Escribí un programa que calcule el tiempo de viaje dados la distancia y la velocidad promedio.

$$
Tiempo = \frac{Distancia}{Velocidad}
$$

**Entrada:**
- Distancia en kilómetros (float)
- Velocidad promedio en km/h (float)

**Salida:**
- Tiempo de viaje en horas

**Ejemplo:**
```
Ingrese la distancia en km: 150
Ingrese la velocidad promedio en km/h: 100

Tiempo de viaje: 1.50 horas
```

---

(ejercicio-1-8)=
### Ejercicio 1.8: Conversión de Unidades

Escribí un programa que convierta una distancia de millas a kilómetros.

Dato: 1 milla = 1.60934 kilómetros

**Entrada:**
- Distancia en millas (float)

**Salida:**
- Distancia en kilómetros (float)

**Ejemplo:**
```
Ingrese la distancia en millas: 10

10.0 millas equivalen a 16.09 kilómetros
```

---

(ejercicio-1-9)=
### Ejercicio 1.9: Promedio de Tres Números

Escribí un programa que calcule el promedio de tres números ingresados por el usuario.

$$
Promedio = \frac{n_1 + n_2 + n_3}{3}
$$

**Entrada:**
- Tres números (float)

**Salida:**
- El promedio de los tres números

**Ejemplo:**
```
Ingrese el primer número: 8
Ingrese el segundo número: 9
Ingrese el tercer número: 7

El promedio es: 8.00
```

---

(ejercicio-1-10)=
### Ejercicio 1.10: Intercambio de Variables

Escribí un programa que lea dos números y los intercambie. Es decir, el primer número debe quedar almacenado donde estaba el segundo, y viceversa.

**Entrada:**
- Dos números (int o float)

**Salida:**
- Los números intercambiados

**Ejemplo:**
```
Ingrese el primer número: 5
Ingrese el segundo número: 10

Antes del intercambio: a = 5, b = 10
Después del intercambio: a = 10, b = 5
```

:::{tip}
En Python podés intercambiar variables en una sola línea: `a, b = b, a`
:::


---

(uso-ia-fundamentos)=
## Uso Ético y Efectivo de la IA en Fundamentos

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
El objetivo de este curso es que **vos** aprendas a programar. La IA puede ser una herramienta poderosa para complementar tu aprendizaje, pero nunca debe reemplazar tu esfuerzo intelectual. **Vos sos, y debés ser siempre, el protagonista de tu aprendizaje.**
:::

### Buenas Prácticas para Fundamentos

En el contexto de variables, tipos de datos y operaciones básicas, podés usar la IA de estas formas productivas:

#### Generar Ejercicios Adicionales

Si comprendiste cómo funcionan las variables y querés practicar más:

- *"Genera cinco ejercicios sobre conversión de tipos en Python que involucren `int()`, `float()` y `str()`"*
- *"Crea ejercicios de práctica sobre operadores aritméticos con números enteros y flotantes"*
- *"Dame ejemplos de uso de `input()` con validación básica"*

#### Obtener Pistas (No Soluciones)

Si estás atascado en un ejercicio:

- *"Estoy trabajando en un ejercicio de promedio de tres números. Ya tengo las tres variables con los valores, ¿cuál sería el siguiente paso lógico?"*
- *"No entiendo por qué mi variable edad da error al sumarle 1. La inicialicé con `input()`. ¿Qué podría estar faltando?"*
- *"¿Cómo puedo formatear la salida de `print()` para que muestre solo 2 decimales?"*

#### Refactorizar y Mejorar tu Código

Una vez que hayas resuelto un ejercicio:

- *"Escribí este código para calcular el área de un rectángulo. ¿Sigue las buenas prácticas de PEP 8?"*
- *"¿Los nombres de mis variables son suficientemente descriptivos?"*
- *"¿Hay alguna forma más 'Pythonic' de intercambiar dos variables?"*

#### Aclarar Conceptos

Si un tema te resulta confuso:

- *"Explicame la diferencia entre `int` y `float` con ejemplos cotidianos"*
- *"¿Por qué necesito convertir el resultado de `input()` a `int` antes de hacer operaciones matemáticas?"*
- *"Dame un resumen de los operadores de comparación en Python con ejemplos"*

#### Debugging de Errores

Si encuentras un mensaje de error que no entendés:

- *"Tengo este error: `TypeError: can only concatenate str (not 'int') to str`. ¿Qué significa?"*
- *"Mi programa dice `NameError: name 'resultado' is not defined`. ¿Qué debo hacer?"*

### Malas Prácticas que Debes Evitar

:::{danger} Prohibido: Copiar Soluciones Directamente
**Nunca hagas esto:**
- Copiar el enunciado del ejercicio y pedir: *"Dame el código completo para esto"*
- Pedir que la IA escriba el programa por vos
- Usar código que no entendés "para salir del paso"

**Consecuencias:**
- No desarrollarás las habilidades de resolución de problemas
- Te encontrarás perdido en módulos siguientes
- No aprenderás a pensar algorítmicamente
- Estarás haciendo trampa contigo mismo

**El objetivo no es "entregar el ejercicio", sino "aprender a resolverlo".**
:::

### Ejemplo de Uso Correcto de IA en este Módulo

**Situación**: Estás trabajando en el Ejercicio 1.5 (calculadora de IMC) y no entendés cómo calcular la potencia.

❌ **Uso Incorrecto**:
```
Prompt: "Dame el código completo del ejercicio 1.5 de IMC"
```

✅ **Uso Correcto**:
```
Prompt: "Estoy calculando el IMC. Tengo el peso y la altura, 
pero no recuerdo cómo elevar la altura al cuadrado en Python. 
¿Cuál es el operador?"
```

**Respuesta apropiada de la IA**: "Para elevar al cuadrado en Python, usás el operador `**`. Por ejemplo: `altura ** 2`"

Ahora **vos** entendés el operador y podés completar tu solución.

:::{tip} Progresión en el uso de IA
A medida que avances en el curso, tu forma de interactuar con la IA debería evolucionar:

- **Módulo 1-2**: Preguntas sobre sintaxis básica y clarificación de errores
- **Módulo 3-4**: Refactorización de código y mejora de estilo
- **Módulo 5-6**: Exploración de alternativas de diseño y patrones

La IA es más útil cuando **ya sabés lo que estás haciendo** y querés pulir o explorar.
:::

---


---

## Resumen

En este capítulo aprendiste los fundamentos de la programación en Python:

✓ **Variables**: Cómo almacenar y manipular datos  
✓ **Tipos de datos**: `int`, `float`, `str`, `bool`  
✓ **Operadores**: Aritméticos, de comparación y lógicos  
✓ **Entrada/Salida**: `input()` y `print()`  
✓ **Conversión de tipos**: Casting entre diferentes tipos  
✓ **Buenas prácticas**: Nombres descriptivos, inicialización, espaciado  

Estos conceptos son la base sobre la cual construirás todo tu conocimiento de programación. En el próximo capítulo aprenderás a tomar decisiones en tu código usando estructuras de control de flujo.

:::{important} Practica, practica, practica
La mejor forma de consolidar estos conceptos es resolviendo los ejercicios. No te limites a leerlos; escribí el código, probalo, modificalo. La programación se aprende programando.
:::
