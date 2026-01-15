---
title: Referencia de la Biblioteca
short_title: 0x0003h - Referencia
subtitle: Guía completa de métodos para str, list, dict, set y tuple en Python.
---

(referencia-tipos)=
# Referencia de Tipos de Datos en Python

```{epigraph}
"La biblioteca estándar de Python es tu mejor amiga. Conocé sus herramientas y programarás mejor."

-- Tim Peters, The Zen of Python
```

Esta guía de referencia cubre los 5 tipos de datos fundamentales:

1. **`str` (Cadenas)**: Inmutables, para texto
2. **`list` (Listas)**: Mutables, secuencias ordenadas
3. **`dict` (Diccionarios)**: Mutables, mapeos clave-valor
4. **`set` (Conjuntos)**: Mutables, colecciones únicas
5. **`tuple` (Tuplas)**: Inmutables, secuencias fijas

Esta guía es tu manual de consulta rápida para los tipos de datos más importantes de Python.

## Introducción: La Biblioteca Estándar

Python viene con una **biblioteca estándar** muy completa. Cada tipo de dato tiene métodos (funciones asociadas) que facilitan operaciones comunes. De hecho, lo que trataremos aquí es una parte mínima de todo lo que tiene disponible de forma _directa_. Python tiene un ecosistema de librerías que amplia aún más las capacidades del lenguaje, sin embargo, esto queda fuera del curso de ingreso por cuestiones de tiempo.

::::{grid} 1 1 2 2

:::{grid-item-card} 📚 Tipos Mutables

Pueden modificarse después de crearse:
- **`list`** - Listas
- **`dict`** - Diccionarios  
- **`set`** - Conjuntos
:::

:::{grid-item-card} 🔒 Tipos Inmutables

No pueden modificarse una vez creados:
- **`str`** - Cadenas
- **`tuple`** - Tuplas
- **`frozenset`** - Conjuntos inmutables
:::

::::

:::{important} Convención de Nomenclatura
Los métodos que **modifican** el objeto (mutables) no retornan nada o retornan `None`.
Los métodos que **no modifican** el objeto (inmutables) retornan un **nuevo objeto**.
:::


---

(referencia-str)=
## Cadenas (str) - Manipulación de Texto

Las cadenas son **inmutables**. Todos los métodos retornan **nuevas cadenas** sin modificar la original.

### Mapa de Métodos de Cadenas

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e3f2fd','primaryTextColor':'#1565c0','primaryBorderColor':'#1976d2','lineColor':'#42a5f5','secondaryColor':'#f3e5f5','tertiaryColor':'#fff'}}}%%
graph TB
    STR[str - Cadenas]
    
    STR --> BUSQ[Búsqueda]
    STR --> VERIF[Verificación]
    STR --> TRANS[Transformación]
    STR --> DIV[División/Unión]
    STR --> FMT[Formato]
    
    BUSQ --> B1[find<br/>index<br/>count]
    BUSQ --> B2[startswith<br/>endswith]
    
    VERIF --> V1[isdigit<br/>isalpha<br/>isalnum]
    VERIF --> V2[isupper<br/>islower<br/>isspace]
    
    TRANS --> T1[upper<br/>lower<br/>capitalize]
    TRANS --> T2[strip<br/>replace]
    
    DIV --> D1[split<br/>splitlines]
    DIV --> D2[join]
    
    FMT --> F1[format<br/>f-strings]
    FMT --> F2[center<br/>ljust<br/>rjust]
    
    style STR fill:#1565c0,stroke:#0d47a1,color:#fff
    style BUSQ fill:#42a5f5,stroke:#1976d2,color:#000
    style VERIF fill:#42a5f5,stroke:#1976d2,color:#000
    style TRANS fill:#42a5f5,stroke:#1976d2,color:#000
    style DIV fill:#42a5f5,stroke:#1976d2,color:#000
    style FMT fill:#42a5f5,stroke:#1976d2,color:#000
```

### Métodos de Búsqueda y Verificación

#### `str.find(sub, start=0, end=len)` → int

Busca la primera aparición de `sub` en la cadena. Retorna el índice o `-1` si no la encuentra.

```{code-cell} ipython3
texto = "Python es genial"
print(texto.find("es"))        # 7
print(texto.find("Java"))      # -1 (no encontrado)
print(texto.find("n", 5))      # 11 (busca desde índice 5)
```

**Usos comunes:**
- Verificar si un substring existe
- Encontrar posición de un patrón
- Buscar en segmentos específicos

```{code-cell} ipython3
# Ejemplo práctico: validar extensión de archivo
archivo = "documento.pdf"
if archivo.find(".pdf") != -1:
    print("Es un PDF")
```

#### `str.index(sub, start=0, end=len)` → int

Similar a `find()`, pero **lanza `ValueError`** si no encuentra el substring.

```{code-cell} ipython3
texto = "Python es genial"
print(texto.index("es"))       # 7

# Manejo de error
try:
    print(texto.index("Java"))
except ValueError:
    print("Substring no encontrado")
```

:::{tip} find() vs index()
- Usá **`find()`** cuando no estés seguro si el substring existe → retorna `-1`
- Usá **`index()`** cuando sepas que existe → más expresivo, lanza error si falla
:::

#### `str.count(sub, start=0, end=len)` → int

Cuenta cuántas veces aparece `sub` en la cadena.

```{code-cell} ipython3
texto = "banana"
print(texto.count("a"))        # 3
print(texto.count("an"))       # 2
print(texto.count("x"))        # 0

# Caso práctico: contar palabras
frase = "Python es Python y Python es genial"
print(frase.count("Python"))   # 3
```

#### `str.startswith(prefix, start=0, end=len)` → bool

Verifica si la cadena comienza con `prefix`.

```{code-cell} ipython3
archivo = "reporte_2024.pdf"
print(archivo.startswith("reporte"))    # True
print(archivo.startswith("datos"))      # False

# Múltiples prefijos (tupla)
print(archivo.startswith(("reporte", "informe")))  # True

# Verificar en una porción
texto = "El gato come pescado"
print(texto.startswith("gato", 3))      # True (desde índice 3)
```

**Casos de uso:**
- Validar formatos de archivo
- Filtrar elementos por prefijo
- Parsear comandos

```{code-cell} ipython3
# Filtrar archivos Python
archivos = ["main.py", "data.csv", "utils.py", "config.txt"]
archivos_py = [f for f in archivos if f.endswith(".py")]
print(archivos_py)  # ['main.py', 'utils.py']
```

#### `str.endswith(suffix, start=0, end=len)` → bool

Verifica si la cadena termina con `suffix`.

```{code-cell} ipython3
archivo = "documento.pdf"
print(archivo.endswith(".pdf"))         # True
print(archivo.endswith(".txt"))         # False

# Múltiples sufijos
print(archivo.endswith((".pdf", ".doc", ".docx")))  # True
```

#### Métodos de Verificación de Contenido

```{code-cell} ipython3
# isdigit() - solo dígitos
print("123".isdigit())         # True
print("12.3".isdigit())        # False (tiene punto)
print("12a".isdigit())         # False (tiene letra)

# isalpha() - solo letras
print("Hola".isalpha())        # True
print("Hola123".isalpha())     # False
print("Hello World".isalpha()) # False (tiene espacio)

# isalnum() - letras o números
print("Hola123".isalnum())     # True
print("Hola 123".isalnum())    # False (tiene espacio)

# isspace() - solo espacios/tabs/newlines
print("   ".isspace())         # True
print("  a  ".isspace())       # False

