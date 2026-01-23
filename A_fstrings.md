---
title: Guía Completa de F-Strings en Python
short_title: A - F-Strings
subtitle: Dominando la creación moderna de cadenas en Python
---

## Introducción

Las **f-strings** (formatted string literals) son la forma moderna, elegante y poderosa de trabajar con texto en Python. Introducidas en Python 3.6, simplifican la manera en que creamos cadenas de texto, haciéndolo más legible, intuitivo y eficiente.

:::{note} ¿Qué es una f-string?
Una **f-string** es una {term}`cadena` que comienza con la letra `f` o `F` antes de las comillas, y permite incluir {term}`expresiones <Expresión>` de Python dentro de llaves `{}` que se evalúan en {term}`tiempo de ejecución`.

```python
nombre = "Ana"
edad = 25
mensaje = f"Me llamo {nombre} y tengo {edad} años"
```
:::

### ¿Por qué f-strings?

Antes de las f-strings, teníamos otras formas menos elegantes de crear cadenas. Aunque su uso no es *técnicamente* un error, son más engorrosas y menos legibles.

Este listado está únicamente para que veas las diferencias, ya que no se recomienda su uso en código nuevo.

#### Método clásico: Concatenación
```python
nombre = "Ana"
edad = 25

# Difícil de leer, propenso a errores
mensaje = "Me llamo " + nombre + " y tengo " + str(edad) + " años"
```

**Problemas:**
- Difícil de leer.
- Hay que convertir tipos manualmente ({term}`cast`).
- Muchos `+` que confunden.

#### Método `.format()`
```python
nombre = "Ana"
edad = 25

# Menos legible, separado del texto
mensaje = "Me llamo {} y tengo {} años".format(nombre, edad)
```

**Problemas:**
- Variables separadas del texto.
- Menos intuitivo.
- Más extenso.

#### Método `%` (más antiguo)
```python
nombre = "Ana"
edad = 25

# Sintaxis antigua tipo C
mensaje = "Me llamo %s y tengo %d años" % (nombre, edad)
```

**Problemas:**
- Sintaxis confusa.
- Difícil de mantener.
- Heredado de C.

#### Método Moderno: F-Strings
```python
nombre = "Ana"
edad = 25

# ¡Claro y directo!
mensaje = f"Me llamo {nombre} y tengo {edad} años"
```

**Ventajas:**
- Súper legible.
- Conversión automática de tipos.
- Más rápido.
- Menos código.


:::{important} Regla de Oro
**Siempre usá f-strings** para formatear cadenas en Python 3.6+. Es la forma recomendada por la comunidad Python y está documentada en la regla de estilo {ref}`0x0017h`.
:::

---

## Sintaxis Básica

### Estructura Fundamental

La anatomía de una f-string es simple:

```{figure} 8/fstring_anatomia.svg
:label: fig-fstring-anatomia
:align: center
:width: 90%

Anatomía de una f-string: prefijo f, comillas, expresiones entre llaves
```

```python
f"Texto literal {expresion_python} más texto"
│  └─────────────┘ └──────────────┘ └────────┘
│        │                │             │
│        │                │             └─ Texto normal
│        │                └─────────────── Expresión evaluada
│        └────────────────────────────── Texto literal
└─────────────────────────────────────── Prefijo 'f' (requerido)
```

### Primeros Pasos

#### Variables Simples

```python
nombre = "Carlos"
edad = 30
ciudad = "Bariloche"

# Insertar variables directamente
print(f"Hola, soy {nombre}")                    # Hola, soy Carlos
print(f"Tengo {edad} años")                     # Tengo 30 años
print(f"Vivo en {ciudad}")                      # Vivo en Bariloche
print(f"{nombre} tiene {edad} años")            # Carlos tiene 30 años
```

:::{tip} Conversión Automática
Las f-strings **convierten automáticamente** cualquier {term}`tipo de dato` a string. No hace falta usar `str()`:

