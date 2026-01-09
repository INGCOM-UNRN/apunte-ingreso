---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Funciones en Python'
footer: 'Definición, parámetros, scope y buenas prácticas'
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Funciones en Python

**Definición, parámetros, scope, documentación y buenas prácticas**

<!--
¡Buenas a todos! Hoy vamos a hablar de una de las herramientas más importantes en la caja de herramientas de cualquier programador: las Funciones. Hasta ahora, veníamos escribiendo código secuencial, todo junto. Las funciones nos permiten empaquetar lógica, darle un nombre y usarla cuando queramos. Es como pasar de escribir recetas en un papel a tener electrodomésticos que hacen el trabajo por nosotros.
-->
---

## ¿Qué vas a aprender?

* Definir y llamar funciones para **reutilizar código**
* Trabajar con **parámetros y argumentos**
* **Retornar valores** y usarlos en tu programa
* Entender el **scope** (alcance) de las variables
* **Documentar funciones** profesionalmente
* Aplicar **buenas prácticas** en el diseño
* **Descomponer problemas** complejos en funciones simples

<!--
¿Qué vamos a ver hoy? Primero, cómo crear nuestras propias funciones y cómo usarlas. Vamos a aprender a pasarles información (parámetros) y a recibir resultados (retorno). También vamos a tocar un tema clave: el scope o alcance de las variables, para evitar errores tontos. Y por supuesto, vamos a ver cómo escribir funciones profesionales, bien documentadas y prolijas.
-->
---

## ¿Qué es una Función?

Una **función** es un bloque de código reutilizable que realiza una tarea específica.

**Piénsalo así:**
- **Receta de cocina**: Instrucciones para hacer un plato
- **Máquina**: Entra algo, procesa, sale algo
- **Control remoto**: Apretás un botón, ejecuta una acción

```python
def saludar():
    print("¡Hola!")

saludar()  # Llamar la función
```

<!--
Imaginen una función como una maquinita. Vos le metés ingredientes por un lado (argumentos), la máquina hace su magia adentro (código), y te saca un producto terminado (valor de retorno). Lo mejor es que no necesitás saber cómo funciona la máquina por dentro cada vez que la usás, solo necesitás saber qué botón apretar. Eso es abstracción.
-->
---

## ¿Por qué Usar Funciones?

**Sin funciones:**
```python
# Calcular área de 3 rectángulos
area1 = 5 * 10
area2 = 8 * 12
area3 = 6 * 9
```

**Con funciones:**
```python
def calcular_area(base, altura):
    return base * altura

area1 = calcular_area(5, 10)
area2 = calcular_area(8, 12)
area3 = calcular_area(6, 9)
```

**Ventajas:** Reutilización, claridad, mantenimiento

<!--
Miren la diferencia. Sin funciones, si tenés que calcular el área de 3 rectángulos, escribís la misma fórmula 3 veces. Si te equivocaste en la fórmula, tenés que corregirla en 3 lugares. Con funciones, definís la lógica UNA vez y la llamás 3 veces. Es más limpio, menos propenso a errores y mucho más fácil de leer.
-->
---

## Beneficios de las Funciones

**🔄 Reutilización:**
```python
# Una vez definida, usala mil veces
saludar()
saludar()
saludar()
```

**🧩 Organización:**
```python
# Código estructurado y modular
leer_datos()
procesar_datos()
mostrar_resultados()
```

**🔧 Mantenimiento:**
```python
# Cambios en un solo lugar
def calcular_descuento(precio):
    return precio * 0.15  # Cambiar % aquí
```

<!--
Tres pilares fundamentales: Reutilización (escribir una vez, usar muchas), Organización (dividir problemas grandes en partes chicas) y Mantenimiento (si hay un bug, lo arreglás en un solo lugar y se arregla en todo el programa). Es la base de la programación modular.
-->
---

<!-- _class: lead -->

# Definir y Llamar Funciones

<!--
Para crear una función usamos la palabra clave `def`. Le ponemos un nombre (en minúsculas y con guiones bajos, por convención), paréntesis `()` y dos puntos `:`. Adentro va todo el código indentado. Ojo, definirla no hace que se ejecute. Para que 'arranque', hay que llamarla por su nombre con paréntesis `saludar()`.
-->
---

## Tu Primera Función

**Sintaxis básica:**
```python
def nombre_funcion():
    # Código de la función
    print("Hola desde la función")
```

**Ejemplo completo:**
```python
def saludar():
    """Función que saluda al usuario."""
    print("¡Hola!")
    print("¡Bienvenido!")

# Llamar la función
saludar()
```

<!--
Vamos a diseccionar una función real. Tiene una cabecera con `def`, nombre y parámetros. Tiene un docstring (esa cadena entre triples comillas) que explica qué hace. Tiene el cuerpo con la lógica. Y tiene un `return` que devuelve el resultado al mundo exterior. Si entienden estas partes, entienden todo.
-->
---