# isupper() / islower()
print("HOLA".isupper())        # True
print("hola".islower())        # True
print("Hola".isupper())        # False
print("Hola".islower())        # False
```

**Tabla resumen de verificación:**

| Método | Retorna True si... | Ejemplo True | Ejemplo False |
|--------|-------------------|--------------|---------------|
| `isdigit()` | Solo contiene dígitos 0-9 | `"123"` | `"12.3"` |
| `isalpha()` | Solo contiene letras | `"abc"` | `"abc123"` |
| `isalnum()` | Letras o números (sin espacios) | `"abc123"` | `"abc 123"` |
| `isspace()` | Solo espacios en blanco | `"   "` | `"  a"` |
| `isupper()` | Todas las letras en mayúscula | `"ABC"` | `"Abc"` |
| `islower()` | Todas las letras en minúscula | `"abc"` | `"Abc"` |

```{code-cell} ipython3
# Validación de entrada
def validar_codigo(codigo):
    """Valida que el código sea alfanumérico de 6 caracteres"""
    if len(codigo) != 6:
        return False, "Debe tener 6 caracteres"
    if not codigo.isalnum():
        return False, "Solo letras y números"
    return True, "Válido"

print(validar_codigo("ABC123"))  # (True, 'Válido')
print(validar_codigo("AB-123"))  # (False, 'Solo letras y números')
```

### Métodos de Transformación

#### `str.upper()` / `str.lower()` / `str.capitalize()` / `str.title()`

Conversión de mayúsculas/minúsculas.

```{code-cell} ipython3
texto = "hola mundo"

print(texto.upper())           # "HOLA MUNDO"
print(texto.lower())           # "hola mundo"
print(texto.capitalize())      # "Hola mundo" (solo primera)
print(texto.title())           # "Hola Mundo" (cada palabra)

# Casos especiales
nombre = "mARÍA garcía lópez"
print(nombre.title())          # "María García López"

# Comparación insensible a mayúsculas
usuario = "ANA"
if usuario.lower() == "ana":
    print("Usuario válido")
```

**Diferencias:**
- `capitalize()`: Solo la **primera letra** de la cadena en mayúscula
- `title()`: Primera letra de **cada palabra** en mayúscula

#### `str.strip()` / `str.lstrip()` / `str.rstrip()`

Elimina caracteres del principio y/o final.

```{code-cell} ipython3
texto = "   hola mundo   "
print(f"'{texto.strip()}'")     # 'hola mundo'
print(f"'{texto.lstrip()}'")    # 'hola mundo   '
print(f"'{texto.rstrip()}'")    # '   hola mundo'

# Eliminar caracteres específicos
url = "https://www.ejemplo.com/"
print(url.strip("https://"))    # "www.ejemplo.com/"
print(url.rstrip("/"))          # "https://www.ejemplo.com"

# Limpiar entrada de usuario
entrada = "  Ana  \n"
print(f"'{entrada.strip()}'")   # 'Ana'
```

**Parámetro `chars`:**
- Si es `None` (default): elimina espacios, tabs, newlines
- Si se especifica: elimina cualquier combinación de esos caracteres

```{code-cell} ipython3
# Eliminar múltiples caracteres
texto = "...Hola..."
print(texto.strip("."))         # "Hola"

texto2 = "xxxHolaxxx"
print(texto2.strip("x"))        # "Hola"
```

#### `str.replace(old, new, count=-1)` → str

Reemplaza ocurrencias de `old` por `new`.

```{code-cell} ipython3
texto = "Me gusta Python. Python es genial."
print(texto.replace("Python", "Java"))
# "Me gusta Java. Java es genial."

# Limitar reemplazos
print(texto.replace("Python", "Java", 1))
# "Me gusta Java. Python es genial."

# Eliminar (reemplazar por vacío)
mensaje = "Hola    mundo"  # Espacios múltiples
print(mensaje.replace("    ", " "))  # "Hola mundo"

# Caso práctico: normalizar datos
telefono = "(011) 4567-8900"
telefono_limpio = telefono.replace("(", "").replace(")", "").replace(" ", "").replace("-", "")
print(telefono_limpio)  # "01145678900"
```

### Métodos de División y Unión

#### `str.split(sep=None, maxsplit=-1)` → list

Divide la cadena en una lista.

```{code-cell} ipython3
# Split por espacios (default)
texto = "hola mundo Python"
palabras = texto.split()
print(palabras)  # ['hola', 'mundo', 'Python']

# Split por separador específico
csv = "nombre,edad,ciudad"
campos = csv.split(",")
print(campos)  # ['nombre', 'edad', 'ciudad']

# Limitar splits
texto = "uno:dos:tres:cuatro"
print(texto.split(":", 2))
# ['uno', 'dos', 'tres:cuatro']

# Procesar línea CSV
linea = "Ana,25,Bariloche"
nombre, edad, ciudad = linea.split(",")
print(f"{nombre} tiene {edad} años")
```

**Parámetro `sep`:**
- Si es `None`: divide por **cualquier** espacio en blanco (espacios, tabs, newlines) y elimina vacíos
- Si se especifica: divide **exactamente** por ese separador

```{code-cell} ipython3
# Diferencia con sep=None vs sep=" "
texto = "hola    mundo"  # Espacios múltiples

print(texto.split())      # ['hola', 'mundo']  ← Elimina vacíos
print(texto.split(" "))   # ['hola', '', '', '', 'mundo']  ← Mantiene vacíos
```

#### `str.splitlines(keepends=False)` → list

Divide por saltos de línea.

```{code-cell} ipython3
texto = """Línea 1
Línea 2
Línea 3"""

print(texto.splitlines())
# ['Línea 1', 'Línea 2', 'Línea 3']

# Mantener el \n
print(texto.splitlines(keepends=True))
# ['Línea 1\n', 'Línea 2\n', 'Línea 3']

# Caso práctico: procesar archivo
contenido = """nombre,edad
Ana,25
Bruno,30"""

lineas = contenido.splitlines()
header = lineas[0].split(",")
print(f"Columnas: {header}")
```

#### `str.join(iterable)` → str

Une elementos de un iterable con la cadena como separador.

```{code-cell} ipython3
palabras = ["Python", "es", "genial"]

# Unir con espacio
print(" ".join(palabras))  # "Python es genial"

# Unir con coma
print(", ".join(palabras))  # "Python, es, genial"

# Unir sin separador
print("".join(palabras))    # "Pythonesgenial"

# Caso común: crear CSV
datos = ["Ana", "25", "Bariloche"]
csv_line = ",".join(datos)
print(csv_line)  # "Ana,25,Bariloche"

# Construir path
partes = ["home", "usuario", "documentos", "archivo.txt"]
path = "/".join(partes)
print(path)  # "home/usuario/documentos/archivo.txt"
```

:::{important} join() es un método de str
Aunque parece al revés, `join()` es un método del **separador**, no de la lista.

```python
# ✓ Correcto
"-".join(["a", "b", "c"])  # "a-b-c"

# ❌ Incorrecto
["a", "b", "c"].join("-")  # AttributeError!
```

**Razón:** El separador es una cadena, y las cadenas saben cómo unir cosas.
:::

### Métodos de Formato

#### `str.format(*args, **kwargs)` → str

Formateo clásico con placeholders `{}`.

```{code-cell} ipython3
# Posicional
print("Hola {}, tenés {} años".format("Ana", 25))
# "Hola Ana, tenés 25 años"

