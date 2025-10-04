---
title: Modularización y Archivos
short_title: Módulos y Archivos
subtitle: Organización de código, módulos, paquetes, archivos y excepciones.
---

(modularizacion)=
# Modularización y Archivos

## Introducción y Motivación

A medida que tus programas crecen, organizarlos en un solo archivo se vuelve impracticable. La **modularización** te permite dividir tu código en múltiples archivos, cada uno con un propósito específico. Además, necesitás que tus programas puedan guardar y leer información de archivos para que los datos persistan entre ejecuciones.

Imagina desarrollar un sistema de gestión de estudiantes. Podrías tener:
- Un módulo para funciones matemáticas (promedios, estadísticas)
- Un módulo para validaciones (emails, DNI)
- Un módulo para manejo de archivos (guardar/leer datos)
- Un programa principal que coordina todo

:::{important} ¿Por qué modularizar?
La modularización te permite:
- **Organizar código**: Agrupar funciones relacionadas
- **Reutilizar código**: Usar módulos en diferentes programas
- **Colaborar mejor**: Cada persona trabaja en módulos diferentes
- **Mantener código**: Cambios aislados en cada módulo
- **Testear fácilmente**: Probar cada módulo por separado
- **Aprovechar bibliotecas**: Usar módulos de la comunidad Python
:::

En este capítulo aprenderás:
- Usar módulos de la biblioteca estándar
- Crear tus propios módulos
- Organizar módulos en paquetes
- Leer y escribir archivos
- Manejar errores con excepciones
- Trabajar con context managers

---

(importar-modulos)=
## Importar Módulos

Python incluye una **biblioteca estándar** con cientos de módulos útiles.

### Importar un Módulo Completo

```python
import math

# Usar funciones del módulo con la sintaxis: modulo.funcion()
raiz = math.sqrt(16)
print(raiz)  # 4.0

pi = math.pi
print(pi)  # 3.141592653589793

seno = math.sin(math.pi / 2)
print(seno)  # 1.0
```

### Importar Funciones Específicas

```python
from math import sqrt, pi, sin

# Ahora podés usar directamente las funciones
raiz = sqrt(16)
print(raiz)  # 4.0

print(pi)  # 3.141592653589793
```

### Importar con Alias

```python
import math as m

raiz = m.sqrt(25)
print(raiz)  # 5.0

# O para funciones específicas
from math import sqrt as raiz_cuadrada

resultado = raiz_cuadrada(9)
print(resultado)  # 3.0
```

### Importar Todo (No Recomendado)

```python
# ❌ Evitar esto
from math import *

# Contamina el namespace
# No es claro de dónde vienen las funciones
```

:::{tip} Buenas prácticas de importación
Según las convenciones de Python:
1. Importá módulos completos cuando uses muchas funciones
2. Importá funciones específicas si solo usás unas pocas
3. Usá alias descriptivos cuando el nombre sea largo
4. NUNCA uses `from module import *`
5. Organizá imports: stdlib, terceros, locales
:::

### Módulos Útiles de la Biblioteca Estándar

```python
# math - Funciones matemáticas
import math
print(math.ceil(4.3))   # 5 (redondear arriba)
print(math.floor(4.8))  # 4 (redondear abajo)

# random - Números y elecciones aleatorias
import random
numero = random.randint(1, 10)     # Entero entre 1 y 10
decimal = random.random()          # Float entre 0 y 1
elemento = random.choice([1, 2, 3])  # Elemento aleatorio

# datetime - Fechas y horas
from datetime import datetime
ahora = datetime.now()
print(ahora)  # 2024-01-15 14:30:45.123456

# os - Interacción con el sistema operativo
import os
directorio_actual = os.getcwd()
archivos = os.listdir('.')

# sys - Parámetros y funciones del sistema
import sys
print(sys.version)  # Versión de Python
```

---

(crear-modulos)=
## Crear Tus Propios Módulos

Un módulo es simplemente un archivo `.py` con funciones, clases y variables.

