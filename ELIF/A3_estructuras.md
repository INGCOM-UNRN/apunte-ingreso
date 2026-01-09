---
title: Estructuras de Datos (Versión Escolar)
short_title: 3 - Estructuras de Datos
subtitle: Organizá tus datos como un profesional
---

(estructuras-datos-escolar)=
# Estructuras de Datos

¡Hola! 👋 En este capítulo vamos a ver cómo guardar muchos datos de forma ordenada. Hasta ahora guardábamos una cosa por vez, pero la vida real es más compleja.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a guardar colecciones de cosas (como listas de compras, coordenadas o agendas) en vez de tener mil variables sueltas desparramadas por ahí.
::::

---

## 1. Introducción: De la Variable Solitaria a la Colección

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Las estructuras de datos son como mochilas o cajas organizadoras para guardar mucha información junta y que no se te pierda nada.

**Analogía:** Imaginate que tenés que llevar 50 lápices a la escuela.
*   **Sin estructura:** Llevás los 50 lápices sueltos en las manos y bolsillos. ¡Se te caen!
*   **Con estructura:** Los ponés todos adentro de una cartuchera. Llevás **un solo objeto** (la cartuchera) que contiene los 50 lápices.

**Vocabulario:**
1.  **Colección:** Un grupo de cosas guardadas juntas.
2.  **Elemento:** Cada una de las cosas que están adentro de la colección.
3.  **Índice:** El número que indica en qué posición está cada cosa.
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Si quiero guardar las notas de 30 alumnos, necesito crear 30 variables llamadas `nota1`, `nota2`, `nota3`... ( **Falso**: Usás una sola lista con 30 notas).
2.  Una estructura de datos me permite manejar muchos datos con un solo nombre de variable. ( **Verdadero**).

---

(listas-escolar)=
## 2. Listas: La Lista del Supermercado 🛒

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Una lista es una fila ordenada de cosas que podés modificar (agregar, sacar o cambiar).

**Analogía:** Pensá en tu lista de compras. Escribís "Pan", "Leche", "Huevos". Sabés que "Pan" es el primero. Si te arrepentís, tachás "Huevos". Si te acordás de algo, agregás "Galletitas" al final.

**Vocabulario:**
1.  **Mutable:** Que se puede cambiar, modificar o editar.
2.  **Append:** La orden para agregar algo al final de la lista.
3.  **Corchetes `[]`:** Los símbolos que usamos para crear una lista.
::::

### Creando y Usando Listas

```python
# Mi mochila de cosas
mochila = ["Cuaderno", "Lápiz", "Goma"]

# ¡Ojo! En programación contamos desde 0
print(mochila[0])  # Muestra: Cuaderno
print(mochila[1])  # Muestra: Lápiz
```

### Modificando la Lista

```python
# Me olvidé la regla, la agrego al final
mochila.append("Regla")

# Perdí la goma (estaba en la posición 2)
mochila.pop(2)

# Cambio el lápiz por una lapicera (posición 1)
mochila[1] = "Lapicera"
```

---

(tuplas-escolar)=
## 3. Tuplas: Lo que está escrito en piedra 🗿

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Una tupla es una lista que **NO** se puede cambiar una vez creada.

**Analogía:** Una lista es como escribir con lápiz (podés borrar y corregir). Una tupla es como tallar en piedra o un tatuaje: una vez que está, queda así para siempre.

**Vocabulario:**
1.  **Inmutable:** Que NO se puede cambiar. Es fijo.
2.  **Paréntesis `()`:** Los símbolos que usamos para crear una tupla.
::::

### ¿Para qué quiero algo que no puedo cambiar?

Para proteger datos importantes. Por ejemplo, las coordenadas GPS de tu casa no cambian a cada rato.

```python
# Coordenadas (Latitud, Longitud)
casa = (-34.6, -58.3)

# casa[0] = -35.0  <-- ¡ERROR! No podés mover tu casa así de fácil.
```

---

(diccionarios-escolar)=
## 4. Diccionarios: Etiquetas y Valores 🏷️

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Un diccionario guarda pares de datos: una "clave" (la etiqueta) y un "valor" (el contenido).

**Analogía:** Pensá en una agenda de contactos del celu. Vos no buscás "contacto número 5", buscás por nombre ("Mamá", "Juan").
*   **Clave:** El nombre ("Juan").
*   **Valor:** El número de teléfono ("11-5555-4444").

