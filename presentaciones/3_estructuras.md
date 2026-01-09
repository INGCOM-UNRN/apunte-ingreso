---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Estructuras de Datos en Python'
footer: 'Listas, tuplas, diccionarios y sets'
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Estructuras de Datos en Python

**Listas, tuplas, diccionarios, sets y strings avanzados**

<!--
¡Buenas, buenas! Hoy nos metemos de lleno en el corazón de Python: las Estructuras de Datos. Si las variables son cajitas, las estructuras de datos son los muebles, las estanterías y los organizadores donde guardamos esas cajitas. Vamos a ver cómo organizar nuestra información de forma eficiente para no volvernos locos.
-->
---

## ¿Qué vas a aprender?

* **Listas**: colecciones mutables y ordenadas
* **Tuplas**: colecciones inmutables
* **Diccionarios**: pares clave-valor
* **Sets**: conjuntos sin duplicados
* **Comprehensions**: crear estructuras de forma elegante

<!--
El menú de hoy es contundente. Vamos a conocer a los 'cuatro fantásticos' de Python: Listas, Tuplas, Diccionarios y Sets. Cada uno tiene su superpoder y su momento de brillar. Y de postre, las 'comprehensions', que son una forma muy elegante y 'pro' de crear estas estructuras.
-->
---

## ¿Por qué Necesitamos Estructuras de Datos?

**Sin estructuras de datos:**
```python
estudiante1 = "Ana"
estudiante2 = "Bruno"
estudiante3 = "Carlos"
estudiante4 = "Diana"
# ... ¿y si tenés 1000 estudiantes? 😱
```

**Con estructuras de datos:**
```python
estudiantes = ["Ana", "Bruno", "Carlos", "Diana"]
# ¡Y podés agregar más!
```

En lugar de 1000 variables, tenés **1 lista**.

<!--
Imaginen que tienen que guardar los nombres de todos los alumnos de la universidad. ¿Van a crear `estudiante1`, `estudiante2`... hasta `estudiante1000`? ¡Ni locos! Sería inmanejable. Para eso usamos estructuras. Una sola lista `estudiantes` que contiene a todos. Es más limpio, más fácil de manejar y escalable.
-->
---

## Comparación Rápida

| Estructura | Mutable | Ordenada | Indexable | Única |
|
---
---
---
---|
---
---
---|
---
---
----|
---
---
-----|
---
----|
| **Lista** | ✅ | ✅ | ✅ | ❌ |
| **Tupla** | ❌ | ✅ | ✅ | ❌ |
| **Dict** | ✅ | ✅* | ❌ | Claves ✅ |
| **Set** | ✅ | ❌ | ❌ | ✅ |

*Ordenado desde Python 3.7+

<!--
Acá tienen un machete rápido. Las Listas son las todo terreno: ordenadas y modificables. Las Tuplas son como listas pero 'blindadas' (inmutables). Los Diccionarios son para buscar rápido por clave (como una agenda). Y los Sets son para elementos únicos, sin repetidos. Tengan esta tabla en mente.
-->
---

<!-- _class: lead -->

# Listas

<!--
Arrancamos con la reina de la fiesta: la Lista. Es una colección ordenada, lo que significa que el primero es el primero y el último es el último. Y es mutable: podés agregar, sacar y cambiar cosas a tu antojo. Se usan corchetes `[]` para definirlas.
-->
---

## ¿Qué es una Lista?

Una **lista** es una colección **ordenada** y **mutable** de elementos.

```python
frutas = ["🍎 manzana", "🍌 banana", "🍊 naranja"]
numeros = [1, 2, 3, 4, 5]
mixta = ["texto", 42, 3.14, True]
vacia = []
```

**Características:**
- Se crean con `[]`
- Pueden contener cualquier tipo de dato
- Los elementos tienen orden y posición
- Se pueden modificar después de crear

<!--
Crear listas es fácil. Pueden estar vacías, tener frutas, números o una mezcla de todo (Python es muy permisivo con esto). La función `list()` también sirve, especialmente para convertir otras cosas en listas, como los rangos.
-->
---

## Crear Listas

```python
# Lista vacía
lista = []
lista = list()

# Con elementos
frutas = ["manzana", "banana", "naranja"]

# Lista de números
numeros = [1, 2, 3, 4, 5]

# Lista mixta (diferentes tipos)
mixta = ["Ana", 25, 1.75, True]

# Lista desde range()
numeros = list(range(5))  # [0, 1, 2, 3, 4]
```

<!--
Para sacar algo de la lista, usamos su índice (su dirección). Ojo que en programación los edificios se numeran desde el 0. El primer elemento es el 0. Los índices negativos son geniales: `-1` es el último, `-2` el anteúltimo. Muy útil cuando no sabés el largo de la lista.
-->
---

