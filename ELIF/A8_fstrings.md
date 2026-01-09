---
title: Guía de F-Strings (Versión Escolar)
short_title: 8 - F-Strings
subtitle: Aprendé a armar textos como un profesional
---

(fstrings-escolar)=
# F-Strings: El Superpoder del Texto en Python

¡Hola! 👋 Hoy vamos a ver una herramienta que te va a cambiar la vida cuando programes: las **f-strings**. Antes, escribir mensajes con variables era un dolor de cabeza, pero con esto es pan comido.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender la forma moderna y fácil de mezclar texto con variables en Python, usando una simple letra `f` antes de las comillas.
::::

---

## 1. Introducción: ¿Qué son las F-Strings? 🤔

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Una f-string es una forma de escribir texto donde podés meter variables y cuentas directamente adentro, sin cortar y pegar pedazos.

**Analogía:** Imaginate que estás escribiendo una carta.
*   **Método viejo (Concatenación):** Escribís "Hola ", agarrás tijera y pegamento, recortás el nombre de tu amigo, lo pegás, y seguís escribiendo. ¡Un lío!
*   **Método nuevo (F-Strings):** Escribís "Hola {nombre}" directamente. Python sabe que tiene que reemplazar `{nombre}` por el valor real. ¡Magia!

**Vocabulario:**
1.  **String:** Cadena de texto (palabras, frases).
2.  **Concatenar:** Unir dos pedazos de texto (como vagones de tren).
3.  **Interpolación:** Meter una variable adentro de un texto.
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Las f-strings son más lentas que usar el signo `+`. ( **Falso**: Son más rápidas y legibles).
2.  Para usar f-strings, tengo que poner una `f` antes de las comillas. ( **Verdadero**: Por eso se llaman **f**-strings).

---

(sintaxis-basica-escolar)=
## 2. Cómo se usan: La Magia de la 'f' ✨

Es re simple. Solo tenés que poner una `f` antes de empezar el texto y usar llaves `{}` para las variables.

```python
nombre = "Mateo"
edad = 16

# Forma vieja y fea (¡No la uses!)
mensaje_feo = "Hola, soy " + nombre + " y tengo " + str(edad) + " años."

# Forma nueva y canchera (F-String)
mensaje_lindo = f"Hola, soy {nombre} y tengo {edad} años."

print(mensaje_lindo)
```

¡Mirá qué limpio queda! No tenés que cerrar comillas a cada rato ni usar `+`.

---

(cuentas-escolar)=
## 3. ¡Podés hacer cuentas adentro! 🧮

No solo sirven para mostrar variables. Podés hacer sumas, restas o lo que quieras adentro de las llaves `{}`.

```python
precio = 100
descuento = 20

print(f"El precio final es: ${precio - descuento}")
# Muestra: El precio final es: $80
```

También podés llamar a funciones:

```python
nombre = "ana"
print(f"Hola {nombre.upper()}") # Muestra: Hola ANA
```

---

(formato-numeros-escolar)=
## 4. Formateando Números (Que se vean lindos) 💅

A veces los números tienen muchos decimales y quedan feos. Con las f-strings podés arreglarlo fácil.

**Analogía:** Es como maquillar los números. El valor sigue siendo el mismo, pero se ve mejor presentado.

### Controlando los decimales (`:.2f`)

Si querés mostrar solo 2 decimales (como para plata), usás `:.2f`.

```python
pi = 3.14159265
print(f"El valor de pi es {pi:.2f}")
# Muestra: El valor de pi es 3.14
```

*   `:` significa "acá viene el formato".
*   `.2` significa "2 decimales".
*   `f` significa "fixed point" (número decimal fijo).

### Mostrando porcentajes (`:.0%`)

```python
bateria = 0.75
print(f"Me queda {bateria:.0%} de batería")
# Muestra: Me queda 75% de batería
```

---

(alineacion-escolar)=
## 5. Alineando Texto (Tablas prolijas) 📏

Si querés hacer una tabla y que quede todo derechito, podés usar alineación.

*   `<` Alinear a la izquierda
*   `>` Alinear a la derecha
*   `^` Centrar

```python
print(f"|{'Izquierda':<15}|")
print(f"|{'Derecha':>15}|")
print(f"|{'Centro':^15}|")
```

Esto es súper útil para hacer listas de precios o puntajes.

---

(debugging-escolar)=
## 6. Truco Ninja para Encontrar Errores (Debugging) 🕵️

Si ponés un signo igual `=` después de la variable adentro de las llaves, Python te muestra el nombre y el valor. ¡Ideal para cuando no entendés qué está pasando!

```python
vidas = 3
puntos = 1500

print(f"{vidas=}")
print(f"{puntos=}")

# Muestra:
# vidas=3
# puntos=1500
```

---

(ejercicios-escolar)=
## 7. Ejercicios: ¡A practicar!

Tratá de resolverlos vos solo antes de mirar la solución. ¡Vos podés!

### Ejercicio 1: El Carnet
Creá variables para `nombre`, `apellido` y `edad`. Usá una f-string para imprimir una frase como: "El alumno Juan Perez tiene 15 años".

````{solution} Solución Ejercicio 1
:class: dropdown
```python
nombre = "Juan"
apellido = "Perez"
edad = 15

print(f"El alumno {nombre} {apellido} tiene {edad} años")
```
````

### Ejercicio 2: Calculadora de Área
Definí `base` y `altura` de un rectángulo. Imprimí: "El área de un rectángulo de [base]x[altura] es [resultado]". ¡Hacé la cuenta adentro de la f-string!

````{solution} Solución Ejercicio 2
:class: dropdown
```python
base = 10
altura = 5

print(f"El área de un rectángulo de {base}x{altura} es {base * altura}")
```
````

### Ejercicio 3: Ticket de Compra
Tenés un producto que vale $45.6789. Imprimilo formateado como dinero (2 decimales).

````{solution} Solución Ejercicio 3
:class: dropdown
```python
precio = 45.6789
print(f"Total a pagar: ${precio:.2f}")
```
````

---

### Resumen Final
¡Excelente! 🎉 Ahora tus programas van a hablar mucho más claro. Las f-strings son una herramienta que vas a usar en casi todos tus códigos de ahora en adelante. Son rápidas, limpias y poderosas. ¡A usarlas!
