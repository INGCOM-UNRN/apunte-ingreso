--- 
title: Referencia de Tipos de Datos en Python
short_title: C - Referencia Tipos
subtitle: Guía completa de métodos para str, list, dict, set y tuple en Python.
---

(referencia-tipos)= 
# Referencia de Tipos de Datos en Python

```{epigraph}
"La biblioteca estándar de Python es tu mejor amiga. Conocé sus herramientas y programarás mejor."

-- Tim Peters, The Zen of Python
```

Esta guía de referencia cubre los 5 tipos de datos fundamentales de Python, profundizando en sus métodos y casos de uso:

1. **`str` (Cadenas)**: Inmutables, para texto.
2. **`list` (Listas)**: Mutables, secuencias ordenadas. *(Ver {ref}`3_estructuras` para teoría completa)*
3. **`dict` (Diccionarios)**: Mutables, mapeos clave-valor. *(Teoría incluida en este capítulo)*
4. **`set` (Conjuntos)**: Mutables, colecciones únicas. *(Ver {ref}`3_estructuras` para teoría completa)*
5. **`tuple` (Tuplas)**: Inmutables, secuencias fijas. *(Teoría incluida en este capítulo)*

:::{note} Organización del Material
- **Listas y Sets** están cubiertos en profundidad en el capítulo {ref}`estructuras-datos`
- **Tuplas y Diccionarios** están explicados completamente en este capítulo
- Todos los tipos incluyen referencia completa de métodos y ejemplos prácticos
:::

Esta guía es tu manual de consulta rápida. Para entender cómo funcionan las {term}`funciones <Función>` y métodos que veremos aquí, asegurate de haber leído el capítulo {ref}`4 - Funciones <funciones>`.

## Introducción: La Biblioteca Estándar

Python viene con una **biblioteca estándar** muy completa. Cada tipo de dato tiene métodos ({term}`funciones <Función>` asociadas al objeto) que facilitan operaciones comunes.

::::{grid} 1 1 2 2

:::{grid-item-card} 📚 Tipos Mutables

Pueden modificarse después de crearse:
- **`list`** - Listas.
- **`dict`** - Diccionarios.
- **`set`** - Conjuntos.
:::

:::{grid-item-card} 🔒 Tipos Inmutables

No pueden modificarse una vez creados:
- **`str`** - Cadenas.
- **`tuple`** - Tuplas.
- **`frozenset`** - Conjuntos inmutables.
:::

::::

:::{important} Convención de Nomenclatura
Los métodos que **modifican** el objeto (mutables) generalmente no retornan nada (`None`).
Los métodos que **no modifican** el objeto (inmutables) retornan un **nuevo objeto**.
:::

---

(referencia-str)= 
## Cadenas (str) - Manipulación de Texto

Las cadenas son **inmutables**. Todos los métodos retornan **nuevas cadenas** sin modificar la original.

### Mapa de Métodos de Cadenas

Este diagrama organiza los métodos de strings en categorías funcionales, facilitando su comprensión y búsqueda. Los métodos están agrupados según su propósito principal: búsqueda de subcadenas, verificación de contenido, transformación de texto, división y unión de cadenas, y formateo. Esta organización te ayuda a elegir rápidamente el método apropiado para cada tarea.

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
- Verificar si un substring existe.
- Encontrar posición de un patrón.
- Buscar en segmentos específicos.

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
- Usá **`find()`** cuando no estés seguro si el substring existe → retorna `-1`.
- Usá **`index()`** cuando sepas que existe → más expresivo, lanza error si falla.
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
- Validar formatos de archivo.
- Filtrar elementos por prefijo.
- Parsear comandos.

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

| Método | Retorna True si… | Ejemplo True | Ejemplo False |
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
    """Valida que el código sea alfanumérico de 6 caracteres."""
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
- `capitalize()`: Solo la **primera letra** de la cadena en mayúscula.
- `title()`: Primera letra de **cada palabra** en mayúscula.

#### `str.strip()` / `str.lstrip()` / `str.rstrip()`

Elimina caracteres del principio y/o final.

