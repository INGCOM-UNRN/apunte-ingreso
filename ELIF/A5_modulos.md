---
title: Módulos y Archivos (Versión Escolar)
short_title: 5 - Módulos
subtitle: ¡No inventes la rueda, usá la caja de herramientas!
---

(modulos-escolar)= 
# Modularización y Archivos

¡Llegamos al último nivel! 🚀 Ya sabés hacer programas que piensan, repiten y usan funciones. Ahora vas a aprender a organizar tu código para no tener un archivo gigante imposible de leer y a guardar tus datos para que no se borren cuando apagás la compu.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a usar código que ya escribieron otros (módulos), a separar tu propio código en archivos más chicos y ordenados, y a leer y escribir archivos en tu disco duro.
::::

---

## 1. Introducción: La Caja de Herramientas 🧰

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Un módulo es un archivo `.py` con funciones listas para usar. No tenés que escribir todo desde cero.

**Analogía:** Imaginate que vas a construir una casa en Minecraft.
*   No te ponés a programar cómo funciona la madera, el vidrio o la electricidad desde cero.
*   Usás los bloques que ya vienen en el juego (la biblioteca estándar) o mods que hicieron otros.
*   Los **módulos** son esos bloques prefabricados que te ahorran trabajo.

**Vocabulario:**
1.  **Módulo:** Un archivo `.py` con código que podés importar.
2.  **Importar:** Traer el código de un módulo a tu programa para usarlo.
3.  **Biblioteca Estándar:** El conjunto de módulos que ya vienen instalados con Python (la caja de herramientas básica).
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Si quiero calcular una raíz cuadrada, tengo que programar la fórmula matemática yo mismo. ( **Falso**: Usás el módulo `math` y listo).
2.  Importar un módulo es como abrir una caja de herramientas específica para un trabajo. ( **Verdadero**).

---

(importar-escolar)=
## 2. Importar: ¡Traeme esa herramienta!

Para usar un módulo, usamos la palabra mágica `import`.

### Forma 1: Traer toda la caja (`import`)

```python
import math

# Ahora puedo usar todo lo que está adentro de 'math'
raiz = math.sqrt(25)
print(f"La raíz de 25 es {raiz}")
```

### Forma 2: Traer solo lo que necesito (`from ... import`)

Si solo querés el martillo, no traigas toda la caja.

```python
from random import randint

# Genero un número al azar entre 1 y 10
dado = randint(1, 10)
print(f"Salió el {dado}")
```

### Forma 3: Ponerle un apodo (`as`)

Si el nombre es muy largo, le ponemos uno corto.

```python
import datetime as dt

hoy = dt.date.today()
print(f"Hoy es {hoy}")
```

---

(biblioteca-estandar-escolar)=
## 3. Módulos Famosos (Los Vengadores de Python)

Acá te presento a los módulos que vas a usar todo el tiempo:

| Módulo |
| :--- |
| **math** |
| **random** |
| **datetime** |
| **os** |

| ¿Para qué sirve? |
| :--- |
| Matemáticas avanzadas |
| Azar, suerte, aleatorio |
| Fechas y horas |
| Manejar archivos y carpetas del sistema |

| Ejemplo |
| :--- |
| `math.pi`, `math.sin()`, `math.sqrt()` |
| `random.randint()`, `random.choice()` |
| `datetime.now()`, `date.today()` |
| `os.getcwd()`, `os.listdir()` |

### Ejemplo: El Sorteo

```python
import random

amigos = ["Ana", "Pedro", "Julieta", "Martín"]
ganador = random.choice(amigos)

print(f"¡El ganador del sorteo es {ganador}! 🎉")
```

---

(crear-modulos-escolar)=
## 4. Creá tus Propios Módulos

¡Vos también podés crear herramientas! Es re fácil:

1.  Creá un archivo `mis_funciones.py`.
2.  Escribí tus funciones ahí.
3.  Desde otro archivo (en la misma carpeta), poné `import mis_funciones`.

**Archivo `mis_funciones.py`:**
```python
def saludar(nombre):
    return f"¡Hola {nombre}, crack!"
```

**Archivo `programa_principal.py`:**
```python
import mis_funciones

mensaje = mis_funciones.saludar("Sofía")
print(mensaje)
```

Es genial para no tener un archivo de 500 líneas imposible de leer.

---

