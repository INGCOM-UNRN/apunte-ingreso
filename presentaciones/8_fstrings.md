---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
header: 'F-Strings en Python'
footer: 'Formateo moderno de cadenas'

---

<!-- _paginate: false -->
<!-- _header: '' -->

# F-Strings en Python

**Dominando la creación moderna de cadenas**

<!--
¡Hola a todos! Hoy vamos a hablar de algo que cambió la vida de los programadores Python para siempre: las f-strings. Antes de ellas, formatear texto era un dolor de cabeza. Había que sumar strings, usar métodos raros... era feo. Las f-strings vinieron a poner orden y belleza. Son una forma moderna, rápida y súper limpia de mezclar texto con variables.
-->
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

<!--
Vamos a ver qué son, por qué son tan geniales y cómo usarlas. Vamos a aprender a darle formato a los números (para que la plata se vea como dinero y los porcentajes como porcentajes), a alinear texto para hacer tablas lindas y a usar expresiones lógicas adentro del texto. Si alguna vez tuvieron que luchar para que un reporte se viera bien, esto les va a encantar.
-->
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

<!--
Imaginen que quieren decir 'Hola Juan, tenés 25 años'. En las épocas oscuras, teníamos que sumar pedazos de texto: 'Hola ' + nombre + ', tenés ' + str(edad). Un lío de comillas y signos más. Después vino `.format()`, que mejoró las cosas pero seguía siendo verbo. Y finalmente, llegaron las f-strings. Ponés una `f` adelante, escribís el texto normal y metés las variables entre llaves `{}`. Listo. Magia.
-->
---

## Ventajas de F-Strings

✅ **Súper legibles**: Variables integradas en el texto
✅ **Conversión automática**: No necesitás `str()`
✅ **Más rápidas**: Mejor rendimiento
✅ **Menos código**: Sintaxis concisa
✅ **Expresivas**: Cualquier expresión Python válida

**Es la forma recomendada por la comunidad Python**

<!--
No solo son más lindas de leer, sino que son más rápidas. Python las optimiza internamente. Además, te ahorran el trabajo de convertir todo a texto (`str()`) porque lo hacen solas. Es ganar-ganar por todos lados. Hoy en día, si estás usando Python 3.6 o superior (que deberías), no hay excusa para no usarlas.
-->
---

<!-- _class: lead -->

# Sintaxis Básica

<!--
La anatomía es simple. La `f` al principio es el interruptor que le dice a Python: 'Ojo, esto es una f-string, buscá las llaves'. Adentro de las llaves podés poner cualquier cosa que sea código Python válido: una variable, una cuenta matemática, una llamada a función... lo que quieras. Python lo evalúa y pega el resultado ahí mismo.
-->
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

<!--
Miren estos ejemplos. Podemos insertar variables directas como `nombre`. Pero también podemos hacer cuentas ahí mismo: `edad + 5`. O acceder a atributos de objetos. Lo importante es que lo que está entre llaves tiene que devolver un valor. Si ponés algo que no devuelve nada, no se va a mostrar nada.
-->
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

<!--
Esto es poderoso. No hace falta crear una variable `suma` antes de imprimirla. Podés poner `{x + y}` directo en el string. Esto hace que el código sea más compacto y directo. Incluso podés llamar funciones como `.upper()` para poner el texto en mayúsculas ahí mismo.
-->
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

<!--
Ahora, hablemos de números. ¿A quién le gusta ver un precio como `1234.56789`? A nadie. Queremos ver `$1,234.57`. Las f-strings tienen un mini-lenguaje de formato. Después de la variable, ponés dos puntos `:` y le decís cómo querés que se vea. `.2f` significa 'flotante con 2 decimales'. Es el estándar para monedas.
-->
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

<!--
El separador de miles es un salvavidas. Con una simple coma `:,` Python te formatea `1000000` como `1,000,000`. Y podés combinarlo con los decimales: `:,.2f`. Adiós a las funciones complejas para formatear números.
-->
---

<!-- _class: lead -->

# Formateo de Números

<!--
Los porcentajes también son fáciles. Si tenés `0.5` y querés mostrar `50%`, usás `:.0%`. Python multiplica por 100 y le agrega el símbolo. Si querés decimales en el porcentaje, `.2%` te da `50.00%`. Todo automático.
-->
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