## Anatomía de una Función

```python
def calcular_area(base, altura):
    """Calcula el área de un rectángulo."""
    area = base * altura
    return area
```

**Componentes:**
1. `def` → Palabra clave para definir función
2. `calcular_area` → Nombre de la función
3. `(base, altura)` → Parámetros
4. `:` → Dos puntos (obligatorio)
5. Docstring → Documentación
6. Cuerpo → Código indentado
7. `return` → Valor que devuelve

<!--
El flujo es como un desvío en la ruta. El programa viene ejecutando línea por línea. Cuando encuentra una llamada a función, 'salta' a la definición de esa función, ejecuta todo lo que hay ahí, y cuando termina, 'vuelve' al lugar exacto donde estaba y sigue. Es un viaje de ida y vuelta.
-->
---

## Flujo de Ejecución

```python
print("Inicio")

def contar_hasta_tres():
    print("Uno")
    print("Dos")
    print("Tres")

print("Antes de llamar")
contar_hasta_tres()  # Salta aquí
print("Después de llamar")
print("Fin")
```

**El programa:**
1. Ejecuta línea por línea
2. Al llegar a la llamada, **salta** a la función
3. Ejecuta todo el código de la función
4. **Vuelve** justo después de la llamada
5. Continúa con el resto

<!--
Las funciones son más útiles cuando son flexibles. En lugar de una función que solo salude a 'Mundo', hacemos una que salude a QUIEN SEA. Para eso usamos parámetros. Son como variables huecas que se llenan cuando llamamos a la función.
-->
---

<!-- _class: lead -->

# Parámetros y Argumentos

<!--
Acá hay una distinción técnica fina pero útil. 'Parámetro' es la variable en la definición (el nombre del marcador de posición). 'Argumento' es el valor real que le enviás cuando la usás. En la práctica, los usamos casi como sinónimos, pero está bueno saber la diferencia.
-->
---

## Funciones que Reciben Información

Las funciones son más útiles cuando trabajan con diferentes datos:

```python
def saludar_persona(nombre):
    """Saluda a una persona por su nombre."""
    print(f"¡Hola, {nombre}! ¿Cómo estás?")

# Misma función, diferentes datos
saludar_persona("Ana")
saludar_persona("Bruno")
saludar_persona("Carlos")
```

<!--
Podés pasar todos los datos que quieras. Nombre, edad, ciudad... Python los recibe en orden. Es como llenar un formulario: campo 1, campo 2, campo 3. Si te equivocás en el orden, te pueden quedar datos cruzados.
-->
---

## Vocabulario: Parámetro vs Argumento

**Parámetro** = Variable en la definición (el "molde")
```python
def saludar(nombre):  # ← "nombre" es el PARÁMETRO
    print(f"Hola, {nombre}")
```

**Argumento** = Valor en la llamada (lo que ponés en el molde)
```python
saludar("Ana")  # ← "Ana" es el ARGUMENTO
```

<!--
Por defecto, los argumentos son posicionales. El primero va al primero, el segundo al segundo. Si tenés una función `restar(a, b)`, `restar(10, 3)` no es lo mismo que `restar(3, 10)`. El orden es sagrado acá.
-->
---

## Múltiples Parámetros

Una función puede recibir varios datos:

```python
def presentar_persona(nombre, edad, ciudad):
    """Presenta a una persona con todos sus datos."""
    print(f"Te presento a {nombre}")
    print(f"  → Tiene {edad} años")
    print(f"  → Vive en {ciudad}")

presentar_persona("Ana", 20, "Buenos Aires")
presentar_persona("Bruno", 22, "Córdoba")
```

<!--
Pero Python tiene un truco genial: los argumentos con nombre o 'keyword arguments'. Podés decir explícitamente `ingrediente='queso'`. Ahí el orden deja de importar porque estás etiquetando cada valor. Es mucho más legible, sobre todo en funciones con muchos parámetros.
-->
---

## Argumentos Posicionales

Los argumentos se pasan **en orden**:

```python
def restar(a, b):
    """Resta b de a."""
    resultado = a - b
    print(f"{a} - {b} = {resultado}")
    return resultado

restar(10, 3)   # 10 - 3 = 7
restar(3, 10)   # 3 - 10 = -7  ← Orden diferente
```

**⚠️ El orden importa:**
```python
def describir_mascota(nombre, tipo, edad):
    print(f"{nombre} es un {tipo} de {edad} años")

describir_mascota("Firulais", "perro", 5)  # ✓ Correcto
describir_mascota("perro", 5, "Firulais")  # ✗ Incorrecto
```

<!--
Podés mezclar. Pero ojo: los posicionales (los que dependen del orden) siempre tienen que ir PRIMERO. No podés tirar un nombre y después volver a confiar en el orden. Python te va a gritar si intentás eso.
-->
---

## Argumentos con Nombre (Keyword)

Podés especificar qué argumento va a qué parámetro:

