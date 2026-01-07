---
marp: true
theme: default
paginate: true
header: 'Modularización en Python'
footer: 'Módulos, paquetes y biblioteca estándar'
style: |
  section {
    font-size: 26px;
  }
  h1 {
    color: #1976d2;
  }
  code {
    background-color: #f5f5f5;
  }
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Modularización en Python

**Organización de código, módulos, paquetes y biblioteca estándar**

---

## ¿Qué vas a aprender?

* **Importar y usar** módulos de Python
* **Crear tus propios** módulos reutilizables
* **Organizar código** en paquetes
* **Usar la biblioteca estándar** de Python
* **Trabajar con archivos** de forma segura
* **Manejar excepciones** correctamente

---

## El Problema: Código Monolítico

**Un archivo gigante de 5000 líneas es:**
- 😵 Difícil de entender
- 🐛 Difícil de debuggear
- ♻️ Imposible de reutilizar
- 👥 Imposible de trabajar en equipo

**La Solución: Módulos**
- ✅ Fácil de leer
- ✅ Fácil de encontrar errores
- ✅ Reutilizable en otros proyectos
- ✅ Colaboración efectiva

---

## Analogía: Tu Celular 📱

Tu celular no tiene una sola app gigante, tiene muchas apps pequeñas:

- 📷 **Cámara** → Módulo de fotos
- 🎵 **Música** → Módulo de audio
- 📧 **Email** → Módulo de mensajería
- 🗺️ **Mapas** → Módulo de navegación

**Cada app (módulo) hace una cosa bien y la usás cuando la necesitás**

---

<!-- _class: lead -->

# Importar Módulos

---

## La Biblioteca Estándar

Python viene con una **caja de herramientas gigante** lista para usar.

**No tenés que inventar la rueda:**
- Matemáticas avanzadas → `math`
- Fechas y tiempos → `datetime`
- Números aleatorios → `random`
- Sistema operativo → `os`
- Archivos JSON → `json`

**¡Y muchos más!**

---

## Forma 1: Importar el Módulo Completo

Traer **toda la caja** y sacar lo que necesitás:

```python
import math

# Usar: modulo.funcion()
raiz = math.sqrt(16)
print(f"Raíz de 16: {raiz}")  # 4.0

# Acceder a constantes
print(f"Pi: {math.pi}")  # 3.141592...

# Más funciones
print(f"Seno de π/2: {math.sin(math.pi / 2)}")  # 1.0
```

**Ventaja:** Claro de dónde viene cada función

---

## Forma 2: Importar Solo lo que Necesitás

Sacar **solo las herramientas específicas**:

```python
from math import sqrt, pi, sin

# Usar directo, sin "math."
raiz = sqrt(16)
print(f"Raíz: {raiz}")

print(f"Pi: {pi}")

print(f"Seno: {sin(pi / 2)}")
```

**Ventajas:** Código más corto, menos tipeo
**Desventaja:** Puede crear conflictos de nombres

---

## Forma 3: Importar Todo (⚠️ Cuidado)

```python
from math import *

# Usar cualquier función del módulo
print(sqrt(25))
print(cos(0))
print(factorial(5))
```

**⚠️ Problema:** No sabés de dónde viene cada función
**⚠️ Riesgo:** Puede sobrescribir tus funciones

```python
from math import *

# Oops, sobrescribiste la función sqrt de math
def sqrt(x):
    return x  # Tu versión diferente
```

---

## Forma 4: Alias (Renombrar)

Darle un **nombre más corto** al módulo:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Usar con el alias
array = np.array([1, 2, 3])
datos = pd.DataFrame({'A': [1, 2, 3]})
plt.plot([1, 2, 3])
```

**Cuándo usar:** Módulos con nombres largos o convención de la comunidad

---

## Comparación de Formas de Import

| Forma | Sintaxis | Uso | Cuándo Usar |
|-------|----------|-----|-------------|
| Completo | `import math` | `math.sqrt(16)` | Muchas funciones |
| Específico | `from math import sqrt` | `sqrt(16)` | Pocas funciones |
| Todo | `from math import *` | `sqrt(16)` | ⚠️ Evitar |
| Alias | `import numpy as np` | `np.array([])` | Nombres largos |

---

<!-- _class: lead -->

# Módulos de la Biblioteca Estándar

---

## `math` - Matemáticas

Funciones matemáticas avanzadas:

```python
import math

