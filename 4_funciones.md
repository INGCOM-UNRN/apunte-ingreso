---
title: Funciones
short_title: 4 - Funciones
subtitle: Definición, parámetros, scope, documentación y buenas prácticas.
---

(funciones)=
# Funciones

## Introducción y Motivación

Hasta ahora has escrito código de forma secuencial: una instrucción tras otra. A medida que tus programas crecen, notarás que ciertos bloques de código se repiten. Las **funciones** son la solución: te permiten agrupar código relacionado bajo un nombre, y luego reutilizarlo cuantas veces necesites.

Imagina que necesitás calcular el promedio de varios conjuntos de números en diferentes partes de tu programa. Sin funciones, tendrías que escribir el mismo código una y otra vez. Con funciones, escribís el código una vez y lo invocás cuando lo necesites.

:::{important} ¿Por qué son importantes las funciones?
Las funciones te permiten:
- **Reutilizar código**: Escribís una vez, usás muchas veces
- **Organizar tu programa**: Dividís problemas grandes en partes más pequeñas
- **Facilitar el mantenimiento**: Modificás en un solo lugar
- **Hacer el código más legible**: Nombres descriptivos explican qué hace cada parte
- **Evitar errores**: Código testeado y reutilizado es menos propenso a bugs
- **Colaborar mejor**: Cada persona puede trabajar en funciones diferentes
:::

En este capítulo aprenderás:
- Definir y llamar funciones
- Trabajar con parámetros y argumentos
- Retornar valores
- Scope de variables (alcance)
- Documentar funciones con docstrings
- Parámetros por defecto y variables
- Funciones como objetos
- Buenas prácticas de diseño

---

(definir-funciones)=
## Definir y Llamar Funciones

### Sintaxis Básica

Una función se define con la palabra clave `def`:

```{code-cell} ipython3
def saludar():
    """Imprime un saludo."""
    print("¡Hola!")
```

**Componentes de una función:**
1. `def` - palabra clave para definir función
2. `saludar` - nombre de la función (snake_case)
3. `()` - paréntesis para parámetros (vacío si no hay)
4. `:` - dos puntos que indican inicio del bloque
5. Docstring - descripción de qué hace (opcional pero recomendado)
6. Cuerpo - código indentado que se ejecuta

### Llamar (Invocar) una Función

Para ejecutar una función, la **llamás** por su nombre:

```{code-cell} ipython3
def saludar():
    """Imprime un saludo."""
    print("¡Hola!")

# Llamar a la función
saludar()  # Salida: ¡Hola!
saludar()  # Salida: ¡Hola!
saludar()  # Salida: ¡Hola!
```

:::{note} Definición vs Llamada
Definir una función NO ejecuta su código. Solo lo ejecuta cuando la llamás.

```{code-cell} ipython3
# Esto define la función (no imprime nada aún)
def saludar():
    print("¡Hola!")

# Esto ejecuta la función (ahora sí imprime)
saludar()
```
:::

### Ejemplo: Función Simple

```{code-cell} ipython3
def mostrar_menu():
    """Muestra el menú de opciones."""
    print("=== MENÚ ===")
    print("1. Nueva partida")
    print("2. Cargar partida")
    print("3. Salir")

# Usar la función
mostrar_menu()
```

---

(parametros-argumentos)=
## Parámetros y Argumentos

Los **parámetros** permiten que las funciones reciban información para trabajar con ella.

### Funciones con Parámetros

```{code-cell} ipython3
def saludar_persona(nombre):
    """Saluda a una persona por su nombre.
    
    Args:
        nombre: El nombre de la persona a saludar.
    """
    print(f"¡Hola, {nombre}!")

# Llamar con diferentes argumentos
saludar_persona("Ana")      # ¡Hola, Ana!
saludar_persona("Bruno")    # ¡Hola, Bruno!
saludar_persona("Carlos")   # ¡Hola, Carlos!
```

**Terminología:**
- **Parámetro**: Variable en la definición de la función (`nombre`)
- **Argumento**: Valor que se pasa al llamar la función (`"Ana"`)

### Múltiples Parámetros

```{code-cell} ipython3
def calcular_rectangulo(base, altura):
    """Calcula el área y perímetro de un rectángulo.
    
    Args:
        base: La base del rectángulo.
        altura: La altura del rectángulo.
    """
    area = base * altura
    perimetro = 2 * (base + altura)
    print(f"Área: {area}")
    print(f"Perímetro: {perimetro}")

# Llamar con dos argumentos
calcular_rectangulo(5, 3)
# Salida:
# Área: 15
# Perímetro: 16
```

### Orden de los Argumentos

Los argumentos se pasan por **posición**:

```{code-cell} ipython3
def presentar(nombre, edad, ciudad):
    """Presenta a una persona."""
    print(f"{nombre} tiene {edad} años y vive en {ciudad}")

# Argumentos posicionales (el orden importa)
presentar("Ana", 20, "Buenos Aires")
# Ana tiene 20 años y vive en Buenos Aires

# Orden incorrecto
presentar(20, "Buenos Aires", "Ana")
# 20 tiene Buenos Aires años y vive en Ana ❌
```

### Argumentos con Nombre (Keyword Arguments)

Podés especificar argumentos por nombre:

```{code-cell} ipython3
def presentar(nombre, edad, ciudad):
    """Presenta a una persona."""
    print(f"{nombre} tiene {edad} años y vive en {ciudad}")

# Con keyword arguments (el orden no importa)
presentar(edad=20, nombre="Ana", ciudad="Buenos Aires")
# Ana tiene 20 años y vive en Buenos Aires

# Mezclar posicionales y keyword
presentar("Ana", ciudad="Buenos Aires", edad=20)
# Ana tiene 20 años y vive en Buenos Aires
```

