---
title: Fundamentos de Programación (Versión Escolar)
short_title: 1 - Fundamentos
subtitle: Aprendiendo a hablar el idioma de las máquinas
---

(fundamentos-escolar)=
# Fundamentos de Programación en Python

¡Hola! Bienvenido al mundo de la programación. Preparate, porque estás a punto de aprender el superpoder de decirle a la computadora qué tiene que hacer.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
En este capítulo vas a aprender a darle órdenes a la computadora, guardar información en "cajitas" llamadas variables y hacer que tu programa haga cuentas y responda preguntas.
::::

---

## 1. Introducción: ¿Qué es programar?

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Programar es escribir una lista de pasos para que la computadora resuelva un problema.

**Analogía:** Imaginate que tenés un robot cocinero que no sabe nada de cocina. Si le decís "hacé una torta", se va a quedar quieto. Tenés que decirle: "Agarrá 3 huevos", "Rompelos en un bowl", "Batilos", etc. Si te olvidás de decirle "sacale la cáscara", ¡va a meter los huevos con cáscara! Programar es dar esas instrucciones precisas.

**Vocabulario:**
1.  **Código:** Las instrucciones escritas en un lenguaje que la compu entiende (como Python).
2.  **Sintaxis:** Las reglas de ortografía y gramática del lenguaje de programación.
3.  **Ejecutar:** Darle "Play" al programa para que la computadora lea y haga lo que le dijiste.
::::

### ¿Por qué Python? 🐍

Python es genial porque se parece mucho a escribir en inglés simple. Otros lenguajes son más complicados y llenos de símbolos raros. Python va al grano.

**Quiz Rápido: ¿Verdadero o Falso?**

1.  La computadora es super inteligente y adivina lo que quiero hacer. ( **Falso**: Es rápida, pero tonta; hace *exactamente* lo que le decís, ni más ni menos).
2.  Python es un lenguaje difícil porque usa muchos símbolos extraños. ( **Falso**: Es famoso por ser limpio y legible).
3.  Programar es solo para genios de matemáticas. ( **Falso**: Es más lógica y organización que matemáticas avanzadas).

---

(primer-programa-escolar)=
## 2. Tu Primer Programa: ¡Hola Mundo!

Desde hace décadas, la tradición es que tu primer programa salude al mundo. ¡No vamos a romper la racha!

```python
print("¡Hola Mundo!")
```

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Usamos `print()` para que la computadora muestre mensajes en la pantalla.

**Analogía:** Es como mandarle un WhatsApp a alguien. Vos escribís el mensaje y apretás enviar. Acá, `print` es el botón de enviar y lo que está entre paréntesis es el mensaje.

**Vocabulario:**
1.  **Función:** Una orden prefabricada que hace una tarea específica (como `print` que muestra texto).
2.  **String (Cadena):** Texto. Para que Python sepa que es texto y no una orden, siempre va entre comillas (`"hola"`).
3.  **Paréntesis `()`:** Son como los brazos de la función, abrazan lo que le querés dar (el mensaje).
::::

### Anatomía de `print`

*   `print`: "Che compu, mostrá esto".
*   `(`: "Acá empieza lo que tenés que mostrar".
*   `"¡Hola Mundo!"`: "Este es el texto".
*   `)`: "Listo, terminó el mensaje".

---

(variables-escolar)=
## 3. Variables: Las Cajitas de la Memoria

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Las variables son nombres que le ponemos a un pedacito de memoria para guardar un dato.

**Analogía:** Pensá en tu mochila o en frascos de cocina. Tenés un frasco con una etiqueta que dice "Azúcar" y adentro tiene azúcar. En programación, creás una "caja" (variable), le pegás una etiqueta (nombre) y adentro guardás un valor (el dato).

**Vocabulario:**
1.  **Variable:** El nombre que usamos para referirnos a un valor guardado.
2.  **Asignar:** Guardar un valor en una variable usando el signo `=`.
3.  **Valor:** La información real (el número, el texto) que guardamos.
::::

### Creando variables

Para crear una variable, elegís un nombre, ponés un igual y el valor. ¡Fácil!

```python
edad = 13
nombre = "Sofía"
tengo_hambre = True
```

