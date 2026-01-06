---
title: Funciones
short_title: 4 - Funciones
subtitle: Definición, parámetros, scope, documentación y buenas prácticas.
---

(funciones)=
# Funciones

:::{admonition} Objetivos de Aprendizaje
:class: tip
Al finalizar este capítulo serás capaz de:
- Definir y llamar funciones para reutilizar código
- Trabajar con diferentes tipos de parámetros y argumentos
- Retornar valores y usarlos en tu programa
- Entender el scope (alcance) de las variables
- Documentar funciones profesionalmente
- Aplicar buenas prácticas en el diseño de funciones
- Usar funciones lambda y recursivas
:::

## Mapa del Capítulo

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'fontSize':'14px'}}}%%
graph TB
    Start([Capítulo 4: Funciones])
    
    %% Sección 1: Introducción
    Intro[Introducción]
    Intro1[¿Qué es una Función?]
    Intro2[¿Por qué Usar Funciones?]
    
    %% Sección 2: Definir y Llamar
    Def[Definir y Llamar Funciones]
    Def1[Tu Primera Función]
    Def2[Anatomía de una Función]
    Def3[Flujo de Ejecución]
    
    %% Sección 3: Parámetros
    Param[Parámetros y Argumentos]
    Param1[Recibir Información]
    Param2[Múltiples Parámetros]
    Param3[Posicionales vs Keyword]
    
    %% Sección 4: Return
    Ret[Retornar Valores]
    Ret1[print vs return]
    Ret2[Return Múltiple]
    Ret3[Salidas Tempranas]
    
    %% Sección 5: Scope
    Scope[Scope de Variables]
    Scope1[Variables Locales]
    Scope2[Variables Globales]
    Scope3[Shadowing]
    
    %% Sección 6: Avanzado
    Adv[Conceptos Avanzados]
    Adv1[Parámetros por Defecto]
    Adv2[*args y **kwargs]
    Adv3[Funciones Lambda]
    Adv4[Recursión]
    
    %% Sección 7: Prácticas
    Pract[Buenas Prácticas]
    Pract1[Documentación]
    Pract2[Diseño de Funciones]
    Pract3[Errores Comunes]
    
    %% Sección 8: Final
    Final[Cierre]
    Final1[Ejercicios Prácticos]
    Final2[Resumen]
    Final3[Referencias]
    
    %% Conexiones principales
    Start --> Intro
    Intro --> Intro1 --> Intro2
    
    Intro2 --> Def
    Def --> Def1 --> Def2 --> Def3
    
    Def3 --> Param
    Param --> Param1 --> Param2 --> Param3
    
    Param3 --> Ret
    Ret --> Ret1 --> Ret2 --> Ret3
    
    Ret3 --> Scope
    Scope --> Scope1 --> Scope2 --> Scope3
    
    Scope3 --> Adv
    Adv --> Adv1 --> Adv2 --> Adv3 --> Adv4
    
    Adv4 --> Pract
    Pract --> Pract1 --> Pract2 --> Pract3
    
    Pract3 --> Final
    Final --> Final1 --> Final2 --> Final3
    
    %% Estilos
    classDef intro fill:#e1f5ff,stroke:#01579b,stroke-width:2px
    classDef basico fill:#fff3e0,stroke:#e65100,stroke-width:2px
    classDef intermedio fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef avanzado fill:#fce4ec,stroke:#880e4f,stroke-width:2px
    classDef practica fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
    classDef final fill:#fff9c4,stroke:#f57f17,stroke-width:2px
    
    class Start,Intro,Intro1,Intro2 intro
    class Def,Def1,Def2,Def3,Param,Param1,Param2,Param3 basico
    class Ret,Ret1,Ret2,Ret3,Scope,Scope1,Scope2,Scope3 intermedio
    class Adv,Adv1,Adv2,Adv3,Adv4 avanzado
    class Pract,Pract1,Pract2,Pract3 practica
    class Final,Final1,Final2,Final3 final