### Crear un Módulo Simple

**Archivo: `matematicas.py`**
```python
"""Módulo con funciones matemáticas básicas."""

PI = 3.14159

def area_circulo(radio):
    """Calcula el área de un círculo.
    
    Args:
        radio: El radio del círculo.
    
    Returns:
        El área del círculo.
    """
    return PI * radio ** 2

def perimetro_circulo(radio):
    """Calcula el perímetro de un círculo.
    
    Args:
        radio: El radio del círculo.
    
    Returns:
        El perímetro del círculo.
    """
    return 2 * PI * radio

def factorial(n):
    """Calcula el factorial de n.
    
    Args:
        n: Número entero no negativo.
    
    Returns:
        El factorial de n.
    """
    if n == 0 or n == 1:
        return 1
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado
```

### Usar Tu Módulo

**Archivo: `programa.py`** (en el mismo directorio)
```python
import matematicas

# Usar funciones del módulo
area = matematicas.area_circulo(5)
print(f"Área: {area}")

perimetro = matematicas.perimetro_circulo(5)
print(f"Perímetro: {perimetro}")

fact = matematicas.factorial(5)
print(f"5! = {fact}")

# Acceder a constantes
print(f"PI = {matematicas.PI}")
```

### Variables Privadas

Por convención, nombres que comienzan con `_` son privados:

**Archivo: `calculadora.py`**
```python
"""Módulo calculadora con funciones públicas y privadas."""

# Variable privada (por convención)
_VERSION = "1.0"

# Función privada (por convención)
def _validar_numero(n):
    """Valida que n sea un número."""
    if not isinstance(n, (int, float)):
        raise TypeError("Debe ser un número")
    return True

# Función pública
def sumar(a, b):
    """Suma dos números después de validarlos."""
    _validar_numero(a)
    _validar_numero(b)
    return a + b
```

### El Bloque `if __name__ == "__main__"`

Permite que un módulo sea ejecutable pero también importable:

**Archivo: `utilidades.py`**
```python
"""Módulo de utilidades."""

def saludar(nombre):
    """Saluda a una persona."""
    return f"¡Hola, {nombre}!"

def despedir(nombre):
    """Se despide de una persona."""
    return f"¡Adiós, {nombre}!"

# Este código solo se ejecuta si el archivo se corre directamente
# NO se ejecuta cuando se importa como módulo
if __name__ == "__main__":
    print("Ejecutando utilidades.py directamente")
    print(saludar("Ana"))
    print(despedir("Bruno"))
```

**Uso:**
```python
# Importar como módulo - no ejecuta el bloque main
import utilidades
print(utilidades.saludar("Carlos"))

# Ejecutar directamente: python utilidades.py
# Sí ejecuta el bloque main
```

:::{important} Cuándo usar `__name__ == "__main__"`
Usá este patrón cuando:
- El módulo tiene funciones útiles para importar
- También querés poder ejecutarlo para testear
- Querés incluir ejemplos de uso

```python
def mi_funcion():
    """Función útil."""
    pass

if __name__ == "__main__":
    # Código de testing o ejemplos
    print("Testing mi_funcion()")
    mi_funcion()
```
:::

---

(paquetes)=
## Paquetes

Un **paquete** es un directorio que contiene módulos y un archivo especial `__init__.py`.

### Crear un Paquete

Estructura de directorios:
```
mi_proyecto/
    programa.py
    matematicas/
        __init__.py
        basicas.py
        avanzadas.py
```

**Archivo: `matematicas/__init__.py`**
```python
"""Paquete de matemáticas."""

# Este archivo puede estar vacío o inicializar el paquete
from .basicas import sumar, restar
from .avanzadas import potencia, raiz

__version__ = "1.0.0"
```

**Archivo: `matematicas/basicas.py`**
```python
"""Operaciones matemáticas básicas."""

def sumar(a, b):
    """Retorna la suma de a y b."""
    return a + b

def restar(a, b):
    """Retorna la resta de a y b."""
    return a - b

def multiplicar(a, b):
    """Retorna el producto de a y b."""
    return a * b

def dividir(a, b):
    """Retorna la división de a entre b."""
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b
```