```{code-cell} ipython3
texto = "   hola mundo   "
print(f'\' {texto.strip()}\'' )     # 'hola mundo'
print(f'\' {texto.lstrip()}\'' )    # 'hola mundo   '
print(f'\' {texto.rstrip()}\'' )    # '   hola mundo'

# Eliminar caracteres específicos
url = "https://www.ejemplo.com/"
print(url.strip("https://"))    # "www.ejemplo.com/"
print(url.rstrip("/"))          # "https://www.ejemplo.com"

# Limpiar entrada de usuario
entrada = "  Ana  \n"
print(f'\' {entrada.strip()}\'' )   # 'Ana'
```

**Parámetro `chars`:**
- Si es `None` (default): elimina espacios, tabs, newlines.
- Si se especifica: elimina cualquier combinación de esos caracteres.

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
- Si es `None`: divide por **cualquier** espacio en blanco (espacios, tabs, newlines) y elimina vacíos.
- Si se especifica: divide **exactamente** por ese separador.

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

La forma **más moderna y recomendada** de formatear cadenas. Se explica en detalle en el apunte de f-strings.

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

Este diagrama muestra los métodos de listas organizados por su función principal. A diferencia de los strings, las listas son mutables, por lo que muchos métodos modifican la lista directamente en lugar de retornar una nueva. Entender esta diferencia es crucial para evitar errores comunes. Los métodos están agrupados en: agregar elementos, eliminar elementos, buscar valores, ordenar, y copiar.

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
- `append(x)`: Cuando querés agregar un **solo** elemento (incluso si es una lista).
- `extend(iter)`: Cuando querés agregar **múltiples** elementos.
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
- `list.sort()`: Cuando querés modificar la lista original.
- `sorted()`: Cuando necesitás mantener la original + crear una nueva ordenada.
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

---

## Diccionarios

Un **diccionario** es una {term}`colección` de {term}`pares clave-valor<Par key-value>`. Cada clave es única y se usa para acceder a su valor asociado. Es como un diccionario real: buscás una palabra ({term}`key`) y encontrás su definición ({term}`value`).

### Crear Diccionarios

Los diccionarios se crean usando llaves `{}` con pares clave-valor separados por dos puntos. A diferencia de las listas que usan índices numéricos, los diccionarios usan claves personalizadas (generalmente strings) para acceder a los valores. Esto los hace ideales para datos estructurados donde cada campo tiene un nombre significativo.

```{code-cell} ipython3
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
Las claves deben ser {term}`inmutables<Inmutable>` como strings, números, tuplas. Las listas u otros diccionarios no pueden ser llave.

```{code-cell} ipython3
# ✓ Válido
d = {"nombre": "Ana", 1: "uno", (1,2): "tupla"}

# ❌ Inválido
# d = {[1,2]: "lista"}  # TypeError: unhashable type: 'list'
```
:::

### Acceso a Valores

Para acceder a valores en un diccionario, usás la clave entre corchetes o el método `get()`. El método `get()` es más seguro porque no lanza un error si la clave no existe; en su lugar, retorna `None` o un valor por defecto que especifiques. Esto es especialmente útil cuando trabajás con datos que pueden estar incompletos.

```{code-cell} ipython3
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

:::{tip} Usar `get()` en lugar de `[]`
Es preferible usar `get()` cuando no estás seguro si la {term}`clave <Key>` existe:

```python
# ❌ Puede dar error
# valor = diccionario[clave]  # KeyError si no existe

# ✓ Más seguro
valor = diccionario.get(clave, valor_por_defecto)
```
:::

### Modificar Diccionarios

Los diccionarios son mutables, lo que significa que podés cambiar sus valores, agregar nuevos pares clave-valor, o eliminar entradas existentes. A diferencia de las listas que se modifican por índice, los diccionarios se modifican por clave. Esto los hace extremadamente flexibles para representar datos que cambian con el tiempo.

```{code-cell} ipython3
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

Los diccionarios en Python tienen métodos poderosos para acceder, modificar y consultar datos de forma segura y eficiente.

```{code-cell} ipython3
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

Antes de acceder a un valor en un diccionario, es común verificar si la clave existe para evitar errores. Python proporciona el operador `in` para esta tarea, que retorna `True` si la clave existe y `False` en caso contrario. Esto es más eficiente y legible que intentar acceder y capturar una excepción.

```{code-cell} ipython3
estudiante = {"nombre": "Ana", "edad": 20}

# in - verifica si existe una clave
if "nombre" in estudiante:
    print("Tiene nombre")

if "nota" not in estudiante:
    print("No tiene nota")
```