```

:::{admonition} Cómo Usar Este Mapa
:class: tip

Este diagrama te muestra el recorrido completo del capítulo:

- **Celeste**: Fundamentos y motivación
- **Naranja**: Conceptos básicos (def, parámetros)
- **Violeta**: Conceptos intermedios (return, scope)
- **Rosa**: Temas avanzados (lambdas, recursión)
- **Verde**: Buenas prácticas y profesionalismo
- **Amarillo**: Práctica y consolidación

Podés seguir el orden lineal o saltar a las secciones que más te interesen. Los conceptos básicos son fundamentales para entender los avanzados.
:::

---

## Introducción: ¿Qué es una Función?

::::{grid} 1 1 2 2

:::{grid-item-card} Piénsalo Así
Imaginate que tenés una **máquina mágica** que hace algo específico. Le ponés ingredientes (los **argumentos**), la máquina hace su trabajo, y te devuelve un resultado.

Por ejemplo: una licuadora es como una función. Le das frutas (argumentos), apretás el botón (llamás a la función), y te devuelve un licuado (valor de retorno).
:::

:::{grid-item-card} En Programación
Una **función** es un bloque de código que:
1. Tiene un **nombre** para identificarla
2. Puede recibir **datos de entrada** (parámetros)
3. Realiza una **tarea específica**
4. Puede **devolver un resultado**
5. Se puede **reutilizar** todas las veces que quieras
:::
::::

### ¿Por qué Usar Funciones?

Sin funciones, tu código se vería así:

```{code-cell} ipython3
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

```{code-cell} ipython3
def calcular_promedio(notas):
    """Calcula el promedio de una lista de notas."""
    return sum(notas) / len(notas)

# Ahora solo llamamos a la función
print(f"Promedio examen 1: {calcular_promedio([7, 8, 9])}")
print(f"Promedio examen 2: {calcular_promedio([6, 7, 8])}")
print(f"Promedio examen 3: {calcular_promedio([9, 9, 10])}")
```

:::{important}  Ventajas de las Funciones
- **Reutilización**: Escribís el código una sola vez
- **Organización**: Código más limpio y fácil de leer
- **Mantenimiento**: Si hay que cambiar algo, lo hacés en un solo lugar
- **Menos errores**: Código probado y reutilizado es más confiable
- **Colaboración**: Varios programadores pueden trabajar en diferentes funciones
- **Modularidad**: Dividís problemas grandes en piezas pequeñas
:::

### En este Capítulo Aprenderás

::::{grid} 1 1 2 3

:::{grid-item-card} Básico
- Definir funciones
- Llamar funciones
- Parámetros y argumentos
- Retornar valores
:::

:::{grid-item-card} Intermedio
- Scope de variables
- Parámetros por defecto
- Documentación (docstrings)
- Funciones como objetos
:::

:::{grid-item-card} Avanzado
- Funciones lambda
- Recursión
- Buenas prácticas
- Patrones comunes
:::
::::

---

(definir-funciones)=
## Definir y Llamar Funciones

### Tu Primera Función 

Empecemos con lo más simple. Para crear una función, usamos la palabra mágica `def` (de "definir"):

```{code-cell} ipython3
def saludar():
    """Imprime un saludo amigable."""
    print("¡Hola! Bienvenido/a a Python")
```

¡Felicitaciones! Acabás de crear tu primera función. Pero... ¿por qué no pasa nada?

:::{admonition} ¿Por qué no imprime nada?
:class: note
Porque **definir**una función es como escribir una receta en un libro de cocina. La receta existe, pero no se cocina automáticamente. Para que funcione, tenés que **llamarla**:

```{code-cell} ipython3
def saludar():
    """Imprime un saludo amigable."""
    print("¡Hola! Bienvenido/a a Python")

# Ahora sí, llamamos a la función
saludar()  # Esto ejecuta el código dentro de la función
```
:::