:::{tip} Cuándo usar keyword arguments
Los keyword arguments mejoran la legibilidad, especialmente con:
- Muchos parámetros
- Parámetros booleanos
- Parámetros opcionales

```{code-cell} ipython3
# Menos claro
configurar_conexion("localhost", 8080, True, False, 30)

# Más claro
configurar_conexion(
    host="localhost",
    puerto=8080,
    ssl=True,
    debug=False,
    timeout=30
)
```
:::

---

(retornar-valores)=
## Retornar Valores

Según la {ref}`0x0009h`, las funciones no deben contener `print()` a menos que ese sea su propósito. En su lugar, deben **retornar** valores.

### La Sentencia `return`

```{code-cell} ipython3
def sumar(a, b):
    """Retorna la suma de dos números.
    
    Args:
        a: Primer número.
        b: Segundo número.
    
    Returns:
        La suma de a y b.
    """
    resultado = a + b
    return resultado

# Usar el valor retornado
total = sumar(5, 3)
print(total)  # 8

# O directamente en expresiones
doble = sumar(5, 3) * 2
print(doble)  # 16
```

### Return sin Valor

Si una función no tiene `return` o tiene `return` sin valor, retorna `None`:

```{code-cell} ipython3
def saludar(nombre):
    """Saluda a una persona."""
    print(f"¡Hola, {nombre}!")
    # No hay return explícito

resultado = saludar("Ana")
print(resultado)  # None
```

### Múltiples Returns

Podés tener múltiples `return` en diferentes puntos:

```{code-cell} ipython3
def clasificar_edad(edad):
    """Clasifica una edad en categorías.
    
    Args:
        edad: La edad a clasificar.
    
    Returns:
        La categoría correspondiente.
    """
    if edad < 0:
        return "Edad inválida"
    
    if edad < 13:
        return "Niño"
    
    if edad < 18:
        return "Adolescente"
    
    if edad < 65:
        return "Adulto"
    
    return "Adulto mayor"

print(clasificar_edad(10))   # Niño
print(clasificar_edad(25))   # Adulto
print(clasificar_edad(70))   # Adulto mayor
```

:::{tip} Retorno temprano (Early Return)
Según la {ref}`0x0008h`, el patrón de retornos tempranos es idiomático en Python para validaciones:

```{code-cell} ipython3
def dividir(a, b):
    """Divide dos números.
    
    Args:
        a: Dividendo.
        b: Divisor.
    
    Returns:
        El resultado de la división, o None si b es cero.
    """
    # Validación temprana
    if b == 0:
        return None
    
    return a / b
```
:::

### Retornar Múltiples Valores

Python permite retornar múltiples valores usando tuplas:

```{code-cell} ipython3
def estadisticas(numeros):
    """Calcula estadísticas de una lista.
    
    Args:
        numeros: Lista de números.
    
    Returns:
        Una tupla con (promedio, minimo, maximo).
    """
    promedio = sum(numeros) / len(numeros)
    minimo = min(numeros)
    maximo = max(numeros)
    
    return promedio, minimo, maximo

# Desempaquetar valores retornados
prom, min_val, max_val = estadisticas([1, 2, 3, 4, 5])
print(f"Promedio: {prom}, Min: {min_val}, Max: {max_val}")
# Promedio: 3.0, Min: 1, Max: 5
```

---

(scope-variables)=
## Scope de Variables (Alcance)

El **scope** determina dónde una variable es accesible en tu código.

### Variables Locales

Las variables definidas **dentro** de una función son **locales** a esa función:

```{code-cell} ipython3
def calcular():
    x = 10  # Variable local
    y = 20  # Variable local
    resultado = x + y
    return resultado

print(calcular())  # 30
# print(x)  # NameError: name 'x' is not defined
```

Las variables locales:
- Solo existen dentro de la función
- Se crean cuando la función se ejecuta
- Se destruyen cuando la función termina

### Variables Globales

Las variables definidas **fuera** de funciones son **globales**:

```{code-cell} ipython3
PI = 3.14159  # Variable global

def calcular_area_circulo(radio):
    """Calcula el área de un círculo.
    
    Args:
        radio: El radio del círculo.
    
    Returns:
        El área del círculo.
    """
    area = PI * radio ** 2  # Puede leer PI
    return area

print(calcular_area_circulo(5))  # 78.53975
```

:::{warning} Evitar modificar variables globales
Según la {ref}`0x000Bh`, debés evitar modificar variables globales dentro de funciones:

```{code-cell} ipython3
# ❌ Mala práctica
contador = 0

def incrementar():
    global contador  # Modifica variable global
    contador += 1

# ✓ Mejor práctica
def incrementar(contador):
    """Retorna el contador incrementado."""
    return contador + 1

# Uso
contador = 0
contador = incrementar(contador)
```
:::

### Constantes Globales

Las constantes globales (en MAYÚSCULAS) son aceptables:

```{code-cell} ipython3
# Constantes globales (solo lectura)
PI = 3.14159
GRAVEDAD = 9.81
MAX_INTENTOS = 3
TASA_IVA = 0.21

def calcular_precio_final(precio):
    """Calcula precio con IVA."""
    return precio * (1 + TASA_IVA)
```

### Diagrama de Scope