# Funciones comunes
print(math.sqrt(16))      # Raíz cuadrada: 4.0
print(math.pow(2, 3))     # Potencia: 8.0
print(math.factorial(5))  # Factorial: 120

# Trigonometría
print(math.sin(math.pi / 2))  # Seno: 1.0
print(math.cos(0))            # Coseno: 1.0

# Constantes
print(math.pi)  # 3.141592...
print(math.e)   # 2.718281...
```

---

## `random` - Números Aleatorios

Generar valores al azar:

```python
import random

# Número aleatorio entre 0 y 1
print(random.random())  # 0.xxx

# Entero aleatorio en rango
dado = random.randint(1, 6)  # Entre 1 y 6
print(f"Tiraste: {dado}")

# Elegir elemento aleatorio
colores = ["rojo", "verde", "azul"]
print(random.choice(colores))

# Mezclar lista
numeros = [1, 2, 3, 4, 5]
random.shuffle(numeros)
print(numeros)  # Orden aleatorio
```

---

## `datetime` - Fechas y Tiempos

Trabajar con fechas y horas:

```python
from datetime import datetime, date, timedelta

# Fecha y hora actual
ahora = datetime.now()
print(f"Ahora: {ahora}")

# Solo la fecha
hoy = date.today()
print(f"Hoy: {hoy}")

# Sumar/restar días
mañana = hoy + timedelta(days=1)
print(f"Mañana: {mañana}")

# Formatear
print(ahora.strftime("%d/%m/%Y %H:%M"))
```

---

## `os` - Sistema Operativo

Interactuar con el sistema:

```python
import os

# Directorio actual
print(os.getcwd())

# Listar archivos
archivos = os.listdir(".")
print(archivos[:5])  # Primeros 5

# Crear carpeta
os.makedirs("nueva_carpeta", exist_ok=True)

# Verificar si existe
if os.path.exists("archivo.txt"):
    print("El archivo existe")

# Información del archivo
info = os.path.getsize("archivo.txt")
print(f"Tamaño: {info} bytes")
```

---

<!-- _class: lead -->

# Crear Tus Propios Módulos

---

## ¿Qué es un Módulo Tuyo?

Un módulo es **simplemente un archivo `.py`** con funciones reutilizables.

**Estructura:**
```
mi_proyecto/
├── main.py           ← Programa principal
└── matematicas.py    ← Tu módulo
```

**Ventajas:**
- ♻️ Reutilizás código
- 📦 Organizás mejor
- 🧪 Más fácil de testear

---

## Paso 1: Crear el Módulo

Creá `matematicas.py`:

```python
"""Módulo con funciones matemáticas básicas."""

PI = 3.14159

def area_circulo(radio):
    """Calcula el área de un círculo."""
    return PI * radio ** 2

def perimetro_circulo(radio):
    """Calcula el perímetro de un círculo."""
    return 2 * PI * radio

def factorial(n):
    """Calcula el factorial de n."""
    if n <= 1:
        return 1
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado
```

---

## Paso 2: Usar tu Módulo

En `main.py`:

```python
import matematicas

# Usar las funciones
area = matematicas.area_circulo(5)
print(f"Área: {area}")

perimetro = matematicas.perimetro_circulo(5)
print(f"Perímetro: {perimetro}")

fact = matematicas.factorial(5)
print(f"5! = {fact}")

# Acceder a la constante
print(f"Pi: {matematicas.PI}")
```

---

## Importar Selectivamente

```python
from matematicas import area_circulo, PI

# Usar sin el prefijo
area = area_circulo(5)
print(f"Área: {area}")

print(f"Pi: {PI}")
```

**Ventaja:** Más conciso cuando usás pocas funciones

---

## Documentación en Módulos

**Siempre documentá tus funciones:**

```python
def area_circulo(radio):
    """Calcula el área de un círculo.
    
    Args:
        radio: La distancia del centro al borde.
    
    Returns:
        El área del círculo (π × radio²).
    
    Example:
        >>> area_circulo(5)
        78.53975
    """
    return PI * radio ** 2