```python
def hacer_pizza(tamaño, ingrediente, extra_queso):
    """Prepara una pizza personalizada."""
    print(f"Pizza {tamaño}")
    print(f"  → Ingrediente: {ingrediente}")
    print(f"  → Extra queso: {'Sí' if extra_queso else 'No'}")

# Con keyword arguments, el orden no importa
hacer_pizza(tamaño="grande", ingrediente="pepperoni", extra_queso=True)
hacer_pizza(extra_queso=False, ingrediente="jamón", tamaño="mediana")
```

**Ventaja:** Más claro y legible

<!--
Esto confunde a muchos al principio. `print` muestra algo en la pantalla para el HUMANO. `return` devuelve un dato al PROGRAMA para que lo siga usando. Si una función solo hace `print`, su valor de retorno es `None` y no podés hacer cuentas con eso.
-->
---

## Mezclar Posicionales y Keyword

```python
def crear_usuario(nombre, edad, ciudad, premium=False):
    print(f"Usuario: {nombre}, {edad} años")
    print(f"Ciudad: {ciudad}")
    print(f"Premium: {premium}")

# Válido: posicionales primero, keyword después
crear_usuario("Ana", 25, "Buenos Aires", premium=True)
crear_usuario("Bruno", 30, ciudad="Córdoba", premium=False)

# ❌ Inválido: keyword antes de posicional
# crear_usuario(nombre="Ana", 25, "Buenos Aires")
```

<!--
Regla de oro: si la función hace un cálculo, usá `return`. Si la función es para interactuar con el usuario o debuggear, usá `print`. Las funciones que retornan valores son más fáciles de testear y de reutilizar en otros contextos.
-->
---

<!-- _class: lead -->

# Retornar Valores

<!--
Python es muy generoso y te deja devolver varias cosas a la vez. En realidad, te está devolviendo una tupla, pero vos podés desempaquetarla en variables sueltas al vuelo. Es comodísimo para funciones como 'división con resto' o coordenadas.
-->
---

## `print()` vs `return`

**`print()` - Mostrar en pantalla:**
```python
def saludar():
    print("Hola")  # Solo muestra

saludar()  # Imprime "Hola"
x = saludar()  # x = None (no retorna nada)
```

**`return` - Devolver un valor:**
```python
def sumar(a, b):
    return a + b  # Devuelve el resultado

resultado = sumar(5, 3)  # resultado = 8
print(resultado * 2)  # Podés usarlo: 16
```

<!--
El `return` también funciona como un botón de 'Eject'. En cuanto se ejecuta, la función termina INSTANTÁNEAMENTE. No importa si hay código abajo. Esto es genial para validar cosas al principio (Guard clauses) y salir rápido si algo está mal.
-->
---

## ¿Cuándo usar cada uno?

**Usá `return` cuando:**
- Necesitás el resultado para cálculos posteriores
- La función debe ser reutilizable
- Querés testear la función

**Usá `print()` cuando:**
- Solo querés mostrar información
- Debugging temporal
- Dentro de funciones principales (`main`)

```python
# ✓ Retorna para reutilizar
def calcular_area(base, altura):
    return base * altura

# ✓ Muestra solo cuando necesario
area = calcular_area(5, 10)
print(f"El área es: {area}")
```

<!--
Si te olvidás del `return`, no pasa nada grave, pero la función devuelve `None` (nulo). Es importante tenerlo en cuenta si esperás recibir un número o un texto. A veces `None` es un resultado válido, a veces es un error.
-->
---

## Retornar Múltiples Valores

Python permite retornar múltiples valores con tuplas:

```python
def dividir_con_resto(dividendo, divisor):
    """Retorna cociente y resto."""
    cociente = dividendo // divisor
    resto = dividendo % divisor
    return cociente, resto

# Desempaquetar
c, r = dividir_con_resto(17, 5)
print(f"17 ÷ 5 = {c} con resto {r}")
# 17 ÷ 5 = 3 con resto 2
```

<!--
El Scope o Alcance es fundamental. Las variables no viven para siempre ni se ven desde todos lados. Hay variables locales (dentro de la función) y globales (fuera). Lo que pasa en Las Vegas (la función), queda en Las Vegas.
-->
---

## Retorno Temprano (Early Return)

Podés usar `return` para salir anticipadamente:

```python
def dividir(a, b):
    """Divide dos números de forma segura."""
    if b == 0:
        return None  # Salida temprana
    
    return a / b

resultado = dividir(10, 0)
if resultado is None:
    print("No se puede dividir por cero")
else:
    print(f"Resultado: {resultado}")
```

**Ventaja:** Evita anidación excesiva

<!--
Las variables que creás adentro de una función son invisibles desde afuera. Nacen cuando empieza la función y mueren cuando termina. Si intentás imprimir `area` desde afuera, Python te va a decir '¿de qué me estás hablando?'.
-->
---