```{code-cell} ipython3
x = "global"  # Scope global

def funcion_externa():
    y = "externa"  # Scope de funcion_externa
    
    def funcion_interna():
        z = "interna"  # Scope de funcion_interna
        print(x)  # Puede acceder a global
        print(y)  # Puede acceder a externa
        print(z)  # Puede acceder a local
    
    funcion_interna()
    # print(z)  # ❌ Error: z no existe aquí

funcion_externa()
# print(y)  # ❌ Error: y no existe aquí
```

---

(parametros-defecto)=
## Parámetros por Defecto

Podés definir valores por defecto para parámetros:

```{code-cell} ipython3
def saludar(nombre, saludo="Hola"):
    """Saluda a una persona.
    
    Args:
        nombre: El nombre de la persona.
        saludo: El saludo a usar (default: "Hola").
    
    Returns:
        El saludo completo.
    """
    return f"{saludo}, {nombre}!"

# Usar valor por defecto
print(saludar("Ana"))  # Hola, Ana!

# Especificar valor diferente
print(saludar("Ana", "Buenos días"))  # Buenos días, Ana!
print(saludar("Ana", saludo="Buenas tardes"))  # Buenas tardes, Ana!
```

### Orden de Parámetros

Los parámetros con valores por defecto deben ir **después** de los obligatorios:

```python
# ✓ Correcto
def presentar(nombre, edad, ciudad="Buenos Aires"):
    print(f"{nombre}, {edad} años, {ciudad}")

# ❌ Incorrecto - SyntaxError
# def presentar(nombre, ciudad="Buenos Aires", edad):
#     print(f"{nombre}, {edad} años, {ciudad}")
```

### Valores por Defecto Mutables (Cuidado)

:::{danger} No usar listas o diccionarios vacíos como default
Los valores por defecto mutables se crean una sola vez:

```{code-cell} ipython3
# ❌ Problema común
def agregar_item(item, lista=[]):
    lista.append(item)
    return lista

# Comportamiento inesperado
print(agregar_item(1))  # [1]
print(agregar_item(2))  # [1, 2] ¡Inesperado!
print(agregar_item(3))  # [1, 2, 3] ¡Inesperado!

# ✓ Solución correcta
def agregar_item(item, lista=None):
    if lista is None:
        lista = []
    lista.append(item)
    return lista

print(agregar_item(1))  # [1]
print(agregar_item(2))  # [2] ✓ Como esperamos
```
:::

---

(args-kwargs)=
## Número Variable de Argumentos

### `*args` - Argumentos Posicionales Variables

El operador `*` permite recibir cualquier cantidad de argumentos posicionales:

```{code-cell} ipython3
def sumar_todos(*numeros):
    """Suma cualquier cantidad de números.
    
    Args:
        *numeros: Cantidad variable de números.
    
    Returns:
        La suma de todos los números.
    """
    total = 0
    for numero in numeros:
        total += numero
    return total

print(sumar_todos(1, 2, 3))        # 6
print(sumar_todos(1, 2, 3, 4, 5))  # 15
print(sumar_todos(10))             # 10
```

Los `*args` se reciben como una tupla:

```{code-cell} ipython3
def mostrar_args(*args):
    """Muestra los argumentos recibidos."""
    print(f"Tipo: {type(args)}")
    print(f"Contenido: {args}")

mostrar_args(1, 2, 3)
# Tipo: <class 'tuple'>
# Contenido: (1, 2, 3)
```

### `**kwargs` - Argumentos con Nombre Variables

El operador `**` permite recibir cualquier cantidad de argumentos con nombre:

```{code-cell} ipython3
def crear_perfil(nombre, **datos):
    """Crea un perfil con datos adicionales.
    
    Args:
        nombre: Nombre obligatorio.
        **datos: Datos adicionales opcionales.
    """
    print(f"Nombre: {nombre}")
    for clave, valor in datos.items():
        print(f"{clave}: {valor}")

crear_perfil("Ana", edad=20, ciudad="Buenos Aires", carrera="Ingeniería")
# Nombre: Ana
# edad: 20
# ciudad: Buenos Aires
# carrera: Ingeniería
```

Los `**kwargs` se reciben como un diccionario:

```{code-cell} ipython3
def mostrar_kwargs(**kwargs):
    """Muestra los kwargs recibidos."""
    print(f"Tipo: {type(kwargs)}")
    print(f"Contenido: {kwargs}")

mostrar_kwargs(a=1, b=2, c=3)
# Tipo: <class 'dict'>
# Contenido: {'a': 1, 'b': 2, 'c': 3}
```

### Combinando Parámetros

El orden debe ser:
1. Parámetros posicionales obligatorios
2. `*args`
3. Parámetros con nombre (con o sin default)
4. `**kwargs`

```{code-cell} ipython3
def funcion_completa(a, b, *args, c=10, **kwargs):
    """Ejemplo con todos los tipos de parámetros."""
    print(f"a={a}, b={b}")
    print(f"args={args}")
    print(f"c={c}")
    print(f"kwargs={kwargs}")

funcion_completa(1, 2, 3, 4, 5, c=20, x=100, y=200)
# a=1, b=2
# args=(3, 4, 5)
# c=20
# kwargs={'x': 100, 'y': 200}
```

---

(documentacion-funciones)=
## Documentación de Funciones (Docstrings)

Según la {ref}`0x000Ah`, todas las funciones deben tener un docstring.

### Formato de Docstrings

