---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Modularización en Python'
footer: 'Módulos, paquetes y biblioteca estándar'

---

<!-- _paginate: false -->
<!-- _header: '' -->

# Modularización en Python

**Organización de código, módulos, paquetes y biblioteca estándar**

<!--
¡Buenas, buenas! Hoy vamos a subir el nivel. Vamos a hablar de Modularización. Hasta ahora, nuestros programas eran scripts chiquitos, de un solo archivo. Pero cuando la cosa se pone seria, no podés tener todo mezclado. Hoy vamos a aprender a organizar el código como profesionales, usando módulos y paquetes. Es la diferencia entre tener un cajón de herramientas desordenado y un taller impecable.
-->
---

## ¿Qué vas a aprender?

* **Importar y usar** módulos de Python
* **Crear tus propios** módulos reutilizables
* **Organizar código** en paquetes
* **Usar la biblioteca estándar** de Python
* **Trabajar con archivos** de forma segura
* **Manejar excepciones** correctamente

<!--
El menú de hoy viene cargado. Vamos a ver cómo usar el código que otros ya escribieron (la biblioteca estándar), cómo crear nuestros propios archivos de código reutilizable (módulos) y cómo organizarlos en carpetas (paquetes). También vamos a tocar dos temas fundamentales para cualquier programa real: trabajar con archivos (leer y escribir datos) y manejar errores (excepciones) para que el programa no explote en la cara del usuario.
-->
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

<!--
Imaginen un archivo de 5000 líneas. Es una pesadilla. Encontrás un error y no sabés dónde mirar. Querés usar una función en otro lado y tenés que copiar y pegar. Es imposible trabajar en equipo así. La solución es dividir y conquistar. Romper ese monolito en piezas pequeñas, lógicas y manejables. Eso es modularizar.
-->
---

## Analogía: Tu Celular 📱

Tu celular no tiene una sola app gigante, tiene muchas apps pequeñas:

- 📷 **Cámara** → Módulo de fotos
- 🎵 **Música** → Módulo de audio
- 📧 **Email** → Módulo de mensajería
- 🗺️ **Mapas** → Módulo de navegación

**Cada app (módulo) hace una cosa bien y la usás cuando la necesitás**

<!--
Piensen en su celular. No es una sola aplicación gigante que hace todo. Tienen la app de Cámara, la de Mapas, la de Spotify. Cada una es un módulo especializado. Cuando querés sacar una foto, abrís la Cámara. Cuando querés escuchar música, abrís Spotify. En Python es igual: tenés un módulo para matemáticas, otro para fechas, otro para archivos. Cada uno hace lo suyo y lo hace bien.
-->
---

<!-- _class: lead -->

# Importar Módulos

<!--
Python viene con 'pilas incluidas'. La Biblioteca Estándar es una colección enorme de módulos que ya vienen instalados. Tienen de todo: desde cosas matemáticas complejas hasta herramientas para conectarse a internet. Antes de escribir una función complicada, fíjense si Python no la trae ya hecha. Spoiler: probablemente sí.
-->
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

<!--
Para usar estas herramientas, tenemos que avisarle a Python. La forma más clásica es `import modulo`. Traés la caja de herramientas entera. Para usar algo, tenés que decir 'caja.herramienta', o sea `math.sqrt`. Es muy claro porque leyendo el código sabés exactamente de dónde salió esa función.
-->
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

<!--
Si solo vas a usar el martillo, ¿para qué traer toda la caja? Con `from modulo import funcion` traés solo lo que necesitás. La ventaja es que lo usás directo: `sqrt(16)`. El código queda más limpio. Pero ojo con los nombres, si tenés una función `sqrt` tuya, podés tener conflictos.
-->
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

<!--
¡Alerta roja! `from modulo import *` parece cómodo porque traés todo y lo usás directo. Pero es una mala práctica. Estás volcando toda la caja de herramientas en tu mesa de trabajo. No sabés qué trajiste, y podés sobrescribir funciones tuyas sin darte cuenta. Eviten esto en código de producción.
-->
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

