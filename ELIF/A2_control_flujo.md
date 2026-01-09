---
title: Control de Flujo (Versión Escolar)
short_title: 2 - Control de Flujo
subtitle: Haciendo que tus programas tomen decisiones inteligentes
---

(control-flujo-escolar)=
# Control de Flujo

¡Hola de nuevo! En el capítulo anterior vimos cómo darle órdenes básicas a la computadora. Ahora vamos a enseñarle a **pensar** y a tomar decisiones.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a hacer que tu programa elija qué camino seguir (como en "Elige tu propia aventura") y a repetir tareas aburridas sin cansarse.
::::

---

## 1. Introducción: Programas Inteligentes 🧠

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** El control de flujo permite que el programa reaccione diferente según lo que pase, en vez de hacer siempre lo mismo como un robot tonto.

**Analogía:** Imaginate un semáforo. Si está en verde, avanzás. Si está en rojo, frenás. Vos mirás el color y **decidís** qué hacer. El control de flujo es el cerebro del programa que toma esas decisiones.

**Vocabulario:**
1.  **Flujo:** El camino que sigue el programa al leer las instrucciones (generalmente de arriba hacia abajo).
2.  **Condición:** Una pregunta que se responde con Sí o No (Verdadero o Falso).
3.  **Bucle (Loop):** Repetir una acción varias veces (como dar vueltas a la manzana).
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Un programa siempre ejecuta todas las líneas de código, una por una, sin saltarse ninguna. ( **Falso**: Con el control de flujo puede saltar partes o repetir otras).
2.  Los programas pueden tomar decisiones por sí mismos sin que nadie los programe. ( **Falso**: Nosotros les damos las reglas para decidir).

---

(condicionales-escolar)=
## 2. Condicionales: Si pasa esto, hacé aquello

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Usamos `if` (si), `elif` (si no, pero...) y `else` (si no) para elegir qué código ejecutar.

**Analogía:** Es como un patovica (guardia) en la puerta de un boliche.
*   **IF:** Si tenés +18, pasás.
*   **ELSE:** Si no, te quedás afuera.

**Vocabulario:**
1.  **if:** "Si sucede esto..." (el comienzo de la decisión).
2.  **else:** "Si no pasó nada de lo anterior..." (el plan B).
3.  **Indentación:** El espacio sangría que le dice a Python qué instrucciones pertenecen a cada decisión. ¡Es obligatorio!
::::

### La Estructura Básica

```python
edad = 15

if edad >= 18:
    print("Podés pasar al boliche 🎉")
else:
    print("Andá a dormir, es tarde 😴")
```

Si hay más de dos opciones, usamos `elif` (una mezcla de "else" e "if"):

```python
nota = 8

if nota >= 9:
    print("¡Sos un genio! 🤓")
elif nota >= 6:
    print("Aprobaste, zafaste. 😎")
else:
    print("A estudiar más para la próxima... 📚")
```

**¡Ojo con la indentación!**
Todo lo que querés que pase *dentro* del `if` tiene que estar empujado hacia la derecha (usando la tecla Tab o 4 espacios). Si no, Python se pierde.

---

(while-escolar)=
## 3. Bucles While: Mientras tanto...

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** El `while` repite un bloque de código **mientras** una condición sea verdadera.

**Analogía:** Imaginate que estás comiendo. **Mientras** tengas hambre, seguís comiendo. Cuando se te pasa el hambre (la condición cambia a Falso), parás. O como cuando tu mamá te dice "No salís de la mesa **mientras** no te termines la verdura".

**Vocabulario:**
1.  **While:** Significa "mientras".
2.  **Bucle Infinito:** Un error donde la condición nunca cambia y el programa se queda "colgado" repitiendo para siempre.
3.  **Contador:** Una variable que usamos para contar cuántas veces repetimos algo.
::::

### Ejemplo: La cuenta regresiva

```python
contador = 5

while contador > 0:
    print(contador)
    contador = contador - 1 # ¡Importante! Cambiamos el contador para no quedarnos atrapados

print("¡Despegue! 🚀")
```

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Si me olvido de restar 1 al contador en el ejemplo anterior, el programa cuenta para siempre. ( **Verdadero**: ¡Cuidado con los bucles infinitos!).
2.  El `while` es útil cuando no sabemos exactamente cuántas veces vamos a repetir algo (ej: pedir contraseña hasta que sea correcta). ( **Verdadero**).

