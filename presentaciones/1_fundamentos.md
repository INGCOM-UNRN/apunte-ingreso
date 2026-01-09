---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Fundamentos de Programación en Python - Introducción a la programación'
---
<!-- _header: '' -->

# <!-- fit --> Hola Python 🐍

**Introducción a la programación, variables, tipos de datos y operadores**

Martín René Vilugrón - Ingeniería en Computación

<!--
¡Bienvenidos a todos! Hoy arrancamos con los fundamentos de programación en Python. Esta es la base de todo lo que vamos a construir. No se preocupen si nunca escribieron una línea de código, vamos a ir paso a paso. La idea es entender cómo piensa la máquina y cómo hablar su idioma.
-->
---
## ¿Qué vas a aprender?

* Cómo crear y usar **variables** para guardar información
* Los **4 tipos de datos básicos**: números, texto y booleanos
* **Operadores** para hacer cálculos y comparaciones
* Cómo **interactuar con el usuario**
* **Errores comunes** y cómo evitarlos

<!--
¿Qué vamos a ver hoy? Primero, cómo guardar información en 'cajitas' llamadas variables. Después, los tipos de datos: números, texto, y lógica de verdadero/falso. También vamos a ver cómo hacer cuentas (matemática básica) y cómo charlar con el usuario (preguntarle cosas y mostrarle respuestas). Y muy importante: cómo no entrar en pánico cuando aparezcan errores.
-->
---
## ¿Qué es programar?

Programar es dar **instrucciones muy detalladas y precisas** a una computadora para que resuelva problemas.

**La computadora es:**
- Increíblemente rápida y precisa
- Pero necesita que le expliques **exactamente** qué hacer

<!--
A ver, ¿qué es programar? Básicamente, es darle órdenes a la computadora. Pero ojo, la computadora es un bicho muy rápido pero muy literal. No entiende indirectas. Si le decís 'hacé eso', te va a preguntar '¿qué es eso?'. Tenés que ser específico: 'agarrá el archivo A, movelo a la carpeta B'. Si no sos preciso, la máquina no arranca.
-->
---
## ¿Por qué Python? 🐍

Python es claro, fácil de leer y lo entiende mucha gente