```python
edad = 25           # int
altura = 1.75       # float
activo = True       # bool

print(f"Edad: {edad}")          # Funciona ✓
print(f"Altura: {altura}")      # Funciona ✓
print(f"Activo: {activo}")      # Funciona ✓
```
:::

#### Expresiones Matemáticas

Podés poner **cualquier expresión** de Python dentro de las llaves:

```python
x = 10
y = 5

print(f"Suma: {x + y}")                    # Suma: 15
print(f"Resta: {x - y}")                   # Resta: 5
print(f"Multiplicación: {x * y}")          # Multiplicación: 50
print(f"División: {x / y}")                # División: 2.0
print(f"Potencia: {x ** 2}")               # Potencia: 100
```

**Expresiones más complejas:**

```python
edad = 25
print(f"El año que viene tendré {edad + 1} años")
# El año que viene tendré 26 años

precio = 100
descuento = 0.15
print(f"Precio final: ${precio * (1 - descuento)}")
# Precio final: $85.0

nota = 7.5
print(f"¿Aprobó?: {nota >= 6}")
# ¿Aprobó?: True
```

#### Llamadas a Funciones

Las f-strings pueden ejecutar {term}`funciones <Función>`:

```python
nombre = "  PYTHON  "

print(f"Original: '{nombre}'")                    # Original: '  PYTHON  '
print(f"Minúsculas: '{nombre.lower()}'")          # Minúsculas: '  python  '
print(f"Sin espacios: '{nombre.strip()}'")        # Sin espacios: 'PYTHON'
print(f"Limpio y bonito: '{nombre.strip().title()}'")  # Limpio y bonito: 'Python'

# Con funciones built-in
numeros = [1, 2, 3, 4, 5]
print(f"Suma: {sum(numeros)}")                    # Suma: 15
print(f"Cantidad: {len(numeros)}")                # Cantidad: 5
print(f"Máximo: {max(numeros)}")                  # Máximo: 5
```

---

## Formateo de Números

Las f-strings tienen un sistema poderoso para formatear números con precisión.

### Números Decimales

La sintaxis para controlar decimales es: `{valor:.Nf}` donde `N` es la cantidad de decimales.

```python
pi = 3.141592653589793

print(f"Sin formato: {pi}")              # Sin formato: 3.141592653589793
print(f"2 decimales: {pi:.2f}")          # 2 decimales: 3.14
print(f"4 decimales: {pi:.4f}")          # 4 decimales: 3.1416
print(f"6 decimales: {pi:.6f}")          # 6 decimales: 3.141593
print(f"0 decimales: {pi:.0f}")          # 0 decimales: 3
```

**Ejemplos prácticos:**

```python
# Precios
precio = 19.9
print(f"Precio: ${precio:.2f}")                   # Precio: $19.90

# Porcentajes
tasa = 0.157
print(f"Tasa de interés: {tasa:.1%}")             # Tasa de interés: 15.7%

# Promedios
notas = [7.5, 8.2, 6.9, 9.1]
promedio = sum(notas) / len(notas)
print(f"Promedio: {promedio:.2f}")                # Promedio: 7.92
```

:::{warning} Redondeo vs. Truncado
El formato `.Nf` **redondea**, no trunca:

```python
valor = 3.14159

print(f"{valor:.2f}")    # 3.14 (redondea hacia abajo)
print(f"{valor:.3f}")    # 3.142 (redondea hacia arriba)
print(f"{valor:.4f}")    # 3.1416 (redondea hacia arriba)
```
:::

### Separadores de Miles

Para números grandes, usá comas como separador:

```python
poblacion = 45000000
print(f"Argentina: {poblacion:,} habitantes")
# Argentina: 45,000,000 habitantes

presupuesto = 1500000.50
print(f"Presupuesto: ${presupuesto:,.2f}")
# Presupuesto: $1,500,000.50

distancia = 149597870700  # Distancia Tierra-Sol en metros
print(f"Distancia Tierra-Sol: {distancia:,} m")
# Distancia Tierra-Sol: 149,597,870,700 m
```