## Sin Return Explícito

Si no hay `return`, la función retorna `None`:

```python
def saludar(nombre):
    print(f"Hola {nombre}")
    # No hay return

resultado = saludar("Ana")
print(resultado)  # None
```

<!--
Las variables de afuera (globales) se pueden LEER desde adentro, pero NO se pueden MODIFICAR así nomás (a menos que uses `global`, que es mala palabra en muchos casos). Traten de evitar depender de variables globales, hacen que el código sea difícil de entender.
-->
---

<!-- _class: lead -->

# Scope (Alcance) de Variables

<!--
Si tenés una variable global `x` y definís una local `x` adentro de una función, la local gana. Es como si te pusieras auriculares: dejás de escuchar la música de afuera y solo escuchás la tuya. Esto se llama 'Shadowing'.
-->
---

## ¿Qué es el Scope?

El **scope** determina **dónde** es visible una variable.

**Variables locales:** Solo dentro de la función
**Variables globales:** En todo el programa

```python
# Global
edad_global = 25

def mostrar_edad():
    # Local
    edad_local = 30
    print(edad_global)  # ✓ Puede acceder a global
    print(edad_local)   # ✓ Puede acceder a local

mostrar_edad()
print(edad_global)  # ✓ Puede acceder a global
print(edad_local)   # ❌ Error: no existe aquí
```

<!--
Resumen de Scope: Pasen los datos necesarios como parámetros. Devuelvan los resultados con return. No toquen variables globales desde adentro de las funciones. Así se evitan dolores de cabeza y bugs difíciles de rastrear.
-->
---

## Variables Locales

Las variables definidas dentro de una función son **locales**:

```python
def calcular_area(base, altura):
    area = base * altura  # Variable local
    return area

resultado = calcular_area(5, 10)
print(resultado)  # 50
print(area)  # ❌ NameError: 'area' no existe aquí
```

**Regla:** Las variables locales **solo existen dentro de la función**

<!--
Podés hacer que algunos parámetros sean opcionales dándoles un valor por defecto. Si el usuario no manda nada, se usa el default. Si manda algo, se usa lo que mandó. Es súper práctico para configuraciones.
-->
---

## Variables Globales

Variables definidas fuera de funciones:

```python
contador = 0  # Global

def incrementar():
    global contador  # Necesario para modificar
    contador += 1

incrementar()
incrementar()
print(contador)  # 2
```

**⚠️ Evitá modificar variables globales:** Es mejor usar parámetros y `return`

<!--
Regla de sintaxis: los que tienen default van AL FINAL. No podés poner uno opcional y después uno obligatorio, porque Python no sabría a quién asignarle los valores posicionales.
-->
---

## Shadowing (Ocultamiento)

Variable local con mismo nombre que global:

```python
x = "global"

def funcion():
    x = "local"  # Oculta la global
    print(f"Dentro: {x}")  # local

funcion()
print(f"Fuera: {x}")  # global (no cambió)
```

**La variable local "oculta" a la global dentro de la función**

<!--
¡Alerta de error clásico! Nunca usen listas o diccionarios vacíos como valor por defecto (`lista=[]`). Python crea ese objeto UNA sola vez al definir la función, y se reutiliza en cada llamada. Si lo modificás, el cambio persiste. Usen `None` y inicialicen adentro.
-->
---

## Reglas de Oro del Scope

**✓ HACÉ:**
- Usar parámetros para pasar datos
- Retornar resultados con `return`
- Usar constantes globales (MAYÚSCULAS)
- Mantener variables locales

**✗ NO HAGAS:**
- Usar `global` para modificar variables
- Depender de variables globales mutables
- Nombres que oculten globales importantes

<!--
A veces no sabés cuántos datos te van a mandar. `*args` (el nombre puede ser cualquiera, pero el asterisco es lo que importa) te permite recibir infinitos argumentos posicionales y los mete todos en una tupla.
-->
---

<!-- _class: lead -->

# Parámetros por Defecto

<!--
Lo mismo para argumentos con nombre. `**kwargs` (doble asterisco) te permite recibir cualquier cosa con nombre y te lo guarda en un diccionario. Es muy potente para funciones de configuración flexibles.
-->
---

## Valores por Defecto

Podés definir valores por defecto para parámetros:

```python
def saludar(nombre, saludo="Hola"):
    """Saluda a una persona."""
    return f"{saludo}, {nombre}!"

# Usar valor por defecto
print(saludar("Ana"))  # Hola, Ana!

# Especificar valor diferente
print(saludar("Ana", "Buenos días"))  # Buenos días, Ana!
print(saludar("Ana", saludo="Buenas tardes"))  # Buenas tardes, Ana!
```

<!--
Podés combinar todo. Pero el orden es estricto: 1. Posicionales normales, 2. `*args`, 3. Defaults/Keyword-only, 4. `**kwargs`. Es la jerarquía de parámetros de Python.
-->
---