**Otros lenguajes (más complicados):**
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("¡Hola Mundo!");
    }
}
```

**Python (¡simple!):**
```python
print("¡Hola Mundo!")
```

<!--
¿Por qué elegimos Python? Miren este ejemplo. A la izquierda tienen Java... mucho código solo para decir 'Hola'. A la derecha, Python: directo al grano. `print('Hola Mundo')` y listo. Es un lenguaje que se lee casi como inglés. Te permite concentrarte en *resolver el problema* y no en pelearte con la sintaxis.
-->
---
## Variables

### ¿Qué es una variable?

Una **variable** es como una caja con una etiqueta donde guardás información.

```python
edad = 18
nombre = "Carlos"
altura = 1.75
```

- `edad`, `nombre`, `altura` → nombres de las variables (etiquetas)
- `=` → operador de asignación
- `18`, `"Carlos"`, `1.75` → valores guardados

<!--
Entremos en tema: Variables. Imaginate una caja de mudanza. Le ponés una etiqueta con fibrón que dice 'Juguetes'. Adentro metés los juguetes. En Python es igual: `edad = 18`. La etiqueta es `edad`, el operador `=` es la acción de meter algo en la caja, y `18` es lo que guardás. Ojo: el `=` NO es 'igual matemático', es ASIGNACIÓN. Significa 'guardar esto acá'.
-->
---
## Reglas para Nombres de Variables

**Pueden contener:**
- Letras (a-z, A-Z)
- Números (0-9, pero **no al inicio**)
- Guiones bajos (_)

**No pueden:**
- Empezar con números
- Tener espacios
- Usar palabras reservadas de Python

<!--
Para ponerle nombre a las variables hay reglas. Podés usar letras, números y guiones bajos. Pero NUNCA arranques con un número. La máquina se confunde. Y nada de espacios, porque el espacio separa cosas. Si querés separar palabras, usá el guion bajo `_`.
-->
---
## Ejemplos de Nombres Válidos e Inválidos

**✓ Válidos:**
```python
nombre = "Ana"
edad_usuario = 25
precio1 = 100
total_ventas = 5000
_valor_interno = 42
```

**✗ Inválidos:**
```python
2nombre = "Error"      # Empieza con número
mi nombre = "Error"    # Tiene espacio
class = "Error"        # Palabra reservada
precio-final = 100     # Usa guion
```

<!--
Miren los ejemplos. `precio_final` con guion bajo está perfecto. Pero `precio-final` con guion medio parece una resta (precio MENOS final). `2nombre` falla porque empieza con número. Y `class` no se puede usar porque es una palabra reservada del lenguaje (como decir 'verbo' en una clase de lengua).
-->
---
## Convenciones de Nomenclatura

**Snake case (Python):**
```python
nombre_completo = "María García"
precio_total = 199.99
cantidad_en_stock = 50
```

**Las variables deben ser:**
- **Descriptivas**: `edad` mejor que `e`
- **En minúsculas**: `nombre_usuario` no `NombreUsuario`
- **Con guiones bajos**: `precio_final` no `precioFinal`

<!--
Más allá de lo que *se puede*, está lo que *se debe*. En Python usamos `snake_case`: todo minúscula y palabras separadas por guiones bajos. Es como una víbora que repta. Sean claros: `x` no me dice nada, `edad_usuario` me dice todo. Escribimos código para que lo lean humanos, no solo máquinas.
-->
---
<!-- _class: lead -->

# Tipos de Datos Básicos

<!--
Bien, ya tenemos las cajas (variables). Ahora veamos qué podemos meter adentro. Los tipos de datos.
-->
---
## Los 4 Tipos Básicos

Python tiene cuatro tipos básicos que son como los "bloques de construcción" de cualquier programa:

1. **`int`** → Números enteros
2. **`float`** → Números con decimales
3. **`str`** → Texto (cadenas)
4. **`bool`** → Verdadero/Falso

<!--
Hay 4 fantásticos: Enteros (números sin coma), Flotantes (con coma), Strings (texto) y Booleanos (lógica). Con estos cuatro ladrillos se construyen imperios de software.
-->
---
## Números Enteros (`int`)

Los **enteros** son números sin decimales

```python
edad = 18
temperatura = -5
año = 2023
poblacion = 1000000
```

**¿Cuándo usar `int`?**
- Contás cosas que no se pueden dividir
- Trabajás con años, días, edades
- No necesitás precisión decimal

<!--
Enteros o `int`. Son para contar cosas enteras. Personas, años, días. No podés tener 1.5 personas (esperemos). Si no tiene decimal, es un `int`.
-->
---
## Números de Punto Flotante (`float`)

Los **flotantes** son números con decimales

```python
altura = 1.75
pi = 3.14159
temperatura = 36.5
precio = 99.99
```

**⚠️ Importante:** Los decimales se escriben con **punto** (`.`), no con coma (`,`)

```python
# ✓ Correcto
precio = 99.99

# ✗ Incorrecto
precio = 99,99
```

<!--
Flotantes o `float`. Acá entran los decimales. Altura, precio, temperatura. ¡Cuidado! En programación usamos PUNTO, no coma. Si ponés `99,99`, Python va a pensar que son dos números distintos. Acordate: `99.99`.
-->
---
## Cadenas de Texto (`str`)

Las **cadenas** son simplemente **texto**: palabras, frases, letras

```python
nombre = "María"
apellido = 'González'
mensaje = "¡Hola! ¿Cómo estás?"
direccion = 'Calle 123, Ciudad'
```

**Podés usar comillas simples (`'`) o dobles (`"`)**
- Elegí una y sé consistente
- Usá la otra cuando necesitás incluir comillas en el texto

<!--
Strings o `str`. Es texto. Cadenas de caracteres. Todo lo que esté entre comillas es texto. Puede ser una palabra, una frase o incluso un número entre comillas (`'123'`). Si tiene comillas, para Python es letra, no número.
-->
---
## Comillas en Cadenas

```python
# Comillas dobles para incluir simples
frase = "Estoy leyendo 'El Quijote'"

# Comillas simples para incluir dobles
dialogo = 'Ella dijo: "Hola"'

# Comillas triples para múltiples líneas
texto_largo = """
Este es un texto
que ocupa varias
líneas.
"""
```