```{code-cell} ipython3
def calcular_promedio(numeros):
    """Calcula el promedio de una lista de números.
    
    Esta función toma una lista de números y retorna su promedio
    aritmético. Si la lista está vacía, retorna 0.
    
    Args:
        numeros: Lista de números (int o float).
    
    Returns:
        El promedio de los números como float.
        Retorna 0 si la lista está vacía.
    
    Raises:
        TypeError: Si numeros no es una lista o contiene no-números.
    
    Example:
        >>> calcular_promedio([1, 2, 3, 4, 5])
        3.0
        >>> calcular_promedio([])
        0
    """
    if not numeros:
        return 0
    return sum(numeros) / len(numeros)
```

**Componentes de un buen docstring:**
1. **Resumen de una línea**: Qué hace la función
2. **Descripción detallada** (opcional): Más contexto si es necesario
3. **Args**: Lista de parámetros y su descripción
4. **Returns**: Qué retorna y su tipo
5. **Raises** (opcional): Excepciones que puede lanzar
6. **Example** (opcional): Ejemplos de uso

### Docstring de Una Línea

Para funciones simples:

```{code-cell} ipython3
def es_par(numero):
    """Retorna True si el número es par."""
    return numero % 2 == 0

def cuadrado(x):
    """Retorna el cuadrado de x."""
    return x ** 2
```

### Acceder a Docstrings

```{code-cell} ipython3
def suma(a, b):
    """Retorna la suma de a y b."""
    return a + b

# Ver el docstring
print(suma.__doc__)
# Retorna la suma de a y b.

# Usar help()
help(suma)
```

---

(funciones-como-objetos)=
## Funciones como Objetos de Primera Clase

En Python, las funciones son **objetos de primera clase**: pueden asignarse a variables, pasarse como argumentos, y retornarse desde otras funciones.

### Asignar Funciones a Variables

```{code-cell} ipython3
def saludar(nombre):
    """Saluda a una persona."""
    return f"¡Hola, {nombre}!"

# Asignar función a variable
mi_funcion = saludar

# Llamar a través de la variable
print(mi_funcion("Ana"))  # ¡Hola, Ana!
```

### Pasar Funciones como Argumentos

```{code-cell} ipython3
def aplicar_operacion(a, b, operacion):
    """Aplica una operación a dos números.
    
    Args:
        a: Primer número.
        b: Segundo número.
        operacion: Función que toma dos números.
    
    Returns:
        El resultado de aplicar la operación.
    """
    return operacion(a, b)

def sumar(x, y):
    """Retorna la suma de x e y."""
    return x + y

def multiplicar(x, y):
    """Retorna el producto de x e y."""
    return x * y

# Pasar funciones como argumentos
print(aplicar_operacion(5, 3, sumar))        # 8
print(aplicar_operacion(5, 3, multiplicar))  # 15
```

### Funciones Lambda (Anónimas)

Las funciones lambda son funciones pequeñas de una línea:

```{code-cell} ipython3
# Función normal
def cuadrado(x):
    return x ** 2

# Función lambda equivalente
cuadrado_lambda = lambda x: x ** 2

print(cuadrado(5))        # 25
print(cuadrado_lambda(5)) # 25

# Útil para operaciones simples
numeros = [1, 2, 3, 4, 5]
cuadrados = list(map(lambda x: x ** 2, numeros))
print(cuadrados)  # [1, 4, 9, 16, 25]
```

:::{tip} Cuándo usar lambda
Las lambdas son útiles para:
- Funciones simples de una línea
- Argumentos a funciones como `map()`, `filter()`, `sorted()`

Para funciones más complejas, usá `def` con un nombre descriptivo.
:::

---

(recursion)=
## Recursión (Opcional)

Una función **recursiva** es una que se llama a sí misma.

### Ejemplo: Factorial

```{code-cell} ipython3
def factorial(n):
    """Calcula el factorial de n recursivamente.
    
    Args:
        n: Número entero no negativo.
    
    Returns:
        El factorial de n.
    """
    # Caso base
    if n == 0 or n == 1:
        return 1
    
    # Caso recursivo
    return n * factorial(n - 1)

print(factorial(5))  # 120
# 5! = 5 × 4 × 3 × 2 × 1 = 120
```

**Flujo de ejecución:**
```
factorial(5)
= 5 * factorial(4)
= 5 * (4 * factorial(3))
= 5 * (4 * (3 * factorial(2)))
= 5 * (4 * (3 * (2 * factorial(1))))
= 5 * (4 * (3 * (2 * 1)))
= 5 * (4 * (3 * 2))
= 5 * (4 * 6)
= 5 * 24
= 120
```

### Componentes de Recursión

Toda función recursiva necesita:
1. **Caso base**: Condición de parada
2. **Caso recursivo**: Llamada a sí misma con problema más pequeño

```{code-cell} ipython3
def suma_recursiva(n):
    """Suma números de 1 a n recursivamente.
    
    Args:
        n: Número hasta el cual sumar.
    
    Returns:
        La suma de 1 + 2 + ... + n.
    """
    # Caso base
    if n == 1:
        return 1
    
    # Caso recursivo
    return n + suma_recursiva(n - 1)

print(suma_recursiva(5))  # 15
# 5 + 4 + 3 + 2 + 1 = 15
```

:::{warning} Cuidado con recursión infinita
Sin caso base, la función se llamará infinitamente:

```{code-cell} ipython3
# ❌ Recursión infinita
def mala_recursion(n):
    return mala_recursion(n - 1)  # No hay caso base!

# Esto causará: RecursionError: maximum recursion depth exceeded
```
:::