# Con índices (reutilizar valores)
print("{0} {1} {0}".format("Python", "es"))  # "Python es Python"

# Con nombres (más legible)
print("{nombre} tiene {edad} años".format(nombre="Bruno", edad=30))

# Con formato numérico
print("Pi: {:.2f}".format(3.14159))      # "Pi: 3.14"
print("Número: {:05d}".format(42))       # "Número: 00042"
print("Porcentaje: {:.1%}".format(0.75)) # "Porcentaje: 75.0%"

# Alineación
print("{:<10} | {:^10} | {:>10}".format("Izq", "Centro", "Der"))
# "Izq        |   Centro   |        Der"
```

**Especificadores de formato comunes:**

| Formato | Descripción | Ejemplo |
|---------|-------------|---------|
| `:.2f` | 2 decimales | `3.14` |
| `:05d` | Entero con padding de 5 | `00042` |
| `:.1%` | Porcentaje con 1 decimal | `75.0%` |
| `:<10` | Alinear izquierda, ancho 10 | `"Python    "` |
| `:^10` | Centrar, ancho 10 | `"  Python  "` |
| `:>10` | Alinear derecha, ancho 10 | `"    Python"` |

#### f-strings (Python 3.6+)

La forma **más moderna y recomendada** de formatear cadenas.

```{code-cell} ipython3
nombre = "Ana"
edad = 25

# Básico
print(f"Hola {nombre}, tenés {edad} años")

# Con expresiones
print(f"El doble de {edad} es {edad * 2}")

# Con formato
pi = 3.14159
print(f"Pi redondeado: {pi:.2f}")

# Con métodos
texto = "python"
print(f"En mayúsculas: {texto.upper()}")

# Multilínea
mensaje = f"""
Nombre: {nombre}
Edad: {edad}
Mayor de edad: {edad >= 18}
"""
print(mensaje)
```

:::{tip} f-strings son la forma recomendada
```python
# ✓ Moderno y legible
f"Hola {nombre}"

# ✗ Antiguo (pero válido)
"Hola {}".format(nombre)

# ✗ Muy antiguo (evitar)
"Hola %s" % nombre
```
:::

#### `str.center()` / `str.ljust()` / `str.rjust()`

Alineación y relleno.

```{code-cell} ipython3
texto = "Python"

# Centrar
print(texto.center(20))        # "       Python       "
print(texto.center(20, "*"))   # "*******Python*******"

# Alinear izquierda
print(texto.ljust(20, "-"))    # "Python--------------"

# Alinear derecha
print(texto.rjust(20, "="))    # "==============Python"

# Caso práctico: tabla alineada
print("| " + "Nombre".ljust(15) + " | " + "Edad".rjust(5) + " |")
print("| " + "Ana García".ljust(15) + " | " + "25".rjust(5) + " |")
print("| " + "Bruno López".ljust(15) + " | " + "30".rjust(5) + " |")
```

#### `str.zfill(width)` → str

Rellena con ceros a la izquierda.

```{code-cell} ipython3
print("42".zfill(5))           # "00042"
print("-42".zfill(5))          # "-0042" (mantiene el signo)
print("3.14".zfill(6))         # "003.14"

# Caso práctico: IDs con formato
ids = [1, 42, 123]
ids_formato = [str(id).zfill(5) for id in ids]
print(ids_formato)  # ['00001', '00042', '00123']
```

### Tabla Resumen - Métodos de str

| Categoría | Métodos | Descripción |
|-----------|---------|-------------|
| **Búsqueda** | `find()`, `index()`, `count()` | Buscar substrings |
| | `startswith()`, `endswith()` | Verificar inicio/final |
| **Verificación** | `isdigit()`, `isalpha()`, `isalnum()` | Tipo de caracteres |
| | `isupper()`, `islower()`, `isspace()` | Estado de caracteres |
| **Transformación** | `upper()`, `lower()`, `capitalize()`, `title()` | Cambiar capitalización |
| | `replace()` | Reemplazar texto |
| **Limpieza** | `strip()`, `lstrip()`, `rstrip()` | Eliminar caracteres |
| **División** | `split()`, `splitlines()` | Dividir en lista |
| **Unión** | `join()` | Unir iterable en string |
| **Formato** | `format()`, f-strings | Interpolar valores |
| | `center()`, `ljust()`, `rjust()`, `zfill()` | Alinear y rellenar |

:::{note} Inmutabilidad
Recordá: **todos** estos métodos retornan **nuevas cadenas**. La cadena original nunca se modifica.

```python
texto = "hola"
texto.upper()  # Retorna "HOLA" pero...
print(texto)   # Sigue siendo "hola"

# Para cambiar:
texto = texto.upper()  # Ahora texto es "HOLA"
```
:::


---

(referencia-list)=
## Listas (list) - Colecciones Mutables

Las listas son **mutables**. Muchos métodos modifican la lista **en el lugar** (in-place) y retornan `None`.

### Mapa de Métodos de Listas

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e8f5e9','primaryTextColor':'#2e7d32','primaryBorderColor':'#43a047','lineColor':'#66bb6a','secondaryColor':'#fff3e0','tertiaryColor':'#fff'}}}%%
graph TB
    LIST[list - Listas]
    
    LIST --> AGR[Agregar]
    LIST --> ELIM[Eliminar]
    LIST --> BUSQ[Buscar]
    LIST --> ORD[Ordenar]
    LIST --> COPY[Copiar]
    
    AGR --> A1[append<br/>extend<br/>insert]
    
    ELIM --> E1[remove<br/>pop<br/>clear]
    
    BUSQ --> B1[index<br/>count]
    
    ORD --> O1[sort<br/>reverse]
    
    COPY --> C1[copy<br/>slicing]
    
    style LIST fill:#2e7d32,stroke:#1b5e20,color:#fff
    style AGR fill:#66bb6a,stroke:#43a047,color:#000
    style ELIM fill:#66bb6a,stroke:#43a047,color:#000
    style BUSQ fill:#66bb6a,stroke:#43a047,color:#000
    style ORD fill:#66bb6a,stroke:#43a047,color:#000
    style COPY fill:#66bb6a,stroke:#43a047,color:#000
```

### Métodos de Modificación - Agregar Elementos

#### `list.append(x)` → None

Agrega un elemento al **final** de la lista.

```{code-cell} ipython3
frutas = ["manzana", "banana"]
frutas.append("naranja")
print(frutas)  # ['manzana', 'banana', 'naranja']

# Agregar múltiples veces
frutas.append("pera")
frutas.append("uva")
print(frutas)  # ['manzana', 'banana', 'naranja', 'pera', 'uva']
```

:::{danger} Error Común - Retorno None
```python
# ❌ Incorrecto - append() retorna None
lista = [1, 2, 3]
lista = lista.append(4)  # lista ahora es None!
print(lista)  # None

# ✓ Correcto
lista = [1, 2, 3]
lista.append(4)  # Modifica la lista
print(lista)  # [1, 2, 3, 4]
```
:::

```{code-cell} ipython3
# Construir lista dinámicamente
numeros = []
for i in range(5):
    numeros.append(i ** 2)
print(numeros)  # [0, 1, 4, 9, 16]
```

#### `list.extend(iterable)` → None

Agrega **todos** los elementos de un iterable.