## Orden de Parámetros

Los parámetros con valores por defecto deben ir **después** de los obligatorios:

```python
# ✓ Correcto
def presentar(nombre, edad, ciudad="Buenos Aires"):
    print(f"{nombre}, {edad} años, {ciudad}")

presentar("Ana", 25)  # Usa default
presentar("Bruno", 30, "Córdoba")  # Especifica ciudad

# ❌ Incorrecto - SyntaxError
# def presentar(nombre, ciudad="Buenos Aires", edad):
#     ...
```

<!--
Las funciones Lambda son funciones 'de bolsillo'. Son anónimas (sin nombre) y tienen una sola línea. Son útiles para cosas rápidas y descartables, como una regla de ordenamiento o una transformación simple.
-->
---

## ⚠️ Valores Mutables por Defecto

**Problema común:**
```python
# ❌ No hacer esto
def agregar_item(item, lista=[]):
    lista.append(item)
    return lista

print(agregar_item(1))  # [1]
print(agregar_item(2))  # [1, 2] ¡Inesperado!
print(agregar_item(3))  # [1, 2, 3] ¡Acumula!
```

**Solución:**
```python
# ✓ Usar None como default
def agregar_item(item, lista=None):
    if lista is None:
        lista = []
    lista.append(item)
    return lista
```

<!--
No abusen de las lambdas. Son geniales para pasarlas como argumento a `map`, `filter` o `sort`. Pero si la lógica es compleja, definan una función normal con `def`. La legibilidad siempre gana.
-->
---

<!-- _class: lead -->

# Número Variable de Argumentos

<!--
La regla es simple: si necesitás más de una expresión, o si necesitás documentarla, o si la vas a usar en varios lados, usá `def`. Lambda es solo para snippets de código rápidos.
-->
---

## `*args` - Argumentos Posicionales Variables

Recibir cualquier cantidad de argumentos posicionales:

```python
def sumar(*numeros):
    """Suma cualquier cantidad de números."""
    total = 0
    for num in numeros:
        total += num
    return total

print(sumar(1, 2, 3))  # 6
print(sumar(10, 20, 30, 40))  # 100
print(sumar(5))  # 5
```

**`*args` crea una tupla con todos los argumentos**

<!--
Documentar es un acto de amor a tu yo del futuro. Los Docstrings son la forma estándar de explicar qué hace tu función. Se escriben justo abajo del `def` y herramientas como `help()` los leen.
-->
---

## `**kwargs` - Argumentos con Nombre Variables

Recibir cualquier cantidad de argumentos keyword:

```python
def imprimir_info(**datos):
    """Imprime información personalizada."""
    for clave, valor in datos.items():
        print(f"{clave}: {valor}")

imprimir_info(nombre="Ana", edad=25, ciudad="Buenos Aires")
# nombre: Ana
# edad: 25
# ciudad: Buenos Aires
```

**`**kwargs` crea un diccionario con todos los argumentos keyword**

<!--
Un buen docstring explica QUÉ hace, qué ARGUMENTOS espera (y sus tipos) y qué RETORNA. Si pueden agregar un ejemplo de uso, mejor todavía. Acostúmbrense a escribir esto, es señal de profesionalismo.
-->
---

## Combinar `*args` y `**kwargs`

```python
def funcion_completa(arg1, arg2, *args, kwarg1="default", **kwargs):
    print(f"Posicionales obligatorios: {arg1}, {arg2}")
    print(f"Args adicionales: {args}")
    print(f"Kwarg con default: {kwarg1}")
    print(f"Kwargs adicionales: {kwargs}")

funcion_completa(1, 2, 3, 4, kwarg1="valor", extra1="a", extra2="b")
```

**Orden:** Posicionales, `*args`, keyword, `**kwargs`

<!--
Miren este ejemplo. Es claro, completo y tiene ejemplos. Cualquiera que lea esto sabe exactamente cómo usar la función sin tener que leer el código interno. Esa es la meta.
-->
---

<!-- _class: lead -->

# Funciones Lambda

<!--
Nombres. Por favor, usen nombres que signifiquen algo. `calc(x,y)` no me dice nada. `calcular_area(base, altura)` me dice todo. El código se lee muchas más veces de las que se escribe.
-->
---

## Funciones Lambda (Anónimas)

Funciones de **una línea** sin nombre:

```python
# Función normal
def cuadrado(x):
    return x ** 2

# Función lambda equivalente
cuadrado = lambda x: x ** 2

print(cuadrado(5))  # 25
```

**Sintaxis:** `lambda parametros: expresion`

<!--
SRP: Principio de Responsabilidad Única. Una función, una tarea. Si tu función se llama `procesar_todo`, probablemente está haciendo demasiado. Dividila en `validar`, `calcular` y `guardar`. Es mucho más fácil de mantener.
-->
---

## ¿Cuándo usar Lambda?