---

(buenas-practicas-funciones)=
## Buenas Prácticas

### 1. Responsabilidad Única

Según la {ref}`0x000Ch`, cada función debe hacer una sola cosa:

```{code-cell} ipython3
# ❌ Hace demasiado
def procesar_y_mostrar_datos(datos):
    """Procesa y muestra datos."""
    # Valida
    if not datos:
        return
    
    # Procesa
    resultado = sum(datos) / len(datos)
    
    # Formatea
    texto = f"Promedio: {resultado:.2f}"
    
    # Muestra
    print(texto)
    
    return resultado

# ✓ Una responsabilidad por función
def calcular_promedio(datos):
    """Calcula el promedio de datos."""
    if not datos:
        return 0
    return sum(datos) / len(datos)

def formatear_promedio(promedio):
    """Formatea el promedio para mostrar."""
    return f"Promedio: {promedio:.2f}"

# Uso
datos = [1, 2, 3, 4, 5]
promedio = calcular_promedio(datos)
texto = formatear_promedio(promedio)
print(texto)
```

### 2. Nombres Descriptivos

```{code-cell} ipython3
# ❌ Nombres poco claros
def calc(x, y):
    return x / y

# ✓ Nombres descriptivos
def calcular_promedio(suma_total, cantidad_elementos):
    """Calcula el promedio de elementos."""
    return suma_total / cantidad_elementos
```

### 3. Evitar Efectos Secundarios

Las funciones deben evitar modificar argumentos mutables:

```{code-cell} ipython3
# ❌ Modifica el argumento
def agregar_iva_mal(precios):
    """Agrega IVA a lista de precios."""
    for i in range(len(precios)):
        precios[i] *= 1.21  # Modifica lista original
    return precios

# ✓ Retorna nueva lista
def agregar_iva(precios):
    """Retorna nueva lista con IVA agregado."""
    return [precio * 1.21 for precio in precios]
```

### 4. Parámetros Razonables

No uses demasiados parámetros:

```{code-cell} ipython3
# ❌ Demasiados parámetros
def crear_usuario(nombre, apellido, edad, email, telefono, 
                  direccion, ciudad, codigo_postal, pais):
    pass

# ✓ Usar diccionario o clase
def crear_usuario(nombre, apellido, datos_contacto):
    """Crea un usuario.
    
    Args:
        nombre: Nombre del usuario.
        apellido: Apellido del usuario.
        datos_contacto: Dict con email, telefono, direccion, etc.
    """
    pass
```

### 5. Funciones Pequeñas

Una función no debería tener más de ~20-30 líneas:

```{code-cell} ipython3
# ✓ Función pequeña y enfocada
def es_email_valido(email):
    """Verifica si un email es válido."""
    return "@" in email and "." in email.split("@")[1]

# ✓ Función descompuesta en partes más pequeñas
def procesar_inscripcion(datos):
    """Procesa una inscripción."""
    if not validar_datos(datos):
        return False
    
    usuario = crear_usuario(datos)
    enviar_confirmacion(usuario)
    registrar_log(usuario)
    
    return True
```

### 6. Retornar, No Imprimir

```{code-cell} ipython3
# ❌ Imprime en lugar de retornar
def calcular_total(items):
    total = sum(item['precio'] for item in items)
    print(f"Total: ${total}")  # Mezcla lógica con presentación

# ✓ Retorna el valor
def calcular_total(items):
    """Calcula el total de items.
    
    Args:
        items: Lista de dicts con clave 'precio'.
    
    Returns:
        El total como float.
    """
    return sum(item['precio'] for item in items)

# El código que llama decide qué hacer con el resultado
total = calcular_total(items)
print(f"Total: ${total}")
```

---

(errores-comunes-funciones)=
## Errores Comunes

### 1. Olvidar el Return

```{code-cell} ipython3
# ❌ Olvidó return
def sumar(a, b):
    resultado = a + b  # No retorna nada

total = sumar(5, 3)
print(total)  # None

# ✓ Con return
def sumar(a, b):
    return a + b

total = sumar(5, 3)
print(total)  # 8
```

### 2. Confundir Parámetros y Argumentos

```{code-cell} ipython3
# ❌ Cantidad incorrecta de argumentos
def saludar(nombre, edad):
    print(f"Hola {nombre}, tienes {edad} años")

saludar("Ana")  # TypeError: missing 1 required positional argument

# ✓ Argumentos correctos
saludar("Ana", 20)
```

### 3. Modificar Argumentos Mutables

```{code-cell} ipython3
# ❌ Efecto secundario inesperado
def duplicar_valores(lista):
    for i in range(len(lista)):
        lista[i] *= 2
    return lista

original = [1, 2, 3]
duplicada = duplicar_valores(original)
print(original)   # [2, 4, 6] ¡Modificó el original!
print(duplicada)  # [2, 4, 6]

# ✓ Sin modificar el original
def duplicar_valores(lista):
    return [x * 2 for x in lista]

original = [1, 2, 3]
duplicada = duplicar_valores(original)
print(original)   # [1, 2, 3] ✓
print(duplicada)  # [2, 4, 6]
```

### 4. No Documentar Funciones

```{code-cell} ipython3
# ❌ Sin documentación
def calc(x, y, z):
    return x * y + z

# ✓ Con documentación
def calcular_costo_total(precio_unitario, cantidad, envio):
    """Calcula el costo total de una compra.
    
    Args:
        precio_unitario: Precio de un item.
        cantidad: Cantidad de items.
        envio: Costo de envío.
    
    Returns:
        El costo total (items + envío).
    """
    return precio_unitario * cantidad + envio
```