<!--
A veces los nombres son largos o querés seguir una convención. `import pandas as pd` es el estándar en ciencia de datos. `import numpy as np`. Usás el alias para escribir menos, pero seguís siendo explícito sobre el origen. Es un buen balance.
-->
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

<!--
Acá tienen un machete para decidir qué import usar. `import modulo` es lo más seguro y claro. `from modulo import funcion` es bueno para cosas muy específicas. Los alias son geniales para bibliotecas populares. Y el asterisco... bueno, déjenlo para la consola interactiva nomás.
-->
---

## Comparación de Formas de Import

| Forma | Sintaxis | Uso | Cuándo Usar |
|
---
----|
---
---
----|
-----|
---
---
---
----|
| Completo | `import math` | `math.sqrt(16)` | Muchas funciones |
| Específico | `from math import sqrt` | `sqrt(16)` | Pocas funciones |
| Todo | `from math import *` | `sqrt(16)` | ⚠️ Evitar |
| Alias | `import numpy as np` | `np.array([])` | Nombres largos |

<!--
Vamos a ver algunos módulos estrella. `math` tiene todo lo que soñaron en el colegio y más. Raíces, potencias, trigonometría, constantes como Pi y Euler. Si tienen que hacer cuentas, arranquen por acá.
-->
---

<!-- _class: lead -->

# Módulos de la Biblioteca Estándar

<!--
`random` es divertidísimo. Números al azar, tirar dados, elegir cartas de un mazo, mezclar listas. Es fundamental para juegos, simulaciones y para testear programas con datos de prueba.
-->
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

<!--
`datetime` es el dueño del tiempo. Manejar fechas a mano es un dolor de cabeza (años bisiestos, zonas horarias). Este módulo lo resuelve. Pueden calcular 'mañana', restar fechas, formatear la hora para que se vea linda. Imprescindible.
-->
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

<!--
`os` es el puente con el sistema operativo. Crear carpetas, listar archivos, ver si un archivo existe. Esto es clave para hacer scripts que automaticen tareas en tu computadora.
-->
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

<!--
Ahora sí, manos a la obra. ¿Cómo hacemos nuestros propios módulos? Es ridículamente fácil: cualquier archivo `.py` ES un módulo. Si creás `matematicas.py` y le ponés funciones adentro, ¡listo! Ya tenés un módulo.
-->
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

<!--
Una vez creado el archivo, lo importás igual que a los de Python. `import matematicas`. Y usás sus funciones con `matematicas.funcion()`. Mágicamente, tu código principal queda limpio y ordenado, y toda la lógica pesada está escondida en el otro archivo.
-->
---

<!-- _class: lead -->

# Crear Tus Propios Módulos

<!--
También podés importar funciones específicas de tu módulo. `from matematicas import area_circulo`. Es exactamente igual que con la biblioteca estándar. Tu código se comporta como ciudadano de primera clase.
-->
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

<!--
Documentar es vital. Si vas a reutilizar código, tenés que explicar qué hace. Los docstrings no son solo comentarios, son la ayuda oficial. Si alguien hace `help(tu_funcion)`, va a ver lo que escribiste ahí. Sean claros y profesionales.
-->
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

<!--
Este truco es clave: `if __name__ == '__main__':`. Este bloque de código solo se ejecuta si corrés el archivo DIRECTAMENTE. Si lo importás desde otro lado, Python lo ignora. Es el lugar perfecto para poner tests rápidos o ejemplos de uso sin ensuciar el código cuando se importa.
-->
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

<!--
Para entender `__name__`: es una variable mágica que Python define. Si sos el programa principal, vale `__main__`. Si fuiste importado, vale el nombre de tu archivo. Es la forma que tiene el módulo de saber si es el protagonista o un actor de reparto.
-->
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

<!--
Cuando tenés muchos módulos, una carpeta plana no alcanza. Necesitás Paquetes. Un paquete es simplemente una carpeta que contiene módulos. El secreto es el archivo `__init__.py`. Ese archivo le dice a Python: 'Che, esta carpeta es un paquete, tratalo con respeto'.
-->
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