**Archivo: `matematicas/avanzadas.py`**
```python
"""Operaciones matemáticas avanzadas."""

def potencia(base, exponente):
    """Calcula base elevado a exponente."""
    return base ** exponente

def raiz(numero, indice=2):
    """Calcula la raíz n-ésima de un número."""
    return numero ** (1 / indice)

def factorial(n):
    """Calcula el factorial de n."""
    if n < 0:
        raise ValueError("n debe ser no negativo")
    if n == 0 or n == 1:
        return 1
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado
```

### Usar el Paquete

**Archivo: `programa.py`**
```python
# Importar todo el paquete
import matematicas

print(matematicas.sumar(5, 3))      # 8
print(matematicas.potencia(2, 3))   # 8

# Importar módulos específicos
from matematicas import basicas
print(basicas.multiplicar(4, 5))    # 20

# Importar funciones específicas
from matematicas.avanzadas import factorial
print(factorial(5))  # 120
```

### Importaciones Relativas

Dentro de un paquete, podés usar importaciones relativas:

```python
# En matematicas/avanzadas.py
from .basicas import sumar  # Mismo paquete
from ..otro_paquete import algo  # Paquete padre
```

---

(manejo-archivos)=
## Manejo de Archivos

Los archivos permiten que tus programas guarden y lean datos.

### Abrir y Cerrar Archivos

```python
# Abrir archivo para lectura
archivo = open("datos.txt", "r")
contenido = archivo.read()
archivo.close()  # IMPORTANTE: siempre cerrar

print(contenido)
```

**Modos de apertura:**

| Modo | Descripción |
|------|-------------|
| `"r"` | Lectura (read) - archivo debe existir |
| `"w"` | Escritura (write) - crea o sobrescribe |
| `"a"` | Agregar (append) - agrega al final |
| `"r+"` | Lectura y escritura |
| `"b"` | Modo binario (ej: `"rb"`, `"wb"`) |

### Context Manager (`with`)

La forma recomendada de trabajar con archivos:

```python
# ✓ Con 'with' - cierra automáticamente
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
    print(contenido)
# El archivo se cierra automáticamente al salir del bloque
```

:::{tip} Siempre usá `with`
El context manager `with` garantiza que el archivo se cierre correctamente, incluso si ocurre un error.

```python
# ❌ Arriesgado
archivo = open("datos.txt", "r")
contenido = archivo.read()  # Si hay error aquí...
archivo.close()  # ...esto nunca se ejecuta

# ✓ Seguro
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
# Siempre se cierra
```
:::

### Leer Archivos

```python
# Leer todo el contenido
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
    print(contenido)

# Leer línea por línea
with open("datos.txt", "r") as archivo:
    for linea in archivo:
        print(linea.strip())  # strip() quita \n

# Leer todas las líneas en una lista
with open("datos.txt", "r") as archivo:
    lineas = archivo.readlines()
    print(lineas)

# Leer línea por línea eficientemente
with open("datos.txt", "r") as archivo:
    linea1 = archivo.readline()
    linea2 = archivo.readline()
```

### Escribir Archivos

```python
# Escribir (sobrescribe si existe)
with open("salida.txt", "w") as archivo:
    archivo.write("Primera línea\n")
    archivo.write("Segunda línea\n")

# Escribir múltiples líneas
lineas = ["Línea 1\n", "Línea 2\n", "Línea 3\n"]
with open("salida.txt", "w") as archivo:
    archivo.writelines(lineas)

# Agregar al final (no sobrescribe)
with open("salida.txt", "a") as archivo:
    archivo.write("Nueva línea al final\n")
```

### Verificar si un Archivo Existe

```python
import os

# Verificar existencia
if os.path.exists("datos.txt"):
    print("El archivo existe")
else:
    print("El archivo no existe")

# Verificar si es archivo o directorio
if os.path.isfile("datos.txt"):
    print("Es un archivo")

if os.path.isdir("carpeta"):
    print("Es un directorio")
```