**Úsalas cuando:**
- Función muy simple (una línea)
- Solo se usa una vez
- Como argumento de otra función

```python
numeros = [1, 2, 3, 4, 5]

# Con lambda
cuadrados = list(map(lambda x: x ** 2, numeros))
print(cuadrados)  # [1, 4, 9, 16, 25]

# Filtrar pares
pares = list(filter(lambda x: x % 2 == 0, numeros))
print(pares)  # [2, 4]

# Ordenar por longitud
palabras = ["python", "es", "genial"]
ordenadas = sorted(palabras, key=lambda x: len(x))
print(ordenadas)  # ['es', 'genial', 'python']
```

<!--
Funciones cortas. Si tenés que scrollear para ver el final de la función, es muy larga. Tratamos de mantenerlas en 20-30 líneas. Si es más larga, seguramente se puede dividir en sub-funciones.
-->
---

## Lambda vs Función Normal

```python
# Lambda: para cosas simples
doble = lambda x: x * 2

# Función normal: para lógica compleja
def procesar_datos(datos):
    """Procesa y valida datos."""
    # Múltiples líneas
    # Validaciones
    # Lógica compleja
    return resultado
```

**Regla:** Si necesitás más de una línea, usá función normal

<!--
Eviten los efectos secundarios. Una función idealmente debería recibir datos y devolver nuevos datos, SIN modificar los originales ni el estado global. Eso las hace predecibles y seguras (Funciones puras).
-->
---

<!-- _class: lead -->

# Documentación de Funciones

<!--
Separación de intereses. La lógica de negocio (calcular total) no debería mezclarse con la interfaz de usuario (print). Retornen el valor y dejen que quien llamó a la función decida si imprimirlo, guardarlo o mandarlo por mail.
-->
---

## Docstrings

Los **docstrings** documentan qué hace la función:

```python
def calcular_area(base, altura):
    """Calcula el área de un rectángulo.
    
    Args:
        base: Base del rectángulo en metros.
        altura: Altura del rectángulo en metros.
    
    Returns:
        El área del rectángulo en metros cuadrados.
    
    Example:
        >>> calcular_area(5, 10)
        50
    """
    return base * altura
```

**Acceder con `help()`:**
```python
help(calcular_area)
```

<!--
No confíen ciegamente en los datos que entran. Validen. Si la altura no puede ser negativa, chequéenlo al principio y levanten un error o retornen algo indicativo. Hace al código robusto.
-->
---

## Formato de Docstrings

**Estructura recomendada:**
1. **Línea resumen:** Qué hace (imperativo)
2. **Línea en blanco**
3. **Descripción detallada** (opcional)
4. **Args:** Parámetros y tipos
5. **Returns:** Qué retorna
6. **Raises:** Excepciones (opcional)
7. **Example:** Ejemplos de uso

<!--
Repasemos errores. Olvidar el `return` es el clásico número 1. Hacés todo el cálculo perfecto pero la función devuelve `None`. Siempre verifiquen qué sale de la función.
-->
---

## Ejemplo Completo

```python
def dividir(dividendo, divisor):
    """Divide dos números de forma segura.
    
    Realiza la división verificando que el divisor
    no sea cero para evitar errores.
    
    Args:
        dividendo: Número a dividir (int o float).
        divisor: Número divisor (int o float).
    
    Returns:
        El resultado de la división (float).
        None si el divisor es cero.
    
    Example:
        >>> dividir(10, 2)
        5.0
        >>> dividir(10, 0)
        None
    """
    if divisor == 0:
        return None
    return dividendo / divisor
```

<!--
Si definís 3 parámetros, tenés que pasar 3 argumentos (a menos que tengan defaults). Python cuenta y te va a retar si no coinciden.
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
El tema de modificar listas que pasás como argumento. A veces es lo que querés, pero muchas veces es un error accidental. Si no querés tocar el original, trabajá sobre una copia o creá una lista nueva.
-->
---

## 1. Nombres Descriptivos

```python
# ❌ Mal: nombres crípticos
def calc(x, y):
    return x * y

# ✓ Bien: nombres claros
def calcular_area_rectangulo(base, altura):
    return base * altura
```

**Regla:** El nombre debe indicar qué hace la función

<!--
Documenten. En serio. Una función sin docstring es una caja negra. Abran la caja y pongan la etiqueta.
-->
---

## 2. Hacer Una Sola Cosa (SRP)

```python
# ❌ Hace demasiado
def procesar_usuario(nombre, edad):
    print(f"Procesando {nombre}")
    validar_edad(edad)
    guardar_bd(nombre, edad)
    enviar_email(nombre)
    generar_reporte()

# ✓ Funciones específicas
def validar_usuario(nombre, edad):
    return edad >= 18

def registrar_usuario(nombre, edad):
    guardar_bd(nombre, edad)

def notificar_registro(nombre):
    enviar_email(nombre)
```