<!--
El tema de las comillas. Podés usar simples ' ' o dobles " ". Da igual, pero sé consistente. El truco es: si tu texto tiene comillas dobles adentro (como una cita), encerralo con simples. Y si tenés un choclo de texto de varios renglones, usá las triples comillas.
-->
---
## Booleanos (`bool`)

Los **booleanos** son valores de verdad: solo pueden ser `True` o `False`

```python
mayor_de_edad = True
llueve = False
tiene_descuento = True
```

**Se usan para:**
- Tomar decisiones en el programa
- Guardar el resultado de comparaciones
- Controlar el flujo del programa

<!--
Booleanos o `bool`. Solo hay dos opciones: `True` (Verdadero) o `False` (Falso). Ojo que van con mayúscula inicial. Son fundamentales para tomar decisiones: ¿Es mayor de edad? Sí/No. ¿Tiene saldo? Sí/No.
-->
---
## Operador de Asignación (`=`)

El símbolo `=` **asigna** un valor a una variable

```python
edad = 25           # Asigna 25 a edad
nombre = "Ana"      # Asigna "Ana" a nombre
altura = 1.75       # Asigna 1.75 a altura
```

**⚠️ No es "igual a"** (eso es `==`)

```python
x = 5    # Asignación: x ahora vale 5
x == 5   # Comparación: ¿x es igual a 5?
```

<!--
Volvemos al `=` vs `==`. Esto tatúenselo. Un solo igual `=` es ASIGNAR (guardar). Dos iguales `==` es COMPARAR (preguntar). Si ponés `x = 5`, x pasa a valer 5. Si ponés `x == 5`, estás preguntando '¿x vale 5?'.
-->
---
## Variables Múltiples

```python
# Asignación múltiple
x, y, z = 1, 2, 3

# Mismo valor a múltiples variables
a = b = c = 100

# Intercambiar valores
x, y = 10, 20
x, y = y, x  # Ahora x=20, y=10
```

<!--
Python tiene magia. Podés asignar varias variables de un saque: `x, y = 1, 2`. Y lo mejor: intercambiar valores sin una variable temporal. `x, y = y, x`. En otros lenguajes esto es un lío, acá es una línea.
-->
---
<!-- _class: lead -->

# Operadores Aritméticos

<!--
Ahora que tenemos datos, ¡hagamos cuentas! Operadores aritméticos.
-->
---
## Operadores Básicos

| Operador | Operación | Ejemplo | Resultado |
|----------|-----------|---------|-----------|
| `+` | Suma | `5 + 3` | `8` |
| `-` | Resta | `10 - 4` | `6` |
| `*` | Multiplicación | `7 * 6` | `42` |
| `/` | División | `15 / 3` | `5.0` |

**Nota:** La división `/` **siempre** retorna un `float`

<!--
Suma, resta y multiplicación son lo de siempre. La división `/` tiene un detalle: SIEMPRE devuelve un flotante (con decimales), aunque el resultado sea redondo. `4 / 2` te da `2.0`.
-->
---
## Operadores Avanzados

| Operador | Operación | Ejemplo | Resultado |
|----------|-----------|---------|-----------|
| `//` | División entera | `17 // 5` | `3` |
| `%` | Módulo (resto) | `17 % 5` | `2` |
| `**` | Potenciación | `2 ** 3` | `8` |

<!--
Acá se pone interesante. La división entera `//` corta los decimales. El módulo `%` te da el RESTO de la división (clave para saber si un número es par o impar). Y la potencia es `**`, no `^`.
-->
---
## Ejemplos Prácticos

```python
# División normal vs. entera
print(17 / 5)   # 3.4 (resultado con decimales)
print(17 // 5)  # 3 (solo la parte entera)

# Módulo: útil para saber si un número es par
print(10 % 2)   # 0 (es par, resto 0)
print(11 % 2)   # 1 (es impar, resto 1)

# Potenciación
radio = 5
area = 3.14159 * radio ** 2  # π × r²
print(f"Área del círculo: {area}")
```

