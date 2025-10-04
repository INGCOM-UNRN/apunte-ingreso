---
title: Estructuras de Datos
short_title: Estructuras de Datos
subtitle: Listas, tuplas, diccionarios, sets y strings avanzados en Python.
---

(estructuras-datos)=
# Estructuras de Datos

## Introducción y Motivación

Hasta ahora has trabajado con datos individuales: un número, un string, un booleano. Pero en la programación real, necesitás trabajar con **colecciones de datos**: una lista de estudiantes, los precios de productos, un inventario, las calificaciones de un curso, etc.

Las **estructuras de datos** son formas organizadas de almacenar y manipular colecciones de información. Python ofrece varias estructuras built-in, cada una con características y usos específicos.

:::{important} ¿Por qué son importantes las estructuras de datos?
Las estructuras de datos te permiten:
- **Organizar información** de forma lógica y eficiente
- **Procesar múltiples valores** sin crear cientos de variables
- **Modelar problemas reales** como inventarios, listas de usuarios, etc.
- **Escribir código más limpio** y mantenible
- **Resolver problemas complejos** de forma estructurada
:::

En este capítulo aprenderás:
- **Listas**: Colecciones ordenadas y modificables
- **Tuplas**: Colecciones ordenadas e inmutables
- **Diccionarios**: Pares clave-valor
- **Sets**: Colecciones de elementos únicos
- **Strings avanzados**: Métodos y operaciones
- **Comprensiones**: Forma concisa de crear estructuras

---

(listas)=
## Listas

Una **lista** es una colección ordenada y modificable de elementos. Es la estructura de datos más versátil y utilizada en Python.

### Crear Listas

```python
# Lista vacía
mi_lista = []

# Lista con elementos
numeros = [1, 2, 3, 4, 5]
frutas = ["manzana", "banana", "naranja"]
mixta = [1, "dos", 3.0, True]  # Puede contener diferentes tipos

# Lista de múltiples líneas
colores = [
    "rojo",
    "verde",
    "azul",
    "amarillo"
]
```

### Acceso a Elementos

Los índices en Python comienzan en **0**:

```python
frutas = ["manzana", "banana", "naranja", "pera"]

# Acceso por índice
print(frutas[0])   # "manzana"
print(frutas[1])   # "banana"
print(frutas[3])   # "pera"

# Índices negativos (desde el final)
print(frutas[-1])  # "pera" (último elemento)
print(frutas[-2])  # "naranja" (penúltimo)
```

**Diagrama de índices:**

```
Lista:  ["manzana", "banana", "naranja", "pera"]
Índice:     0          1         2         3
Negativo:  -4         -3        -2        -1
```

:::{warning} Índice fuera de rango
Intentar acceder a un índice que no existe causa un error:

```python
frutas = ["manzana", "banana"]
print(frutas[5])  # IndexError: list index out of range
```

Siempre verificá que el índice esté dentro del rango válido: `0` a `len(lista) - 1`.
:::

### Slicing (Rebanado)

El slicing permite obtener sub-listas:

```python
numeros = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# [inicio:fin] - desde inicio hasta fin-1
print(numeros[2:5])    # [2, 3, 4]

# [inicio:] - desde inicio hasta el final
print(numeros[5:])     # [5, 6, 7, 8, 9]

# [:fin] - desde el inicio hasta fin-1
print(numeros[:4])     # [0, 1, 2, 3]

# [inicio:fin:paso] - con incremento
print(numeros[0:9:2])  # [0, 2, 4, 6, 8]

# Invertir una lista
print(numeros[::-1])   # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

### Modificar Listas

Las listas son **mutables** (modificables):

```python
frutas = ["manzana", "banana", "naranja"]

# Modificar un elemento
frutas[1] = "pera"
print(frutas)  # ["manzana", "pera", "naranja"]

# Modificar con slice
frutas[0:2] = ["kiwi", "uva"]
print(frutas)  # ["kiwi", "uva", "naranja"]
```

### Métodos de Listas

#### Agregar Elementos

```python
frutas = ["manzana", "banana"]

# append() - agrega al final
frutas.append("naranja")
print(frutas)  # ["manzana", "banana", "naranja"]

# insert() - inserta en una posición
frutas.insert(1, "pera")
print(frutas)  # ["manzana", "pera", "banana", "naranja"]

# extend() - agrega múltiples elementos
frutas.extend(["kiwi", "uva"])
print(frutas)  # ["manzana", "pera", "banana", "naranja", "kiwi", "uva"]
```

#### Eliminar Elementos

```python
frutas = ["manzana", "banana", "naranja", "pera", "banana"]

# remove() - elimina la primera ocurrencia
frutas.remove("banana")
print(frutas)  # ["manzana", "naranja", "pera", "banana"]

# pop() - elimina y retorna el último elemento
ultima = frutas.pop()
print(ultima)   # "banana"
print(frutas)   # ["manzana", "naranja", "pera"]

# pop(índice) - elimina en posición específica
segunda = frutas.pop(1)
print(segunda)  # "naranja"
print(frutas)   # ["manzana", "pera"]

# del - elimina por índice o slice
numeros = [1, 2, 3, 4, 5]
del numeros[2]
print(numeros)  # [1, 2, 4, 5]

# clear() - vacía la lista
frutas.clear()
print(frutas)   # []
```

#### Búsqueda y Conteo

```python
numeros = [1, 3, 5, 3, 7, 3, 9]

