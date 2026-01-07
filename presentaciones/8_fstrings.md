---
marp: true
theme: default
paginate: true
header: 'F-Strings en Python'
footer: 'Formateo moderno de cadenas'
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

# F-Strings en Python

**Dominando la creación moderna de cadenas**

---

## ¿Qué es una F-String?

Una **f-string** (formatted string literal) es un string que:
- Comienza con la letra `f` o `F` antes de las comillas
- Permite incluir **expresiones de Python** dentro de llaves `{}`
- Se evalúa en **tiempo de ejecución**

```python
nombre = "Ana"
edad = 25
mensaje = f"Me llamo {nombre} y tengo {edad} años"
print(mensaje)
# Me llamo Ana y tengo 25 años
```

**Introducidas en Python 3.6**

---

## ¿Por qué F-Strings?

Antes de las f-strings, teníamos formas menos elegantes:

**❌ Concatenación (engorroso):**
```python
mensaje = "Me llamo " + nombre + " y tengo " + str(edad) + " años"
```

**❌ `.format()` (menos legible):**
```python
mensaje = "Me llamo {} y tengo {} años".format(nombre, edad)
```

**✅ F-Strings (claro y directo):**
```python
mensaje = f"Me llamo {nombre} y tengo {edad} años"
```

---

## Ventajas de F-Strings

✅ **Súper legibles**: Variables integradas en el texto
✅ **Conversión automática**: No necesitás `str()`
✅ **Más rápidas**: Mejor rendimiento
✅ **Menos código**: Sintaxis concisa
✅ **Expresivas**: Cualquier expresión Python válida

**Es la forma recomendada por la comunidad Python**

---

<!-- _class: lead -->

# Sintaxis Básica

---

## Anatomía de una F-String

```python
f"Texto literal {expresion_python} más texto"
│  └─────────────┘ └──────────────┘ └────────┘
│        │                │             │
│        │                │             └─ Texto normal
│        │                └─────────────── Expresión evaluada
│        └────────────────────────────── Texto literal
└─────────────────────────────────────── Prefijo 'f' (obligatorio)
```

**Componentes:**
1. Prefijo `f` o `F`
2. Comillas (simples `'` o dobles `"`)
3. Texto literal
4. Expresiones entre llaves `{}`

---

## Variables Simples

```python
nombre = "Carlos"
edad = 30
ciudad = "Bariloche"

# Insertar variables directamente
print(f"Hola, soy {nombre}")                # Hola, soy Carlos
print(f"Tengo {edad} años")                 # Tengo 30 años
print(f"Vivo en {ciudad}")                  # Vivo en Bariloche
print(f"{nombre} tiene {edad} años")        # Carlos tiene 30 años
```

**Conversión automática de tipos:**
```python
edad = 25           # int
altura = 1.75       # float
activo = True       # bool

print(f"Edad: {edad}, Altura: {altura}, Activo: {activo}")
# Edad: 25, Altura: 1.75, Activo: True
```

---

## Expresiones Matemáticas

Podés poner **cualquier expresión** de Python:

```python
x = 10
y = 20

print(f"Suma: {x + y}")              # Suma: 30
print(f"Producto: {x * y}")          # Producto: 200
print(f"División: {x / y}")          # División: 0.5
print(f"Potencia: {x ** 2}")         # Potencia: 100

# Más complejo
radio = 5
print(f"Área del círculo: {3.14159 * radio ** 2}")
# Área del círculo: 78.53975
```

---

## Llamar Funciones

```python
def mayusculas(texto):
    return texto.upper()

nombre = "ana"
print(f"Nombre en mayúsculas: {mayusculas(nombre)}")
# Nombre en mayúsculas: ANA

# Funciones integradas
lista = [1, 2, 3, 4, 5]
print(f"Longitud: {len(lista)}")      # Longitud: 5
print(f"Suma: {sum(lista)}")          # Suma: 15
print(f"Máximo: {max(lista)}")        # Máximo: 5
```

---

<!-- _class: lead -->

# Formateo de Números

---

## Decimales

```python
pi = 3.14159265359

print(f"2 decimales: {pi:.2f}")       # 2 decimales: 3.14
print(f"4 decimales: {pi:.4f}")       # 4 decimales: 3.1416
print(f"Sin decimales: {pi:.0f}")     # Sin decimales: 3
```

**Sintaxis:** `{valor:.Nf}`
- `.N` = cantidad de decimales
- `f` = formato de punto flotante

---

## Separadores de Miles

```python
precio = 1234567.89

print(f"Con separador: {precio:,}")
# Con separador: 1,234,567.89

print(f"Separador y decimales: {precio:,.2f}")
# Separador y decimales: 1,234,567.89

# Números enteros
habitantes = 45000000
print(f"Población: {habitantes:,}")
# Población: 45,000,000
```