### Iterar sobre Diccionarios

Los diccionarios permiten múltiples formas de iteración dependiendo de lo que necesitás: solo claves, solo valores, o ambos. Python 3.7+ mantiene el orden de inserción, lo que hace que la iteración sea predecible. La forma más común y recomendada es usar `.items()` para acceder a pares clave-valor simultáneamente.

```{code-cell} ipython3
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

Los diccionarios pueden contener otros diccionarios como valores, creando estructuras de datos complejas y jerárquicas. Esto es útil para representar datos relacionados de forma organizada, como información de múltiples estudiantes, configuraciones de aplicaciones, o respuestas de APIs. El acceso a datos anidados se hace encadenando corchetes.

```{code-cell} ipython3
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

Un caso de uso común de diccionarios es contar frecuencias de elementos. En este ejemplo, usamos un diccionario para contar cuántas veces aparece cada palabra en un texto. El patrón es simple: si la palabra ya existe como clave, incrementamos su valor; si no, la agregamos con valor 1.

```{code-cell} ipython3
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
| `get(clave, default)` | Obtiene valor (o `default`) | `d.get("edad", 0)` |
| `keys()` | Retorna claves | `d.keys()` |
| `values()` | Retorna valores | `d.values()` |
| `items()` | Retorna pares (clave, valor) | `d.items()` |
| `pop(clave)` | Elimina y retorna valor | `d.pop("edad")` |
| `update(otro)` | Actualiza con otro `dict` | `d.update({"x": 1})` |
| `clear()` | Vacía el diccionario | `d.clear()` |


---

## Sets (set) - Conjuntos

Los sets son **mutables**, pero sus elementos deben ser **inmutables** (hashables). No permiten duplicados ni orden.

### Mapa de Métodos de Sets

Este diagrama organiza los métodos de sets según su funcionalidad. Los sets son colecciones no ordenadas de elementos únicos, ideales para operaciones matemáticas de conjuntos y eliminación de duplicados. Los métodos se clasifican en: agregar elementos, eliminar elementos, operaciones de conjuntos (unión, intersección, diferencia), y verificaciones de relaciones entre conjuntos (subconjunto, superconjunto).

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
- `remove()`: Usa cuando **sabes** que existe.
- `discard()`: Usa cuando **no estás seguro**.
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
| **Unión** | `union(*others)` | `|` | A ∪ B |
| **Intersección** | `intersection(*others)` | `&` | A ∩ B |
| **Diferencia** | `difference(*others)` | `-` | A - B |
| **Diff. Simétrica** | `symmetric_difference(other)` | `^` | A △ B |
| **Subconjunto** | `issubset(other)` | `<=` | A ⊆ B |
| **Superconjunto** | `issuperset(other)` | `>=` | A ⊇ B |
| **Disjuntos** | `isdisjoint(other)` | | A ∩ B = ∅ |

---

(referencia-tuple)= 

---

## Tuplas: La Prima Inmutable de las Listas 

### ¿Qué es una Tupla?

Una **tupla** es esencialmente una lista que no puede ser modificada. Una vez creada, sus elementos son fijos. Se utilizan para agrupar datos que conceptualmente pertenecen juntos y no deberían cambiar, como coordenadas geográficas, fechas, o registros de base de datos.

::::{tip} Analogía: Lista vs Tupla

**Lista = Playlist de Spotify:**
- Podés agregar canciones.
- Podés eliminar canciones.
- Podés cambiar el orden.
- **Mutable** → Cambia.

**Tupla = DVD grabado:**
- Las canciones están grabadas.
- NO podés agregar canciones.
- NO podés cambiar nada.
- **Inmutable** → No cambia.

```python
# Lista - puedo cambiar
playlist = ["Canción 1", "Canción 2"]
playlist[0] = "Otra canción"  # ✓ Funciona