# count() - cuenta ocurrencias
cantidad = numeros.count(3)
print(cantidad)  # 3

# index() - encuentra la primera posición
posicion = numeros.index(5)
print(posicion)  # 2

# in - verifica pertenencia
if 7 in numeros:
    print("7 está en la lista")

if 10 not in numeros:
    print("10 no está en la lista")
```

#### Ordenar y Revertir

```python
numeros = [5, 2, 8, 1, 9, 3]

# sort() - ordena la lista (modifica la original)
numeros.sort()
print(numeros)  # [1, 2, 3, 5, 8, 9]

# sort(reverse=True) - orden descendente
numeros.sort(reverse=True)
print(numeros)  # [9, 8, 5, 3, 2, 1]

# sorted() - retorna nueva lista ordenada (no modifica original)
original = [5, 2, 8, 1]
ordenada = sorted(original)
print(original)   # [5, 2, 8, 1]
print(ordenada)   # [1, 2, 5, 8]

# reverse() - invierte el orden
numeros = [1, 2, 3, 4, 5]
numeros.reverse()
print(numeros)  # [5, 4, 3, 2, 1]
```

### Longitud de una Lista

```python
frutas = ["manzana", "banana", "naranja"]
cantidad = len(frutas)
print(f"Hay {cantidad} frutas")  # Hay 3 frutas
```

### Iterar sobre Listas

```python
frutas = ["manzana", "banana", "naranja"]

# Forma Pythonic
for fruta in frutas:
    print(fruta)

# Con enumerate() si necesitás el índice
for i, fruta in enumerate(frutas):
    print(f"{i}: {fruta}")

# Con índices (menos Pythonic)
for i in range(len(frutas)):
    print(frutas[i])
```

### Listas Anidadas (Matrices)

```python
# Matriz 3x3
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Acceso a elementos
print(matriz[0][0])  # 1
print(matriz[1][2])  # 6
print(matriz[2][1])  # 8

# Iterar sobre matriz
for fila in matriz:
    for elemento in fila:
        print(elemento, end=" ")
    print()  # Nueva línea
```

### Tabla Resumen de Métodos de Listas

| Método | Descripción | Ejemplo |
|--------|-------------|---------|
| `append(x)` | Agrega x al final | `lista.append(5)` |
| `insert(i, x)` | Inserta x en posición i | `lista.insert(0, 5)` |
| `extend(iterable)` | Agrega elementos de iterable | `lista.extend([1,2,3])` |
| `remove(x)` | Elimina primera ocurrencia de x | `lista.remove(5)` |
| `pop([i])` | Elimina y retorna elemento en i | `lista.pop()` |
| `clear()` | Vacía la lista | `lista.clear()` |
| `index(x)` | Retorna índice de primera ocurrencia | `lista.index(5)` |
| `count(x)` | Cuenta ocurrencias de x | `lista.count(5)` |
| `sort()` | Ordena la lista | `lista.sort()` |
| `reverse()` | Invierte la lista | `lista.reverse()` |
| `copy()` | Retorna copia superficial | `nueva = lista.copy()` |

---

(tuplas)=
## Tuplas

Una **tupla** es una colección ordenada e **inmutable** (no se puede modificar después de creada). Se usa para datos que no deben cambiar.

### Crear Tuplas

```python
# Con paréntesis
coordenadas = (10, 20)
colores = ("rojo", "verde", "azul")

# Sin paréntesis (también válido)
punto = 5, 10

# Tupla de un elemento (requiere coma)
solo_uno = (5,)   # Tupla
no_tupla = (5)    # Esto es un int, no una tupla

# Tupla vacía
vacia = ()
```

### Acceso a Elementos

```python
punto = (10, 20, 30)

# Por índice
print(punto[0])   # 10
print(punto[-1])  # 30

# Slicing
numeros = (0, 1, 2, 3, 4, 5)
print(numeros[2:5])  # (2, 3, 4)
```

### Inmutabilidad

```python
punto = (10, 20)

# Intentar modificar causa error
# punto[0] = 15  # TypeError: 'tuple' object does not support item assignment

# NO se puede agregar, eliminar o modificar elementos
```

:::{note} ¿Por qué usar tuplas?
Las tuplas son útiles cuando:
1. **Los datos no deben cambiar**: coordenadas, RGB, dimensiones
2. **Mejor rendimiento**: son más rápidas que las listas
3. **Como claves de diccionarios**: las tuplas pueden, las listas no
4. **Retornar múltiples valores** de una función
:::

### Desempaquetado de Tuplas

```python
# Desempaquetado simple
punto = (10, 20)
x, y = punto
print(f"x={x}, y={y}")  # x=10, y=20

# Desempaquetado con *
numeros = (1, 2, 3, 4, 5)
primero, *resto, ultimo = numeros
print(primero)  # 1
print(resto)    # [2, 3, 4]
print(ultimo)   # 5

# Intercambio de variables
a, b = 5, 10
a, b = b, a  # Intercambio elegante
print(a, b)  # 10 5
```

### Métodos de Tuplas

Las tuplas tienen solo dos métodos:

```python
numeros = (1, 3, 5, 3, 7, 3)

# count() - cuenta ocurrencias
print(numeros.count(3))  # 3

# index() - encuentra posición
print(numeros.index(5))  # 2
```

### Convertir entre Listas y Tuplas

```python
# Lista a tupla
lista = [1, 2, 3]
tupla = tuple(lista)
print(tupla)  # (1, 2, 3)