---

## Porcentajes

```python
aprobados = 45
total = 50
tasa = aprobados / total

print(f"Aprobaron: {tasa:.0%}")          # Aprobaron: 90%
print(f"Tasa: {tasa:.1%}")               # Tasa: 90.0%
print(f"Exacto: {tasa:.2%}")             # Exacto: 90.00%

# Automáticamente multiplica por 100
descuento = 0.15
print(f"Descuento: {descuento:.0%}")     # Descuento: 15%
```

**Nota:** El formato `%` multiplica por 100 automáticamente

---

## Notación Científica

```python
numero_grande = 1500000000

print(f"Científica: {numero_grande:e}")
# Científica: 1.500000e+09

print(f"2 decimales: {numero_grande:.2e}")
# 2 decimales: 1.50e+09

# Número pequeño
numero_pequeño = 0.0000123
print(f"Científica: {numero_pequeño:.2e}")
# Científica: 1.23e-05
```

---

<!-- _class: lead -->

# Alineación y Espaciado

---

## Alineación Básica

```python
texto = "Python"

print(f"|{texto:<20}|")    # Izquierda  |Python              |
print(f"|{texto:>20}|")    # Derecha    |              Python|
print(f"|{texto:^20}|")    # Centro     |       Python       |
```

**Sintaxis:**
- `<` = Alinear a la izquierda
- `>` = Alinear a la derecha
- `^` = Centrar
- Número = ancho total

---

## Tabla con Alineación

```python
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

---

## Rellenar con Caracteres

```python
numero = 42

print(f"{numero:0>5}")     # 00042 (rellena con ceros)
print(f"{numero:*^10}")    # ****42**** (rellena con *)
print(f"{numero:.>8}")     # ......42 (rellena con puntos)

# Títulos decorados
titulo = "PYTHON"
print(f"{titulo:=^30}")    # ============PYTHON============
print(f"{titulo:*^30}")    # ************PYTHON************
```

**Sintaxis:** `{valor:caracter alineacion ancho}`

---

## Tabla de Multiplicar

```python
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

---

<!-- _class: lead -->

# Expresiones Complejas

---

## Condicionales (Operador Ternario)

```python
edad = 20
print(f"Es {'mayor' if edad >= 18 else 'menor'} de edad")
# Es mayor de edad

nota = 7
print(f"Estado: {'Aprobado ✓' if nota >= 6 else 'Desaprobado ✗'}")
# Estado: Aprobado ✓

temperatura = 30
print(f"Clima: {'calor' if temperatura > 25 else 'frío'}")
# Clima: calor
```

---

## Listas y Diccionarios

```python
# Listas
numeros = [1, 2, 3, 4, 5]
print(f"Primer elemento: {numeros[0]}")       # Primer elemento: 1
print(f"Último elemento: {numeros[-1]}")      # Último elemento: 5
print(f"Suma: {sum(numeros)}")                # Suma: 15

# Diccionarios
persona = {"nombre": "Ana", "edad": 25}
print(f"Nombre: {persona['nombre']}")         # Nombre: Ana
print(f"Edad: {persona['edad']}")             # Edad: 25

# Métodos
texto = "python"
print(f"Mayúsculas: {texto.upper()}")         # Mayúsculas: PYTHON
```

---

## Métodos de String

```python
texto = "python programming"

print(f"Mayúsculas: {texto.upper()}")
# Mayúsculas: PYTHON PROGRAMMING

print(f"Capitalize: {texto.capitalize()}")
# Capitalize: Python programming

print(f"Title: {texto.title()}")
# Title: Python Programming

print(f"Longitud: {len(texto)}")
# Longitud: 18

print(f"Reemplazar: {texto.replace('python', 'Python')}")
# Reemplazar: Python programming
```

---

<!-- _class: lead -->

# Características Avanzadas

---

## F-Strings Multilínea

```python
nombre = "Ana"
edad = 25
ciudad = "Buenos Aires"

mensaje = f"""
Hola, me llamo {nombre}.
Tengo {edad} años.
Vivo en {ciudad}.
"""
print(mensaje)
```

**Útil para:**
- Mensajes largos
- Reportes
- Templates
- SQL queries

---

## Escapar Llaves

Para mostrar llaves literales, duplicalas:

```python
valor = 42

# Una llave → Variable
print(f"Valor: {valor}")        # Valor: 42

# Doble llave → Literal
print(f"Llaves: {{valor}}")     # Llaves: {valor}

# Ejemplo de JSON
print(f'{{"nombre": "{nombre}", "edad": {edad}}}')
# {"nombre": "Ana", "edad": 25}
```