<!--
Miren la diferencia entre `/` y `//`. Y el módulo: `10 % 2` es 0 porque es par. `11 % 2` sobra 1. Esto se usa muchísimo en lógica de programación.
-->
---
## Orden de Precedencia (PEMDAS)

Python sigue el orden matemático estándar:

1. **P**aréntesis → `( )`
2. **E**xponenciación → `**`
3. **M**ultiplicación / **D**ivisión → `*`, `/`, `//`, `%`
4. **S**uma / Resta → `+`, `-`

```python
resultado = 2 + 3 * 4
print(resultado)  # 14 (primero 3*4, luego +2)

resultado = (2 + 3) * 4
print(resultado)  # 20 (primero 2+3, luego *4)
```

<!--
El orden importa. Python respeta las reglas de matemática. Primero paréntesis, después potencias, después multiplicación/división, y al final suma/resta. 'Papomudas' le dicen algunos. No confíen en su memoria, ante la duda...
-->
---
## Uso de Paréntesis

**Usar paréntesis hace el código más claro:**

```python
# Menos claro
total = precio * cantidad + descuento * 0.1

# Más claro
total = (precio * cantidad) + (descuento * 0.1)
```

**💡 Consejo:** Cuando hay dudas, ¡usá paréntesis!

<!--
...¡Usen paréntesis! Aunque no sean obligatorios, ayudan a leer. `(a * b) + c` es mucho más claro que `a * b + c`. Ayuden al que lee su código (que seguro van a ser ustedes mismos en un mes).
-->
---
<!-- _class: lead -->

# Operadores de Comparación

<!--
Bien, ya sabemos calcular. Ahora aprendamos a comparar cosas.
-->
---
## Comparando Valores

Los **operadores de comparación** comparan dos valores y devuelven `True` o `False`

```python
# Igualdad
print(5 == 5)   # True
print(5 == 3)   # False

# Desigualdad
print(5 != 3)   # True
print(5 != 5)   # False
```

<!--
Comparar siempre nos devuelve un Booleano: Sí o No (`True` o `False`). ¿5 es igual a 5? `True`. ¿5 es igual a 3? `False`.
-->
---
## Tabla de Operadores de Comparación

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `==` | Igual a | `5 == 5` | `True` |
| `!=` | Diferente de | `5 != 3` | `True` |
| `>` | Mayor que | `10 > 5` | `True` |
| `<` | Menor que | `3 < 8` | `True` |
| `>=` | Mayor o igual | `5 >= 5` | `True` |
| `<=` | Menor o igual | `4 <= 9` | `True` |

<!--
Acá tienen la lista. El doble igual `==` es el rey de las comparaciones. El `!=` es 'distinto de'. Y los clásicos mayor, menor, mayor o igual...
-->
---
## Ejemplos de Comparación

```python
edad = 18
precio = 99.99
nombre = "Ana"

# Comparaciones numéricas
print(edad >= 18)           # True
print(precio < 100)         # True

# Comparación de strings
print(nombre == "Ana")      # True
print(nombre == "Juan")     # False
```

<!--
Fíjense que podemos comparar números y también texto. `'Ana' == 'Ana'` es `True`. Pero ojo que Python distingue mayúsculas de minúsculas. `'ana' == 'Ana'` daría `False`.
-->
---
## ⚠️ Diferencia entre `=` y `==`

```python
# = es ASIGNACIÓN
edad = 25  # Guarda 25 en la variable edad

# == es COMPARACIÓN
edad == 25  # Pregunta: ¿edad es igual a 25?
```

**Error común:**
```python
if edad = 25:  # ✗ ERROR: no se puede asignar en condición
    print("Mayor de edad")

if edad == 25:  # ✓ CORRECTO: comparación
    print("Mayor de edad")
```

<!--
Insisto con esto porque es el error número 1. Si quieren preguntar en un `if`, usen `==`. Si usan `=` les va a tirar error de sintaxis o, peor, van a romper la lógica del programa.
-->
---
<!-- _class: lead -->

# Operadores Lógicos

<!--
Ahora vamos a combinar preguntas. Operadores Lógicos.
-->
---
## Operadores Lógicos

