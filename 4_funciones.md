---
title: Funciones
short_title: 4 - Funciones
subtitle: Definición, parámetros, scope, documentación y buenas prácticas.
---

(funciones)=
# Funciones

:::{tip} Objetivos de Aprendizaje

Al finalizar este capítulo serás capaz de:
- Definir y llamar funciones para reutilizar código.
- Trabajar con diferentes tipos de parámetros y argumentos.
- Retornar valores y usarlos en tu programa.
- Entender el scope (alcance) de las variables.
- Documentar funciones profesionalmente.
- Aplicar buenas prácticas en el diseño de funciones.
- **Descomponer problemas complejos en funciones más simples.**
- **Aplicar principios de diseño funcional (SRP, DRY, abstracción).**
:::

---

## Introducción: ¿Qué es una Función?

::::{grid} 1 1 2 2

:::{grid-item-card} Analogía: La Máquina Mágica
Imaginate que tenés una **máquina mágica** que hace algo específico. Le ponés ingredientes (los {term}`argumentos <Argumento>`), la máquina hace su trabajo, y te devuelve un resultado.

Por ejemplo: una licuadora es como una función. Le das frutas (argumentos), apretás el botón (llamás a la función), y te devuelve un licuado ({term}`valor de retorno`).
:::

:::{grid-item-card} En Programación
Una {term}`función` es un bloque de código que:
1. Tiene un **nombre** para identificarla.
2. Puede recibir **datos de entrada** (parámetros).
3. Realiza una **tarea específica**.
4. Puede **devolver un resultado**.
5. Se puede **reutilizar** todas las veces que quieras.
:::
::::

### ¿Por qué Usar Funciones?

Sin funciones, tu código se vería así:

```python
# Calcular promedio del primer examen
suma1 = 7 + 8 + 9
cantidad1 = 3
promedio1 = suma1 / cantidad1
print(f"Promedio examen 1: {promedio1}")

# Calcular promedio del segundo examen (REPETIMOS TODO)
suma2 = 6 + 7 + 8
cantidad2 = 3
promedio2 = suma2 / cantidad2
print(f"Promedio examen 2: {promedio2}")

# Calcular promedio del tercer examen (OTRA VEZ)
suma3 = 9 + 9 + 10
cantidad3 = 3
promedio3 = suma3 / cantidad3
print(f"Promedio examen 3: {promedio3}")
```

Con funciones, es mucho más simple:

```python
def calcular_promedio(notas):
    """Calcula el promedio de una lista de notas."""
    if not notas:
        return 0
    return sum(notas) / len(notas)

# Ahora solo llamamos a la función
print(f"Promedio examen 1: {calcular_promedio([7, 8, 9])}")
print(f"Promedio examen 2: {calcular_promedio([6, 7, 8])}")
print(f"Promedio examen 3: {calcular_promedio([9, 9, 10])}")
```

:::{important} Ventajas de las Funciones
- **Reutilización**: Escribís el código una sola vez.
- **Organización**: Código más limpio y fácil de leer.
- **Mantenimiento**: Si hay que cambiar algo, lo hacés en un solo lugar.
- **Menos errores**: Código probado y reutilizado es más confiable.
- **Colaboración**: Varios programadores pueden trabajar en diferentes funciones.
- **Modularidad**: Dividís problemas grandes en piezas pequeñas.
:::

### En este Capítulo Aprenderás

::::{grid} 1 1 2 3

:::{grid-item-card} Básico
- Definir funciones.
- Llamar funciones.
- Parámetros y argumentos.
- Retornar valores.
:::

:::{grid-item-card} Intermedio
- {term}`Scope` de variables.
- {term}`Parámetros por defecto <Parámetro por defecto>`.
- Documentación (docstrings).
- Funciones como objetos.
:::

:::{grid-item-card} Avanzado
- {term}`Recursión`.
- Buenas prácticas.
- Patrones comunes.
:::
::::

---

(definir-funciones)=
## Definir y Llamar Funciones

### Tu Primera Función 

Empecemos con lo más simple. Para crear una {term}`función`, usamos la palabra mágica `def` (de "definir"):

```python
def saludar():
    """Imprime un saludo amigable."""
    print("¡Hola! Bienvenido/a a Python")
```

¡Felicitaciones! Acabás de crear tu primera función. Pero... ¿por qué no pasa nada?

:::{note} ¿Por qué no imprime nada?
Porque **definir** una {term}`función` es como escribir una receta en un libro de cocina. La receta existe, pero no se cocina automáticamente. Para que funcione, tenés que **llamarla**:

```python
def saludar():
    """Imprime un saludo amigable."""
    print("¡Hola! Bienvenido/a a Python")

# Ahora sí, llamamos a la función
saludar()  # Esto ejecuta el código dentro de la función
```
:::

### Anatomía de una Función

Veamos de qué partes está hecha una {term}`función`:

```{figure} ./4_funciones/funcion_basica.svg
:name: fig-funcion-basica
:alt: Anatomía de una función
:align: center
:width: 90%

Componentes de una función en Python
```

::::{grid} 1 1 2 2

:::{grid-item-card} Componentes Esenciales
**1. Palabra clave `def`**
Indica que vas a definir una {term}`función`.

**2. Nombre de la {term}`función`**
Usa `snake_case`: todo minúsculas con guiones bajos.

**3. Paréntesis `()`**
Contienen los parámetros (si los hay).

**4. Dos puntos `:`**
Marcan el inicio del bloque de código.
:::

:::{grid-item-card} Componentes Opcionales
**5. {term}`docstring`**
Texto entre `"""` que explica qué hace la función.

**6. Cuerpo**
Código indentado que se ejecuta cuando llamás a la función.

**7. Return**
Devuelve un valor (lo veremos más adelante).
:::
::::

### Ejemplo Paso a Paso

```python
# Paso 1: Definir la función
def mostrar_bienvenida():
    """Muestra un mensaje de bienvenida decorado."""
    print("╔══════════════════════════╗")
    print("║   ¡Bienvenido/a a mi     ║")
    print("║   Programa en Python!    ║")
    print("╚══════════════════════════╝")

# Paso 2: Llamar la función (ejecutarla)
mostrar_bienvenida()
```

:::{tip} Podés Llamarla Múltiples Veces
Una vez que definiste la función, podés usarla todas las veces que quieras:

```python
def aplaudir():
    """Muestra un aplauso."""
    print("¡Bien hecho!")

# Usar la función varias veces
aplaudir()
aplaudir()
aplaudir()
print("¡Lo lograste!")
aplaudir()
```
:::

### Flujo de Ejecución

Cuando llamás a una función, el programa "salta" al código de la función, lo ejecuta, y luego vuelve:

```{figure} ./4_funciones/flujo_funcion.svg
:name: fig-flujo-funcion
:alt: Flujo de ejecución de una función
:align: center
:width: 90%

Cómo fluye la ejecución cuando llamás a una función
```

```python
def contar_hasta_tres():
    """Cuenta del 1 al 3."""
    print("  → Estoy dentro de la función")
    print("  1")
    print("  2")
    print("  3")
    print("  → Saliendo de la función")

print("Inicio del programa")
print("Voy a llamar a la función...")
contar_hasta_tres()  # Aquí "salta" a la función
print("Volví del la función")
print("Fin del programa")
```

:::{important} Observá el Flujo
1. El programa ejecuta línea por línea.
2. Cuando llega a `contar_hasta_tres()`, **salta** a la función.
3. Ejecuta todo el código dentro de la función.
4. Cuando termina, **vuelve** justo después de donde fue llamada.
5. Continúa con el resto del programa.
:::

### Ejercicio Práctico: Jugá con Funciones

```python
def dibujar_separador():
    """Dibuja una línea decorativa."""
    print("=" * 40)

def mostrar_titulo(texto):
    """Muestra un título formateado."""
    dibujar_separador()
    print(texto.center(40))
    dibujar_separador()

# Probá tu función
mostrar_titulo("MI PRIMER PROGRAMA")
print("Este programa usa funciones")
print("para organizar mejor el código")
dibujar_separador()
```

---

(parametros-argumentos)=
## Parámetros y Argumentos

### Funciones que Reciben Información

Las {term}`funciones <Función>` son más útiles cuando pueden trabajar con diferentes datos. Es como una licuadora: podés ponerle diferentes frutas cada vez.

```python
def saludar_persona(nombre):
    """Saluda a una persona por su nombre."""
    print(f"¡Hola, {nombre}! ¿Cómo estás?")

# Misma función, diferentes datos
saludar_persona("Ana")
saludar_persona("Bruno")
saludar_persona("Carlos")
```

:::{note} Vocabulario Importante

**Parámetro** = La "casilla" donde va a entrar el dato (en la definición).
```python
def saludar(nombre):  # ← "nombre" es el PARÁMETRO
    print(f"Hola, {nombre}")
```

**Argumento** = El dato real que le pasás (en la llamada).
```python
saludar("Ana")  # ← "Ana" es el ARGUMENTO
```

**Pensalo así**: El parámetro es como un molde, el argumento es lo que ponés en ese molde.
:::

### Múltiples Parámetros

Una función puede recibir varios datos a la vez:

```python
def presentar_persona(nombre, edad, ciudad):
    """Presenta a una persona con todos sus datos."""
    print(f"Te presento a {nombre}")
    print(f"  → Tiene {edad} años")
    print(f"  → Vive en {ciudad}")

presentar_persona("Ana", 20, "Buenos Aires")
presentar_persona("Bruno", 22, "Córdoba")
```