# Tupla a lista
tupla = (4, 5, 6)
lista = list(tupla)
print(lista)  # [4, 5, 6]
```

---

(diccionarios)=
## Diccionarios

Un **diccionario** es una colección de pares **clave-valor**. Cada clave es única y se usa para acceder a su valor asociado. Es como un diccionario real: buscás una palabra (clave) y encontrás su definición (valor).

### Crear Diccionarios

```python
# Diccionario vacío
vacio = {}
tambien_vacio = dict()

# Con pares clave-valor
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Ingeniería"
}

# Claves y valores de diferentes tipos
datos = {
    "numero": 42,
    "lista": [1, 2, 3],
    "activo": True
}
```

:::{important} Claves de diccionarios
Las claves deben ser **inmutables**: strings, números, tuplas.
No pueden ser listas o diccionarios.

```python
# ✓ Válido
d = {"nombre": "Ana", 1: "uno", (1,2): "tupla"}

# ❌ Inválido
# d = {[1,2]: "lista"}  # TypeError: unhashable type: 'list'
```
:::

### Acceso a Valores

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Ingeniería"
}

# Acceso con corchetes
nombre = estudiante["nombre"]
print(nombre)  # "Ana"

# get() - más seguro (no da error si no existe)
edad = estudiante.get("edad")
print(edad)  # 20

nota = estudiante.get("nota")
print(nota)  # None

# get() con valor por defecto
nota = estudiante.get("nota", 0)
print(nota)  # 0
```

:::{tip} Usar get() en lugar de []
Es preferible usar `get()` cuando no estás seguro si la clave existe:

```python
# ❌ Puede dar error
# valor = diccionario[clave]  # KeyError si no existe

# ✓ Más seguro
valor = diccionario.get(clave, valor_por_defecto)
```
:::

### Modificar Diccionarios

```python
estudiante = {"nombre": "Ana", "edad": 20}

# Modificar valor existente
estudiante["edad"] = 21
print(estudiante)  # {"nombre": "Ana", "edad": 21}

# Agregar nueva clave-valor
estudiante["carrera"] = "Ingeniería"
print(estudiante)  # {"nombre": "Ana", "edad": 21, "carrera": "Ingeniería"}

# Eliminar con del
del estudiante["edad"]
print(estudiante)  # {"nombre": "Ana", "carrera": "Ingeniería"}

# pop() - elimina y retorna valor
carrera = estudiante.pop("carrera")
print(carrera)      # "Ingeniería"
print(estudiante)   # {"nombre": "Ana"}
```

### Métodos de Diccionarios

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Ingeniería"
}

# keys() - obtiene todas las claves
claves = estudiante.keys()
print(claves)  # dict_keys(['nombre', 'edad', 'carrera'])

# values() - obtiene todos los valores
valores = estudiante.values()
print(valores)  # dict_values(['Ana', 20, 'Ingeniería'])

# items() - obtiene pares clave-valor
items = estudiante.items()
print(items)  # dict_items([('nombre', 'Ana'), ('edad', 20), ...])

# update() - actualiza con otro diccionario
estudiante.update({"edad": 21, "ciudad": "Buenos Aires"})
print(estudiante)

# clear() - vacía el diccionario
estudiante.clear()
print(estudiante)  # {}
```

### Verificar Existencia de Claves

```python
estudiante = {"nombre": "Ana", "edad": 20}

# in - verifica si existe una clave
if "nombre" in estudiante:
    print("Tiene nombre")

if "nota" not in estudiante:
    print("No tiene nota")
```

### Iterar sobre Diccionarios

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Ingeniería"
}

# Iterar sobre claves
for clave in estudiante:
    print(clave)

# Iterar sobre claves (explícito)
for clave in estudiante.keys():
    print(clave)

# Iterar sobre valores
for valor in estudiante.values():
    print(valor)

# Iterar sobre pares clave-valor (recomendado)
for clave, valor in estudiante.items():
    print(f"{clave}: {valor}")
```

### Diccionarios Anidados

```python
# Diccionario de diccionarios
curso = {
    "estudiante1": {
        "nombre": "Ana",
        "edad": 20,
        "notas": [8, 9, 7]
    },
    "estudiante2": {
        "nombre": "Bruno",
        "edad": 21,
        "notas": [9, 8, 9]
    }
}

# Acceso a datos anidados
nombre1 = curso["estudiante1"]["nombre"]
print(nombre1)  # "Ana"

primera_nota = curso["estudiante1"]["notas"][0]
print(primera_nota)  # 8
```

### Ejemplo Práctico: Contador de Palabras

```python
"""Cuenta cuántas veces aparece cada palabra en un texto."""

texto = "python es genial python es fácil python es poderoso"
palabras = texto.split()

contador = {}
for palabra in palabras:
    if palabra in contador:
        contador[palabra] += 1
    else:
        contador[palabra] = 1

print(contador)
# {'python': 3, 'es': 3, 'genial': 1, 'fácil': 1, 'poderoso': 1}
```

### Tabla Resumen de Métodos de Diccionarios

| Método | Descripción | Ejemplo |
|--------|-------------|---------|
| `get(clave, default)` | Obtiene valor (o default) | `d.get("edad", 0)` |
| `keys()` | Retorna claves | `d.keys()` |
| `values()` | Retorna valores | `d.values()` |
| `items()` | Retorna pares (clave, valor) | `d.items()` |
| `pop(clave)` | Elimina y retorna valor | `d.pop("edad")` |
| `update(otro)` | Actualiza con otro dict | `d.update({"x": 1})` |
| `clear()` | Vacía el diccionario | `d.clear()` |