### 5. Variables Globales sin Declarar

```{code-cell} ipython3
contador = 0

# ❌ Error: intenta modificar sin 'global'
def incrementar_mal():
    contador += 1  # UnboundLocalError

# ✓ Pero mejor: no usar global
def incrementar(valor):
    return valor + 1

contador = 0
contador = incrementar(contador)
```

---

(ejercicios-funciones)=
## Ejercicios

(ejercicio-4-1)=
### Ejercicio 4.1: Calculadora Modular

Creá una calculadora usando funciones separadas para cada operación.

**Requerimientos:**
- Funciones: `sumar()`, `restar()`, `multiplicar()`, `dividir()`
- Cada función debe tener docstring
- `dividir()` debe manejar división por cero (retornar None)
- Función `main()` que muestre menú y use las operaciones

**Ejemplo:**
```
=== CALCULADORA ===
1. Sumar
2. Restar
3. Multiplicar
4. Dividir
5. Salir

Opción: 1
Primer número: 10
Segundo número: 5
Resultado: 15.0
```

---

(ejercicio-4-2)=
### Ejercicio 4.2: Validación de Datos

Escribí funciones para validar diferentes tipos de datos:

**Funciones a implementar:**
```{code-cell} ipython3
def es_email_valido(email):
    """Verifica si un email es válido (contiene @ y .)."""
    pass

def es_telefono_valido(telefono):
    """Verifica si un teléfono tiene 10 dígitos."""
    pass

def es_edad_valida(edad):
    """Verifica si edad está entre 0 y 120."""
    pass

def validar_formulario(email, telefono, edad):
    """Retorna True si todos los datos son válidos."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
print(es_email_valido("ana@example.com"))  # True
print(es_email_valido("ana.com"))          # False
print(es_telefono_valido("1234567890"))    # True
print(es_edad_valida(25))                  # True
```

---

(ejercicio-4-3)=
### Ejercicio 4.3: Análisis de Texto

Creá funciones para analizar texto:

**Funciones:**
```{code-cell} ipython3
def contar_palabras(texto):
    """Retorna la cantidad de palabras."""
    pass

def contar_vocales(texto):
    """Retorna la cantidad de vocales."""
    pass

def palabra_mas_larga(texto):
    """Retorna la palabra más larga."""
    pass

def invertir_palabras(texto):
    """Retorna el texto con palabras invertidas."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
texto = "Python es un lenguaje poderoso"
print(contar_palabras(texto))      # 5
print(contar_vocales(texto))       # 11
print(palabra_mas_larga(texto))    # "lenguaje"
print(invertir_palabras(texto))    # "nohtyP se nu ejaugnel osoredop"
```

---

(ejercicio-4-4)=
### Ejercicio 4.4: Conversión de Temperaturas

Implementá funciones para convertir temperaturas entre Celsius, Fahrenheit y Kelvin.

**Fórmulas:**
$$
F = C \times \frac{9}{5} + 32
$$
$$
K = C + 273.15
$$

**Funciones:**
```{code-cell} ipython3
def celsius_a_fahrenheit(celsius):
    pass

def fahrenheit_a_celsius(fahrenheit):
    pass

def celsius_a_kelvin(celsius):
    pass

def kelvin_a_celsius(kelvin):
    pass
```

:::{tip}
Implementá solo conversiones desde/hacia Celsius, luego podés combinarlas para otras conversiones.
:::

---

(ejercicio-4-5)=
### Ejercicio 4.5: Generador de Contraseñas

Creá una función que genere contraseñas aleatorias.

**Requerimientos:**
```{code-cell} ipython3
def generar_contraseña(longitud=8, incluir_numeros=True, 
                       incluir_simbolos=True):
    """Genera una contraseña aleatoria.
    
    Args:
        longitud: Longitud de la contraseña (default: 8).
        incluir_numeros: Si incluir números (default: True).
        incluir_simbolos: Si incluir símbolos (default: True).
    
    Returns:
        String con la contraseña generada.
    """
    pass
```

**Ejemplo:**
```{code-cell} ipython3
print(generar_contraseña())           # "aB3$xY9!"
print(generar_contraseña(12))         # "aB3$xY9!mK2@"
print(generar_contraseña(10, False))  # "aBxYmKpQ"
```

:::{tip}
Usá `import random` y `random.choice()` para elegir caracteres aleatorios.
:::

---

(ejercicio-4-6)=
### Ejercicio 4.6: Estadísticas de Lista

Implementá funciones estadísticas sin usar funciones built-in:

**Funciones:**
```{code-cell} ipython3
def calcular_promedio(numeros):
    """Calcula el promedio."""
    pass

def encontrar_mediana(numeros):
    """Encuentra la mediana (valor del medio)."""
    pass

def encontrar_moda(numeros):
    """Encuentra el valor más frecuente."""
    pass

def calcular_rango(numeros):
    """Calcula el rango (max - min)."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
datos = [1, 2, 2, 3, 4, 5, 5, 5, 6]
print(calcular_promedio(datos))  # 3.67
print(encontrar_mediana(datos))  # 4
print(encontrar_moda(datos))     # 5
print(calcular_rango(datos))     # 5
```

---

(ejercicio-4-7)=
### Ejercicio 4.7: Fibonacci con y sin Recursión

Implementá la secuencia de Fibonacci de dos formas:

