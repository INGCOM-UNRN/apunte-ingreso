---
title: Manejo de Excepciones (Versión Escolar)
short_title: 6 - Excepciones
subtitle: Aprendé a evitar que tu programa explote por el aire
---

(excepciones-escolar)=
# Manejo de Excepciones

¡Hola! 👋 Llegamos a una parte clave. Hasta ahora, si algo salía mal en tu programa, este se cerraba de golpe y te mostraba un mensaje rojo horrible. Hoy vamos a aprender a manejar esos errores con elegancia, para que tu programa sea a prueba de balas.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a anticipar errores (como que el usuario escriba letras en vez de números) y a decirle a la compu qué hacer en esos casos en lugar de colgarse.
::::

---

## 1. Introducción: Cuando las cosas salen mal 💥

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Una excepción es un error que ocurre mientras el programa está funcionando, interrumpiendo todo si no lo manejás.

**Analogía:** Imaginate que estás andando en bici (ejecutando el programa).
*   **Sin manejo de excepciones:** Agarrás un bache y te caés de cara al piso. Fin del paseo.
*   **Con manejo de excepciones:** Tenés suspensión en la bici. Sentís el bache, la suspensión lo absorbe, y vos seguís andando como si nada.

**Vocabulario:**
1.  **Excepción:** Un evento inesperado (error) que rompe el flujo normal del programa.
2.  **Crashear:** Cuando el programa se cierra inesperadamente por un error.
3.  **Bug:** Un error en el código.
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Si mi programa tiene un error, no hay forma de evitar que se cierre. ( **Falso**: Usando `try-except` podemos evitar que se cierre).
2.  Las excepciones son siempre culpa del programador. ( **Falso**: A veces el usuario ingresa datos mal o se corta internet).

---

(try-except-escolar)=
## 2. Try y Except: Tu chaleco antibalas 🛡️

Para proteger nuestro código, usamos dos palabras mágicas: `try` (intentar) y `except` (si hay excepción).

```python
try:
    # Acá ponemos el código peligroso
    edad = int(input("¿Cuántos años tenés? "))
    print(f"Tenés {edad} años.")
except:
    # Acá ponemos el plan B si algo falla
    print("¡Che, tenés que poner un número, no letras!")
```

### ¿Cómo funciona?
1.  Python intenta ejecutar lo que está dentro del `try`.
2.  Si todo sale bien, salta el `except` y sigue.
3.  Si ocurre un error en el `try`, salta inmediatamente al `except` y ejecuta ese código de emergencia.

---

(tipos-errores-escolar)=
## 3. Tipos de Errores Comunes 👾

No todos los errores son iguales. Python tiene nombres específicos para cada metida de pata.

::::{admonition} La Fauna de Errores
:class: warning

*   **ValueError:** Cuando el tipo de dato es correcto pero el valor no. (Ej: `int("hola")`).
*   **ZeroDivisionError:** Intentar dividir por cero. (Ej: `10 / 0`). ¡Rompe las matemáticas!
*   **NameError:** Usar una variable que no existe. (Ej: `print(x)` cuando nunca creaste `x`).
*   **TypeError:** Mezclar tipos incompatibles. (Ej: `"hola" + 5`).
*   **IndexError:** Querer sacar algo de una lista que no existe. (Ej: pedir el elemento 10 de una lista de 3).
::::

### Cazando errores específicos

Podés tener un plan distinto para cada tipo de error:

```python
try:
    numero = int(input("Ingresá un número: "))
    resultado = 100 / numero
    print(f"El resultado es {resultado}")

except ValueError:
    print("¡Eso no es un número!")

except ZeroDivisionError:
    print("¡No podés dividir por cero! ¿Querés destruir el universo?")
```

---

(else-finally-escolar)=
## 4. Else y Finally: El equipo completo

Además de `try` y `except`, tenemos a `else` y `finally`.

*   **else:** Se ejecuta solo si **NO** hubo ningún error en el `try`.
*   **finally:** Se ejecuta **SIEMPRE**, pase lo que pase (haya error o no).

**Analogía:**
*   **Try:** Intentás hacer una torta.
*   **Except:** Se te quema (error) -> Pedís delivery.
*   **Else:** Salió rica (sin error) -> La decorás.
*   **Finally:** Pase lo que pase -> Lavás los platos.

```python
try:
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    print("El archivo no existe.")
else:
    print("Leí el archivo con éxito.")
    print(contenido)
finally:
    print("Operación terminada.")
```

---

(ejercicios-escolar)=
## 5. Ejercicios: ¡A romper cosas (y arreglarlas)! 🔨

Tratá de resolverlos vos solo antes de mirar la solución. ¡Vos podés!

### Ejercicio 1: La División Segura
Hacé un programa que pida dos números y los divida. Si el usuario ingresa letras o intenta dividir por cero, mostrá mensajes amigables en vez de errores rojos.

````{solution} Solución Ejercicio 1
:class: dropdown
```python
try:
    a = float(input("Numerador: "))
    b = float(input("Denominador: "))
    print(f"Resultado: {a / b}")
except ValueError:
    print("Error: Ingresá solo números.")
except ZeroDivisionError:
    print("Error: No se puede dividir por cero.")
```
````

### Ejercicio 2: El Buscador de Listas
Tenés una lista de frutas: `["Manzana", "Banana", "Pera"]`. Pedile al usuario un número (índice) y mostrale la fruta correspondiente. Si pone un número fuera de rango o letras, avisale.

````{solution} Solución Ejercicio 2
:class: dropdown
```python
frutas = ["Manzana", "Banana", "Pera"]
try:
    indice = int(input("Elegí un número (0-2): "))
    print(f"Elegiste: {frutas[indice]}")
except ValueError:
    print("Tenés que poner un número entero.")
except IndexError:
    print("Ese número no está en la lista.")
```
````

### Ejercicio 3: Validación de Edad
Pedile la edad al usuario. Si ingresa algo negativo, "levantá" un error propio usando `raise ValueError("La edad no puede ser negativa")`.

````{solution} Solución Ejercicio 3
:class: dropdown
```python
try:
    edad = int(input("Tu edad: "))
    if edad < 0:
        raise ValueError("La edad no puede ser negativa")
    print(f"Edad válida: {edad}")
except ValueError as e:
    print(f"Error: {e}")
```
````

---

### Resumen Final
¡Felicitaciones! 🎉 Ahora tus programas son mucho más profesionales y resistentes. Ya no se van a "colgar" ante el primer error del usuario. Sabés cómo anticipar problemas y manejarlos con elegancia. ¡Sos un experto en control de daños!