<!--
Paso a paso: creás la carpeta, metés el `__init__.py` (puede estar vacío o exponer funciones principales) y adentro ponés tus módulos `.py`. Ahora tenés una estructura jerárquica profesional.
-->
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

<!--
Los módulos del paquete pueden ser tan simples o complejos como quieras. Acá `basicas.py` tiene sumar y restar. Fíjense que cada función tiene su docstring. La prolijidad ante todo.
-->
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

<!--
Y `avanzadas.py` tiene cosas más potentes. Dividir el código así te ayuda a mentalizar el problema. ¿Es una cuenta básica? Voy a `basicas`. ¿Es algo raro? Voy a `avanzadas`.
-->
---

<!-- _class: lead -->

# Paquetes

<!--
Para usarlo, navegás la jerarquía con puntos. `from paquete import modulo`. O `from paquete.modulo import funcion`. Es muy intuitivo. Python se encarga de encontrar los archivos.
-->
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

<!--
Y esto puede seguir. Paquetes dentro de paquetes. `mate.geometria.plano`. No hay límite (más allá del sentido común). Así están organizadas las grandes librerías como Django o Flask.
-->
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

<!--
Cambio de tema: Archivos. Los programas necesitan memoria a largo plazo. Leer y escribir archivos es básico. La regla de oro acá es usar `with open(...)`. El `with` se encarga de cerrar el archivo pase lo que pase. Es el cinturón de seguridad de los archivos.
-->
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

<!--
Escribir es igual de fácil. Ojo con los modos: `'w'` borra todo lo que había y escribe de cero. `'a'` (append) agrega al final sin borrar. Elijan con sabiduría.
-->
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

<!--
Esta tabla es para imprimir y pegar en el monitor. `r` (read), `w` (write), `a` (append). Y si trabajan con imágenes o archivos binarios, le agregan una `b` (`rb`, `wb`).
-->
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

<!--
JSON es el formato estándar de la web. Python lo ama. El módulo `json` te permite convertir diccionarios de Python a texto JSON (`dump`) y viceversa (`load`). Es la forma más fácil de guardar configuraciones o datos estructurados.
-->
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

<!--
Antes de intentar abrir un archivo, preguntá si existe. `os.path.exists()` te salva de errores feos. Es como golpear antes de entrar.
-->
---

<!-- _class: lead -->

# Trabajar con Archivos

<!--
Hablando de errores... Manejo de Excepciones. Los programas fallan. El usuario ingresa texto en vez de números, el archivo no está, se corta internet. Si no manejamos estos errores, el programa crashea feo. Las excepciones son la forma elegante de manejar lo inesperado.
-->
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

<!--
El bloque `try-except` es la red de contención. En el `try` ponés el código riesgoso. En el `except` decís qué hacer si falla. En lugar de un error rojo y feo, el usuario recibe un mensaje amable.
-->
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

<!--
Podés capturar el error en una variable `e` para saber qué pasó exactamente. A veces querés mostrar el error técnico, a veces solo un mensaje genérico.
-->
---

## Modos de Apertura

| Modo | Descripción | Crea si no existe |
|
---
---|
---
---
---
----|
---
---
---
---
---
----|
| `"r"` | Solo lectura | ❌ Error |
| `"w"` | Escritura (sobrescribe) | ✅ Sí |
| `"a"` | Agregar al final | ✅ Sí |
| `"r+"` | Lectura y escritura | ❌ Error |
| `"w+"` | Lectura y escritura | ✅ Sí |

**Agregar `b` para binario:** `"rb"`, `"wb"`

<!--
`else` se ejecuta si todo salió bien (útil para código que depende del éxito del `try` pero no querés que sus errores sean capturados). `finally` se ejecuta SIEMPRE, haya error o no. Es ideal para limpieza, cerrar conexiones, etc.
-->
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

