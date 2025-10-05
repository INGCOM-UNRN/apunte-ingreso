title: Cuestiones de estilo en Python
short_title: 0x0000h - Estilo Python
subtitle: Pautas para la organización y prolijidad del código en Python basadas en PEP 8 y buenas prácticas.
---

## Introducción

Este documento establece un conjunto de reglas de estilo para Python, diseñadas para que tu código sea más claro, legible y menos propenso a errores. Estas reglas están alineadas con las mejores prácticas de la comunidad Python, especialmente:

- **[PEP 8](https://peps.python.org/pep-0008/)**: La guía de estilo oficial de Python
- **[PEP 20](https://peps.python.org/pep-0020/)**: The Zen of Python (filosofía de diseño)
- **[PEP 257](https://peps.python.org/pep-0257/)**: Convenciones para docstrings

:::{note} ¿Qué es un PEP?
**PEP** significa Python Enhancement Proposal (Propuesta de Mejora de Python). Los PEPs son documentos de diseño que proporcionan información a la comunidad Python o describen una nueva característica para Python, sus procesos o su entorno. Los PEPs son el mecanismo principal para proponer nuevas características importantes, recopilar opiniones de la comunidad sobre un problema y documentar las decisiones de diseño que han entrado en Python. Cada PEP tiene un número único y está disponible en [https://peps.python.org/](https://peps.python.org/).
:::

Python es un lenguaje que enfatiza la legibilidad y la simplicidad. Como dice el Zen de Python: **"La legibilidad cuenta"** (Readability counts). Estas reglas te ayudarán a escribir código que no solo funcione, sino que sea comprensible para cualquier desarrollador Python, incluyéndote a vos mismo en el futuro.

:::{note} The Zen of Python
Python tiene una filosofía de diseño expresada en "The Zen of Python" ({ref}`pep-20-ref`). Podés leerla ejecutando `import this` en un intérprete de Python. Algunos principios clave:
- Bello es mejor que feo
- Explícito es mejor que implícito
- Simple es mejor que complejo
- La legibilidad cuenta
- Los errores nunca deberían pasar silenciosamente
:::

Un código de calidad no solo debe ser funcional, sino también comprensible para cualquier profesional que deba leerlo. Un código limpio y bien organizado facilita la colaboración, ahorra tiempo en corrección y previene complicaciones durante la depuración.

## Apertura a Sugerencias y Debate

Estamos abiertos a debatir todas las reglas. Para ello, solo tenés que abrir un hilo en Discussions o un ticket en el Issue Tracker. Aceptamos propuestas de nuevas reglas, clasificaciones, explicaciones y potenciales excepciones.

## Principios Clave

- **Claridad (Readability):** El código debe ser fácil de leer. "Explicit is better than implicit".
- **Simplicidad:** "Simple is better than complex" - preferir soluciones simples sobre complejas.
- **Consistencia:** El uso de un estilo uniforme optimiza la colaboración.
- **Pythonic:** Aprovechar las características idiomáticas de Python.
- **Mantenibilidad:** El código debe ser sencillo de modificar y extender.

---

## Las Reglas

(0x0000h)=
### Regla `0x0000h`: La claridad y legibilidad son de máxima importancia

**Principio:** El código debe ser claro y fácil de entender para cualquier lector, no solo para su autor. La claridad es siempre preferible a técnicas de programación ofuscadas.

```diff
- # Incorrecto: demasiado compacto y difícil de leer
- resultado = suma([x for x in range(100) if x % 2 == 0 and x > 10]) if validar() else 0

+ # Correcto: claro y explícito
+ if validar():
+     numeros_pares = [x for x in range(100) if x % 2 == 0 and x > 10]
+     resultado = sum(numeros_pares)
+ else:
+     resultado = 0
```

En Python, la indentación forzada ya promueve la claridad. Aprovechá esto escribiendo código que "respira" y es fácil de seguir visualmente.

:::{tip} PEP 20
"Si la implementación es difícil de explicar, es una mala idea. Si la implementación es fácil de explicar, puede ser una buena idea."
:::

---

(0x0001h)=
### Regla `0x0001h`: Los identificadores deben ser descriptivos

**Principio:** Los nombres de variables, funciones, clases y módulos deben reflejar con precisión su propósito. Esto contribuye a que el código sea autodescriptivo.

**Convenciones de Python ({ref}`pep-8-ref`):
- Variables y funciones: `snake_case` (minúsculas con guiones bajos)
- Constantes: `SNAKE_CASE_MAYUSCULAS`
- Clases: `PascalCase` (también llamado CapWords)
- Módulos: `snake_case` (nombres cortos, todo en minúsculas)

```python
# ❌ Incorrecto: identificadores poco descriptivos
a, b = get_price(), None
b = calc(a)

# ✓ Correcto: identificadores descriptivos
precio_original = obtener_precio()
precio_con_descuento = calcular_descuento(precio_original)
```

#### Nombres de Variables

```python
# ❌ Incorrecto
x = 25
d = 86400
l = []

# ✓ Correcto
edad_minima = 25
segundos_por_dia = 86400
lista_estudiantes = []
```

#### Nombres Cortos: Cuándo Son Aceptables

Bajo ciertas condiciones, los nombres cortos son aceptables y hasta preferibles:

1. Variables de bucle en contextos obvios: `i`, `j`, `k`
2. Coordenadas matemáticas: `x`, `y`, `z`
3. Contadores simples en ámbitos muy reducidos: `n`, `count`
4. Variables temporales en list comprehensions (cuando el contexto es claro)

```python
# ✓ Aceptable: contexto matemático claro
for i in range(10):
    resultado = i ** 2

# ✓ Aceptable: comprensión simple
cuadrados = [x**2 for x in range(10)]

# ❌ Incorrecto: nombre muy corto sin contexto claro
for x in estudiantes:
    p(x)  # ¿Qué hace p?

# ✓ Correcto
for estudiante in estudiantes:
    procesar_inscripcion(estudiante)
```

---

(0x0002h)=
### Regla `0x0002h`: Una asignación o declaración por línea

**Principio:** Cada asignación debe estar en su propia línea para mayor claridad, excepto cuando el desempaquetado de tuplas es natural e idiomático.

```diff
- # Incorrecto: múltiples asignaciones complejas en una línea
- x, y, z, resultado = 1, obtener_valor(), calcular(), procesar()

+ # Correcto: cada asignación en su propia línea
+ x = 1
+ y = obtener_valor()
+ z = calcular()
+ resultado = procesar()
```

**Excepciones idiomáticas en Python:**

```python
# ✓ Aceptable: desempaquetado simple y claro
x, y = 10, 20
nombre, edad = obtener_datos_usuario()

# ✓ Aceptable: swap pythonic
a, b = b, a

# ✓ Aceptable: desempaquetado de funciones que retornan múltiples valores
ancho, alto = obtener_dimensiones()

# ❌ Evitar: cadenas complejas
a, b, c = x, y, z = calcular(), procesar(), validar()
```

---

(0x0003h)=
### Regla `0x0003h`: Siempre inicializar variables con valores explícitos

**Principio:** En Python, las variables no existen hasta que se les asigna un valor. Es importante inicializar contadores, acumuladores y variables de control con valores explícitos antes de usarlos.

```python
# ❌ Incorrecto: variable no inicializada
for i in range(10):
    contador += 1  # NameError: name 'contador' is not defined

# ✓ Correcto: inicialización explícita
contador = 0
for i in range(10):
    contador += 1
```

**Valores por defecto sensatos:**

```python
# Contadores y acumuladores
contador = 0
suma_total = 0
producto = 1

# Colecciones vacías
lista_nombres = []
diccionario_edades = {}
conjunto_unicos = set()
tupla_vacia = ()

# Strings
mensaje = ""
texto_acumulado = ""

# Booleanos
encontrado = False
es_valido = True

# None para valores que se asignarán después
resultado = None
archivo = None
```

:::{warning} Evitar valores mutables como argumentos por defecto
```python
# ❌ ERROR COMÚN: lista mutable como default
def agregar_elemento(elemento, lista=[]):
    lista.append(elemento)
    return lista

# ✓ Correcto: usar None y crear nueva lista
def agregar_elemento(elemento, lista=None):
    if lista is None:
        lista = []
    lista.append(elemento)
    return lista
```
:::

---

(0x0004h)=
### Regla `0x0004h`: Un espacio antes y después de cada operador binario

**Principio ({ref}`pep-8-ref`):** Los operadores binarios deben estar rodeados de un espacio a cada lado para mejorar la legibilidad.

```diff
- # Incorrecto
- resultado=valor1+valor2*3
- x=5

+ # Correcto
+ resultado = valor1 + valor2 * 3
+ x = 5
```

**Operadores que requieren espacios:**

```python
# Asignación
x = 5
y += 10

# Comparación
if edad >= 18:
    pass

# Aritméticos
resultado = a + b - c * d / e

# Lógicos
if es_valido and tiene_permiso or es_admin:
    pass

# Membership
if nombre in lista_estudiantes:
    pass
```

**Excepciones ({ref}`pep-8-ref`):**

```python
# ✓ Sin espacios en argumentos por keyword
funcion(arg1=valor1, arg2=valor2)

# ✓ Sin espacios en slicing
lista[inicio:fin]
lista[inicio:fin:paso]

# ✓ Agrupar por precedencia (opcional pero válido)
resultado = a*b + c*d  # Agrupa multiplicaciones sin espacios
```

---

(0x0005h)=
### Regla `0x0005h`: La indentación debe ser consistente (4 espacios)

**Principio ({ref}`pep-8-ref`):** Python usa indentación para definir bloques de código. **Siempre usar 4 espacios**, nunca tabs.

```python
# ✓ Correcto: 4 espacios por nivel de indentación
def calcular_promedio(numeros):
    if len(numeros) == 0:
        return 0
    
    suma = 0
    for numero in numeros:
        suma += numero
    
    promedio = suma / len(numeros)
    return promedio
```

**Reglas de indentación:**

1. **4 espacios por nivel** (no 2, no 8, no tabs)
2. **Consistencia total** en todo el archivo
3. **Líneas continuadas:** Alinear con el delimitador de apertura o usar indentación colgante

```python
# ✓ Opción 1: Alinear con delimitador
resultado = funcion_con_nombre_largo(argumento1, argumento2,
                                     argumento3, argumento4)

# ✓ Opción 2: Indentación colgante (hanging indent)
resultado = funcion_con_nombre_largo(
    argumento1,
    argumento2,
    argumento3,
    argumento4
)

# ✓ Opción 3: Listas/diccionarios largos
lista_valores = [
    valor1,
    valor2,
    valor3,
    valor4,
]
```

:::{danger} Nunca mezclar tabs y espacios
Python 3 no permite mezclar tabs y espacios. Configurá tu editor para convertir tabs en 4 espacios automáticamente.
:::

---

(0x0006h)=
### Regla `0x0006h`: Evitar `break` y `continue`; usar banderas de control

**Principio:** Aunque Python permite `break` y `continue`, en este curso preferimos usar **banderas de control** (variables booleanas) para gestionar la terminación de loops. Esto produce código más predecible y estructurado.

```python
# ❌ Evitar (aunque Python lo permite)
for numero in numeros:
    if numero < 0:
        continue
    if numero > 100:
        break
    procesar(numero)

# ✓ Preferido: usando bandera
i = 0
seguir_procesando = True

while i < len(numeros) and seguir_procesando:
    numero = numeros[i]
    
    if numero >= 0:  # Solo procesar si no es negativo
        if numero > 100:
            seguir_procesando = False
        else:
            procesar(numero)
    
    i += 1
```

**Ventajas del enfoque con banderas:**

1. **Flujo explícito:** La condición de salida está en el `while`
2. **Más fácil de razonar:** No hay saltos inesperados
3. **Mejor para debugging:** Puedes inspeccionar la bandera
4. **Más fácil de testear:** El estado es visible

:::{note} Contexto Pedagógico
Esta regla es específica de este curso para enseñar control de flujo estructurado. En código Python profesional, `break` y `continue` son comunes y aceptados cuando mejoran la claridad.
:::

---

(0x0007h)=
### Regla `0x0007h`: Preferir `while` sobre `for` para loops condicionales

**Principio:** Usar `while` cuando la condición de parada no es un simple recorrido de secuencia. El `for` de Python es idiomático para iterar sobre colecciones.

**Usar `while` cuando:**
- No sabés cuántas iteraciones necesitarás
- La condición de parada es compleja
- Estás esperando una condición externa (input del usuario, etc.)

```python
# ✓ Correcto: while para condición
numero = int(input("Ingrese un número (0 para terminar): "))

while numero != 0:
    procesar(numero)
    numero = int(input("Ingrese un número (0 para terminar): "))
```

**Usar `for` cuando:**
- Iterás sobre una secuencia conocida (lista, range, string, etc.)
- Sabés exactamente cuántas iteraciones necesitás

```python
# ✓ Correcto: for para iterar colecciones
for estudiante in lista_estudiantes:
    procesar_inscripcion(estudiante)

# ✓ Correcto: for con range para contador conocido
for i in range(10):
    print(f"Iteración {i}")

# ✓ Correcto: for para strings
for caracter in "Python":
    print(caracter)
```

:::{tip} Estilo Pythonic
En Python, el `for` es más idiomático que en otros lenguajes. Aprovechá las características de iteración de Python:
```python
# ✓ Pythonic
for i, valor in enumerate(lista):
    print(f"Índice {i}: {valor}")

# ✓ Pythonic
for clave, valor in diccionario.items():
    print(f"{clave}: {valor}")
```
:::

---

(0x0008h)=
### Regla `0x0008h`: Cada función debe tener un único punto de retorno

**Principio:** Limitar una función a un único `return` mejora la legibilidad y facilita el seguimiento del flujo de control.

```python
# ❌ Evitar: múltiples returns
def calcular_descuento(precio, es_cliente_vip, es_oferta):
    if precio < 0:
        return 0
    
    if es_cliente_vip:
        return precio * 0.8
    
    if es_oferta:
        return precio * 0.9
    
    return precio

# ✓ Preferido: un solo return
def calcular_descuento(precio, es_cliente_vip, es_oferta):
    precio_final = precio
    
    if precio >= 0:
        if es_cliente_vip:
            precio_final = precio * 0.8
        elif es_oferta:
            precio_final = precio * 0.9
    else:
        precio_final = 0
    
    return precio_final
```

**Ventajas:**
1. Facilita el debugging (un solo punto para inspeccionar)
2. Permite cleanup/logging centralizado antes del return
3. Hace el flujo más predecible

:::{note} Excepciones razonables
En funciones de validación muy simples, múltiples returns pueden ser más claros:
```python
def es_par(numero):
    return numero % 2 == 0
```
Usá tu criterio: si múltiples returns hacen el código **más claro**, pueden ser aceptables.
:::

---

(0x0009h)=
### Regla `0x0009h`: Las funciones no deben contener `print()` o `input()`, a menos que ese sea su propósito explícito

**Principio:** Las funciones deben estar desacopladas de I/O para maximizar su reutilización y facilitar las pruebas.

```python
# ❌ Incorrecto: mezcla lógica con I/O
def calcular_promedio(numeros):
    suma = sum(numeros)
    promedio = suma / len(numeros)
    print(f"El promedio es: {promedio}")  # ❌ I/O dentro de función de cálculo
    return promedio

# ✓ Correcto: función pura, sin I/O
def calcular_promedio(numeros):
    """Calcula el promedio de una lista de números.
    
    Args:
        numeros: Lista de números
        
    Returns:
        float: El promedio
    """
    return sum(numeros) / len(numeros)

# ✓ El caller decide qué hacer con el resultado
promedio = calcular_promedio([10, 20, 30])
print(f"El promedio es: {promedio}")
```

**Excepciones legítimas:**

```python
# ✓ Correcto: función cuyo propósito ES hacer I/O
def solicitar_edad():
    """Solicita y valida la edad del usuario. 
    
    Returns:
        int: Edad válida ingresada por el usuario
    """
    while True:
        try:
            edad = int(input("Ingrese su edad: "))
            if 0 < edad < 120:
                return edad
            print("Edad inválida. Intente nuevamente.")
        except ValueError:
            print("Por favor ingrese un número.")
```

**Ventajas del desacoplamiento:**
1. **Reutilización:** La función puede usarse en diferentes contextos
2. **Testing:** Fácil de probar sin interacción humana
3. **Flexibilidad:** El caller decide cómo usar el resultado (print, guardar, enviar, etc.)

---

(0x000Ah)=
### Regla `0x000Ah`: Todas las funciones deben incluir docstrings

**Principio ({ref}`pep-257-ref`):** Las funciones deben documentarse con docstrings que expliquen su propósito, parámetros, retorno y excepciones.

**Formato recomendado (estilo Google/NumPy):**

```python
def calcular_area_rectangulo(base, altura):
    """Calcula el área de un rectángulo. 
    
    Descripción más detallada si es necesaria. El área se calcula
    multiplicando la base por la altura.
    
    Args:
        base (float): La longitud de la base del rectángulo.
        altura (float): La altura del rectángulo.
    
    Returns:
        float: El área del rectángulo.
    
    Raises:
        ValueError: Si base o altura son negativos.
    
    Examples:
        >>> calcular_area_rectangulo(5, 3)
        15.0
        >>> calcular_area_rectangulo(2.5, 4)
        10.0
    """
    if base < 0 or altura < 0:
        raise ValueError("Base y altura deben ser no negativos")
    
    return base * altura
```

**Elementos del docstring:**

1. **Primera línea:** Resumen breve (una línea, termina con punto)
2. **Línea en blanco**
3. **Descripción extendida:** (opcional) Explicación más detallada
4. **Args:** Cada parámetro con tipo y descripción
5. **Returns:** Qué retorna la función
6. **Raises:** Qué excepciones puede lanzar
7. **Examples:** (opcional) Ejemplos de uso

**Docstrings mínimos para funciones simples:**

```python
def sumar(a, b):
    """Retorna la suma de a y b."""
    return a + b
```

:::{important} Cuándo documentar
- **Siempre:** Funciones públicas (que serán usadas por otros)
- **Recomendado:** Funciones complejas o con lógica no obvia
- **Opcional:** Funciones privadas muy simples (pero consideralo)
:::

---

(0x000Bh)=
### Regla `0x000Bh`: Evitar variables globales; usar parámetros y retornos

**Principio:** Las variables globales pueden ser modificadas desde cualquier parte del programa, causando efectos secundarios impredecibles.

```python
# ❌ Incorrecto: variable global
contador_global = 0

def incrementar_contador():
    global contador_global  # Efecto secundario oculto
    contador_global += 1

def imprimir_contador():
    print(contador_global)  # Dependencia no explícita
```

```python
# ✓ Correcto: pasar estado como parámetros
def incrementar_contador(contador):
    """Incrementa un contador y retorna el nuevo valor. 
    
    Args:
        contador (int): Valor actual del contador
        
    Returns:
        int: Contador incrementado
    """
    return contador + 1

def imprimir_contador(contador):
    """Imprime el valor del contador. 
    
    Args:
        contador (int): Valor a imprimir
    """
    print(f"Contador: {contador}")

# Uso
contador_local = 0
contador_local = incrementar_contador(contador_local)
imprimir_contador(contador_local)
```

**Excepciones aceptables:**
- **Constantes:** Variables que no cambian (en MAYUSCULAS)
- **Configuración:** Valores de configuración del programa

```python
# ✓ Aceptable: constantes globales
PI = 3.14159265359
VELOCIDAD_LUZ = 299792458  # m/s
MAX_INTENTOS = 3

# ✓ Aceptable: configuración
DEBUG_MODE = True
DATABASE_URL = "sqlite:///datos.db"
```

:::{tip} Alternativas a globales
Si necesitás compartir estado:
1. **Clases:** Encapsular estado en objetos (verás esto más adelante)
2. **Parámetros:** Pasar explícitamente
3. **Return múltiple:** Retornar estado actualizado
:::

---

(0x000Ch)=
### Regla `0x000Ch`: Cada función debe tener una única responsabilidad (SRP)

**Principio (Single Responsibility Principle):** Una función debe hacer una cosa y hacerla bien. Si necesitás usar "y" para describir qué hace una función, probablemente hace demasiadas cosas.

```python
# ❌ Incorrecto: función con múltiples responsabilidades
def procesar_estudiante(nombre, notas):
    # Validación
    if not nombre:
        return None
    
    # Cálculo de promedio
    promedio = sum(notas) / len(notas)
    
    # Determinación de estado
    if promedio >= 6:
        estado = "Aprobado"
    else:
        estado = "Reprobado"
    
    # Formateo de salida
    mensaje = f"{nombre}: {promedio:.2f} - {estado}"
    
    # I/O
    print(mensaje)
    
    return promedio
```

```python
# ✓ Correcto: funciones con responsabilidad única
def validar_nombre(nombre):
    """Valida que el nombre no esté vacío."""
    return bool(nombre and nombre.strip())

def calcular_promedio(notas):
    """Calcula el promedio de una lista de notas."""
    return sum(notas) / len(notas)

def determinar_estado(promedio):
    """Determina si el estudiante aprobó según el promedio."""
    return "Aprobado" if promedio >= 6 else "Reprobado"

def formatear_resultado(nombre, promedio, estado):
    """Formatea el resultado como string."""
    return f"{nombre}: {promedio:.2f} - {estado}"

# Uso coordinado
def procesar_estudiante(nombre, notas):
    """Procesa la información de un estudiante."""
    if not validar_nombre(nombre):
        return None
    
    promedio = calcular_promedio(notas)
    estado = determinar_estado(promedio)
    mensaje = formatear_resultado(nombre, promedio, estado)
    
    print(mensaje)
    return promedio
```

**Ventajas:**
1. **Testeo:** Cada función se puede probar independientemente
2. **Reutilización:** Funciones específicas son reutilizables
3. **Mantenimiento:** Cambios localizados en una función
4. **Comprensión:** Funciones simples son fáciles de entender

---

(0x000Dh)=
### Regla `0x000Dh`: Las condiciones complejas deben extraerse a variables booleanas descriptivas

**Principio:** Las expresiones booleanas complejas deben descomponerse en variables con nombres descriptivos para mejorar la legibilidad.

```python
# ❌ Difícil de leer
if (edad >= 18 and tiene_dni and not esta_inhabilitado) or (es_emancipado and tiene_autorizacion):
    permitir_acceso()
```

```python
# ✓ Más claro con variables booleanas
es_mayor_de_edad = edad >= 18
tiene_documentacion_valida = tiene_dni and not esta_inhabilitado
es_adulto_habilitado = es_mayor_de_edad and tiene_documentacion_valida

es_menor_autorizado = es_emancipado and tiene_autorizacion

puede_acceder = es_adulto_habilitado or es_menor_autorizado

if puede_acceder:
    permitir_acceso()
```

**O extraer a funciones:**

```python
# ✓ Aún mejor: extraer a funciones
def puede_acceder_como_adulto(edad, tiene_dni, esta_inhabilitado):
    """Verifica si puede acceder como adulto."""
    return edad >= 18 and tiene_dni and not esta_inhabilitado

def puede_acceder_como_menor(es_emancipado, tiene_autorizacion):
    """Verifica si puede acceder como menor emancipado."""
    return es_emancipado and tiene_autorizacion

def puede_acceder(edad, tiene_dni, esta_inhabilitado, es_emancipado, tiene_autorizacion):
    """Determina si una persona puede acceder."""
    return (puede_acceder_como_adulto(edad, tiene_dni, esta_inhabilitado) or
            puede_acceder_como_menor(es_emancipado, tiene_autorizacion))

if puede_acceder(edad, tiene_dni, esta_inhabilitado, es_emancipado, tiene_autorizacion):
    permitir_acceso()
```

---

(0x000Eh)=
### Regla `0x000Eh`: Usar constantes con nombres descriptivos en lugar de "números mágicos"

**Principio:** Los números literales en el código (excepto 0, 1, -1 en contextos obvios) deben ser reemplazados por constantes con nombres descriptivos.

```python
# ❌ Números mágicos
def calcular_impuesto(precio):
    return precio * 0.21

def validar_edad(edad):
    return 18 <= edad <= 120

# ✓ Usar constantes
IVA = 0.21
EDAD_MINIMA_LEGAL = 18
EDAD_MAXIMA_RAZONABLE = 120

def calcular_impuesto(precio):
    """Calcula el impuesto (IVA) sobre un precio."""
    return precio * IVA

def validar_edad(edad):
    """Valida que la edad esté en un rango razonable."""
    return EDAD_MINIMA_LEGAL <= edad <= EDAD_MAXIMA_RAZONABLE
```

**Convención:** Constantes en `MAYUSCULAS_CON_GUIONES_BAJOS`

```python
# Constantes al inicio del archivo o módulo
MAX_INTENTOS_LOGIN = 3
TIMEOUT_SEGUNDOS = 30
TAMAÑO_BUFFER = 1024
PI = 3.14159265359
DIAS_POR_SEMANA = 7
```

**Excepciones razonables:**
- 0, 1, -1 en contextos matemáticos obvios
- Índices de lista evidentes: `lista[0]`, `lista[-1]`
- Porcentajes cuando el contexto es claro: `nota * 0.4 + examen * 0.6`

---

(0x000Fh)=
### Regla `0x000Fh`: Limitar las líneas de código a 79 caracteres ({ref}`pep-8-ref`)

**Principio:** Las líneas no deben exceder 79 caracteres para facilitar la lectura y visualización en múltiples ventanas.

```python
# ❌ Línea demasiado larga
mensaje_muy_largo = f"Este es un mensaje extremadamente largo que definitivamente excede el límite de 79 caracteres establecido en PEP 8"

# ✓ Dividir en múltiples líneas
mensaje_muy_largo = (
    "Este es un mensaje extremadamente largo que definitivamente "
    "excede el límite de 79 caracteres establecido en PEP 8"
)
```

**Técnicas para líneas largas:**

```python
# Strings largos: concatenación implícita
mensaje = (
    "Primera parte del mensaje. "
    "Segunda parte del mensaje. "
    "Tercera parte del mensaje."
)

# Llamadas a funciones: múltiples líneas
resultado = funcion_con_nombre_largo(
    parametro1,
    parametro2,
    parametro3,
    parametro4
)

# Listas y diccionarios: un elemento por línea
lista_valores = [
    "valor1",
    "valor2",
    "valor3",
    "valor4",
]

diccionario = {
    "clave1": "valor1",
    "clave2": "valor2",
    "clave3": "valor3",
}

# Condiciones largas: usar paréntesis
if (condicion1 and condicion2 and
        condicion3 and condicion4):
    hacer_algo()

# O mejor: extraer a variables
condiciones_basicas = condicion1 and condicion2
condiciones_adicionales = condicion3 and condicion4

if condiciones_basicas and condiciones_adicionales:
    hacer_algo()
```

:::{note} Límites modernos
PEP 8 permite hasta 99 caracteres para comentarios y docstrings, pero recomienda 79 para código. Algunos equipos usan 88 o 100. En este curso, usamos 79 como estándar.
:::

---

(0x0010h)=
### Regla `0x0010h`: No comparar con `True`, `False` o `None` usando `==`

**Principio:** Usar comparadores de identidad (`is`, `is not`) para `None`, `True`, `False`, y evaluar directamente valores booleanos.

```python
# ❌ Incorrecto
if valor == True:
    hacer_algo()

if resultado == None:
    manejar_error()

if bandera == False:
    continuar()

# ✓ Correcto
if valor:  # Evaluar directamente
    hacer_algo()

if resultado is None:  # Usar 'is' para None
    manejar_error()

if not bandera:  # Negar con 'not'
    continuar()
```

**Razón:** `is` compara identidad (mismo objeto en memoria), mientras `==` compara valor. Para singletons como `None`, `True`, `False`, siempre usar `is`.

```python
# Comparaciones correctas
if valor is None:
    pass

if valor is not None:
    pass

# Para booleanos, evaluar directamente
if es_valido:  # No: if es_valido == True
    pass

if not es_valido:  # No: if es_valido == False
    pass
```

:::{tip} Valores "truthy" y "falsy"
Python considera "falsy": `False`, `None`, `0`, `0.0`, `""`, `[]`, `{}`, `set()`

Todos los demás valores son "truthy". Aprovechá esto:
```python
if lista:  # True si lista tiene elementos
    procesar(lista)

if nombre:  # True si nombre no está vacío
    saludar(nombre)
```
:::

---

---

(0x0011h)=
### Regla `0x0011h`: Mantener el alcance de las variables al mínimo posible

**Principio:** Las variables deben declararse en el ámbito más pequeño posible donde sean necesarias. Esto reduce confusión, facilita el debugging y hace el código más predecible.

```python
# ❌ Incorrecto: variable con alcance innecesariamente amplio
def procesar_datos():
    resultado = None  # Declarada muy arriba, sin uso inmediato
    contador = 0       # Alcance demasiado amplio
    # ... mucho código ...
    
    for i in range(100):
        resultado = calcular(i)
        contador += 1
    
    print(f"Procesados: {contador}")
    return resultado

# ✓ Correcto: alcance mínimo
def procesar_datos():
    # resultado se declara justo antes del loop donde se usa
    for i in range(100):
        resultado = calcular(i)
    
    # contador solo existe donde se necesita
    cantidad_procesada = 100  # O directamente usar el valor conocido
    print(f"Procesados: {cantidad_procesada}")
    
    return resultado
```

**Ventajas:**
1. Menos riesgo de reutilizar incorrectamente una variable
2. Más fácil identificar dónde se modifica una variable
3. El código es más claro sobre las dependencias

---

(0x0012h)=
### Regla `0x0012h`: Usar constantes o `None` para valores especiales

**Principio:** Los valores de retorno especiales (como -1 para "no encontrado") deben ser constantes con nombres descriptivos, o mejor aún, usar `None` cuando sea apropiado.

```python
# ❌ Incorrecto: número mágico
def buscar_elemento(lista, elemento):
    for i, item in enumerate(lista):
        if item == elemento:
            return i
    return -1  # ¿Qué significa -1? No es obvio

# ✓ Opción 1: Constante descriptiva
NO_ENCONTRADO = -1

def buscar_elemento(lista, elemento):
    """Busca un elemento en la lista. 
    
    Args:
        lista: Lista donde buscar
        elemento: Elemento a buscar
    
    Returns:
        int: Índice del elemento o NO_ENCONTRADO si no existe
    """
    for i, item in enumerate(lista):
        if item == elemento:
            return i
    return NO_ENCONTRADO

# ✓ Opción 2: Más Pythonic usando None
def buscar_elemento(lista, elemento):
    """Busca un elemento en la lista. 
    
    Args:
        lista: Lista donde buscar
        elemento: Elemento a buscar
    
    Returns:
        int or None: Índice del elemento o None si no se encuentra
    """
    for i, item in enumerate(lista):
        if item == elemento:
            return i
    return None

# Uso con None (más Pythonic)
indice = buscar_elemento([1, 2, 3], 5)
if indice is not None:
    print(f"Encontrado en posición {indice}")
else:
    print("No encontrado")
```

:::{note} ¿Cuándo usar None vs. constante?
- **Usar `None`:** Cuando representa ausencia de valor (más Pythonic)
- **Usar constante:** Cuando el valor especial tiene significado en el dominio del problema
:::

---

(0x0013h)=
### Regla `0x0013h`: Validar siempre las entradas del usuario

**Principio:** Nunca confiar en que el usuario ingresará datos válidos. Siempre validar tipo, rango y formato.

```python
# ❌ Incorrecto: sin validación (propenso a errores)
edad = int(input("Ingrese su edad: "))  # ValueError si no es número
anos_restantes = 100 - edad             # Valores negativos posibles

# ✓ Correcto: validación completa
def solicitar_edad():
    """Solicita y valida la edad del usuario. 
    
    Returns:
        int: Edad válida en rango [0, 150]
    """
    EDAD_MINIMA = 0
    EDAD_MAXIMA = 150
    
    while True:
        try:
            entrada = input("Ingrese su edad: ")
            edad = int(entrada)
            
            if edad < EDAD_MINIMA:
                print(f"Error: La edad no puede ser menor a {EDAD_MINIMA}.")
                continue
            
            if edad > EDAD_MAXIMA:
                print(f"Error: Edad fuera de rango válido (máximo {EDAD_MAXIMA}).")
                continue
            
            return edad
        
        except ValueError:
            print("Error: Debe ingresar un número entero válido.")

# Uso seguro
edad = solicitar_edad()
```

**Validaciones típicas:**
- **Tipo:** ¿Es un número, string, etc.?
- **Rango:** ¿Está dentro de valores aceptables?
- **Formato:** ¿Cumple con el patrón esperado? (emails, DNI, etc.)
- **Lógica:** ¿Tiene sentido en el contexto? (fecha de nacimiento no puede ser futura)

---

(0x0014h)=
### Regla `0x0014h`: Usar comprehensions solo cuando mejoren la legibilidad

**Principio:** Las list/dict comprehensions son poderosas y Pythonic, pero solo usarlas cuando hagan el código **más claro**, no más complejo.

```python
# ✓ Correcto: comprehensions simples y claras
cuadrados = [x ** 2 for x in range(10)]
pares = [x for x in numeros if x % 2 == 0]
mayusculas = [nombre.upper() for nombre in nombres]

# ✓ Correcto: dict comprehension
longitudes = {nombre: len(nombre) for nombre in nombres}

# ❌ Incorrecto: demasiado complejo (difícil de leer)
resultado = [
    x * 2 if x % 2 == 0 else x * 3
    for x in range(100)
    if x > 50 and x < 75
    if x % 3 == 0 or x % 5 == 0
]

# ✓ Correcto: loop explícito para lógica compleja
resultado = []
for x in range(100):
    # Filtro de rango
    if x > 50 and x < 75:
        # Filtro de divisibilidad
        if x % 3 == 0 or x % 5 == 0:
            # Transformación condicional
            if x % 2 == 0:
                resultado.append(x * 2)
            else:
                resultado.append(x * 3)
```

**Regla práctica:** Si tu comprehension necesita más de 79 caracteres o tiene más de 2 condiciones, probablemente sea mejor usar un loop explícito.

---

(0x0015h)=
### Regla `0x0015h`: Usar `with` para manejo de archivos

**Principio:** El context manager `with` garantiza que los recursos (archivos, conexiones, etc.) se cierren correctamente, incluso si ocurren errores.

```python
# ❌ Incorrecto: manejo manual (riesgo de no cerrar)
archivo = open('datos.txt', 'r')
contenido = archivo.read()
archivo.close()  # Se puede olvidar o no ejecutar si hay error

# ✓ Correcto: with garantiza el cierre automático
with open('datos.txt', 'r') as archivo:
    contenido = archivo.read()
# El archivo se cierra automáticamente aquí

# ✓ Múltiples archivos
with open('entrada.txt', 'r') as entrada, \
     open('salida.txt', 'w') as salida:
    for linea in entrada:
        salida.write(linea.upper())

# ✓ Escritura con with
with open('datos.txt', 'w') as archivo:
    archivo.write("Primera línea\n")
    archivo.write("Segunda línea\n")
```

**Ventajas del `with`:**
1. **Seguridad:** Garantiza cierre incluso si hay excepciones
2. **Limpieza:** No necesitás recordar cerrar manualmente
3. **Legibilidad:** El ámbito del recurso es explícito

:::{tip} Context managers más allá de archivos
El `with` funciona con cualquier "context manager". Más adelante verás otros usos como locks, conexiones a bases de datos, y transacciones.
:::

---

(0x0016h)=
### Regla `0x0016h`: Estructurar programas con funciones

**Principio:** Incluso en ejercicios simples, organizar el código en funciones mejora la claridad, testabilidad y reutilización.

```python
# ❌ Incorrecto: lógica suelta en programa principal
base = 10
altura = 5
area = base * altura
perimetro = 2 * (base + altura)
print(f"Área: {area}")
print(f"Perímetro: {perimetro}")

# ✓ Correcto: funciones con responsabilidades claras
def calcular_area_rectangulo(base, altura):
    """Calcula el área de un rectángulo. 
    
    Args:
        base: Longitud de la base
        altura: Altura del rectángulo
        
    Returns:
        float: Área calculada
    """
    return base * altura

def calcular_perimetro_rectangulo(base, altura):
    """Calcula el perímetro de un rectángulo. 
    
    Args:
        base: Longitud de la base
        altura: Altura del rectángulo
        
    Returns:
        float: Perímetro calculado
    """
    return 2 * (base + altura)

def main():
    """Función principal del programa."""
    base = 10
    altura = 5
    
    area = calcular_area_rectangulo(base, altura)
    perimetro = calcular_perimetro_rectangulo(base, altura)
    
    print(f"Área: {area}")
    print(f"Perímetro: {perimetro}")

if __name__ == "__main__":
    main()
```

**Estructura recomendada:**
```python
# 1. Imports (si hay)
import math

# 2. Constantes globales
PI = 3.14159

# 3. Funciones auxiliares
def funcion_auxiliar():
    pass

# 4. Función principal
def main():
    pass

# 5. Punto de entrada
if __name__ == "__main__":
    main()
```

---

(0x0017h)=
### Regla `0x0017h`: Usar operador `in` para pertenencia

**Principio:** Python tiene operadores poderosos para verificar pertenencia. Usarlos en lugar de loops manuales hace el código más Pythonic y eficiente.

```python
# ❌ Incorrecto: búsqueda manual
encontrado = False
for elemento in lista:
    if elemento == objetivo:
        encontrado = True
        break

if encontrado:
    print("Encontrado")

# ✓ Correcto: usar 'in' (más claro y eficiente)
if objetivo in lista:
    print("Encontrado")

# ✓ Para strings
if 'Python' in mensaje:
    print("El mensaje menciona Python")

if mensaje.startswith('Hola'):
    print("El mensaje es un saludo")

# ✓ Para diccionarios (verifica claves por defecto)
if 'nombre' in diccionario:
    print(f"Nombre: {diccionario['nombre']}")

# ✓ Para verificar valores en diccionario
if 'Ana' in diccionario.values():
    print("Ana está entre los valores")

# ✓ not in
if objetivo not in lista_prohibidos:
    procesar(objetivo)
```

**Ventajas:**
- Más legible y conciso
- Más eficiente (implementación en C)
- Menos propenso a errores (no olvidar el `break`)

---

(0x0018h)=
### Regla `0x0018h`: Usar `enumerate()` en lugar de `range(len())`

**Principio:** Cuando necesitás el índice y el elemento, `enumerate()` es más Pythonic y menos propenso a errores que usar `range(len())`.

```python
nombres = ['Ana', 'Luis', 'Carlos']

# ❌ Incorrecto: range(len()) es anti-Pythonic
for i in range(len(nombres)):
    print(f"{i}: {nombres[i]}")

# ✓ Correcto: usar enumerate()
for i, nombre in enumerate(nombres):
    print(f"{i}: {nombre}")

# ✓ Con índice inicial personalizado
for i, nombre in enumerate(nombres, start=1):
    print(f"{i}. {nombre}")  # Numeración desde 1

# ✓ Ejemplo práctico: procesar con índice
for i, linea in enumerate(archivo):
    if i == 0:
        continue  # Saltar encabezado
    procesar_linea(linea)
```

**¿Por qué `enumerate()` es mejor?**
1. Más legible: la intención es clara
2. Menos errores: no hay riesgo de indexar incorrectamente
3. Más eficiente: evita llamadas repetidas a `len()`
4. Más Pythonic: aprovecha las características del lenguaje

---

(0x0019h)=
### Regla `0x0019h`: Usar `zip()` para iterar múltiples secuencias

**Principio:** Cuando necesitás iterar sobre múltiples listas en paralelo, `zip()` es la forma Pythonic de hacerlo.

```python
nombres = ['Ana', 'Luis', 'Carlos']
edades = [25, 30, 28]
ciudades = ['Buenos Aires', 'Córdoba', 'Rosario']

# ❌ Incorrecto: índices manuales
for i in range(len(nombres)):
    print(f"{nombres[i]} tiene {edades[i]} años y vive en {ciudades[i]}")

# ✓ Correcto: usar zip()
for nombre, edad, ciudad in zip(nombres, edades, ciudades):
    print(f"{nombre} tiene {edad} años y vive en {ciudad}")

# ✓ Con enumerate si también necesitás el índice
for i, (nombre, edad) in enumerate(zip(nombres, edades), start=1):
    print(f"{i}. {nombre}: {edad} años")

# ✓ zip trunca a la lista más corta
lista1 = [1, 2, 3, 4, 5]
lista2 = ['a', 'b', 'c']
for num, letra in zip(lista1, lista2):
    print(num, letra)
# Solo imprime 3 pares
```

:::{tip} zip para crear diccionarios
```python
claves = ['nombre', 'edad', 'ciudad']
valores = ['Ana', 25, 'Buenos Aires']
diccionario = dict(zip(claves, valores))
# {'nombre': 'Ana', 'edad': 25, 'ciudad': 'Buenos Aires'}
```
:::

---

(0x001Ah)=
### Regla `0x001Ah`: Usar f-strings para formateo (Python 3.6+)

**Principio:** Las f-strings son la forma moderna, legible y eficiente de formatear strings en Python.

```python
nombre = "Ana"
edad = 25
altura = 1.68

# ❌ Antiguo: concatenación (evitar)
mensaje = "Hola, me llamo " + nombre + " y tengo " + str(edad) + " años"

# ❌ Antiguo: format() (funciona pero menos legible)
mensaje = "Hola, me llamo {} y tengo {} años".format(nombre, edad)

# ✓ Moderno: f-strings (preferido)
mensaje = f"Hola, me llamo {nombre} y tengo {edad} años"

# ✓ Con expresiones
mensaje = f"El próximo año tendré {edad + 1} años"
mensaje = f"Mi nombre tiene {len(nombre)} letras"

# ✓ Con formato numérico
precio = 19.99
mensaje = f"Precio: ${precio:.2f}"  # $19.99

pi = 3.14159265359
mensaje = f"π ≈ {pi:.4f}"  # π ≈ 3.1416

# ✓ Con alineación
for i in range(1, 11):
    cuadrado = i ** 2
    cubo = i ** 3
    print(f"{i:2d} | {cuadrado:3d} | {cubo:4d}")
# Tabla alineada

# ✓ Con expresiones complejas
estudiantes = ['Ana', 'Luis', 'Carlos']
mensaje = f"Hay {len(estudiantes)} estudiantes: {', '.join(estudiantes)}"
```

**Especificadores de formato útiles:**
```python
numero = 42
print(f"{numero:05d}")    # 00042 (relleno con ceros)
print(f"{numero:>10}")    # "        42" (alineado derecha)
print(f"{numero:<10}")    # "42        " (alineado izquierda)
print(f"{numero:^10}")    # "    42    " (centrado)

porcentaje = 0.859
print(f"{porcentaje:.1%}") # 85.9%

numero_grande = 1000000
print(f"{numero_grande:,}") # 1,000,000
```

---

(0x001Bh)=
### Regla `0x001Bh`: Type hints para documentación (opcional, progresivo)

**Principio:** Los type hints mejoran la documentación del código y permiten detección temprana de errores. Se introducen progresivamente en el curso.

```python
# Sin type hints (principiantes - módulos 1-3)
def sumar(a, b):
    """Suma dos números."""
    return a + b

# ✓ Con type hints (intermedio - módulo 4+)
def sumar(a: int, b: int) -> int:
    """Suma dos números enteros. 
    
    Args:
        a: Primer número
        b: Segundo número
        
    Returns:
        La suma de a y b
    """
    return a + b

# ✓ Tipos más complejos (avanzado - módulos 5-6)
from typing import List, Dict, Optional, Union

def procesar_nombres(nombres: List[str]) -> Dict[str, int]:
    """Cuenta la longitud de cada nombre. 
    
    Args:
        nombres: Lista de nombres a procesar
        
    Returns:
        Diccionario {nombre: longitud}
    """
    return {nombre: len(nombre) for nombre in nombres}

def buscar_elemento(lista: List[int], elemento: int) -> Optional[int]:
    """Busca un elemento en la lista. 
    
    Args:
        lista: Lista donde buscar
        elemento: Elemento a buscar
        
    Returns:
        Índice del elemento o None si no se encuentra
    """
    for i, item in enumerate(lista):
        if item == elemento:
            return i
    return None

# ✓ Union types
def convertir_a_entero(valor: Union[str, int, float]) -> int:
    """Convierte un valor a entero."""
    return int(valor)
```

:::{note} Type hints en este curso
Los type hints se introducen **gradualmente**:
- **Módulos 1-3:** Sin type hints (enfoque en lógica)
- **Módulo 4:** Introducción básica (int, str, float, bool)
- **Módulos 5-6:** Types complejos (List, Dict, Optional)
:::

---

(0x001Ch)=
### Regla `0x001Ch`: Acceso seguro a diccionarios con `get()`

**Principio:** Usar `dict.get()` en lugar de acceso directo previene errores `KeyError` y hace el código más robusto.

```python
usuario = {'nombre': 'Ana', 'edad': 25}

# ❌ Incorrecto: acceso directo (puede fallar)
ciudad = usuario['ciudad']  # KeyError: 'ciudad'

# ✓ Correcto: get() retorna None si no existe
ciudad = usuario.get('ciudad')
if ciudad is None:
    print("Ciudad no especificada")

# ✓ Mejor: get() con valor por defecto
ciudad = usuario.get('ciudad', 'Desconocida')
print(f"Ciudad: {ciudad}")  # Ciudad: Desconocida

# ✓ Uso práctico en validación
config = {
    'debug': True,
    'timeout': 30
}

modo_debug = config.get('debug', False)
timeout = config.get('timeout', 60)
max_intentos = config.get('max_intentos', 3)  # Usa default si no está

# ✓ vs try/except (get es más limpio para casos simples)
# Menos Pythonic:
try:
    ciudad = usuario['ciudad']
except KeyError:
    ciudad = 'Desconocida'

# Más Pythonic:
ciudad = usuario.get('ciudad', 'Desconocida')
```

---

(0x001Dh)=
### Regla `0x001Dh`: Comentarios explican "por qué", no "qué"

**Principio:** El código debe ser autoexplicativo (el "qué"). Los comentarios deben explicar el razonamiento (el "por qué").

```python
# ❌ Incorrecto: comentarios obvios
i += 1  # Incrementa i en 1
x = x * 2  # Multiplica x por 2
lista.append(elemento)  # Agrega elemento a la lista

# ✓ Correcto: comentarios explican intención
i += 1  # Saltamos el encabezado para procesar solo datos

# Factor de conversión específico del sensor modelo X200
factor = 2.54

# Duplicamos el valor porque el protocolo espera unidades en centímetros
valor_cm = valor_pulgadas * factor

# ✓ Los docstrings explican QUÉ hace la función
def calcular_factorial(n):
    """Calcula el factorial de n recursivamente. 
    
    Args:
        n: Número entero no negativo
        
    Returns:
        El factorial de n
    """
    # Caso base: necesario para detener la recursión
    if n <= 1:
        return 1
    # Caso recursivo: n! = n * (n-1)!
    return n * calcular_factorial(n - 1)

# ✓ Comentarios para decisiones de diseño
# Usamos búsqueda binaria en lugar de lineal porque
# la lista está ordenada y puede contener millones de elementos
resultado = busqueda_binaria(lista, objetivo)

# Caché de resultados: mejora significativa de performance
# para inputs repetidos en benchmark (50% más rápido)
cache = {}
```

**Reglas para buenos comentarios:**
1. Explicar decisiones de diseño
2. Aclarar algoritmos complejos
3. Advertir sobre casos especiales
4. Referenciar documentación externa
5. Explicar "TODO" y limitaciones conocidas

---

(0x001Eh)=
### Regla `0x001Eh`: Aprovechar métodos de string

**Principio:** Python tiene métodos de string muy poderosos. Conocerlos y usarlos hace el código más limpio y eficiente.

```python
texto = "  Hola Mundo  "

# ✓ Limpieza
texto.strip()        # "Hola Mundo" (elimina espacios)
texto.lstrip()       # "Hola Mundo  " (elimina izquierda)
texto.rstrip()       # "  Hola Mundo" (elimina derecha)

# ✓ Conversión de caso
texto.lower()        # "  hola mundo  "
texto.upper()        # "  HOLA MUNDO  "
texto.title()        # "  Hola Mundo  "
texto.capitalize()   # "  hola mundo  "

# ✓ Búsqueda
texto.startswith(" ")     # True
texto.endswith("  ")      # True
texto.find("Mundo")       # 8 (índice)
"Mundo" in texto          # True (preferir esto)

# ✓ Reemplazo
texto.replace("o", "0")   # "  H0la Mund0  "
texto.replace(" ", "")    # "HolaMundo"

# ✓ División y unión (MUY IMPORTANTE)
palabras = "Hola,Mundo,Python".split(",")  # ['Hola', 'Mundo', 'Python']
palabras = texto.split()                    # ['Hola', 'Mundo']
unido = "-".join(palabras)                  # 'Hola-Mundo'
ruta = "/".join(['usr', 'local', 'bin'])   # 'usr/local/bin'

# ✓ Validación (MUY ÚTIL)
"123".isdigit()      # True
"abc".isalpha()      # True
"abc123".isalnum()   # True
"   ".isspace()      # True
"Hello".isupper()    # False
"hello".islower()    # True

# ✓ Relleno y alineación
"42".zfill(5)        # "00042"
"texto".center(10)   # "  texto   "
"texto".ljust(10)    # "texto     "
"texto".rjust(10)    # "     texto"

# ✓ Ejemplo práctico: validación de DNI
def validar_dni(dni_str):
    """Valida formato de DNI argentino."""
    dni_limpio = dni_str.replace(".", "").replace("-", "").strip()
    return dni_limpio.isdigit() and 1000000 <= int(dni_limpio) <= 99999999
```

---

(0x001Fh)=
### Regla `0x001Fh`: Nunca usar mutables como argumentos por defecto

**Principio:** Los valores mutables (listas, diccionarios) como defaults se evalúan **una sola vez** cuando se define la función, causando bugs sutiles.

```python
# ❌ ERROR COMÚN: lista mutable como default
def agregar_alumno(nombre, lista_alumnos=[]):
    """INCORRECTO: lista_alumnos se comparte entre llamadas."""
    lista_alumnos.append(nombre)
    return lista_alumnos

# Comportamiento inesperado:
lista1 = agregar_alumno("Ana")     # ['Ana']
lista2 = agregar_alumno("Luis")    # ['Ana', 'Luis'] - ¡Inesperado!
lista3 = agregar_alumno("Carlos")  # ['Ana', 'Luis', 'Carlos']
# ¡Todas las listas son el mismo objeto!

# ✓ Correcto: usar None e inicializar dentro
def agregar_alumno(nombre, lista_alumnos=None):
    """Agrega un alumno a la lista."""
    if lista_alumnos is None:
        lista_alumnos = []  # Nueva lista cada vez
    lista_alumnos.append(nombre)
    return lista_alumnos

# Ahora funciona correctamente:
lista1 = agregar_alumno("Ana")     # ['Ana']
lista2 = agregar_alumno("Luis")    # ['Luis']
lista3 = agregar_alumno("Carlos")  # ['Carlos']

# ✓ Similar para diccionarios
def crear_config(opciones=None):
    """Crea configuración con opciones personalizadas."""
    if opciones is None:
        opciones = {}
    # Agregar opciones por defecto
    opciones.setdefault('debug', False)
    opciones.setdefault('timeout', 30)
    return opciones
```

**¿Por qué pasa esto?**
```python
def funcion_problema(lista=[]):
    pass

# El [] se crea UNA VEZ cuando Python lee la definición
# Todas las llamadas usan el mismo objeto lista
```

:::{danger} Otros mutables a evitar como defaults
- Listas: `[]`
- Diccionarios: `{}`
- Sets: `set()`
- Objetos custom mutables

**Siempre usar `None` y crear dentro de la función.**
:::

---

## Resumen de Convenciones PEP 8

### Nomenclatura

| Elemento | Convención | Ejemplo |
|----------|------------|---------|
| Variables | `snake_case` | `edad_usuario` |
| Funciones | `snake_case` | `calcular_impuesto()` |
| Constantes | `MAYUSCULAS` | `PI`, `MAX_INTENTOS` |
| Clases | `PascalCase` | `CalculadoraImpuestos` |
| Módulos | `snake_case` | `utilidades.py` |
| Privados | `_nombre` | `_variable_interna` |

### Formato

- **Indentación**: 4 espacios (nunca tabs)
- **Longitud**: Máximo 79 caracteres
- **Espacios**: Alrededor de operadores
- **Imports**: Al inicio, ordenados

---

## Herramientas

### Black (Formateador)
```bash
pip install black
black mi_script.py
```

### Flake8 (Linter)
```bash
pip install flake8
flake8 mi_script.py
```

### MyPy (Type Checker)
```bash
pip install mypy
mypy mi_script.py
```

---

## Conclusión

Estas reglas están basadas en décadas de experiencia de la comunidad Python. Seguirlas te hará:

1. **Más productivo**: Código claro es fácil de mantener
2. **Mejor colaborador**: Otros entenderán tu código
3. **Más profesional**: Calidad refleja profesionalismo
4. **Menos propenso a errores**: Buen estilo previene bugs

Recordá el Zen de Python:

> **Beautiful is better than ugly.**  
> **Explicit is better than implicit.**  
> **Simple is better than complex.**  
> **Readability counts.**

---

## Referencias

### Python Enhancement Proposals (PEPs)

Los PEPs son la documentación oficial que define las mejores prácticas y estándares de Python:

(pep-8-ref)=
- **[PEP 8 - Style Guide for Python Code](https://peps.python.org/pep-0008/)**: La guía de estilo oficial y más importante de Python. Define convenciones para la escritura de código Python legible y consistente.

(pep-20-ref)=
- **[PEP 20 - The Zen of Python](https://peps.python.org/pep-0020/)**: Los principios filosóficos de diseño de Python. Podés verlo ejecutando `import this` en el intérprete de Python.

(pep-257-ref)=
- **[PEP 257 - Docstring Conventions](https://peps.python.org/pep-0257/)**: Convenciones para escribir docstrings, la documentación integrada en el código Python.

- **[PEP 0 - Index of Python Enhancement Proposals](https://peps.python.org/)**: Índice completo de todos los PEPs.

### Guías de Estilo Adicionales

- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html): Guía de estilo de Google para Python, con extensiones prácticas sobre PEP 8.
- [Real Python - Python Code Quality](https://realpython.com/python-code-quality/): Tutoriales y recursos sobre calidad de código.

### Herramientas

- [Black](https://black.readthedocs.io/): Formateador automático de código Python.
- [Flake8](https://flake8.pycqa.org/): Herramienta de linting para verificar el cumplimiento de PEP 8.
- [MyPy](https://mypy.readthedocs.io/): Verificador de tipos estáticos para Python.