:::{note} Separador Regional
El separador por defecto es la coma (`,`). En algunos países se usa el punto. Python respeta el separador estándar estadounidense.
:::

### Notación Científica

Para números muy grandes o muy pequeños:

```python
velocidad_luz = 299792458  # m/s
print(f"Velocidad de la luz: {velocidad_luz:e}")
# Velocidad de la luz: 2.997925e+08

masa_electron = 0.00000000000000000000000000000091093837  # kg
print(f"Masa del electrón: {masa_electron:.2e}")
# Masa del electrón: 9.11e-31

# Controlar decimales en notación científica
avogadro = 602214076000000000000000
print(f"Número de Avogadro: {avogadro:.3e}")
# Número de Avogadro: 6.022e+23
```

### Números Binarios, Octales y Hexadecimales

```python
numero = 42

print(f"Decimal: {numero}")               # Decimal: 42
print(f"Binario: {numero:b}")             # Binario: 101010
print(f"Octal: {numero:o}")               # Octal: 52
print(f"Hexadecimal: {numero:x}")         # Hexadecimal: 2a
print(f"Hexadecimal (mayúsculas): {numero:X}")  # Hexadecimal (mayúsculas): 2A

# Con prefijos
print(f"Binario: {numero:#b}")            # Binario: 0b101010
print(f"Octal: {numero:#o}")              # Octal: 0o52
print(f"Hexadecimal: {numero:#x}")        # Hexadecimal: 0x2a
```

### Porcentajes

```python
aprobados = 45
total = 50
tasa = aprobados / total

print(f"Aprobaron: {tasa:.0%}")                   # Aprobaron: 90%
print(f"Tasa de aprobación: {tasa:.1%}")          # Tasa de aprobación: 90.0%
print(f"Porcentaje exacto: {tasa:.2%}")           # Porcentaje exacto: 90.00%

# Automáticamente multiplica por 100
descuento = 0.15
print(f"Descuento: {descuento:%}")                # Descuento: 15.000000%
print(f"Descuento: {descuento:.0%}")              # Descuento: 15%
```

---

## Alineación y Espaciado

Podés controlar cómo se alinea el texto dentro de un ancho específico.

### Alineación Básica

```python
texto = "Python"

print(f"|{texto:<20}|")    # Izquierda   |Python              |
print(f"|{texto:>20}|")    # Derecha     |              Python|
print(f"|{texto:^20}|")    # Centro      |       Python       |
```

**Sintaxis:**
- `<`: Alinear a la izquierda.
- `>`: Alinear a la derecha.
- `^`: Centrar.

### Alineación con Números

```python
#Tabla de productos
productos = [
    ("Manzana", 2.50, 10),
    ("Banana", 1.20, 25),
    ("Naranja", 3.00, 15),
]

print("Producto       Precio   Cantidad")
print("-" * 35)
for nombre, precio, cantidad in productos:
    print(f"{nombre:<12} ${precio:>6.2f}  {cantidad:>8}")

# Salida:
# Producto       Precio   Cantidad
# -----------------------------------
# Manzana       $  2.50        10
# Banana        $  1.20        25
# Naranja       $  3.00        15
```

### Rellenar con Caracteres

Podés elegir qué carácter usar para rellenar:

```python
numero = 42

print(f"{numero:0>5}")     # 00042 (rellena con ceros a la derecha)
print(f"{numero:*^10}")    # ****42**** (rellena con * y centra)
print(f"{numero:.>8}")     # ......42 (rellena con puntos)

# Títulos decorados
titulo = "PYTHON"
print(f"{titulo:=^30}")    # ============PYTHON============
print(f"{titulo:*^30}")    # ************PYTHON************
```

### Casos de Uso Prácticos

#### Tabla Alineada