<!--
Podés tener múltiples `except` para atajar distintos problemas. No es lo mismo dividir por cero que no encontrar un archivo. Y podés tener un `except Exception` genérico para 'cualquier otra cosa', pero úsenlo con cuidado.
-->
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

<!--
A veces vos querés generar tus propios errores. Si la función espera positivos y recibe un negativo, ¡`raise ValueError`! Es la forma de decirle a quien usa tu función: 'Hiciste algo mal'.
-->
---

<!-- _class: lead -->

# Manejo de Excepciones

<!--
Volvemos al `with`. Técnicamente es un 'Context Manager'. Se asegura de que los recursos (archivos, conexiones) se liberen correctamente. Úsenlo siempre que puedan.
-->
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

<!--
Buenas prácticas para cerrar. Los imports van arriba de todo. Ordenados: primero biblioteca estándar, después librerías externas, y al final tus módulos. Separados por grupos. Es cuestión de orden y limpieza.
-->
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

<!--
Jamás de los jamases confíen en cerrar archivos manualmente. Siempre `with`. Un error antes del `close()` y el archivo queda abierto, consumiendo memoria y bloqueando el sistema.
-->
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

<!--
Documenten sus módulos. Un docstring al principio del archivo explicando qué hace el módulo entero ayuda muchísimo a entender la arquitectura del proyecto.
-->
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

<!--
Repito: NO usen `from modulo import *`. Ensucia el espacio de nombres (namespace). Sean explícitos. `math.sqrt` es mejor que `sqrt` suelta que no sabés de dónde vino.
-->
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

<!--
Nombres claros. `import modulo_procesamiento_imagenes` es largo pero claro. Si es muy largo, usen un alias `import modulo... as mpi`. Pero no usen nombres crípticos.
-->
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

<!--
Repasemos. Vimos Módulos (archivos), Paquetes (carpetas con `__init__`), cómo importar, cómo leer/escribir archivos con `with` y JSON, y cómo manejar errores con `try-except`. Tienen el kit completo.
-->
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

<!--
Checklist mental. Archivos, excepciones, módulos estándar. Si dominan esto, ya no son principiantes. Están escribiendo software robusto.
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
La biblioteca estándar es su mejor amiga. `os`, `sys`, `math`, `json`, `datetime`. Apréndanlos, los van a usar en todos los proyectos.
-->
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

<!--
Si pueden tachar todo esto de la lista, felicidades. Están listos para construir sistemas complejos y organizados.
-->
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

<!--
Cuidado con estos errores. Olvidar el `__init__`, no cerrar archivos, importar todo con asterisco. Son errores de novato que ahora ya saben evitar.
-->
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

<!--
¡Gracias por la atención! Ahora, a romper el código. Prueben crear su propio paquete, intenten leer un archivo que no existe y atajen el error. La práctica hace al maestro. ¡A codear!
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Resumen

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

## Biblioteca Estándar Esencial

| Módulo | Para qué sirve |
|
---
-----|
---
---
---
---
----|
| `math` | Matemáticas avanzadas |
| `random` | Números aleatorios |
| `datetime` | Fechas y tiempos |
| `os` | Sistema operativo |
| `json` | Formato JSON |
| `sys` | Información del sistema |

<!--
NO MORE NOTES
-->
---

## Checklist de Aprendizaje

✅ Crear un módulo con funciones propias
✅ Importar y usar funciones de un módulo
✅ Organizar código en paquetes
✅ Leer y escribir archivos con `with`
✅ Manejar errores con `try-except`
✅ Usar módulos de la biblioteca estándar
✅ Documentar módulos con docstrings

<!--
NO MORE NOTES
-->
---

## Errores Comunes

❌ Olvidar `__init__.py` en paquetes
❌ No cerrar archivos (usar `with`)
❌ Usar `import *` (contamina namespace)
❌ No manejar excepciones en archivos
❌ Rutas hardcodeadas en lugar de `os.path`
❌ No documentar módulos

<!--
NO MORE NOTES
-->
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