## Acceder a Elementos por Índice

**Los índices empiezan en 0:**

```python
frutas = ["🍎", "🍌", "🍊", "🍐"]
#          0     1     2     3

print(frutas[0])   # 🍎 (primera)
print(frutas[1])   # 🍌 (segunda)
print(frutas[3])   # 🍐 (cuarta/última)
```

**Índices negativos (desde el final):**
```python
print(frutas[-1])  # 🍐 (última)
print(frutas[-2])  # 🍊 (penúltima)
print(frutas[-3])  # 🍌 (antepenúltima)
```

<!--
¡Alerta roja! Si tratás de acceder al piso 5 de un edificio de 2 pisos, te chocás contra el techo. Eso es el `IndexError`. Siempre verifiquen el largo con `len()` antes de acceder a índices dudosos.
-->
---

## ⚠️ Error: Índice Fuera de Rango

```python
frutas = ["🍎", "🍌"]

# ❌ Error
print(frutas[5])  # IndexError: list index out of range
```

**Cómo evitarlo:**
```python
index = 5
if index < len(frutas):
    print(frutas[index])
else:
    print(f"Índice {index} no existe")
```

<!--
El Slicing (rebanado) es una de las cosas más potentes de Python. Podés sacar sub-listas con la sintaxis `[inicio:fin]`. Acuérdense que el límite superior NO se incluye. Es como decir 'desde el 2 HASTA (pero no incluyendo) el 5'.
-->
---

## Slicing: Cortar Rebanadas 🍰

**Sintaxis:** `lista[inicio:fin:paso]`

```python
numeros = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Elementos del 2 al 5 (NO incluye el 5)
print(numeros[2:5])    # [2, 3, 4]

# Desde el inicio hasta el 4
print(numeros[:4])     # [0, 1, 2, 3]

# Desde el 5 hasta el final
print(numeros[5:])     # [5, 6, 7, 8, 9]

# Todos los elementos
print(numeros[:])      # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<!--
El slicing tiene un tercer parámetro: el paso. `[::2]` va de 2 en 2. `[::-1]` es el truco de magia para invertir una lista al instante. Es súper expresivo y eficiente.
-->
---

## Slicing con Paso

```python
numeros = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Cada 2 elementos
print(numeros[::2])    # [0, 2, 4, 6, 8]

# Cada 3 elementos
print(numeros[::3])    # [0, 3, 6, 9]

# Invertir la lista
print(numeros[::-1])   # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

# Últimos 3 elementos
print(numeros[-3:])    # [7, 8, 9]
```

<!--
Como dijimos, las listas son mutables. Podés ir a una posición específica y cambiar lo que hay ahí. 'Sacame la banana y pone uvas'. Así de simple.
-->
---

## Modificar Listas

Las listas son **mutables**: podés cambiar sus elementos

```python
frutas = ["🍎", "🍌", "🍊"]

# Cambiar un elemento
frutas[1] = "🍇"
print(frutas)  # ["🍎", "🍇", "🍊"]

# Cambiar múltiples con slicing
frutas[0:2] = ["🍓", "🍉"]
print(frutas)  # ["🍓", "🍉", "🍊"]
```

<!--
Para agregar inquilinos: `append()` lo manda al fondo de la cola. `insert()` lo mete donde vos le digas (empujando al resto). Y `extend()` es para sumar otra lista entera de una sola vez.
-->
---

## Agregar Elementos

**`append()` - agregar al final:**
```python
frutas = ["🍎", "🍌"]
frutas.append("🍊")
print(frutas)  # ["🍎", "🍌", "🍊"]
```

**`insert()` - insertar en posición:**
```python
frutas = ["🍎", "🍊"]
frutas.insert(1, "🍌")  # Inserta en índice 1
print(frutas)  # ["🍎", "🍌", "🍊"]
```

**`extend()` - agregar múltiples:**
```python
frutas = ["🍎", "🍌"]
frutas.extend(["🍊", "🍐"])
print(frutas)  # ["🍎", "🍌", "🍊", "🍐"]
```

<!--
Para desalojar: `remove()` busca el elemento y lo saca (al primero que encuentre). `pop()` saca por índice (por defecto el último) y TE LO DEVUELVE, ideal para pilas de tareas. Si no necesitás el valor, `del` también sirve.
-->
---

## Eliminar Elementos

**`remove()` - eliminar por valor:**
```python
frutas = ["🍎", "🍌", "🍊"]
frutas.remove("🍌")
print(frutas)  # ["🍎", "🍊"]
```

**`pop()` - eliminar y retornar:**
```python
frutas = ["🍎", "🍌", "🍊"]
ultima = frutas.pop()       # Elimina última
print(ultima)               # "🍊"
print(frutas)               # ["🍎", "🍌"]

