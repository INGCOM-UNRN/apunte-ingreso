---
title: Modularización
short_title: 5 - Módulos
subtitle: Organización de código, módulos, paquetes y biblioteca estándar.
---

(modularizacion)=
#  Modularización

```{epigraph}
"Los grandes programas no se construyen en un solo archivo, se organizan en módulos reutilizables."

-- Filosofía de programación modular
```

## Introducción: Organizando tu Código

Imaginate que estás construyendo una casa 🏠. No pondrías todas tus herramientas en una sola caja gigante, ¿verdad? Las organizarías en diferentes cajas: una para herramientas eléctricas 🔌, otra para pintura , otra para carpintería 🔨. 

**Los módulos en Python son exactamente eso: cajas organizadas de herramientas (funciones) que podés usar cuando las necesitás.**

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} El Problema
:class-header: bg-danger text-white

Un archivo de 5000 líneas es:
- Difícil de entender
- Difícil de debuggear  
- Imposible de reutilizar
- Imposible de trabajar en equipo
:::

:::{grid-item-card} La Solución: Módulos
:class-header: bg-success text-white

Dividir en archivos pequeños:
- Fácil de leer
- Fácil de encontrar errores
- Reutilizable en otros proyectos
- Colaboración efectiva
:::
::::

```{figure} ./5_modulos/modulo_concepto.svg
:name: fig-modulo-concepto
:align: center
:width: 100%

Concepto visual de un módulo: una caja de herramientas que importás y usás
```

::::{admonition} Analogía del Día a Día
:class: tip

Pensá en tu celular 📱. No tiene una sola app gigante, tiene muchas apps pequeñas:
- Cámara → Módulo de fotos
- Música → Módulo de audio
- Email → Módulo de mensajería
- Mapas → Módulo de navegación

Cada app (módulo) hace una cosa bien y podés usarlas cuando las necesitás.
::::

### Objetivos de Este Capítulo

```{admonition} Lo que aprenderás
:class: note

1. **Importar y usar** módulos de Python
2. **Crear tus propios** módulos reutilizables
3. **Organizar código** en paquetes
4. **Usar la biblioteca estándar** de Python

---

(importar-modulos)=
## Importar Módulos: Trayendo Herramientas

Python viene con una **caja de herramientas gigante**llamada "biblioteca estándar". Son cientos de módulos listos para usar. ¡No tenés que inventar la rueda!

```{figure} ./5_modulos/import_formas.svg
:name: fig-import-formas
:align: center
:width: 100%

Las diferentes formas de importar módulos y cuándo usar cada una
```

###  Forma 1: Importar el Módulo Completo

Es como traer **toda la caja de herramientas**y sacar lo que necesitás.

```{code-cell} ipython3
import math

# Usás: modulo.funcion()
raiz = math.sqrt(16)
print(f"La raíz cuadrada de 16 es: {raiz}")

# Acceder a constantes
print(f"El valor de π (pi) es: {math.pi}")

# Más funciones
print(f"El seno de π/2 es: {math.sin(math.pi / 2)}")
```

::::{admonition} Cuándo Usar Esta Forma
:class: tip

Usá `import modulo` cuando:
- Uses **muchas funciones**del módulo
- Quieras que sea **claro de dónde viene**cada función
- Quieras **evitar conflictos**de nombres

```{code-cell} ipython3
import math
import statistics

# Claro que sqrt viene de math
promedio = math.sqrt(statistics.mean([4, 9, 16]))
print(promedio)
```
::::

### Forma 2: Importar Solo lo que Necesitás

Es como sacar **solo las herramientas específicas** que vas a usar.

```{code-cell} ipython3
from math import sqrt, pi, sin

# Usás directo, sin el "math."
raiz = sqrt(16)
print(f"Raíz: {raiz}")

print(f"Pi: {pi}")

print(f"Seno: {sin(pi / 2)}")
```

::::{grid} 1 1 2 2
:gutter: 2

:::{grid-item-card} ✅ Ventajas
- Código más corto
- Menos tipeo
- Más legible si son pocas cosas
:::

:::{grid-item-card} Desventajas
- Menos claro de dónde viene
- Puede causar conflictos
:::
::::

### Forma 3: Importar con Alias (Sobrenombre)

Es como ponerle un **apodo más corto**a algo largo.

```{code-cell} ipython3
# Alias para módulos
import pandas as pd          # ¡Convención de la comunidad!
import numpy as np           # Todos usan estos nombres
import matplotlib.pyplot as plt

# Alias para funciones
from math import sqrt as raiz_cuadrada

resultado = raiz_cuadrada(25)
print(f"La raíz de 25 es: {resultado}")
```

::::{admonition} Aliases Comunes (Convenciones)
:class: note

Algunos módulos tienen aliases **estándar** que todos usan:

| Módulo Original | Alias | ¿Por qué? |
|----------------|-------|-----------|
| `pandas` | `pd` | Más corto, convención universal |
| `numpy` | `np` | Estándar de la comunidad |
| `matplotlib.pyplot` | `plt` | Simplifica el código |
| `tensorflow` | `tf` | Nombre largo, alias corto |

```{code-cell} ipython3
import pandas as pd

# Todos los programadores Python reconocen "pd"
df = pd.DataFrame({'nombres': ['Ana', 'Bruno']})
print(df)
```
::::

### Forma 4: `import *` (¡NO LO USES!)

Es como **volcar toda la caja** de herramientas en el piso. ¡Desorden total!

```{code-cell} ipython3
# ❌ NUNCA HAGAS ESTO
from math import *

# ¿De dónde viene sqrt? ¿De math? ¿De numpy? ¿De otro módulo?
resultado = sqrt(16)  # No está claro

# Y si tenés dos módulos con funciones del mismo nombre...
# from numpy import *  # numpy también tiene sqrt()
# ¡Conflicto! ¿Cuál sqrt() se usa?
```

::::{danger} ¿Por Qué Es Malo `import *`?
1. **Confusión**: No sabés de dónde viene cada función
2. **Conflictos**: Dos módulos pueden tener funciones con el mismo nombre
3. **Debugging difícil**: Los editores no pueden ayudarte
4. **Rendimiento**: Importás cosas que no usás

```{code-cell} ipython3
# ❌ MAL
from math import *
from numpy import *
resultado = sqrt(16)  # ¿math.sqrt o numpy.sqrt?

# ✅ BIEN
import math
import numpy as np
resultado1 = math.sqrt(16)
resultado2 = np.sqrt(16)  # Claro y sin ambigüedades
```
::::

### Guía Rápida: ¿Cuál Forma Usar?

```{list-table}
:header-rows: 1
:name: tabla-import-guia

* - Situación
  - Forma Recomendada
  - Ejemplo
* - Usás muchas funciones
  - `import modulo`
  - `import math`
* - Usás pocas funciones
  - `from modulo import func`
  - `from math import sqrt, pi`
* - Nombre muy largo
  - `import modulo as alias`
  - `import pandas as pd`
* - Evitar conflictos
  - `import modulo`
  - `import math`
* - **NUNCA**
  - `from modulo import *`
  - ❌ No usar
```

### Caja de Herramientas: Módulos Útiles

Python incluye módulos super útiles que te ahorran **horas de programación**. ¡Conocelos!

::::{tab-set}

:::{tab-item} math
:sync: math

**Funciones matemáticas avanzadas**

```{code-cell} ipython3
import math

# Redondeo
print(f"Techo de 4.3: {math.ceil(4.3)}")      # 5 (redondea arriba)
print(f"Piso de 4.8: {math.floor(4.8)}")     # 4 (redondea abajo)

# Raíces y potencias
print(f"Raíz cuadrada de 16: {math.sqrt(16)}")        # 4.0
print(f"2 elevado a 10: {math.pow(2, 10)}")           # 1024.0

# Trigonometría
print(f"Seno de 90°: {math.sin(math.radians(90))}")   # 1.0

# Constantes
print(f"Pi: {math.pi}")      # 3.141592...
print(f"e: {math.e}")        # 2.718281...
```

:::

:::{tab-item} 🎲 random
:sync: random

**Números y elecciones aleatorias**

```{code-cell} ipython3
import random

# Números aleatorios
numero_entero = random.randint(1, 10)        # Entre 1 y 10
numero_decimal = random.random()             # Entre 0.0 y 1.0
numero_rango = random.uniform(5.5, 10.5)     # Float en rango

print(f"Número aleatorio: {numero_entero}")

# Elecciones aleatorias
colores = ['rojo', 'verde', 'azul', 'amarillo']
color = random.choice(colores)               # Un elemento
print(f"Color elegido: {color}")

# Mezclar listas
random.shuffle(colores)                      # Mezcla in-place
print(f"Colores mezclados: {colores}")

# Múltiples elementos sin repetición
muestra = random.sample(colores, 2)
print(f"Muestra de 2: {muestra}")
```

```{admonition} Casos de Uso Reales
:class: tip

- Juegos: dados, cartas, posiciones enemigas
- Simulaciones: experimentos aleatorios
- Seguridad: generar IDs temporales (¡no para passwords!)
- Muestreo: seleccionar datos aleatorios
```

:::

:::{tab-item} datetime
:sync: datetime

**Fechas, horas y tiempo**

```{code-cell} ipython3
from datetime import datetime, date, time, timedelta

# Fecha y hora actual
ahora = datetime.now()
print(f"Ahora: {ahora}")
print(f"Solo fecha: {ahora.date()}")
print(f"Solo hora: {ahora.time()}")

# Crear fechas específicas
mi_cumple = date(2005, 7, 15)
print(f"Mi cumpleaños: {mi_cumple}")

# Formatear fechas
formato_arg = ahora.strftime("%d/%m/%Y %H:%M")
print(f"Formato argentino: {formato_arg}")

# Operaciones con fechas
mañana = ahora + timedelta(days=1)
print(f"Mañana: {mañana}")

# Diferencia entre fechas
hoy = date.today()
dias_hasta_cumple = (mi_cumple.replace(year=2024) - hoy).days
print(f"Días hasta mi próximo cumple: {dias_hasta_cumple}")
```

:::

:::{tab-item}  os
:sync: os

**Interacción con el sistema operativo**

```{code-cell} ipython3
import os

# Directorio actual
directorio = os.getcwd()
print(f"Estoy en: {directorio}")

# Listar archivos
archivos = os.listdir('.')
print(f"Archivos aquí: {archivos[:5]}")  # Primeros 5

# Verificar existencia
existe = os.path.exists('mi_archivo.txt')
print(f"¿El archivo existe? {existe}")

# Crear directorios
# os.makedirs('nueva_carpeta', exist_ok=True)