<!--
Descomponer es clave. Enfrentar un problema gigante asusta. Dividirlo en problemitas chiquitos y manejables es la estrategia ganadora. 'Divide y vencerás'.
-->
---

## 3. Funciones Cortas

```python
# ✓ Bien: función corta y clara
def es_par(numero):
    """Verifica si un número es par."""
    return numero % 2 == 0

# ✓ Bien: < 20 líneas idealmente
def calcular_promedio(notas):
    """Calcula el promedio de notas."""
    if not notas:
        return 0
    return sum(notas) / len(notas)
```

**Regla:** Si no cabe en una pantalla, es demasiado larga

<!--
Empiecen por el 'qué' (la función principal de alto nivel) y después vayan al 'cómo' (los detalles en sub-funciones). Es como hacer un boceto y después pintar los detalles.
-->
---

## 4. Evitar Efectos Secundarios

```python
# ❌ Modifica argumentos (efecto secundario)
def duplicar_valores(lista):
    for i in range(len(lista)):
        lista[i] *= 2
    return lista

original = [1, 2, 3]
duplicada = duplicar_valores(original)
print(original)  # [2, 4, 6] ¡Modificó!

# ✓ Sin efectos secundarios
def duplicar_valores(lista):
    return [x * 2 for x in lista]

original = [1, 2, 3]
duplicada = duplicar_valores(original)
print(original)  # [1, 2, 3] ✓
```

<!--
Cada pieza del rompecabezas tiene que encajar y hacer su trabajo. Si `validar_pedido` también calcula el total, está mal diseñada. Separen las tareas.
-->
---

## 5. Retornar, No Imprimir

```python
# ❌ Mezcla lógica con presentación
def calcular_total(items):
    total = sum(item['precio'] for item in items)
    print(f"Total: ${total}")  # No retorna

# ✓ Retorna el valor
def calcular_total(items):
    """Calcula el total de items."""
    return sum(item['precio'] for item in items)

# Quien llama decide qué hacer
total = calcular_total(items)
print(f"Total: ${total}")
```

<!--
Miren este validador. En vez de un choclo de `if` complejos, tenemos tres funciones chiquitas con nombres claros. `es_password_valido` se lee casi como lenguaje natural. Eso es calidad de código.
-->
---

## 6. Validar Entradas

```python
def calcular_area(base, altura):
    """Calcula área con validación."""
    if base <= 0 or altura <= 0:
        raise ValueError("Base y altura deben ser positivos")
    
    return base * altura

# Uso seguro
try:
    area = calcular_area(-5, 10)
except ValueError as e:
    print(f"Error: {e}")
```

<!--
Resumiendo: `def` para definir, indentación para el cuerpo, parámetros para entrada, `return` para salida. Scope local vs global. Y herramientas poderosas como lambda y argumentos variables.
-->
---

<!-- _class: lead -->

# Errores Comunes

<!--
Recuerden: Return devuelve, Print muestra. Scope local protege variables. Eviten `global`.
-->
---

## Error #1: Olvidar el Return

```python
# ❌ Olvidó return
def sumar(a, b):
    resultado = a + b  # No retorna

total = sumar(5, 3)
print(total)  # None

# ✓ Con return
def sumar(a, b):
    return a + b

total = sumar(5, 3)
print(total)  # 8
```

<!--
Las buenas prácticas no son capricho. Nombres claros, funciones cortas, responsabilidad única. Son las reglas que nos permiten trabajar en equipos y mantener proyectos grandes.
-->
---

## Error #2: Cantidad Incorrecta de Argumentos

```python
# ❌ Faltan argumentos
def saludar(nombre, edad):
    print(f"Hola {nombre}, tienes {edad} años")

saludar("Ana")  # TypeError: missing 1 required argument

# ✓ Todos los argumentos
saludar("Ana", 20)
```

<!--
El flujo de trabajo profesional: Entender el problema -> Diseñar la firma de la función (nombre y parámetros) -> Escribir el docstring -> Implementar -> Probar. Y repetir.
-->
---

## Error #3: Modificar Argumentos Mutables

```python
# ❌ Efecto secundario
def duplicar(lista):
    for i in range(len(lista)):
        lista[i] *= 2
    return lista

nums = [1, 2, 3]
nuevos = duplicar(nums)
print(nums)  # [2, 4, 6] ¡Modificó el original!

# ✓ Sin modificar original
def duplicar(lista):
    return [x * 2 for x in lista]
```

<!--
Cuidado con los sospechosos de siempre: `return` faltante, argumentos incorrectos, mutabilidad inesperada. Estén atentos.
-->
---

## Error #4: No Documentar

```python
# ❌ Sin documentación
def calc(x, y, z):
    return x * y + z

# ✓ Con documentación
def calcular_costo_total(precio, cantidad, envio):
    """Calcula el costo total de una compra.
    
    Args:
        precio: Precio unitario.
        cantidad: Cantidad de items.
        envio: Costo de envío.
    
    Returns:
        El costo total.
    """
    return precio * cantidad + envio
```