segunda = frutas.pop(1)     # Elimina índice 1
print(segunda)              # "🍌"
```

<!--
¿Está el 3 en la lista? `count()` te dice cuántas veces. `index()` te dice dónde está el primero (ojo si no está, tira error). Y el operador `in` es la forma más pythonica de preguntar '¿tenemos bananas?'.
-->
---

## Buscar en Listas

**`count()` - contar ocurrencias:**
```python
numeros = [1, 3, 5, 3, 7, 3, 9]
veces = numeros.count(3)
print(veces)  # 3
```

**`index()` - encontrar posición:**
```python
frutas = ["🍎", "🍌", "🍊", "🍐"]
pos = frutas.index("🍊")
print(pos)  # 2
```

**`in` - verificar si existe:**
```python
if "🍌" in frutas:
    print("Tenemos bananas")
```

<!--
El orden es importante. `sort()` ordena la lista original (la modifica). `sorted()` te devuelve UNA COPIA ordenada y deja la original intacta. Si necesitan preservar el orden de llegada, usen `sorted()`.
-->
---

## Ordenar Listas

**`sort()` - ordena la lista (in-place):**
```python
numeros = [5, 2, 8, 1, 9]
numeros.sort()
print(numeros)  # [1, 2, 5, 8, 9]

# Orden descendente
numeros.sort(reverse=True)
print(numeros)  # [9, 8, 5, 2, 1]
```

**`sorted()` - retorna nueva lista ordenada:**
```python
original = [5, 2, 8, 1, 9]
ordenada = sorted(original)
print(original)  # [5, 2, 8, 1, 9] (sin cambios)
print(ordenada)  # [1, 2, 5, 8, 9]
```

<!--
Iterar es recorrer la lista elemento por elemento. El `for` simple es lo más común. Si necesitan saber en qué posición están, `enumerate()` es su mejor amigo. Les da el índice y el valor en cada vuelta.
-->
---

## Iterar sobre Listas

**Con `for` simple:**
```python
frutas = ["🍎", "🍌", "🍊"]
for fruta in frutas:
    print(fruta)
```

**Con índice usando `enumerate()`:**
```python
for i, fruta in enumerate(frutas):
    print(f"{i}: {fruta}")
# 0: 🍎
# 1: 🍌
# 2: 🍊
```

**Desde índice 1:**
```python
for i, fruta in enumerate(frutas, start=1):
    print(f"{i}: {fruta}")
```

<!--
List Comprehensions. Esto es Python puro. En lugar de escribir 3 líneas para llenar una lista, lo hacés en una. Se lee: 'Poné x al cuadrado PARA CADA x EN el rango'. Es conciso y generalmente más rápido.
-->
---

## List Comprehensions

Forma elegante de crear listas:

```python
# Tradicional
cuadrados = []
for i in range(10):
    cuadrados.append(i ** 2)

# Con list comprehension
cuadrados = [i ** 2 for i in range(10)]
print(cuadrados)
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

<!--
Y se pone mejor. Podés filtrar sobre la marcha. 'Solo los pares'. Es como tener un `filter` y un `map` integrados en la sintaxis de la lista.
-->
---

## Comprehensions con Condición

```python
# Solo números pares
pares = [i for i in range(20) if i % 2 == 0]
print(pares)
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Transformación con condición
numeros = [1, 2, 3, 4, 5]
dobles_pares = [n * 2 for n in numeros if n % 2 == 0]
print(dobles_pares)  # [4, 8]
```

<!--
Listas dentro de listas. Inception. Así hacemos matrices o tablas. Para acceder, usás doble corchete `[fila][columna]`. Acuérdense que siempre es fila primero.
-->
---

## Listas Anidadas (Matrices)

```python
# Matriz 3x3
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Acceder a elementos
print(matriz[0][0])  # 1 (fila 0, columna 0)
print(matriz[1][2])  # 6 (fila 1, columna 2)

# Iterar
for fila in matriz:
    for elemento in fila:
        print(elemento, end=" ")
    print()
```

<!--
Pasamos a las Tuplas. Son listas que hicieron un voto de silencio y quietud. Una vez creadas, NO CAMBIAN. Son inmutables. Se usan paréntesis `()`.
-->
---

<!-- _class: lead -->

# Tuplas

<!--
Se pueden crear con o sin paréntesis (el poder de la coma). Ojo con la tupla de un solo elemento: `(42)` es un número, `(42,)` es una tupla. Esa coma final es clave.
-->
---