```{code-cell} ipython3
lista1 = [1, 2, 3]
lista2 = [4, 5, 6]

# extend() agrega cada elemento individualmente
lista1.extend(lista2)
print(lista1)  # [1, 2, 3, 4, 5, 6]

# También funciona con otros iterables
lista = [1, 2]
lista.extend("abc")
print(lista)  # [1, 2, 'a', 'b', 'c']

lista.extend((7, 8, 9))
print(lista)  # [1, 2, 'a', 'b', 'c', 7, 8, 9]
```

**Diferencia clave: `append()` vs `extend()`**

```{code-cell} ipython3
# append() agrega el objeto completo como UN elemento
lista1 = [1, 2, 3]
lista1.append([4, 5, 6])
print(lista1)  # [1, 2, 3, [4, 5, 6]]  ← Lista anidada!

# extend() agrega cada elemento del iterable
lista2 = [1, 2, 3]
lista2.extend([4, 5, 6])
print(lista2)  # [1, 2, 3, 4, 5, 6]  ← Lista plana
```

:::{tip} Cuándo usar cada uno
- `append(x)`: Cuando querés agregar un **solo** elemento (incluso si es una lista)
- `extend(iter)`: Cuando querés agregar **múltiples** elementos
:::

#### `list.insert(i, x)` → None

Inserta `x` en la posición `i`, desplazando elementos a la derecha.

```{code-cell} ipython3
numeros = [1, 2, 4, 5]
numeros.insert(2, 3)  # Insertar 3 en índice 2
print(numeros)  # [1, 2, 3, 4, 5]

# Insertar al principio
numeros.insert(0, 0)
print(numeros)  # [0, 1, 2, 3, 4, 5]

# Insertar al final (equivalente a append)
numeros.insert(len(numeros), 6)
print(numeros)  # [0, 1, 2, 3, 4, 5, 6]

# Índice mayor a len: inserta al final
numeros.insert(100, 7)
print(numeros)  # [0, 1, 2, 3, 4, 5, 6, 7]
```

:::{warning} Rendimiento de insert()
`insert(0, x)` es **lento** en listas grandes porque debe desplazar todos los elementos.

Para agregar al principio frecuentemente, considerá usar `collections.deque`.
:::

### Métodos de Eliminación

#### `list.remove(x)` → None

Elimina la **primera** aparición de `x`. Lanza `ValueError` si no existe.

```{code-cell} ipython3
frutas = ["manzana", "banana", "manzana", "naranja"]
frutas.remove("manzana")
print(frutas)  # ['banana', 'manzana', 'naranja']  ← Solo quitó la primera

# Error si no existe
try:
    frutas.remove("pera")
except ValueError as e:
    print(f"Error: {e}")
```

```{code-cell} ipython3
# Eliminar todas las apariciones
numeros = [1, 2, 3, 2, 4, 2, 5]
while 2 in numeros:
    numeros.remove(2)
print(numeros)  # [1, 3, 4, 5]

# Alternativa con list comprehension (más eficiente)
numeros = [1, 2, 3, 2, 4, 2, 5]
numeros = [n for n in numeros if n != 2]
print(numeros)  # [1, 3, 4, 5]
```

:::{tip} Eliminar sin error
```python
if "pera" in frutas:
    frutas.remove("pera")

# O manejar la excepción
try:
    frutas.remove("pera")
except ValueError:
    pass  # No hacer nada si no existe
```
:::

#### `list.pop(i=-1)` → elemento

Elimina y **retorna** el elemento en posición `i`. Por defecto, elimina el último.

```{code-cell} ipython3
numeros = [1, 2, 3, 4, 5]

# Pop último elemento (default)
ultimo = numeros.pop()
print(f"Eliminado: {ultimo}")  # 5
print(f"Lista: {numeros}")     # [1, 2, 3, 4]

# Pop índice específico
segundo = numeros.pop(1)
print(f"Eliminado: {segundo}")  # 2
print(f"Lista: {numeros}")      # [1, 3, 4]

# Pop primero
primero = numeros.pop(0)
print(f"Eliminado: {primero}")  # 1
print(f"Lista: {numeros}")      # [3, 4]
```

**Casos de uso:**

```{code-cell} ipython3
# Implementar pila (stack) - LIFO (Last In, First Out)
pila = []
pila.append(1)  # Push
pila.append(2)
pila.append(3)
print(pila.pop())  # 3 - Pop
print(pila.pop())  # 2

# Procesar elementos uno a uno
tareas = ["lavar", "cocinar", "limpiar"]
while tareas:
    tarea = tareas.pop(0)  # Toma el primero
    print(f"Haciendo: {tarea}")
```

:::{warning} Error en lista vacía
```python
lista = []
lista.pop()  # IndexError: pop from empty list

# Verificar antes
if lista:
    elemento = lista.pop()
```
:::

#### `list.clear()` → None

Elimina **todos** los elementos de la lista.

```{code-cell} ipython3
numeros = [1, 2, 3, 4, 5]
numeros.clear()
print(numeros)  # []

# Equivalente a:
# numeros = []  (pero clear() es más explícito)
# del numeros[:]
```

### Métodos de Búsqueda

#### `list.index(x, start=0, stop=len)` → int

Retorna el índice de la **primera** aparición de `x`. Lanza `ValueError` si no existe.

```{code-cell} ipython3
numeros = [10, 20, 30, 20, 40]

# Buscar desde el principio
print(numeros.index(20))       # 1 (primera aparición)

# Buscar desde una posición
print(numeros.index(20, 2))    # 3 (desde índice 2)

# Buscar en rango
print(numeros.index(20, 2, 4)) # 3 (entre índices 2 y 4)
```

```{code-cell} ipython3
# Encontrar todas las posiciones
numeros = [1, 2, 3, 2, 4, 2, 5]
posiciones = []
inicio = 0
while True:
    try:
        pos = numeros.index(2, inicio)
        posiciones.append(pos)
        inicio = pos + 1
    except ValueError:
        break
print(f"El 2 está en: {posiciones}")  # [1, 3, 5]

# Alternativa con enumerate (más Pythonic)
posiciones = [i for i, x in enumerate(numeros) if x == 2]
print(posiciones)  # [1, 3, 5]
```

#### `list.count(x)` → int

Cuenta cuántas veces aparece `x` en la lista.

```{code-cell} ipython3
numeros = [1, 2, 2, 3, 2, 4]
print(numeros.count(2))  # 3
print(numeros.count(5))  # 0

# Caso práctico: frecuencia de elementos
votos = ["A", "B", "A", "C", "A", "B"]
print(f"Votos por A: {votos.count('A')}")  # 3
print(f"Votos por B: {votos.count('B')}")  # 2
print(f"Votos por C: {votos.count('C')}")  # 1
```

### Métodos de Ordenamiento

#### `list.sort(key=None, reverse=False)` → None

Ordena la lista **en el lugar** (modifica la lista original).

```{code-cell} ipython3
numeros = [3, 1, 4, 1, 5, 9, 2]
numeros.sort()
print(numeros)  # [1, 1, 2, 3, 4, 5, 9]

# Orden descendente
numeros.sort(reverse=True)
print(numeros)  # [9, 5, 4, 3, 2, 1, 1]
```

**Parámetro `key`: función de ordenamiento**

```{code-cell} ipython3
# Ordenar por longitud
palabras = ["Python", "es", "genial", "y", "poderoso"]
palabras.sort(key=len)
print(palabras)  # ['es', 'y', 'Python', 'genial', 'poderoso']

# Ordenar strings ignorando mayúsculas
nombres = ["ana", "Bruno", "carlos", "Diana"]
nombres.sort(key=str.lower)
print(nombres)  # ['ana', 'Bruno', 'carlos', 'Diana']

# Ordenar por segundo elemento de tuplas
pares = [(1, 'b'), (2, 'a'), (3, 'c')]
pares.sort(key=lambda x: x[1])
print(pares)  # [(2, 'a'), (1, 'b'), (3, 'c')]
```