### Ejemplo: Guardar y Cargar Lista

```python
def guardar_nombres(nombres, archivo):
    """Guarda una lista de nombres en un archivo.
    
    Args:
        nombres: Lista de strings.
        archivo: Nombre del archivo.
    """
    with open(archivo, "w") as f:
        for nombre in nombres:
            f.write(nombre + "\n")

def cargar_nombres(archivo):
    """Carga nombres desde un archivo.
    
    Args:
        archivo: Nombre del archivo.
    
    Returns:
        Lista de nombres.
    """
    if not os.path.exists(archivo):
        return []
    
    with open(archivo, "r") as f:
        nombres = [linea.strip() for linea in f]
    
    return nombres

# Uso
nombres = ["Ana", "Bruno", "Carlos"]
guardar_nombres(nombres, "nombres.txt")

nombres_cargados = cargar_nombres("nombres.txt")
print(nombres_cargados)  # ['Ana', 'Bruno', 'Carlos']
```

---

(json)=
## Trabajar con JSON

JSON (JavaScript Object Notation) es un formato estándar para intercambiar datos.

### Módulo `json`

```python
import json

# Convertir dict a JSON (string)
datos = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Ingeniería",
    "materias": ["Programación", "Matemática", "Física"]
}

json_string = json.dumps(datos, indent=2)
print(json_string)
```

### Guardar JSON en Archivo

```python
import json

# Guardar
datos = {"nombre": "Ana", "edad": 20}

with open("datos.json", "w") as archivo:
    json.dump(datos, archivo, indent=2)

# Cargar
with open("datos.json", "r") as archivo:
    datos_cargados = json.load(archivo)

print(datos_cargados)  # {'nombre': 'Ana', 'edad': 20}
```

### Ejemplo: Sistema de Configuración

```python
import json
import os

class Configuracion:
    """Maneja la configuración de la aplicación."""
    
    def __init__(self, archivo="config.json"):
        self.archivo = archivo
        self.datos = self.cargar()
    
    def cargar(self):
        """Carga configuración desde archivo."""
        if os.path.exists(self.archivo):
            with open(self.archivo, "r") as f:
                return json.load(f)
        return self._configuracion_por_defecto()
    
    def guardar(self):
        """Guarda configuración en archivo."""
        with open(self.archivo, "w") as f:
            json.dump(self.datos, f, indent=2)
    
    def _configuracion_por_defecto(self):
        """Retorna configuración por defecto."""
        return {
            "idioma": "es",
            "tema": "claro",
            "max_intentos": 3
        }
    
    def obtener(self, clave, default=None):
        """Obtiene un valor de configuración."""
        return self.datos.get(clave, default)
    
    def establecer(self, clave, valor):
        """Establece un valor de configuración."""
        self.datos[clave] = valor
        self.guardar()

# Uso
config = Configuracion()
print(config.obtener("idioma"))  # "es"
config.establecer("idioma", "en")
```

---

(excepciones)=
## Excepciones

Las **excepciones** son errores que ocurren durante la ejecución del programa. Python permite manejarlos elegantemente.

### Tipos Comunes de Excepciones

```python
# ValueError - valor inapropiado
int("abc")  # ValueError: invalid literal for int()

# TypeError - tipo inapropiado
"texto" + 5  # TypeError: can only concatenate str

# KeyError - clave no existe
d = {"a": 1}
d["b"]  # KeyError: 'b'

# IndexError - índice fuera de rango
lista = [1, 2, 3]
lista[10]  # IndexError: list index out of range

# FileNotFoundError - archivo no existe
open("no_existe.txt")  # FileNotFoundError

# ZeroDivisionError - división por cero
10 / 0  # ZeroDivisionError
```

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

```python
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

```python
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

```python
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
## Ejemplo Completo: Sistema de Contactos

Un ejemplo que integra módulos, archivos y excepciones.

**Archivo: `contactos.py`** (módulo)
```python
"""Módulo para gestionar contactos."""