# Separador de rutas (funciona en Windows, Linux, Mac)
ruta = os.path.join('carpeta', 'subcarpeta', 'archivo.txt')
print(f"Ruta: {ruta}")

# Información del archivo
if os.path.exists('README.md'):
    tamaño = os.path.getsize('README.md')
    print(f"Tamaño de README: {tamaño} bytes")
```

:::

:::{tab-item} sys
:sync: sys

**Información del sistema Python**

```{code-cell} ipython3
import sys

# Versión de Python
print(f"Versión de Python: {sys.version}")

# Argumentos de línea de comandos
print(f"Argumentos: {sys.argv}")  # Lista de argumentos

# Plataforma
print(f"Sistema operativo: {sys.platform}")

# Rutas donde Python busca módulos
print("Algunas rutas de búsqueda:")
for ruta in sys.path[:3]:
    print(f"  - {ruta}")

# Salir del programa con código
# sys.exit(0)  # 0 = éxito, otro = error
```

:::
::::

::::{admonition} Consejo Pro
:class: tip dropdown

No memorices todos los módulos. Solo recordá que existen y buscá la documentación cuando los necesites:

```python
# En el intérprete de Python:
help(math)         # Ver ayuda del módulo
dir(math)          # Ver todas las funciones disponibles
help(math.sqrt)    # Ayuda de una función específica
```
::::

---

(crear-modulos)=
## Crear Tus Propios Módulos

¡Ahora viene lo divertido! Crear tu propia caja de herramientas reutilizable. 

::::{admonition} ¿Qué es un Módulo Tuyo?
:class: tip

Un módulo es **simplemente un archivo `.py`**con funciones que querés reutilizar.

```{mermaid}
graph LR
    A[Archivo .py] -->|contiene| B[Funciones]
    B -->|+| C[Variables]
    C -->|+| D[Constantes]
    D -->|=| E[¡MÓDULO!]
    
    style A fill:#3498db,color:#fff
    style E fill:#27ae60,color:#fff
```
::::

### Paso 1: Crear el Módulo

Creá un archivo llamado `matematicas.py`:

```{code-block} python
:linenos:
:emphasize-lines: 1,4,17,30
:caption: matematicas.py - Tu primer módulo

"""Módulo con funciones matemáticas básicas.

Este módulo contiene funciones útiles para cálculos
geométricos y matemáticos simples.
"""

# Constante del módulo
PI = 3.14159

def area_circulo(radio):
    """Calcula el área de un círculo.
    
    Imaginate que pintás un círculo completo. Esta función
    te dice cuánta pintura necesitás (el área).
    
    Args:
        radio: La distancia del centro al borde del círculo.
    
    Returns:
        El área del círculo (π × radio²).
    
    Example:
        >>> area_circulo(5)
        78.53975
    """
    return PI * radio **2

def perimetro_circulo(radio):
    """Calcula el perímetro (circunferencia) de un círculo.
    
    Imaginate que rodeás el círculo con una cuerda.
    Esta función te dice qué tan larga es esa cuerda.
    
    Args:
        radio: La distancia del centro al borde.
    
    Returns:
        El perímetro del círculo (2 × π × radio).
    """
    return 2 * PI * radio

def factorial(n):
    """Calcula el factorial de n (n!).
    
    El factorial es: n! = n × (n-1) × (n-2) × ... × 2 × 1
    Por ejemplo: 5! = 5 × 4 × 3 × 2 × 1 = 120
    
    Args:
        n: Número entero no negativo.
    
    Returns:
        El factorial de n.
    
    Raises:
        ValueError: Si n es negativo.
    """
    if n < 0:
        raise ValueError("El factorial no está definido para negativos")
    if n == 0 or n == 1:
        return 1
    
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado
```

::::{admonition} Documentación (Docstring)
:class: note

Fijate que cada función tiene un **docstring**(la parte entre `"""`). Es super importante porque:

1. **Explica qué hace**la función
2. **Documenta los parámetros**(Args)
3. **Documenta lo que retorna**(Returns)
4. **Da ejemplos**(Example)
5. **La ayuda de Python**lo usa automáticamente

```{code-cell} ipython3
# Después podés hacer:
import matematicas
help(matematicas.area_circulo)  # ¡Muestra tu documentación!
```
::::

### Paso 2: Usar Tu Módulo

Creá otro archivo llamado `programa.py` en el **mismo directorio**:

```{code-block} python
:linenos:
:caption: programa.py - Usando tu módulo

import matematicas

# Calcular área de un círculo
radio = 5
area = matematicas.area_circulo(radio)
print(f"Círculo con radio {radio}")
print(f"   Área: {area:.2f} unidades cuadradas")

# Calcular perímetro
perimetro = matematicas.perimetro_circulo(radio)
print(f"   Perímetro: {perimetro:.2f} unidades")

# Usar el factorial
numero = 5
fact = matematicas.factorial(numero)
print(f"\nEl factorial de {numero} es: {fact}")

# Acceder a constantes del módulo
print(f"\nEl valor de PI en mi módulo: {matematicas.PI}")
```

**Salida del programa:**
```{code-block} text
 Círculo con radio 5
   Área: 78.54 unidades cuadradas
   Perímetro: 31.42 unidades

El factorial de 5 es: 120

El valor de PI en mi módulo: 3.14159
```

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} ✅ Ventajas
:class-header: bg-success text-white

-  **Reutilizable**: Usalo en múltiples programas
-  **Organizado**: Funciones relacionadas juntas
-  **Testeable**: Probalo independientemente
-  **Compartible**: Dale el archivo a otros
:::

:::{grid-item-card} Estructura de Archivos
:class-header: bg-info text-white

```
mi_proyecto/
├── matematicas.py    ← Tu módulo
├── programa.py       ← Tu programa principal
└── otro_programa.py  ← Otro programa que usa el módulo
```

Todos los archivos `.py` en la misma carpeta pueden importarse entre sí.
:::
::::

### Ejemplo Interactivo

```{code-cell} ipython3
# Simulamos tener el módulo matematicas
class matematicas:
    PI = 3.14159
    
    @staticmethod
    def area_circulo(radio):
        return matematicas.PI * radio **2
    
    @staticmethod
    def perimetro_circulo(radio):
        return 2 * matematicas.PI * radio
    
    @staticmethod
    def factorial(n):
        if n < 0:
            raise ValueError("No negativo")
        if n <= 1:
            return 1
        resultado = 1
        for i in range(2, n + 1):
            resultado *= i
        return resultado

# Ahora lo usamos
print(" Calculadora de Círculos")
print("=" * 30)

for radio in [3, 5, 10]:
    area = matematicas.area_circulo(radio)
    peri = matematicas.perimetro_circulo(radio)
    print(f"Radio {radio:2d}: Área={area:7.2f}, Perímetro={peri:6.2f}")

print("\nFactoriales:")
print("=" * 30)
for n in [3, 5, 7, 10]:
    fact = matematicas.factorial(n)
    print(f"{n:2d}! = {fact:,}")
```

### Variables y Funciones Privadas

En Python, usamos el **guión bajo**`_` al principio del nombre para decir: "Esto es interno, no lo uses desde afuera".

::::{admonition} ¿Por Qué "Privado"?
:class: tip

Imaginate que fabricás celulares 📱. Tenés:
- **Botones y pantalla**(público) → Los usuarios los usan
- **Circuitos internos**(privado) → Los usuarios NO deben tocarlos

Lo mismo en programación:
- **Funciones públicas**→ Otros programas las usan
- **Funciones privadas**→ Son ayudantes internos
::::

```{code-block} python
:linenos:
:emphasize-lines: 4,7
:caption: calculadora.py - Con funciones privadas y públicas

"""Módulo calculadora con validación."""

# Variable privada (convención)
# El _ significa: "No uses esto directamente"
_VERSION = "1.0"
_PRECISION = 2

# Función privada (ayudante interno)
def _validar_numero(n):
    """Valida que n sea un número.
    
    Esta es una función INTERNA que usan otras funciones
    del módulo. Los programas externos no deberían llamarla.
    """
    if not isinstance(n, (int, float)):
        raise TypeError(f"Se esperaba un número, se recibió {type(n).__name__}")
    return True

# Función pública (la que otros usan)
def sumar(a, b):
    """Suma dos números después de validarlos.
    
    Esta función ES PÚBLICA. Los programas externos la llaman.
    """
    _validar_numero(a)
    _validar_numero(b)
    return a + b

def dividir(a, b):
    """Divide a entre b con validación."""
    _validar_numero(a)
    _validar_numero(b)
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return round(a / b, _PRECISION)
```

```{code-cell} ipython3
# Uso del módulo
class calculadora:
    _VERSION = "1.0"
    _PRECISION = 2
    
    @staticmethod
    def _validar_numero(n):
        if not isinstance(n, (int, float)):
            raise TypeError(f"Se esperaba un número")
        return True
    
    @staticmethod
    def sumar(a, b):
        calculadora._validar_numero(a)
        calculadora._validar_numero(b)
        return a + b

# ✅ BIEN: Usar funciones públicas
resultado = calculadora.sumar(5, 3)
print(f"5 + 3 = {resultado}")

# EVITAR: Usar funciones privadas
# calculadora._validar_numero(5)  # Funciona, pero NO deberías
```

:::{note}
El `_` es solo una **convención**, no impide el acceso. Es como un cartel que dice "No entrar", pero la puerta no está cerrada con llave. Los buenos programadores respetan esta convención.
:::

### El Bloque Mágico: `if __name__ == "__main__"`

Este es uno de los **conceptos más confusos** para principiantes, ¡pero es súper útil!

::::{admonition} El Problema
:class: tip

Querés que tu módulo pueda hacer **DOS COSAS**:
1. Ser importado por otros programas (como biblioteca)
2. Ejecutarse solo para probar que funciona

```{mermaid}
graph TD
    A[utilidades.py] -->|python utilidades.py| B[Se ejecuta como programa]
    A -->|import utilidades| C[Se importa como módulo]
    B --> D[Corre código de testing]
    C --> E[Solo carga las funciones]
    
    style B fill:#3498db,color:#fff
    style C fill:#27ae60,color:#fff
```
::::

```{code-block} python
:linenos:
:emphasize-lines: 14
:caption: utilidades.py - Módulo ejecutable

"""Módulo de utilidades con funciones de saludo."""

def saludar(nombre):
    """Saluda a una persona con un mensaje amigable."""
    return f"¡Hola, {nombre}! 👋"

def despedir(nombre):
    """Se despide de una persona."""
    return f"¡Adiós, {nombre}! Nos vemos pronto. 👋"

# Este código SOLO se ejecuta si corres el archivo directamente
# NO se ejecuta cuando alguien hace "import utilidades"
if __name__ == "__main__":
    print("=" * 40)
    print("TESTING del módulo utilidades")
    print("=" * 40)
    
    # Probá las funciones
    print(saludar("Ana"))
    print(saludar("Bruno"))
    print(despedir("Carlos"))
    
    print("\n✅ Todas las funciones funcionan correctamente")
```

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} 🏃 Ejecutar Directamente
:class-header: bg-primary text-white

```bash
$ python utilidades.py
```

**Salida:**
```
========================================
TESTING del módulo utilidades
========================================
¡Hola, Ana! 👋
¡Hola, Bruno! 👋
¡Adiós, Carlos! Nos vemos pronto. 👋

✅ Todas las funciones funcionan correctamente
```

El bloque `if __name__ == "__main__":` **SÍ se ejecuta**.
:::

:::{grid-item-card} Importar como Módulo
:class-header: bg-success text-white

```python
import utilidades

print(utilidades.saludar("Diego"))
```

**Salida:**
```
¡Hola, Diego! 👋
```

El bloque `if __name__ == "__main__":` **NO se ejecuta**.
:::
::::

###  ¿Cómo Funciona la Magia?

Cuando Python ejecuta un archivo, define una variable especial llamada `__name__`:

```{list-table}
:header-rows: 1
:name: tabla-name-valores

* - Forma de Ejecutar
  - Valor de `__name__`
  - ¿Ejecuta el bloque?
* - `python archivo.py`
  - `"__main__"`
  - ✅ Sí
* - `import archivo`
  - `"archivo"`
  - ❌ No
```

```{code-cell} ipython3
# Simulación para entender __name__

# Cuando ejecutás el archivo directamente:
nombre_cuando_ejecutas = "__main__"

# Cuando importás el módulo:
nombre_cuando_importas = "nombre_del_modulo"

# El if verifica:
print("Ejecutando directamente:")
if nombre_cuando_ejecutas == "__main__":
    print("  ✅ ¡Se ejecuta el bloque!")

print("\nImportando como módulo:")
if nombre_cuando_importas == "__main__":
    print("  ✅ Se ejecuta el bloque")
else:
    print("  ❌ No se ejecuta el bloque")
```

### Casos de Uso Reales

```{code-block} python
:linenos:
:caption: matematicas.py - Módulo con tests integrados

"""Módulo matemático con auto-testing."""

def factorial(n):
    """Calcula n!"""
    if n <= 1:
        return 1
    return n * factorial(n - 1)

def es_primo(n):
    """Verifica si n es primo."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Bloque de testing