### Anatomía de una Función

Veamos de qué partes está hecha una función:

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
Indica que vas a definir una función

**2. Nombre de la función**
Usa `snake_case`: todo minúsculas con guiones bajos

**3. Paréntesis `()`**
Contienen los parámetros (si los hay)

**4. Dos puntos `:`**
Marcan el inicio del bloque de código
:::

:::{grid-item-card} Componentes Opcionales
**5. Docstring**
Texto entre `"""` que explica qué hace la función

**6. Cuerpo**
Código indentado que se ejecuta cuando llamás a la función

**7. Return**
Devuelve un valor (lo veremos más adelante)
:::
::::

### Ejemplo Paso a Paso

```{code-cell} ipython3
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

```{code-cell} ipython3
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

```{code-cell} ipython3
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

:::{admonition} Observá el Flujo
:class: important
1. El programa ejecuta línea por línea
2. Cuando llega a `contar_hasta_tres()`, **salta**a la función
3. Ejecuta todo el código dentro de la función
4. Cuando termina, **vuelve**justo después de donde fue llamada
5. Continúa con el resto del programa
:::

### Ejercicio Práctico: Jugá con Funciones

```{code-cell} ipython3
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

Las funciones son más útiles cuando pueden trabajar con diferentes datos. Es como una licuadora: podés ponerle diferentes frutas cada vez.

```{code-cell} ipython3
def saludar_persona(nombre):
    """Saluda a una persona por su nombre."""
    print(f"¡Hola, {nombre}! ¿Cómo estás?")

# Misma función, diferentes datos
saludar_persona("Ana")
saludar_persona("Bruno")
saludar_persona("Carlos")
```

:::{admonition} Vocabulario Importante
:class: note

**Parámetro**= La "casilla" donde va a entrar el dato (en la definición)
```python
def saludar(nombre):  # ← "nombre" es el PARÁMETRO
    print(f"Hola, {nombre}")
```

**Argumento**= El dato real que le pasás (en la llamada)
```python
saludar("Ana")  # ← "Ana" es el ARGUMENTO
```

**Pensalo así**: El parámetro es como un molde, el argumento es lo que ponés en ese molde.
:::

### Múltiples Parámetros

Una función puede recibir varios datos a la vez:

```{code-cell} ipython3
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

### Tipo 1: Argumentos Posicionales

Los argumentos se pasan **en orden**. La posición importa:

```{code-cell} ipython3
def restar(a, b):
    """Resta b de a."""
    resultado = a - b
    print(f"{a} - {b} = {resultado}")
    return resultado

restar(10, 3)   # 10 - 3 = 7
restar(3, 10)   # 3 - 10 = -7  ← ¡Orden diferente, resultado diferente!
```

:::{warning} ¡El Orden Importa!
```{code-cell} ipython3
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

### Tipo 2: Argumentos con Nombre (Keyword Arguments)

Podés especificar qué argumento va a qué parámetro usando su nombre:

```{code-cell} ipython3
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
- ✓ Hay muchos parámetros
- ✓ Algunos tienen valores por defecto
- ✓ Querés que el código sea más legible

```{code-cell} ipython3
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

```{code-cell} ipython3
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

```{code-cell} ipython3
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

❌ No podés usar el resultado  
❌ Solo sirve para ver en pantalla  
❌ Se pierde el valor
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

✓ Podés usar el resultado  
✓ Guardás el valor en una variable  
✓ Podés hacer operaciones con él
:::
::::

:::{important} Regla de Oro
Según la {ref}`0x0009h`:  
**Las funciones NO deben contener `print()` a menos que ese sea su propósito específico.**

✓ **Hacé**: `return resultado`  
✗ **No hagas**: `print(resultado)`

¿Por qué? Porque `return` te da flexibilidad para usar el resultado como quieras.
:::

### La Palabra Mágica: `return`