## ¿Qué es una Tupla?

Una **tupla** es una colección **ordenada** e **inmutable** de elementos.

```python
punto = (10, 20)
persona = ("Ana", 25, "Argentina")
vacia = ()
un_elemento = (42,)  # Nota la coma
```

**Diferencia con listas:**
- Listas: `[]` → mutables (se pueden modificar)
- Tuplas: `()` → inmutables (NO se pueden modificar)

<!--
Intentar cambiar una tupla es chocar contra una pared. No `append`, no asignación `[0] = x`. Si querés cambiarla, tenés que crear una nueva combinando partes.
-->
---

## Crear Tuplas

```python
# Con paréntesis
coordenadas = (10, 20)
persona = ("Ana", 25, 1.75)

# Sin paréntesis (tupla implícita)
punto = 10, 20
datos = "Carlos", 30, "México"

# Tupla vacía
vacia = ()

# Tupla de un elemento (necesita coma)
solo_uno = (42,)     # ✓ Tupla
no_tupla = (42)      # ✗ Es solo el número 42
```

<!--
Para leerlas, funcionan IGUAL que las listas. Índices, slicing... todo eso anda perfecto.
-->
---

## ⚠️ Las Tuplas son Inmutables

```python
tupla = (1, 2, 3)

# ❌ No podés modificar
tupla[0] = 10  # TypeError: 'tuple' object does not support item assignment

# ❌ No podés agregar
tupla.append(4)  # AttributeError: 'tuple' object has no attribute 'append'

# ❌ No podés eliminar
del tupla[0]  # TypeError: 'tuple' object doesn't support item deletion
```

**Pero SÍ podés crear una nueva:**
```python
tupla = (1, 2, 3)
nueva = tupla + (4, 5)  # (1, 2, 3, 4, 5)
```

<!--
Como son estáticas, tienen pocos métodos. Básicamente `count` e `index`. No busquen `sort` o `reverse` acá porque modifican in-place.
-->
---

## Acceder a Elementos

Al igual que las listas:

```python
persona = ("Ana", 25, "Argentina")

print(persona[0])   # "Ana"
print(persona[1])   # 25
print(persona[-1])  # "Argentina"

# Slicing también funciona
print(persona[1:])  # (25, "Argentina")
```

<!--
El desempaquetado es magia. Podés asignar los valores de la tupla a variables sueltas en una línea. `x, y = punto`. Es súper cómodo y legible.
-->
---

## Métodos de Tuplas

Las tuplas solo tienen 2 métodos:

```python
numeros = (1, 3, 5, 3, 7, 3, 9)

# count() - contar ocurrencias
cantidad = numeros.count(3)
print(cantidad)  # 3

# index() - encontrar posición
posicion = numeros.index(5)
print(posicion)  # 2
```

<!--
El asterisco `*` captura 'todo lo demás'. Es muy útil cuando solo te interesan el primero y el último, por ejemplo.
-->
---

## Desempaquetado (Unpacking) 🎁

Extraer elementos de una tupla en variables individuales:

```python
# Ejemplo 1: Coordenadas
punto = (10, 20)
x, y = punto
print(f"x={x}, y={y}")  # x=10, y=20

# Ejemplo 2: Color RGB
color = (255, 128, 0)
rojo, verde, azul = color
print(f"R={rojo} G={verde} B={azul}")

# Ejemplo 3: Persona
persona = ("Ana", 25, "Argentina")
nombre, edad, pais = persona
print(f"{nombre} tiene {edad} años")
```

<!--
El truco de intercambiar variables en Python. En otros lenguajes necesitás una variable temporal `aux`. Acá no. `a, b = b, a`. Elegante.
-->
---

## Desempaquetado con * (Rest)

```python
numeros = (1, 2, 3, 4, 5, 6, 7, 8, 9)

# Primero y el resto
primero, *resto = numeros
print(f"Primero: {primero}")  # 1
print(f"Resto: {resto}")      # [2, 3, 4, 5, 6, 7, 8, 9]

# Primero, medio y último
primero, *medio, ultimo = numeros
print(f"Primero: {primero}")  # 1
print(f"Medio: {medio}")      # [2, 3, 4, 5, 6, 7, 8]
print(f"Último: {ultimo}")    # 9
```

<!--
¿Por qué limitarnos? Usen tuplas para cosas que son conceptualmente fijas: días de la semana, coordenadas GPS, config de base de datos. Además, ocupan menos memoria y protegen los datos.
-->
---

## Intercambio de Variables

**Forma tradicional:**
```python
a = 5
b = 10

temp = a
a = b
b = temp
print(a, b)  # 10 5
```