import json
import os

class ContactoError(Exception):
    """Excepción base para errores de contactos."""
    pass

class ContactoNoEncontradoError(ContactoError):
    """Excepción cuando no se encuentra un contacto."""
    pass

class GestorContactos:
    """Gestiona una lista de contactos guardados en JSON."""
    
    def __init__(self, archivo="contactos.json"):
        """Inicializa el gestor.
        
        Args:
            archivo: Nombre del archivo JSON.
        """
        self.archivo = archivo
        self.contactos = self._cargar_contactos()
    
    def _cargar_contactos(self):
        """Carga contactos desde archivo."""
        if not os.path.exists(self.archivo):
            return {}
        
        try:
            with open(self.archivo, "r") as f:
                return json.load(f)
        except json.JSONDecodeError:
            print(f"Error al leer {self.archivo}, creando nuevo")
            return {}
    
    def _guardar_contactos(self):
        """Guarda contactos en archivo."""
        with open(self.archivo, "w") as f:
            json.dump(self.contactos, f, indent=2)
    
    def agregar(self, nombre, telefono, email=None):
        """Agrega un contacto.
        
        Args:
            nombre: Nombre del contacto.
            telefono: Teléfono del contacto.
            email: Email opcional.
        
        Raises:
            ValueError: Si el contacto ya existe.
        """
        if nombre in self.contactos:
            raise ValueError(f"El contacto '{nombre}' ya existe")
        
        self.contactos[nombre] = {
            "telefono": telefono,
            "email": email
        }
        self._guardar_contactos()
    
    def buscar(self, nombre):
        """Busca un contacto por nombre.
        
        Args:
            nombre: Nombre del contacto.
        
        Returns:
            Dict con datos del contacto.
        
        Raises:
            ContactoNoEncontradoError: Si no existe.
        """
        if nombre not in self.contactos:
            raise ContactoNoEncontradoError(
                f"No se encontró el contacto '{nombre}'"
            )
        return self.contactos[nombre]
    
    def eliminar(self, nombre):
        """Elimina un contacto.
        
        Args:
            nombre: Nombre del contacto.
        
        Raises:
            ContactoNoEncontradoError: Si no existe.
        """
        if nombre not in self.contactos:
            raise ContactoNoEncontradoError(
                f"No se encontró el contacto '{nombre}'"
            )
        
        del self.contactos[nombre]
        self._guardar_contactos()
    
    def listar(self):
        """Retorna lista de todos los contactos."""
        return list(self.contactos.keys())
    
    def actualizar(self, nombre, telefono=None, email=None):
        """Actualiza un contacto existente.
        
        Args:
            nombre: Nombre del contacto.
            telefono: Nuevo teléfono (opcional).
            email: Nuevo email (opcional).
        
        Raises:
            ContactoNoEncontradoError: Si no existe.
        """
        if nombre not in self.contactos:
            raise ContactoNoEncontradoError(
                f"No se encontró el contacto '{nombre}'"
            )
        
        if telefono:
            self.contactos[nombre]["telefono"] = telefono
        if email:
            self.contactos[nombre]["email"] = email
        
        self._guardar_contactos()
```

**Archivo: `main.py`** (programa principal)
```python
"""Programa principal para gestión de contactos."""

from contactos import GestorContactos, ContactoNoEncontradoError

def mostrar_menu():
    """Muestra el menú principal."""
    print("\n=== GESTOR DE CONTACTOS ===")
    print("1. Agregar contacto")
    print("2. Buscar contacto")
    print("3. Listar contactos")
    print("4. Eliminar contacto")
    print("5. Actualizar contacto")
    print("6. Salir")

def agregar_contacto(gestor):
    """Agrega un nuevo contacto."""
    nombre = input("Nombre: ")
    telefono = input("Teléfono: ")
    email = input("Email (Enter para omitir): ").strip()
    
    try:
        gestor.agregar(
            nombre, 
            telefono, 
            email if email else None
        )
        print(f"✓ Contacto '{nombre}' agregado")
    except ValueError as e:
        print(f"✗ Error: {e}")