**Reglas de etiqueta (para no pasar vergüenza):**
*   Usá nombres claros: `puntos_vida` es mejor que `pv` o `x`.
*   Si son varias palabras, usá guiones bajos: `nombre_completo` (esto se llama *snake_case* 🐍).
*   No pueden empezar con números ni tener espacios.

---

(tipos-datos-escolar)=
## 4. Tipos de Datos: No es lo mismo pera que manzana

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Python necesita saber qué clase de cosa es cada dato para saber qué puede hacer con él.

**Analogía:** En la vida real, no tratás igual a una hamburguesa que a una ecuación. La hamburguesa se come, la ecuación se resuelve. Si intentás comer la ecuación, vas a tener problemas. Los tipos de datos le dicen a Python: "esto es un número (se suma)", "esto es texto (se lee)".

**Vocabulario:**
1.  **Integer (int):** Números enteros, sin coma (ej: contar personas).
2.  **Float:** Números con coma o decimales (ej: medir altura o precio).
3.  **Boolean (bool):** Interruptor de luz. Solo puede ser Verdadero (`True`) o Falso (`False`).
::::

### Los 4 Fantásticos

| Tipo | Nombre Técnico | Ejemplo | Para qué sirve |
| :--- | :--- | :--- | :--- |
| **Entero** | `int` | `15` | Contar cosas enteras (vidas, niveles). |
| **Decimal** | `float` | `1.75` | Cosas precisas (plata, peso). ¡Ojo! Se usa punto `.`, no coma. |
| **Texto** | `str` | `"Hola"` | Palabras y frases. Siempre entre comillas. |
| **Booleano** | `bool` | `True` | Decisiones: Sí o No. |

**Quiz Rápido: ¿Verdadero o Falso?**

1.  `"15"` y `15` son lo mismo para la computadora. ( **Falso**: `"15"` entre comillas es texto, como un dibujo del número. `15` es el valor matemático).
2.  Los booleanos pueden valer `True`, `False` o `Más o menos`. ( **Falso**: Es blanco o negro, prendido o apagado. Sin grises).

---

(operadores-escolar)=
## 5. Operadores: La Calculadora Vitaminizada

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Son símbolos que usamos para hacer cuentas matemáticas o comparar cosas.

**Analogía:** Son como los signos que usás en la escuela (+, -, x), pero con algunos superpoderes extra para programar.

**Vocabulario:**
1.  **Aritmética:** Hacer cuentas (suma, resta, etc.).
2.  **Comparación:** Ver si dos cosas son iguales, mayores o menores.
3.  **Lógica:** Combinar condiciones (esto Y aquello).
::::

### Matemáticas (`+`, `-`, `*`, `/`)

Python es una calculadora de lujo.

```python
vidas = 3
vidas = vidas + 1  # Ahora tenés 4 vidas
puntos = 10 * 2    # Multiplicamos por 2
```

*   `*` es multiplicar.
*   `/` es dividir (siempre da con decimales).
*   `**` es potencia (como $2^3$).
*   `%` es el resto de la división (re útil para saber si un número es par).

### Comparaciones (`>`, `<`, `==`)

Sirven para hacer preguntas que se responden con Sí (`True`) o No (`False`).

*   `==` ¿Son iguales? (Ojo, doble igual. Uno solo `=` es para asignar).
*   `!=` ¿Son distintos?
*   `>` / `<` Mayor / Menor.

### Lógica (`and`, `or`, `not`)

Para cuando tenés condiciones compuestas.
*   **AND (Y):** Las dos cosas tienen que ser verdad. (Tener entrada **Y** ser mayor de edad).
*   **OR (O):** Con que una sea verdad, alcanza. (Tener efectivo **O** tarjeta).
*   **NOT (NO):** Invierte todo. (Si no llueve).

---

(input-output-escolar)=
## 6. Hablando con el Usuario (Entrada y Salida)

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** `input()` escucha lo que escribe el usuario y `print()` le responde.

**Analogía:** Es como una entrevista. `print` es el entrevistador hablando y `input` es cuando le acerca el micrófono al invitado para que responda.

**Vocabulario:**
1.  **Input (Entrada):** Datos que entran al programa desde afuera (teclado).
2.  **Output (Salida):** Datos que el programa muestra hacia afuera (pantalla).
3.  **F-string:** Una forma cheta y fácil de mezclar texto con variables.
::::