**Versión Iterativa:**
```{code-cell} ipython3
def fibonacci_iterativo(n):
    """Retorna el n-ésimo número de Fibonacci iterativamente."""
    pass
```

**Versión Recursiva:**
```{code-cell} ipython3
def fibonacci_recursivo(n):
    """Retorna el n-ésimo número de Fibonacci recursivamente."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
for i in range(10):
    print(fibonacci_iterativo(i), end=" ")
# 0 1 1 2 3 5 8 13 21 34
```

:::{tip}
La secuencia de Fibonacci: cada número es la suma de los dos anteriores.
F(0) = 0, F(1) = 1, F(n) = F(n-1) + F(n-2)
:::

---

(ejercicio-4-8)=
### Ejercicio 4.8: Juego de Piedra, Papel o Tijera

Creá un juego usando funciones modulares.

**Funciones sugeridas:**
```{code-cell} ipython3
def obtener_jugada_usuario():
    """Solicita y valida jugada del usuario."""
    pass

def obtener_jugada_computadora():
    """Genera jugada aleatoria para la computadora."""
    pass

def determinar_ganador(jugada_usuario, jugada_computadora):
    """Determina quién ganó.
    
    Returns:
        "usuario", "computadora" o "empate"
    """
    pass

def mostrar_resultado(jugada_usuario, jugada_computadora, ganador):
    """Muestra el resultado del juego."""
    pass

def jugar():
    """Función principal del juego."""
    pass
```

---

(ejercicio-4-9)=
### Ejercicio 4.9: Sistema de Calificaciones

Implementá un sistema para calcular calificaciones finales.

**Funciones:**
```{code-cell} ipython3
def calcular_promedio_examenes(examenes):
    """Calcula promedio de lista de exámenes."""
    pass

def calcular_nota_trabajos(trabajos, pesos):
    """Calcula nota ponderada de trabajos."""
    pass

def calcular_nota_final(promedio_examenes, nota_trabajos, 
                        participacion):
    """Calcula nota final: 60% exámenes, 30% trabajos, 10% participación."""
    pass

def obtener_letra(nota):
    """Convierte nota numérica a letra (A, B, C, D, F)."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
examenes = [85, 90, 88]
trabajos = [90, 85, 92]
pesos = [0.3, 0.3, 0.4]
participacion = 95

prom_ex = calcular_promedio_examenes(examenes)
nota_trab = calcular_nota_trabajos(trabajos, pesos)
final = calcular_nota_final(prom_ex, nota_trab, participacion)
letra = obtener_letra(final)

print(f"Nota final: {final:.2f} ({letra})")
```

---

(ejercicio-4-10)=
### Ejercicio 4.10: Conversor de Bases Numéricas

Implementá funciones para convertir números entre diferentes bases.

**Funciones:**
```{code-cell} ipython3
def decimal_a_binario(decimal):
    """Convierte decimal a binario (como string)."""
    pass

def binario_a_decimal(binario):
    """Convierte binario (string) a decimal."""
    pass

def decimal_a_hexadecimal(decimal):
    """Convierte decimal a hexadecimal."""
    pass
```

**Ejemplo:**
```{code-cell} ipython3
print(decimal_a_binario(10))      # "1010"
print(binario_a_decimal("1010"))  # 10
print(decimal_a_hexadecimal(255)) # "FF"
```

:::{tip}
Para binario, usá divisiones sucesivas por 2 y guardá los restos.
:::

---

(ejercicio-4-11)=
### Ejercicio 4.11: Manipulación de Matrices

Creá funciones para trabajar con matrices (listas de listas).

**Funciones:**
```{code-cell} ipython3
def crear_matriz(filas, columnas, valor_inicial=0):
    """Crea matriz de filas×columnas con valor inicial."""
    pass

def sumar_matrices(matriz1, matriz2):
    """Suma dos matrices elemento por elemento."""
    pass

def multiplicar_por_escalar(matriz, escalar):
    """Multiplica matriz por un número."""
    pass

def transponer_matriz(matriz):
    """Retorna la transpuesta de la matriz."""
    pass
```

---

(ejercicio-4-12)=
### Ejercicio 4.12: Sistema de Inventario

Creá un sistema de inventario modular usando funciones.

**Funciones sugeridas:**
```{code-cell} ipython3
def agregar_producto(inventario, nombre, precio, cantidad):
    """Agrega o actualiza producto en inventario."""
    pass

def eliminar_producto(inventario, nombre):
    """Elimina producto del inventario."""
    pass

def buscar_producto(inventario, nombre):
    """Busca y retorna datos de un producto."""
    pass

def calcular_valor_total(inventario):
    """Calcula valor total del inventario."""
    pass

def productos_con_stock_bajo(inventario, minimo=10):
    """Retorna lista de productos con stock bajo."""
    pass

def generar_reporte(inventario):
    """Genera reporte formateado del inventario."""
    pass
```

**Estructura del inventario:**
```{code-cell} ipython3
inventario = {
    "manzana": {"precio": 2.5, "cantidad": 100},
    "banana": {"precio": 1.8, "cantidad": 5},
    "naranja": {"precio": 3.0, "cantidad": 80}
}
```


---

(uso-ia-funciones)=
## Uso Ético y Efectivo de la IA en Funciones

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Aprender a descomponer problemas en funciones es una habilidad fundamental. La IA puede ayudarte a mejorar tus funciones, pero **vos debés diseñar la descomposición** del problema.
:::

### Buenas Prácticas para Funciones

#### Generar Ejercicios Adicionales