---

(sets)=
## Sets (Conjuntos)

Un **set** es una colección **no ordenada** de elementos **únicos**. Es útil para eliminar duplicados y realizar operaciones matemáticas de conjuntos.

### Crear Sets

```python
# Con llaves
numeros = {1, 2, 3, 4, 5}
colores = {"rojo", "verde", "azul"}

# Con set()
letras = set("abracadabra")
print(letras)  # {'a', 'b', 'r', 'c', 'd'} - sin duplicados

# Set vacío (DEBE usar set(), no {})
vacio = set()   # Set vacío
no_set = {}     # Esto es un diccionario vacío
```

:::{warning} Sets no tienen orden
Los sets no mantienen orden de inserción:

```python
numeros = {5, 1, 3, 2, 4}
print(numeros)  # Puede imprimir en cualquier orden
```

No podés acceder por índice: `numeros[0]` causará un error.
:::

### Operaciones Básicas

```python
# Agregar elementos
colores = {"rojo", "verde"}
colores.add("azul")
print(colores)  # {'rojo', 'verde', 'azul'}

# Agregar no tiene efecto si ya existe
colores.add("rojo")
print(colores)  # {'rojo', 'verde', 'azul'} - sin cambios

# Eliminar
colores.remove("verde")  # KeyError si no existe
print(colores)  # {'rojo', 'azul'}

# discard() - elimina sin error si no existe
colores.discard("amarillo")  # No da error
print(colores)  # {'rojo', 'azul'}

# pop() - elimina elemento arbitrario
elemento = colores.pop()
print(elemento)
```

### Operaciones de Conjuntos

```python
a = {1, 2, 3, 4, 5}
b = {4, 5, 6, 7, 8}

# Unión (elementos en a O en b)
union = a | b
print(union)  # {1, 2, 3, 4, 5, 6, 7, 8}

# O con método
union = a.union(b)

# Intersección (elementos en a Y en b)
interseccion = a & b
print(interseccion)  # {4, 5}

# O con método
interseccion = a.intersection(b)

# Diferencia (elementos en a pero NO en b)
diferencia = a - b
print(diferencia)  # {1, 2, 3}

# Diferencia simétrica (en a O b pero NO en ambos)
dif_simetrica = a ^ b
print(dif_simetrica)  # {1, 2, 3, 6, 7, 8}
```

**Diagrama de operaciones:**

```{mermaid}
flowchart LR
    A[Conjunto A<br/>{1,2,3,4,5}] 
    B[Conjunto B<br/>{4,5,6,7,8}]
    
    A -->|Unión| U["{1,2,3,4,5,6,7,8}"]
    A -->|Intersección| I["{4,5}"]
    A -->|Diferencia A-B| D["{1,2,3}"]
```

### Métodos de Verificación

```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

# Subconjunto (todos los elementos de a están en b)
print(a.issubset(b))     # True
print(a <= b)            # True

# Superconjunto (a contiene todos los elementos de b)
print(b.issuperset(a))   # True
print(b >= a)            # True

# Disjuntos (no tienen elementos en común)
x = {1, 2, 3}
y = {4, 5, 6}
print(x.isdisjoint(y))   # True
```

### Uso Práctico: Eliminar Duplicados

```python
# Eliminar duplicados de una lista
numeros = [1, 2, 2, 3, 3, 3, 4, 4, 5]
sin_duplicados = list(set(numeros))
print(sin_duplicados)  # [1, 2, 3, 4, 5]

# Nota: el orden puede cambiar
```

---

(strings-avanzados)=
## Strings Avanzados

Ya viste strings en el capítulo de fundamentos. Ahora exploraremos métodos y operaciones más avanzadas.

### Métodos de Búsqueda

```python
texto = "Python es un lenguaje de programación"

# find() - encuentra posición (-1 si no existe)
pos = texto.find("un")
print(pos)  # 10

# index() - como find() pero da error si no existe
# pos = texto.index("xyz")  # ValueError

# count() - cuenta ocurrencias
cantidad = texto.count("a")
print(cantidad)  # 4

# startswith() - verifica si comienza con
if texto.startswith("Python"):
    print("Comienza con Python")

# endswith() - verifica si termina con
if texto.endswith("ción"):
    print("Termina con ción")
```

### Métodos de Transformación

```python
texto = "Python es Genial"

# upper() - convierte a mayúsculas
print(texto.upper())  # "PYTHON ES GENIAL"

# lower() - convierte a minúsculas
print(texto.lower())  # "python es genial"

# title() - primera letra de cada palabra en mayúscula
print(texto.title())  # "Python Es Genial"

# capitalize() - solo primera letra en mayúscula
print(texto.capitalize())  # "Python es genial"

# swapcase() - invierte mayúsculas y minúsculas
print(texto.swapcase())  # "pYTHON ES gENIAL"
```

### Métodos de Validación

```python
# isalpha() - solo letras
print("Python".isalpha())      # True
print("Python3".isalpha())     # False

# isdigit() - solo dígitos
print("123".isdigit())         # True
print("12.3".isdigit())        # False

# isalnum() - letras o números
print("Python3".isalnum())     # True
print("Python 3".isalnum())    # False

# isspace() - solo espacios en blanco
print("   ".isspace())         # True
print(" a ".isspace())         # False

# isupper() / islower()
print("PYTHON".isupper())      # True
print("python".islower())      # True
```