# Tupla - NO puedo cambiar
dvd = ("Canción 1", "Canción 2")
dvd[0] = "Otra canción"  # ✗ ERROR
```
::::

---

### Comparación Visual: Lista vs Tupla

| Característica | Lista `[]` | Tupla `()` |
|----------------|------------|------------|
| **Sintaxis**| Corchetes `[]` | Paréntesis `()` |
| **Mutable**| ✅ Sí | ❌ No |
| **Velocidad**| Más lenta | Más rápida |
| **Uso de memoria**| Más | Menos |
| **Cuándo usar**| Datos que cambian | Datos constantes |
| **Métodos**| Muchos (append, etc.) | Solo 2 (count, index) |
| **Como clave de dict**| ❌ No | ✅ Sí |

--- 

### Crear Tuplas: 4 Formas

Python ofrece múltiples formas de crear tuplas, cada una con su propósito. Podés usar paréntesis explícitos, aprovechar el empaquetado automático de Python, o incluso crear tuplas de un solo elemento (con cuidado especial en la sintaxis). La flexibilidad de Python permite elegir la sintaxis más clara para cada situación.

```{code-cell} ipython3
# 1️⃣ Con paréntesis (forma común)
coordenadas = (10, 20)
colores = ("🔴 rojo", "🟢 verde", "🔵 azul")
print("Coordenadas:", coordenadas)
print("Colores:", colores)

# 2️⃣ Sin paréntesis (tuple packing)
punto = 5, 10, 15  # Python entiende que es tupla
print("Punto:", punto)

# 3️⃣ Tupla de un elemento (requiere coma final)
solo_uno = (5,)   # ✓ Esto ES una tupla
no_tupla = (5)    # ✗ Esto es un int (paréntesis de agrupación)
print(f"solo_uno es tupla: {type(solo_uno)}")
print(f"no_tupla es int: {type(no_tupla)}")

# 4️⃣ Tupla vacía
vacia = ()
tambien_vacia = tuple()
print(f"Tupla vacía: {vacia}, longitud: {len(vacia)}")
```

:::{danger} 🚨 Error Común: Tupla de 1 Elemento

Es fácil confundir un paréntesis de agrupación matemática `(5)` con una tupla. La coma es lo que define a la tupla, no el paréntesis.

```{code-cell} ipython3
# ❌ INCORRECTO - Es un entero, no tupla
numero = (42)
print(f"Tipo: {type(numero)}, valor: {numero}")  # <class 'int'>

# ✓ CORRECTO - La coma lo hace tupla
tupla = (42,)  # ← Nota la coma
print(f"Tipo: {type(tupla)}, valor: {tupla}")    # <class 'tuple'>
```

**Regla:** Para tupla de 1 elemento, **siempre ponés la coma**: `(elemento,)`
:::

---

### Crear Tuplas con `tuple()`

La función `tuple()` es útil cuando necesitás convertir otros tipos de iterables (listas, strings, ranges) en tuplas. Esto es común cuando una función requiere específicamente una tupla, o cuando querés “congelar” una lista para evitar modificaciones accidentales. La conversión es directa: cada elemento del iterable se convierte en un elemento de la tupla.

```{code-cell} ipython3
# Convertir lista a tupla
lista = [1, 2, 3, 4, 5]
tupla = tuple(lista)
print(f"Lista: {lista}")
print(f"Tupla: {tupla}")

# Convertir string a tupla (cada caracter es un elemento)
texto = "Python"
tupla_letras = tuple(texto)
print(f"Tupla de letras: {tupla_letras}")

# Convertir range a tupla
tupla_nums = tuple(range(5))
print(f"Tupla de 0 a 4: {tupla_nums}")
```

---

### Acceso a Elementos: Igual que Listas

Las tuplas se comportan exactamente como las listas en cuanto al acceso de elementos: usan índices que empiezan en 0, soportan índices negativos, y permiten slicing. La única diferencia es que no podés modificar los elementos. Todas las operaciones de lectura funcionan igual.

```{code-cell} ipython3
punto_3d = (10, 20, 30)
print("Tupla:", punto_3d)

# Acceso por índice (igual que listas)
print(f"Primer elemento [0]: {punto_3d[0]}")    # 10
print(f"Segundo [1]: {punto_3d[1]}")            # 20
print(f"Último [-1]: {punto_3d[-1]}")           # 30

