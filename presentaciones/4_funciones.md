---
marp: true
theme: default
paginate: true
header: 'Funciones en Python'
footer: 'Definición, parámetros, scope y buenas prácticas'
style: |
  section {
    font-size: 26px;
  }
  h1 {
    color: #1976d2;
  }
  code {
    background-color: #f5f5f5;
  }
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Funciones en Python

**Definición, parámetros, scope, documentación y buenas prácticas**

---

## ¿Qué vas a aprender?

* Definir y llamar funciones para **reutilizar código**
* Trabajar con **parámetros y argumentos**
* **Retornar valores** y usarlos en tu programa
* Entender el **scope** (alcance) de las variables
* **Documentar funciones** profesionalmente
* Aplicar **buenas prácticas** en el diseño
* **Descomponer problemas** complejos en funciones simples

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

---

<!-- _class: lead -->

# Definir y Llamar Funciones

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

---

<!-- _class: lead -->

# Parámetros y Argumentos

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

---

<!-- _class: lead -->

# Retornar Valores

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

---

<!-- _class: lead -->

# Scope (Alcance) de Variables

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

---

<!-- _class: lead -->

# Parámetros por Defecto

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

---

<!-- _class: lead -->

# Número Variable de Argumentos

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

---

<!-- _class: lead -->

# Funciones Lambda

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

---

<!-- _class: lead -->

# Documentación de Funciones

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

---

<!-- _class: lead -->

# Buenas Prácticas

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

---

<!-- _class: lead -->

# Errores Comunes

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

---

<!-- _class: lead -->

# Descomposición Funcional

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

---

<!-- _class: lead -->

# Resumen

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

---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Las funciones son la base de la programación modular y reutilizable.

Dominá estos conceptos y podrás escribir código profesional, limpio y mantenible.

**Recordá:** Una función bien escrita es una función que otro programador (o vos en 6 meses) puede entender fácilmente.