```{code-cell} ipython3
# Ordenar objetos complejos
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __repr__(self):
        return f"{self.nombre}({self.edad})"

personas = [
    Persona("Ana", 25),
    Persona("Bruno", 20),
    Persona("Carlos", 30)
]

# Ordenar por edad
personas.sort(key=lambda p: p.edad)
print(personas)  # [Bruno(20), Ana(25), Carlos(30)]

# Ordenar por nombre
personas.sort(key=lambda p: p.nombre)
print(personas)  # [Ana(25), Bruno(20), Carlos(30)]
```

**`sort()` vs `sorted()`**

```{code-cell} ipython3
# sort() - modifica en el lugar, retorna None
numeros1 = [3, 1, 4]
resultado = numeros1.sort()
print(f"Retorno: {resultado}")  # None
print(f"Lista: {numeros1}")      # [1, 3, 4]  ← Modificada

# sorted() - NO modifica, retorna nueva lista
numeros2 = [3, 1, 4]
ordenados = sorted(numeros2)
print(f"Original: {numeros2}")   # [3, 1, 4]  ← Sin cambios
print(f"Nueva: {ordenados}")     # [1, 3, 4]
```

:::{tip} Cuándo usar cada uno
- `list.sort()`: Cuando querés modificar la lista original
- `sorted()`: Cuando necesitás mantener la original + crear una nueva ordenada
:::

#### `list.reverse()` → None

Invierte el orden de los elementos **en el lugar**.

```{code-cell} ipython3
numeros = [1, 2, 3, 4, 5]
numeros.reverse()
print(numeros)  # [5, 4, 3, 2, 1]

# Útil combinado con sort
numeros = [3, 1, 4]
numeros.sort()
numeros.reverse()
print(numeros)  # [4, 3, 1] (ordenar descendente manual)
```

**Alternativas:**

```{code-cell} ipython3
numeros = [1, 2, 3, 4, 5]

# Slicing (crea nueva lista)
invertidos = numeros[::-1]
print(invertidos)  # [5, 4, 3, 2, 1]
print(numeros)     # [1, 2, 3, 4, 5] ← Sin cambios

# reversed() (retorna iterador)
for n in reversed(numeros):
    print(n, end=" ")  # 5 4 3 2 1
```

### Métodos de Copia

#### `list.copy()` → list

Crea una **copia superficial** (shallow copy) de la lista.

```{code-cell} ipython3
original = [1, 2, 3]
copia = original.copy()

copia.append(4)
print(f"Original: {original}")  # [1, 2, 3]  ← Sin cambios
print(f"Copia: {copia}")        # [1, 2, 3, 4]

# Equivalentes
copia2 = original[:]
copia3 = list(original)
```

:::{warning} Copia Superficial (Shallow Copy)
`copy()` solo copia las **referencias** del primer nivel.

```python
original = [[1, 2], [3, 4]]
copia = original.copy()

# Modificar lista interna
copia[0].append(3)
print(original)  # [[1, 2, 3], [3, 4]]  ← ¡También cambió!

# Las sublistas son compartidas
print(original[0] is copia[0])  # True (mismo objeto)
```

Para copias profundas, usá `copy.deepcopy()`:
```python
import copy
copia_profunda = copy.deepcopy(original)
```
:::

```{code-cell} ipython3
# Ejemplo de copia superficial
original = [1, 2, [3, 4]]
copia = original.copy()

# Modificar elemento simple: OK
copia[0] = 999
print(f"Original: {original}")  # [1, 2, [3, 4]]  ← Sin cambios

# Modificar sublista: PROBLEMA
copia[2].append(5)
print(f"Original: {original}")  # [1, 2, [3, 4, 5]]  ← ¡Cambió!
print(f"Copia: {copia}")        # [999, 2, [3, 4, 5]]
```

### Tabla Resumen - Métodos de list

| Categoría | Método | Descripción | Retorna | Modifica |
|-----------|--------|-------------|---------|----------|
| **Agregar** | `append(x)` | Agrega al final | `None` | ✅ |
| | `extend(iter)` | Agrega múltiples | `None` | ✅ |
| | `insert(i, x)` | Inserta en posición | `None` | ✅ |
| **Eliminar** | `remove(x)` | Elimina primera aparición | `None` | ✅ |
| | `pop(i=-1)` | Elimina y retorna | elemento | ✅ |
| | `clear()` | Elimina todo | `None` | ✅ |
| **Buscar** | `index(x)` | Encuentra índice | int | ❌ |
| | `count(x)` | Cuenta apariciones | int | ❌ |
| **Ordenar** | `sort()` | Ordena en lugar | `None` | ✅ |
| | `reverse()` | Invierte orden | `None` | ✅ |
| **Copiar** | `copy()` | Copia superficial | list | ❌ |

:::{important} Patrón de Modificación
Los métodos que **modifican** la lista retornan `None`.
Los métodos que **no modifican** retornan un nuevo valor.

```python
# ❌ Error común
lista = lista.append(4)  # lista es None ahora!

# ✓ Correcto
lista.append(4)  # lista se modifica
```
:::




---



---

(referencia-dict)=
## Diccionarios (dict) - Mapeos Clave-Valor

Los diccionarios son **mutables** y almacenan pares clave-valor. Desde Python 3.7+, mantienen el orden de inserción.

### Mapa de Métodos de Diccionarios

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#fce4ec','primaryTextColor':'#c2185b','primaryBorderColor':'#d81b60','lineColor':'#f06292','secondaryColor':'#f3e5f5','tertiaryColor':'#fff'}}}%%
graph TB
    DICT[dict - Diccionarios]
    
    DICT --> ACC[Acceso]
    DICT --> MOD[Modificación]
    DICT --> ELIM[Eliminación]
    DICT --> CREA[Creación]
    
    ACC --> A1[get<br/>keys<br/>values<br/>items]
    
    MOD --> M1[update<br/>setdefault]
    
    ELIM --> E1[pop<br/>popitem<br/>clear]
    
    CREA --> C1[copy<br/>fromkeys]
    
    style DICT fill:#c2185b,stroke:#880e4f,color:#fff
    style ACC fill:#f06292,stroke:#d81b60,color:#000
    style MOD fill:#f06292,stroke:#d81b60,color:#000
    style ELIM fill:#f06292,stroke:#d81b60,color:#000
    style CREA fill:#f06292,stroke:#d81b60,color:#000
```

### Métodos de Acceso

#### `dict.get(key, default=None)` → valor

Obtiene el valor asociado a `key`. Si no existe, retorna `default` (sin error).

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 25}

# get() no lanza error si no existe
print(persona.get("nombre"))              # "Ana"
print(persona.get("ciudad"))              # None
print(persona.get("ciudad", "Desconocida"))  # "Desconocida"

# Comparar con acceso directo
print(persona["nombre"])                  # "Ana"
try:
    print(persona["ciudad"])              # KeyError!
except KeyError:
    print("Clave no existe")
```

**Cuándo usar:**
- `dict[key]`: Cuando **sabes** que la clave existe (falla rápido)
- `dict.get(key)`: Cuando **no estás seguro** (evita errores)