Permiten combinar condiciones:

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `and` | Y lógico | `True and False` | `False` |
| `or` | O lógico | `True or False` | `True` |
| `not` | Negación | `not True` | `False` |

<!--
Son tres: `and` (y), `or` (o), `not` (no). Se escriben en inglés y minúscula.
-->
---
## `and`: Ambas condiciones deben ser verdaderas

```python
edad = 20
tiene_licencia = True

# AND: ambas deben ser True
puede_conducir = edad >= 18 and tiene_licencia
print(puede_conducir)  # True

# Si falta una condición
edad = 16
puede_conducir = edad >= 18 and tiene_licencia
print(puede_conducir)  # False
```

<!--
El `and` es exigente. Para que te dé `True`, TODAS las condiciones tienen que ser verdaderas. Si tenés entrada Y tenés DNI, pasás. Si te falta una, afuera.
-->
---
## `or`: Al menos una condición debe ser verdadera

```python
es_fin_de_semana = True
es_feriado = False

# OR: al menos una debe ser True
puede_descansar = es_fin_de_semana or es_feriado
print(puede_descansar)  # True

# Si ambas son False
es_fin_de_semana = False
es_feriado = False
puede_descansar = es_fin_de_semana or es_feriado
print(puede_descansar)  # False
```

<!--
El `or` es más relajado. Con que UNA sea verdadera, ya está. ¿Es sábado O es domingo? Si cualquiera es sí, no trabajo.
-->
---
## `not`: Invierte el valor booleano

```python
esta_lloviendo = False
buen_tiempo = not esta_lloviendo
print(buen_tiempo)  # True

tiene_cuenta = True
debe_registrarse = not tiene_cuenta
print(debe_registrarse)  # False
```

<!--
El `not` te lleva la contra. Invierte el valor. Si es `True`, lo hace `False`. Si llueve es `True`, `not llueve` es `False`. Útil para decir 'si NO está vacío' o 'si NO es válido'.
-->
---
## Combinando Operadores Lógicos

```python
edad = 25
tiene_experiencia = True
tiene_titulo = False

# Múltiples condiciones
puede_aplicar = edad >= 21 and (tiene_experiencia or tiene_titulo)
print(puede_aplicar)  # True
```

**💡 Consejo:** Usar paréntesis para claridad

<!--
Podés armar condiciones complejas. 'Si es mayor de 21 Y (tiene experiencia O tiene título)'. Los paréntesis acá son vitales para agrupar la lógica correctamente.
-->
---
<!-- _class: lead -->

# Entrada y Salida

<!--
Hasta ahora la compu hablaba sola. Vamos a hacerla interactuar. Entrada y Salida.
-->
---
## Interactuando con el Usuario

Los programas útiles necesitan **interactuar**:
- **Entrada:** Pedir información al usuario (`input()`)
- **Salida:** Mostrar resultados (`print()`)

<!--
Entrada es lo que el usuario tipea (`input`). Salida es lo que la máquina muestra (`print`). Es el diálogo básico.
-->
---
## Salida: `print()`

La función `print()` muestra información en la pantalla

```python
# Imprimir texto
print("Hola Mundo")

# Imprimir variables
nombre = "Ana"
print(nombre)

# Imprimir múltiples valores
edad = 20
print("Nombre:", nombre, "Edad:", edad)
```

<!--
`print()` es nuestro grito al mundo. Podés imprimir texto fijo, variables, o mezclar todo con comas.
-->
---
## F-strings (Formateo Moderno)

```python
nombre = "Carlos"
edad = 25

# F-string: coloca f antes de las comillas
print(f"Mi nombre es {nombre} y tengo {edad} años")
# Salida: Mi nombre es Carlos y tengo 25 años

# Formateo de números
precio = 19.99
print(f"El precio es ${precio:.2f}")
# Salida: El precio es $19.99
```

**Los f-strings son la forma más legible de formatear texto**

<!--
Esta es la joyita de Python moderno: las f-strings. Ponés una `f` antes de las comillas y podés meter variables directamente entre llaves `{}`. Es mucho más limpio que andar concatenando con `+` o `,`.
-->
---
## Entrada: `input()`

La función `input()` lee texto desde el teclado