if __name__ == "__main__":
    print("🧪 Testing matematicas.py\n")
    
    # Test 1: Factorial
    print("Test factorial:")
    assert factorial(5) == 120, "❌ Error en factorial(5)"
    assert factorial(0) == 1, "❌ Error en factorial(0)"
    print("  ✅ factorial() funciona correctamente")
    
    # Test 2: Es primo
    print("\nTest es_primo:")
    assert es_primo(7) == True, "❌ 7 debería ser primo"
    assert es_primo(8) == False, "❌ 8 no debería ser primo"
    print("  ✅ es_primo() funciona correctamente")
    
    print("\n¡Todos los tests pasaron!")
```

::::{admonition} Cuándo Usar `if __name__ == "__main__"`
:class: tip

Usá este patrón para:

1. **🧪 Tests rápidos**: Probá tus funciones sin crear otro archivo
2. **Ejemplos de uso**: Mostrá cómo usar tu módulo
3. **🛠️ Herramientas CLI**: Hacé que tu módulo también sea un programa
4. **Debugging**: Código que solo se ejecuta cuando desarrollás

```{code-cell} ipython3
def mi_funcion_util():
    """Una función que otros van a importar."""
    return "¡Funciona!"

# Solo para development/testing
if __name__ == "__main__":
    print("Modo desarrollo")
    print(f"Resultado: {mi_funcion_util()}")
    print("✅ Todo bien")
```
::::

---

---

(paquetes)=
##  Paquetes: Organizando Muchos Módulos

Cuando tenés muchos módulos relacionados, los organizás en **paquetes**. Es como tener un edificio con muchas oficinas. 🏢

```{figure} ./5_modulos/paquete_estructura.svg
:name: fig-paquete-estructura
:align: center
:width: 100%

Estructura de un paquete: carpetas y archivos organizados
```

::::{admonition} ¿Qué es un Paquete?
:class: tip

Un **paquete**es:
- Una **carpeta**(directorio)
- Que contiene **módulos**(archivos `.py`)
- Y un archivo especial **`__init__.py`**(que puede estar vacío)

```{mermaid}
graph TD
    A[ Carpeta] -->|+| B[📄 __init__.py]
    B -->|+| C[📄 modulos.py]
    C -->|=| D[ PAQUETE]
    
    style D fill:#27ae60,color:#fff,stroke:#27ae60,stroke-width:3px
```

Sin `__init__.py`, Python no reconoce la carpeta como paquete.
::::

### Crear un Paquete Paso a Paso

Imaginá que querés crear un paquete de matemáticas con funciones básicas y avanzadas.

**Estructura de carpetas:**

```{code-block} text
:emphasize-lines: 4
mi_proyecto/
├── programa.py              ← Tu programa principal
└── matematicas/             ← Carpeta del paquete
    ├── __init__.py          ← Archivo mágico (marca como paquete)
    ├── basicas.py           ← Módulo con operaciones básicas
    └── avanzadas.py         ← Módulo con operaciones avanzadas
```

### Paso 1: Crear `__init__.py`

El archivo `__init__.py` es la "puerta de entrada" del paquete.

```{code-block} python
:linenos:
:caption: matematicas/__init__.py

"""Paquete de operaciones matemáticas.

Este paquete provee funciones matemáticas organizadas
en módulos temáticos:
- basicas: suma, resta, multiplicación, división
- avanzadas: potencias, raíces, factorial
"""

# Importar funciones de los módulos para acceso directo
from .basicas import sumar, restar, multiplicar, dividir
from .avanzadas import potencia, raiz, factorial

# Metadatos del paquete
__version__ = "1.0.0"
__author__ = "Tu Nombre"

# Definir qué se exporta con "from matematicas import *"
__all__ = ['sumar', 'restar', 'multiplicar', 'dividir',
           'potencia', 'raiz', 'factorial']
```

:::{note}
**El punto `.` en el import**significa "mismo paquete". 
- `.basicas` = en la misma carpeta
- `..otro` = carpeta padre
:::

### Paso 2: Crear Módulo `basicas.py`

```{code-block} python
:linenos:
:caption: matematicas/basicas.py

"""Operaciones matemáticas básicas.

Este módulo contiene las operaciones fundamentales.
"""

def sumar(a, b):
    """Suma dos números.
    
    Args:
        a: Primer número
        b: Segundo número
    
    Returns:
        La suma de a y b
    
    Example:
        >>> sumar(5, 3)
        8
    """
    return a + b

def restar(a, b):
    """Resta dos números."""
    return a - b

def multiplicar(a, b):
    """Multiplica dos números."""
    return a * b

def dividir(a, b):
    """Divide a entre b.
    
    Raises:
        ValueError: Si b es cero.
    """
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b
```

### Paso 3: Crear Módulo `avanzadas.py`

```{code-block} python
:linenos:
:caption: matematicas/avanzadas.py

"""Operaciones matemáticas avanzadas.

Funciones más complejas como potencias y factoriales.
"""

def potencia(base, exponente):
    """Calcula base elevado a exponente.
    
    Example:
        >>> potencia(2, 3)
        8
    """
    return base **exponente

def raiz(numero, indice=2):
    """Calcula la raíz n-ésima de un número.
    
    Args:
        numero: El número del cual calcular la raíz
        indice: El índice de la raíz (default: 2 para raíz cuadrada)
    
    Example:
        >>> raiz(16)      # Raíz cuadrada
        4.0
        >>> raiz(27, 3)   # Raíz cúbica
        3.0
    """
    return numero **(1 / indice)

def factorial(n):
    """Calcula el factorial de n (n!).
    
    Args:
        n: Número entero no negativo
    
    Returns:
        El factorial de n
    
    Raises:
        ValueError: Si n es negativo
    """
    if n < 0:
        raise ValueError("El factorial no está definido para números negativos")
    if n == 0 or n == 1:
        return 1
    
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado
```

### Paso 4: Usar el Paquete

Ahora podés usar tu paquete de varias formas:

::::{tab-set}

:::{tab-item} Forma 1: Import Directo
```{code-block} python
:caption: programa.py
:linenos:

import matematicas

# Gracias a __init__.py, podés acceder directo
print(matematicas.sumar(5, 3))      # 8
print(matematicas.potencia(2, 3))   # 8
print(matematicas.factorial(5))     # 120

# También podés ver la versión
print(f"Versión: {matematicas.__version__}")
```
:::

:::{tab-item} Forma 2: Import de Módulos
```{code-block} python
:caption: programa.py
:linenos:

from matematicas import basicas, avanzadas

# Usar módulos específicos
suma = basicas.sumar(10, 5)
print(f"10 + 5 = {suma}")

potencia = avanzadas.potencia(2, 10)
print(f"2^10 = {potencia}")
```
:::

:::{tab-item} Forma 3: Import de Funciones
```{code-block} python
:caption: programa.py
:linenos:

from matematicas.basicas import sumar, restar
from matematicas.avanzadas import factorial

# Usar funciones directamente
print(sumar(100, 50))      # 150
print(restar(100, 50))     # 50
print(factorial(7))        # 5040
```
:::

:::{tab-item} Forma 4: Import con Alias
```{code-block} python
:caption: programa.py
:linenos:

import matematicas as mat

# Nombre más corto
print(mat.sumar(1, 2))
print(mat.potencia(3, 3))
```
:::
::::

###  Ejemplo Completo Interactivo

```{code-cell} ipython3
# Simulamos el paquete matematicas
class basicas:
    @staticmethod
    def sumar(a, b):
        return a + b
    
    @staticmethod
    def restar(a, b):
        return a - b
    
    @staticmethod
    def multiplicar(a, b):
        return a * b
    
    @staticmethod
    def dividir(a, b):
        if b == 0:
            raise ValueError("División por cero")
        return a / b

class avanzadas:
    @staticmethod
    def potencia(base, exp):
        return base **exp
    
    @staticmethod
    def raiz(num, indice=2):
        return num **(1/indice)
    
    @staticmethod
    def factorial(n):
        if n <= 1:
            return 1
        resultado = 1
        for i in range(2, n + 1):
            resultado *= i
        return resultado

# Programa de ejemplo
print(" CALCULADORA MATEMÁTICA")
print("=" * 50)