```

**Ver la ayuda:**
```python
help(matematicas.area_circulo)
```

---

## `if __name__ == "__main__"`

Código que solo se ejecuta si ejecutás el módulo directamente:

```python
# matematicas.py
def factorial(n):
    """Calcula n!"""
    if n <= 1:
        return 1
    return n * factorial(n - 1)

# Solo se ejecuta si ejecutás este archivo
if __name__ == "__main__":
    print("Testing factorial:")
    print(f"5! = {factorial(5)}")  # 120
    print(f"0! = {factorial(0)}")  # 1
    print("✅ Tests pasaron")
```

**Cuando importás el módulo, este código NO se ejecuta**

---

## ¿Para qué sirve `__name__`?

**Cuando ejecutás directamente:**
```bash
$ python matematicas.py
```
→ `__name__` es `"__main__"` → Se ejecuta el bloque

**Cuando importás:**
```python
import matematicas
```
→ `__name__` es `"matematicas"` → NO se ejecuta el bloque

**Usos:**
- 🧪 Tests rápidos
- 📝 Ejemplos de uso
- 🛠️ Herramientas CLI

---

<!-- _class: lead -->

# Paquetes

---

## ¿Qué es un Paquete?

Un **paquete** es una **carpeta** con módulos organizados.

**Estructura:**
```
mi_proyecto/
├── main.py
└── matematicas/           ← Paquete
    ├── __init__.py        ← ¡Importante!
    ├── basicas.py
    └── avanzadas.py
```

**Sin `__init__.py`, Python NO reconoce la carpeta como paquete**

---

## Crear un Paquete Paso a Paso

**1. Crear la carpeta:**
```bash
mkdir matematicas
```

**2. Crear `__init__.py`:**
```python
# matematicas/__init__.py
"""Paquete de operaciones matemáticas."""

from .basicas import sumar, restar
from .avanzadas import potencia, factorial

__version__ = "1.0.0"
```

**3. Crear módulos:**
- `basicas.py` → Funciones simples
- `avanzadas.py` → Funciones complejas

---

## Módulo `basicas.py`

```python
# matematicas/basicas.py
"""Operaciones matemáticas básicas."""

def sumar(a, b):
    """Suma dos números."""
    return a + b

def restar(a, b):
    """Resta dos números."""
    return a - b

def multiplicar(a, b):
    """Multiplica dos números."""
    return a * b

def dividir(a, b):
    """Divide dos números."""
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b
```

---

## Módulo `avanzadas.py`

```python
# matematicas/avanzadas.py
"""Operaciones matemáticas avanzadas."""

def potencia(base, exponente):
    """Calcula base^exponente."""
    return base ** exponente

def raiz(numero, n=2):
    """Calcula la raíz n-ésima."""
    return numero ** (1/n)

def factorial(n):
    """Calcula n!"""
    if n < 0:
        raise ValueError("n debe ser no negativo")
    if n <= 1:
        return 1
    return n * factorial(n - 1)
```

---

## Usar el Paquete

```python
# Forma 1: Importar funciones directamente
from matematicas import sumar, potencia

print(sumar(5, 3))      # 8
print(potencia(2, 3))   # 8

# Forma 2: Importar módulos
from matematicas import basicas, avanzadas

print(basicas.multiplicar(4, 5))    # 20
print(avanzadas.factorial(5))       # 120

# Forma 3: Importar todo el paquete
import matematicas

print(matematicas.restar(10, 3))    # 7
```

---

## Paquetes Anidados

Podés tener paquetes dentro de paquetes:

```
proyecto/
└── mate/
    ├── __init__.py
    ├── aritmetica/
    │   ├── __init__.py
    │   ├── basicas.py
    │   └── avanzadas.py
    └── geometria/
        ├── __init__.py
        ├── plano.py
        └── espacio.py
```

**Importar:**
```python
from mate.aritmetica.basicas import sumar
from mate.geometria.plano import area_circulo
```

---

<!-- _class: lead -->

# Trabajar con Archivos

---

## Leer Archivos

**Forma correcta (con `with`):**

```python
# Leer todo el archivo
with open("datos.txt", "r", encoding="utf-8") as archivo:
    contenido = archivo.read()
    print(contenido)
# El archivo se cierra automáticamente

# Leer línea por línea
with open("datos.txt", "r", encoding="utf-8") as archivo:
    for linea in archivo:
        print(linea.strip())  # strip() quita \n