```python
# Pedir el nombre
nombre = input("¿Cuál es tu nombre? ")
print(f"¡Hola {nombre}!")

# Pedir edad (retorna string)
edad_str = input("¿Cuántos años tenés? ")
```

**⚠️ Importante:** `input()` **siempre retorna un string**

<!--
`input()` frena el programa y espera que el usuario escriba y de Enter. IMPORTANTE: Todo lo que entra por `input` es TEXTO (`str`). Aunque escribas un número '50', entra como el texto '50'.
-->
---
## Conversión de Tipos

Para usar números, debés convertir el string:

```python
# Leer edad y convertir a int
edad_str = input("¿Cuántos años tenés? ")
edad = int(edad_str)

# Ahora podés hacer operaciones
print(f"El próximo año tendrás {edad + 1} años")

# Lo mismo para float
altura_str = input("¿Cuánto medís (en metros)? ")
altura = float(altura_str)
print(f"Tu altura es {altura}m")
```

<!--
Si `input` nos da texto y queremos sumar, tenemos un problema. '50' + 1 da error. Tenemos que CONVERTIR ese texto a número. Eso es el 'casting'.
-->
---
## Programa Completo de Ejemplo

```python
# Solicitar datos
nombre = input("¿Cómo te llamás? ")
edad_str = input("¿Cuántos años tenés? ")
edad = int(edad_str)

# Procesar
año_nacimiento = 2024 - edad

# Mostrar resultados
print(f"\n¡Hola {nombre}!")
print(f"Tenés {edad} años")
print(f"Naciste aproximadamente en {año_nacimiento}")
```

<!--
Miren este flujo. 1: Pido datos (y convierto la edad a int ahí mismo). 2: Calculo. 3: Muestro con f-string. Es el ciclo de vida de cualquier script básico.
-->
---
<!-- _class: lead -->

# Conversión de Tipos

<!--
Profundicemos un poco en esto de convertir tipos.
-->
---
## ¿Por qué convertir tipos?

No podés sumar directamente un número con un string:

```python
edad = "25"
print(edad + 1)  # ✗ ERROR: no se puede sumar str + int
```

Necesitás convertir:

```python
edad = "25"
edad_numero = int(edad)
print(edad_numero + 1)  # ✓ Salida: 26
```

<!--
Intentar sumar peras con manzanas (texto con números) explota. Python no adivina. Tenés que ser explícito: 'Tratame esto como un número'.
-->
---
## Funciones de Conversión

| Función | Conversión | Ejemplo |
|---------|------------|---------|
| `int()` | A entero | `int("25")` → `25` |
| `float()` | A flotante | `float("3.14")` → `3.14` |
| `str()` | A string | `str(25)` → `"25"` |
| `bool()` | A booleano | `bool(1)` → `True` |

<!--
Las funciones se llaman igual que los tipos: `int()`, `float()`, `str()`. Son como máquinas transformadoras. Metés texto, sale número.
-->
---
## Ejemplos de Conversión

```python
# String a int
texto = "100"
numero = int(texto)
print(numero + 50)  # 150

# String a float
texto = "3.14"
pi = float(texto)
print(pi * 2)  # 6.28

# Int a string
edad = 25
mensaje = "Tengo " + str(edad) + " años"
print(mensaje)  # "Tengo 25 años"
```

<!--
Ojo que la conversión tiene que tener sentido. `int('hola')` va a fallar. Pero `int('100')` funciona joya. También sirve al revés: `str(25)` para concatenar texto.
-->
---
## Conversiones Automáticas (Coerción)

Python convierte automáticamente en algunas operaciones:

```python
# int a float en divisiones
resultado = 5 / 2
print(resultado)  # 2.5 (float)

# int + float → float
resultado = 5 + 2.5
print(resultado)  # 7.5 (float)
```

<!--
A veces Python es buena onda y convierte solo. Si sumás un entero y un flotante (`5 + 2.5`), el resultado es flotante (`7.5`). No pierde información.
-->
---
<!-- _class: lead -->

# Errores Comunes

<!--
Para ir cerrando: Errores. No se frustren, son parte del día a día. Vamos a ver los clásicos.
-->
---
## Error #1: Usar variable antes de definirla