print("\nOperaciones Básicas:")
print(f"  15 + 7 = {basicas.sumar(15, 7)}")
print(f"  15 - 7 = {basicas.restar(15, 7)}")
print(f"  15 × 7 = {basicas.multiplicar(15, 7)}")
print(f"  15 ÷ 7 = {basicas.dividir(15, 7):.2f}")

print("\nOperaciones Avanzadas:")
print(f"  2^10 = {avanzadas.potencia(2, 10)}")
print(f"  √16 = {avanzadas.raiz(16)}")
print(f"  ∛27 = {avanzadas.raiz(27, 3)}")
print(f"  5! = {avanzadas.factorial(5)}")

print("\n✅ ¡Paquete funcionando perfectamente!")
```

### Importaciones Relativas

Dentro de un paquete, los módulos pueden importarse entre sí:

```{code-block} python
:caption: matematicas/avanzadas.py
:emphasize-lines: 4,5

"""Operaciones avanzadas con importaciones relativas."""

# Importar del módulo basicas en el mismo paquete
from .basicas import sumar, multiplicar

def promedio(*numeros):
    """Calcula el promedio usando sum del módulo básico."""
    total = sum(numeros)  # Usa la suma de Python
    return total / len(numeros)

def sumatoria_cuadrados(*numeros):
    """Suma los cuadrados de los números."""
    total = 0
    for num in numeros:
        cuadrado = multiplicar(num, num)  # Usa multiplicar del módulo basicas
        total = sumar(total, cuadrado)    # Usa sumar del módulo basicas
    return total
```

::::{admonition} Importaciones Relativas: La Sintaxis
:class: note

- `.modulo` → mismo paquete (hermano)
- `..modulo` → paquete padre
- `..otro_paquete.modulo` → primo (otro paquete del padre)

```{code-block} text
proyecto/
├── paquete1/
│   ├── __init__.py
│   └── modulo_a.py      → from ..paquete2.modulo_b import funcion
└── paquete2/
    ├── __init__.py
    └── modulo_b.py      → from ..paquete1.modulo_a import otra
```
::::


(biblioteca-estandar)=
##  Biblioteca Estándar: Módulos Incluidos

Python viene con **cientos de módulos ya incluidos**. No necesitás instalar nada extra para usarlos. Es como tener una caja de herramientas completa.

::::{admonition} ¿Qué es la Biblioteca Estándar?
:class: tip

La **Python Standard Library** es un conjunto de módulos que vienen con Python:
- Ya instalados (no necesitás pip)
- Mantenidos por el equipo de Python
- Documentación oficial completa
- Funcionan en todas las plataformas

```{mermaid}
graph LR
    A[Python] -->|incluye| B[ Biblioteca Estándar]
    B --> C[math, random, datetime...]
    B --> D[os, sys, pathlib...]
    B --> E[json, csv, re...]
    
    style B fill:#3498db,color:#fff,stroke:#3498db
```
::::

###  `math` - Matemáticas Avanzadas

Para cálculos matemáticos más allá de `+`, `-`, `*`, `/`:

```{code-cell} ipython3
import math

print("Constantes matemáticas:")
print(f"  π (pi) = {math.pi:.10f}")
print(f"  e (euler) = {math.e:.10f}")
print(f"  τ (tau) = {math.tau:.10f}")

print("\nFunciones trigonométricas:")
angulo_grados = 45
angulo_radianes = math.radians(angulo_grados)
print(f"  sen(45°) = {math.sin(angulo_radianes):.4f}")
print(f"  cos(45°) = {math.cos(angulo_radianes):.4f}")
print(f"  tan(45°) = {math.tan(angulo_radianes):.4f}")

print("\n🔺 Raíces y potencias:")
print(f"  √16 = {math.sqrt(16)}")
print(f"  ∛27 = {math.pow(27, 1/3):.2f}")
print(f"  2^10 = {math.pow(2, 10)}")

print("\nRedondeo:")
print(f"  ceil(4.2) = {math.ceil(4.2)}")    # Redondea hacia arriba
print(f"  floor(4.8) = {math.floor(4.8)}")  # Redondea hacia abajo

print("\nLogaritmos:")
print(f"  log₁₀(100) = {math.log10(100)}")
print(f"  ln(e) = {math.log(math.e):.4f}")
```

---

### `random` - Números Aleatorios

Para generar valores aleatorios (juegos, simulaciones, testing):

```{code-cell} ipython3
import random

print("Números aleatorios:")
print(f"  Entero entre 1-100: {random.randint(1, 100)}")
print(f"  Float entre 0-1: {random.random():.4f}")
print(f"  Float entre 10-20: {random.uniform(10, 20):.2f}")

print("\nTrabajar con listas:")
cartas = ["A♠", "K♥", "Q♦", "J♣", "10♠"]
print(f"  Carta aleatoria: {random.choice(cartas)}")

random.shuffle(cartas)
print(f"  Barajar: {cartas}")

print(f"  3 cartas aleatorias: {random.sample(cartas, 3)}")

print("\nEjemplos prácticos:")
# Lanzar una moneda
moneda = random.choice(["Cara", "Cruz"])
print(f"  Lanzar moneda: {moneda}")

# Lanzar un dado
dado = random.randint(1, 6)
print(f"  Lanzar dado: {dado}")

# Probabilidad del 30%
if random.random() < 0.3:
    print(f"  ¡Evento raro ocurrió! (30% probabilidad)")
else:
    print(f"  Evento común (70% probabilidad)")
```

---

### `datetime` - Fechas y Horas

Para trabajar con fechas, horas y duraciones:

```{code-cell} ipython3
from datetime import datetime, date, time, timedelta

print("Fecha y hora actual:")
ahora = datetime.now()
print(f"  Completa: {ahora}")
print(f"  Solo fecha: {ahora.date()}")
print(f"  Solo hora: {ahora.time()}")

print("\nCrear fechas específicas:")
navidad = date(2024, 12, 25)
print(f"  Navidad 2024: {navidad}")
print(f"  Día de la semana: {navidad.strftime('%A')}")

print("\nFormatear fechas:")
print(f"  Formato ISO: {ahora.isoformat()}")
print(f"  Formato legible: {ahora.strftime('%d/%m/%Y %H:%M:%S')}")
print(f"  Formato texto: {ahora.strftime('%A, %d de %B de %Y')}")

print("\nCálculos con fechas:")
hoy = date.today()
manana = hoy + timedelta(days=1)
la_semana_pasada = hoy - timedelta(weeks=1)
en_30_dias = hoy + timedelta(days=30)

print(f"  Hoy: {hoy}")
print(f"  Mañana: {manana}")
print(f"  Hace una semana: {la_semana_pasada}")
print(f"  En 30 días: {en_30_dias}")

print("\nDiferencia entre fechas:")
cumpleanos = date(2024, 6, 15)
diferencia = cumpleanos - hoy
print(f"  Días hasta tu cumpleaños: {abs(diferencia.days)}")
```

---

### `os` - Interactuar con el Sistema Operativo

Para trabajar con archivos, carpetas y el sistema:

```{code-cell} ipython3
import os

print("Información del sistema:")
print(f"  Sistema operativo: {os.name}")
print(f"  Directorio actual: {os.getcwd()}")

print("\n Trabajar con rutas:")
ruta = os.path.join("carpeta", "subcarpeta", "archivo.txt")
print(f"  Ruta construida: {ruta}")
print(f"  Directorio: {os.path.dirname(ruta)}")
print(f"  Nombre archivo: {os.path.basename(ruta)}")

print("\nVerificar existencia:")
print(f"  ¿Existe 'ejemplo.txt'? {os.path.exists('ejemplo.txt')}")
print(f"  ¿Es archivo? {os.path.isfile('ejemplo.txt')}")
print(f"  ¿Es carpeta? {os.path.isdir('ejemplo.txt')}")

print("\nListar archivos:")
archivos = [f for f in os.listdir('.') if f.endswith('.txt')]
print(f"  Archivos .txt: {archivos[:5]}")  # Primeros 5
```

---

### `json` - Trabajar con JSON

JSON es un formato muy usado para guardar y compartir datos:

```{code-cell} ipython3
import json

print(" Convertir Python ↔ JSON\n")

# Datos en Python
persona = {
    "nombre": "Ana García",
    "edad": 25,
    "ciudad": "Buenos Aires",
    "hobbies": ["leer", "programar", "viajar"],
    "activo": True
}

# Convertir a JSON (string)
json_string = json.dumps(persona, indent=2, ensure_ascii=False)
print("Python dict → JSON string:")
print(json_string)

# Convertir de JSON a Python
datos_recuperados = json.loads(json_string)
print(f"\nJSON string → Python dict:")
print(f"Nombre: {datos_recuperados['nombre']}")
print(f"Hobbies: {', '.join(datos_recuperados['hobbies'])}")

# Guardar en archivo
print("\n Guardar en archivo JSON:")
with open("persona.json", "w", encoding="utf-8") as archivo:
    json.dump(persona, archivo, indent=2, ensure_ascii=False)
print("Guardado en 'persona.json'")

# Leer desde archivo
print("\nLeer desde archivo JSON:")
with open("persona.json", "r", encoding="utf-8") as archivo:
    persona_cargada = json.load(archivo)
print(f"Cargado: {persona_cargada['nombre']}, {persona_cargada['edad']} años")
```

---

### `re` - Expresiones Regulares

Para buscar patrones complejos en texto:

```{code-cell} ipython3
import re

texto = """
Contactos:
- Juan: juan@email.com (011-1234-5678)
- María: maria@company.org (011-8765-4321)
- Pedro: pedro.gomez@mail.net (011-5555-1234)
"""