```python
# Tabla de multiplicar del 7
numero = 7
print(f"Tabla del {numero}")
print("=" * 20)

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero:2d} × {i:2d} = {resultado:3d}")

# Salida:
#  7 ×  1 =   7
#  7 ×  2 =  14
#  7 ×  3 =  21
# ...
#  7 × 10 =  70
```

#### Reporte de Notas

```python
estudiantes = [
    ("Ana García", 8.5, 9.0, 7.5),
    ("Juan Pérez", 7.0, 8.5, 9.0),
    ("María López", 9.5, 9.5, 10.0),
]

print("Reporte de Calificaciones")
print("=" * 55)
print(f"{ 'Estudiante':<20} {'Parcial 1':>10} {'Parcial 2':>10} {'Final':>10}")
print("-" * 55)

for nombre, p1, p2, final in estudiantes:
    promedio = (p1 + p2 + final) / 3
    print(f"{nombre:<20} {p1:>10.1f} {p2:>10.1f} {final:>10.1f}")

print("=" * 55)

# Salida perfectamente alineada
```

---

## Expresiones Complejas

Las f-strings pueden contener expresiones Python arbitrarias.

### Condicionales (Operador Ternario)

```python
edad = 20
print(f"Es {'mayor' if edad >= 18 else 'menor'} de edad")
# Es mayor de edad

nota = 7
print(f"Estado: {'Aprobado ✓' if nota >= 6 else 'Desaprobado ✗'}")
# Estado: Aprobado ✓

temperatura = 30
print(f"Clima: {'calor 🥵' if temperatura > 25 else 'frío 🥶'}")
# Clima: calor 🥵
```

### Listas y Diccionarios

```python
# Acceder a elementos de listas
frutas = ["🍎 manzana", "🍌 banana", "🍊 naranja"]
print(f"Primera fruta: {frutas[0]}")              # Primera fruta: 🍎 manzana
print(f"Última fruta: {frutas[-1]}")              # Última fruta: 🍊 naranja
print(f"Cantidad: {len(frutas)}")                 # Cantidad: 3

# Acceder a elementos de diccionarios
persona = {"nombre": "Ana", "edad": 25, "ciudad": "Mendoza"}
print(f"Nombre: {persona['nombre']}")             # Nombre: Ana
print(f"Edad: {persona['edad']}")                 # Edad: 25
print(f"Vive en {persona['ciudad']}")             # Vive en Mendoza
```

### Comprensiones de Listas

```python
numeros = [1, 2, 3, 4, 5]

print(f"Cuadrados: {[n**2 for n in numeros]}")
# Cuadrados: [1, 4, 9, 16, 25]

print(f"Pares: {[n for n in numeros if n % 2 == 0]}")
# Pares: [2, 4]

# Suma con comprensión
print(f"Suma de cuadrados: {sum([n**2 for n in numeros])}")
# Suma de cuadrados: 55
```

### Llamadas a Métodos Encadenadas

```python
texto = "  hola MUNDO  "

print(f"Procesado: '{texto.strip().title()}'")
# Procesado: 'Hola Mundo'

nombre_archivo = "DOCUMENTO.TXT"
print(f"Limpio: {nombre_archivo.lower().replace('.txt', '.pdf')}")
# Limpio: documento.pdf
```

### Operaciones con Strings

```python
nombre = "Ana María"
apellido = "González"

print(f"Iniciales: {nombre[0]}.{apellido[0]}.")
# Iniciales: A.G.

print(f"Nombre completo: {nombre + ' ' + apellido}")
# Nombre completo: Ana María González

print(f"Longitud total: {len(nombre) + len(apellido)} caracteres")
# Longitud total: 17 caracteres
```

---

## Caracteres Especiales

### Comillas Dentro de F-Strings

Podés mezclar comillas simples y dobles:

```python
nombre = "Ana"

# Comillas simples en el f-string, dobles dentro
mensaje = f'Ella dijo: "Hola, soy {nombre}"'
print(mensaje)  # Ella dijo: "Hola, soy Ana"

# Comillas dobles en el f-string, simples dentro
mensaje = f"Ella dijo: 'Hola, soy {nombre}'"
print(mensaje)  # Ella dijo: 'Hola, soy Ana'

# Escapar comillas
mensaje = f"Ella dijo: \"{nombre}\""
print(mensaje)  # Ella dijo: "Hola, soy Ana"
```

### Llaves Literales

Si necesitás imprimir llaves literales `{}`, duplicalas:

```python
print(f"Para incluir llaves, usá {{}} así")
# Para incluir llaves, usá {} así

variable = "ejemplo"
print(f"Sintaxis: f\"{{variable}}\" → {variable}")
# Sintaxis: f"{variable}" → ejemplo
```

### Saltos de Línea y Tabulaciones

```python
nombre = "Python"
version = "3.12"

# Salto de línea con \n
print(f"Lenguaje: {nombre}\nVersión: {version}")
# Lenguaje: Python
# Versión: 3.12

# Tabulación con \t
print(f"Nombre:\t{nombre}\nVersión:\t{version}")
# Nombre:    Python
# Versión:   3.12
```

### F-Strings Multilínea

Podés usar f-strings con triple comillas:

```python
nombre = "Ana"
edad = 25
ciudad = "Córdoba"

mensaje = f"""
Datos Personales:
  • Nombre: {nombre}
  • Edad: {edad} años
  • Ciudad: {ciudad}
"""

print(mensaje)
# Datos Personales:
#   • Nombre: Ana
#   • Edad: 25 años
#   • Ciudad: Córdoba
```

---

## Casos de Uso Avanzados

### Formateo Dinámico

Podés usar variables para controlar el formato:

```python
valor = 3.14159
decimales = 2

# Formateo dinámico
print(f"Valor: {valor:.{decimales}f}")     # Valor: 3.14

# Cambiar decimales
decimales = 4
print(f"Valor: {valor:.{decimales}f}")     # Valor: 3.1416

# Ancho dinámico
ancho = 20
texto = "Python"
print(f"|{texto:^{ancho}}|")               # |       Python       |
```

### Depuración

_Está disponible a partir de Python 3.8+ (Nuestro JupyterLab usa Python 3.11 :-) )._

El operador `=` dentro de f-strings es excelente para *debugging*:

```python
x = 10
y = 20
suma = x + y

# Sin el operador =
print(f"suma: {suma}")                      # suma: 30

# Con el operador = (muestra la expresión y el valor)
print(f"{suma=}")                           # suma=30
print(f"{x + y=}")                          # x + y=30
print(f"{suma / 2=}")                       # suma / 2=15.0

# Útil para debugging
def calcular_area(base, altura):
    area = base * altura
    print(f"{base=}, {altura=}, {area=}")
    return area

calcular_area(5, 10)
# base=5, altura=10, area=50
```

:::{tip} Debugging con = 
El operador `=` es **extremadamente útil** para {term}`debugging` rápido. En lugar de escribir:

```python
print(f"variable: {variable}")
```

Simplemente escribís:

```python
print(f"{variable=}")
```

Muestra tanto el nombre como el valor.
:::

### Fechas y Horas

```python
from datetime import datetime

ahora = datetime.now()

# Formatos básicos
print(f"Fecha y hora: {ahora}")
# Fecha y hora: 2026-01-06 14:18:23.640000

print(f"Fecha: {ahora:%d/%m/%Y}")
# Fecha: 06/01/2026

print(f"Hora: {ahora:%H:%M:%S}")
# Hora: 14:18:23

# Formatos completos
print(f"Completo: {ahora:%d de %B de %Y, %H:%M}")
# Completo: 06 de January de 2026, 14:18

# Formato ISO
print(f"ISO: {ahora:%Y-%m-%d}")
# ISO: 2026-01-06
```

