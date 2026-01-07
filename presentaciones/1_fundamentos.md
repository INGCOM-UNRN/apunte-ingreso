---
marp: true
theme: default
paginate: true
header: 'Fundamentos de Programación en Python'
footer: 'Introducción a la programación'
style: |
  section {
    font-family: 'Roboto', 'Segoe UI', 'Liberation Sans', 'Helvetica', 'Arial', sans-serif;
    font-size: 28px;
  }
  h1 {
    color: #1976d2;
  }
  code {
    background-color: #f5f5f5;
  }
  section pre, section code {
    font-family: 'FiraCode Nerd Font', monospace;
  }
</style>
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Fundamentos de Programación en Python

**Introducción a la programación, variables, tipos de datos y operadores**

---

## ¿Qué vas a aprender?

* Cómo crear y usar **variables** para guardar información
* Los **4 tipos de datos básicos**: números, texto y booleanos
* **Operadores** para hacer cálculos y comparaciones
* Cómo **interactuar con el usuario**
* **Errores comunes** y cómo evitarlos

---

## ¿Qué es programar?

Programar es dar **instrucciones muy detalladas y precisas** a una computadora para que resuelva problemas.

**La computadora es:**
- Increíblemente rápida y precisa
- Pero necesita que le expliques **exactamente** qué hacer

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

---

<!-- _class: lead -->

# Tipos de Datos Básicos

---

## Los 4 Tipos Básicos

Python tiene cuatro tipos básicos que son como los "bloques de construcción" de cualquier programa:

1. **`int`** → Números enteros
2. **`float`** → Números con decimales
3. **`str`** → Texto (cadenas)
4. **`bool`** → Verdadero/Falso

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

---

<!-- _class: lead -->

# Operadores Aritméticos

---

## Operadores Básicos

| Operador | Operación | Ejemplo | Resultado |
|----------|-----------|---------|-----------|
| `+` | Suma | `5 + 3` | `8` |
| `-` | Resta | `10 - 4` | `6` |
| `*` | Multiplicación | `7 * 6` | `42` |
| `/` | División | `15 / 3` | `5.0` |

**Nota:** La división `/` **siempre** retorna un `float`

---

## Operadores Avanzados

| Operador | Operación | Ejemplo | Resultado |
|----------|-----------|---------|-----------|
| `//` | División entera | `17 // 5` | `3` |
| `%` | Módulo (resto) | `17 % 5` | `2` |
| `**` | Potenciación | `2 ** 3` | `8` |

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

---

<!-- _class: lead -->

# Operadores de Comparación

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

---

<!-- _class: lead -->

# Operadores Lógicos

---

## Operadores Lógicos

Permiten combinar condiciones:

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `and` | Y lógico | `True and False` | `False` |
| `or` | O lógico | `True or False` | `True` |
| `not` | Negación | `not True` | `False` |

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

---

<!-- _class: lead -->

# Entrada y Salida

---

## Interactuando con el Usuario

Los programas útiles necesitan **interactuar**:
- **Entrada:** Pedir información al usuario (`input()`)
- **Salida:** Mostrar resultados (`print()`)

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

---

<!-- _class: lead -->

# Conversión de Tipos

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

---

## Funciones de Conversión

| Función | Conversión | Ejemplo |
|---------|------------|---------|
| `int()` | A entero | `int("25")` → `25` |
| `float()` | A flotante | `float("3.14")` → `3.14` |
| `str()` | A string | `str(25)` → `"25"` |
| `bool()` | A booleano | `bool(1)` → `True` |

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

---

<!-- _class: lead -->

# Errores Comunes

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

---

<!-- _class: lead -->

# Resumen

---

## Conceptos Clave

1) **Variables:** Cajas con nombre para guardar valores
2) **Tipos de datos:** `int`, `float`, `str`, `bool`
3) **Operadores aritméticos:** `+`, `-`, `*`, `/`, `//`, `%`, `**`
4) **Operadores de comparación:** `==`, `!=`, `>`, `<`, `>=`, `<=`
5) **Operadores lógicos:** `and`, `or`, `not`
6) **Entrada/Salida:** `input()` y `print()`
7) **Conversión de tipos:** `int()`, `float()`, `str()`

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

---

## Buenas Prácticas

* Usá **nombres descriptivos** para variables
* **Snake_case** para nombres de variables
* Espacios alrededor de operadores: `x = 5 + 3`
* Comentarios para explicar el "por qué"
* **F-strings** para formatear texto
* Siempre **convertir** el resultado de `input()`

---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Los fundamentos son la base de todo en programación. Dedicá tiempo a dominarlos.