### Métodos de Formato

```python
# strip() - elimina espacios al inicio y final
texto = "  Python  "
print(texto.strip())       # "Python"
print(texto.lstrip())      # "Python  "
print(texto.rstrip())      # "  Python"

# replace() - reemplaza subcadenas
texto = "Hola Mundo"
nuevo = texto.replace("Mundo", "Python")
print(nuevo)  # "Hola Python"

# split() - divide en lista
frase = "uno,dos,tres,cuatro"
palabras = frase.split(",")
print(palabras)  # ["uno", "dos", "tres", "cuatro"]

# join() - une lista en string
palabras = ["Python", "es", "genial"]
frase = " ".join(palabras)
print(frase)  # "Python es genial"
```

### Format Strings

```python
nombre = "Ana"
edad = 20

# F-strings (Python 3.6+) - Recomendado
mensaje = f"Me llamo {nombre} y tengo {edad} años"
print(mensaje)

# Expresiones en f-strings
x = 10
y = 20
print(f"La suma de {x} y {y} es {x + y}")

# Formato de números
pi = 3.14159
print(f"Pi: {pi:.2f}")  # Pi: 3.14

precio = 1234.56
print(f"Precio: ${precio:,.2f}")  # Precio: $1,234.56
```

### Strings Multilínea

```python
# Con triple comillas
texto = """
Este es un texto
que ocupa múltiples
líneas.
"""

# Manteniendo indentación limpia
def funcion():
    mensaje = """\
    Primera línea
    Segunda línea
    Tercera línea\
    """
    print(mensaje)
```

---

(comprensiones)=
## Comprensiones

Las **comprensiones** son una forma concisa y Pythonic de crear estructuras de datos.

### List Comprehensions

```python
# Forma tradicional
cuadrados = []
for i in range(10):
    cuadrados.append(i ** 2)

# Con list comprehension
cuadrados = [i ** 2 for i in range(10)]
print(cuadrados)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Con condición
pares = [i for i in range(20) if i % 2 == 0]
print(pares)  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Transformación con condición
numeros = [1, 2, 3, 4, 5]
dobles_pares = [n * 2 for n in numeros if n % 2 == 0]
print(dobles_pares)  # [4, 8]
```

:::{tip} Cuándo usar comprensiones
Las comprensiones son más legibles para operaciones simples:

```python
# ✓ Claro con comprensión
cuadrados = [x**2 for x in range(10)]

# ❌ Demasiado complejo para comprensión
resultado = [
    procesar(x) if validar(x) and condicion_compleja(x) else default(x)
    for x in datos if filtro1(x) and filtro2(x)
]
# Mejor con loop tradicional si es muy complejo
```
:::

### Dictionary Comprehensions

```python
# Crear diccionario de cuadrados
cuadrados = {x: x**2 for x in range(5)}
print(cuadrados)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Invertir diccionario
original = {"a": 1, "b": 2, "c": 3}
invertido = {v: k for k, v in original.items()}
print(invertido)  # {1: 'a', 2: 'b', 3: 'c'}

# Con condición
numeros = {"a": 1, "b": 2, "c": 3, "d": 4}
pares = {k: v for k, v in numeros.items() if v % 2 == 0}
print(pares)  # {'b': 2, 'd': 4}
```

### Set Comprehensions

```python
# Set de cuadrados
cuadrados = {x**2 for x in range(-5, 6)}
print(cuadrados)  # {0, 1, 4, 9, 16, 25} - sin duplicados

# Eliminar duplicados con transformación
numeros = [1, 2, 2, 3, 3, 3, 4]
unicos_dobles = {x * 2 for x in numeros}
print(unicos_dobles)  # {2, 4, 6, 8}
```

---

(operaciones-comunes)=
## Operaciones Comunes entre Estructuras

### Conversiones

```python
# Lista ⟷ Tupla
lista = [1, 2, 3]
tupla = tuple(lista)
lista_nueva = list(tupla)

# Lista ⟷ Set
lista = [1, 2, 2, 3, 3]
conjunto = set(lista)  # {1, 2, 3}
lista_sin_dup = list(conjunto)

# Diccionario → Listas
d = {"a": 1, "b": 2, "c": 3}
claves = list(d.keys())     # ['a', 'b', 'c']
valores = list(d.values())  # [1, 2, 3]
pares = list(d.items())     # [('a', 1), ('b', 2), ('c', 3)]
```

### Funciones Built-in Útiles

```python
numeros = [3, 1, 4, 1, 5, 9, 2, 6]

# len() - longitud
print(len(numeros))  # 8

# sum() - suma
print(sum(numeros))  # 31

# min() / max() - mínimo y máximo
print(min(numeros))  # 1
print(max(numeros))  # 9

# sorted() - retorna lista ordenada
ordenados = sorted(numeros)
print(ordenados)  # [1, 1, 2, 3, 4, 5, 6, 9]

# reversed() - iterador inverso
for n in reversed(numeros):
    print(n, end=" ")  # 6 2 9 5 1 4 1 3

# enumerate() - con índices
for i, n in enumerate(numeros):
    print(f"{i}: {n}")

# zip() - combina múltiples iterables
nombres = ["Ana", "Bruno", "Carlos"]
edades = [20, 21, 22]
for nombre, edad in zip(nombres, edades):
    print(f"{nombre}: {edad}")
```

---

(errores-comunes-estructuras)=
## Errores Comunes

### 1. Modificar lista mientras se itera