```{figure} ./4_funciones/parametros_tipos.svg
:name: fig-parametros-tipos
:alt: Tipos de parámetros y argumentos
:align: center
:width: 95%

Diferentes formas de pasar argumentos a una función
```

### Tipo 1: {term}`Argumentos Posicionales <Argumento posicional>`

Los argumentos se pasan **en orden**. La posición importa:

```python
def restar(a, b):
    """Resta b de a."""
    resultado = a - b
    print(f"{a} - {b} = {resultado}")
    return resultado

restar(10, 3)   # 10 - 3 = 7
restar(3, 10)   # 3 - 10 = -7  ← ¡Orden diferente, resultado diferente!
```

:::{warning} ¡El Orden Importa!
```python
def describir_mascota(nombre, tipo, edad):
    """Describe una mascota."""
    print(f"{nombre} es un {tipo} de {edad} años")

# Orden correcto
describir_mascota("Firulais", "perro", 5)
# Firulais es un perro de 5 años ✓

# Orden incorrecto
describir_mascota("perro", 5, "Firulais")
# perro es un 5 de Firulais años ✗
```
:::

### Tipo 2: {term}`Argumentos con Nombre <Argumento con nombre>` (Keyword Arguments)

Podés especificar qué argumento va a qué parámetro usando su nombre:

```python
def hacer_pizza(tamaño, ingrediente, extra_queso):
    """Prepara una pizza personalizada."""
    print(f"Pizza {tamaño}")
    print(f"  → Ingrediente principal: {ingrediente}")
    print(f"  → Extra queso: {'Sí' if extra_queso else 'No'}")

# Con keyword arguments, el orden no importa
hacer_pizza(tamaño="grande", ingrediente="pepperoni", extra_queso=True)
hacer_pizza(extra_queso=False, ingrediente="jamón", tamaño="mediana")
hacer_pizza(ingrediente="hongos", tamaño="chica", extra_queso=True)
```

:::{tip} ¿Cuándo Usar Keyword Arguments?
Son especialmente útiles cuando:
- ✓ Hay muchos parámetros.
- ✓ Algunos tienen valores por defecto.
- ✓ Querés que el código sea más legible.

```python
# Difícil de entender
conectar("localhost", 8080, True, False, 30, "utf-8")

# Mucho más claro
conectar(
    host="localhost",
    puerto=8080,
    ssl=True,
    debug=False,
    timeout=30,
    encoding="utf-8"
)
```
:::

### Tipo 3: Mezclar Posicionales y con Nombre

Podés combinar ambos estilos, pero los posicionales **siempre van primero**:

```python
def registrar_usuario(nombre, email, edad, premium=False, notificaciones=True):
    """Registra un nuevo usuario."""
    print(f"Usuario: {nombre}")
    print(f"Email: {email}")
    print(f"Edad: {edad}")
    print(f"Premium: {premium}")
    print(f"Notificaciones: {notificaciones}")

# ✓ Correcto: posicionales primero, luego con nombre
registrar_usuario("Ana", "ana@mail.com", 20, notificaciones=False)

# ✓ También correcto: todos posicionales
registrar_usuario("Bruno", "bruno@mail.com", 22, True, False)

# ✓ También correcto: todos con nombre
registrar_usuario(nombre="Carlos", email="carlos@mail.com", edad=21)
```

:::{error} ❌ Error Común
```python
# ✗ MAL: keyword antes de posicionales
registrar_usuario(nombre="Ana", "ana@mail.com", 20)
# SyntaxError: positional argument follows keyword argument
```
:::

### Ejemplo Práctico: Calculadora

```python
def calcular_rectangulo(base, altura):
    """Calcula área y perímetro de un rectángulo.
    
    Args:
        base: La base del rectángulo
        altura: La altura del rectángulo
    """
    area = base * altura
    perimetro = 2 * (base + altura)
    
    print(f"Rectángulo de {base} × {altura}")
    print(f"   Área: {area} unidades²")
    print(f"   Perímetro: {perimetro} unidades")
    
    return area, perimetro  # Retorna ambos valores

# Usar la función
calcular_rectangulo(5, 3)
calcular_rectangulo(base=10, altura=7)
```

---

(retornar-valores)=
## Retornar Valores con `return`

### print() vs return: ¿Cuál es la Diferencia?

Esta es una de las confusiones más comunes cuando empezás con funciones. ¡Miremos la diferencia!

::::{grid} 1 1 2 2

:::{grid-item-card} print() - Solo Muestra
```python
def sumar_con_print(a, b):
    resultado = a + b
    print(resultado)  # Solo lo muestra

total = sumar_con_print(5, 3)
# Muestra: 8
print(total)
# Muestra: None ← ¡No retorna nada!
```

❌ No podés usar el resultado.  
❌ Solo sirve para ver en pantalla.  
❌ Se pierde el valor.
:::

:::{grid-item-card} return - Devuelve el Valor
```python
def sumar_con_return(a, b):
    resultado = a + b
    return resultado  # Lo devuelve

total = sumar_con_return(5, 3)
# No muestra nada (pero guarda el valor)
print(total)
# Muestra: 8
```

✓ Podés usar el resultado.  
✓ Guardás el valor en una variable.  
✓ Podés hacer operaciones con él.
:::
::::

:::{important} Reglas de funciones y retornos
Según la {ref}`0x0009h`:  
**Las funciones NO deben contener `print()` a menos que ese sea su propósito específico.**

✓ **Hacé**: `return resultado`  
✗ **No hagas**: `print(resultado)`

¿Por qué? Porque `return` te da flexibilidad para usar el resultado como quieras.
:::

### La Palabra Mágica: `return`

`return` hace dos cosas importantes:
1. **Devuelve** un valor al código que llamó a la función.
2. **Termina** la ejecución de la función inmediatamente.

```python
def sumar(a, b):
    """Suma dos números y retorna el resultado."""
    resultado = a + b
    return resultado  # ← Devuelve el valor
    print("Esto nunca se ejecuta")  # ← Código muerto (después del return)

# Usar el valor retornado
total = sumar(5, 3)
print(f"La suma es: {total}")  # La suma es: 8

# También podés usarlo directamente
print(f"El doble es: {sumar(5, 3) * 2}")  # El doble es: 16
```

### Ejemplo Comparativo

Miremos el mismo problema resuelto de dos formas:

```python
# ❌ MAL: Usando print (no es reutilizable)
def calcular_area_mala(base, altura):
    """Calcula el área pero solo la imprime."""
    area = base * altura
    print(f"El área es: {area}")  # Solo muestra, no devuelve

calcular_area_mala(5, 3)
# Muestra: El área es: 15

# Pero no podés hacer esto:
# total = calcular_area_mala(5, 3) + calcular_area_mala(4, 2)
# ← Esto da error porque print no devuelve nada

print("---")

# ✓ BIEN: Usando return (reutilizable)
def calcular_area_buena(base, altura):
    """Calcula y RETORNA el área."""
    area = base * altura
    return area  # Devuelve el valor

area1 = calcular_area_buena(5, 3)
area2 = calcular_area_buena(4, 2)
total = area1 + area2
print(f"Área 1: {area1}")
print(f"Área 2: {area2}")
print(f"Total: {total}")
```

### Return Múltiple: Salidas Tempranas

Podés tener varios `return` en una función. Cuando se ejecuta uno, la función termina:

```python
def clasificar_nota(nota):
    """Clasifica una nota en Aprobado/Desaprobado.
    
    Args:
        nota: Nota numérica del 0 al 10.
        
    Returns:
        Clasificación de la nota.
    """
    # Validación temprana (early return)
    if nota < 0 or nota > 10:
        return "❌ Nota inválida"  # ← Sale aquí si es inválida
    
    # Si llegamos acá, la nota es válida
    if nota >= 6:
        return "✓ Aprobado"  # ← Sale aquí si aprobó
    else:
        return "✗ Desaprobado"  # ← Sale aquí si no aprobó

# Probar diferentes casos
print(clasificar_nota(8))    # ✓ Aprobado
print(clasificar_nota(4))    # ✗ Desaprobado
print(clasificar_nota(11))   # ❌ Nota inválida
```

:::{tip} Early Return (Retorno Temprano)
Según la {ref}`0x0008h`, es un patrón idiomático en Python validar primero y salir temprano:

```python
def dividir_seguro(a, b):
    """Divide dos números de forma segura."""
    # ✓ BIEN: Validar y salir temprano
    if b == 0:
        return None  # o return 0, o lanzar un error
    
    return a / b  # Si llegamos acá, sabemos que b != 0

# ❌ MAL: Anidar todo en un if
def dividir_anidado(a, b):
    """Versión con anidamiento innecesario."""
    if b != 0:
        return a / b
    else:
        return None  # else innecesario
```
:::

### Retornar Múltiples Valores

Python te permite retornar varios valores a la vez usando tuplas:

```python
def analizar_texto(texto):
    """Analiza un texto y retorna varias estadísticas.
    
    Args:
        texto: El texto a analizar.
        
    Returns:
        Una tupla con (cantidad_caracteres, cantidad_palabras, primera_palabra).
    """
    caracteres = len(texto)
    palabras = len(texto.split())
    primera = texto.split()[0] if palabras > 0 else ""
    
    return caracteres, palabras, primera  # ← Retorna 3 valores

# Desempaquetar los valores
texto = "Python es un lenguaje genial"
cant_char, cant_palabras, primera_palabra = analizar_texto(texto)

print(f"Caracteres: {cant_char}")
print(f"Palabras: {cant_palabras}")
print(f"Primera palabra: {primera_palabra}")
```

