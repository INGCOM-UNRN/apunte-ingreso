---
title: Funciones (Versión Escolar)
short_title: 4 - Funciones
subtitle: El arte de enseñarle trucos nuevos a la compu
---

(funciones-escolar)=
# Funciones

¡Hola! 👋 Hasta ahora, cada vez que queríamos hacer algo varias veces, teníamos que escribir el mismo código una y otra vez. ¡Un embole! Hoy vamos a ver cómo crear nuestros propios comandos para no repetirnos como loros.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a crear tus propios "miniprogramas" (funciones) dentro de tu programa principal para organizar tu código y hacerlo más fácil de entender.
::::

---

## 1. Introducción: ¿Qué es una Función?

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Una función es un bloque de código con nombre que hace una tarea específica y que podés usar cuando quieras.

**Analogía:** Imaginate una licuadora.
*   Vos no necesitás saber cómo funciona el motor o la cuchilla por dentro.
*   Solo sabés que si le metés fruta (**entrada**) y apretás el botón (**nombre de la función**), te devuelve un licuado (**salida**).
*   ¡Y podés usar la misma licuadora para hacer mil licuados distintos!

**Vocabulario:**
1.  **Definir:** Crear la función, explicarle a la compu qué tiene que hacer.
2.  **Llamar (Invocar):** Usar la función, decirle "¡Hacé lo tuyo!".
3.  **Reutilizar:** Usar el mismo código muchas veces sin volver a escribirlo.
::::

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Una función se ejecuta apenas la escribís en el código. ( **Falso**: Tenés que "llamarla" para que arranque).
2.  Las funciones sirven para no escribir el mismo código 20 veces. ( **Verdadero**).

---

(definir-funciones-escolar)=
## 2. Creando tu Primera Función 🍳

Para crear una función usamos la palabra mágica `def` (de definir).

```python
def saludar():
    print("¡Hola! ¿Todo bien?")
```

Acá solo le enseñamos el truco. Para que lo haga, tenemos que llamarla:

```python
saludar()  # Muestra: ¡Hola! ¿Todo bien?
```

---

(parametros-escolar)=
## 3. Parámetros: Pasame la data 📥

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Los parámetros son variables especiales que le permiten a la función recibir información de afuera para trabajar.

**Analogía:** Es como una máquina de hacer churros. El **parámetro** es el agujero por donde metés la masa. El **argumento** es la masa real (de vainilla, de chocolate) que le ponés cuando la usás.

**Vocabulario:**
1.  **Parámetro:** El nombre de la variable en la definición de la función (`def saludar(nombre)`).
2.  **Argumento:** El valor real que le enviás (`saludar("Juan")`).
3.  **Posicional:** Que importa el orden en que pasás los datos.
::::

```python
def saludar_a(nombre):
    print(f"¡Hola, {nombre}!")

saludar_a("Ana")   # Muestra: ¡Hola, Ana!
saludar_a("Pedro") # Muestra: ¡Hola, Pedro!
```

### Múltiples ingredientes

Podés pedir más de un dato, separándolos con comas:

```python
def sumar(a, b):
    print(f"La suma es {a + b}")

sumar(5, 3) # Muestra: La suma es 8
```

---

(return-escolar)=
## 4. Return: Devolviéndote el resultado 📤

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** `return` es la forma en que la función te entrega el resultado final para que lo uses en otra parte.

**Analogía:**
*   **print()** es como si el cocinero te mostrara la pizza y la tirara a la basura. La ves, pero no te la podés llevar.
*   **return** es cuando el cocinero te entrega la pizza en una caja para que te la lleves y hagas lo que quieras (comerla, guardarla, regalarla).

**Vocabulario:**
1.  **Retornar:** Devolver un valor desde la función al programa principal.
2.  **None:** Lo que devuelve una función si te olvidás de poner `return` (significa "nada").
::::

```python
def cuadrado(numero):
    return numero * numero

resultado = cuadrado(5) # Guardamos el 25 en la variable 'resultado'
print(f"El cuadrado es {resultado}")
```

**¡Ojo al piojo!** Cuando la función llega a un `return`, termina inmediatamente. Todo lo que escribas abajo del `return` (dentro de la función) es invisible para la compu.

---

(scope-escolar)=
## 5. Scope (Alcance): Lo que pasa en Las Vegas... 🕵️

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Las variables creadas dentro de una función solo existen ahí adentro.

**Analogía:** Pensá en tu casa. Las cosas que están dentro de tu casa son tuyas (**locales**). Las cosas que están en la calle (semáforos, árboles) son de todos (**globales**). Vos podés ver el semáforo desde tu ventana, pero el semáforo no puede ver tu tele.

**Vocabulario:**
1.  **Scope Local:** El "barrio" privado de la función. Las variables mueren cuando termina la función.
2.  **Scope Global:** El programa principal. Todos pueden ver estas variables (pero es mejor no tocarlas mucho).
::::

```python
x = 10 # Variable Global

def mi_funcion():
    y = 5 # Variable Local
    print(x) # Puedo ver la global (10)
    print(y) # Puedo ver la local (5)

mi_funcion()
# print(y) # ¡ERROR! 'y' no existe fuera de la función
```

---

(buenas-practicas-escolar)=
## 6. Buenas Prácticas: Sé un Pro 😎

1.  **Nombres claros:** `calcular_promedio` es mejor que `func1`.
2.  **Una cosa a la vez:** Una función debe hacer **una sola tarea** bien hecha. Si hace café, lava la ropa y pasea al perro, ¡dividila en tres funciones!
3.  **Documentá:** Usá comentarios o *docstrings* (comentarios entre `"""`) para explicar qué hace tu función. Ayudate a vos mismo del futuro.

```python
def calcular_area(base, altura):
    """Calcula el área de un rectángulo."""
    return base * altura
```

---

(ejercicios-escolar)=
## 7. Ejercicios: ¡Manos a la obra!

Tratá de resolverlos vos solo antes de mirar la solución. ¡Vos podés!

### Ejercicio 1: El Saludo Personalizado
Creá una función que reciba un nombre y una edad, y devuelva: "Hola [nombre], tenés [edad] años".

````{solution} Solución Ejercicio 1
:class: dropdown
```python
def saludo_completo(nombre, edad):
    return f"Hola {nombre}, tenés {edad} años"

mensaje = saludo_completo("Julieta", 14)
print(mensaje)
```
````

### Ejercicio 2: Calculadora de Descuento
Hacé una función que reciba un precio y un porcentaje de descuento, y devuelva el precio final.

````{solution} Solución Ejercicio 2
:class: dropdown
```python
def calcular_precio_final(precio, descuento):
    monto_descuento = precio * (descuento / 100)
    return precio - monto_descuento

precio_pagar = calcular_precio_final(1000, 20) # 20% de descuento a 1000
print(precio_pagar) # Debería dar 800
```
````

### Ejercicio 3: ¿Es Par?
Creá una función que reciba un número y devuelva `True` si es par y `False` si es impar. (Pista: usá el operador `%`).

````{solution} Solución Ejercicio 3
:class: dropdown
```python
def es_par(numero):
    if numero % 2 == 0:
        return True
    else:
        return False

# O versión pro: return numero % 2 == 0

print(es_par(4)) # True
print(es_par(7)) # False
```
````

---

### Resumen Final
¡Genial! 🚀 Ahora tenés el poder de crear tus propias herramientas. Las funciones son los ladrillos con los que se construyen los programas grandes. En el próximo capítulo vamos a ver cómo organizar estos ladrillos en **Módulos**, para tener todo ordenadito como en una biblioteca. ¡Nos vemos!