`return` hace dos cosas importantes:
1. **Devuelve**un valor al código que llamó a la función
2. **Termina**la ejecución de la función inmediatamente

```{code-cell} ipython3
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

```{code-cell} ipython3
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

```{code-cell} ipython3
def clasificar_nota(nota):
    """Clasifica una nota en Aprobado/Desaprobado.
    
    Args:
        nota: Nota numérica del 0 al 10
        
    Returns:
        Clasificación de la nota
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

```{code-cell} ipython3
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

```{code-cell} ipython3
def analizar_texto(texto):
    """Analiza un texto y retorna varias estadísticas.
    
    Args:
        texto: El texto a analizar
        
    Returns:
        Una tupla con (cantidad_caracteres, cantidad_palabras, primera_palabra)
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

```{code-cell} ipython3
def calcular_rectangulo(base, altura):
    """Calcula área y perímetro de un rectángulo.
    
    Returns:
        Tupla con (area, perimetro)
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

```{code-cell} ipython3
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
Es útil para **salir temprano**de una función sin retornar nada:

```{code-cell} ipython3
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

```{code-cell} ipython3
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

El **scope**(alcance) es como el "territorio" donde vive una variable. Determina **dónde podés usar**una variable en tu código.

:::{admonition} 🏠 Pensalo Como Casas
:class: tip
Imaginate que cada función es una casa:
- Las variables **dentro**de la casa son **privadas**(locales) - solo existen ahí
- Las variables **fuera**de las casas son **públicas**(globales) - todos pueden verlas
- Desde adentro de la casa podés ver afuera, pero desde afuera NO podés ver adentro
:::

```{figure} ./4_funciones/scope.svg
:name: fig-scope
:alt: Scope de variables
:align: center
:width: 90%

Visualización del alcance (scope) de las variables
```

### Variables Locales: Las que Viven Dentro

Las variables creadas **dentro de una función**son **locales**- solo existen dentro de esa función:

```{code-cell} ipython3
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
1. **Nacen**cuando se ejecuta la función
2. **Mueren**cuando la función termina
3. **No se ven**desde afuera de la función
4. Cada llamada a la función crea variables nuevas
:::

```{code-cell} ipython3
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

Las variables definidas **fuera de todas las funciones**son **globales**:

```{code-cell} ipython3
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
Las funciones pueden **leer**variables globales, pero NO deberían **modificarlas**:

```{code-cell} ipython3
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
- Pasá los datos como parámetros
- Retorná los resultados

### Constantes Globales: La Excepción

Las **constantes**(valores que no cambian) globales **sí son aceptables**. Se escriben en MAYÚSCULAS:

```{code-cell} ipython3
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
- Escribilas en `MAYUSCULAS_CON_GUIONES`
- Ponelas al principio del archivo
- NUNCA las modifiques (de ahí el nombre "constantes")
- Está bien leerlas desde funciones
:::

### Ejemplo Completo: Scope en Acción

```{code-cell} ipython3
# Scope GLOBAL
DESCUENTO_PREMIUM = 0.20  # Constante global
nombre_tienda = "PyShop"  # Variable global (no se recomienda modificar)

def calcular_precio_final(precio_base, es_premium):
    """Calcula el precio final aplicando descuentos si corresponde.
    
    Args:
        precio_base: Precio sin descuento
        es_premium: Si el cliente es premium
        
    Returns:
        El precio final con descuento aplicado
    """
    # Scope LOCAL de esta función
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

```{code-cell} ipython3
x = "global"  # Variable global

def funcion_con_shadow():
    """Tiene una variable local con el mismo nombre."""
    x = "local"  # ← Esta x es DIFERENTE a la x global
    print(f"Dentro de la función: {x}")  # local

funcion_con_shadow()
print(f"Fuera de la función: {x}")  # global ← No cambió
```

:::{error} ❌ Error Común: Confundir Scope
```{code-cell} ipython3
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
- Usar parámetros para pasar datos
- Retornar resultados
- Usar constantes globales (MAYÚSCULAS)
- Mantener variables locales
:::

:::{grid-item-card} ✗ NO HAGAS
- Usar `global` para modificar variables
- Depender de variables globales mutables
- Nombres que ocultan variables globales importantes
- Efectos secundarios en funciones
:::
::::

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

Los parámetros con valores por defecto deben ir **después**de los obligatorios:

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
2. **Descripción detallada**(opcional): Más contexto si es necesario
3. **Args**: Lista de parámetros y su descripción
4. **Returns**: Qué retorna y su tipo
5. **Raises**(opcional): Excepciones que puede lanzar
6. **Example**(opcional): Ejemplos de uso

### Docstring de Una Línea

Para funciones simples:

```{code-cell} ipython3
def es_par(numero):
    """Retorna True si el número es par."""
    return numero % 2 == 0

def cuadrado(x):
    """Retorna el cuadrado de x."""
    return x **2
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
    return x **2

# Función lambda equivalente
cuadrado_lambda = lambda x: x **2

print(cuadrado(5))        # 25
print(cuadrado_lambda(5)) # 25

# Útil para operaciones simples
numeros = [1, 2, 3, 4, 5]
cuadrados = list(map(lambda x: x **2, numeros))
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

### 5. Valor por Defecto Mutable

```{code-cell} ipython3
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
Los valores por defecto se evalúan **UNA SOLA VEZ**cuando se define la función. Si usás una lista o diccionario como default, ¡será compartido entre todas las llamadas!
:::

### 6. No Usar Parámetros con Nombre

```{code-cell} ipython3
# ❌ Difícil de entender
def crear_cuenta(True, "premium", 100, False):
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

(ejercicios-funciones)=
## Ejercicios Prácticos

### Nivel Básico

::::{exercise} Función de Saludo
:label: ex-saludo-personalizado

Creá una función `saludar_persona(nombre, edad)` que:
- Reciba nombre y edad
- Retorne un saludo personalizado
- Si la edad es menor a 18, agregar "eres menor de edad"
- Si es mayor o igual a 18, agregar "eres mayor de edad"

:::{dropdown} Solución
```python
def saludar_persona(nombre, edad):
    """Genera un saludo personalizado según la edad.
    
    Args:
        nombre: Nombre de la persona.
        edad: Edad de la persona.
    
    Returns:
        Mensaje de saludo personalizado.
    """
    mensaje = f"¡Hola {nombre}! "
    
    if edad < 18:
        mensaje += "Eres menor de edad."
    else:
        mensaje += "Eres mayor de edad."
    
    return mensaje

# Pruebas
print(saludar_persona("Ana", 15))   # "¡Hola Ana! Eres menor de edad."
print(saludar_persona("Juan", 25))  # "¡Hola Juan! Eres mayor de edad."
```
:::
::::

::::{exercise} Calculadora de Propinas
:label: ex-calculadora-propina

Creá una función `calcular_propina(monto, porcentaje=15)` que:
- Reciba el monto de la cuenta
- Reciba opcionalmente el porcentaje de propina (default 15%)
- Retorne una tupla con (propina, total)

:::{dropdown} Solución
```python
def calcular_propina(monto, porcentaje=15):
    """Calcula propina y total a pagar.
    
    Args:
        monto: Monto de la cuenta.
        porcentaje: Porcentaje de propina (default 15).
    
    Returns:
        Tupla (propina, total).
    """
    propina = monto * (porcentaje / 100)
    total = monto + propina
    return (propina, total)

# Pruebas
propina, total = calcular_propina(100)
print(f"Propina: ${propina:.2f}, Total: ${total:.2f}")
# Propina: $15.00, Total: $115.00

propina, total = calcular_propina(100, 20)
print(f"Propina: ${propina:.2f}, Total: ${total:.2f}")
# Propina: $20.00, Total: $120.00
```
:::
::::

### Nivel Intermedio

::::{exercise} Validador de Contraseñas
:label: ex-validador-password

Creá una función `validar_password(password)` que retorne `True` si:
- Tiene al menos 8 caracteres
- Contiene al menos una mayúscula
- Contiene al menos un número
- Contiene al menos un carácter especial (!@#$%^&*)

:::{dropdown} Solución
```python
def validar_password(password):
    """Valida que una contraseña cumpla requisitos de seguridad.
    
    Args:
        password: Contraseña a validar.
    
    Returns:
        True si cumple todos los requisitos, False en caso contrario.
    """
    # Verificar longitud mínima
    if len(password) < 8:
        return False
    
    # Verificar mayúscula
    tiene_mayuscula = any(c.isupper() for c in password)
    if not tiene_mayuscula:
        return False
    
    # Verificar número
    tiene_numero = any(c.isdigit() for c in password)
    if not tiene_numero:
        return False
    
    # Verificar carácter especial
    caracteres_especiales = "!@#$%^&*"
    tiene_especial = any(c in caracteres_especiales for c in password)
    if not tiene_especial:
        return False
    
    return True

# Pruebas
print(validar_password("abc"))           # False (muy corta)
print(validar_password("abcdefgh"))      # False (sin mayúscula, número, especial)
print(validar_password("Abcdefgh"))      # False (sin número, especial)
print(validar_password("Abcdefgh1"))     # False (sin especial)
print(validar_password("Abcdefgh1!"))    # True ✓
```
:::
::::

::::{exercise} Calculadora Estadística
:label: ex-calculadora-estadistica

Creá una función `estadisticas(numeros)` que retorne un diccionario con:
- `'promedio'`: promedio de los números
- `'minimo'`: valor mínimo
- `'maximo'`: valor máximo
- `'rango'`: diferencia entre máximo y mínimo

:::{dropdown} Solución
```python
def estadisticas(numeros):
    """Calcula estadísticas básicas de una lista de números.
    
    Args:
        numeros: Lista de números.
    
    Returns:
        Diccionario con estadísticas.
    """
    if not numeros:
        return None
    
    return {
        'promedio': sum(numeros) / len(numeros),
        'minimo': min(numeros),
        'maximo': max(numeros),
        'rango': max(numeros) - min(numeros)
    }

# Prueba
datos = [10, 5, 8, 12, 3, 15]
resultado = estadisticas(datos)
print(f"Promedio: {resultado['promedio']:.2f}")
print(f"Mínimo: {resultado['minimo']}")
print(f"Máximo: {resultado['maximo']}")
print(f"Rango: {resultado['rango']}")
# Promedio: 8.83
# Mínimo: 3
# Máximo: 15
# Rango: 12
```
:::
::::

### Nivel Avanzado

::::{exercise} Sistema de Descuentos
:label: ex-sistema-descuentos

Creá un sistema de descuentos con estas funciones:

1. `aplicar_descuento(precio, porcentaje)`: aplica descuento básico
2. `descuento_por_cantidad(precio, cantidad)`: 
   - 10% si cantidad >= 5
   - 20% si cantidad >= 10
   - 30% si cantidad >= 20
3. `descuento_temporal(precio, es_black_friday=False)`: 
   - 50% en Black Friday
   - 0% en días normales
4. `calcular_precio_final(precio, cantidad, es_black_friday=False)`:
   - Combina todos los descuentos anteriores

:::{dropdown} Solución
```python
def aplicar_descuento(precio, porcentaje):
    """Aplica un descuento porcentual al precio.
    
    Args:
        precio: Precio original.
        porcentaje: Porcentaje de descuento (0-100).
    
    Returns:
        Precio con descuento aplicado.
    """
    descuento = precio * (porcentaje / 100)
    return precio - descuento

def descuento_por_cantidad(precio, cantidad):
    """Calcula descuento según cantidad comprada.
    
    Args:
        precio: Precio por unidad.
        cantidad: Cantidad de unidades.
    
    Returns:
        Tupla (precio_con_descuento, porcentaje_aplicado).
    """
    if cantidad >= 20:
        porcentaje = 30
    elif cantidad >= 10:
        porcentaje = 20
    elif cantidad >= 5:
        porcentaje = 10
    else:
        porcentaje = 0
    
    precio_final = aplicar_descuento(precio, porcentaje)
    return (precio_final, porcentaje)

def descuento_temporal(precio, es_black_friday=False):
    """Aplica descuento temporal según evento.
    
    Args:
        precio: Precio actual.
        es_black_friday: True si es Black Friday.
    
    Returns:
        Precio con descuento temporal aplicado.
    """
    if es_black_friday:
        return aplicar_descuento(precio, 50)
    return precio

def calcular_precio_final(precio, cantidad, es_black_friday=False):
    """Calcula precio final con todos los descuentos.
    
    Args:
        precio: Precio unitario.
        cantidad: Cantidad de unidades.
        es_black_friday: Si aplica descuento de Black Friday.
    
    Returns:
        Diccionario con desglose de precios.
    """
    # Precio sin descuentos
    subtotal = precio * cantidad
    
    # Aplicar descuento por cantidad
    precio_unitario_desc, porc_cantidad = descuento_por_cantidad(precio, cantidad)
    subtotal_con_desc_cantidad = precio_unitario_desc * cantidad
    
    # Aplicar descuento temporal
    total_final = descuento_temporal(subtotal_con_desc_cantidad, es_black_friday)
    
    # Calcular ahorro total
    ahorro_total = subtotal - total_final
    porc_ahorro_total = (ahorro_total / subtotal) * 100 if subtotal > 0 else 0
    
    return {
        'subtotal': subtotal,
        'descuento_cantidad': porc_cantidad,
        'descuento_black_friday': 50 if es_black_friday else 0,
        'total_final': total_final,
        'ahorro_total': ahorro_total,
        'porcentaje_ahorro': porc_ahorro_total
    }

# Pruebas
print("Caso 1: 3 unidades, día normal")
resultado = calcular_precio_final(100, 3, False)
print(f"Total: ${resultado['total_final']:.2f}")
print(f"Ahorro: ${resultado['ahorro_total']:.2f} ({resultado['porcentaje_ahorro']:.1f}%)")
print()

print("Caso 2: 15 unidades, día normal")
resultado = calcular_precio_final(100, 15, False)
print(f"Total: ${resultado['total_final']:.2f}")
print(f"Ahorro: ${resultado['ahorro_total']:.2f} ({resultado['porcentaje_ahorro']:.1f}%)")
print()

print("Caso 3: 15 unidades, Black Friday")
resultado = calcular_precio_final(100, 15, True)
print(f"Total: ${resultado['total_final']:.2f}")
print(f"Ahorro: ${resultado['ahorro_total']:.2f} ({resultado['porcentaje_ahorro']:.1f}%)")
```

**Salida:**
```
Caso 1: 3 unidades, día normal
Total: $300.00
Ahorro: $0.00 (0.0%)

Caso 2: 15 unidades, día normal
Total: $1200.00
Ahorro: $300.00 (20.0%)

Caso 3: 15 unidades, Black Friday
Total: $600.00
Ahorro: $900.00 (60.0%)
```
:::
::::

::::{exercise} Generador de Contraseñas
:label: ex-generador-passwords

Creá una función `generar_password(longitud=12, incluir_especiales=True)` que:
- Genere una contraseña aleatoria
- Incluya mayúsculas, minúsculas y números
- Opcionalmente incluya caracteres especiales
- Asegure que cumple requisitos de seguridad (usar `validar_password`)

**Pista:**Necesitarás `import random` y `import string`

:::{dropdown} Solución
```python
import random
import string

def generar_password(longitud=12, incluir_especiales=True):
    """Genera una contraseña segura aleatoria.
    
    Args:
        longitud: Longitud de la contraseña (default 12).
        incluir_especiales: Si incluir caracteres especiales (default True).
    
    Returns:
        Contraseña generada.
    
    Raises:
        ValueError: Si longitud es menor a 8.
    """
    if longitud < 8:
        raise ValueError("La contraseña debe tener al menos 8 caracteres")
    
    # Definir conjuntos de caracteres
    minusculas = string.ascii_lowercase
    mayusculas = string.ascii_uppercase
    numeros = string.digits
    especiales = "!@#$%^&*"
    
    # Construir conjunto total
    todos_caracteres = minusculas + mayusculas + numeros
    if incluir_especiales:
        todos_caracteres += especiales
    
    # Generar contraseña asegurando requisitos mínimos
    while True:
        # Elegir caracteres aleatorios
        password = ''.join(random.choice(todos_caracteres) for _ in range(longitud))
        
        # Verificar que cumple requisitos
        tiene_minuscula = any(c in minusculas for c in password)
        tiene_mayuscula = any(c in mayusculas for c in password)
        tiene_numero = any(c in numeros for c in password)
        tiene_especial = any(c in especiales for c in password) if incluir_especiales else True
        
        # Si cumple todos los requisitos, retornar
        if tiene_minuscula and tiene_mayuscula and tiene_numero and tiene_especial:
            return password

# Pruebas
print("Contraseñas generadas:")
for i in range(5):
    pwd = generar_password(12, True)
    es_valida = validar_password(pwd)
    print(f"{i+1}. {pwd} - {'✓ Válida' if es_valida else '✗ Inválida'}")
```
:::
::::

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
- `*args` y `**kwargs`
:::

:::{grid-item-card} Return
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
- Evitar `global`
- Usar parámetros y returns
:::

:::{grid-item-card} Funciones Lambda
- Funciones anónimas
- Una sola expresión
- Útiles con map/filter
- No reemplazan funciones normales
:::
::::

### Checklist de Buenas Prácticas

```{admonition} ✅ Funciones de Calidad
:class: tip

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
| Kwargs variables | `def func(**kwargs):` | `def config(**opts):` |
| Lambda | `lambda params: expresion` | `lambda x: x * 2` |
| Docstring | `"""descripcion"""` | `"""Suma dos números."""` |
| Scope local | Variable dentro de función | `def f(): x = 1` |
| Scope global | Variable fuera de funciones | `X = 1` (constante) |

### Para Seguir Practicando

```{admonition} Próximos Pasos
:class: tip

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

:::{admonition} ¡Felicitaciones!
:class: success

Completaste el capítulo de **Funciones**. Ahora sabés:

✅ Crear funciones con diferentes tipos de parámetros  
✅ Documentar funciones profesionalmente  
✅ Entender y aplicar scope correctamente  
✅ Usar funciones lambda cuando son apropiadas  
✅ Aplicar buenas prácticas en diseño de funciones  
✅ Evitar errores comunes

**¡Seguí adelante con el próximo capítulo!**
:::

:::{tip}
**¡Seguí con el próximo capítulo!**

[Capítulo 5 - Módulos y Paquetes →](5_modulos.md)
:::

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

Este tipo de revisión te ayuda a **mejorar tu estilo**y aprender buenas prácticas.

### Errores Comunes en este Módulo

:::{danger} No pidas que la IA escriba tus funciones
La capacidad de **descomponer un problema en funciones** es lo que estás aprendiendo. Si la IA hace esta descomposición por vos, perdés el objetivo del módulo.

**Proceso correcto:**
1. Vos identificás las tareas del problema
2. Vos decidís qué funciones necesitás
3. Vos escribís las funciones básicas
4. La IA te ayuda a **refinar**lo que ya escribiste
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