```

**Ventaja del `with`:** Cierra el archivo automáticamente, incluso si hay error

---

## Escribir Archivos

```python
# Modo "w" - Sobrescribe (cuidado!)
with open("salida.txt", "w", encoding="utf-8") as archivo:
    archivo.write("Primera línea\n")
    archivo.write("Segunda línea\n")

# Modo "a" - Agrega al final
with open("salida.txt", "a", encoding="utf-8") as archivo:
    archivo.write("Línea adicional\n")

# Escribir múltiples líneas
lineas = ["Línea 1\n", "Línea 2\n", "Línea 3\n"]
with open("salida.txt", "w", encoding="utf-8") as archivo:
    archivo.writelines(lineas)
```

---

## Modos de Apertura

| Modo | Descripción | Crea si no existe |
|------|-------------|-------------------|
| `"r"` | Solo lectura | ❌ Error |
| `"w"` | Escritura (sobrescribe) | ✅ Sí |
| `"a"` | Agregar al final | ✅ Sí |
| `"r+"` | Lectura y escritura | ❌ Error |
| `"w+"` | Lectura y escritura | ✅ Sí |

**Agregar `b` para binario:** `"rb"`, `"wb"`

---

## Trabajar con JSON

```python
import json

# Python dict → JSON
persona = {
    "nombre": "Ana",
    "edad": 25,
    "hobbies": ["leer", "programar"]
}

# Guardar en archivo
with open("persona.json", "w", encoding="utf-8") as archivo:
    json.dump(persona, archivo, indent=2, ensure_ascii=False)

# Cargar desde archivo
with open("persona.json", "r", encoding="utf-8") as archivo:
    datos = json.load(archivo)

print(datos["nombre"])  # Ana
```

---

## Verificar Existencia de Archivo

```python
import os

archivo = "datos.txt"

# Verificar si existe
if os.path.exists(archivo):
    print("El archivo existe")
    
    # Información adicional
    tamaño = os.path.getsize(archivo)
    print(f"Tamaño: {tamaño} bytes")
else:
    print("El archivo NO existe")
    # Crearlo
    with open(archivo, "w") as f:
        f.write("Archivo nuevo\n")
```

---

<!-- _class: lead -->

# Manejo de Excepciones

---

## ¿Qué es una Excepción?

Un **error** que ocurre durante la ejecución del programa.

**Ejemplos comunes:**
- `ValueError`: Conversión inválida
- `TypeError`: Tipo incorrecto
- `ZeroDivisionError`: División por cero
- `FileNotFoundError`: Archivo no existe
- `KeyError`: Clave no existe en dict
- `IndexError`: Índice fuera de rango

---

## Try-Except Básico

```python
try:
    # Código que puede fallar
    numero = int(input("Ingrese un número: "))
    resultado = 10 / numero
    print(f"Resultado: {resultado}")
except ValueError:
    print("Error: debe ingresar un número válido")
except ZeroDivisionError:
    print("Error: no se puede dividir por cero")
```

**Sin try-except, el programa se detiene. Con try-except, lo manejás.**

---

## Capturar el Error

```python
try:
    numero = int(input("Número: "))
except ValueError as e:
    print(f"Error: {e}")
    print("Por favor ingrese un número válido")
```

**La variable `e` contiene información del error**

---

## Try-Except-Else-Finally

```python
try:
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    print("El archivo no existe")
else:
    # Se ejecuta si NO hubo error
    print(f"Leído: {len(contenido)} caracteres")
finally:
    # SIEMPRE se ejecuta
    if 'archivo' in locals():
        archivo.close()
        print("Archivo cerrado")
```

---

## Múltiples Excepciones

```python
# Capturar varias en una línea
try:
    resultado = int(input("Número: ")) / 2
except (ValueError, ZeroDivisionError) as e:
    print(f"Error: {e}")

# Capturar todas las excepciones
try:
    # Código peligroso
    resultado = procesar_datos()
except Exception as e:
    print(f"Ocurrió un error: {e}")
```

---

## Lanzar Excepciones

```python
def dividir(a, b):
    """Divide dos números."""
    if b == 0:
        raise ValueError("El divisor no puede ser cero")
    
    if not isinstance(a, (int, float)):
        raise TypeError("Los argumentos deben ser números")
    
    return a / b