def buscar_contacto(gestor):
    """Busca y muestra un contacto."""
    nombre = input("Nombre a buscar: ")
    
    try:
        datos = gestor.buscar(nombre)
        print(f"\nContacto: {nombre}")
        print(f"Teléfono: {datos['telefono']}")
        if datos['email']:
            print(f"Email: {datos['email']}")
    except ContactoNoEncontradoError as e:
        print(f"✗ {e}")

def listar_contactos(gestor):
    """Lista todos los contactos."""
    contactos = gestor.listar()
    
    if not contactos:
        print("No hay contactos guardados")
        return
    
    print(f"\nContactos ({len(contactos)}):")
    for nombre in sorted(contactos):
        datos = gestor.buscar(nombre)
        print(f"  • {nombre}: {datos['telefono']}")

def eliminar_contacto(gestor):
    """Elimina un contacto."""
    nombre = input("Nombre a eliminar: ")
    
    try:
        gestor.eliminar(nombre)
        print(f"✓ Contacto '{nombre}' eliminado")
    except ContactoNoEncontradoError as e:
        print(f"✗ {e}")

def actualizar_contacto(gestor):
    """Actualiza un contacto existente."""
    nombre = input("Nombre del contacto: ")
    
    try:
        # Mostrar datos actuales
        datos = gestor.buscar(nombre)
        print(f"Teléfono actual: {datos['telefono']}")
        print(f"Email actual: {datos['email'] or '(sin email)'}")
        
        # Solicitar nuevos datos
        telefono = input("Nuevo teléfono (Enter para mantener): ").strip()
        email = input("Nuevo email (Enter para mantener): ").strip()
        
        gestor.actualizar(
            nombre,
            telefono if telefono else None,
            email if email else None
        )
        print(f"✓ Contacto '{nombre}' actualizado")
    except ContactoNoEncontradoError as e:
        print(f"✗ {e}")

def main():
    """Función principal."""
    gestor = GestorContactos()
    
    while True:
        mostrar_menu()
        opcion = input("\nOpción: ").strip()
        
        if opcion == "1":
            agregar_contacto(gestor)
        elif opcion == "2":
            buscar_contacto(gestor)
        elif opcion == "3":
            listar_contactos(gestor)
        elif opcion == "4":
            eliminar_contacto(gestor)
        elif opcion == "5":
            actualizar_contacto(gestor)
        elif opcion == "6":
            print("¡Hasta luego!")
            break
        else:
            print("Opción inválida")

if __name__ == "__main__":
    main()
```

---

(buenas-practicas-modulos)=
## Buenas Prácticas

### 1. Organización de Imports

```python
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

```python
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

```python
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

```python
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

```python
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
```python
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
### Ejercicio 5.2: Sistema de Notas

Creá un sistema para guardar y cargar notas de estudiantes en archivos.

**Funcionalidades:**
- Agregar estudiante con sus notas
- Calcular promedio de un estudiante
- Listar todos los estudiantes
- Guardar datos en archivo JSON
- Cargar datos al iniciar

**Estructura de datos:**
```python
{
    "Ana": [8, 9, 7],
    "Bruno": [9, 8, 9],
    "Carlos": [7, 7, 8]
}
```

---

(ejercicio-5-3)=
### Ejercicio 5.3: Conversor de Archivos CSV

Creá funciones para leer y escribir archivos CSV (valores separados por comas).

**Funciones:**
```python
def leer_csv(nombre_archivo):
    """Lee CSV y retorna lista de listas."""
    pass

def escribir_csv(nombre_archivo, datos):
    """Escribe lista de listas en CSV."""
    pass

def csv_a_dict(nombre_archivo):
    """Lee CSV y retorna lista de dicts (primera fila son claves)."""
    pass