```python
# ❌ Incorrecto
numeros = [1, 2, 3, 4, 5]
for n in numeros:
    if n % 2 == 0:
        numeros.remove(n)  # Problemático

# ✓ Correcto - crear nueva lista
numeros = [1, 2, 3, 4, 5]
impares = [n for n in numeros if n % 2 != 0]
```

### 2. Confundir métodos que modifican vs que retornan

```python
# ❌ sort() modifica, no retorna
numeros = [3, 1, 4]
ordenados = numeros.sort()  # ordenados es None!

# ✓ Correcto
numeros.sort()  # Modifica numeros
print(numeros)  # [1, 3, 4]

# O usa sorted()
numeros = [3, 1, 4]
ordenados = sorted(numeros)  # Retorna nueva lista
```

### 3. Olvidar que sets no tienen orden

```python
# ❌ Incorrecto
conjunto = {3, 1, 4, 1, 5}
# primero = conjunto[0]  # TypeError

# ✓ Correcto - convertir a lista si necesitás índices
lista = list(conjunto)
primero = lista[0]
```

### 4. Usar lista como clave de diccionario

```python
# ❌ Incorrecto
# d = {[1, 2]: "valor"}  # TypeError: unhashable type

# ✓ Correcto - usar tupla
d = {(1, 2): "valor"}
```

### 5. Copia superficial vs profunda

```python
# Copia superficial - problemas con listas anidadas
original = [[1, 2], [3, 4]]
copia = original.copy()
copia[0][0] = 999
print(original)  # [[999, 2], [3, 4]] - modificó el original!

# ✓ Copia profunda
import copy
original = [[1, 2], [3, 4]]
copia = copy.deepcopy(original)
copia[0][0] = 999
print(original)  # [[1, 2], [3, 4]] - no afectó al original
```

---

(buenas-practicas-estructuras)=
## Buenas Prácticas

### 1. Elegir la Estructura Apropiada

```python
# Para datos únicos sin orden → Set
colores_unicos = {"rojo", "verde", "azul"}

# Para datos que no cambian → Tupla
coordenadas = (10, 20)

# Para pares clave-valor → Diccionario
estudiante = {"nombre": "Ana", "edad": 20}

# Para colección ordenada y modificable → Lista
tareas = ["estudiar", "practicar", "descansar"]
```

### 2. Usar Comprensiones para Operaciones Simples

```python
# ✓ Claro y conciso
pares = [x for x in range(20) if x % 2 == 0]

# En lugar de
pares = []
for x in range(20):
    if x % 2 == 0:
        pares.append(x)
```

### 3. Usar `in` para Verificar Pertenencia

```python
# ✓ Pythonic
if "Python" in lenguajes:
    print("Python está en la lista")

# En lugar de
encontrado = False
for lenguaje in lenguajes:
    if lenguaje == "Python":
        encontrado = True
```

### 4. Usar Métodos Apropiados

```python
# Para agregar un elemento → append()
lista.append(5)

# Para agregar múltiples → extend()
lista.extend([6, 7, 8])

# NO uses append() en un loop para múltiples
# lista.append([6, 7, 8])  # Agrega la lista como un elemento
```

### 5. Nombrar Estructuras Descriptivamente

```python
# ✓ Descriptivo
estudiantes_aprobados = ["Ana", "Bruno"]
precio_por_producto = {"manzana": 2.5, "banana": 1.8}

# ❌ Poco claro
lista1 = ["Ana", "Bruno"]
dict2 = {"manzana": 2.5, "banana": 1.8}
```

---

(ejercicios-estructuras)=
## Ejercicios

(ejercicio-3-1)=
### Ejercicio 3.1: Estadísticas de Lista

Escribí un programa que reciba una lista de números y calcule:
- El promedio
- El valor máximo y mínimo
- La cantidad de números pares e impares

**Entrada:**
Una lista de números enteros.

**Salida:**
Las estadísticas calculadas.

**Ejemplo:**
```python
numeros = [12, 7, 3, 14, 25, 8, 19, 4]

Promedio: 11.50
Máximo: 25
Mínimo: 3
Pares: 4
Impares: 4
```

---

(ejercicio-3-2)=
### Ejercicio 3.2: Eliminar Duplicados Manteniendo Orden

Escribí un programa que elimine elementos duplicados de una lista manteniendo el orden original.

**Entrada:**
Lista con posibles duplicados.

**Salida:**
Lista sin duplicados, orden preservado.

**Ejemplo:**
```python
entrada = [1, 2, 3, 2, 4, 1, 5, 3]
salida = [1, 2, 3, 4, 5]
```

:::{tip}
Podés usar un diccionario o set auxiliar para trackear elementos vistos.
:::

---

(ejercicio-3-3)=
### Ejercicio 3.3: Agenda Telefónica

Implementá una agenda telefónica usando un diccionario. El programa debe permitir:
1. Agregar contacto (nombre y teléfono)
2. Buscar teléfono por nombre
3. Eliminar contacto
4. Listar todos los contactos
5. Salir

**Ejemplo de uso:**
```
=== AGENDA TELEFÓNICA ===
1. Agregar contacto
2. Buscar contacto
3. Eliminar contacto
4. Listar contactos
5. Salir

Opción: 1
Nombre: Ana
Teléfono: 1234-5678
Contacto agregado.

Opción: 2
Nombre: Ana
Teléfono: 1234-5678
```

---

(ejercicio-3-4)=
### Ejercicio 3.4: Frecuencia de Letras