**Forma Pythonic (con tuplas):**
```python
a = 5
b = 10

a, b = b, a  # ¡Una sola línea!
print(a, b)  # 10 5
```

<!--
Ahora, los Diccionarios. Son la estructura más poderosa. Clave-Valor. Como una agenda: buscás 'Juan' (clave) y tenés su 'Teléfono' (valor). El acceso es instantáneo, no importa si hay 10 o 10 millones de datos.
-->
---

## ¿Cuándo usar Tuplas?

**Usá tuplas cuando:**
- Los datos no deben cambiar (coordenadas, fechas, config)
- Querés garantizar que nadie modifique los datos
- Necesitás usar como clave en diccionario
- Retornar múltiples valores de una función

**Ejemplos:**
```python
# Coordenadas (no cambian)
punto = (10, 20)

# Fecha (inmutable)
fecha = (2024, 1, 15)

# Configuración (no debe cambiar)
config = ("localhost", 8080, False)
```

<!--
Se crean con llaves `{}`. Clave a la izquierda, dos puntos, valor a la derecha. También pueden usar `dict()`.
-->
---

<!-- _class: lead -->

# Diccionarios

<!--
Accedemos por clave, no por índice. `persona['nombre']`. Si la clave no existe, explota. Por eso `get()` es más seguro: si no está, te devuelve `None` o lo que vos quieras, y el programa sigue vivo.
-->
---

## ¿Qué es un Diccionario?

Un **diccionario** es una colección de pares **clave-valor**.

```python
persona = {
    "nombre": "Ana",
    "edad": 25,
    "ciudad": "Buenos Aires"
}
```

**Analogía:** Como un diccionario real:
- **Palabra** (clave) → **Definición** (valor)
- **DNI** (clave) → **Persona** (valor)
- **Email** (clave) → **Usuario** (valor)

<!--
Son mutables. Podés cambiar el valor de una clave, o crear una clave nueva simplemente asignándole algo. `update()` sirve para mezclar diccionarios.
-->
---

## Crear Diccionarios

```python
# Diccionario vacío
vacio = {}
vacio = dict()

# Con pares clave-valor
persona = {
    "nombre": "Ana",
    "edad": 25,
    "ciudad": "Buenos Aires"
}

# Usando dict()
estudiante = dict(nombre="Carlos", nota=8.5)

# Desde lista de tuplas
datos = dict([("a", 1), ("b", 2), ("c", 3)])
```

<!--
Para borrar: `del` por clave, `pop` si querés el valor de despedida, o `clear` para limpiar la casa.
-->
---

## Acceder a Valores

```python
persona = {
    "nombre": "Ana",
    "edad": 25,
    "ciudad": "Buenos Aires"
}

# Con corchetes
print(persona["nombre"])  # "Ana"
print(persona["edad"])    # 25

# ❌ Error si la clave no existe
print(persona["telefono"])  # KeyError

# ✓ Con get() (más seguro)
print(persona.get("telefono"))  # None
print(persona.get("telefono", "No tiene"))  # "No tiene"
```

<!--
Métodos clave: `keys()` te da la lista de entradas, `values()` los datos, e `items()` te da las parejitas para iterar.
-->
---

## Modificar y Agregar

```python
persona = {"nombre": "Ana", "edad": 25}

# Modificar valor existente
persona["edad"] = 26
print(persona)  # {"nombre": "Ana", "edad": 26}

# Agregar nueva clave
persona["ciudad"] = "Buenos Aires"
print(persona)
# {"nombre": "Ana", "edad": 26, "ciudad": "Buenos Aires"}

# Agregar múltiples con update()
persona.update({"telefono": "123-456", "email": "ana@mail.com"})
```

<!--
Iterar un diccionario tiene trucos. Por defecto iterás claves. Si querés todo, usá `.items()` y desempaquetá la clave y el valor en el `for`.
-->
---

## Eliminar Elementos

```python
persona = {"nombre": "Ana", "edad": 25, "ciudad": "BA"}

# del - eliminar clave
del persona["ciudad"]
print(persona)  # {"nombre": "Ana", "edad": 25}

# pop() - eliminar y retornar valor
edad = persona.pop("edad")
print(edad)     # 25
print(persona)  # {"nombre": "Ana"}

# clear() - vaciar diccionario
persona.clear()
print(persona)  # {}
```

<!--
También existen las comprehensions para diccionarios. `{k: v ...}`. Muy útil para invertir diccionarios o filtrar datos.
-->
---

## Métodos Principales

```python
persona = {"nombre": "Ana", "edad": 25, "ciudad": "BA"}

# keys() - todas las claves
print(persona.keys())
# dict_keys(['nombre', 'edad', 'ciudad'])

# values() - todos los valores
print(persona.values())
# dict_values(['Ana', 25, 'BA'])

# items() - pares (clave, valor)
print(persona.items())
# dict_items([('nombre', 'Ana'), ('edad', 25), ('ciudad', 'BA')])
```