```python
def calcular_rectangulo(base, altura):
    """Calcula área y perímetro de un rectángulo.
    
    Returns:
        Tupla con (area, perimetro).
    """
    area = base * altura
    perimetro = 2 * (base + altura)
    return area, perimetro

# Forma 1: Desempaquetar
a, p = calcular_rectangulo(5, 3)
print(f"Área: {a}, Perímetro: {p}")

# Forma 2: Como tupla
resultado = calcular_rectangulo(5, 3)
print(f"Resultado: {resultado}")  # (15, 16)
print(f"Área: {resultado[0]}, Perímetro: {resultado[1]}")
```

### Return sin Valor: `None`

Si una función no tiene `return`, o tiene `return` sin valor, automáticamente retorna `None`:

```python
def funcion_sin_return():
    """Esta función no retorna nada explícitamente."""
    x = 10
    y = 20
    # No hay return

resultado1 = funcion_sin_return()
print(f"Resultado 1: {resultado1}")  # None

def funcion_con_return_vacio():
    """Esta función tiene return pero sin valor."""
    print("Haciendo algo...")
    return  # ← Return sin valor

resultado2 = funcion_con_return_vacio()
print(f"Resultado 2: {resultado2}")  # None
```

:::{note} ¿Cuándo Usar `return` sin Valor?
Es útil para **salir temprano** de una función sin retornar nada:

```python
def procesar_usuario(usuario):
    """Procesa un usuario si es válido."""
    if usuario is None:
        print("Usuario inválido")
        return  # ← Sale temprano, no continúa
    
    # Si llegamos acá, el usuario es válido
    print(f"✓ Procesando usuario: {usuario}")
    # ... más código ...

procesar_usuario(None)
procesar_usuario("Ana")
```
:::

### Ejercicio Práctico: Calculadora

```python
def calculadora(operacion, a, b):
    """Calculadora simple que retorna el resultado.
    
    Args:
        operacion: '+', '-', '*', o '/'
        a: Primer número
        b: Segundo número
        
    Returns:
        El resultado de la operación, o None si es inválida
    """
    if operacion == '+':
        return a + b
    elif operacion == '-':
        return a - b
    elif operacion == '*':
        return a * b
    elif operacion == '/':
        if b == 0:
            return None  # División por cero
        return a / b
    else:
        return None  # Operación inválida

# Usar la calculadora
resultado = calculadora('+', 10, 5)
print(f"10 + 5 = {resultado}")

resultado = calculadora('/', 10, 0)
if resultado is None:
    print("Error: No se puede dividir por cero")
else:
    print(f"Resultado: {resultado}")
```

---

(scope-variables)=
## Scope de Variables (Alcance)

### ¿Qué es el Scope?

El {term}`scope` (alcance) es como el "territorio" donde vive una variable. Determina **dónde podés usar** una variable en tu código.

:::{tip} 🏠 Pensalo Como Casas

Imaginate que cada función es una casa:
- Las variables **dentro** de la casa son **privadas** (locales) - solo existen ahí.
- Las variables **fuera** de las casas son **públicas** (globales) - todos pueden verlas.
- Desde adentro de la casa podés ver afuera, pero desde afuera NO podés ver adentro.
:::

```{figure} ./4_funciones/scope.svg
:name: fig-scope
:alt: Scope de variables
:align: center
:width: 90%

Visualización del alcance (scope) de las variables
```

### Variables Locales: Las que Viven Dentro

Las variables creadas **dentro de una función** son **locales** - solo existen dentro de esa función:

```python
def calcular_promedio():
    """Calcula el promedio de tres notas."""
    nota1 = 8  # ← Variable LOCAL
    nota2 = 7  # ← Variable LOCAL
    nota3 = 9  # ← Variable LOCAL
    promedio = (nota1 + nota2 + nota3) / 3  # ← También LOCAL
    return promedio

resultado = calcular_promedio()
print(f"Promedio: {resultado}")  # ✓ Funciona

# print(nota1)  # ❌ Error: NameError: name 'nota1' is not defined
```

:::{important} 📍 Características de Variables Locales
1. **Nacen** cuando se ejecuta la función.
2. **Mueren** cuando la función termina.
3. **No se ven** desde afuera de la función.
4. Cada llamada a la función crea variables nuevas.
:::

```python
def contar():
    """Cada llamada tiene su propia variable local."""
    contador = 0  # ← Nueva variable cada vez
    contador += 1
    print(f"Contador: {contador}")
    return contador

contar()  # Contador: 1
contar()  # Contador: 1 ← Siempre 1, no se acumula
contar()  # Contador: 1
```

### Variables Globales: Las que Todos Ven

Las variables definidas **fuera de todas las funciones** son **globales**:

```python
# Variable global (fuera de funciones)
mensaje = "¡Hola desde el scope global!"
contador_global = 0

def mostrar_mensaje():
    """Puede LEER variables globales."""
    print(mensaje)  # ✓ Puede leer 'mensaje'
    print(f"Contador global: {contador_global}")

mostrar_mensaje()
print(mensaje)  # ✓ También se puede usar acá
```

:::{warning} Leer Sí, Modificar NO
Las funciones pueden **leer** variables globales, pero NO deberían **modificarlas**:

```python
puntos = 100  # Variable global

def sumar_puntos_mal():
    """❌ MAL: Intenta modificar variable global."""
    # puntos = puntos + 10  # ❌ Error: UnboundLocalError
    # Python piensa que 'puntos' es local porque le asignamos

def sumar_puntos_global():
    """❌ FUNCIONA pero es mala práctica."""
    global puntos  # ← Palabra clave para modificar globales
    puntos = puntos + 10

# ✓ MEJOR: Pasarla como parámetro y retornarla
def sumar_puntos_bien(puntos_actuales, puntos_nuevos):
    """✓ BIEN: No toca variables globales."""
    return puntos_actuales + puntos_nuevos

# Uso correcto
puntos = sumar_puntos_bien(puntos, 10)
print(f"Puntos: {puntos}")  # 110
```
:::

Según la {ref}`0x000Bh`, **evitá usar `global`**. En su lugar:
- Pasá los datos como parámetros.
- Retorná los resultados.

### Constantes Globales: La Excepción

Las **constantes** (valores que no cambian) globales **sí son aceptables**. Se escriben en MAYÚSCULAS:

```python
# ✓ Constantes globales (SOLO LECTURA)
PI = 3.14159
GRAVEDAD = 9.81
VELOCIDAD_LUZ = 299792458  # m/s
IVA = 0.21
MAX_INTENTOS = 3

def calcular_area_circulo(radio):
    """Usa la constante PI."""
    return PI * radio **2  # ✓ BIEN: solo la lee

def calcular_precio_con_iva(precio):
    """Usa la constante IVA."""
    return precio * (1 + IVA)  # ✓ BIEN: solo la lee

print(f"Área del círculo: {calcular_area_circulo(5)}")
print(f"Precio con IVA: ${calcular_precio_con_iva(100)}")
```

:::{tip} Reglas para Constantes
- Escribilas en `MAYUSCULAS_CON_GUIONES`.
- Ponelas al principio del archivo.
- NUNCA las modifiques (de ahí el nombre "constantes").
- Está bien leerlas desde funciones.
:::

### Ejemplo Completo: Scope en Acción

```python
# Scope GLOBAL
DESCUENTO_PREMIUM = 0.20  # Constante global
nombre_tienda = "PyShop"  # Variable global (no se recomienda modificar)

def calcular_precio_final(precio_base, es_premium):
    """Calcula el precio final aplicando descuentos si corresponde.
    
    Args:
        precio_base: Precio sin descuento.
        es_premium: Si el cliente es premium.
        
    Returns:
        El precio final con descuento aplicado.
    """
    # Scope local de esta función
    descuento = 0  # Variable local
    precio_final = precio_base  # Variable local
    
    # Puede LEER la constante global DESCUENTO_PREMIUM
    if es_premium:
        descuento = precio_base * DESCUENTO_PREMIUM
        precio_final = precio_base - descuento
    
    # Mostrar cálculo
    print(f"Tienda: {nombre_tienda}")  # ← Lee variable global
    print(f"Precio base: ${precio_base}")
    print(f"Descuento: ${descuento}")
    print(f"Precio final: ${precio_final}")
    
    return precio_final

# Usar la función
total = calcular_precio_final(100, True)

# Variables locales NO existen acá
# print(descuento)  # ❌ Error: NameError
# print(precio_final)  # ❌ Error: NameError
```

### Shadowing: Cuando se Ocultan Variables

Si una variable local tiene el mismo nombre que una global, la local "oculta" a la global:

```python
x = "global"  # Variable global

def funcion_con_shadow():
    """Tiene una variable local con el mismo nombre."""
    x = "local"  # ← Esta x es DIFERENTE a la x global
    print(f"Dentro de la función: {x}")  # local

funcion_con_shadow()
print(f"Fuera de la función: {x}")  # global ← No cambió
```

:::{error} ❌ Error Común: Confundir Scope
```python
total = 0  # Global

def sumar_malo(numero):
    """Intenta modificar variable global sin global."""
    # total = total + numero  # ❌ UnboundLocalError
    # Python ve que le asignamos a 'total', entonces cree que es local
    # Pero al intentar leer 'total + numero', todavía no está definida localmente
    pass

# ✓ Solución: pasarla como parámetro
def sumar_bien(total_actual, numero):
    """Recibe el total como parámetro."""
    return total_actual + numero

total = sumar_bien(total, 5)
print(f"Total: {total}")
```
:::