<!--
Para los científicos o los que trabajan con números muy grandes o muy chicos, la notación científica `:e` es fundamental. Te convierte `1500000000` en `1.50e+09` para que sea legible. Es un detalle que suma mucho profesionalismo.
-->
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

<!--
Hacer tablas en la consola suele ser una pesadilla de contar espacios. Con f-strings es trivial. Le decís el ancho que querés y hacia dónde alinear. `<` izquierda, `>` derecha, `^` centro. `{texto:^20}` te centra el texto en un espacio de 20 caracteres. Perfecto para encabezados.
-->
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

<!--
Miren esta tabla. Alineamos el nombre a la izquierda, el precio a la derecha (como corresponde con los números) y la cantidad también a la derecha. Todo queda perfectamente encolumnado sin tener que calcular espacios a mano. Es una herramienta muy potente para reportes de texto.
-->
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

<!--
¿Y si queremos rellenar el espacio vacío? Por ejemplo, en un cheque o un ticket. Podemos decirle con qué carácter rellenar. `*^20` rellena con asteriscos y centra. `0>5` rellena con ceros a la izquierda (muy usado para IDs o códigos postales).
-->
---

<!-- _class: lead -->

# Alineación y Espaciado

<!--
Acá hay un ejemplo clásico: la tabla de multiplicar. Fíjense cómo usamos `:2d` y `:3d` para reservar espacio para los números. Aunque el resultado tenga 1 o 2 dígitos, siempre ocupa el mismo ancho, así que la columna queda recta.
-->
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

