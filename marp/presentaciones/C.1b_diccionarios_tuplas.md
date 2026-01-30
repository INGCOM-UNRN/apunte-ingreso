---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Estructuras de Datos - Parte 4/5' -->

# <!-- fit --> Diccionarios y Tuplas
## Mapeos e Inmutabilidad
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Diccionarios (dict)' -->

# Clave y Valor

Un diccionario asocia una **clave** (única) con un **valor**.
Es como un diccionario real: buscás palabra (clave) → obtenés definición (valor).

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Sistemas"
}

print(estudiante["nombre"])  # "Ana"
```

**Claves:** Deben ser inmutables (str, int, tuple).
**Valores:** Pueden ser cualquier cosa (listas, otros dicts).

---

<!-- _header: 'Acceso seguro' -->

# get() vs []

**Acceso directo (`[]`):**
```python
print(estudiante["nota"])  # ❌ KeyError si no existe
```

**Método `get()`:**
```python
print(estudiante.get("nota"))      # None (no falla)
print(estudiante.get("nota", 0))   # 0 (valor por defecto)
```

**Recomendación:** Usá `get()` si no estás seguro de que la clave exista.

---

<!-- _header: 'Modificación' -->

# Agregar y cambiar

Los diccionarios son **mutables**.

```python
datos = {"a": 1, "b": 2}

# Modificar existente
datos["a"] = 10

# Agregar nuevo
datos["c"] = 3

# Eliminar
del datos["b"]

print(datos)  # {"a": 10, "c": 3}
```

---

<!-- _header: 'Iteración' -->

# Recorrer un diccionario

```python
capitales = {"Argentina": "Buenos Aires", "Chile": "Santiago"}

# Solo claves (por defecto)
for pais in capitales:
    print(pais)

# Clave y Valor (items) - EL MÁS ÚTIL
for pais, ciudad in capitales.items():
    print(f"La capital de {pais} es {ciudad}")
```

**Métodos de vista:**
* `.keys()`: Claves
* `.values()`: Valores
* `.items()`: Pares (clave, valor)

---

<!-- _class: inverse -->

# <!-- fit --> Tuplas (tuple)
## Listas inmutables

---

<!-- _header: '¿Qué es una tupla?' -->

# Inmutabilidad

Una tupla es como una lista, pero **no se puede modificar** una vez creada.

**Sintaxis:** Paréntesis `()`
```python
punto = (10, 20)
colores = ("rojo", "verde", "azul")
```

**Intento de modificación fallará:**
```python
punto[0] = 5  # ❌ TypeError
```

---

<!-- _header: 'Uso de tuplas' -->

# ¿Cuándo usarlas?

1.  **Datos constantes:** Días de la semana, coordenadas, configuraciones fijas.
2.  **Seguridad:** Garantizar que los datos no cambien accidentalmente.
3.  **Claves de diccionario:** Las listas no pueden ser claves, las tuplas sí.
4.  **Rendimiento:** Son ligeramente más rápidas que las listas.

---

<!-- _header: 'Unpacking' -->

# Desempaquetado

Asignar elementos de una tupla (o lista) a variables individuales.

```python
# Tupla de coordenadas
coordenadas = (10, 20, 30)

# Desempaquetado
x, y, z = coordenadas

print(f"x={x}, y={y}, z={z}")
```

**Intercambio de variables (swap):**
```python
a, b = 5, 10
a, b = b, a  # a=10, b=5
```

---

<!-- _header: 'Tuplas y Funciones' -->

# Retorno múltiple

Las funciones pueden devolver múltiples valores usando tuplas implícitas.

```python
def min_max(numeros):
    return min(numeros), max(numeros)  # Retorna tupla

lista = [1, 5, 2, 8, 3]
menor, mayor = min_max(lista)

print(f"Mínimo: {menor}, Máximo: {mayor}")
```

---

<!-- _header: 'Resumen' -->

# Diccionarios y Tuplas

**Diccionarios:**
* Pares Clave-Valor `{k: v}`.
* Acceso rápido por clave.
* Usar `get()` para evitar errores.
* Iterar con `.items()`.

**Tuplas:**
* Inmutables `()`.
* Útiles para datos fijos y retorno múltiple.
* Desempaquetado: `x, y = punto`.

**Próximo:**
* Módulos Random y Math.