### Reglas de Oro del Scope

::::{grid} 1 1 2 2

:::{grid-item-card} ✓ HACÉ
- Usar parámetros para pasar datos.
- Retornar resultados.
- Usar constantes globales (MAYÚSCULAS).
- Mantener variables locales.
:::

:::{grid-item-card} ✗ NO HAGAS
- Usar `global` para modificar variables.
- Depender de variables globales mutables.
- Nombres que ocultan variables globales importantes.
- Efectos secundarios en funciones.
:::
::::

```python
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

```python
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

```python
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

(documentacion-funciones)=
## Documentación de Funciones (Docstrings)

Según la {ref}`0x000Ah`, todas las funciones deben tener un {term}`docstring`.

### Formato de Docstrings

```python
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
1. **Resumen de una línea**: Qué hace la función.
2. **Descripción detallada** (opcional): Más contexto si es necesario.
3. **Args**: Lista de parámetros y su descripción.
4. **Returns**: Qué retorna y su tipo.
5. **Raises** (opcional): Excepciones que puede lanzar.
6. **Example** (opcional): Ejemplos de uso.

### Docstring de Una Línea

Para funciones simples:

```python
def es_par(numero):
    """Retorna True si el número es par."""
    return numero % 2 == 0

def cuadrado(x):
    """Retorna el cuadrado de x."""
    return x **2
```

### Acceder a Docstrings

```python
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

```python
def saludar(nombre):
    """Saluda a una persona."""
    return f"¡Hola, {nombre}!"

# Asignar función a variable
mi_funcion = saludar

# Llamar a través de la variable
print(mi_funcion("Ana"))  # ¡Hola, Ana!
```

### Pasar Funciones como Argumentos

```python
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

---

(recursion)=
## Recursión (Tema Opcional)

Una función **recursiva** es una que se llama a sí misma.

### Ejemplo: Factorial

```python
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

Toda función {term}`recursiva <Recursión>` necesita:
1. **Caso base**: Condición de parada.
2. **Caso recursivo**: Llamada a sí misma con problema más pequeño.

```python
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

```python
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

```python
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

```python
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

```python
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

```python
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

```python
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

```python
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

```python
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

```python
# ❌ Cantidad incorrecta de argumentos
def saludar(nombre, edad):
    print(f"Hola {nombre}, tienes {edad} años")

try:
    saludar("Ana")
except TypeError as e:
    print(f"Error: {e}")

# ✓ Argumentos correctos
saludar("Ana", 20)
```

### 3. Modificar Argumentos Mutables

```python
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

```python
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

### 5. Valor por Defecto Mutable

```python
# ❌ PELIGRO: Lista mutable como default
def agregar_tarea(tarea, lista=[]):
    """¡Lista compartida entre llamadas!"""
    lista.append(tarea)
    return lista

# Comportamiento inesperado
print(agregar_tarea("Estudiar"))     # ['Estudiar']
print(agregar_tarea("Ejercitar"))   # ['Estudiar', 'Ejercitar'] ¡Acumula!
print(agregar_tarea("Descansar"))   # ['Estudiar', 'Ejercitar', 'Descansar']

# ✓ CORRECTO: Usar None como default
def agregar_tarea(tarea, lista=None):
    """Crea nueva lista si no se proporciona una."""
    if lista is None:
        lista = []
    lista.append(tarea)
    return lista

# Comportamiento esperado
print(agregar_tarea("Estudiar"))     # ['Estudiar']
print(agregar_tarea("Ejercitar"))   # ['Ejercitar'] ✓
print(agregar_tarea("Descansar"))   # ['Descansar'] ✓
```

:::{danger} 🚨 Error Sutil pero Crítico
Los valores por defecto se evalúan **UNA SOLA VEZ** cuando se define la función. Si usás una lista o diccionario como default, ¡será compartido entre todas las llamadas!
:::

### 6. No Usar Parámetros con Nombre

```python
# ❌ Difícil de entender
def crear_cuenta(activa, tipo, creditos, notificaciones):
    pass

# ✓ Claro y explícito
def crear_cuenta(activa=True, tipo="premium", creditos=100, notificaciones=False):
    pass

crear_cuenta(
    activa=True,
    tipo="premium",
    creditos=100,
    notificaciones=False
)
```

---

(descomposicion-funcional)=
## {term}`Descomposición Funcional`: Dividir para Conquistar

:::{tip} ¿Qué es la Descomposición Funcional?

La **descomposición funcional** es el proceso de dividir un problema complejo en subproblemas más pequeños y manejables, donde cada subproblema se resuelve con una función específica.

Es como desarmar un motor complejo en sus piezas individuales: pistones, bielas, válvulas... cada una con una función clara y específica.
:::

### ¿Por qué Descomponer?

Imaginate que tenés que escribir un programa de gestión de biblioteca. Si intentás escribir todo en una sola función gigante, terminás con algo así:

```python
# ❌ Código monolítico (todo junto)
def sistema_biblioteca():
    """Función gigante que hace TODO."""
    # 300 líneas de código mezclando:
    # - Validar usuarios
    # - Buscar libros
    # - Registrar préstamos
    # - Calcular multas
    # - Generar reportes
    # ... ¡imposible de mantener!
```

**Problemas de este enfoque:**
- 🐛 **Difícil de debuggear**: Si hay un error, ¿dónde está?
- 🔍 **Difícil de entender**: ¿Qué hace exactamente?
- ♻️ **No se puede reutilizar**: Todo está mezclado.
- 🧪 **No se puede testear**: No se puede probar cada parte.
- 👥 **Difícil trabajar en equipo**: Todos tocan el mismo código.

### Principios de Descomposición

#### 1. Principio de Responsabilidad Única (SRP)

Cada función debe hacer **una sola cosa**, y hacerla bien.

```python
# ❌ Hace demasiadas cosas
def procesar_pedido(cliente, items):
    # Valida cliente
    # Valida stock
    # Calcula precio
    # Aplica descuentos
    # Genera factura
    # Envía email
    # Actualiza inventario
    pass

# ✓ Cada función una responsabilidad
def validar_cliente(cliente):
    """Solo valida datos del cliente."""
    pass

def verificar_stock(items):
    """Solo verifica disponibilidad."""
    pass

def calcular_total(items, descuento=0):
    """Solo calcula el precio total."""
    pass

def generar_factura(pedido):
    """Solo genera el documento."""
    pass

def enviar_email(cliente, factura):
    """Solo envía el email."""
    pass

def actualizar_inventario(items):
    """Solo actualiza el stock."""
    pass
```

#### 2. Abstracción: Esconder la Complejidad

Las funciones te permiten **usar** algo sin necesitar saber **cómo** funciona internamente.

```python
# Función de alto nivel (abstracción)
def procesar_pedido(cliente, items):
    """Orquesta todas las operaciones."""
    validar_cliente(cliente)
    verificar_stock(items)
    total = calcular_total(items)
    factura = generar_factura(cliente, items, total)
    enviar_email(cliente, factura)
    actualizar_inventario(items)
    return factura

# ¡Fácil de leer y entender el flujo general!
```

#### 3. DRY (Don't Repeat Yourself)

Si hacés algo más de una vez, probablemente debería ser una función.

```python
# ❌ Código repetitivo
edad1 = 2024 - 1998
edad2 = 2024 - 2005
edad3 = 2024 - 1990

# ✓ Función reutilizable
def calcular_edad(año_nacimiento):
    """Calcula edad a partir del año de nacimiento."""
    return 2024 - año_nacimiento

edad1 = calcular_edad(1998)
edad2 = calcular_edad(2005)
edad3 = calcular_edad(1990)
```

### Proceso de Descomposición: Paso a Paso

Vamos a descomponer un problema real paso a paso.

#### Problema: Sistema de Cálculo de Notas

**Requerimientos:**
- Pedir notas de 3 parciales.
- Calcular promedio.
- Determinar si aprobó (≥6).
- Mostrar mensaje según resultado.
- Calcular nota necesaria en recuperatorio.

#### Paso 1: Identificar las Tareas Principales

Leé el problema y subrayá los **verbos de acción**:
- **Pedir** notas.
- **Calcular** promedio.
- **Determinar** si aprobó.
- **Mostrar** mensaje.
- **Calcular** nota necesaria.

Cada verbo es potencialmente una función.

#### Paso 2: Diseñar la Estructura

```python
# Estructura de alto nivel (pseudocódigo)
def main():
    notas = pedir_notas()
    promedio = calcular_promedio(notas)
    aprobado = verificar_aprobacion(promedio)
    mostrar_resultado(promedio, aprobado)
    
    if not aprobado:
        nota_necesaria = calcular_nota_recuperatorio(promedio)
        print(f"Necesitás {nota_necesaria} en el recuperatorio")
```

#### Paso 3: Implementar Cada Función