---

## Formato Dinámico

Podés usar variables para controlar el formato:

```python
# Cambiar decimales
valor = 3.14159
decimales = 2
print(f"Valor: {valor:.{decimales}f}")     # Valor: 3.14

decimales = 4
print(f"Valor: {valor:.{decimales}f}")     # Valor: 3.1416

# Ancho dinámico
ancho = 20
texto = "Python"
print(f"|{texto:^{ancho}}|")               # |       Python       |
```

---

## Depuración con `=`

**Disponible desde Python 3.8+**

El operador `=` es excelente para debugging:

```python
x = 10
y = 20
suma = x + y

# Sin =
print(f"suma: {suma}")              # suma: 30

# Con = (muestra expresión y valor)
print(f"{suma=}")                   # suma=30
print(f"{x + y=}")                  # x + y=30
print(f"{suma / 2=}")               # suma / 2=15.0
```

**Muestra tanto el nombre/expresión como el valor**

---

## Fechas y Horas

```python
from datetime import datetime

ahora = datetime.now()

# Formatos básicos
print(f"Fecha y hora: {ahora}")
# Fecha y hora: 2026-01-07 14:18:23.640000

print(f"Fecha: {ahora:%d/%m/%Y}")
# Fecha: 07/01/2026

print(f"Hora: {ahora:%H:%M:%S}")
# Hora: 14:18:23

# Formato completo
print(f"Completo: {ahora:%d de %B de %Y, %H:%M}")
# Completo: 07 de January de 2026, 14:18
```

---

<!-- _class: lead -->

# Tabla de Referencia

---

## Especificadores de Formato

| Código | Descripción | Ejemplo | Resultado |
|--------|-------------|---------|-----------|
| `:.2f` | 2 decimales | `f"{3.14159:.2f}"` | `3.14` |
| `:.0f` | Sin decimales | `f"{3.14:.0f}"` | `3` |
| `:,` | Sep. miles | `f"{1000000:,}"` | `1,000,000` |
| `:.2%` | Porcentaje | `f"{0.25:.2%}"` | `25.00%` |
| `:e` | Científica | `f"{1000:e}"` | `1.000000e+03` |

---

## Alineación

| Código | Descripción | Ejemplo | Resultado |
|--------|-------------|---------|-----------|
| `:<10` | Izquierda | `f"{'Hi':<10}"` | `'Hi        '` |
| `:>10` | Derecha | `f"{'Hi':>10}"` | `'        Hi'` |
| `:^10` | Centro | `f"{'Hi':^10}"` | `'    Hi    '` |
| `:0>5` | Relleno 0 | `f"{42:0>5}"` | `00042` |
| `:*^10` | Relleno * | `f"{'Hi':*^10}"` | `****Hi****` |

---

## Conversiones

| Código | Descripción | Uso |
|--------|-------------|-----|
| `!s` | Llamar `str()` | `f"{obj!s}"` |
| `!r` | Llamar `repr()` | `f"{obj!r}"` |
| `!a` | Llamar `ascii()` | `f"{obj!a}"` |
| `=` | Debug (nombre=valor) | `f"{variable=}"` |

---

<!-- _class: lead -->

# Errores Comunes

---

## Error #1: Olvidar el Prefijo `f`

```python
nombre = "Ana"

# ❌ Error: sin 'f'
print("Hola {nombre}")
# Hola {nombre} (literal, no evalúa)

# ✅ Correcto: con 'f'
print(f"Hola {nombre}")
# Hola Ana
```

**Solución:** SIEMPRE usar el prefijo `f`

---

## Error #2: Comillas Anidadas

```python
# ❌ Error: comillas conflictivas
mensaje = f"Dice: "Hola""  # SyntaxError

# ✅ Solución 1: Alternar comillas
mensaje = f"Dice: 'Hola'"
mensaje = f'Dice: "Hola"'

# ✅ Solución 2: Escapar
mensaje = f"Dice: \"Hola\""

# ✅ Solución 3: Triple comillas
mensaje = f"""Dice: "Hola" """
```

---

## Error #3: Expresiones Complejas

```python
# ❌ Difícil de leer
resultado = f"{calculo_complejo(x, y, z) if condicion else valor_por_defecto(a, b)}"

# ✅ Mejor: dividir en pasos
temp = calculo_complejo(x, y, z) if condicion else valor_por_defecto(a, b)
resultado = f"{temp}"

# ✅ Aún mejor: variable descriptiva
valor_calculado = calculo_complejo(x, y, z) if condicion else valor_por_defecto(a, b)
resultado = f"El resultado es: {valor_calculado}"
```

