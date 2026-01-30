---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Estilo - Parte 1/2' -->

# <!-- fit --> PEP 8
## Guía de estilo de Python
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: '¿Qué es PEP 8?' -->

# PEP 8

**Python Enhancement Proposal 8**
* Guía oficial de estilo de Python
* Convenciones de escritura
* Legibilidad ante todo
* "El código se lee más que se escribe"

**No son reglas absolutas, son recomendaciones**

---

<!-- _header: 'Indentación' -->

# Espacios, no tabs

**Regla de oro: 4 espacios**
```python
# ✅ Correcto
def funcion():
    if condicion:
        hacer_algo()
    return resultado

# ❌ Incorrecto (2 espacios)
def funcion():
  if condicion:
    hacer_algo()
  return resultado
```

**Configurá tu editor para usar 4 espacios**

---

<!-- _header: 'Longitud de línea' -->

# Máximo 79 caracteres

**Líneas largas dificultan lectura:**
```python
# ❌ Muy largo
resultado = funcion_con_nombre_largo(parametro1, parametro2, parametro3, parametro4, parametro5)

# ✅ Dividir en varias líneas
resultado = funcion_con_nombre_largo(
    parametro1, parametro2, parametro3,
    parametro4, parametro5
)
```

---

<!-- _header: 'Líneas en blanco' -->

# Separación visual

**2 líneas entre funciones/clases:**
```python
def funcion1():
    pass


def funcion2():
    pass
```

**1 línea dentro de funciones:**
```python
def funcion():
    preparar()
    
    procesar()
    
    finalizar()
```

---

<!-- _header: 'Importaciones' -->

# Orden y formato

**Orden recomendado:**
```python
# 1. Biblioteca estándar
import math
import random

# 2. Bibliotecas de terceros
import numpy
import pandas

# 3. Módulos locales
import mi_modulo
```

**Un import por línea:**
```python
# ✅ Correcto
import math
import random

# ❌ Evitar
import math, random
```

---

<!-- _header: 'Nombres de variables' -->

# snake_case para variables

**Minúsculas con guiones bajos:**
```python
# ✅ Correcto
nombre_usuario = "Ana"
numero_intentos = 0
precio_final = 100.50

# ❌ Incorrecto (camelCase)
nombreUsuario = "Ana"
numeroIntentos = 0

# ❌ Incorrecto (mayúsculas)
NOMBRE_USUARIO = "Ana"
```

---

<!-- _header: 'Nombres de funciones' -->

# snake_case para funciones

**Verbos descriptivos:**
```python
# ✅ Correcto
def calcular_promedio(numeros):
    pass

def validar_email(email):
    pass

def obtener_datos_usuario():
    pass

# ❌ Incorrecto
def CalcularPromedio(numeros):
    pass

def val_email(email):
    pass
```

---

<!-- _header: 'Nombres de constantes' -->

# MAYUSCULAS_CON_GUIONES

**Para valores que no cambian:**
```python
# ✅ Correcto
PI = 3.14159
MAX_INTENTOS = 3
VELOCIDAD_LUZ = 299792458

# ❌ Incorrecto
pi = 3.14159
MaxIntentos = 3
```

---

<!-- _header: 'Nombres de clases' -->

# PascalCase para clases

**Primera letra de cada palabra en mayúscula:**
```python
# ✅ Correcto
class Usuario:
    pass

class CuentaBancaria:
    pass

class SistemaGestion:
    pass

# ❌ Incorrecto
class usuario:
    pass

class cuenta_bancaria:
    pass
```

---

<!-- _header: 'Espacios en expresiones' -->

# Espacios alrededor de operadores

**Mejorar legibilidad:**
```python
# ✅ Correcto
x = 5
y = x + 10
z = x * y

# ❌ Incorrecto
x=5
y=x+10
z=x*y

# ✅ En llamadas
resultado = funcion(a, b, c)

# ❌ Espacios de más
resultado = funcion( a , b , c )
```

---

<!-- _header: 'Espacios en listas' -->

# Espacios en colecciones