**Vocabulario:**
1.  **Clave (Key):** La etiqueta única para encontrar un dato.
2.  **Valor (Value):** La información guardada bajo esa etiqueta.
3.  **Llaves `{}`:** Los símbolos para crear diccionarios.
::::

### Creando un Diccionario

```python
# Perfil de un jugador
jugador = {
    "nombre": "Messi",
    "equipo": "Inter Miami",
    "goles": 800
}

print(jugador["equipo"])  # Muestra: Inter Miami
```

---

(sets-escolar)=
## 5. Sets (Conjuntos): El Club de los Únicos 🦄

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Un set es una bolsa de cosas donde **no hay orden** y **no se permiten repetidos**.

**Analogía:** Imaginate el álbum de figuritas. Si te toca una repe, no la pegás dos veces en el álbum. El álbum (set) solo tiene una de cada una. Y no importa si pegaste primero la 10 o la 5, están todas ahí.

**Vocabulario:**
1.  **Único:** Que no se repite.
2.  **Desordenado:** Que no tiene un "primero" o "segundo".
::::

```python
# Invitados a la fiesta (sin repetidos)
invitados = {"Ana", "Pedro", "Ana", "Luis"}

print(invitados)
# Muestra: {'Ana', 'Pedro', 'Luis'} <-- ¡Ana aparece una sola vez!
```

---

(comparacion-escolar)=
## 6. ¿Cuál elijo? Guía rápida 🤔

| Estructura | Símbolo | ¿Ordenada? | ¿Se cambia? | ¿Repetidos? | Ejemplo |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Lista** | `[]` | Sí | Sí | Sí | Compras del súper |
| **Tupla** | `()` | Sí | No | Sí | Coordenadas GPS |
| **Diccionario**| `{k:v}` | Sí* | Sí | Claves no | Agenda de contactos |
| **Set** | `{}` | No | Sí | No | Figuritas del álbum |

*(Desde versiones nuevas de Python, los diccionarios recuerdan el orden de inserción, pero su fuerte es buscar por clave).*

---

(ejercicios-escolar)=
## 7. Ejercicios: ¡A organizar el caos!

Tratá de resolverlos vos solo antes de mirar la solución. ¡Vos podés!

### Ejercicio 1: El Organizador de Torneos
Tenés una lista de equipos. El último equipo se bajó del torneo y entró uno nuevo. Modificá la lista.

*Equipos:* Boca, River, Racing, Independiente.
*Cambio:* Sale Independiente, entra San Lorenzo.

````{solution} Solución Ejercicio 1
:class: dropdown
```python
equipos = ["Boca", "River", "Racing", "Independiente"]
# Opción 1: Sacar y agregar
equipos.pop() # Saca el último
equipos.append("San Lorenzo")

# Opción 2: Reemplazar directo (si sabés la posición)
# equipos[3] = "San Lorenzo"

print(equipos)
```
````

### Ejercicio 2: La Agenda Secreta
Creá un diccionario con los datos de un agente secreto: nombre clave, nivel de acceso y misión actual. Luego imprimí: "El agente [Nombre] está en la misión [Misión]".

````{solution} Solución Ejercicio 2
:class: dropdown
```python
agente = {
    "nombre": "007",
    "nivel": "Top Secret",
    "mision": "Salvar el mundo"
}

print(f"El agente {agente['nombre']} está en la misión {agente['mision']}.")
```
````

### Ejercicio 3: El Detector de Repetidos
Tenés una lista con números: `[1, 2, 2, 3, 4, 4, 5]`. Usá un **Set** para mostrar solo los números únicos.

````{solution} Solución Ejercicio 3
:class: dropdown
```python
numeros = [1, 2, 2, 3, 4, 4, 5]
unicos = set(numeros)
print(unicos) # {1, 2, 3, 4, 5}
```
````

---

### Resumen Final
¡Excelente! 🎉 Ahora ya no tenés datos sueltos, tenés **estructuras**. Sabés cuándo usar una mochila (lista), una caja fuerte (tupla), una agenda (diccionario) o un álbum de figuritas (set). En el próximo capítulo vamos a ver **Funciones**, que son como mini-programas dentro de tu programa. ¡Nos vemos!