### Trabajando con Objetos

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    
    def __str__(self):
        return f"Persona({self.nombre}, {self.edad} años)"
    
    def __repr__(self):
        return f"Persona(nombre='{self.nombre}', edad={self.edad})"

ana = Persona("Ana", 25)

print(f"String: {ana}")           # String: Persona(Ana, 25 años)
print(f"Repr: {ana!r}")            # Repr: Persona(nombre='Ana', edad=25)
print(f"Nombre: {ana.nombre}")    # Nombre: Ana
print(f"Edad: {ana.edad}")        # Edad: 25
```

---

## Tabla de Referencia Rápida

### Especificadores de Formato

| Código | Descripción | Ejemplo | Resultado |
|--------|-------------|---------|-----------|
| `:.2f` | 2 decimales | `f"{3.14159:.2f}"` | `3.14` |
| `:.0f` | Sin decimales | `f"{3.14159:.0f}"` | `3` |
| `:,` | Separador de miles | `f"{1000000:,}"` | `1,000,000` |
| `:.2%` | Porcentaje | `f"{0.25:.2%}"` | `25.00%` |
| `:e` | Notación científica | `f"{1000:e}"` | `1.000000e+03` |
| `:b` | Binario | `f"{42:b}"` | `101010` |
| `:x` | Hexadecimal | `f"{255:x}"` | `ff` |
| `:o` | Octal | `f"{8:o}"` | `10` |

### Alineación

| Código | Descripción | Ejemplo | Resultado |
|--------|-------------|---------|-----------|
| `:<10` | Izquierda, ancho 10 | `f"{ 'Hi':<10}"` | `'Hi        '` |
| `:>10` | Derecha, ancho 10 | `f"{ 'Hi':>10}"` | `'        Hi'` |
| `:^10` | Centro, ancho 10 | `f"{ 'Hi':^10}"` | `'    Hi    '` |
| `:0>5` | Rellenar con 0 | `f"{42:0>5}"` | `00042` |
| `:*^10` | Rellenar con * | `f"{ 'Hi':*^10}"` | `****Hi****` |

### Conversiones

| Código | Descripción | Ejemplo |
|--------|-------------|---------|
| `!s` | Llamar `str()` | `f"{obj!s}"` |
| `!r` | Llamar `repr()` | `f"{obj!r}"` |
| `!a` | Llamar `ascii()` | `f"{obj!a}"` |

---

## Errores Comunes

### Error 1: Olvidar el Prefijo `f`

```python
nombre = "Ana"

# ❌ Error: sin 'f'
print("Hola {nombre}")          # Imprime literal: Hola {nombre}

# ✓ Correcto: con 'f'
print(f"Hola {nombre}")         # Imprime: Hola Ana
```

### Error 2: Llaves No Balanceadas

```python
# ❌ Error: llave de cierre extra
print(f"Valor: {x}}")           # SyntaxError

# ❌ Error: falta llave de cierre
print(f"Valor: {x}")             # SyntaxError

# ✓ Correcto
print(f"Valor: {x}")
```

### Error 3: Expresiones Inválidas

```python
# ❌ Error: no podés usar asignaciones
print(f"{x = 5}")               # SyntaxError (Python < 3.8)

# ❌ Error: backslash en expresión (Python < 3.12)
print(f"{nombre\n}")            # SyntaxError