### El truco del `input()`

¡Cuidado! `input()` siempre devuelve **texto** (`str`). Aunque escribas un número, Python lo ve como letras.

```python
nombre = input("¿Cómo te llamás? ")
print(f"Hola, {nombre}!")  # Usamos la f antes de las comillas para meter la variable adentro
```

Si querés pedir un número para hacer cuentas, tenés que convertirlo (ver la siguiente sección).

---

(conversion-tipos-escolar)=
## 7. Conversión de Tipos: El Traductor

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** A veces tenemos un dato en formato texto y lo necesitamos como número (o al revés).

**Analogía:** Si tenés un billete de 10 dólares pero querés comprar algo en pesos, necesitás cambiarlo. El valor es el mismo, pero el formato es distinto. `int("10")` cambia el formato de texto a número.

**Vocabulario:**
1.  **Casting:** La acción técnica de convertir un tipo de dato en otro.
2.  **Parsear:** Analizar un texto para extraer información (como sacar un número de un string).
::::

**El problema clásico:**
```python
edad = input("Tu edad: ") # Imaginá que escribís 15
# edad es "15" (texto)
cumple = edad + 1 # ¡ERROR! No podés sumar texto con números
```

**La solución:**
```python
edad_texto = input("Tu edad: ")
edad_numero = int(edad_texto) # ¡Convertimos a entero!
cumple = edad_numero + 1 # Ahora sí, 16.
```

---

(errores-escolar)=
## 8. Errores Comunes: ¡No entres en pánico! 😱

Equivocarse es parte de aprender. En serio, los programadores profesionales viven arreglando errores.

1.  **NameError:** Usaste una variable que no existe (o la escribiste mal).
    *   *Ejemplo:* Pusiste `print(nonbre)` en vez de `nombre`.
2.  **TypeError:** Mezclaste peras con manzanas.
    *   *Ejemplo:* Intentaste sumar `"Hola"` + `5`.
3.  **SyntaxError:** Escribiste mal la "gramática" de Python.
    *   *Ejemplo:* Te olvidaste de cerrar un paréntesis `)`.

---

(ejercicios-escolar)=
## 9. Ejercicios: A practicar

¡Ponete a prueba! Tratá de resolverlos vos solo antes de mirar la solución.

### Ejercicio 1: El Presentador
Creá un programa que te pregunte tu nombre y tu comida favorita, y luego imprima una frase armando todo.

**Ejemplo:**
*Entrada:* Martín, Milanesa.
*Salida:* "A Martín le encanta comer Milanesa."

````{solution} Solución Ejercicio 1
:class: dropdown
```python
nombre = input("¿Cómo te llamás? ")
comida = input("¿Cuál es tu comida favorita? ")
print(f"A {nombre} le encanta comer {comida}.")
```
````

### Ejercicio 2: Calculadora de Edad en 2050
Preguntale al usuario su edad actual y calculá cuántos años va a tener en el 2050 (asumiendo que estamos en 2023, o restando años).

*Pista:* Vas a tener que convertir la entrada a `int`.

````{solution} Solución Ejercicio 2
:class: dropdown
```python
edad_actual = input("¿Qué edad tenés? ")
edad_numero = int(edad_actual)
# Asumiendo año actual 2023, faltan 27 años para 2050
edad_futura = edad_numero + 27
print(f"En el 2050 vas a tener {edad_futura} años. ¡Qué viejo!")
```
````

### Ejercicio 3: El Repetidor
Pedile al usuario una palabra y un número. Mostrá esa palabra repetida tantas veces como diga el número.

*Pista:* En Python podés multiplicar texto por un número (`"Ja" * 3` da `"JaJaJa"`).

````{solution} Solución Ejercicio 3
:class: dropdown
```python
palabra = input("Decime una palabra: ")
cantidad = int(input("¿Cuántas veces la repito? "))
resultado = palabra * cantidad
print(resultado)
```
````

---
**¡Felicitaciones!** Ya tenés los cinturones básicos de programación. Ahora andá a descansar un rato, que en el próximo capítulo vamos a ver cómo hacer que la compu tome decisiones. ¡Nos vemos!