```

**Ejemplo de CSV:**
```
nombre,edad,ciudad
Ana,20,Buenos Aires
Bruno,21,Córdoba
Carlos,19,Rosario
```

---

(ejercicio-5-4)=
### Ejercicio 5.4: Logger Simple

Implementá un módulo que registre mensajes en un archivo de log.

**Funciones:**
```python
def log_info(mensaje):
    """Registra mensaje informativo."""
    pass

def log_error(mensaje):
    """Registra mensaje de error."""
    pass

def log_warning(mensaje):
    """Registra advertencia."""
    pass
```

**Formato del log:**
```
2024-01-15 14:30:45 - INFO - Programa iniciado
2024-01-15 14:31:12 - ERROR - Archivo no encontrado
2024-01-15 14:31:30 - WARNING - Memoria baja
```

---

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
### Ejercicio 5.6: Gestor de Tareas

Creá un sistema de TODO list que guarde tareas en JSON.

**Funcionalidades:**
- Agregar tarea (descripción, fecha límite)
- Marcar como completada
- Listar pendientes/completadas
- Eliminar tarea
- Guardar/cargar automáticamente

**Estructura de tarea:**
```python
{
    "id": 1,
    "descripcion": "Estudiar Python",
    "fecha_limite": "2024-01-20",
    "completada": false
}
```

---

(ejercicio-5-7)=
### Ejercicio 5.7: Calculadora con Historial

Creá una calculadora que guarde el historial de operaciones en un archivo.

**Funcionalidades:**
- Operaciones básicas (+, -, *, /)
- Guardar cada operación: "2024-01-15 14:30 | 5 + 3 = 8"
- Ver historial
- Limpiar historial
- Exportar historial a archivo de texto

---

(ejercicio-5-8)=
### Ejercicio 5.8: Conversor de Temperaturas Mejorado

Mejorá el conversor de temperaturas del capítulo de funciones:
- Organizalo en módulos separados
- Guardá conversiones en un archivo de log
- Maneja excepciones (temperaturas inválidas)
- Permite cargar temperatura desde archivo

---

(ejercicio-5-9)=
### Ejercicio 5.9: Sistema de Inventario con Archivos

Extendé el ejercicio de inventario del capítulo de funciones:
- Guardá inventario en JSON
- Cargá al iniciar
- Exportá reporte a archivo de texto
- Maneja excepciones (archivo corrupto, sin permisos)

---

(ejercicio-5-10)=
### Ejercicio 5.10: Analizador de Texto

Creá un programa que analice archivos de texto.

**Funcionalidades:**
- Contar palabras, líneas, caracteres
- Encontrar palabra más frecuente
- Generar reporte en nuevo archivo
- Maneja archivos grandes línea por línea

**Ejemplo de reporte:**
```
=== ANÁLISIS DE TEXTO ===
Archivo: discurso.txt
Líneas: 150
Palabras: 1234
Caracteres: 8765
Palabra más frecuente: "libertad" (23 veces)
```

---

## Resumen

En este capítulo aprendiste sobre modularización y manejo de archivos:

✓ **Importar módulos**: Biblioteca estándar, alias, buenas prácticas  
✓ **Crear módulos**: Archivos .py, variables privadas, `__name__`  
✓ **Paquetes**: Organizar módulos, `__init__.py`, importaciones relativas  
✓ **Manejo de archivos**: Leer, escribir, context managers (`with`)  
✓ **JSON**: Guardar y cargar estructuras de datos  
✓ **Excepciones**: Try-except, tipos comunes, crear propias  
✓ **Buenas prácticas**: Organización, documentación, manejo robusto  

La modularización es clave para crear programas grandes y mantenibles. Te permite:
- Dividir código en partes lógicas y reutilizables
- Colaborar eficientemente en equipo
- Mantener y actualizar código fácilmente
- Aprovechar código de otros (bibliotecas)
- Persistir datos entre ejecuciones

:::{important} El poder de los módulos
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

**¡Éxitos en tu carrera de Ingeniería en Computación!** 🎓🚀