---

## Error #4: No Escapar Llaves

```python
# ❌ Error: interpreta como variable
print(f"Usar llaves: {variable}")
# NameError si 'variable' no existe

# ✅ Correcto: duplicar llaves
print(f"Usar llaves: {{variable}}")
# Usar llaves: {variable}

# Para diccionarios JSON
print(f'{{"clave": "{valor}"}}')
# {"clave": "valor"}
```

---

<!-- _class: lead -->

# Buenas Prácticas

---

## 1. Preferir F-Strings

```python
nombre = "Ana"
edad = 25

# ❌ Evitar concatenación
mensaje = "Hola " + nombre + ", tienes " + str(edad) + " años"

# ❌ Evitar .format()
mensaje = "Hola {}, tienes {} años".format(nombre, edad)

# ✅ Usar f-strings
mensaje = f"Hola {nombre}, tienes {edad} años"
```

---

## 2. Mantener Expresiones Simples

```python
# ❌ Demasiado complejo
print(f"Resultado: {sum([x**2 for x in range(10) if x % 2 == 0])}")

# ✅ Dividir en pasos
pares = [x for x in range(10) if x % 2 == 0]
cuadrados = [x**2 for x in pares]
suma = sum(cuadrados)
print(f"Resultado: {suma}")
```

---

## 3. Usar Nombres Descriptivos

```python
# ❌ Variables crípticas
print(f"Total: {x * y + z}")

# ✅ Variables descriptivas
print(f"Total: {precio_unitario * cantidad + envio}")
```

---

## 4. Formatear Números Consistentemente

```python
# ✅ Siempre especificar decimales para dinero
precio = 19.5
print(f"Precio: ${precio:.2f}")  # Precio: $19.50

# ✅ Usar separadores de miles
habitantes = 45000000
print(f"Población: {habitantes:,}")  # Población: 45,000,000
```

---

## 5. Usar Multilínea para Mensajes Largos

```python
nombre = "Ana"
saldo = 1500.50

# ✅ Más legible
mensaje = f"""
Estimado/a {nombre}:

Su saldo actual es de ${saldo:.2f}.
Gracias por confiar en nosotros.

Saludos cordiales.
"""
```

---

<!-- _class: lead -->

# Ejercicio Práctico

---

## Calculadora de Propinas

```python
monto_cuenta = float(input("Monto: $"))
porcentaje_propina = float(input("Propina %: "))

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

---

## Tabla de Conversión

```python
print("Celsius a Fahrenheit")
print("=" * 40)
print(f"{'Celsius':^15} | {'Fahrenheit':^15}")
print("-" * 40)

for celsius in range(0, 101, 10):
    fahrenheit = (celsius * 9/5) + 32
    print(f"{celsius:^15}°C | {fahrenheit:^15.1f}°F")
```

---

<!-- _class: lead -->

# Resumen

---

## Conceptos Clave

**F-Strings:**
- Forma moderna de formatear strings (Python 3.6+)
- Prefijo `f` antes de las comillas: `f"texto {variable}"`
- Cualquier expresión Python entre llaves
- Más rápidas y legibles que otros métodos

**Formateo:**
- Decimales: `:.2f`
- Miles: `:,`
- Porcentajes: `:.2%`
- Alineación: `:<`, `:>`, `:^`

---

## Cuándo Usar F-Strings

✅ **Usar f-strings para:**
- Concatenar texto y variables
- Formatear números
- Crear mensajes dinámicos
- Debugging (operador `=`)
- Cualquier formateo de strings

❌ **No usar cuando:**
- Python < 3.6
- Strings para traducción (i18n)

---

## Checklist de Dominio

- [ ] Crear f-strings básicas
- [ ] Usar expresiones matemáticas
- [ ] Formatear decimales
- [ ] Usar separadores de miles
- [ ] Formatear porcentajes
- [ ] Alinear texto
- [ ] Expresiones condicionales
- [ ] Operador `=` para debugging
- [ ] F-strings multilínea
- [ ] Escapar llaves

---

## Recursos

**Documentación oficial:**
- [PEP 498 - F-Strings](https://peps.python.org/pep-0498/)
- [Format Specification](https://docs.python.org/3/library/string.html#formatspec)

**Tip:** La mejor forma de dominar f-strings es **usarlas constantemente**

---

<!-- _paginate: false -->

# ¡Ahora sos un experto en f-strings! 🎉

Usá este conocimiento para escribir código más limpio, legible y Pythonic

**Recordá:**
- Siempre usar el prefijo `f`
- Mantener expresiones simples
- Formatear números consistentemente
- Aprovechar el operador `=` para debugging

🐍✨