---

(for-escolar)=
## 4. Bucles For: Para cada cosa de la lista...

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** El `for` recorre una lista de cosas y hace algo con cada una de ellas.

**Analogía:** Es como tener una lista de compras. Agarrás la lista y, **para cada** producto que está anotado, lo buscás en la góndola y lo metés al carrito. No parás hasta terminar la lista.

**Vocabulario:**
1.  **Iterar:** La acción de recorrer los elementos uno por uno.
2.  **Range:** Una función mágica que crea una secuencia de números para que el `for` la recorra.
3.  **Elemento:** Cada ítem individual dentro de la lista que recorremos.
::::

### Ejemplo: La Lista de Invitados

```python
amigos = ["Ana", "Pedro", "Julieta"]

for amigo in amigos:
    print(f"¡Hola {amigo}, vení a mi cumple!")
```

### El truco del `range()`

Si querés repetir algo 10 veces, usás `range(10)`.

```python
for numero in range(5):
    print(f"Número: {numero}")
# Ojo: Empieza en 0 y termina en 4 (hace 5 cosas, pero termina uno antes)
```

---

(control-bucles-escolar)=
## 5. Controlando los Bucles: Break y Continue

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Son frenos de emergencia o atajos dentro de los bucles.

**Analogía:**
*   **Break:** Estás buscando las llaves. En cuanto las encontrás, dejás de buscar (**rompes** la búsqueda). No seguís revisando lugares al pepe.
*   **Continue:** Estás repartiendo cartas. Si ves una carta marcada, la saltás (**continuás** con la siguiente) y no se la das a nadie.

**Vocabulario:**
1.  **Break:** Romper/Salir del bucle inmediatamente.
2.  **Continue:** Saltar lo que queda de esta vuelta y pasar a la siguiente.
::::

```python
# Buscando a Nemo
peces = ["Dory", "Marlin", "Nemo", "Bruce"]

for pez in peces:
    if pez == "Nemo":
        print("¡Lo encontré!")
        break # Listo, dejo de buscar
    print(f"Este no es Nemo, es {pez}...")
```

---

(ejercicios-escolar)=
## 6. Ejercicios: ¡A entrenar el cerebro! 🧠

Tratá de resolverlos sin mirar la solución. ¡Vos podés!

### Ejercicio 1: El Portero Electrónico
Creá un programa que pida la edad. Si es menor de 12, dice "Niño". Si tiene entre 12 y 17, dice "Adolescente". Si es 18 o más, dice "Adulto".

````{solution} Solución Ejercicio 1
:class: dropdown
```python
edad = int(input("¿Qué edad tenés? "))

if edad < 12:
    print("Sos un niño.")
elif edad < 18:
    print("Sos un adolescente.")
else:
    print("Sos un adulto.")
```
````

### Ejercicio 2: La Contraseña Testaruda
Pedile al usuario una contraseña. Mientras no sea "secreto123", seguí pidiéndola y decile "Incorrecto". Cuando acierte, decile "Bienvenido".

````{solution} Solución Ejercicio 2
:class: dropdown
```python
clave = "" # Arrancamos vacía
while clave != "secreto123":
    clave = input("Ingresá la contraseña: ")
    if clave != "secreto123":
        print("¡Incorrecto! Probá de nuevo.")

print("¡Bienvenido agente secreto! 🕵️")
```
````

### Ejercicio 3: La Tabla del 7
Usá un bucle `for` para imprimir la tabla del 7 (del 7x1 al 7x10).

````{solution} Solución Ejercicio 3
:class: dropdown
```python
print("Tabla del 7:")
for i in range(1, 11): # Del 1 al 10
    resultado = 7 * i
    print(f"7 x {i} = {resultado}")
```
````

---

### Resumen Final
¡Bien ahí! 🎉 Ya sabés cómo hacer que tus programas tomen decisiones y repitan cosas. Esto es la base de cualquier videojuego o app que uses. En el próximo capítulo vamos a ver **Listas**, que son como mochilas gigantes para guardar muchos datos juntos. ¡Nos vemos!
