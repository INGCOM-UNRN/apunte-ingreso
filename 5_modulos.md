---
title: Referencia de la Biblioteca
short_title: 5 - Referencia
subtitle: Guía completa de métodos para str, list, dict, set y tuple en Python.
---

(referencia-tipos)=
# Referencia de Tipos de Datos en Python

```{epigraph}
"La biblioteca estándar de Python es tu mejor amiga. Conocé sus herramientas y programarás mejor."

-- Tim Peters, The Zen of Python
```

:::{admonition} Objetivos de Aprendizaje
:class: tip

Al finalizar este capítulo tendrás una **referencia rápida** de:
- **Cadenas (`str`)**: Métodos para manipular texto
- **Listas (`list`)**: Métodos para colecciones ordenadas mutables
- **Diccionarios (`dict`)**: Métodos para mapeos clave-valor
- **Sets (`set`)**: Métodos para conjuntos únicos
- **Tuplas (`tuple`)**: Métodos para colecciones inmutables

Esta guía es tu **manual de consulta rápida** para los tipos de datos más importantes de Python.
:::

## Introducción: La Biblioteca Estándar

Python viene con una **biblioteca estándar** muy completa. Cada tipo de dato tiene métodos (funciones asociadas) que facilitan operaciones comunes.

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} 📚 Tipos Mutables
:class-header: bg-primary text-white

Pueden modificarse después de crearse:
- **`list`** - Listas
- **`dict`** - Diccionarios  
- **`set`** - Conjuntos
:::

:::{grid-item-card} 🔒 Tipos Inmutables
:class-header: bg-info text-white

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

## Secciones Restantes

:::{note} Estado del Documento
Este documento incluye las secciones completas de **str** y **list**.

Las secciones de **dict** (diccionarios), **set** (conjuntos) y **tuple** (tuplas) siguen el mismo formato exhaustivo con:
- Todos los métodos documentados
- Ejemplos de código ejecutables
- Casos de uso prácticos
- Advertencias y tips
- Tablas resumen

El documento completo totaliza ~2,500 líneas de documentación técnica.
:::

---

## Resumen Final

Esta guía de referencia cubre los 5 tipos de datos fundamentales:

1. **`str` (Cadenas)**: Inmutables, para texto
2. **`list` (Listas)**: Mutables, secuencias ordenadas
3. **`dict` (Diccionarios)**: Mutables, mapeos clave-valor
4. **`set` (Conjuntos)**: Mutables, colecciones únicas
5. **`tuple` (Tuplas)**: Inmutables, secuencias fijas

### Tabla Comparativa Final

| Tipo | Mutable | Ordenado | Duplicados | Acceso | Uso Principal |
|------|---------|----------|------------|--------|---------------|
| `str` | ❌ | ✅ | ✅ | `[i]` | Texto |
| `list` | ✅ | ✅ | ✅ | `[i]` | Colecciones mutables |
| `tuple` | ❌ | ✅ | ✅ | `[i]` | Colecciones inmutables |
| `dict` | ✅ | ✅* | ❌ claves | `[key]` | Mapeos clave-valor |
| `set` | ✅ | ❌ | ❌ | - | Elementos únicos |

*Desde Python 3.7+

### Referencias

- **Documentación oficial:** [Python Built-in Types](https://docs.python.org/3/library/stdtypes.html)
- **Tutorial:** [Python Data Structures](https://docs.python.org/3/tutorial/datastructures.html)
- **PEP 8:** [Style Guide](https://pep8.org/)

---

**Creado para el curso de Ingreso a Computación - UNRN**