<!--
Diccionarios dentro de diccionarios. Ideal para estructuras complejas como JSONs de APIs. Accedés encadenando corchetes `['clave1']['clave2']`.
-->
---

## Iterar sobre Diccionarios

```python
persona = {"nombre": "Ana", "edad": 25, "ciudad": "BA"}

# Solo claves
for clave in persona:
    print(clave)

# Solo valores
for valor in persona.values():
    print(valor)

# Clave y valor
for clave, valor in persona.items():
    print(f"{clave}: {valor}")
# nombre: Ana
# edad: 25
# ciudad: BA
```

<!--
Finalmente, los Sets (Conjuntos). Son bolsas de gatos. No tienen orden, pero tienen una regla de oro: NO ADMITEN DUPLICADOS. Son súper rápidos para verificar si algo existe.
-->
---

## Dictionary Comprehensions

```python
# Crear diccionario de cuadrados
cuadrados = {x: x**2 for x in range(5)}
print(cuadrados)
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Invertir diccionario
original = {"a": 1, "b": 2, "c": 3}
invertido = {v: k for k, v in original.items()}
print(invertido)
# {1: 'a', 2: 'b', 3: 'c'}

# Con condición
numeros = {"a": 1, "b": 2, "c": 3, "d": 4}
pares = {k: v for k, v in numeros.items() if v % 2 == 0}
print(pares)  # {'b': 2, 'd': 4}
```

<!--
Ojo al crear un set vacío: `{}` es un diccionario vacío. Usen `set()`. Los sets son geniales para limpiar listas con repetidos.
-->
---

## Diccionarios Anidados

```python
estudiantes = {
    "001": {
        "nombre": "Ana",
        "edad": 20,
        "notas": [8, 9, 7]
    },
    "002": {
        "nombre": "Bruno",
        "edad": 21,
        "notas": [7, 8, 8]
    }
}

# Acceder a datos anidados
print(estudiantes["001"]["nombre"])  # "Ana"
print(estudiantes["002"]["notas"][0])  # 7

# Promedio de Ana
notas_ana = estudiantes["001"]["notas"]
print(sum(notas_ana) / len(notas_ana))  # 8.0
```

<!--
La magia de los sets: unicidad garantizada. Si metés el 4 cinco veces, solo se guarda uno. Convertir lista a set y volver a lista es el truco clásico para borrar duplicados.
-->
---

<!-- _class: lead -->

# Sets (Conjuntos)

<!--
Tienen sus propios métodos `add`, `remove`, `discard` (que no falla si no está). No hay `append` ni índices.
-->
---

## ¿Qué es un Set?

Un **set** es una colección **no ordenada** de elementos **únicos**.

```python
numeros = {1, 2, 3, 4, 5}
letras = {'a', 'b', 'c'}
mixto = {1, "dos", 3.0, True}
```

**Características:**
- No tienen orden (no indexables)
- No permiten duplicados
- Útiles para eliminar duplicados y operaciones matemáticas

<!--
Acá es donde brillan: teoría de conjuntos. Unión, Intersección, Diferencia. Si quieren saber 'usuarios que están en A pero no en B', esto se hace en una línea con sets.
-->
---

## Crear Sets

```python
# Con llaves
numeros = {1, 2, 3, 4, 5}

# Set vacío (¡NO con {}!)
vacio = set()  # ✓ Correcto
vacio = {}     # ✗ Esto es un diccionario

# Desde lista (elimina duplicados)
lista = [1, 2, 2, 3, 3, 3, 4]
conjunto = set(lista)
print(conjunto)  # {1, 2, 3, 4}

# Desde string
letras = set("hola")
print(letras)  # {'h', 'o', 'l', 'a'}
```

<!--
La diferencia simétrica es el 'XOR': están en uno o en otro, pero no en ambos. También podemos preguntar si uno incluye al otro.
-->
---

## Sets Eliminan Duplicados

```python
# Con duplicados
numeros = {1, 2, 2, 3, 3, 3, 4, 4, 4, 4}
print(numeros)  # {1, 2, 3, 4}

# Caso de uso: eliminar duplicados de lista
lista = [1, 2, 2, 3, 3, 4, 5, 5]
sin_duplicados = list(set(lista))
print(sin_duplicados)  # [1, 2, 3, 4, 5]
```

<!--
Y sí, también tienen comprehensions. Se ven igual que las de diccionarios pero sin los dos puntos.
-->
---

## Agregar y Eliminar