# Slicing (igual que listas)
numeros = (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
print(f"[2:5]: {numeros[2:5]}")       # (2, 3, 4)
print(f"[:3]: {numeros[:3]}")         # (0, 1, 2)
print(f"[::2]: {numeros[::2]}")       # (0, 2, 4, 6, 8)
print(f"[::-1]: {numeros[::-1]}")     # Invertida

# Iterar (igual que listas)
colores = ("🔴", "🟢", "🔵")
for color in colores:
    print(color)
```

:::{tip} Operaciones de Lectura
Todas las operaciones de **lectura** de listas funcionan igual en tuplas:
- ✅ Acceso por índice: `tupla[i]`
- ✅ Slicing: `tupla[inicio:fin]`
- ✅ Iteración: `for x in tupla`
- ✅ Búsqueda: `x in tupla`
- ✅ Longitud: `len(tupla)`

Lo que **NO funciona** son operaciones de **escritura**:
- ❌ Modificar: `tupla[i] = x`
- ❌ Agregar: `tupla.append(x)`
- ❌ Eliminar: `tupla.remove(x)`
:::

---

### Inmutabilidad: El Poder de “No Cambiar” 

La inmutabilidad de las tuplas es su característica definitoria y la fuente de muchas de sus ventajas.

::::{tip} Analogía: Tatuaje vs Sticker

**Lista = Sticker:**
- Podés pegar otro encima.
- Podés sacarlo.
- Podés modificarlo.
- **Mutable**.

**Tupla = Tatuaje:**
- Una vez hecho, es permanente.
- No podés modificarlo.
- Tenés que vivir con él (o crear uno nuevo).
- **Inmutable**.
::::

```{code-cell} ipython3
# Lista - MUTABLE
lista = [1, 2, 3]
print("Lista original:", lista)
lista[0] = 999  # ✓ Funciona
print("Lista modificada:", lista)

print("\n" + "="*50 + "\n")

# Tupla - INMUTABLE
tupla = (1, 2, 3)
print("Tupla original:", tupla)

try:
    tupla[0] = 999  # ✗ Error
except TypeError as e:
    print(f"❌ ERROR: {e}")
    print("✓ Las tuplas NO se pueden modificar")
```

--- 

#### ¿Qué NO Podés Hacer con Tuplas?

Debido a su inmutabilidad, muchas operaciones que funcionan en listas simplemente no existen o fallan en tuplas.

```{code-cell} ipython3
mi_tupla = (10, 20, 30)

# ❌ No podés modificar elementos
try:
    mi_tupla[0] = 99
except TypeError:
    print("❌ No se puede modificar elementos")

# ❌ No podés agregar elementos
try:
    mi_tupla.append(40)
except AttributeError:
    print("❌ No existe método append()")

# ❌ No podés eliminar elementos
try:
    mi_tupla.remove(20)
except AttributeError:
    print("❌ No existe método remove()")

# ❌ No podés ordenar in-place
try:
    mi_tupla.sort()
except AttributeError:
    print("❌ No existe método sort()")
```

--- 

#### ¿Por qué Usar Tuplas? 5 Razones

Si las tuplas no se pueden modificar, ¿para qué usarlas? La inmutabilidad trae consigo ventajas importantes:

:::::{grid} 1 1 2 2

::::{grid-item-card} 1️⃣ Datos Constantes
**Cuando los datos NO deben cambiar:**

```python
# Coordenadas GPS
ubicacion = (-34.6037, -58.3816)

# Color RGB
rojo = (255, 0, 0)

# Dimensiones de pantalla
resolucion = (1920, 1080)

# Días de la semana (no cambian)
dias = ("Lun", "Mar", "Mié", "Jue", "Vie", "Sáb", "Dom")
```

**Ventaja:** Evitás modificaciones accidentales.
::::

::::{grid-item-card} 2️⃣ Mejor Rendimiento
**Las tuplas son más rápidas:**

```python
# Tupla - más rápida de crear
tupla = (1, 2, 3, 4, 5)

# Lista - más lenta de crear
lista = [1, 2, 3, 4, 5]
```

**Ventaja:**
- Menos memoria.
- Más rápidas de crear.
- Acceso más eficiente.
::::

::::{grid-item-card} 3️⃣ Claves de Diccionarios
**Solo tuplas pueden ser claves:**

```python
# ✓ Tupla como clave
cache = {}
coordenada = (10, 20)
cache[coordenada] = "Tesoro"

# ✗ Lista NO puede
# punto = [10, 20]
# cache[punto] = "Tesoro"  # ERROR
```

**Ventaja:** Puede ser clave (hashable).
::::

::::{grid-item-card} 4️⃣ Retornar Múltiples Valores
**Funciones retornan tuplas:**

```python
def obtener_coordenadas():
    return (10, 20, 30)  # Tupla

x, y, z = obtener_coordenadas()
```

**Ventaja:** Sintaxis clara para múltiples valores.
::::

:::::

::::{grid-item-card} 5️⃣ Protección de Datos
**Pasar datos sin riesgo de modificación:**

```python
def procesar_datos(tupla_datos):
    # tupla_datos no puede ser modificada
    # dentro de la función
    pass

configuracion = (800, 600, True)
procesar_datos(configuracion)
# configuracion no fue modificada
```

**Ventaja:** Seguridad en el código.
::::

:::::

---

### Métodos de Tuplas: Solo 2

Las tuplas tienen **solo 2 métodos** (vs 11 de las listas): `count` y `index`. Son métodos de solo lectura.

```{code-cell} ipython3
numeros = (1, 3, 5, 3, 7, 3)

# 1️⃣ count() - cuenta ocurrencias
cantidad = numeros.count(3)
print(f"El 3 aparece {cantidad} veces")

# 2️⃣ index() - encuentra posición de primera ocurrencia
posicion = numeros.index(5)
print(f"El 5 está en posición {posicion}")

# También funciona con inicio y fin
segunda_pos = numeros.index(3, 2)  # Busca desde posición 2
print(f"Segundo 3 está en posición {segunda_pos}")
```

---

### Desempaquetado (Unpacking): El Super Poder de las Tuplas 🎁

El {term}`desempaquetado` (unpacking) es una característica poderosa que permite extraer los elementos de una tupla (o cualquier iterable) en variables individuales de forma concisa.

::::{tip} Analogía: Desempacar una Caja

Imaginate que recibís una caja con 3 regalos:

```python
caja = (🎁, 🎁, 🎁)
```

**Desempaquetar** es sacar cada regalo y ponerlo en su propio lugar:

```python
regalo1, regalo2, regalo3 = caja
# Ahora tenés 3 variables separadas
```
::::

---

#### Desempaquetado Básico

La forma más común es asignar los elementos de la tupla a variables.

```{code-cell} ipython3
# Ejemplo 1: Coordenadas
punto = (10, 20)
x, y = punto  # Desempaqueta en 2 variables
print(f"x = {x}, y = {y}")

# Ejemplo 2: Color RGB
color = (255, 128, 0)
rojo, verde, azul = color
print(f"R={rojo}, G={verde}, B={azul}")

# Ejemplo 3: Datos de persona
persona = ("Ana", 25, "Argentina")
nombre, edad, pais = persona
print(f"{nombre} tiene {edad} años y es de {pais}")
```

:::{warning} Cantidad de Variables Debe Coincidir

El número de variables a la izquierda debe coincidir exactamente con el número de elementos en la tupla.

```{code-cell} ipython3
tupla = (1, 2, 3)

# ❌ Muy pocas variables
try:
    a, b = tupla  # Espera 2, hay 3
except ValueError as e:
    print(f"ERROR: {e}")

# ❌ Demasiadas variables
try:
    a, b, c, d = tupla  # Espera 4, hay 3
except ValueError as e:
    print(f"ERROR: {e}")

# ✓ Cantidad correcta
a, b, c = tupla
print(f"✓ Correcto: a={a}, b={b}, c={c}")
```
:::

---

#### Desempaquetado con `*` (Rest Pattern)

El asterisco `*` permite capturar múltiples elementos restantes en una lista.

```{code-cell} ipython3
# El * captura "el resto" de los elementos
numeros = (1, 2, 3, 4, 5, 6, 7, 8, 9)

# 1️⃣ Primero y el resto
primero, *resto = numeros
print(f"Primero: {primero}")
print(f"Resto: {resto}")

print("\n" + "="*50 + "\n")

# 2️⃣ Primero, resto y último
primero, *medio, ultimo = numeros
print(f"Primero: {primero}")
print(f"Medio: {medio}")
print(f"Último: {ultimo}")

print("\n" + "="*50 + "\n")

# 3️⃣ Primeros dos y el resto
a, b, *resto = numeros
print(f"a={a}, b={b}")
print(f"Resto: {resto}")
```

**Ejemplo práctico con CSV:**

```{code-cell} ipython3
# Datos de estudiante: nombre, apellido, nota1, nota2, nota3, ...
estudiante = ("Ana", "García", 85, 90, 88, 92, 87)

nombre, apellido, *notas = estudiante
print(f"Estudiante: {nombre} {apellido}")
print(f"Notas: {notas}")
print(f"Promedio: {sum(notas) / len(notas):.1f}")
```

---

#### Intercambio de Variables: El Truco Elegante

El desempaquetado hace que intercambiar valores entre variables sea increíblemente simple y legible.

```{code-cell} ipython3
# Forma tradicional (con variable temporal)
a = 5
b = 10
print(f"Antes: a={a}, b={b}")

temp = a
a = b
b = temp
print(f"Después (tradicional): a={a}, b={b}")

print("\n" + "="*50 + "\n")

# Forma Pythonic (con desempaquetado de tuplas)
a = 5
b = 10
print(f"Antes: a={a}, b={b}")

a, b = b, a  # ✨ ¡Intercambio elegante!
print(f"Después (Pythonic): a={a}, b={b}")
```

**¿Cómo funciona?**

```python
a, b = b, a

# Se evalúa así:
# 1. Primero se crea una tupla: (b, a) → (10, 5)
# 2. Luego se desempaqueta: a, b = (10, 5)
# 3. Resultado: a=10, b=5
```

---

#### Desempaquetado en Funciones

Las funciones que retornan tuplas se benefician enormemente del desempaquetado.

```{code-cell} ipython3
# Función que retorna tupla
def obtener_datos_usuario():
    return ("Carlos", "carlos@email.com", 28, "México")

# Desempaquetar el retorno
nombre, email, edad, pais = obtener_datos_usuario()
print(f"Nombre: {nombre}")
print(f"Email: {email}")
print(f"Edad: {edad}")
print(f"País: {pais}")

print("\n" + "="*50 + "\n")

# Ignorar valores con _
def obtener_coordenadas():
    return (10, 20, 30)

x, _, z = obtener_coordenadas()  # Ignoramos y
print(f"x={x}, z={z}")  # Solo usamos x y z
```

---

#### Desempaquetado en Loops

Podés desempaquetar directamente dentro de un bucle `for`.

```{code-cell} ipython3
# Lista de tuplas
personas = [
    ("Ana", 25, "🇦🇷"),
    ("Bruno", 30, "🇧🇷"),
    ("Carlos", 28, "🇲🇽")
]

# Desempaquetar cada tupla en el loop
for nombre, edad, pais in personas:
    print(f"{nombre} ({edad} años) {pais}")

print("\n" + "="*50 + "\n")

# Con enumerate
frutas = ("🍎 manzana", "🍌 banana", "🍊 naranja")
for i, fruta in enumerate(frutas, start=1):
    print(f"{i}. {fruta}")
```

---

#### Desempaquetado Anidado

Si tenés tuplas (u otros iterables) anidados, podés desempaquetarlos de forma anidada.

```{code-cell} ipython3
# Tupla con tuplas adentro
datos = (("Ana", "García"), (25, "Argentina"))

# Desempaquetado anidado
(nombre, apellido), (edad, pais) = datos
print(f"Nombre completo: {nombre} {apellido}")
print(f"Edad: {edad}, País: {pais}")
```

---

#### Casos Prácticos

:::::{grid} 1 1 2 2

::::{grid-item-card} División con Resto
```python
# divmod() retorna tupla (cociente, resto)
resultado = divmod(17, 5)
cociente, resto = resultado
print(f"17 ÷ 5 = {cociente} resto {resto}")
# 17 ÷ 5 = 3 resto 2
```
::::

::::{grid-item-card} Min y Max Simultáneos
```python
numeros = [10, 5, 20, 15, 8]

# Obtener min y max a la vez
minimo, maximo = min(numeros), max(numeros)
print(f"Min: {minimo}, Max: {maximo}")
# Min: 5, Max: 20
```
::::

::::{grid-item-card} Rotar Lista
```python
lista = [1, 2, 3, 4, 5]

# Rotar elementos
primero, *resto = lista
lista = resto + [primero]
print(lista)
# [2, 3, 4, 5, 1]
```
::::

::::{grid-item-card} Procesar CSV
```python
# Línea CSV
linea = "Juan,Pérez,30,Argentina"

# Desempaquetar datos
datos = tuple(linea.split(','))
nombre, apellido, edad, pais = datos
print(f"{nombre} {apellido}")
```
::::

:::::

:::{tip} Consejos de Desempaquetado
1. **Usa `_`** para valores que no necesitás: `x, _, z = tupla`.
2. **Usa `*`** para capturar múltiples valores: `primero, *resto, ultimo`.
3. **Combina con `enumerate()`** en loops: `for i, valor in enumerate(tupla)`.
4. **Intercambio elegante** de variables: `a, b = b, a`.
5. **Funciones que retornan tuplas** → desempaqueta directamente.
:::

---

### Convertir entre Listas y Tuplas

A menudo necesitás convertir entre listas y tuplas dependiendo de tus necesidades: si necesitás mutabilidad (lista) o inmutabilidad (tupla). Python hace esto simple con las funciones `list()` y `tuple()`. La conversión preserva el orden de los elementos.

```{code-cell} ipython3
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
✅ Trabajás con texto.
✅ Necesitás inmutabilidad.
✅ Vas a usar como clave de diccionario.
✅ Procesás datos de entrada/salida.

```{code-cell} ipython3
# Ejemplos de uso
nombre = "Ana García"
email = "ana@ejemplo.com"
mensaje = f"Hola {nombre}, tu email es {email}"
```

#### Usa `list` cuando:
✅ Necesitás secuencia ordenada.
✅ Vas a modificar elementos.
✅ El orden importa.
✅ Pueden haber duplicados.

```{code-cell} ipython3
# Ejemplos de uso
tareas = ["lavar", "cocinar", "limpiar"]
numeros = [1, 2, 2, 3, 3, 3]  # Duplicados OK
tareas.append("estudiar")  # Mutable
```

#### Usa `dict` cuando:
✅ Necesitás mapeo clave-valor.
✅ Acceso rápido por clave (O(1)).
✅ Datos estructurados.
✅ Configuraciones o metadatos.

```{code-cell} ipython3
# Ejemplos de uso
persona = {"nombre": "Ana", "edad": 25, "ciudad": "Bariloche"}
config = {"host": "localhost", "puerto": 8080}
contador = {"manzanas": 5, "bananas": 3}
```

#### Usa `set` cuando:
✅ Necesitás elementos únicos.
✅ Operaciones de conjuntos (unión, intersección).
✅ El orden no importa.
✅ Verificar pertenencia rápida (O(1)).

```{code-cell} ipython3
# Ejemplos de uso
tags = {"python", "programacion", "tutorial"}
visitados = {1, 5, 10, 15}

# Eliminar duplicados
numeros = [1, 2, 2, 3, 3, 3]
unicos = list(set(numeros))  # [1, 2, 3]
```

#### Usa `tuple` cuando:
✅ Secuencia inmutable.
✅ Retornar múltiples valores.
✅ Usarla como clave de diccionario.
✅ Datos que no deben cambiar.

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

Python facilita la conversión entre diferentes tipos de colecciones mediante funciones constructoras. Estas conversiones son útiles cuando necesitás las características específicas de un tipo: por ejemplo, convertir a `set` para eliminar duplicados, a `list` para ordenar, o a `tuple` para hacerlo inmutable. Cada conversión tiene sus reglas: algunas preservan orden, otras eliminan duplicados, y algunas requieren estructuras específicas como pares clave-valor para diccionarios.

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
# elemento in coleccion    # True/False
# elemento not in coleccion

# Ejemplos
print(2 in [1, 2, 3])           # True
print("Ana" in {"nombre": "Ana"})  # True (busca en claves)
print("x" in "texto")           # True
```

#### Longitud (todos los tipos)

```{code-cell} ipython3
# len(coleccion)  # Número de elementos

print(len("Python"))        # 6
print(len([1, 2, 3]))       # 3
print(len({"a": 1, "b": 2}))  # 2
print(len({1, 2, 3}))       # 3
```

#### Iteración (todos los tipos)

```{code-cell} ipython3
coleccion = [1, 2, 3]
diccionario = {"a": 1}

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

Para más detalles sobre {term}`funciones <Función>`, consultá el capítulo {ref}`4 - Funciones <funciones>`.

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

```