# Usar
try:
    resultado = dividir(10, 0)
except ValueError as e:
    print(f"Error: {e}")
```

---

## Context Managers (with)

El `with` es un **context manager** que maneja recursos automáticamente:

```python
# ❌ Sin with (manual)
archivo = open("datos.txt", "r")
try:
    contenido = archivo.read()
finally:
    archivo.close()  # Tenés que recordar cerrar

# ✓ Con with (automático)
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
# Se cierra automáticamente, incluso si hay error
```

---

<!-- _class: lead -->

# Buenas Prácticas

---

## 1. Organizar Imports

```python
# ✓ Orden correcto:
# 1. Biblioteca estándar
import os
import sys
from datetime import datetime

# 2. Bibliotecas de terceros
import numpy as np
import pandas as pd

# 3. Módulos propios
from mis_modulos import funciones
import configuracion
```

**Regla:** Alfabéticamente dentro de cada grupo

---

## 2. Usar `with` para Archivos

```python
# ❌ Mal: puede no cerrar el archivo
archivo = open("datos.txt", "r")
contenido = archivo.read()
archivo.close()  # ¿Qué pasa si hay error antes?

# ✓ Bien: cierre automático
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
# Garantizado que se cierra
```

---

## 3. Documentar Módulos

```python
"""Módulo de utilidades matemáticas.

Este módulo provee funciones para cálculos
matemáticos comunes.

Example:
    >>> from matematicas import factorial
    >>> factorial(5)
    120
"""

def factorial(n):
    """Calcula n!
    
    Args:
        n: Entero no negativo.
    
    Returns:
        El factorial de n.
    """
    pass
```

---

## 4. No Usar `import *`

```python
# ❌ Mal: confuso, contamina namespace
from math import *
from random import *

resultado = sqrt(16)  # ¿De dónde viene?

# ✓ Bien: explícito
import math
import random

resultado = math.sqrt(16)  # Claro que es de math
```

---

## 5. Nombres Descriptivos

```python
# ❌ Mal: nombres genéricos
import datos as d
from utils import func

# ✓ Bien: nombres claros
import procesador_datos as proc_datos
from utilidades import validar_email
```

---

<!-- _class: lead -->

# Resumen

---

## Conceptos Clave

**Módulos:**
- Archivo `.py` con funciones reutilizables
- `import modulo` o `from modulo import funcion`
- Crear: escribir funciones en un archivo

**Paquetes:**
- Carpeta con `__init__.py` y módulos
- Organizar código relacionado
- Imports: `from paquete.modulo import funcion`

---

## Conceptos Clave (cont.)

**Archivos:**
- `with open()` para lectura/escritura segura
- Modos: `"r"` lectura, `"w"` escritura, `"a"` agregar
- JSON: `json.dump()` y `json.load()`

**Excepciones:**
- `try-except` para manejar errores
- `finally` siempre se ejecuta
- `raise` para lanzar excepciones propias

---

## Biblioteca Estándar Esencial

| Módulo | Para qué sirve |
|--------|----------------|
| `math` | Matemáticas avanzadas |
| `random` | Números aleatorios |
| `datetime` | Fechas y tiempos |
| `os` | Sistema operativo |
| `json` | Formato JSON |
| `sys` | Información del sistema |

---

## Checklist de Aprendizaje

✅ Crear un módulo con funciones propias
✅ Importar y usar funciones de un módulo
✅ Organizar código en paquetes
✅ Leer y escribir archivos con `with`
✅ Manejar errores con `try-except`
✅ Usar módulos de la biblioteca estándar
✅ Documentar módulos con docstrings

---

## Errores Comunes

❌ Olvidar `__init__.py` en paquetes
❌ No cerrar archivos (usar `with`)
❌ Usar `import *` (contamina namespace)
❌ No manejar excepciones en archivos
❌ Rutas hardcodeadas en lugar de `os.path`
❌ No documentar módulos

---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

La modularización es clave para escribir código profesional, mantenible y reutilizable.

**Recordá:**
- Dividí tu código en módulos lógicos
- Usá `with` para archivos
- Manejá excepciones apropiadamente
- Documentá tus módulos

¡Tu código será más limpio, organizado y profesional!