```python
conjunto = {1, 2, 3}

# add() - agregar un elemento
conjunto.add(4)
print(conjunto)  # {1, 2, 3, 4}

# update() - agregar múltiples
conjunto.update([5, 6, 7])
print(conjunto)  # {1, 2, 3, 4, 5, 6, 7}

# remove() - eliminar (error si no existe)
conjunto.remove(3)

# discard() - eliminar (sin error si no existe)
conjunto.discard(100)  # No da error

# pop() - eliminar y retornar elemento aleatorio
elemento = conjunto.pop()
```

<!--
Bonus track: Strings Avanzados. Los strings son inmutables (como tuplas de caracteres), pero tienen métodos super poderosos. `find`, `startswith`, `count`...
-->
---

## Operaciones de Conjuntos

**Unión** (`|` o `union()`):
```python
a = {1, 2, 3}
b = {3, 4, 5}
print(a | b)  # {1, 2, 3, 4, 5}
```

**Intersección** (`&` o `intersection()`):
```python
print(a & b)  # {3}
```

**Diferencia** (`-` o `difference()`):
```python
print(a - b)  # {1, 2}
print(b - a)  # {4, 5}
```

<!--
Transformaciones: `upper`, `lower`, `strip`. Recuerden que devuelven COPIAS nuevas, no cambian el original.
-->
---

## Más Operaciones de Conjuntos

**Diferencia simétrica** (`^` o `symmetric_difference()`):
```python
a = {1, 2, 3}
b = {3, 4, 5}
print(a ^ b)  # {1, 2, 4, 5} (elementos en uno pero no en ambos)
```

**Verificar subconjunto:**
```python
a = {1, 2}
b = {1, 2, 3, 4}
print(a.issubset(b))  # True
print(b.issuperset(a))  # True
```

<!--
`strip` es vital para limpiar inputs de usuario, saca los espacios 'basura' de los costados.
-->
---

## Set Comprehensions

```python
# Set de cuadrados
cuadrados = {x**2 for x in range(-5, 6)}
print(cuadrados)
# {0, 1, 4, 9, 16, 25} (sin duplicados)

# Eliminar duplicados con transformación
numeros = [1, 2, 2, 3, 3, 3, 4]
unicos_dobles = {x * 2 for x in numeros}
print(unicos_dobles)  # {2, 4, 6, 8}
```

<!--
`split` rompe un string en una lista (por espacios o comas). `join` hace lo contrario: pega una lista de strings con un conector.
-->
---

<!-- _class: lead -->

# Strings Avanzados

<!--
F-strings. Ya las vimos, pero insisto: úsenlas. Son lo más legible y eficiente para formatear texto y números.
-->
---

## Métodos de Búsqueda

```python
texto = "Python es genial"

# find() - retorna índice (o -1 si no encuentra)
print(texto.find("es"))  # 7
print(texto.find("xxx"))  # -1

# index() - retorna índice (error si no encuentra)
print(texto.index("es"))  # 7

# count() - cuenta ocurrencias
frase = "el gato y el perro"
print(frase.count("el"))  # 2

# startswith() / endswith()
print(texto.startswith("Python"))  # True
print(texto.endswith("genial"))  # True
```

<!--
Resumen general. Tengan esta tabla en la cabeza. ¿Necesito orden? Lista. ¿Clave-Valor? Dict. ¿Unicos? Set. ¿Inmutables? Tupla.
-->
---

## Transformaciones

```python
texto = "Python Es Genial"

# Mayúsculas y minúsculas
print(texto.upper())  # "PYTHON ES GENIAL"
print(texto.lower())  # "python es genial"
print(texto.title())  # "Python Es Genial"
print(texto.swapcase())  # "pYTHON eS gENIAL"

# Capitalizar primera letra
frase = "hola mundo"
print(frase.capitalize())  # "Hola mundo"
```

<!--
Guía rápida de decisión. Piensen en qué NECESITAN hacer con los datos, y la estructura correcta aparecerá sola.
-->
---

## Strip: Eliminar Espacios

```python
texto = "   Python   "

# strip() - elimina espacios al inicio y final
print(texto.strip())  # "Python"

# lstrip() - solo inicio
print(texto.lstrip())  # "Python   "

# rstrip() - solo final
print(texto.rstrip())  # "   Python"

# Eliminar caracteres específicos
email = "xxx@correo.comxxx"
print(email.strip("x"))  # "@correo.com"
```

<!--
Más sobre el 'cuándo usar qué'. La performance importa. Buscar en un set/dict es O(1) (instantáneo). En lista es O(n) (tengo que recorrerla).
-->
---

## Split y Join