```python
# ✗ Incorrecto
print(resultado)  # NameError: name 'resultado' is not defined

# ✓ Correcto
resultado = 0
print(resultado)  # Salida: 0
```

**Siempre definí las variables antes de usarlas**

<!--
`NameError`. Usaste una variable que no creaste. Ojo con los typos: si definís `edad` y usás `Edad`, fuiste.
-->
---
## Error #2: Confundir `=` con `==`

```python
# ✗ Incorrecto - Asignación en lugar de comparación
edad = 18
if edad = 18:  # SyntaxError
    print("Mayor de edad")

# ✓ Correcto - Comparación
edad = 18
if edad == 18:
    print("Mayor de edad")
```

<!--
El del `=` en el `if`. `SyntaxError`. Python te está diciendo 'No entiendo la gramática de esto'.
-->
---
## Error #3: Olvidar convertir `input()`

```python
# ✗ Incorrecto
edad = input("¿Cuántos años tenés? ")
print(edad + 1)  # TypeError: no se puede sumar str + int

# ✓ Correcto
edad = int(input("¿Cuántos años tenés? "))
print(edad + 1)  # Funciona correctamente
```

<!--
`TypeError`. Operación prohibida. Sumar texto y número. Acuérdense de convertir el input.
-->
---
## Error #4: División por cero

```python
# ✗ Cuidado
resultado = 10 / 0  # ZeroDivisionError

# ✓ Verificar antes
divisor = 0
if divisor != 0:
    resultado = 10 / divisor
else:
    print("No se puede dividir por cero")
```

<!--
`ZeroDivisionError`. No podés dividir por cero. Matemática básica, pero la compu explota. Siempre validen que el divisor no sea 0.
-->
---
## Error #5: Comillas mal cerradas

```python
# ✗ Incorrecto
mensaje = "Hola Mundo'  # SyntaxError
nombre = 'Ana          # SyntaxError

# ✓ Correcto
mensaje = "Hola Mundo"
nombre = 'Ana'
```

<!--
Comillas desparejas. Abrís dobles, cerrás simples. O te olvidás de cerrar. El editor de código suele avisar con colores raros.
-->
---
<!-- _class: lead -->

# Resumen

<!--
¡Uff,ímos un montón! Repasemos.
-->
---
## Conceptos Clave

1) **Variables:** Cajas con nombre para guardar valores
2) **Tipos de datos:** `int`, `float`, `str`, `bool`
3) **Operadores aritméticos:** `+`, `-`, `*`, `/`, `//`, `%`, `**`
4) **Operadores de comparación:** `==`, `!=`, `>`, `<`, `>=`, `<=`
5) **Operadores lógicos:** `and`, `or`, `not`
6) **Entrada/Salida:** `input()` y `print()`
7) **Conversión de tipos:** `int()`, `float()`, `str()`

<!--
Variables, Tipos, Operadores (matemáticos, lógicos, de comparación), Input/Output y Conversiones. Si entienden esto, ya tienen el 80% de la lógica de cualquier script.
-->
---
## Estructura de un Programa Simple

```python
# 1. Entrada: Pedir datos
nombre = input("¿Cómo te llamás? ")
edad = int(input("¿Cuántos años tenés? "))

# 2. Procesamiento: Hacer cálculos
año_nacimiento = 2024 - edad
mayor_de_edad = edad >= 18

# 3. Salida: Mostrar resultados
print(f"Hola {nombre}, naciste en {año_nacimiento}")
if mayor_de_edad:
    print("Sos mayor de edad")
```

<!--
Entrada -> Proceso -> Salida. Ese es el mantra. Pido datos, los mastico, muestro el resultado.
-->
---
## Buenas Prácticas

* Usá **nombres descriptivos** para variables
* **Snake_case** para nombres de variables
* Espacios alrededor de operadores: `x = 5 + 3`
* Comentarios para explicar el "por qué"
* **F-strings** para formatear texto
* Siempre **convertir** el resultado de `input()`

<!--
Sean prolijos. Nombres claros (`snake_case`), espacios para que respire el código, y comentarios útiles. Escriban código que les dé orgullo mostrar.
-->
---
<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Los fundamentos son la base de todo en programación. Dedicá tiempo a dominarlos.