# ✓ Correcto: backslash fuera de llaves
print(f"{nombre}
")
```

### Error 4: Comillas No Escapadas

```python
# ❌ Error: comillas conflictivas (nota: ejemplo corregido)
# print(f"Dijo: "{nombre}"")      # SyntaxError

# ✓ Solución 1: alternar comillas
print(f"Dijo: '{nombre}'")

# ✓ Solución 2: escapar
print(f"Dijo: \"{nombre}\"")

# ✓ Solución 3: comillas simples externas
print(f'Dijo: "{nombre}"')
```

---

## Comparación con Otros Métodos

### Rendimiento

Las f-strings son **más rápidas** que otros métodos:

```python
import timeit

nombre = "Python"
numero = 42

# Concatenación
t1 = timeit.timeit(lambda: "Hola " + nombre + ", número " + str(numero), number=100000)

# .format()
t2 = timeit.timeit(lambda: "Hola {}, número {}".format(nombre, numero), number=100000)

# F-string
t3 = timeit.timeit(lambda: f"Hola {nombre}, número {numero}", number=100000)

print(f"Concatenación: {t1:.4f}s")      # ~0.0180s
print(f".format():     {t2:.4f}s")      # ~0.0250s
print(f"F-string:      {t3:.4f}s")      # ~0.0120s ← ¡Más rápido!
```

### Legibilidad

```python
nombre = "Ana"
edad = 25
ciudad = "Rosario"

# ❌ Concatenación: difícil de leer
msg = "Me llamo " + nombre + ", tengo " + str(edad) + " años y vivo en " + ciudad

# ❌ .format(): desconectado
msg = "Me llamo {}, tengo {} años y vivo en {}".format(nombre, edad, ciudad)

# ❌ .format() con índices: confuso
msg = "Me llamo {0}, tengo {1} años y vivo en {2}".format(nombre, edad, ciudad)

# ✓ F-string: claro y directo
msg = f"Me llamo {nombre}, tengo {edad} años y vivo en {ciudad}"
```

---

## Mejores Prácticas

### 1. Siempre Usar F-Strings (Python 3.6+)

```python
# ✓ Preferir siempre
mensaje = f"Hola, {nombre}"

# ❌ Evitar
mensaje = "Hola, " + nombre
mensaje = "Hola, {}".format(nombre)
mensaje = "Hola, %s" % nombre
```

### 2. Mantener Expresiones Simples

```python
# ✓ Simple y claro
edad = 25
mensaje = f"Tengo {edad} años"

# ❌ Demasiado complejo
mensaje = f"Tengo {sum([int(x) for x in str(datetime.now().year - 1998)])} años"

# ✓ Mejor: separar lógica
año_actual = datetime.now().year
año_nacimiento = 1998
edad = año_actual - año_nacimiento
mensaje = f"Tengo {edad} años"
```

### 3. Usar para Debugging

```python
# ✓ Excelente para debug (Python 3.8+)
x = 10
y = 20
print(f"{x=}, {y=}, {x+y=}")
# x=10, y=20, x+y=30
```

### 4. Formatear Números Consistentemente

```python
# ✓ Precios siempre con 2 decimales
precio = 19.9
print(f"Precio: ${precio:.2f}")         # $19.90

# ✓ Porcentajes con el formato correcto
tasa = 0.157
print(f"Tasa: {tasa:.1%}")              # Tasa: 15.7%
```

### 5. Usar Multilínea para Mensajes Largos

```python
# ✓ Más legible para mensajes largos
nombre = "Ana"
saldo = 1500.50

mensaje = f"""
Estimado/a {nombre}:

Su saldo actual es de ${saldo:.2f}.
Gracias por confiar en nosotros.

Saludos cordiales.
"""
```

---

## Ejercicios Prácticos

### Ejercicio 1: Datos Personales

Creá un programa que pida nombre, edad y ciudad, y muestre un mensaje formateado.

```python
# Tu código aquí
nombre = input("Tu nombre: ")
edad = int(input("Tu edad: "))
ciudad = input("Tu ciudad: ")

print(f"""
╔════════════════════════════╗
║   DATOS PERSONALES         ║
╠════════════════════════════╣
║ Nombre: {nombre:<18}║
║ Edad:   {edad:<18}║
║ Ciudad: {ciudad:<18}║
╚════════════════════════════╝
""")
```

### Ejercicio 2: Calculadora de Propinas

```python
monto_cuenta = float(input("Monto de la cuenta: $"))
porcentaje_propina = float(input("Porcentaje de propina (ej: 10): "))

propina = monto_cuenta * (porcentaje_propina / 100)
total = monto_cuenta + propina

print(f"""
Resumen de la Cuenta:
━━━━━━━━━━━━━━━━━━━━
Subtotal:   ${monto_cuenta:>10.2f}
Propina ({porcentaje_propina:.0f}%): ${propina:>10.2f}
━━━━━━━━━━━━━━━━━━━━
TOTAL:      ${total:>10.2f}
""")
```

### Ejercicio 3: Tabla de Conversión

```python
print("Tabla de Conversión Celsius a Fahrenheit")
print("=" * 40)
print(f"{ 'Celsius':^15} | {'Fahrenheit':^15}")
print("-" * 40)

for celsius in range(0, 101, 10):
    fahrenheit = (celsius * 9/5) + 32
    print(f"{celsius:^15}°C | {fahrenheit:^15.1f}°F")
```

### Ejercicio 4: Reporte de Ventas

```python
ventas = [
    ("Lunes", 1500.50),
    ("Martes", 2300.75),
    ("Miércoles", 1800.00),
    ("Jueves", 2100.25),
    ("Viernes", 3500.80),
]

print("REPORTE SEMANAL DE VENTAS")
print("=" * 40)

total = 0
for dia, monto in ventas:
    print(f"{dia:<12} ${monto:>10,.2f}")
    total += monto

print("=" * 40)
print(f"{ 'TOTAL':<12} ${total:>10,.2f}")
print(f"\nPromedio diario: ${total/len(ventas):,.2f}")
```

---

## Resumen

### Puntos Clave

:::{important} Conceptos Fundamentales
1. **F-strings** son la forma moderna de formatear strings en Python 3.6+.
2. Se crean con el prefijo `f` antes de las comillas: `f"texto {variable}" `.
3. Cualquier {term}`expresión` de Python válida puede ir entre llaves.
4. Son **más rápidas** y **más legibles** que otros métodos.
5. Soportan formateo avanzado de números, alineación y más.
:::

### Cuándo Usar F-Strings

✅ **Usar f-strings para:**
- Concatenar texto y variables.
- Formatear números (decimales, porcentajes, etc.).
- Crear mensajes dinámicos.
- {term}`Debugging` (con el operador `=`).
- Cualquier tipo de formateo de strings.

❌ **No usar f-strings cuando:**
- Trabajás con Python < 3.6 (usar `.format()`)
- El string debe ser traducido (usar `.format()` para i18n)

### Recursos Adicionales

- [PEP 498 - Literal String Interpolation](https://peps.python.org/pep-0498/)
- [Python String Formatting Best Practices](https://realpython.com/python-f-strings/)
- [Python Format Specification Mini-Language](https://docs.python.org/3/library/string.html#formatspec)

---

## Checklist de Dominio

Marcá lo que ya sabés hacer con f-strings:

- [ ] Crear f-strings básicas con variables.
- [ ] Usar expresiones matemáticas dentro de f-strings.
- [ ] Formatear números decimales (`.2f`).
- [ ] Usar separadores de miles (`,`).
- [ ] Formatear porcentajes (`%`).
- [ ] Alinear texto (izquierda, derecha, centro).
- [ ] Usar el ancho de campo.
- [ ] Incluir expresiones condicionales (ternario).
- [ ] Acceder a elementos de listas/diccionarios.
- [ ] Usar el operador `=` para debugging.
- [ ] Crear f-strings multilínea.
- [ ] Escapar llaves `{{` y `}}`.
- [ ] Aplicar formato dinámico.
- [ ] Formatear fechas y horas.

:::{tip} Práctica
La mejor forma de dominar las f-strings es **usarlas constantemente**. En cualquier situación donde necesites formatear texto, pensá primero en f-strings.
:::

---

¡Ahora sos un experto en f-strings! 🎉 Usá este conocimiento para escribir código más limpio, legible y Pythonic. 🐍✨
