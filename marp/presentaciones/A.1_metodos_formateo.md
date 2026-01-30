---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'F-Strings - Parte 1/2' -->

# <!-- fit --> Formateo de Cadenas
## Métodos tradicionales
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'El problema' -->

# Combinar texto y variables

**Necesidad común:**
```python
nombre = "Ana"
edad = 20

# ¿Cómo mostrar esto bonito?
# "Hola, me llamo Ana y tengo 20 años"
```

**Varios métodos disponibles**

---

<!-- _header: 'Método 1' -->

# Concatenación con +

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo " + nombre + \
          " y tengo " + str(edad) + " años"
print(mensaje)
```

**Problemas:**
* Difícil de leer
* Hay que convertir a string
* Muchos `+` y espacios

---

<!-- _header: 'Método 2' -->

# Operador % (estilo C)

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo %s y tengo %d años" % (nombre, edad)
print(mensaje)
```

**Especificadores:**
* `%s` → string
* `%d` → entero
* `%f` → float

**Antiguo pero funciona**

---

<!-- _header: 'Método 3' -->

# Método .format()

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo {} y tengo {} años".format(
    nombre, edad
)
print(mensaje)
```

**Con índices:**
```python
mensaje = "{0} tiene {1} años. {0} estudia Python".format(
    nombre, edad
)
```

---

<!-- _header: 'format() con nombres' -->

# Named placeholders

```python
mensaje = "Hola, me llamo {n} y tengo {e} años".format(
    n=nombre, 
    e=edad
)
print(mensaje)
```

**Más legible pero verboso**

---

<!-- _header: 'Formateo de números' -->

# .format() avanzado

**Decimales:**
```python
precio = 19.99876
print("Precio: ${:.2f}".format(precio))
# Precio: $19.99
```

**Alineación:**
```python
print("|{:>10}|".format("derecha"))  # |   derecha|
print("|{:<10}|".format("izq"))      # |izq       |
print("|{:^10}|".format("centro"))   # |  centro  |
```

---

<!-- _header: 'Comparación' -->

# Métodos tradicionales

**Concatenación (+):**
* ❌ Difícil de leer
* ❌ Conversiones manuales

**Operador %:**
* ❌ Sintaxis arcaica
* ❌ Fácil confundirse

**Método .format():**
* ✅ Más legible
* ✅ Flexible
* ❌ Algo verboso

---

<!-- _header: 'Ejemplo práctico' -->

# Tabla con .format()

```python
productos = [
    ("Pan", 50),
    ("Leche", 100),
    ("Huevos", 75)
]

print("{:<10} {:>8}".format("Producto", "Precio"))
print("-" * 20)

for prod, precio in productos:
    print("{:<10} ${:>7.2f}".format(prod, precio))
```

**Salida:**
```
Producto     Precio
--------------------
Pan        $  50.00
Leche      $ 100.00
Huevos     $  75.00
```

---

<!-- _header: 'Limitaciones' -->

# ¿Por qué no usar siempre .format()?

**Ejemplo:**
```python
nombre = "Ana"
edad = 20
ciudad = "Buenos Aires"

# Muy largo y repetitivo
mensaje = "{} vive en {} y tiene {} años".format(
    nombre, ciudad, edad
)
```

**Necesitamos algo mejor...**

---

<!-- _header: 'Resumen' -->

# Métodos tradicionales

**Concatenación (+):**
* Simple pero tedioso

**Operador %:**
* Estilo antiguo

**Método .format():**
* Poderoso pero verboso

**Próximo:**
* F-Strings (la solución moderna)

---

<!-- _class: centered -->

# ¿Preguntas?