(archivos-escolar)=
## 5. Archivos: Guardando tus secretos 💾

Hasta ahora, si cerrabas tu programa, los datos se perdían. ¡No más! Vamos a aprender a escribir en el disco duro.

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Podemos leer y escribir archivos de texto (`.txt`) para que la información persista.

**Analogía:**
*   La memoria RAM (variables) es como un pizarrón: si lo borrás o apagás la luz, se va todo.
*   El disco duro (archivos) es como un cuaderno: lo que escribís queda guardado aunque lo cierres.

**Vocabulario:**
1.  **Open (Abrir):** Abrir el archivo para usarlo.
2.  **Modo:** Decirle a Python si queremos leer (`'r'`), escribir (`'w'`) o agregar (`'a'`).
3.  **Close (Cerrar):** Cerrar el archivo al terminar (¡muy importante!).
::::

### La forma segura: `with open`

Usamos `with` para que Python se encargue de cerrar el archivo automáticamente, incluso si hay errores.

### Escribir (Guardar)

```python
# 'w' significa Write (Escribir). ¡Ojo! Borra lo que había antes.
with open("mi_diario.txt", "w") as archivo:
    archivo.write("Querido diario...\n")
    archivo.write("Hoy aprendí a programar archivos.\n")
```

### Leer (Recuperar)

```python
# 'r' significa Read (Leer).
with open("mi_diario.txt", "r") as archivo:
    contenido = archivo.read()
    print(contenido)
```

### Agregar (Sin borrar)

```python
# 'a' significa Append (Agregar al final).
with open("mi_diario.txt", "a") as archivo:
    archivo.write("PD: ¡Python está buenísimo!\n")
```

---

(excepciones-escolar)=
## 6. Manejo de Errores: Try / Except 🛡️

A veces los programas fallan (el archivo no existe, dividís por cero, el usuario escribe letras en vez de números). Para que el programa no explote, usamos `try` (intentar) y `except` (si falla, hacé esto).

```python
try:
    edad = int(input("Ingresá tu edad: "))
    print(f"Tenés {edad} años.")
except ValueError:
    print("¡Che, tenés que poner un número, no letras!")
```

Si el usuario escribe "quince", el programa no se rompe, sino que muestra el mensaje amable.

---

(ejercicios-escolar)=
## 7. Ejercicios: ¡El desafío final! 🏆

Tratá de resolverlos vos solo antes de mirar la solución. ¡Vos podés!

### Ejercicio 1: El Dado Mágico
Usá el módulo `random` para simular un dado de 6 caras. Tirá el dado 5 veces y mostrá los resultados.

````{solution} Solución Ejercicio 1
:class: dropdown
```python
import random

print("Tirando los dados...")
for i in range(5):
    dado = random.randint(1, 6)
    print(f"Tiro {i+1}: {dado}")
```
````

### Ejercicio 2: El Guardián de Nombres
Pedile al usuario 3 nombres y guardalos en un archivo llamado `amigos.txt`. Luego, leé el archivo y mostrá los nombres en pantalla.

````{solution} Solución Ejercicio 2
:class: dropdown
```python
# Escribir
with open("amigos.txt", "w") as f:
    for i in range(3):
        nombre = input(f"Nombre del amigo {i+1}: ")
        f.write(nombre + "\n") # \n es para bajar de renglón

# Leer
print("\nLeyendo archivo:")
with open("amigos.txt", "r") as f:
    contenido = f.read()
    print(contenido)
```
````


### Ejercicio 3: Calculadora a Prueba de Balas
Hacé una división de dos números, pero usá `try/except` para evitar que el programa explote si el usuario intenta dividir por cero.

````{solution} Solución Ejercicio 3
:class: dropdown
```python
try:
    a = int(input("Numerador: "))
    b = int(input("Denominador: "))
    resultado = a / b
    print(f"El resultado es {resultado}")
except ZeroDivisionError:
    print("¡No podés dividir por cero! Eso rompe el universo. 🌌")
except ValueError:
    print("Por favor, ingresá solo números enteros.")
```
````

---


### ¡Fin del Curso! 🎓

¡Felicitaciones! Llegaste al final. Aprendiste un montón: variables, condicionales, bucles, listas, funciones, módulos y archivos. Ya tenés todas las herramientas básicas de un programador.

Ahora... **¡a programar cosas increíbles!** 🚀