```python
def pedir_notas():
    """Solicita las 3 notas al usuario.
    
    Returns:
        list: Lista con las 3 notas ingresadas.
    """
    notas = []
    for i in range(1, 4):
        while True:
            try:
                nota = float(input(f"Ingresá la nota del parcial {i} (0-10): "))
                if 0 <= nota <= 10:
                    notas.append(nota)
                    break
                else:
                    print("La nota debe estar entre 0 y 10")
            except ValueError:
                print("Ingresá un número válido")
    return notas


def calcular_promedio(notas):
    """Calcula el promedio de una lista de notas.
    
    Args:
        notas: Lista de notas numéricas.
    
    Returns:
        float: El promedio de las notas.
    """
    return sum(notas) / len(notas)


def verificar_aprobacion(promedio, nota_minima=6):
    """Verifica si un promedio es aprobado.
    
    Args:
        promedio: El promedio a verificar.
        nota_minima: Nota mínima para aprobar (default: 6).
    
    Returns:
        bool: True si aprobó, False si no.
    """
    return promedio >= nota_minima


def mostrar_resultado(promedio, aprobado):
    """Muestra el resultado de la evaluación.
    
    Args:
        promedio: El promedio obtenido.
        aprobado: Si el estudiante aprobó o no.
    """
    print(f"\n{'='*40}")
    print(f"Promedio: {promedio:.2f}")
    
    if aprobado:
        print("Estado: ✅ APROBADO")
        if promedio >= 8:
            print("¡Excelente trabajo!")
        else:
            print("Buen trabajo.")
    else:
        print("Estado: ❌ DESAPROBADO")
    print(f"{'='*40}\n")


def calcular_nota_recuperatorio(promedio_actual, nota_minima=6, peso_parciales=0.6, peso_recup=0.4):
    """Calcula qué nota se necesita en el recuperatorio para aprobar.
    
    Args:
        promedio_actual: Promedio actual de parciales.
        nota_minima: Nota mínima para aprobar.
        peso_parciales: Peso de los parciales en la nota final.
        peso_recup: Peso del recuperatorio en la nota final.
    
    Returns:
        float: Nota necesaria en el recuperatorio.
    """
    # Formula: promedio_actual * 0.6 + nota_recup * 0.4 = nota_minima
    nota_necesaria = (nota_minima - (promedio_actual * peso_parciales)) / peso_recup
    return max(0, min(10, nota_necesaria))  # Entre 0 y 10


def main():
    """Función principal que orquesta el programa."""
    print("Sistema de Cálculo de Notas")
    print("="*40)
    
    notas = pedir_notas()
    promedio = calcular_promedio(notas)
    aprobado = verificar_aprobacion(promedio)
    mostrar_resultado(promedio, aprobado)
    
    if not aprobado:
        nota_recup = calcular_nota_recuperatorio(promedio)
        if nota_recup <= 10:
            print(f"Nota necesaria en recuperatorio: {nota_recup:.2f}")
        else:
            print("Lamentablemente, ya no es posible aprobar con el recuperatorio.")


# Ejecutar el programa
if __name__ == "__main__":
    main()
```

#### Paso 4: Analizar los Beneficios

Comparemos:

::::{grid} 1 1 2 2

:::{grid-item-card} ❌ Sin Descomposición
```python
# Todo en una función
def sistema_notas():
    # 80 líneas mezcladas
    # Difícil de leer
    # Imposible de testear
    # No reutilizable
    pass
```

**Problemas:**
- No se puede reutilizar `calcular_promedio`.
- No se puede testear `verificar_aprobacion` aisladamente.
- Cambiar la lógica de input rompe todo.
:::

:::{grid-item-card} ✅ Con Descomposición
```python
# Funciones separadas
pedir_notas()
calcular_promedio()
verificar_aprobacion()
mostrar_resultado()
calcular_nota_recuperatorio()
main()
```

**Ventajas:**
- ✅ Cada función se puede testear sola.
- ✅ `calcular_promedio` se reutiliza en otros programas.
- ✅ Cambiar input no afecta cálculos.
- ✅ Fácil de entender y mantener.
:::

::::

### Niveles de Descomposición

La descomposición suele tener varios niveles de abstracción:

```{figure} 4_funciones/niveles_descomposicion.svg
:label: fig-niveles-descomposicion
:align: center
:width: 100%

Niveles de descomposición: desde la función principal hasta las funciones auxiliares
```

```python
# NIVEL 1: Función de máximo nivel (orquestación)
def procesar_ventas_mensuales():
    """Función principal que coordina todo el proceso."""
    ventas = cargar_ventas()
    reporte = generar_reporte(ventas)
    guardar_reporte(reporte)

# NIVEL 2: Funciones de nivel medio (operaciones principales)
def generar_reporte(ventas):
    """Genera reporte de ventas."""
    resumen = calcular_resumen(ventas)
    grafico = crear_grafico(ventas)
    return formatear_reporte(resumen, grafico)

# NIVEL 3: Funciones de bajo nivel (operaciones básicas)
def calcular_resumen(ventas):
    """Calcula estadísticas de ventas."""
    total = calcular_total(ventas)
    promedio = calcular_promedio(ventas)
    maximo = encontrar_maximo(ventas)
    return {"total": total, "promedio": promedio, "max": maximo}

# NIVEL 4: Funciones auxiliares (operaciones atómicas)
def calcular_total(valores):
    """Suma todos los valores."""
    return sum(valores)
```

**Principio:** Las funciones de nivel superior **usan** las de nivel inferior, creando una jerarquía clara.

### Caso de Estudio 1: Validador de Contraseñas

Vamos a descomponer un programa que valida contraseñas.

**Requerimientos:**
- Longitud mínima de 8 caracteres.
- Al menos una mayúscula.
- Al menos una minúscula.
- Al menos un número.
- Al menos un carácter especial.
- Dar feedback específico de qué falta.

#### Solución Sin Descomponer (Monolítica)

```python
# ❌ Todo en una función
def validar_password(password):
    """Valida una contraseña según criterios."""
    if len(password) < 8:
        return False, "Muy corta"
    
    tiene_mayuscula = False
    tiene_minuscula = False
    tiene_numero = False
    tiene_especial = False
    
    for char in password:
        if char.isupper():
            tiene_mayuscula = True
        elif char.islower():
            tiene_minuscula = True
        elif char.isdigit():
            tiene_numero = True
        elif char in "!@#$%^&*()_+-=[]{}|;:,.<>?":
            tiene_especial = True
    
    errores = []
    if not tiene_mayuscula:
        errores.append("Falta mayúscula")
    if not tiene_minuscula:
        errores.append("Falta minúscula")
    if not tiene_numero:
        errores.append("Falta número")
    if not tiene_especial:
        errores.append("Falta carácter especial")
    
    if errores:
        return False, ", ".join(errores)
    return True, "Contraseña válida"

# Difícil de entender, modificar y testear
```

#### Solución Descompuesta (Modular)

```python
# ✅ Descompuesto en funciones especializadas

def tiene_longitud_minima(password, minimo=8):
    """Verifica si la contraseña tiene la longitud mínima.
    
    Args:
        password: Contraseña a validar.
        minimo: Longitud mínima requerida.
    
    Returns:
        bool: True si cumple, False si no.
    """
    return len(password) >= minimo


def tiene_mayuscula(password):
    """Verifica si la contraseña tiene al menos una mayúscula.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        bool: True si tiene mayúscula, False si no.
    """
    return any(char.isupper() for char in password)


def tiene_minuscula(password):
    """Verifica si la contraseña tiene al menos una minúscula.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        bool: True si tiene minúscula, False si no.
    """
    return any(char.islower() for char in password)


def tiene_numero(password):
    """Verifica si la contraseña tiene al menos un número.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        bool: True si tiene número, False si no.
    """
    return any(char.isdigit() for char in password)


def tiene_caracter_especial(password):
    """Verifica si la contraseña tiene al menos un carácter especial.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        bool: True si tiene carácter especial, False si no.
    """
    caracteres_especiales = "!@#$%^&*()_+-=[]{}|;:,.<>?"
    return any(char in caracteres_especiales for char in password)


def obtener_errores_validacion(password):
    """Obtiene lista de errores de validación.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        list: Lista de mensajes de error.
    """
    errores = []
    
    if not tiene_longitud_minima(password):
        errores.append("Debe tener al menos 8 caracteres")
    if not tiene_mayuscula(password):
        errores.append("Debe tener al menos una mayúscula")
    if not tiene_minuscula(password):
        errores.append("Debe tener al menos una minúscula")
    if not tiene_numero(password):
        errores.append("Debe tener al menos un número")
    if not tiene_caracter_especial(password):
        errores.append("Debe tener al menos un carácter especial")
    
    return errores


def validar_password(password):
    """Valida una contraseña según todos los criterios.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        tuple: (es_valida, mensaje)
    """
    errores = obtener_errores_validacion(password)
    
    if errores:
        return False, " | ".join(errores)
    return True, "✅ Contraseña válida"


def solicitar_password():
    """Solicita contraseña al usuario hasta que sea válida.
    
    Returns:
        str: Contraseña válida ingresada.
    """
    while True:
        password = input("Ingresá una contraseña: ")
        valida, mensaje = validar_password(password)
        
        print(mensaje)
        
        if valida:
            return password
        print("Intentá de nuevo.\n")


def main():
    """Función principal del programa."""
    print("=== Creación de Contraseña Segura ===\n")
    print("Requisitos:")
    print("  • Mínimo 8 caracteres")
    print("  • Al menos una mayúscula")
    print("  • Al menos una minúscula")
    print("  • Al menos un número")
    print("  • Al menos un carácter especial (!@#$...)\n")
    
    password = solicitar_password()
    print(f"\n✅ Contraseña creada exitosamente!")


if __name__ == "__main__":
    main()
```

**Ventajas de esta descomposición:**