```python
# split() - dividir en lista
frase = "Python es genial"
palabras = frase.split()
print(palabras)  # ['Python', 'es', 'genial']

# split con separador
csv = "Ana,25,Argentina"
datos = csv.split(",")
print(datos)  # ['Ana', '25', 'Argentina']

# join() - unir lista en string
palabras = ["Python", "es", "genial"]
frase = " ".join(palabras)
print(frase)  # "Python es genial"
```

<!--
Las comprehensions son una herramienta poderosa, úsenlas para escribir código más limpio y 'Pythonic'.
-->
---

## F-strings: Formateo Avanzado

```python
nombre = "Ana"
edad = 25

# Básico
print(f"Me llamo {nombre} y tengo {edad} años")

# Expresiones
x, y = 10, 20
print(f"La suma de {x} y {y} es {x + y}")

# Formato de números
pi = 3.14159
print(f"Pi: {pi:.2f}")  # "Pi: 3.14"

precio = 1234.56
print(f"Precio: ${precio:,.2f}")  # "Precio: $1,234.56"
```

<!--
Convertir entre tipos es muy común. `list(set(lista))` es un clásico. `tuple(lista)` para protegerla.
-->
---

<!-- _class: lead -->

# Resumen

<!--
Estos son los verbos que van a usar el 90% del tiempo. Apréndanselos bien.
-->
---

## Comparación de Estructuras

| Estructura | Sintaxis | Ordenada | Mutable | Duplicados | Uso Principal |
|
---
---
---
---|
---
---
----|
---
---
----|
---
---
---|
---
---
---
---|
---
---
---
---
---|
| **Lista** | `[]` | ✅ | ✅ | ✅ | Secuencias ordenadas |
| **Tupla** | `()` | ✅ | ❌ | ✅ | Datos inmutables |
| **Dict** | `{}` | ✅* | ✅ | Claves ❌ | Mapeo clave-valor |
| **Set** | `{}` | ❌ | ✅ | ❌ | Elementos únicos |

<!--
Errores clásicos. Modificar lo inmutable, índices fuera de rango, claves que no existen. Son los golpes con los que se aprende.
-->
---

## ¿Cuándo usar cada estructura?

**Lista:**
- Secuencia ordenada de elementos
- Necesitás modificar elementos
- Permiten duplicados

**Tupla:**
- Datos que no cambian
- Coordenadas, configuración
- Retornar múltiples valores

<!--
¡Eso es todo! Las estructuras de datos son los cimientos de sus programas. Practiquen mucho, combínenlas y experimenten. ¡A codear!
-->
---

## ¿Cuándo usar cada estructura? (cont.)

**Diccionario:**
- Asociar claves con valores
- Búsquedas rápidas por clave
- Datos estructurados (JSON)

**Set:**
- Eliminar duplicados
- Operaciones matemáticas de conjuntos
- Verificar pertenencia rápidamente

<!--
NO MORE NOTES
-->
---

## Comprehensions

**Lista:**
```python
[x**2 for x in range(10)]
```

**Diccionario:**
```python
{x: x**2 for x in range(5)}
```

**Set:**
```python
{x**2 for x in range(10)}
```

**Con condición:**
```python
[x for x in range(20) if x % 2 == 0]
```

<!--
NO MORE NOTES
-->
---

## Conversiones entre Estructuras

```python
# Lista ⟷ Tupla
lista = [1, 2, 3]
tupla = tuple(lista)
lista_nueva = list(tupla)

# Lista ⟷ Set
conjunto = set(lista)
lista_sin_dup = list(conjunto)

# Dict ⟷ Lista
dict_items = list(diccionario.items())
nuevo_dict = dict(lista_tuplas)
```

<!--
NO MORE NOTES
-->
---

## Métodos Más Usados

**Listas:** `append()`, `extend()`, `insert()`, `remove()`, `pop()`, `sort()`, `reverse()`

**Tuplas:** `count()`, `index()`

**Diccionarios:** `get()`, `keys()`, `values()`, `items()`, `update()`, `pop()`

**Sets:** `add()`, `remove()`, `discard()`, `union()`, `intersection()`, `difference()`

<!--
NO MORE NOTES
-->
---

## Errores Comunes

❌ Modificar tupla (son inmutables)
❌ Índice fuera de rango en listas
❌ Acceder a clave inexistente en dict (usar `get()`)
❌ Intentar indexar un set (no están ordenados)
❌ Confundir `{}` vacío (es dict, no set)
❌ Olvidar coma en tupla de un elemento: `(42,)`

<!--
NO MORE NOTES
-->
---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Las estructuras de datos son fundamentales para organizar y manipular información en tus programas.

Practicá con ejercicios para dominar cada una y saber cuándo usar cuál.
