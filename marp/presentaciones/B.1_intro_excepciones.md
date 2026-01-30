---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 1/4' -->

# <!-- fit --> Excepciones
## Manejo de errores
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Los errores existen' -->

# Los errores son parte del juego

**Todo programa puede fallar:**
* Usuario ingresa texto en lugar de número
* Archivo no existe
* División por cero
* Memoria llena
* Conexión de red perdida

**¿Cómo manejarlos profesionalmente?**

---

<!-- _header: 'Programa frágil' -->

# Sin manejo de errores

```python
def dividir(a, b):
    return a / b

num1 = int(input("Numerador: "))
num2 = int(input("Denominador: "))

resultado = dividir(num1, num2)
print(f"Resultado: {resultado}")
```

**¿Qué pasa si el usuario ingresa "hola"?**
**¿O si ingresa 0 como denominador?**

---

<!-- _header: 'Programa robusto' -->

# Con manejo de errores

```python
def dividir(a, b):
    if b == 0:
        raise ValueError("No se puede dividir por 0")
    return a / b

try:
    num1 = int(input("Numerador: "))
    num2 = int(input("Denominador: "))
    resultado = dividir(num1, num2)
    print(f"Resultado: {resultado}")
except ValueError as e:
    print(f"Error: {e}")
```

**El programa no se rompe**

---

<!-- _header: '¿Qué es una excepción?' -->

# Excepción

**Evento anormal que interrumpe el flujo:**
* Se "lanza" cuando hay error
* Si no se captura, el programa termina
* Si se captura, se puede manejar

**Analogía:**
* Alarma de incendio (excepción)
* Seguir el procedimiento (try-except)
* Evacuación segura (manejo correcto)

---

<!-- _header: 'Tipos comunes' -->

# Excepciones frecuentes

**ValueError:**
```python
int("abc")  # ValueError: no es un número
```

**TypeError:**
```python
"2" + 2  # TypeError: tipos incompatibles
```

**ZeroDivisionError:**
```python
10 / 0  # ZeroDivisionError
```

---

<!-- _header: 'Más tipos' -->

# Otras excepciones comunes

**IndexError:**
```python
lista = [1, 2, 3]
lista[10]  # IndexError: índice fuera de rango
```

**KeyError:**
```python
dict = {"a": 1}
dict["b"]  # KeyError: clave no existe
```

**FileNotFoundError:**
```python
open("noexiste.txt")  # FileNotFoundError
```

---

<!-- _header: 'Sin manejo' -->

# ¿Qué pasa sin try-except?

```python
numero = int("abc")  # Crash aquí
print("Esto nunca se ejecuta")
```

**Salida:**
```
Traceback (most recent call last):
  File "programa.py", line 1, in <module>
    numero = int("abc")
ValueError: invalid literal for int() with base 10: 'abc'
```

**Programa termina abruptamente**

---

<!-- _header: 'Con manejo' -->

# Con try-except

```python
try:
    numero = int("abc")
    print("Esto no se ejecuta")
except ValueError:
    print("Error: ingresá un número válido")

print("El programa continúa")
```

**Salida:**
```
Error: ingresá un número válido
El programa continúa
```

---

<!-- _header: 'Filosofía' -->

# EAFP vs LBYL

**LBYL:** Look Before You Leap
```python
if b != 0:
    resultado = a / b
else:
    print("No se puede dividir por 0")
```

**EAFP:** Easier to Ask Forgiveness than Permission
```python
try:
    resultado = a / b
except ZeroDivisionError:
    print("No se puede dividir por 0")
```

**Python prefiere EAFP**

---

<!-- _header: 'Cuándo usar' -->

# ¿Cuándo manejar excepciones?

**✅ Usar try-except para:**
* Validar entrada de usuario
* Operaciones de archivo/red
* Conversiones de tipo
* Operaciones que pueden fallar

**❌ No usar para:**
* Control de flujo normal
* Validaciones simples (if)
* Ocultar bugs reales

---

<!-- _header: 'Ejemplo práctico' -->

# Pedir número válido

```python
def pedir_numero(mensaje):
    """Pide número hasta que sea válido."""
    while True:
        try:
            valor = input(mensaje)
            return int(valor)
        except ValueError:
            print("❌ Debe ser un número entero")

# Usar
edad = pedir_numero("Edad: ")
print(f"Edad válida: {edad}")
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**Excepciones:**
* Eventos anormales
* Interrumpen el flujo
* Se pueden capturar

**Tipos comunes:**
* ValueError, TypeError
* ZeroDivisionError
* IndexError, KeyError

**Próximo:**
* try-except en detalle

---

<!-- _class: centered -->

# ¿Preguntas?