1. **Testeable:** Cada función se puede testear individualmente
   ```python
   assert tiene_mayuscula("Hola123!") == True
   assert tiene_numero("Hola!") == False
   ```

2. **Reutilizable:** Podés usar `tiene_numero()` en otros contextos
   ```python
   if tiene_numero(codigo_postal):
       print("El código postal contiene números")
   ```

3. **Modificable:** Cambiar un requisito es fácil
   ```python
   # Solo modificar una función
   def tiene_longitud_minima(password, minimo=12):  # Cambio aquí
       return len(password) >= minimo
   ```

4. **Legible:** El código se lee como una historia
   ```python
   # Se lee naturalmente:
   if not tiene_mayuscula(password):
       errores.append("Falta mayúscula")
   ```

### Caso de Estudio 2: Calculadora de IMC Completa

Vamos a construir una calculadora de Índice de Masa Corporal (IMC) profesional.

**Requerimientos:**
- Pedir peso y altura
- Validar que sean valores positivos
- Calcular IMC
- Clasificar según estándares OMS
- Mostrar reporte formateado
- Dar recomendación personalizada

#### Análisis y Descomposición

```python
# PASO 1: Identificar responsabilidades
# - Obtener datos (input)
# - Validar datos (validación)
# - Calcular IMC (cálculo)
# - Clasificar IMC (clasificación)
# - Generar recomendación (lógica de negocio)
# - Mostrar resultado (output)

# PASO 2: Diseñar funciones

def solicitar_numero_positivo(mensaje, nombre_campo):
    """Solicita un número positivo al usuario con validación.
    
    Args:
        mensaje: Mensaje a mostrar al usuario.
        nombre_campo: Nombre del campo para mensajes de error.
    
    Returns:
        float: Número positivo ingresado.
    """
    while True:
        try:
            valor = float(input(mensaje))
            if valor <= 0:
                print(f"❌ {nombre_campo} debe ser positivo")
                continue
            return valor
        except ValueError:
            print(f"❌ Ingresá un número válido para {nombre_campo}")


def calcular_imc(peso, altura):
    """Calcula el Índice de Masa Corporal.
    
    Args:
        peso: Peso en kilogramos.
        altura: Altura en metros.
    
    Returns:
        float: IMC calculado.
    
    Formula:
        IMC = peso / (altura^2)
    """
    return peso / (altura ** 2)


def clasificar_imc(imc):
    """Clasifica el IMC según estándares de la OMS.
    
    Args:
        imc: Índice de masa corporal.
    
    Returns:
        str: Clasificación del IMC.
    """
    if imc < 18.5:
        return "Bajo peso"
    elif imc < 25:
        return "Peso normal"
    elif imc < 30:
        return "Sobrepeso"
    elif imc < 35:
        return "Obesidad I"
    elif imc < 40:
        return "Obesidad II"
    else:
        return "Obesidad III"


def obtener_emoji_clasificacion(clasificacion):
    """Obtiene emoji según la clasificación.
    
    Args:
        clasificacion: Clasificación del IMC.
    
    Returns:
        str: Emoji representativo.
    """
    emojis = {
        "Bajo peso": "⚠️",
        "Peso normal": "✅",
        "Sobrepeso": "⚠️",
        "Obesidad I": "❌",
        "Obesidad II": "❌",
        "Obesidad III": "🚨"
    }
    return emojis.get(clasificacion, "")


def generar_recomendacion(clasificacion):
    """Genera recomendación personalizada según clasificación.
    
    Args:
        clasificacion: Clasificación del IMC.
    
    Returns:
        str: Recomendación personalizada.
    """
    recomendaciones = {
        "Bajo peso": "Considerá consultar a un nutricionista para aumentar tu masa muscular de forma saludable.",
        "Peso normal": "¡Excelente! Mantené tus hábitos saludables de alimentación y ejercicio.",
        "Sobrepeso": "Considerá incorporar más actividad física y mejorar tu alimentación.",
        "Obesidad I": "Te recomendamos consultar a un profesional de la salud para un plan personalizado.",
        "Obesidad II": "Es importante que consultes con un médico para evaluación y tratamiento.",
        "Obesidad III": "Te recomendamos urgente consulta médica para prevenir complicaciones."
    }
    return recomendaciones.get(clasificacion, "Consultá con un profesional de la salud.")


def calcular_peso_ideal(altura):
    """Calcula rango de peso ideal para una altura.
    
    Args:
        altura: Altura en metros.
    
    Returns:
        tuple: (peso_minimo, peso_maximo) para IMC normal (18.5-25).
    """
    peso_minimo = 18.5 * (altura ** 2)
    peso_maximo = 25 * (altura ** 2)
    return peso_minimo, peso_maximo


def mostrar_reporte(peso, altura, imc, clasificacion):
    """Muestra reporte completo formateado.
    
    Args:
        peso: Peso en kg.
        altura: Altura en m.
        imc: IMC calculado.
        clasificacion: Clasificación del IMC.
    """
    emoji = obtener_emoji_clasificacion(clasificacion)
    recomendacion = generar_recomendacion(clasificacion)
    peso_min, peso_max = calcular_peso_ideal(altura)
    
    print("\n" + "="*50)
    print("         REPORTE DE ÍNDICE DE MASA CORPORAL")
    print("="*50)
    print(f"\n📊 Datos ingresados:")
    print(f"   • Peso: {peso:.1f} kg")
    print(f"   • Altura: {altura:.2f} m")
    print(f"\n📈 Resultados:")
    print(f"   • IMC: {imc:.2f}")
    print(f"   • Clasificación: {emoji} {clasificacion}")
    print(f"\n💡 Recomendación:")
    print(f"   {recomendacion}")
    print(f"\n🎯 Rango de peso saludable para tu altura:")
    print(f"   {peso_min:.1f} kg - {peso_max:.1f} kg")
    print("="*50)


def ejecutar_calculadora_imc():
    """Función principal que ejecuta la calculadora de IMC."""
    print("╔" + "="*48 + "╗")
    print("║     CALCULADORA DE ÍNDICE DE MASA CORPORAL    ║")
    print("╚" + "="*48 + "╝\n")
    
    # Obtener datos
    peso = solicitar_numero_positivo("Ingresá tu peso (kg): ", "peso")
    altura = solicitar_numero_positivo("Ingresá tu altura (m): ", "altura")
    
    # Procesar
    imc = calcular_imc(peso, altura)
    clasificacion = clasificar_imc(imc)
    
    # Mostrar resultado
    mostrar_reporte(peso, altura, imc, clasificacion)


def main():
    """Función principal con manejo de reinicio."""
    while True:
        ejecutar_calculadora_imc()
        
        respuesta = input("\n¿Calcular otro IMC? (s/n): ").lower()
        if respuesta != 's':
            print("\n¡Hasta luego! Cuidá tu salud. 💪")
            break
        print("\n")


if __name__ == "__main__":
    main()
```

**Análisis de la Descomposición:**

| Función | Responsabilidad | Nivel | Reutilizable |
|---------|----------------|-------|--------------|
| `solicitar_numero_positivo` | Input validado | Bajo | ✅ Muy |
| `calcular_imc` | Cálculo puro | Bajo | ✅ Muy |
| `clasificar_imc` | Lógica de negocio | Medio | ✅ Sí |
| `obtener_emoji_clasificacion` | Presentación | Bajo | ✅ Sí |
| `generar_recomendacion` | Lógica de negocio | Medio | ✅ Sí |
| `calcular_peso_ideal` | Cálculo derivado | Medio | ✅ Sí |
| `mostrar_reporte` | Output formateado | Medio | ⚠️ Parcial |
| `ejecutar_calculadora_imc` | Orquestación | Alto | ❌ No |
| `main` | Control flujo | Muy Alto | ❌ No |

### Estrategias de Descomposición

#### 1. Top-Down (De Arriba hacia Abajo)

Empezás con la función principal y vas detallando:

```python
# 1. Definir qué hace el programa en alto nivel
def procesar_ventas():
    datos = cargar_datos()
    resultados = analizar_datos(datos)
    guardar_resultados(resultados)

# 2. Detallar cada función de nivel medio
def analizar_datos(datos):
    limpios = limpiar_datos(datos)
    estadisticas = calcular_estadisticas(limpios)
    return generar_reporte(estadisticas)

# 3. Implementar funciones específicas
def limpiar_datos(datos):
    # Implementación detallada
    pass
```

**Ventaja:** Ves el panorama completo primero.

#### 2. Bottom-Up (De Abajo hacia Arriba)

Empezás con las funciones más básicas y construís hacia arriba:

```python
# 1. Funciones básicas primero
def es_numero_valido(texto):
    return texto.isdigit()

def convertir_a_numero(texto):
    return int(texto)

# 2. Combinar en funciones de nivel medio
def obtener_numero_valido(mensaje):
    while True:
        entrada = input(mensaje)
        if es_numero_valido(entrada):
            return convertir_a_numero(entrada)
        print("Error: no es un número válido")

# 3. Función de alto nivel
def main():
    edad = obtener_numero_valido("Ingresá tu edad: ")
    # ...
```

**Ventaja:** Cada pieza está testeada antes de combinarla.

#### 3. Por Responsabilidad

Agrupá funciones según su tipo de responsabilidad:

```python
# === VALIDACIÓN ===
def validar_email(email):
    pass

def validar_telefono(telefono):
    pass

# === CÁLCULO ===
def calcular_descuento(precio, porcentaje):
    pass

def calcular_impuestos(monto):
    pass

# === FORMATO ===
def formatear_fecha(fecha):
    pass

def formatear_moneda(monto):
    pass

# === PERSISTENCIA ===
def guardar_en_archivo(datos, archivo):
    pass

def cargar_desde_archivo(archivo):
    pass
```

### Indicadores de que Necesitás Descomponer

:::{danger} Señales de Alerta 🚨

Tu función probablemente necesita descomponerse si:

1. **Tiene más de 20-30 líneas** (regla general)
2. **Usa la palabra "y" al describir qué hace**
   - "Valida datos *y* calcula resultado *y* muestra output"
3. **Tiene más de 3 niveles de indentación**
   ```python
   def funcion():
       if condicion1:
           for item in lista:
               if condicion2:
                   while algo:  # ¡4 niveles!
   ```
4. **Es difícil ponerle nombre** (hace demasiado)
5. **Necesitás scrollear para ver toda**
6. **Tiene muchas variables locales** (>7)
7. **Tiene secciones separadas por comentarios**
   ```python
   def funcion():
       # Validar entrada
       # ... 10 líneas ...
       
       # Procesar datos
       # ... 10 líneas ...
       
       # Generar output
       # ... 10 líneas ...
       # ¡Cada sección debería ser una función!
   ```
:::

### Ejercicios de Descomposición

#### Ejercicio 1: Análisis de Código

Dado este código monolítico, identificá qué funciones crearías:

```python
def procesar():
    # Pedir nombre
    nombre = input("Nombre: ")
    while len(nombre) < 2:
        print("Muy corto")
        nombre = input("Nombre: ")
    
    # Pedir edad
    edad = input("Edad: ")
    while not edad.isdigit():
        print("Debe ser número")
        edad = input("Edad: ")
    edad = int(edad)
    
    # Calcular categoría
    if edad < 18:
        categoria = "Menor"
        descuento = 0.2
    elif edad < 65:
        categoria = "Adulto"
        descuento = 0
    else:
        categoria = "Senior"
        descuento = 0.3
    
    # Calcular precio
    precio_base = 100
    precio_final = precio_base * (1 - descuento)
    
    # Mostrar resultado
    print(f"Hola {nombre}")
    print(f"Categoría: {categoria}")
    print(f"Precio: ${precio_final}")

# ¿Qué funciones crearías? Lista al menos 5.
```

<details>
<summary>💡 Ver Solución</summary>

```python
def solicitar_nombre():
    """Solicita y valida el nombre."""
    pass

def solicitar_edad():
    """Solicita y valida la edad."""
    pass

def determinar_categoria(edad):
    """Determina categoría según edad."""
    pass

def calcular_descuento(categoria):
    """Calcula descuento según categoría."""
    pass

def calcular_precio_final(precio_base, descuento):
    """Calcula precio final aplicando descuento."""
    pass

def mostrar_resumen(nombre, categoria, precio):
    """Muestra resumen de la compra."""
    pass

def main():
    """Función principal."""
    nombre = solicitar_nombre()
    edad = solicitar_edad()
    categoria = determinar_categoria(edad)
    descuento = calcular_descuento(categoria)
    precio = calcular_precio_final(100, descuento)
    mostrar_resumen(nombre, categoria, precio)
```
</details>

#### Ejercicio 2: Sistema de Gestión de Tareas

**Problema:** Diseñá la descomposición funcional para un sistema de gestión de tareas que debe:
- Agregar tareas nuevas
- Marcar tareas como completadas
- Listar tareas pendientes
- Listar tareas completadas
- Eliminar tareas
- Buscar tareas por palabra clave
- Guardar y cargar desde archivo

**Tu tarea:** Antes de escribir código, diseñá:
1. Lista de funciones necesarias
2. Qué parámetros recibe cada una
3. Qué retorna cada una
4. Cómo se relacionan entre sí

<details>
<summary>💡 Ver Diseño Sugerido</summary>

```python
# === OPERACIONES BÁSICAS (CRUD) ===
def agregar_tarea(tareas, descripcion, prioridad="normal"):
    """Agrega nueva tarea a la lista."""
    pass

def marcar_completada(tareas, indice):
    """Marca una tarea como completada."""
    pass

def eliminar_tarea(tareas, indice):
    """Elimina una tarea de la lista."""
    pass

# === CONSULTAS ===
def obtener_pendientes(tareas):
    """Retorna lista de tareas pendientes."""
    pass

def obtener_completadas(tareas):
    """Retorna lista de tareas completadas."""
    pass

def buscar_tareas(tareas, palabra_clave):
    """Busca tareas que contengan la palabra clave."""
    pass

# === PERSISTENCIA ===
def guardar_tareas(tareas, archivo="tareas.txt"):
    """Guarda tareas en archivo."""
    pass

def cargar_tareas(archivo="tareas.txt"):
    """Carga tareas desde archivo."""
    pass

# === INTERFAZ ===
def mostrar_menu():
    """Muestra menú de opciones."""
    pass

def obtener_opcion():
    """Obtiene opción válida del usuario."""
    pass

def mostrar_tareas(tareas, titulo="Tareas"):
    """Muestra lista de tareas formateada."""
    pass

# === ORQUESTACIÓN ===
def main():
    """Función principal."""
    pass
```
</details>

### Checklist de Descomposición

Antes de considerar que tu descomposición está completa, verificá:

- [ ] **Cada función tiene un nombre descriptivo** que dice qué hace
- [ ] **Cada función hace una sola cosa bien** (SRP)
- [ ] **Funciones no tienen más de 20-30 líneas**
- [ ] **No hay código duplicado** (DRY)
- [ ] **Cada función tiene docstring** explicando qué hace
- [ ] **Parámetros son descriptivos** y mínimos necesarios
- [ ] **Return es claro:** sabes qué retorna cada función
- [ ] **Funciones son testeables** independientemente
- [ ] **No hay efectos secundarios** inesperados
- [ ] **Niveles de abstracción** están claros (alto/medio/bajo)

### Recursos Adicionales

Para profundizar en descomposición funcional:

- **Libro:** "Clean Code" de Robert C. Martin (Capítulos 3-4)
- **Artículo:** [Function Design Principles](https://www.python.org/dev/peps/pep-0020/) (Zen of Python)
- **Video:** [Writing Clean Functions](https://www.youtube.com/watch?v=7EmboKQH8lM)

---

(resumen-funciones)=
##  Resumen del Capítulo

```{figure} ./4_funciones/resumen_funciones.svg
:name: fig-resumen-funciones
:align: center
:width: 90%

Mapa conceptual completo del capítulo de funciones
```

### Conceptos Clave

::::{grid} 1 1 2 2

:::{grid-item-card} Definición
**Sintaxis básica:**
```python
def nombre_funcion(parametros):
    """Docstring"""
    # código
    return resultado
```
:::

:::{grid-item-card} 📥 Parámetros
- Posicionales
- Con nombre (keyword)
- Por defecto
:::

:::{grid-item-card} `return`
- Retorna valores
- Termina ejecución
- Puede retornar múltiples valores (tupla)
- Sin `return` → `None`
:::

:::{grid-item-card} Documentación
- Docstrings obligatorios
- Formato estándar
- Describe Args y Returns
- Incluye ejemplos
:::

:::{grid-item-card} Scope
- Variables locales vs globales
- LEGB: Local, Enclosing, Global, Built-in
- Evitar {term}`global`
- Usar parámetros y `return`s
:::

:::{grid-item-card} {term}`funciones lambda <Función lambda>`
- Funciones anónimas
- Una sola expresión
- Útiles con map/filter
- No reemplazan funciones normales
:::
::::

### Checklist de Buenas Prácticas

```{tip} ✅ Funciones de Calidad

- [ ] **Nombre descriptivo** que indica qué hace
- [ ] **Una sola responsabilidad**(principio SRP)
- [ ] **Docstring completo**con Args y Returns
- [ ] **Retorna valor**, no imprime (separar lógica de presentación)
- [ ] **Parámetros claros**y no demasiados (máx 3-4)
- [ ] **No modifica**argumentos mutables
- [ ] **Evita variables globales**, usa parámetros
- [ ] **Maneja casos borde**(lista vacía, None, etc.)
- [ ] **Testeable**y fácil de probar
- [ ] **Tamaño razonable**(~20-30 líneas máximo)
```

### Errores a Evitar

::::{grid} 1 1 2 3

:::{grid-item-card} ❌ Olvidar Return
```python
def sumar(a, b):
    a + b  # Falta return!
```
:::

:::{grid-item-card} ❌ Default Mutable
```python
def func(lista=[]):  # ¡Peligro!
    lista.append(1)
```
:::

:::{grid-item-card} ❌ Usar global
```python
def func():
    global x  # Evitar
    x = 10
```
:::

:::{grid-item-card} ❌ Sin Docstring
```python
def calc(x, y, z):  # ¿Qué hace?
    return x * y + z
```
:::

:::{grid-item-card} ❌ Modificar Argumentos
```python
def func(lista):
    lista.append(1)  # Side effect
```
:::

:::{grid-item-card} ❌ Muchos Parámetros
```python
def func(a, b, c, d, e, f):
    # Demasiados!
```
:::
::::

### Tabla de Referencia Rápida

| Concepto | Sintaxis | Ejemplo |
|----------|----------|---------|
| Función básica | `def nombre(params): return valor` | `def suma(a, b): return a + b` |
| Parámetro default | `def func(param=valor):` | `def saludar(nombre="Mundo"):` |
| Args variables | `def func(*args):` | `def sumar(*nums): return sum(nums)` |
| Docstring | `"""descripcion"""` | `"""Suma dos números."""` |
| Scope local | Variable dentro de función | `def f(): x = 1` |
| Scope global | Variable fuera de funciones | `X = 1` (constante) |

### Para Seguir Practicando

```{tip} Próximos Pasos

1. **Practicar**con los ejercicios propuestos
2. **Refactorizar**código existente en funciones
3. **Leer**código de proyectos open source
4. **Escribir**funciones para problemas reales
5. **Revisar**PEP 8 para estilo de funciones
```

---

(referencias-funciones)=
## Referencias y Recursos

### Documentación Oficial

- [Python Functions Tutorial](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
- [PEP 8 - Style Guide](https://www.python.org/dev/peps/pep-0008/)
- [PEP 257 - Docstring Conventions](https://www.python.org/dev/peps/pep-0257/)

### Recursos Adicionales

- [Real Python - Defining Your Own Python Function](https://realpython.com/defining-your-own-python-function/)
- [Clean Code by Robert C. Martin](https://www.oreilly.com/library/view/clean-code/9780136083238/) - Capítulo sobre funciones

### Herramientas

- **pylint**: Linter para verificar estilo
- **black**: Formateador automático
- **pydocstyle**: Verifica docstrings

---

:::{success} ¡Felicitaciones!

Completaste el capítulo de **Funciones**. Ahora sabés:

✅ Crear funciones con diferentes tipos de parámetros  
✅ Documentar funciones profesionalmente  
✅ Entender y aplicar scope correctamente  
✅ Aplicar buenas prácticas en diseño de funciones  
✅ Evitar errores comunes

**¡Seguí adelante con el próximo capítulo!**
:::

:::{tip}
**¡Seguí con el próximo capítulo!**

[Capítulo 5 - Módulos y Paquetes →](5_modulos.md)
:::

### 5. Variables Globales sin Declarar

```python
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

(uso-ia-funciones)=
## Uso Ético y Efectivo de la IA en Funciones

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Aprender a descomponer problemas en funciones es una habilidad fundamental. La IA puede ayudarte a mejorar tus funciones, pero **vos debés diseñar la descomposición**del problema.
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
\✓ **Documentación**: Docstrings con formato apropiado  
✓ **Recursión**: Caso base y recursivo (opcional)  
✓ **Buenas prácticas**: Responsabilidad única, nombres, efectos secundarios  
✓ **Descomposición funcional**: Dividir problemas complejos en funciones simples  
✓ **Principios de diseño**: SRP, DRY, abstracción y niveles de descomposición

Las funciones son fundamentales para escribir código modular, reutilizable y mantenible. Te permiten dividir problemas complejos en partes más pequeñas y manejables, cada una con una responsabilidad clara.

:::{important} La modularización es clave
Un programa bien diseñado está compuesto de muchas funciones pequeñas, cada una haciendo una cosa bien. Esto facilita:
- Entender el código
- Testear cada parte por separado
- Encontrar y corregir errores
- Reutilizar código en diferentes contextos
- Trabajar en equipo

Pensá en funciones como "bloques de construcción" que combinás para crear programas más grandes. La **descomposición funcional** es la habilidad más importante que desarrollarás como programador: dividir un problema complejo en subproblemas simples, donde cada función tiene una responsabilidad única y clara.
:::

En el próximo capítulo, aprenderás sobre modularización avanzada: cómo organizar funciones en módulos y paquetes, y cómo trabajar con archivos para persistir datos.

---

(glosario-funciones)=
## Glosario

```{glossary}
Función
: Bloque de código reutilizable que realiza una tarea específica. Se define una vez con `def` y puede llamarse muchas veces. Puede recibir datos ({term}`parámetros <parámetro>`), procesarlos y devolver un resultado ({term}`return`).

def
: Palabra clave para **definir** una función. Sintaxis: `def nombre_funcion():`. Indica a Python que el código indentado siguiente es el cuerpo de la función.

Llamada de función
:  Ejecutar el código de una función escribiendo su nombre seguido de paréntesis. Ejemplo: `saludar()` llama a la función `saludar`. También se dice **invocar** una función.

Parámetro
: Variable en la **definición** de una función que recibe un valor cuando se llama. Ejemplo: en `def sumar(a, b):`, `a` y `b` son parámetros. También conocido como **parameter** en inglés.

Argumento
: Valor **real** que se pasa a una función al llamarla. Ejemplo: en `sumar(5, 3)`, `5` y `3` son argumentos. También conocido como **argument** en inglés.

return
: Palabra clave que devuelve un valor desde una función y termina su ejecución. El valor retornado puede usarse en el código que llamó la función. Ejemplo: `return resultado`.

Valor de retorno
: Resultado que una función devuelve con {term}`return`. Puede asignarse a una variable o usarse directamente. Si no hay `return`, la función devuelve {term}`None`.

None
: Valor especial que representa "nada" o "sin valor". Es lo que devuelve una función si no tiene `return` explícito. También se usa para indicar ausencia de valor.

Cuerpo de la función
: Bloque de código indentado que contiene las instrucciones que ejecuta la función. Todo lo que está indentado después de `def nombre():` es el cuerpo.

Docstring
: String de documentación al inicio de una función, entre triple comillas `"""..."""`. Describe qué hace la función, sus parámetros y valor de retorno. Se accede con `help(funcion)` o `funcion.__doc__`.

Argumento posicional
: {term}`Argumento` que se asigna a un {term}`argumento` según su **posición**. En `sumar(5, 3)`, `5` va al primer parámetro y `3` al segundo, por posición.

Argumento con nombre
: Argumento que se asigna explícitamente a un parámetro usando su nombre. Ejemplo: `sumar(a=5, b=3)`. El orden no importa. También conocido como **keyword argument**.

Parámetro por defecto
: Parámetro con un valor predeterminado en la definición. Si no se pasa argumento, usa ese valor. Ejemplo: `def saludar(nombre="Mundo"):`. Debe ir después de parámetros sin defecto.

Scope
: Región del código donde una variable es accesible. Hay dos tipos: {term}`scope local` (dentro de función) y {term}`scope global` (fuera de funciones). También conocido como **alcance**.

Scope local
: Variables definidas **dentro** de una función. Solo existen mientras la función se ejecuta y no son accesibles fuera de ella. Se crean al llamar la función y se destruyen al terminar.

Scope global
: Variables definidas **fuera** de funciones, en el nivel principal del programa. Son accesibles desde cualquier parte del código, incluyendo dentro de funciones.

global
: Palabra clave para declarar que se usará una variable global dentro de una función. Permite **modificar** una variable de{term}`scope global`. Ejemplo: `global contador`. Usar con precaución.

Shadowing
: Cuando una variable de {term}`Scope local` tiene el mismo nombre que una {term}`Scope global`, "tapa" o "enmascara" la global dentro de la función. La función usa la local, no la global.

*args
: Parámetro especial que recibe una **cantidad variable** de argumentos posicionales como una tupla. El `*` es lo importante, `args` es convención. Ejemplo: `def sumar(*numeros):`.

**kwargs
: Parámetro especial que recibe una **cantidad variable** de argumentos con nombre como diccionario. El `**` es lo importante, `kwargs` es convención. Ejemplo: `def config(**opciones):`.

Función lambda
: Función anónima de una sola línea. Sintaxis: `lambda parametros: expresion`. Ejemplo: `lambda x: x * 2` multiplica por 2. Útil para funciones simples temporales.

Recursión
: Técnica donde una función **se llama a sí misma** para resolver un problema dividiéndolo en casos más pequeños. Debe tener un **caso base** para detenerse, sino resulta en {term}`stack overflow`.

Caso base
: Condición en una {term}`función recursiva <recursión>` que detiene las llamadas recursivas. Sin caso base, la recursión nunca termina. Ejemplo: `if n == 0: return 1`.

Stack overflow
: Error que ocurre cuando hay demasiadas llamadas de función anidadas (especialmente en {term}`recursión` sin {term}`caso base`). Python lanza `RecursionError`. La pila de llamadas se llena.

Firma de función
: Definición de una función: nombre, parámetros y tipos (si se especifican). Ejemplo: `def area_rectangulo(base, altura):`. Define la interfaz de la función.

Side effect
: Cuando una función modifica algo **fuera** de ella: variables globales, archivos, pantalla (print), etc. Funciones puras no tienen efectos secundarios, solo retornan valores.

Función pura
: Función que: 1) Siempre retorna el mismo resultado para los mismos argumentos, y 2) No tiene {term}`efectos secundarios <side effect>`. Ejemplo: funciones matemáticas como `abs()`, `len()`.

DRY
: Principio "Don't Repeat Yourself" (No te repitas). Si escribís el mismo código varias veces, extraelo en una {term}`Función` para reutilizarlo. Reduce bugs y facilita mantenimiento.

SRP
: Principio "Single Responsibility Principle" (Principio de Responsabilidad Única). Cada función debe hacer **una cosa** y hacerla bien. Si hace múltiples cosas, dividirla en funciones más pequeñas.

Descomposición funcional
: Técnica de dividir un problema complejo en funciones más simples. Cada función resuelve una parte del problema. Facilita entendimiento, testing y mantenimiento del código.

Abstracción
: Ocultar detalles de implementación complejos detrás de una interfaz simple (la función). Los usuarios de la función no necesitan saber **cómo** funciona, solo **qué** hace.
```