```{code-cell} ipython3
# Patrón común: valores por defecto en configuración
config = {"puerto": 8080}

host = config.get("host", "localhost")
puerto = config.get("puerto", 80)
print(f"Servidor: {host}:{puerto}")  # "localhost:8080"
```

#### `dict.keys()` / `dict.values()` / `dict.items()`

Retornan **vistas** dinámicas de claves, valores y pares (clave, valor).

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 25, "ciudad": "Bariloche"}

# keys() - vista de claves
print(persona.keys())  # dict_keys(['nombre', 'edad', 'ciudad'])

# values() - vista de valores
print(persona.values())  # dict_values(['Ana', 25, 'Bariloche'])

# items() - vista de pares (clave, valor)
print(persona.items())  
# dict_items([('nombre', 'Ana'), ('edad', 25), ('ciudad', 'Bariloche')])
```

```{code-cell} ipython3
# Forma más común: iterar con desempaquetado
for clave, valor in persona.items():
    print(f"{clave}: {valor}")

# Operaciones útiles con values()
edades = {"Ana": 25, "Bruno": 30, "Carlos": 20}
print(f"Promedio: {sum(edades.values()) / len(edades)}")  # 25.0
print(f"Mayor: {max(edades.values())}")  # 30
```

:::{tip} Desempaquetado en for
```python
# ✓ Pythonic y eficiente
for clave, valor in diccionario.items():
    print(f"{clave} = {valor}")

# ✗ Menos eficiente
for clave in diccionario.keys():
    valor = diccionario[clave]
    print(f"{clave} = {valor}")
```
:::

### Métodos de Modificación

#### `dict.update(other)` → None

Actualiza el diccionario con pares de `other`. Sobrescribe claves existentes.

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 25}
nuevos = {"edad": 26, "ciudad": "Bariloche"}

persona.update(nuevos)
print(persona)
# {'nombre': 'Ana', 'edad': 26, 'ciudad': 'Bariloche'}

# También con keyword arguments
persona.update(profesion="Ingeniera")
print(persona)
```

#### `dict.setdefault(key, default=None)` → valor

Si `key` existe, retorna su valor. Si no, **inserta** `key=default` y retorna `default`.

```{code-cell} ipython3
persona = {"nombre": "Ana"}

# Clave existente: solo retorna
print(persona.setdefault("nombre", "Desconocido"))  # "Ana"

# Clave nueva: inserta Y retorna
print(persona.setdefault("edad", 18))  # 18
print(persona)  # {'nombre': 'Ana', 'edad': 18}
```

**Caso de uso: agrupar elementos**

```{code-cell} ipython3
estudiantes = [
    ("Ana", "A"),
    ("Bruno", "B"),
    ("Carlos", "A"),
    ("Diana", "C"),
    ("Eduardo", "B")
]

# Agrupar por calificación
por_nota = {}
for nombre, nota in estudiantes:
    por_nota.setdefault(nota, []).append(nombre)

print(por_nota)
# {'A': ['Ana', 'Carlos'], 'B': ['Bruno', 'Eduardo'], 'C': ['Diana']}
```

### Métodos de Eliminación

#### `dict.pop(key, default)` → valor

Elimina `key` y retorna su valor. Si no existe y hay `default`, retorna `default`.

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 25, "ciudad": "Bariloche"}

edad = persona.pop("edad")
print(f"Eliminado: {edad}")  # 25
print(persona)  # {'nombre': 'Ana', 'ciudad': 'Bariloche'}

# Con default
pais = persona.pop("pais", "Argentina")
print(pais)  # "Argentina" (no existía, retorna default)
```

#### `dict.popitem()` → (key, value)

Elimina y retorna el último par insertado (Python 3.7+).

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 25}
item = persona.popitem()
print(item)  # ('edad', 25)
```

#### `dict.clear()` → None

Elimina todos los elementos.

```{code-cell} ipython3
persona.clear()
print(persona)  # {}
```

### Métodos de Copia y Creación

#### `dict.copy()` → dict

Crea una copia superficial.

```{code-cell} ipython3
original = {"a": 1, "b": 2}
copia = original.copy()

copia["c"] = 3
print(original)  # {'a': 1, 'b': 2}
print(copia)     # {'a': 1, 'b': 2, 'c': 3}
```

#### `dict.fromkeys(iterable, value=None)` → dict

Crea nuevo diccionario con claves de `iterable` y valores iguales a `value`.

```{code-cell} ipython3
claves = ["nombre", "edad", "ciudad"]
d = dict.fromkeys(claves, "Desconocido")
print(d)
# {'nombre': 'Desconocido', 'edad': 'Desconocido', 'ciudad': 'Desconocido'}
```

:::{danger} Cuidado con mutables
```python
# ❌ Todas las claves comparten la MISMA lista
d = dict.fromkeys(["a", "b"], [])
d["a"].append(1)
print(d)  # {'a': [1], 'b': [1]}  ← Ambas cambiaron!

# ✓ Usar dict comprehension
d = {k: [] for k in ["a", "b"]}
```
:::

### Tabla Resumen - Métodos de dict

| Categoría | Método | Descripción | Retorna |
|-----------|--------|-------------|---------|
| **Acceso** | `get(key, default)` | Valor o default | valor |
| | `keys()` / `values()` / `items()` | Vistas dinámicas | vista |
| **Modificación** | `update(other)` | Actualizar/agregar | `None` |
| | `setdefault(key, default)` | Obtener o insertar | valor |
| **Eliminación** | `pop(key, default)` | Eliminar y retornar | valor |
| | `popitem()` | Eliminar último | (k, v) |
| | `clear()` | Eliminar todo | `None` |
| **Creación** | `copy()` | Copia superficial | dict |
| | `fromkeys(iter, val)` | Desde claves | dict |

---

(referencia-set)=
## Sets (set) - Conjuntos

Los sets son **mutables**, pero sus elementos deben ser **inmutables** (hashables). No permiten duplicados ni orden.

### Mapa de Métodos de Sets

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#fff3e0','primaryTextColor':'#e65100','primaryBorderColor':'#f57c00','lineColor':'#ff9800','secondaryColor':'#fce4ec','tertiaryColor':'#fff'}}}%%
graph TB
    SET[set - Conjuntos]
    
    SET --> AGR[Agregar]
    SET --> ELIM[Eliminar]
    SET --> OPS[Operaciones]
    SET --> VERIF[Verificación]
    
    AGR --> A1[add<br/>update]
    
    ELIM --> E1[remove<br/>discard<br/>pop<br/>clear]
    
    OPS --> O1[union<br/>intersection]
    OPS --> O2[difference<br/>symmetric_difference]
    
    VERIF --> V1[issubset<br/>issuperset<br/>isdisjoint]
    
    style SET fill:#e65100,stroke:#bf360c,color:#fff
    style AGR fill:#ff9800,stroke:#f57c00,color:#000
    style ELIM fill:#ff9800,stroke:#f57c00,color:#000
    style OPS fill:#ff9800,stroke:#f57c00,color:#000
    style VERIF fill:#ff9800,stroke:#f57c00,color:#000
```

### Métodos de Agregado

#### `set.add(elem)` → None

Agrega un elemento. Si ya existe, no hace nada.

```{code-cell} ipython3
frutas = {"manzana", "banana"}
frutas.add("naranja")
print(frutas)  # {'manzana', 'banana', 'naranja'}