<!--
También podemos poner lógica. El operador ternario (el `if` en una línea) brilla acá. `{ 'Sí' if activo else 'No' }`. Te permite cambiar el texto según una condición sin tener que escribir un bloque `if-else` gigante afuera.
-->
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
# 
---
---
---
---
---
---
---
---
---
---<!--
Acceder a elementos de listas y diccionarios es natural. Solo tengan cuidado con las comillas. Si la f-string usa comillas dobles, usen simples adentro para las claves del diccionario `persona['nombre']`. Si no, Python se confunde y piensa que terminó el string.
-->
-----
# Manzana       $  2.50        10
# Banana        $  1.20        25
# Naranja       $  3.00        15
```

<!--
Todos los métodos de string funcionan. `.upper()`, `.lower()`, `.strip()`. Podés limpiar y formatear los datos en el momento de mostrarlos. Es muy útil cuando recibís datos sucios de una base de datos o un archivo.
-->
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

<!--
Las f-strings multilínea son geniales para mails o mensajes largos. Usás triple comilla `f"""` y podés escribir en varios renglones, manteniendo las variables vivas. Es mucho más limpio que poner `
` por todos lados.
-->
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

<!--
A veces querés mostrar una llave literal, no una variable. ¿Cómo hacés? La duplicás. `{{` se convierte en `{`. Esto es vital si estás generando JSON o CSS desde Python, donde las llaves tienen su propio significado.
-->
---

<!-- _class: lead -->

# Expresiones Complejas

<!--
Un truco avanzado: podés anidar f-strings. Podés usar una variable para definir la cantidad de decimales. `:.{decimales}f`. Esto te permite hacer sistemas de reporte súper flexibles donde el usuario elige la precisión.
-->
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

<!--
Este es mi favorito para debuggear. Si ponés un igual `=` al final de la variable `{suma=}`, Python te imprime el nombre de la variable Y su valor: `suma=30`. Te ahorra escribir `f'suma: {suma}'`. Úsenlo, es un viaje de ida.
-->
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

<!--
Las fechas son otro mundo. `datetime` se lleva bárbaro con f-strings. Podés usar los códigos de formato estándar (`%Y`, `%m`, `%d`) directamente adentro de las llaves. Te olvidás de llamar a `.strftime()` manualmente.
-->
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

<!--
Acá les dejo unas tablas de referencia. Imprímanlas o guárdenlas. Tienen los códigos más comunes para números, alineación y conversiones. Es el 'machete' oficial de f-strings.
-->
---

<!-- _class: lead -->

# Características Avanzadas

<!--
Errores comunes. El número 1 es olvidarse la `f`. Escribís todo perfecto pero te sale `{nombre}` literal. Siempre revisen que la `f` esté ahí adelante. El resaltado de sintaxis de su editor les va a ayudar (si no cambia de color, falta la f).
-->
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

<!--
El tema de las comillas. Si quieren poner comillas adentro del texto, tienen que ser distintas a las de afuera, o escaparlas con `\`. O usar triples comillas. Es cuestión de práctica.
-->
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

<!--
No abusen. Si meten una lógica súper compleja adentro de las llaves, el código se vuelve ilegible. Si no entra en una línea cómodamente, mejor calculen el valor afuera en una variable y muestren la variable.
-->
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

<!--
Buenas prácticas. Úsenlas siempre que puedan. Son el estándar moderno. Pero mantengan la lógica simple. La f-string es para MOSTRAR, no para CALCULAR todo el programa. Nombres descriptivos siempre ayudan.
-->
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

<!--
Consistencia. Si muestran plata, usen siempre 2 decimales. Si muestran números grandes, usen separadores de miles. Hacen que su aplicación se sienta profesional y cuidada.
-->
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

<!--
Vamos a practicar. Prueben hacer esta calculadora de propinas. Fíjense cómo combina todo: inputs, cuentas, formato de moneda, alineación y multilínea. Es un ejemplo completo de la vida real.
-->
---

<!-- _class: lead -->

# Tabla de Referencia

<!--
Y otro desafío: la tabla de conversión. Usen alineación centrada y formato de decimales para que quede prolija. Experimenten cambiando los anchos y los formatos.
-->
---

## Especificadores de Formato

| Código | Descripción | Ejemplo | Resultado |
|
---
-----|
---
---
---
----|
---
---
---|
---
---
-----|
| `:.2f` | 2 decimales | `f"{3.14159:.2f}"` | `3.14` |
| `:.0f` | Sin decimales | `f"{3.14:.0f}"` | `3` |
| `:,` | Sep. miles | `f"{1000000:,}"` | `1,000,000` |
| `:.2%` | Porcentaje | `f"{0.25:.2%}"` | `25.00%` |
| `:e` | Científica | `f"{1000:e}"` | `1.000000e+03` |

<!--
En resumen: F-strings son la forma de facto de manejar texto en Python hoy. Son rápidas, legibles y poderosas. Apréndanlas bien porque las van a usar en cada script que escriban.
-->
---

## Alineación

| Código | Descripción | Ejemplo | Resultado |
|
---
-----|
---
---
---
----|
---
---
---|
---
---
-----|
| `:<10` | Izquierda | `f"{'Hi':<10}"` | `'Hi        '` |
| `:>10` | Derecha | `f"{'Hi':>10}"` | `'        Hi'` |
| `:^10` | Centro | `f"{'Hi':^10}"` | `'    Hi    '` |
| `:0>5` | Relleno 0 | `f"{42:0>5}"` | `00042` |
| `:*^10` | Relleno * | `f"{'Hi':*^10}"` | `****Hi****` |

<!--
La regla de oro: si es Python 3.6+, usá f-strings. Si es código legado muy viejo, bueno, `.format()`. Pero para todo lo nuevo, la `f` es tu mejor amiga. ¡A formatear se ha dicho!
-->
---

## Conversiones

| Código | Descripción | Uso |
|
---
-----|
---
---
---
----|
-----|
| `!s` | Llamar `str()` | `f"{obj!s}"` |
| `!r` | Llamar `repr()` | `f"{obj!r}"` |
| `!a` | Llamar `ascii()` | `f"{obj!a}"` |
| `=` | Debug (nombre=valor) | `f"{variable=}"` |

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Errores Comunes

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

## 3. Usar Nombres Descriptivos

```python
# ❌ Variables crípticas
print(f"Total: {x * y + z}")

# ✅ Variables descriptivas
print(f"Total: {precio_unitario * cantidad + envio}")
```

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Ejercicio Práctico

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
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

<!--
NO MORE NOTES
-->
---

## Recursos

**Documentación oficial:**
- [PEP 498 - F-Strings](https://peps.python.org/pep-0498/)
- [Format Specification](https://docs.python.org/3/library/string.html#formatspec)

**Tip:** La mejor forma de dominar f-strings es **usarlas constantemente**

<!--
NO MORE NOTES
-->
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