- *"Genera ejercicios sobre funciones que reciban parámetros y retornen valores"*
- *"Crea problemas que requieran descomponer un programa en múltiples funciones"*
- *"Dame ejercicios de funciones recursivas simples para practicar"*

#### Obtener Pistas sobre Diseño

- *"Tengo un programa que hace varias cosas. ¿Cómo decido qué partes convertir en funciones?"*
- *"Mi función `procesar_datos()` hace tres cosas diferentes. ¿Debería dividirla?"*
- *"¿Cómo elijo buenos nombres para mis funciones?"*

#### Refactorizar y Mejorar

- *"Esta es mi función para calcular el promedio: [código]. ¿Cumple con el principio de responsabilidad única?"*
- *"Mi docstring es: 'Calcula cosas'. ¿Cómo puedo mejorarlo siguiendo PEP 257?"*
- *"¿Esta función debería retornar un valor o modificar un parámetro?"*

#### Debugging de Funciones

- *"Mi función retorna `None` en lugar del valor que calcula. ¿Qué estoy olvidando?"*
- *"Tengo un error de scope: mi función no puede acceder a una variable. ¿Por qué?"*
- *"Llamo a mi función pero dice que falta un argumento. ¿Cómo lo soluciono?"*

#### Explorar Técnicas

- *"¿Cuándo debería usar un parámetro con valor por defecto?"*
- *"¿Cuál es la diferencia entre parámetros posicionales y parámetros con nombre?"*
- *"¿Qué son los type hints y debería usarlos?"*

### Ejemplos Específicos de este Módulo

**Situación 1**: Descomposición en funciones

❌ **Incorrecto**:
```
Prompt: "Tengo que hacer un programa que calcule el IMC y lo clasifique.
Dame el código con funciones."
```

✅ **Correcto**:
```
Prompt: "Estoy descomponiendo un programa de IMC en funciones.
Identifiqué estas tareas: calcular IMC, clasificar IMC, pedir datos, mostrar resultado.
¿Es una buena división? ¿Debería combinar o dividir más?"
```

**Situación 2**: Parámetros y retorno

❌ **Incorrecto**:
```
Prompt: "¿Cómo hago para que mi función use una variable del main?"
```

✅ **Correcto**:
```
Prompt: "Mi función necesita un valor que está en main. ¿Debería:
a) Pasarlo como parámetro
b) Usar una variable global
c) Otra opción?
Explica ventajas y desventajas."
```

### Enfoque en Buenas Prácticas

:::{tip} Checklist antes de consultar la IA
Antes de pedir ayuda sobre una función, verificá:

- [ ] ¿Tiene un nombre descriptivo?
- [ ] ¿Hace una sola cosa (SRP)?
- [ ] ¿Tiene docstring completo?
- [ ] ¿Usa `return` correctamente?
- [ ] ¿Evita efectos secundarios (no print/input a menos que sea su propósito)?
- [ ] ¿Los nombres de parámetros son descriptivos?

Si no cumple estos criterios, **refactoriza primero**, luego consultá.
:::

### Uso Avanzado: Crítica de Diseño

Una vez que hayas escrito tus funciones:

```
Prompt: "Escribí estas tres funciones para un programa de validación de contraseña:
[pega tu código]

¿Están bien diseñadas? ¿Hay algo que viole principios de diseño?
¿Los nombres son suficientemente descriptivos?
¿Los docstrings están completos?"
```

Este tipo de revisión te ayuda a **mejorar tu estilo** y aprender buenas prácticas.

### Errores Comunes en este Módulo

:::{danger} No pidas que la IA escriba tus funciones
La capacidad de **descomponer un problema en funciones** es lo que estás aprendiendo. Si la IA hace esta descomposición por vos, perdés el objetivo del módulo.

**Proceso correcto:**
1. Vos identificás las tareas del problema
2. Vos decidís qué funciones necesitás
3. Vos escribís las funciones básicas
4. La IA te ayuda a **refinar** lo que ya escribiste
:::

---


---

## Resumen

En este capítulo aprendiste sobre funciones en Python:

✓ **Definir y llamar funciones**: Sintaxis básica y componentes  
✓ **Parámetros y argumentos**: Posicionales, keyword, múltiples  
✓ **Retornar valores**: Simple, múltiple, retorno temprano  
✓ **Scope de variables**: Local, global, constantes  
✓ **Parámetros por defecto**: Valores opcionales y cuidados  
✓ **`*args` y `**kwargs`**: Número variable de argumentos  
✓ **Documentación**: Docstrings con formato apropiado  
✓ **Funciones como objetos**: Primera clase, lambda  
✓ **Recursión**: Caso base y recursivo (opcional)  
✓ **Buenas prácticas**: Responsabilidad única, nombres, efectos secundarios  

Las funciones son fundamentales para escribir código modular, reutilizable y mantenible. Te permiten dividir problemas complejos en partes más pequeñas y manejables, cada una con una responsabilidad clara.

:::{important} La modularización es clave
Un programa bien diseñado está compuesto de muchas funciones pequeñas, cada una haciendo una cosa bien. Esto facilita:
- Entender el código
- Testear cada parte por separado
- Encontrar y corregir errores
- Reutilizar código en diferentes contextos
- Trabajar en equipo

Pensá en funciones como "bloques de construcción" que combinás para crear programas más grandes.
:::

En el próximo capítulo, aprenderás sobre modularización avanzada: cómo organizar funciones en módulos y paquetes, y cómo trabajar con archivos para persistir datos.