print("Buscar emails:")
emails = re.findall(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b', texto)
for email in emails:
    print(f"    {email}")

print("\n📞 Buscar teléfonos:")
telefonos = re.findall(r'\(\d{3}-\d{4}-\d{4}\)', texto)
for tel in telefonos:
    print(f"    {tel}")

print("\nReemplazar texto:")
texto_limpio = re.sub(r'\(\d{3}-\d{4}-\d{4}\)', '[TELÉFONO]', texto)
print(texto_limpio)
```

---

(resumen-modulos)=
## Resumen del Capítulo

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} Módulos
:class-header: bg-primary text-white

**Definición:**Archivo `.py` con funciones reutilizables

**Usar:**
```python
import modulo
from modulo import funcion
```

**Crear:**Escribir funciones en un archivo `.py`
:::

:::{grid-item-card} Paquetes
:class-header: bg-info text-white

**Definición:**Carpeta con módulos + `__init__.py`

**Estructura:**
```
paquete/
├── __init__.py
├── modulo1.py
└── modulo2.py
```
:::

:::{grid-item-card} Archivos
:class-header: bg-success text-white

**Leer:**
```python
with open("archivo.txt", "r") as f:
    contenido = f.read()
```

**Escribir:**
```python
with open("archivo.txt", "w") as f:
    f.write("datos")
```
:::

:::{grid-item-card} Biblioteca Estándar
:class-header: bg-warning

**Módulos útiles:**
- `math`: matemáticas
- `random`: aleatorios
- `datetime`: fechas
- `os`: sistema operativo
- `json`: formato JSON
:::
::::

---

## Conceptos Clave

```{admonition} Lo Más Importante
:class: tip

1. **Módulos = Reutilización**: Escribí código una vez, usalo muchas veces
2. **`import`**: Trae código de otros archivos
3. **Paquetes = Organización**: Agrupa módulos relacionados
4. **`with open()`**: SIEMPRE usá esto para archivos (cierre automático)
5. **Biblioteca Estándar**: Explorá los módulos incluidos antes de buscar externas
```

---

## Checklist de Aprendizaje

Verificá que podés hacer esto:

- [ ] Crear un módulo con funciones propias
- [ ] Importar y usar funciones de un módulo
- [ ] Entender `if __name__ == "__main__"`
- [ ] Crear un paquete con `__init__.py`
- [ ] Leer un archivo de texto con `with open()`
- [ ] Escribir datos en un archivo
- [ ] Usar modo append para agregar sin borrar
- [ ] Manejar errores al trabajar con archivos
- [ ] Usar módulos de la biblioteca estándar (`math`, `random`, etc.)
- [ ] Guardar y cargar datos en formato JSON

---

## Ejercicios Propuestos

::::{admonition} Práctica Guiada
:class: note

### Ejercicio 1: Mi Primer Módulo
Creá un módulo `calculadora.py` con funciones para:
- Sumar, restar, multiplicar, dividir
- Calcular promedio de una lista
- Encontrar el máximo de una lista

Luego creá un programa que lo importe y use.

### Ejercicio 2: Sistema de Tareas
Creá un programa que:
- Permita agregar tareas a un archivo `tareas.txt`
- Liste todas las tareas
- Marque tareas como completadas
- Guarde todo en formato JSON

### Ejercicio 3: Analizador de Texto
Creá un programa que:
- Lea un archivo de texto
- Cuente palabras, líneas y caracteres
- Encuentre la palabra más usada
- Guarde las estadísticas en un archivo JSON

### Ejercicio 4: Mini Juego
Creá un juego de adivinanza que:
- Genere un número aleatorio
- Guarde el historial de partidas en un archivo
- Muestre estadísticas (mejor puntaje, promedio, etc.)
::::

---

## 🎊 ¡Felicitaciones!

¡Completaste el capítulo de Módulos y Archivos! Ahora sabés:

Organizar código en módulos y paquetes  
Reutilizar código eficientemente  
Leer y escribir archivos de forma segura  
Usar la potente Biblioteca Estándar de Python  

**Próximo paso:**¡Seguí practicando y explorando más módulos de la biblioteca estándar!

```python
print("Procesando línea por línea:")
with open("ejemplo.txt", "r") as archivo:
    for numero, linea in enumerate(archivo, 1):
        linea_limpia = linea.strip()
        print(f"  Línea {numero}: '{linea_limpia}' ({len(linea_limpia)} chars)")
```

**Cuándo usar:**
- **SIEMPRE para archivos grandes**(lee de a poco)
- Solo necesitás procesar una vez
- No necesitás guardar todas las líneas en memoria

:::
::::

::::{admonition} Guía de Elección Rápida
:class: tip

| Archivo | Acción | Método Recomendado |
|---------|--------|--------------------|
| Pequeño (< 10 MB) | Leer todo | `.read()` o `.readlines()` |
| Grande (> 10 MB) | Procesar línea por línea | `for linea in archivo` |
| Cualquiera | Leer N líneas específicas | `.readline()` |
| Cualquiera | Buscar algo específico | `for linea in archivo` |
::::

### Escribir Archivos: Tres Formas

::::{tab-set}

:::{tab-item} `.write()` - String Individual
:sync: write

**Escribe un string al archivo.**

```{code-cell} ipython3
# Escribir línea por línea
with open("salida.txt", "w") as archivo:
    archivo.write("Primera línea\n")  # ¡Recordá el \n!
    archivo.write("Segunda línea\n")
    archivo.write("Tercera línea\n")

# Leer para verificar
with open("salida.txt", "r") as archivo:
    print(archivo.read())
```

:::{warning}
¡`write()` NO agrega saltos de línea automáticamente! Tenés que agregar `\n` vos mismo.
:::

:::

:::{tab-item} `.writelines()` - Lista de Strings
:sync: writelines

**Escribe una lista de strings.**

```{code-cell} ipython3
# Preparar lista de líneas
lineas = [
    "Línea 1\n",
    "Línea 2\n",
    "Línea 3\n"
]

# Escribir todas a la vez
with open("salida2.txt", "w") as archivo:
    archivo.writelines(lineas)

# Verificar
with open("salida2.txt", "r") as archivo:
    print(archivo.read())
```

:::{warning}
`writelines()` tampoco agrega `\n` automáticamente. Tenés que incluirlos en cada string.
:::

:::

:::{tab-item} Modo "a" - Append (Agregar)
:sync: append

**Agrega al final sin borrar lo existente.**

```{code-cell} ipython3
# Crear archivo inicial
with open("log.txt", "w") as archivo:
    archivo.write("Log inicio: 10:00\n")

# Agregar más entradas
with open("log.txt", "a") as archivo:  # Nota el modo "a"
    archivo.write("Log evento: 10:15\n")
    archivo.write("Log evento: 10:30\n")

# Ver todo el log
with open("log.txt", "r") as archivo:
    print("Contenido del log:")
    print(archivo.read())
```

**Perfecto para:**
- Logs y registros
- Agregar datos sin perder los anteriores
-  Archivos que crecen con el tiempo

:::
::::

### Ejemplos Prácticos Completos

::::{dropdown} Ejemplo 1: Sistema de Notas

```{code-cell} ipython3
def guardar_notas(estudiantes, archivo="notas.txt"):
    """Guarda las notas de estudiantes en un archivo."""
    with open(archivo, "w") as f:
        f.write("REGISTRO DE NOTAS\n")
        f.write("=" * 40 + "\n")
        for nombre, nota in estudiantes.items():
            f.write(f"{nombre}: {nota}\n")
        f.write("=" * 40 + "\n")

def leer_notas(archivo="notas.txt"):
    """Lee y muestra las notas."""
    try:
        with open(archivo, "r") as f:
            contenido = f.read()
            print(contenido)
    except FileNotFoundError:
        print(f"❌ El archivo {archivo} no existe")

# Usar las funciones
notas = {
    "Ana": 9,
    "Bruno": 8,
    "Carlos": 10,
    "Diana": 7
}

print(" Guardando notas...")
guardar_notas(notas)

print("\nLeyendo notas:")
leer_notas()
```
::::

::::{dropdown} Ejemplo 2: Procesar Archivo Grande

```{code-cell} ipython3
def procesar_archivo_grande(archivo_entrada, archivo_salida):
    """Procesa un archivo línea por línea (eficiente para archivos grandes)."""
    
    lineas_procesadas = 0
    
    with open(archivo_entrada, "r") as entrada:
        with open(archivo_salida, "w") as salida:
            for linea in entrada:
                # Procesar línea: convertir a mayúsculas
                linea_procesada = linea.upper()
                salida.write(linea_procesada)
                lineas_procesadas += 1
    
    return lineas_procesadas

# Crear archivo de ejemplo
with open("datos.txt", "w") as f:
    f.write("primera línea\n")
    f.write("segunda línea\n")
    f.write("tercera línea\n")

# Procesar
n = procesar_archivo_grande("datos.txt", "datos_procesados.txt")
print(f"✅ Procesadas {n} líneas")

# Ver resultado
with open("datos_procesados.txt", "r") as f:
    print("\n📄 Resultado:")
    print(f.read())
```
::::

---

### Verificar si un Archivo Existe

Antes de intentar leer un archivo, es buena práctica verificar que exista. ¡Así evitás errores! 

```{code-cell} ipython3
import os

# Verificar existencia
archivo = "datos.txt"
if os.path.exists(archivo):
    print(f"✅ El archivo '{archivo}' existe")
    with open(archivo, "r") as f:
        print(f.read())
else:
    print(f"❌ El archivo '{archivo}' no existe")
    print("Creándolo...")
    with open(archivo, "w") as f:
        f.write("Archivo creado\n")
```

::::{tab-set}

:::{tab-item} os.path.exists()
Verifica si existe (archivo O carpeta)

```{code-cell} ipython3
import os

cosas_a_verificar = ["ejemplo.txt", "carpeta_inexistente", "5_modulos"]

for cosa in cosas_a_verificar:
    if os.path.exists(cosa):
        print(f"✅ '{cosa}' existe")
    else:
        print(f"❌ '{cosa}' NO existe")
```
:::

:::{tab-item} os.path.isfile()
Verifica si es un ARCHIVO

```{code-cell} ipython3
import os

# Crear archivo de prueba
with open("prueba.txt", "w") as f:
    f.write("test")

print(f"¿'prueba.txt' es archivo? {os.path.isfile('prueba.txt')}")
print(f"¿'5_modulos' es archivo? {os.path.isfile('5_modulos')}")  # Carpeta, no archivo
```
:::

:::{tab-item} os.path.isdir()
Verifica si es una CARPETA

```{code-cell} ipython3
import os

print(f"¿'5_modulos' es carpeta? {os.path.isdir('5_modulos')}")
print(f"¿'prueba.txt' es carpeta? {os.path.isdir('prueba.txt')}")  # Archivo, no carpeta
```
:::

:::{tab-item} os.path.getsize()
Obtiene el tamaño del archivo

```{code-cell} ipython3
import os

if os.path.exists("prueba.txt"):
    tamaño = os.path.getsize("prueba.txt")
    print(f"Tamaño de 'prueba.txt': {tamaño} bytes")
```
:::
::::

###  Ejemplo Completo: Sistema de Gestión de Nombres

Un sistema que guarda y carga listas de nombres con manejo de errores.

```{code-cell} ipython3
import os

def guardar_nombres(nombres, archivo="nombres.txt"):
    """Guarda una lista de nombres en un archivo.
    
    Args:
        nombres: Lista de strings con los nombres.
        archivo: Nombre del archivo donde guardar (default: "nombres.txt").
    
    Example:
        >>> guardar_nombres(["Ana", "Bruno"], "alumnos.txt")
    """
    try:
        with open(archivo, "w", encoding="utf-8") as f:
            for nombre in nombres:
                f.write(nombre + "\n")
        print(f"✅ Guardados {len(nombres)} nombres en '{archivo}'")
        return True
    except Exception as e:
        print(f"❌ Error al guardar: {e}")
        return False

def cargar_nombres(archivo="nombres.txt"):
    """Carga nombres desde un archivo.
    
    Args:
        archivo: Nombre del archivo a leer.
    
    Returns:
        Lista de nombres. Lista vacía si el archivo no existe.
    
    Example:
        >>> nombres = cargar_nombres("alumnos.txt")
    """
    if not os.path.exists(archivo):
        print(f"ℹ️ El archivo '{archivo}' no existe. Retornando lista vacía.")
        return []
    
    try:
        with open(archivo, "r", encoding="utf-8") as f:
            # Leer líneas y quitar espacios/saltos de línea
            nombres = [linea.strip() for linea in f if linea.strip()]
        print(f"✅ Cargados {len(nombres)} nombres desde '{archivo}'")
        return nombres
    except Exception as e:
        print(f"❌ Error al cargar: {e}")
        return []

def agregar_nombre(nombre, archivo="nombres.txt"):
    """Agrega un nombre al final del archivo sin borrar los anteriores.
    
    Args:
        nombre: El nombre a agregar.
        archivo: Nombre del archivo.
    """
    try:
        with open(archivo, "a", encoding="utf-8") as f:
            f.write(nombre + "\n")
        print(f"✅ Agregado '{nombre}' a '{archivo}'")
        return True
    except Exception as e:
        print(f"❌ Error al agregar: {e}")
        return False

# 🎮 Demo del sistema
print("=== SISTEMA DE GESTIÓN DE NOMBRES ===\n")

# Paso 1: Guardar nombres iniciales
print("Paso 1: Guardar nombres iniciales")
nombres_iniciales = ["Ana García", "Bruno López", "Carlos Pérez"]
guardar_nombres(nombres_iniciales, "alumnos.txt")

# Paso 2: Cargar nombres
print("\nPaso 2: Cargar nombres")
nombres_cargados = cargar_nombres("alumnos.txt")
print(f"Nombres: {nombres_cargados}")

# Paso 3: Agregar un nombre nuevo
print("\n➕ Paso 3: Agregar nombre nuevo")
agregar_nombre("Diana Martínez", "alumnos.txt")

# Paso 4: Cargar de nuevo para ver todos
print("\nPaso 4: Ver todos los nombres actualizados")
todos_los_nombres = cargar_nombres("alumnos.txt")
for i, nombre in enumerate(todos_los_nombres, 1):
    print(f"  {i}. {nombre}")
```

::::{admonition} Buenas Prácticas en el Ejemplo
:class: tip

Fijate estas buenas prácticas en el código:

1. **`encoding="utf-8"`**: Para que funcionen acentos y ñ
2. **`try-except`**: Manejo de errores para evitar crashes
3. **Verificar existencia**: Con `os.path.exists()` antes de leer
4. **Documentación completa**: Docstrings con Args, Returns, Example
5. **`.strip()`**: Limpiar espacios y saltos de línea
6. **Mensajes descriptivos**: El usuario sabe qué está pasando
:::

---

##  Excepciones: Manejo de Errores

Los programas no siempre funcionan perfectamente. Los usuarios ingresan datos incorrectos, los archivos no existen, la red falla... **Las excepciones te permiten manejar estos errores elegantemente**sin que tu programa se rompa. 

::::{admonition} ¿Qué es una Excepción?
:class: tip

Una **excepción** es un error que ocurre **durante la ejecución**del programa. Es como cuando manejás un auto 🚗 y aparece un obstáculo en el camino:

- **Sin manejo**: Chocás y el auto se destruye (programa crashea) 
- **Con manejo**: Esquivás el obstáculo y seguís manejando (programa continúa) ✅

```{mermaid}
graph LR
    A[Código] -->|Error| B{¿Manejado?}
    B -->|No| C[ Crash<br/>Programa termina]
    B -->|Sí| D[✅ Continúa<br/>Programa sigue]
    
    style C fill:#e74c3c,color:#fff
    style D fill:#27ae60,color:#fff
```
::::

```{figure} ./5_modulos/excepciones_flujo.svg
:name: fig-excepciones-flujo
:align: center
:width: 100%

Flujo de ejecución con y sin manejo de excepciones
```

###  Tipos Comunes de Excepciones

Python tiene muchos tipos de excepciones. Cada una representa un error diferente.

```{figure} ./5_modulos/excepciones_comunes.svg
:name: fig-excepciones-comunes
:align: center
:width: 100%

Las excepciones más comunes en Python y cómo solucionarlas
```

::::{tab-set}

:::{tab-item} ValueError
:sync: valueerror

**Valor inapropiado para el tipo esperado.**

```{code-cell} ipython3
# Problema: Intentar convertir algo que no es un número
try:
    numero = int("abc")  # "abc" no es un número válido
except ValueError as e:
    print(f"❌ Error: {e}")
    print("Solución: Validar antes o pedir input correcto")

# Solución
texto = "abc"
if texto.isdigit():
    numero = int(texto)
else:
    print("No es un número válido")
```

**Casos comunes:**
- `int("hola")` → No se puede convertir
- `float("xyz")` → No es un número
- `datetime.strptime("invalid", "%Y-%m-%d")` → Formato incorrecto
:::

:::{tab-item} TypeError
:sync: typeerror

**Operación con tipos incompatibles.**

```{code-cell} ipython3
# Problema: Sumar string + número
try:
    resultado = "5" + 3
except TypeError as e:
    print(f"❌ Error: {e}")
    print("Solución: Convertir todo al mismo tipo")

# Solución 1: Convertir a número
resultado = int("5") + 3
print(f"✅ Como números: {resultado}")

# Solución 2: Convertir a string
resultado = "5" + str(3)
print(f"✅ Como strings: {resultado}")
```

**Casos comunes:**
- `"texto" + 5` → No se pueden sumar diferentes tipos
- `len(42)` → len() necesita una secuencia
- `sorted(5)` → sorted() necesita un iterable
:::

:::{tab-item} KeyError
:sync: keyerror

**Clave no existe en el diccionario.**

```{code-cell} ipython3
# Problema: Acceder a clave inexistente
estudiante = {"nombre": "Ana", "edad": 20}

try:
    carrera = estudiante["carrera"]  # "carrera" no existe
except KeyError as e:
    print(f"❌ Error: La clave {e} no existe")
    print("Solución: Usar .get() o verificar antes")

# Solución 1: Usar .get() con valor por defecto
carrera = estudiante.get("carrera", "No especificada")
print(f"✅ Carrera: {carrera}")

# Solución 2: Verificar si existe
if "carrera" in estudiante:
    carrera = estudiante["carrera"]
else:
    print("✅ Clave no existe, usando default")
```
:::

:::{tab-item} IndexError
:sync: indexerror

**Índice fuera de rango.**

```{code-cell} ipython3
# Problema: Acceder a índice que no existe
lista = [10, 20, 30]  # Índices válidos: 0, 1, 2

try:
    elemento = lista[10]  # No hay índice 10
except IndexError as e:
    print(f"❌ Error: {e}")
    print(f"La lista solo tiene {len(lista)} elementos")

# Solución: Verificar longitud
indice = 10
if indice < len(lista):
    elemento = lista[indice]
else:
    print(f"✅ Índice {indice} fuera de rango (0-{len(lista)-1})")
```
:::

:::{tab-item} FileNotFoundError
:sync: filenotfounderror

**Archivo no existe.**

```{code-cell} ipython3
# Problema: Intentar abrir archivo inexistente
try:
    with open("archivo_inexistente.txt", "r") as f:
        contenido = f.read()
except FileNotFoundError as e:
    print(f"❌ Error: {e}")
    print("Solución: Verificar existencia antes")

# Solución: Verificar con os.path.exists()
import os

archivo = "archivo_inexistente.txt"
if os.path.exists(archivo):
    with open(archivo, "r") as f:
        contenido = f.read()
else:
    print(f"✅ El archivo '{archivo}' no existe, creándolo...")
    with open(archivo, "w") as f:
        f.write("Contenido inicial\n")
```
:::

:::{tab-item} ZeroDivisionError
:sync: zerodivisionerror

**División por cero.**

```{code-cell} ipython3
# Problema: Dividir por cero
try:
    resultado = 10 / 0
except ZeroDivisionError as e:
    print(f"❌ Error: {e}")
    print("Solución: Verificar divisor antes")

# Solución: Validar antes de dividir
def dividir_seguro(a, b):
    if b == 0:
        print("No se puede dividir por cero, retornando None")
        return None
    return a / b

print(f"✅ 10 / 0 = {dividir_seguro(10, 0)}")
print(f"✅ 10 / 2 = {dividir_seguro(10, 2)}")
```
:::
::::

::::{admonition} Jerarquía de Excepciones
:class: note dropdown

Todas las excepciones heredan de `Exception`. Esto te permite capturar grupos:

```{code-cell} ipython3
try:
    # Código que puede fallar
    resultado = int(input("Número: "))
except ValueError:
    print("Error de valor")
except Exception as e:  # Captura cualquier otra excepción
    print(f"Otro error: {e}")
```

**Jerarquía común:**
```
BaseException
└── Exception
    ├── ValueError
    ├── TypeError
    ├── KeyError
    ├── IndexError
    ├── FileNotFoundError
    ├── ZeroDivisionError
    └── ...
```
::::

### Try-Except

```python
try:
    # Código que puede generar error
    numero = int(input("Ingrese un número: "))
    resultado = 10 / numero
    print(f"Resultado: {resultado}")
except ValueError:
    print("Error: debe ingresar un número válido")
except ZeroDivisionError:
    print("Error: no se puede dividir por cero")
```

### Try-Except-Else-Finally

```{code-cell} ipython3
try:
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    print("El archivo no existe")
else:
    # Se ejecuta si NO hubo excepción
    print(f"Archivo leído: {len(contenido)} caracteres")
finally:
    # SIEMPRE se ejecuta (con o sin excepción)
    if 'archivo' in locals():
        archivo.close()
        print("Archivo cerrado")
```

### Capturar Múltiples Excepciones

```python
try:
    numero = int(input("Número: "))
    resultado = 10 / numero
except (ValueError, ZeroDivisionError) as e:
    print(f"Error: {e}")
```

### Capturar la Excepción

```python
try:
    numero = int(input("Número: "))
except ValueError as error:
    print(f"Error específico: {error}")
    print(f"Tipo de error: {type(error)}")
```

### Lanzar Excepciones

```{code-cell} ipython3
def dividir(a, b):
    """Divide a entre b.
    
    Args:
        a: Dividendo.
        b: Divisor.
    
    Returns:
        El resultado de la división.
    
    Raises:
        ValueError: Si b es cero.
        TypeError: Si a o b no son números.
    """
    if not isinstance(a, (int, float)) or not isinstance(b, (int, float)):
        raise TypeError("Los argumentos deben ser números")
    
    if b == 0:
        raise ValueError("El divisor no puede ser cero")
    
    return a / b

# Uso
try:
    resultado = dividir(10, 0)
except ValueError as e:
    print(f"Error: {e}")
```

### Excepciones Personalizadas

```{code-cell} ipython3
class EdadInvalidaError(Exception):
    """Excepción para edad inválida."""
    pass

def validar_edad(edad):
    """Valida que la edad esté en rango válido.
    
    Args:
        edad: La edad a validar.
    
    Raises:
        EdadInvalidaError: Si la edad es inválida.
    """
    if edad < 0 or edad > 120:
        raise EdadInvalidaError(f"Edad inválida: {edad}")
    return True

# Uso
try:
    validar_edad(-5)
except EdadInvalidaError as e:
    print(f"Error de validación: {e}")
```

:::{important} Cuándo usar excepciones
Usá excepciones para:
- Manejar errores que podés anticipar
- Validar entrada del usuario
- Operaciones con archivos/red
- Conversiones de tipos

NO uses excepciones para:
- Control de flujo normal
- Validaciones que podés hacer con `if`
- Situaciones esperadas y frecuentes
:::

---

(ejemplo-completo)=
## Buenas Prácticas

### 1. Organización de Imports

```{code-cell} ipython3
# ✓ Orden correcto
# 1. Biblioteca estándar
import os
import sys
from datetime import datetime

# 2. Bibliotecas de terceros
import numpy as np
import requests

# 3. Módulos locales
from mi_paquete import mi_modulo
from .utilidades import funcion_util
```

### 2. Estructura de Módulos

```{code-cell} ipython3
"""Docstring del módulo.

Descripción más detallada de lo que hace el módulo.
"""

# Imports
import os
import sys

# Constantes
VERSION = "1.0.0"
DEBUG = False

# Funciones y clases
def mi_funcion():
    """Docstring de la función."""
    pass

class MiClase:
    """Docstring de la clase."""
    pass

# Código principal (si aplica)
if __name__ == "__main__":
    # Código de testing o ejemplos
    pass
```

### 3. Nombrar Módulos y Paquetes

```{code-cell} ipython3
# ✓ Buenos nombres (snake_case, descriptivos)
mi_modulo.py
utilidades_texto.py
procesador_datos.py

# ❌ Malos nombres
Modulo.py
mod.py
m.py
```

### 4. Documentar Módulos

```{code-cell} ipython3
"""Módulo de utilidades matemáticas.

Este módulo proporciona funciones para operaciones matemáticas
comunes que no están en la biblioteca estándar.

Ejemplo:
    >>> from matematicas import promedio
    >>> promedio([1, 2, 3, 4, 5])
    3.0

Atributos:
    PI (float): Constante pi con 5 decimales.
    E (float): Constante e (número de Euler).
"""

PI = 3.14159
E = 2.71828

def promedio(numeros):
    """Calcula el promedio de una lista."""
    pass
```

### 5. Manejo de Archivos Robusto

```{code-cell} ipython3
def leer_archivo_seguro(nombre_archivo):
    """Lee un archivo de forma segura.
    
    Args:
        nombre_archivo: Ruta del archivo.
    
    Returns:
        Contenido del archivo o None si hay error.
    """
    try:
        with open(nombre_archivo, "r", encoding="utf-8") as f:
            return f.read()
    except FileNotFoundError:
        print(f"Error: {nombre_archivo} no existe")
        return None
    except PermissionError:
        print(f"Error: sin permisos para leer {nombre_archivo}")
        return None
    except Exception as e:
        print(f"Error inesperado: {e}")
        return None
```

---

(ejercicios-modulos)=
## Ejercicios

(ejercicio-5-1)=
### Ejercicio 5.1: Módulo de Validaciones

Creá un módulo `validaciones.py` con funciones para validar datos comunes.

**Funciones a implementar:**
```{code-cell} ipython3
def validar_email(email):
    """Valida formato de email."""
    pass

def validar_telefono(telefono):
    """Valida que tenga 10 dígitos."""
    pass

def validar_dni(dni):
    """Valida DNI argentino (7-8 dígitos)."""
    pass

def validar_codigo_postal(cp):
    """Valida código postal (4 dígitos)."""
    pass
```

Luego creá un programa que use estas funciones para validar un formulario.

---

(ejercicio-5-2)=

(ejercicio-5-3)=
(ejercicio-5-5)=
### Ejercicio 5.5: Biblioteca de Funciones

Organizá funciones en un paquete estructurado.

**Estructura:**
```
mi_biblioteca/
    __init__.py
    matematicas/
        __init__.py
        basicas.py
        estadisticas.py
    texto/
        __init__.py
        procesamiento.py
        validacion.py
```

Implementá al menos 3 funciones en cada módulo.

---

(ejercicio-5-6)=

Mejorá el conversor de temperaturas del capítulo de funciones:
- Organizalo en módulos separados
- Guardá conversiones en un archivo de log
- Maneja excepciones (temperaturas inválidas)
- Permite cargar temperatura desde archivo

---

(ejercicio-5-9)=

---

(uso-ia-modulos)=
## Uso Ético y Efectivo de la IA en Módulos

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Entender cómo organizar código en módulos y usar bibliotecas es esencial para proyectos reales. La IA puede ayudarte a explorar la biblioteca estándar, pero **vos debés entender la estructura modular**de tu proyecto.
:::

### Buenas Prácticas para Módulos

#### Generar Ejercicios Adicionales

- *"Genera ejercicios sobre creación de módulos con funciones relacionadas"*
- *"Crea problemas que requieran usar módulos de la biblioteca estándar como `math` o `random`"*
- *"Dame ejercicios de organización de código en múltiples archivos"*

#### Obtener Pistas sobre Organización

- *"Tengo un programa grande. ¿Cómo decido qué funciones van en qué módulo?"*
- *"¿Cuándo debería crear un paquete (con `__init__.py`) versus solo módulos separados?"*
- *"Tengo funciones relacionadas con cálculos matemáticos y otras con entrada/salida. ¿Cómo las organizo?"*

#### Explorar la Biblioteca Estándar

- *"Necesito generar números aleatorios. ¿Qué módulo de Python me ayuda y cómo se usa?"*
- *"¿Qué funciones del módulo `math` son más útiles para cálculos básicos?"*
- *"Quiero trabajar con fechas y horas. ¿Qué módulo debería usar?"*

#### Debugging de Imports

- *"Obtengo `ModuleNotFoundError` al intentar importar mi módulo. ¿Qué estoy haciendo mal?"*
- *"Mi importación funciona en el intérprete pero no cuando ejecuto el script. ¿Por qué?"*
- *"¿Cuál es la diferencia entre `import math` y `from math import sqrt`?"*

#### Buenas Prácticas de Imports

- *"¿Es mala práctica hacer `from modulo import *`? ¿Por qué?"*
- *"¿En qué orden debería organizar mis imports? ¿Importo primero bibliotecas estándar o mis propios módulos?"*
- *"¿Debería importar funciones específicas o el módulo completo?"*

### Ejemplos Específicos de este Módulo

**Situación 1**: Exploración de biblioteca estándar

❌ **Incorrecto**:
```
Prompt: "Dame código que calcule raíz cuadrada, seno y coseno de un número."
```

✅ **Correcto**:
```
Prompt: "Necesito calcular funciones matemáticas avanzadas.
Sé que existe el módulo `math`, pero no sé qué funciones tiene disponibles.
¿Podrías darme una lista de las más comunes con ejemplos breves?"
```

**Situación 2**: Organización de proyecto

❌ **Incorrecto**:
```
Prompt: "Organiza mi programa en módulos por mí."
```

✅ **Correcto**:
```
Prompt: "Estoy organizando un programa de gestión de estudiantes.
Identifiqué estos grupos de funciones:
- Validación de datos (DNI, email, edad)
- Cálculos (promedios, estadísticas)
- Entrada/Salida (menús, archivos)

¿Es buena esta división? ¿Cómo los nombro?"
```

### Exploración Segura de Bibliotecas

:::{tip} Cómo aprender nuevas bibliotecas con IA
1. **Pregunta por el propósito**: *"¿Para qué se usa el módulo X?"*
2. **Pide ejemplos simples**: *"Dame un ejemplo básico de uso del módulo X"*
3. **Explora gradualmente**: *"¿Qué otras funciones útiles tiene?"*
4. **Prueba por tu cuenta**: Escribe código probando lo que aprendiste
5. **Busca documentación oficial**: La IA puede errar, la documentación es la verdad

**No saltes directamente a copiar código complejo**sin entender lo básico.
:::

### Uso Avanzado: Revisión de Estructura

Después de organizar tu código en módulos:

```
Prompt: "Organicé mi proyecto así:
- modulo_validaciones.py: Funciones de validación de datos
- modulo_calculos.py: Cálculos matemáticos y estadísticos
- modulo_io.py: Entrada/salida y menús
- main.py: Programa principal

¿Esta estructura tiene sentido? ¿Los nombres son apropiados?
¿Hay algo que esté en el módulo equivocado?"
```

### Errores Comunes en este Módulo

:::{warning} No copies código que usa bibliotecas que no entendés
Es tentador copiar código que "funciona" usando bibliotecas complejas. Pero si no entendés:

- **Para qué**sirve la biblioteca
- **Cómo**funcionan las funciones que usás
- **Por qué**ese código resuelve el problema

Entonces **no estás aprendiendo**, solo estás copiando.

**Aprendé las bases primero**, luego explora bibliotecas avanzadas.
:::

### Documentación Oficial

Recordá que Python tiene **excelente documentación oficial**:

- [Biblioteca Estándar de Python](https://docs.python.org/3/library/)
- [Módulo math](https://docs.python.org/3/library/math.html)
- [Módulo random](https://docs.python.org/3/library/random.html)
- [Módulo datetime](https://docs.python.org/3/library/datetime.html)

La IA es útil para **explicaciones rápidas**, pero la documentación oficial es **la fuente de verdad**.

---

## Resumen

En este capítulo aprendiste sobre modularización:

✓ **Importar módulos**: Biblioteca estándar, alias, buenas prácticas  
✓ **Crear módulos**: Archivos .py, variables privadas, `__name__`  
✓ **Paquetes**: Organizar módulos, `__init__.py`, importaciones relativas  
✓ **Excepciones**: Try-except, tipos comunes, crear propias  
✓ **Buenas prácticas**: Organización, documentación, manejo robusto  

La modularización es clave para crear programas grandes y mantenibles. Te permite:
- Dividir código en partes lógicas y reutilizables
- Colaborar eficientemente en equipo
- Mantener y actualizar código fácilmente
- Aprovechar código de otros (bibliotecas)

Los módulos son la base de todo el ecosistema de Python. La vasta cantidad de bibliotecas disponibles (NumPy, Pandas, Django, Flask, etc.) son todas módulos y paquetes que otros programadores han creado y compartido.

Al dominar la modularización, no solo escribís mejor código, sino que podés contribuir a la comunidad Python creando tus propias bibliotecas.
:::

---

## Conclusión del Curso

¡Felicitaciones! Has completado el curso de ingreso a Ingeniería en Computación.

A lo largo de estos 5 capítulos, has aprendido:

1. **Fundamentos**: Variables, tipos, operadores, I/O
2. **Control de Flujo**: Condicionales, loops, patrones
3. **Estructuras de Datos**: Listas, tuplas, dicts, sets
4. **Funciones**: Modularización, scope, documentación
5. **Módulos y Archivos**: Organización, persistencia, excepciones

Con estas herramientas, podés:
- Escribir programas Python completos y funcionales
- Resolver problemas algorítmicos complejos
- Organizar código de forma profesional
- Trabajar con datos persistentes
- Manejar errores elegantemente
- Documentar y mantener código
- Continuar aprendiendo de forma autónoma

:::{tip} Próximos pasos
Para seguir creciendo como programador:
1. Practicá resolviendo los ejercicios de todos los capítulos
2. Leé código de otros programadores (GitHub, proyectos open source)
3. Contribuí a proyectos open source
4. Aprendé bibliotecas especializadas según tu interés:
   - **Ciencia de datos**: NumPy, Pandas, Matplotlib
   - **Web**: Flask, Django, FastAPI
   - **Automatización**: Selenium, BeautifulSoup
   - **Machine Learning**: scikit-learn, TensorFlow
5. Construí proyectos propios
6. Seguí aprendiendo: estructuras de datos avanzadas, algoritmos, diseño de software

¡El viaje de aprendizaje nunca termina, pero ya tenés una base sólida para comenzar!
:::

**¡Éxitos en tu carrera de Ingeniería en Computación!**

---

(glosario-modulos)=
## Glosario sobre módulos

```{glossary}
Módulo
Module
  Archivo `.py` que contiene código Python (funciones, clases, variables). Permite organizar código en unidades lógicas reutilizables. Ejemplo: `import math` importa el módulo math. También conocido como **module** en inglés.

import
  Palabra clave para traer código de un {term}`módulo` a tu programa. Sintaxis básica: `import nombre_modulo`. Hace disponible el código del módulo en tu programa actual.

from ... import
  Sintaxis para importar elementos específicos de un {term}`módulo`. Ejemplo: `from math import sqrt` importa solo la función `sqrt`. Evita tener que usar el nombre del módulo cada vez.

as
  Palabra clave para crear un {term}`alias` al importar. Ejemplo: `import numpy as np` permite usar `np` en lugar de `numpy`. Útil para nombres largos o evitar conflictos.

Alias
  Nombre alternativo para un módulo o función importada. Se crea con {term}`as`. Ejemplo: `import pandas as pd` hace que `pd` sea un alias de `pandas`. Reduce escritura.

Namespace
Espacio de nombres
  Contexto que contiene nombres de variables, funciones y clases. Cada {term}`módulo` tiene su propio namespace. Previene conflictos de nombres entre módulos. También conocido como **espacio de nombres**.

Biblioteca estándar
Standard library
  Colección de {term}`módulos <módulo>` incluidos con Python sin necesidad de instalación. Ejemplos: `math`, `random`, `datetime`, `os`, `json`. Disponible inmediatamente después de instalar Python.

Biblioteca de terceros
Third-party library
  {term}`Módulo` o {term}`paquete` creado por la comunidad, no incluido por defecto. Debe instalarse con `pip`. Ejemplos: NumPy, Pandas, Django, Flask. También conocida como **third-party library**.

pip
  Herramienta para **instalar y gestionar** bibliotecas de Python. Descarga paquetes de PyPI. Uso: `pip install nombre_paquete`. Viene incluido con Python desde versión 3.4+.

PyPI
  "Python Package Index", repositorio oficial donde se publican {term}`bibliotecas de terceros <biblioteca de terceros>`. URL: pypi.org. Contiene más de 400,000 paquetes. `pip` descarga desde aquí.

Paquete
Package
  Directorio que contiene múltiples {term}`módulos <módulo>` y un archivo especial `__init__.py`. Organiza módulos relacionados en una jerarquía. Ejemplo: `from paquete.subpaquete import modulo`.

__init__.py
  Archivo especial que convierte un directorio en un {term}`paquete` Python. Puede estar vacío o contener código de inicialización. Su presencia indica que el directorio es importable.

__name__
  Variable especial que contiene el nombre del {term}`módulo`. Cuando un módulo se ejecuta directamente, `__name__ == "__main__"`. Cuando se importa, contiene el nombre del archivo.

__main__
  Valor especial de {term}`__name__` cuando un módulo se ejecuta directamente (no importado). Patrón común: `if __name__ == "__main__":` para código que solo corre en ejecución directa.

sys.path
  Lista de directorios donde Python busca {term}`módulos <módulo>` al importar. Incluye el directorio actual, directorios de biblioteca estándar y {term}`site-packages`. Modificable en tiempo de ejecución.

site-packages
  Directorio donde {term}`pip` instala {term}`bibliotecas de terceros <biblioteca de terceros>`. Ubicación típica: `.../Python3.x/site-packages/`. Python busca aquí automáticamente al importar.

Archivo
File
  Entidad en el sistema de archivos que almacena datos. Python puede leer/escribir archivos de texto, binarios, JSON, CSV, etc. Se abre con `open()`.

open()
  Función que abre un archivo y devuelve un objeto de archivo. Sintaxis: `open(ruta, modo)`. Modos: `'r'` (leer), `'w'` (escribir), `'a'` (append), `'b'` (binario).

Modo de apertura
File mode
  String que especifica cómo abrir un archivo con {term}`open()`. Principales: `'r'` (lectura), `'w'` (escritura sobrescribe), `'a'` (append agrega), `'x'` (crea nuevo).

Context manager
Gestor de contexto
  Estructura `with` que garantiza la correcta apertura/cierre de recursos. Ejemplo: `with open('file.txt') as f:`. Cierra el archivo automáticamente, incluso si hay error.

with
  Palabra clave para usar un {term}`context manager`. Sintaxis: `with recurso as variable:`. Asegura limpieza correcta de recursos (archivos, conexiones, etc.).

Ruta absoluta
Absolute path
  Ruta completa desde la raíz del sistema de archivos. Ejemplos: `/home/user/file.txt` (Linux), `C:\Users\user\file.txt` (Windows). No depende del directorio actual.

Ruta relativa
Relative path
  Ruta desde el directorio actual. Ejemplos: `./archivo.txt`, `../data/datos.csv`. Usa `.` (actual) y `..` (padre). Depende de dónde se ejecute el programa.

Excepción
Exception
  Evento que interrumpe el flujo normal del programa cuando ocurre un error. Ejemplos: `FileNotFoundError`, `ValueError`, `TypeError`. Si no se maneja, el programa termina.

try-except
  Estructura para **manejar excepciones**. El código en `try` se ejecuta, si hay error, se ejecuta `except`. Evita que el programa termine abruptamente. Permite recuperación de errores.

try-except-else
  Extensión de {term}`try-except` con bloque `else` que se ejecuta solo si **no** hubo excepción en `try`. Útil para código que depende del éxito del `try`.

try-except-finally
  Extensión de {term}`try-except` con bloque `finally` que **siempre** se ejecuta, haya o no excepción. Usado para limpieza: cerrar archivos, liberar recursos, etc.

raise
  Palabra clave para **lanzar** una {term}`excepción` manualmente. Sintaxis: `raise TipoError("mensaje")`. Útil para validar condiciones y reportar errores específicos en funciones.

FileNotFoundError
  {term}`Excepción` lanzada cuando se intenta abrir un archivo que no existe. Común con `open()`. Debe manejarse con {term}`try-except` o verificar existencia antes.

ValueError
  Excepción lanzada cuando una función recibe un argumento del tipo correcto pero valor inapropiado. Ejemplo: `int("abc")` lanza `ValueError`.

JSON
  Formato de texto para intercambio de datos (JavaScript Object Notation). Python lo maneja con el módulo `json`. Convierte entre dict/list de Python y texto JSON.

CSV
  Formato de archivo de texto para datos tabulares (Comma-Separated Values). Python lo maneja con el módulo `csv`. Cada línea es una fila, valores separados por comas.

Serialización
  Convertir un objeto Python a un formato que se puede guardar en archivo o transmitir. Ejemplo: dict → JSON string. También: pickle, YAML.

Deserialización
  Convertir datos serializados de vuelta a objetos Python. Ejemplo: JSON string → dict. Operación inversa de {term}`serialización`.

Biblioteca
Library
  Conjunto de {term}`módulos <módulo>` y {term}`paquetes <paquete>` que proporcionan funcionalidad específica. Término general para código reutilizable de otros. Ejemplos: biblioteca estándar, NumPy, Pandas.

Dependencia
Dependency
  {term}`Biblioteca de terceros <biblioteca de terceros>` que tu proyecto necesita para funcionar. Se especifican en `requirements.txt`. Deben instalarse con {term}`pip` antes de ejecutar el programa.

requirements.txt
  Archivo de texto que lista las {term}`dependencias <dependencia>` de un proyecto Python. Formato: `nombre_paquete==version`. Se instalan con `pip install -r requirements.txt`.

Virtual environment
Entorno virtual
  Entorno Python aislado con sus propias bibliotecas. Evita conflictos entre proyectos con diferentes versiones de dependencias. Se crea con `venv` o `virtualenv`.

__pycache__
  Directorio generado automáticamente por Python con versiones compiladas (`.pyc`) de módulos. Mejora velocidad de importación. Se puede ignorar en git (`.gitignore`).

Importación circular
Circular import
  Error cuando dos {term}`módulos <módulo>` se importan mutuamente. Ejemplo: A importa B, B importa A. Causa `ImportError`. Se soluciona reestructurando código.
```