# Duplicado: no hace nada
frutas.add("manzana")
print(frutas)  # Sin cambios
```

#### `set.update(*iterables)` → None

Agrega todos los elementos de uno o más iterables.

```{code-cell} ipython3
s = {1, 2, 3}
s.update([3, 4, 5], {5, 6, 7})
print(s)  # {1, 2, 3, 4, 5, 6, 7}
```

### Métodos de Eliminación

#### `set.remove(elem)` → None

Elimina `elem`. Lanza `KeyError` si no existe.

```{code-cell} ipython3
frutas = {"manzana", "banana", "naranja"}
frutas.remove("banana")
print(frutas)  # {'manzana', 'naranja'}

# Error si no existe
# frutas.remove("pera")  # KeyError!
```

#### `set.discard(elem)` → None

Elimina `elem` si existe. **No lanza error** si no existe.

```{code-cell} ipython3
frutas.discard("banana")   # Elimina
frutas.discard("pera")     # No hace nada (no hay error)
```

:::{tip} remove() vs discard()
- `remove()`: Usa cuando **sabes** que existe
- `discard()`: Usa cuando **no estás seguro**
:::

#### `set.pop()` → elem

Elimina y retorna un elemento **arbitrario**.

```{code-cell} ipython3
s = {1, 2, 3, 4, 5}
elemento = s.pop()
print(f"Eliminado: {elemento}")
print(f"Restantes: {s}")
```

#### `set.clear()` → None

Elimina todos los elementos.

```{code-cell} ipython3
s.clear()
print(s)  # set()
```

### Operaciones de Conjuntos

#### `set.union(*others)` → set | Operador: `|`

Retorna unión (elementos en cualquiera de los conjuntos).

```{code-cell} ipython3
a = {1, 2, 3}
b = {3, 4, 5}

print(a.union(b))  # {1, 2, 3, 4, 5}
print(a | b)       # {1, 2, 3, 4, 5}
```

#### `set.intersection(*others)` → set | Operador: `&`

Retorna intersección (elementos comunes).

```{code-cell} ipython3
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a.intersection(b))  # {3, 4}
print(a & b)              # {3, 4}
```

#### `set.difference(*others)` → set | Operador: `-`

Retorna elementos en `set` pero no en `others`.

```{code-cell} ipython3
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a.difference(b))  # {1, 2}  ← En a pero no en b
print(a - b)            # {1, 2}
```

#### `set.symmetric_difference(other)` → set | Operador: `^`

Retorna elementos en uno u otro, pero **no en ambos**.

```{code-cell} ipython3
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a.symmetric_difference(b))  # {1, 2, 5, 6}
print(a ^ b)                      # {1, 2, 5, 6}
```

### Métodos de Verificación

#### `set.issubset(other)` → bool | Operador: `<=`

Verifica si `set` es subconjunto de `other`.

```{code-cell} ipython3
a = {1, 2}
b = {1, 2, 3, 4}

print(a.issubset(b))  # True
print(a <= b)         # True
```

#### `set.issuperset(other)` → bool | Operador: `>=`

Verifica si `set` es superconjunto de `other`.

```{code-cell} ipython3
print(b.issuperset(a))  # True
print(b >= a)           # True
```

#### `set.isdisjoint(other)` → bool

Verifica si dos sets **no** tienen elementos en común.

```{code-cell} ipython3
a = {1, 2, 3}
b = {4, 5, 6}
c = {3, 4, 5}

print(a.isdisjoint(b))  # True  ← Sin elementos comunes
print(a.isdisjoint(c))  # False ← Comparten el 3
```

### Tabla Resumen - Métodos de set

| Categoría | Método | Operador | Descripción |
|-----------|--------|----------|-------------|
| **Agregar** | `add(elem)` | | Agregar elemento |
| | `update(*iters)` | | Agregar múltiples |
| **Eliminar** | `remove(elem)` | | Eliminar (error si no existe) |
| | `discard(elem)` | | Eliminar (sin error) |
| | `pop()` | | Eliminar arbitrario |
| | `clear()` | | Eliminar todo |
| **Unión** | `union(*others)` | `\|` | A ∪ B |
| **Intersección** | `intersection(*others)` | `&` | A ∩ B |
| **Diferencia** | `difference(*others)` | `-` | A - B |
| **Diff. Simétrica** | `symmetric_difference(other)` | `^` | A △ B |
| **Subconjunto** | `issubset(other)` | `<=` | A ⊆ B |
| **Superconjunto** | `issuperset(other)` | `>=` | A ⊇ B |
| **Disjuntos** | `isdisjoint(other)` | | A ∩ B = ∅ |

---

(referencia-tuple)=
## Tuplas (tuple) - Secuencias Inmutables

Las tuplas son **inmutables**. Solo tienen 2 métodos propios.

### Métodos de Tupla

#### `tuple.count(value)` → int

Cuenta cuántas veces aparece `value`.

```{code-cell} ipython3
numeros = (1, 2, 2, 3, 2, 4)
print(numeros.count(2))  # 3
print(numeros.count(5))  # 0
```

#### `tuple.index(value, start=0, stop=len)` → int

Retorna índice de la primera aparición.

```{code-cell} ipython3
numeros = (10, 20, 30, 20, 40)
print(numeros.index(20))       # 1
print(numeros.index(20, 2))    # 3  ← Desde índice 2
```

### Operaciones con Tuplas

```{code-cell} ipython3
# Concatenación
a = (1, 2, 3)
b = (4, 5, 6)
print(a + b)  # (1, 2, 3, 4, 5, 6)

# Repetición
print(a * 3)  # (1, 2, 3, 1, 2, 3, 1, 2, 3)

# Slicing
print(a[1:])  # (2, 3)

# Membresía
print(2 in a)  # True

# Longitud, máximo, mínimo
print(len(a), max(a), min(a))  # 3 3 1
```

### Desempaquetado de Tuplas

```{code-cell} ipython3
# Desempaquetado básico
coordenadas = (10, 20)
x, y = coordenadas
print(f"x={x}, y={y}")

# Desempaquetado con *
numeros = (1, 2, 3, 4, 5)
primero, *resto, ultimo = numeros
print(f"Primero: {primero}")  # 1
print(f"Resto: {resto}")      # [2, 3, 4]
print(f"Último: {ultimo}")    # 5

# Intercambio de variables
a, b = 5, 10
a, b = b, a  # Swap
print(f"a={a}, b={b}")  # a=10, b=5
```

### namedtuple - Tuplas con Nombres

```{code-cell} ipython3
from collections import namedtuple

# Definir estructura
Punto = namedtuple("Punto", ["x", "y"])
Persona = namedtuple("Persona", "nombre edad ciudad")

# Crear instancias
p = Punto(10, 20)
ana = Persona("Ana", 25, "Bariloche")

# Acceder por nombre (más legible)
print(p.x, p.y)              # 10 20
print(ana.nombre, ana.edad)  # Ana 25