Escribí un programa que cuente la frecuencia de cada letra en un texto (ignorando mayúsculas/minúsculas y espacios).

**Entrada:**
Un string de texto.

**Salida:**
Diccionario con la frecuencia de cada letra.

**Ejemplo:**
```
Texto: "Hola Mundo"

Frecuencia de letras:
h: 1
o: 2
l: 1
a: 1
m: 1
u: 1
n: 1
d: 1
```

---

(ejercicio-3-5)=
### Ejercicio 3.5: Unión e Intersección de Listas

Dado dos listas de números, encontrá:
- Elementos que están en ambas listas (intersección)
- Elementos que están en cualquiera de las dos (unión)
- Elementos que están en la primera pero no en la segunda

**Entrada:**
Dos listas de números.

**Salida:**
Las tres operaciones de conjuntos.

**Ejemplo:**
```python
lista1 = [1, 2, 3, 4, 5]
lista2 = [4, 5, 6, 7, 8]

Intersección: [4, 5]
Unión: [1, 2, 3, 4, 5, 6, 7, 8]
Solo en lista1: [1, 2, 3]
```

---

(ejercicio-3-6)=
### Ejercicio 3.6: Matriz Transpuesta

Escribí un programa que calcule la transpuesta de una matriz (intercambiar filas por columnas).

**Entrada:**
Matriz (lista de listas).

**Salida:**
Matriz transpuesta.

**Ejemplo:**
```python
Original:
1 2 3
4 5 6

Transpuesta:
1 4
2 5
3 6
```

:::{tip}
La transpuesta de una matriz A (m×n) es una matriz B (n×m) donde `B[j][i] = A[i][j]`.
:::

---

(ejercicio-3-7)=
### Ejercicio 3.7: Inventario de Productos

Creá un sistema de inventario usando un diccionario donde:
- Clave: nombre del producto
- Valor: diccionario con precio y cantidad

El sistema debe permitir:
1. Agregar producto
2. Actualizar precio
3. Actualizar cantidad
4. Mostrar inventario
5. Calcular valor total del inventario

**Ejemplo:**
```
Inventario:
manzana - Precio: $2.50, Cantidad: 100
banana - Precio: $1.80, Cantidad: 150
naranja - Precio: $3.00, Cantidad: 80

Valor total: $690.00
```

---

(ejercicio-3-8)=
### Ejercicio 3.8: Anagramas

Escribí un programa que determine si dos palabras son anagramas (contienen las mismas letras en diferente orden).

**Entrada:**
Dos palabras (strings).

**Salida:**
Si son anagramas o no.

**Ejemplo:**
```
Palabra 1: amor
Palabra 2: roma
Son anagramas: Sí

Palabra 1: python
Palabra 2: java
Son anagramas: No
```

:::{tip}
Dos palabras son anagramas si tienen las mismas letras con la misma frecuencia.
Podés ordenar las letras o contar frecuencias.
:::

---

(ejercicio-3-9)=
### Ejercicio 3.9: Top K Elementos

Dada una lista de números, encontrá los K elementos más grandes.

**Entrada:**
- Lista de números
- K (cantidad de elementos a retornar)

**Salida:**
Los K elementos más grandes (ordenados de mayor a menor).

**Ejemplo:**
```python
numeros = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3]
k = 3

Top 3 elementos: [9, 6, 5]
```

---

(ejercicio-3-10)=
### Ejercicio 3.10: Agrupar por Propiedad

Dada una lista de estudiantes (diccionarios), agrupalos por carrera.

**Entrada:**
```python
estudiantes = [
    {"nombre": "Ana", "carrera": "Ingeniería"},
    {"nombre": "Bruno", "carrera": "Medicina"},
    {"nombre": "Carlos", "carrera": "Ingeniería"},
    {"nombre": "Diana", "carrera": "Derecho"},
    {"nombre": "Elena", "carrera": "Medicina"}
]
```

**Salida:**
```
Ingeniería: Ana, Carlos
Medicina: Bruno, Elena
Derecho: Diana
```

---

(ejercicio-3-11)=
### Ejercicio 3.11: Palabras Más Comunes

Dado un texto, encontrá las N palabras más frecuentes.

**Entrada:**
- Texto (string)
- N (cantidad de palabras a mostrar)

**Salida:**
Las N palabras más frecuentes con sus conteos.

**Ejemplo:**
```
Texto: "python es genial python es poderoso python es fácil"
N: 2

Palabras más comunes:
python: 3
es: 3
```

---

(ejercicio-3-12)=
### Ejercicio 3.12: Fusionar Diccionarios

Escribí una función que fusione dos diccionarios. Si una clave existe en ambos:
- Si los valores son números: sumarlos
- Si son listas: concatenarlas
- Caso contrario: mantener el del segundo diccionario

**Entrada:**
Dos diccionarios.

**Salida:**
Diccionario fusionado.

**Ejemplo:**
```python
d1 = {"a": 1, "b": [1, 2], "c": "x"}
d2 = {"b": [3, 4], "c": "y", "d": 2}

Resultado:
{"a": 1, "b": [1, 2, 3, 4], "c": "y", "d": 2}
```


---

(uso-ia-estructuras-datos)=
## Uso Ético y Efectivo de la IA en Estructuras de Datos

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Dominar estructuras de datos es fundamental para la programación. La IA puede ayudarte a explorar diferentes formas de resolver problemas, pero **vos debés entender cómo funcionan las estructuras** antes de usarlas.
:::