**Después de comas:**
```python
# ✅ Correcto
numeros = [1, 2, 3, 4, 5]
persona = {"nombre": "Ana", "edad": 25}

# ❌ Incorrecto
numeros = [1,2,3,4,5]
persona = {"nombre":"Ana","edad":25}

# ❌ Espacios dentro
numeros = [ 1, 2, 3 ]
```

---

<!-- _header: 'Comparaciones' -->

# Comparaciones claras

**Usar is para None:**
```python
# ✅ Correcto
if valor is None:
    pass

if valor is not None:
    pass

# ❌ Incorrecto
if valor == None:
    pass
```

**Comparar booleanos:**
```python
# ✅ Correcto
if activo:
    pass

# ❌ Innecesario
if activo == True:
    pass
```

---

<!-- _header: 'Strings' -->

# Comillas consistentes

**Elegir un estilo:**
```python
# ✅ Consistente (comillas dobles)
nombre = "Ana"
mensaje = "Hola mundo"

# ✅ Consistente (comillas simples)
nombre = 'Ana'
mensaje = 'Hola mundo'

# ✅ Para strings con comillas
frase = "Ella dijo 'hola'"
frase = 'Él dijo "hola"'
```

**Lo importante es ser consistente**

---

<!-- _header: 'Comentarios' -->

# Comentarios útiles

**Explicar el por qué, no el qué:**
```python
# ❌ Comentario obvio
x = x + 1  # Incrementar x

# ✅ Comentario útil
x = x + 1  # Compensar por índice basado en 1

# ✅ Documentar decisiones
# Usamos bubble sort porque la lista es pequeña
# y prioriza simplicidad sobre eficiencia
ordenar_burbuja(numeros)
```

---

<!-- _header: 'Docstrings' -->

# Documentar funciones

**Triple comillas para docstrings:**
```python
def calcular_promedio(numeros):
    """
    Calcula el promedio de una lista de números.
    
    Args:
        numeros: Lista de números enteros o flotantes
        
    Returns:
        float: Promedio de los números
        
    Raises:
        ValueError: Si la lista está vacía
    """
    if not numeros:
        raise ValueError("Lista vacía")
    return sum(numeros) / len(numeros)
```

---

<!-- _header: 'Ejemplo completo' -->

# Código siguiendo PEP 8

```python
"""Módulo para gestionar usuarios."""

MAX_INTENTOS = 3


def validar_usuario(nombre, edad):
    """
    Valida datos de usuario.
    
    Args:
        nombre: Nombre del usuario
        edad: Edad del usuario
        
    Returns:
        bool: True si válido, False caso contrario
    """
    if not nombre or len(nombre) < 2:
        return False
    
    if edad < 0 or edad > 120:
        return False
    
    return True
```

---

<!-- _header: 'Herramientas' -->

# Verificar estilo automáticamente

**Linters y formateadores:**
* **pycodestyle** - verifica PEP 8
* **pylint** - análisis estático
* **black** - formateador automático
* **flake8** - combina varios

```bash
# Instalar
pip install pycodestyle black flake8

# Verificar archivo
pycodestyle mi_programa.py
flake8 mi_programa.py

# Formatear automáticamente
black mi_programa.py
```

---

<!-- _header: 'Resumen' -->

# Reglas principales

**Formato:**
* 4 espacios de indentación
* Máximo 79 caracteres por línea
* 2 líneas entre funciones

**Nombres:**
* `snake_case` para variables y funciones
* `MAYUSCULAS` para constantes
* `PascalCase` para clases

**Espacios:**
* Alrededor de operadores
* Después de comas
* Sin espacios dentro de paréntesis

---

<!-- _header: 'Filosofía' -->

# El Zen de Python

```python
import this
```

**Principios clave:**
* Bello es mejor que feo
* Explícito es mejor que implícito
* Simple es mejor que complejo
* **La legibilidad cuenta**
* Los casos especiales no son tan especiales
* Debería haber una -y preferiblemente solo una- forma obvia de hacerlo

---

<!-- _header: 'Para recordar' -->

# Código legible

**PEP 8 busca:**
* Código consistente
* Fácil de leer
* Fácil de mantener
* Colaboración efectiva

**"El código se lee mucho más de lo que se escribe"**

**Próximo:**
* Buenas prácticas generales

---

<!-- _class: centered -->

# ¿Preguntas?