# También por índice
print(p[0], p[1])  # 10 20
```

### Tabla Resumen - Métodos de tuple

| Método | Descripción |
|--------|-------------|
| `count(value)` | Cuenta apariciones |
| `index(value)` | Busca índice |

**Operaciones:** `+`, `*`, `[]`, `in`, `len()`, `max()`, `min()`

## Comparativa de Tipos - Guía de Decisión

### Mutabilidad e Inmutabilidad

| Tipo | Mutable | Hashable | Puede ser clave de dict | Puede estar en set |
|------|---------|----------|-------------------------|-------------------|
| **str** | ❌ | ✅ | ✅ | ✅ |
| **int, float** | ❌ | ✅ | ✅ | ✅ |
| **list** | ✅ | ❌ | ❌ | ❌ |
| **tuple** | ❌ | ✅* | ✅* | ✅* |
| **dict** | ✅ | ❌ | ❌ | ❌ |
| **set** | ✅ | ❌ | ❌ | ❌ |
| **frozenset** | ❌ | ✅ | ✅ | ✅ |

*Tupla es hashable solo si todos sus elementos son hashables.

### Cuándo Usar Cada Tipo

#### Usa `str` cuando:
✅ Trabajás con texto  
✅ Necesitás inmutabilidad  
✅ Vas a usar como clave de diccionario  
✅ Procesás datos de entrada/salida

```{code-cell} ipython3
# Ejemplos de uso
nombre = "Ana García"
email = "ana@ejemplo.com"
mensaje = f"Hola {nombre}, tu email es {email}"
```

#### Usa `list` cuando:
✅ Necesitás secuencia ordenada  
✅ Vas a modificar elementos  
✅ El orden importa  
✅ Pueden haber duplicados

```{code-cell} ipython3
# Ejemplos de uso
tareas = ["lavar", "cocinar", "limpiar"]
numeros = [1, 2, 2, 3, 3, 3]  # Duplicados OK
tareas.append("estudiar")  # Mutable
```

#### Usa `dict` cuando:
✅ Necesitás mapeo clave-valor  
✅ Acceso rápido por clave (O(1))  
✅ Datos estructurados  
✅ Configuraciones o metadatos

```{code-cell} ipython3
# Ejemplos de uso
persona = {"nombre": "Ana", "edad": 25, "ciudad": "Bariloche"}
config = {"host": "localhost", "puerto": 8080}
contador = {"manzanas": 5, "bananas": 3}
```

#### Usa `set` cuando:
✅ Necesitás elementos únicos  
✅ Operaciones de conjuntos (unión, intersección)  
✅ El orden no importa  
✅ Verificar pertenencia rápida (O(1))

```{code-cell} ipython3
# Ejemplos de uso
tags = {"python", "programacion", "tutorial"}
visitados = {1, 5, 10, 15}

# Eliminar duplicados
numeros = [1, 2, 2, 3, 3, 3]
unicos = list(set(numeros))  # [1, 2, 3]
```

#### Usa `tuple` cuando:
✅ Secuencia inmutable  
✅ Retornar múltiples valores  
✅ Usarla como clave de diccionario  
✅ Datos que no deben cambiar

```{code-cell} ipython3
# Ejemplos de uso
coordenadas = (10, 20)
fecha = (2024, 1, 15)

# Retornar múltiples valores
def obtener_datos():
    return "Ana", 25, "Bariloche"

nombre, edad, ciudad = obtener_datos()

# Como clave de dict
ubicaciones = {
    (0, 0): "origen",
    (1, 0): "este",
    (0, 1): "norte"
}
```

### Conversión entre Tipos

```{code-cell} ipython3
# A lista
list("abc")          # ['a', 'b', 'c']
list((1, 2, 3))      # [1, 2, 3]
list({1, 2, 3})      # [1, 2, 3] (orden arbitrario)

# A tupla
tuple([1, 2, 3])     # (1, 2, 3)
tuple("abc")         # ('a', 'b', 'c')

# A set (elimina duplicados)
set([1, 2, 2, 3])    # {1, 2, 3}
set("hello")         # {'h', 'e', 'l', 'o'}

# A string
"".join(['a', 'b'])  # 'ab'
str([1, 2, 3])       # '[1, 2, 3]'

# A dict
dict([('a', 1), ('b', 2)])  # {'a': 1, 'b': 2}
dict(zip(['a', 'b'], [1, 2]))  # {'a': 1, 'b': 2}
```

### Operaciones Comunes

#### Pertenencia (todos los tipos)

```{code-cell} ipython3
# in / not in
elemento in coleccion    # True/False
elemento not in coleccion

# Ejemplos
print(2 in [1, 2, 3])           # True
print("Ana" in {"nombre": "Ana"})  # True (busca en claves)
print("x" in "texto")           # True
```

#### Longitud (todos los tipos)

```{code-cell} ipython3
len(coleccion)  # Número de elementos

print(len("Python"))        # 6
print(len([1, 2, 3]))       # 3
print(len({"a": 1, "b": 2}))  # 2
print(len({1, 2, 3}))       # 3
```

#### Iteración (todos los tipos)

```{code-cell} ipython3
# str, list, tuple, set
for item in coleccion:
    print(item)

# dict (por defecto itera sobre claves)
for clave in diccionario:
    print(clave)

# dict - iterar sobre valores
for valor in diccionario.values():
    print(valor)

# dict - iterar sobre pares
for clave, valor in diccionario.items():
    print(f"{clave}: {valor}")
```

### Funciones Built-in Útiles

```{code-cell} ipython3
# Funciones de agregación (numéricas)
numeros = [1, 2, 3, 4, 5]
print(sum(numeros))    # 15
print(max(numeros))    # 5
print(min(numeros))    # 1
print(len(numeros))    # 5

# Funciones de transformación
print(sorted([3, 1, 4]))        # [1, 3, 4] (crea nueva lista)
print(list(reversed([1, 2, 3]))) # [3, 2, 1]

# map() - aplicar función
cuadrados = list(map(lambda x: x**2, [1, 2, 3]))  # [1, 4, 9]

# filter() - filtrar elementos
pares = list(filter(lambda x: x % 2 == 0, [1, 2, 3, 4]))  # [2, 4]

# zip() - combinar iterables
nombres = ["Ana", "Bruno"]
edades = [25, 30]
personas = list(zip(nombres, edades))  # [('Ana', 25), ('Bruno', 30)]

# enumerate() - índice + elemento
for i, valor in enumerate(["a", "b", "c"]):
    print(f"{i}: {valor}")
```

### Cheat Sheet de Métodos Más Usados

#### `str`
```python
texto.lower() / .upper()        # Cambiar capitalización
texto.strip()                   # Eliminar espacios
texto.split()                   # Dividir en lista
",".join(lista)                 # Unir lista en string
texto.replace(viejo, nuevo)     # Reemplazar
texto.find(sub)                 # Buscar
f"Hola {nombre}"                # f-strings (formato)
```

#### `list`
```python
lista.append(x)                 # Agregar al final
lista.extend(otra)              # Agregar múltiples
lista.insert(i, x)              # Insertar en posición
lista.remove(x)                 # Eliminar primera aparición
lista.pop()                     # Eliminar y retornar último
lista.sort()                    # Ordenar in-place
lista.reverse()                 # Invertir in-place
```

#### `dict`
```python
d.get(key, default)             # Obtener valor seguro
d.keys() / .values() / .items() # Vistas
d.update(otro)                  # Actualizar
d.pop(key)                      # Eliminar y retornar
d.setdefault(key, default)      # Obtener o crear
```

#### `set`
```python
s.add(x)                        # Agregar elemento
s.remove(x) / .discard(x)       # Eliminar
s1 | s2                         # Unión
s1 & s2                         # Intersección
s1 - s2                         # Diferencia
s1 ^ s2                         # Diferencia simétrica
```

#### `tuple`
```python
t.count(x)                      # Contar apariciones
t.index(x)                      # Buscar índice
a, b, c = t                     # Desempaquetado
```

---

### Referencias

- **Documentación oficial:** [Python Built-in Types](https://docs.python.org/3/library/stdtypes.html)
- **Tutorial:** [Python Data Structures](https://docs.python.org/3/tutorial/datastructures.html)
- **PEP 8:** [Style Guide](https://pep8.org/)