### Buenas Prácticas para Estructuras de Datos

#### Generar Ejercicios Adicionales

- *"Genera ejercicios sobre manipulación de listas en Python que incluyan append, remove y búsqueda"*
- *"Crea problemas de práctica sobre diccionarios con diferentes tipos de claves y valores"*
- *"Dame ejercicios que requieran decidir entre usar lista, tupla, diccionario o conjunto"*

#### Obtener Pistas sobre Manipulación

- *"Tengo una lista de nombres y quiero eliminar los duplicados. ¿Qué estructura de datos de Python me ayudaría?"*
- *"Necesito almacenar pares clave-valor de alumnos y sus notas. Tengo una lista de tuplas: `[('Ana', 8), ('Luis', 9)]`. ¿Hay una estructura mejor para esto?"*
- *"¿Cómo puedo verificar si un elemento existe en una lista sin recorrerla manualmente con un `for`?"*

#### Refactorizar Código

- *"Estoy usando múltiples variables para almacenar datos relacionados: `nombre1, nombre2, nombre3...`. ¿Cómo debería refactorizar esto?"*
- *"Tengo este código que busca en una lista con un loop. ¿Hay una forma más Pythonic de hacerlo?"*

#### Debugging de Operaciones

- *"Obtengo `IndexError: list index out of range`. ¿Qué significa y cómo lo prevengo?"*
- *"Modifiqué una tupla y Python dice que no puedo. ¿Por qué?"*
- *"Mi lista no se ordena correctamente con `sort()`. ¿Qué estoy haciendo mal?"*

#### Explorar Métodos y Técnicas

- *"¿Cuáles son los métodos más útiles de listas en Python?"*
- *"¿Cuándo debería usar una list comprehension y cuándo un loop `for` normal?"*
- *"¿Cuál es la diferencia entre `list.sort()` y `sorted(list)`?"*

### Ejemplos Específicos de este Módulo

**Situación 1**: Elección de estructura

❌ **Incorrecto**:
```
Prompt: "Tengo que almacenar nombres de alumnos sin repetidos. Dame el código."
```

✅ **Correcto**:
```
Prompt: "Necesito almacenar nombres sin repetidos. Estoy considerando 
usar una lista o un set. ¿Cuál sería más apropiado y por qué?"
```

**Situación 2**: Slicing

❌ **Incorrecto**:
```
Prompt: "¿Cómo obtengo los primeros 3 elementos de una lista?"
```

✅ **Correcto**:
```
Prompt: "Estoy usando `lista[0:3]` para obtener los primeros 3 elementos. 
¿Es correcto o debería ser `lista[0:2]`? Tengo confusión con el índice final."
```

### Comprensión vs Memorización

:::{tip} Enfoque correcto
No intentes memorizar todos los métodos de cada estructura. En su lugar:

1. **Entiende** qué hace cada estructura y cuándo usarla
2. **Practica** las operaciones básicas (agregar, eliminar, buscar)
3. **Consulta** la documentación (o la IA) para operaciones específicas

La IA es excelente para recordarte sintaxis, pero **vos** debés saber QUÉ operación necesitás.
:::

### Errores Comunes en este Módulo

:::{warning} No pidas código sin entender la estructura
Antes de pedir código que use listas o diccionarios, asegurate de entender:

- ¿Por qué esta estructura es apropiada?
- ¿Cómo se accede a los elementos?
- ¿Es mutable o inmutable?
- ¿Permite duplicados?
- ¿Está ordenada?

Si no podés responder estas preguntas, **leé el apunte primero**.
:::

### Uso Avanzado: Comparar Enfoques

Una vez que hayas resuelto un ejercicio, podés usar la IA para explorar:

```
Prompt: "Resolví este problema usando dos listas paralelas para nombres y edades.
¿Hay alguna ventaja en usar un diccionario en su lugar? ¿O una lista de tuplas?"
```

Este tipo de pregunta te ayuda a **profundizar tu comprensión** más allá de lo básico.

---


---

## Resumen

En este capítulo aprendiste sobre estructuras de datos en Python:

✓ **Listas**: Colecciones ordenadas y modificables  
  - Acceso, modificación, slicing  
  - Métodos: append, insert, remove, pop, sort, etc.  
  - Listas anidadas (matrices)  

✓ **Tuplas**: Colecciones ordenadas e inmutables  
  - Cuándo usarlas  
  - Desempaquetado  
  - Retornar múltiples valores  

✓ **Diccionarios**: Pares clave-valor  
  - Acceso seguro con get()  
  - Métodos: keys, values, items, update  
  - Diccionarios anidados  

✓ **Sets**: Colecciones de elementos únicos  
  - Eliminar duplicados  
  - Operaciones de conjuntos (unión, intersección, diferencia)  
  - Verificaciones de pertenencia  

✓ **Strings avanzados**: Métodos de búsqueda, transformación, validación  

✓ **Comprensiones**: Forma concisa de crear estructuras  
  - List, dict y set comprehensions  

Las estructuras de datos son fundamentales para organizar y manipular información de forma eficiente. Elegir la estructura apropiada para cada problema es clave para escribir código claro y eficiente.

:::{important} Práctica con datos reales
Las estructuras de datos cobran vida cuando trabajás con datos reales. Probá los ejercicios con diferentes conjuntos de datos y experimentá con las distintas estructuras para entender cuándo usar cada una.
:::

En el próximo capítulo, aprenderás sobre funciones, que te permitirán organizar y reutilizar tu código de forma modular.