<!--
¡Eso es todo por hoy! Las funciones son los ladrillos con los que construimos software. Practiquen crear sus propias funciones, jueguen con los parámetros y traten de escribir código limpio. ¡A programar!
-->
---

<!-- _class: lead -->

# Descomposición Funcional

<!--
NO MORE NOTES
-->
---

## ¿Qué es la Descomposición?

**Dividir un problema grande en funciones más pequeñas**

**Problema grande:**
```python
# 100 líneas de código en una función
def procesar_todo():
    # ... validar
    # ... calcular
    # ... formatear
    # ... guardar
    # ... enviar email
```

**Problema descompuesto:**
```python
validar_datos()
calcular_resultados()
formatear_salida()
guardar_en_bd()
enviar_notificacion()
```

<!--
NO MORE NOTES
-->
---

## Estrategia: Top-Down

**Empezá por el nivel más alto:**

```python
def main():
    """Función principal."""
    datos = obtener_datos()
    resultados = procesar_datos(datos)
    mostrar_resultados(resultados)

# Luego implementá cada parte
def obtener_datos():
    # ...

def procesar_datos(datos):
    # ...

def mostrar_resultados(resultados):
    # ...
```

<!--
NO MORE NOTES
-->
---

## Principio de Responsabilidad Única

**Cada función debe hacer UNA cosa:**

```python
# ❌ Hace demasiado
def procesar_pedido(pedido):
    validar(pedido)
    calcular_total(pedido)
    aplicar_descuento(pedido)
    procesar_pago(pedido)
    enviar_confirmacion(pedido)

# ✓ Responsabilidad única
def validar_pedido(pedido):
    return pedido['items'] and pedido['total'] > 0

def calcular_total(pedido):
    return sum(item['precio'] for item in pedido['items'])
```

<!--
NO MORE NOTES
-->
---

## Ejemplo: Validador de Contraseña

**Problema:** Validar que una contraseña cumpla requisitos

**Descomposición:**
```python
def tiene_longitud_minima(password):
    return len(password) >= 8

def tiene_mayuscula(password):
    return any(c.isupper() for c in password)

def tiene_numero(password):
    return any(c.isdigit() for c in password)

def es_password_valido(password):
    return (tiene_longitud_minima(password) and
            tiene_mayuscula(password) and
            tiene_numero(password))
```

**Ventaja:** Cada función es simple, testeable, reutilizable

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Resumen

<!--
NO MORE NOTES
-->
---

## Conceptos Clave

**Definición:**
- `def nombre(parametros):`
- Documentación con docstrings
- Indentación del cuerpo

**Parámetros:**
- Posicionales: orden importa
- Keyword: nombre explícito
- Por defecto: valores opcionales
- `*args`, `**kwargs`: variables

<!--
NO MORE NOTES
-->
---

## Conceptos Clave (cont.)

**Return:**
- Devuelve valores
- Múltiples valores con tuplas
- `None` si no hay `return`

**Scope:**
- Locales: dentro de función
- Globales: fuera de funciones
- Evitar `global`

**Avanzado:**
- Lambda: funciones anónimas
- Recursión: función que se llama a sí misma

<!--
NO MORE NOTES
-->
---

## Buenas Prácticas Fundamentales

1. **Nombres descriptivos** que indiquen qué hace
2. **Una responsabilidad** por función (SRP)
3. **Funciones cortas** (< 20 líneas idealmente)
4. **Documentar** con docstrings
5. **Retornar, no imprimir**
6. **Evitar efectos secundarios**
7. **Validar entradas**
8. **Descomponer problemas** complejos

<!--
NO MORE NOTES
-->
---

## Flujo de Desarrollo

```python
# 1. Definir el problema
# ¿Qué necesito hacer?

# 2. Diseñar la función
def nombre_descriptivo(parametros):
    """Documentar qué hace."""
    pass

# 3. Implementar
def calcular_promedio(notas):
    """Calcula el promedio de notas."""
    if not notas:
        return 0
    return sum(notas) / len(notas)

# 4. Probar
assert calcular_promedio([8, 9, 7]) == 8.0
assert calcular_promedio([]) == 0

# 5. Refactorizar si es necesario
```

<!--
NO MORE NOTES
-->
---

## Errores Más Comunes

❌ Olvidar `return`
❌ Cantidad incorrecta de argumentos
❌ Modificar argumentos mutables
❌ No documentar funciones
❌ Funciones que hacen demasiado
❌ Usar `global` innecesariamente
❌ Valores mutables por defecto
❌ Nombres poco descriptivos

<!--
NO MORE NOTES
-->
---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Las funciones son la base de la programación modular y reutilizable.

Dominá estos conceptos y podrás escribir código profesional, limpio y mantenible.

**Recordá:** Una función bien escrita es una función que otro programador (o vos en 6 meses) puede entender fácilmente.
