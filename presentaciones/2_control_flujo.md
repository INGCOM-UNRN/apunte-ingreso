---
marp: true
theme: default
paginate: true
header: 'Control de Flujo en Python'
footer: 'Condicionales y estructuras de repetición'
style: |
  section {
    font-size: 28px;
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

# Control de Flujo en Python

**Condicionales y estructuras de repetición**

---

## ¿Qué vas a aprender?

* Cómo hacer que tu programa **tome decisiones** (`if`, `elif`, `else`)
* Repetir acciones con **`while`** y **`for`**
* Controlar lazos con **`break`** y **`continue`**
* **Patrones comunes** de programación

---

## ¿Qué es el Control de Flujo? 🚦

Hasta ahora, tus programas han seguido una secuencia fija. Los programas reales necesitan ser **inteligentes**.

**Sin Control de Flujo:**
```python
print("Buenos días")
print("Buenas tardes")
print("Buenas noches")
# Siempre saluda igual...
```

**Con Control de Flujo:**
```python
hora = 14
if hora < 12:
    print("Buenos días")
elif hora < 20:
    print("Buenas tardes")
else:
    print("Buenas noches")
```

---

## Analogía del Semáforo 🚦

Tu programa **mira la situación** y **decide** qué hacer:

🟢 **Verde** → Paso
🟡 **Amarillo** → Freno con cuidado
🔴 **Rojo** → Me detengo

**El control de flujo permite:**
- Tomar decisiones basadas en datos
- Evitar repetir código
- Crear programas interactivos
- Manejar diferentes escenarios

---

## Ejemplos del Mundo Real

**🏧 Cajero Automático:** ¿El PIN es correcto? Permitir 3 intentos
**🎮 Videojuego:** ¿El jugador chocó? Loop principal del juego
**🌡️ Termostato:** ¿Temperatura baja? Encender/apagar calefacción
**📱 App de Mensajes:** ¿Hay conexión? Revisar nuevos mensajes

---

<!-- _class: lead -->

# Condicionales: `if`

---

## La Estructura `if` Simple

Ejecuta código **solo si** una condición es verdadera

```python
if condicion:
    # Código que se ejecuta si condición es True
```

**Ejemplo:**
```python
edad = 20

if edad >= 18:
    print("Sos mayor de edad")
    print("Podés votar")

print("Gracias por consultar")
```

---

## Elementos Clave del `if`

```python
if temperatura > 30:
    print("Hace mucho calor!")
    print("Tomá agua")
```

**Componentes:**
1. `if` → Palabra clave
2. `temperatura > 30` → Condición (debe ser booleana)
3. `:` → Dos puntos (¡obligatorio!)
4. **Indentación** → Define el bloque de código

---

## ⚠️ La Indentación es FUNDAMENTAL

Python usa la **indentación** para definir bloques de código

```python
# ✓ Correcto
if llueve:
    print("Llevá paraguas")
    print("Cuidado al caminar")

# ✗ Incorrecto - Error de indentación
if llueve:
print("Llevá paraguas")
    print("Cuidado al caminar")
```

**Regla:** Usá **4 espacios** para indentar

---

## Condiciones Simples

```python
edad = 18

if edad >= 18:
    print("Sos mayor de edad")

# La condición debe ser booleana (True o False)
if edad == 18:
    print("Tenés exactamente 18 años")

if edad != 21:
    print("No tenés 21 años")
```

---

## Múltiples Instrucciones en el Bloque

```python
puntos = 95

if puntos >= 90:
    print("¡Excelente trabajo!")
    print("Obtuviste una A")
    print("Felicitaciones")
    # Todo esto se ejecuta si puntos >= 90

print("Fin del programa")  # Siempre se ejecuta
```

---

<!-- _class: lead -->

# Condicionales: `if-else`

---

## La Estructura `if-else`

Cuando tenés **exactamente 2 opciones**: una cosa **u** otra

```python
if condicion:
    # Se ejecuta si condición es True
else:
    # Se ejecuta si condición es False
```

**Ejemplo:**
```python
edad = 16

if edad >= 18:
    print("Sos mayor de edad")
else:
    print("Sos menor de edad")
```

---

## Analogía: Lanzamiento de Moneda

Tirás una moneda:
- **Si** sale cara → ganás
- **Si** sale cruz (else) → perdés

```python
moneda = "cara"

if moneda == "cara":
    print("¡Ganaste!")
else:
    print("Perdiste")
```

**Siempre pasa UNA de las dos cosas**, nunca ambas.

---

## ¿Cuándo usar `if-else`?

Usá `if-else` cuando:
- Hay **exactamente 2 opciones** (blanco o negro, sí o no)
- **Siempre** querés hacer algo (una cosa u otra)
- Las opciones son **excluyentes**

**Ejemplos:**
- Aprobar/Reprobar un examen
- Día/Noche
- Par/Impar
- Usuario logueado / No logueado

---

## Comparación: `if` vs `if-else`

**Solo `if`:**
```python
if soleado:
    print("¡Vamos al parque!")
# Si no es soleado, no pasa nada
```

**Con `if-else`:**
```python
if soleado:
    print("¡Vamos al parque!")
else:
    print("Nos quedamos en casa")
# Siempre hacemos algo ✓
```

---

<!-- _class: lead -->

# Condicionales: `if-elif-else`

---

## Múltiples Caminos con `elif`

Cuando tenés **más de 2 opciones**, usás `elif` (else if)

```python
if condicion1:
    # Si condicion1 es True
elif condicion2:
    # Si condicion1 es False y condicion2 es True
elif condicion3:
    # Si condicion1 y condicion2 son False, pero condicion3 es True
else:
    # Si todas las anteriores son False
```

---

## Ejemplo: Sistema de Calificaciones

```python
nota = 85

if nota >= 90:
    print("📗 Excelente - A")
elif nota >= 70:
    print("📘 Muy Bueno - B")
elif nota >= 60:
    print("📙 Bueno - C")
elif nota >= 40:
    print("📕 Regular - D")
else:
    print("❌ Insuficiente - F")

print(f"Tu nota fue: {nota}")
```

---

## ¿Cómo Funciona `elif`?

**Flujo de evaluación con `nota = 85`:**

1️⃣ ¿`nota >= 90`? → No (85 < 90) → Pasa a la siguiente

2️⃣ ¿`nota >= 70`? → **¡Sí!** (85 >= 70)
   ✅ Ejecuta este bloque
   🛑 **Se detiene, NO evalúa el resto**

3️⃣ ¿`nota >= 60`? → No se evalúa
4️⃣ ¿`nota >= 40`? → No se evalúa
5️⃣ `else` → No se ejecuta

---

## Importante: Orden de las Condiciones

```python
# ❌ Orden incorrecto
nota = 85
if nota >= 40:          # Esto es True para 85
    print("Regular")    # Se ejecuta esto
elif nota >= 70:        # Nunca se llega aquí
    print("Muy Bueno")

# ✓ Orden correcto (de mayor a menor)
if nota >= 90:
    print("Excelente")
elif nota >= 70:
    print("Muy Bueno")
elif nota >= 40:
    print("Regular")
```

**Regla:** Siempre ir de **más restrictivo a menos restrictivo**

---

## Ejemplo: Consejo de Temperatura

```python
temperatura = int(input("Temperatura actual: "))

if temperatura >= 35:
    print("Extremadamente caluroso - Evitá la exposición al sol")
elif temperatura >= 25:
    print("Caluroso - Mantenete hidratado")
elif temperatura >= 15:
    print("Agradable - Clima ideal")
elif temperatura >= 5:
    print("Fresco - Llevá una campera")
else:
    print("Frío - Abrigate bien")
```

---

<!-- _class: lead -->

# Lazos: `while`

---

## ¿Qué es un Lazo?

Un **lazo** (loop o bucle) permite ejecutar código **repetidamente**.

El lazo `while` continúa ejecutándose **mientras** una condición sea verdadera.

```python
while condicion:
    # Bloque de código que se repite
    # mientras la condición sea True
```

---

## Ejemplo Simple de `while`

```python
contador = 1

while contador <= 5:
    print(f"Contador: {contador}")
    contador = contador + 1

print("Fin del lazo")
```

**Salida:**
```
Contador: 1
Contador: 2
Contador: 3
Contador: 4
Contador: 5
Fin del lazo
```

---

## Flujo de Ejecución del `while`

```python
contador = 1
while contador <= 5:
    print(contador)
    contador = contador + 1
```

**Proceso:**
1. ¿`contador <= 5`? → Sí (1 <= 5) → Ejecuta bloque
2. ¿`contador <= 5`? → Sí (2 <= 5) → Ejecuta bloque
3. ¿`contador <= 5`? → Sí (3 <= 5) → Ejecuta bloque
4. ¿`contador <= 5`? → Sí (4 <= 5) → Ejecuta bloque
5. ¿`contador <= 5`? → Sí (5 <= 5) → Ejecuta bloque
6. ¿`contador <= 5`? → No (6 > 5) → **Termina**

---

## 🚨 ¡Cuidado con los Lazos Infinitos!

Si la condición **nunca** se vuelve `False`, el lazo se ejecutará **para siempre**:

```python
# ❌ Lazo infinito
contador = 1
while contador <= 5:
    print(contador)
    # ¡Olvidamos incrementar!
    # contador siempre vale 1
```

```python
# ✓ Correcto
contador = 1
while contador <= 5:
    print(contador)
    contador = contador + 1  # ✓ Incrementa
```

---

## Checklist Anti-Lazos-Infinitos

Antes de ejecutar un `while`, verificá:

- [ ] ¿La condición puede volverse `False`?
- [ ] ¿Modifico las variables de la condición dentro del lazo?
- [ ] ¿Hay una forma de salir del lazo?

**Tip:** Si tu programa "se colgó", probablemente tenés un lazo infinito. Presiona **Ctrl+C** para detenerlo.

---

## Patrón: Acumulador

```python
# Calcular la suma de los primeros 10 números
suma = 0          # Acumulador (empieza en 0)
contador = 1

while contador <= 10:
    suma = suma + contador  # Acumula el valor
    contador = contador + 1

print(f"La suma de 1 a 10 es: {suma}")
# Salida: La suma de 1 a 10 es: 55
```

**Usos:** Sumar números, contar elementos, calcular promedios

---

## Patrón: Contador Regresivo

```python
print("Cuenta regresiva para despegue:")
numero = 10

while numero > 0:
    print(numero)
    numero = numero - 1

print("🚀 ¡Despegue!")
```

**Salida:**
```
Cuenta regresiva para despegue:
10
9
8
...
1
🚀 ¡Despegue!
```

---

## Patrón: Validación de Entrada

```python
edad = -1  # Valor inválido inicial

while edad < 0 or edad > 120:
    edad = int(input("Ingrese su edad (0-120): "))
    
    if edad < 0 or edad > 120:
        print("Error: Edad inválida. Intente nuevamente.")

print(f"Edad ingresada correctamente: {edad}")
```

**Este patrón se repite hasta que el usuario ingresa un valor válido**

---

<!-- _class: lead -->

# Lazos: `for`

---

## El Lazo `for`

El lazo `for` se usa para iterar sobre una **secuencia** (lista, rango, string, etc.)

```python
for variable in secuencia:
    # Código que se ejecuta
    # para cada elemento
```

**Diferencia con `while`:**
- `while` → "Hacé esto **mientras** X sea verdadero"
- `for` → "Hacé esto **para cada** elemento de la secuencia"

---

## Ejemplo Simple con `range()`

```python
for i in range(5):
    print(f"Iteración {i}")
```

**Salida:**
```
Iteración 0
Iteración 1
Iteración 2
Iteración 3
Iteración 4
```

**Nota:** `range(5)` genera números del 0 al 4 (5 números en total)

---

## La Función `range()`

`range()` genera una secuencia de números:

```python
# range(stop) → de 0 a stop-1
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# range(start, stop) → de start a stop-1
for i in range(2, 7):
    print(i)  # 2, 3, 4, 5, 6

# range(start, stop, step) → con saltos
for i in range(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8
```

---

## Iterar sobre Listas

```python
frutas = ["manzana", "banana", "naranja"]

for fruta in frutas:
    print(f"Me gusta la {fruta}")
```

**Salida:**
```
Me gusta la manzana
Me gusta la banana
Me gusta la naranja
```

**Python itera directamente sobre los elementos, no sobre índices**

---

## Iterar sobre Strings

```python
palabra = "Python"

for letra in palabra:
    print(letra)
```

**Salida:**
```
P
y
t
h
o
n
```

---

## Usando `enumerate()` para Índices

Si necesitás tanto el **índice** como el **elemento**, usá `enumerate()`:

```python
colores = ["rojo", "verde", "azul"]

for indice, color in enumerate(colores):
    print(f"Color {indice}: {color}")
```

**Salida:**
```
Color 0: rojo
Color 1: verde
Color 2: azul
```

**Empezar desde 1:**
```python
for indice, color in enumerate(colores, start=1):
    print(f"Color {indice}: {color}")
```

---

## Ejemplo: Tabla de Multiplicar

```python
numero = int(input("Ingrese un número: "))

print(f"\nTabla de multiplicar del {numero}:")
print("-" * 30)

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i:2d} = {resultado:3d}")
```

**Salida (para numero = 5):**
```
Tabla de multiplicar del 5:
------------------------------
5 x  1 =   5
5 x  2 =  10
5 x  3 =  15
...
5 x 10 =  50
```

---

## Ejemplo: Suma de Lista

```python
numeros = [10, 20, 30, 40, 50]
suma = 0

for numero in numeros:
    suma = suma + numero

print(f"La suma es: {suma}")
# Salida: La suma es: 150
```

---

<!-- _class: lead -->

# `while` vs `for`

---

## ¿Cuándo usar cada uno?

**Usar `while` cuando:**
- No conocés de antemano cuántas iteraciones necesitás
- La condición de parada es compleja
- El lazo puede no ejecutarse ninguna vez

**Usar `for` cuando:**
- Iterás sobre una secuencia conocida
- Conocés exactamente cuántas iteraciones necesitás
- Necesitás procesar cada elemento de una colección

---

## Ejemplo: `while` vs `for`

**Validación (usa `while`):**
```python
edad = -1
while edad < 0 or edad > 120:
    edad = int(input("Edad (0-120): "))
```

**Procesar lista (usa `for`):**
```python
for nombre in lista_nombres:
    print(nombre)
```

**Repetir N veces (usa `for`):**
```python
for i in range(10):
    print(i)
```

---

## Tabla Comparativa

| Aspecto | `while` | `for` |
|---------|---------|-------|
| **Iteraciones** | Número desconocido | Número conocido |
| **Condición** | Puede ser compleja | Implícita |
| **Uso típico** | Validaciones, menús | Procesar colecciones |
| **Riesgo** | Lazo infinito | Menor riesgo |

---

<!-- _class: lead -->

# Control de Lazos: `break` y `continue`

---

## `break`: Salir del Lazo

`break` **termina** el lazo inmediatamente

```python
contador = 1

while contador <= 10:
    if contador == 5:
        break  # Sale del lazo cuando contador es 5
    
    print(contador)
    contador += 1

print("Fin del lazo")
```

**Salida:**
```
1
2
3
4
Fin del lazo
```

---

## Ejemplo: Búsqueda con `break`

```python
numeros = [10, 25, 30, 45, 50]
objetivo = 30

for numero in numeros:
    if numero == objetivo:
        print(f"¡Encontrado! {numero}")
        break  # No sigue buscando
    print(f"Verificando {numero}...")

print("Búsqueda terminada")
```

**Salida:**
```
Verificando 10...
Verificando 25...
¡Encontrado! 30
Búsqueda terminada
```

---

## `continue`: Saltar a la Siguiente Iteración

`continue` **salta** al inicio del lazo para la siguiente iteración

```python
for i in range(1, 6):
    if i == 3:
        continue  # Salta cuando i es 3
    
    print(i)

print("Fin")
```

**Salida:**
```
1
2
4
5
Fin
```

---

## Ejemplo: Imprimir Solo Impares

```python
for numero in range(1, 11):
    if numero % 2 == 0:
        continue  # Salta los pares
    
    print(numero)
```

**Salida:**
```
1
3
5
7
9
```

---

## `break` vs `continue`

**`break`:**
- **Sale completamente** del lazo
- **Termina** todas las iteraciones
- Como decir "¡Ya terminé, salgo!"

**`continue`:**
- **Salta** la iteración actual
- **Continúa** con la siguiente
- Como decir "Salteo esta, sigo con la próxima"

---

## Ejemplo Combinado

```python
intentos = 0
MAX_INTENTOS = 3

while intentos < MAX_INTENTOS:
    password = input("Ingrese contraseña: ")
    intentos += 1
    
    if password == "":
        print("Contraseña vacía, intente nuevamente")
        continue  # Vuelve al inicio
    
    if password == "secreto123":
        print("¡Acceso concedido!")
        break  # Sale del lazo
    
    print(f"Contraseña incorrecta. Intentos restantes: {MAX_INTENTOS - intentos}")

if intentos == MAX_INTENTOS:
    print("Demasiados intentos fallidos. Acceso bloqueado.")
```

---

<!-- _class: lead -->

# Lazos Anidados

---

## Lazos Dentro de Lazos

Podés colocar lazos dentro de otros lazos. Cada iteración del lazo externo ejecuta **completamente** el lazo interno.

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"i={i}, j={j}")
```

**Salida:**
```
i=1, j=1
i=1, j=2
i=1, j=3
i=2, j=1
i=2, j=2
i=2, j=3
i=3, j=1
i=3, j=2
i=3, j=3
```

---

## Ejemplo: Tabla de Multiplicar Completa

```python
for numero in range(1, 6):
    print(f"\nTabla del {numero}:")
    for multiplicador in range(1, 11):
        resultado = numero * multiplicador
        print(f"{numero} x {multiplicador:2d} = {resultado:3d}")
```

---

## Ejemplo: Patrón de Asteriscos

```python
for fila in range(1, 6):
    for columna in range(fila):
        print("*", end="")
    print()  # Nueva línea
```

**Salida:**
```
*
**
***
****
*****
```

---

<!-- _class: lead -->

# Patrones Comunes

---

## Patrón 1: Menú Interactivo

```python
while True:
    print("\n=== MENÚ ===")
    print("1. Opción 1")
    print("2. Opción 2")
    print("3. Salir")
    
    opcion = input("\nElegí una opción: ")
    
    if opcion == "1":
        print("Ejecutando opción 1...")
    elif opcion == "2":
        print("Ejecutando opción 2...")
    elif opcion == "3":
        print("¡Hasta luego!")
        break
    else:
        print("Opción inválida")
```

---

## Patrón 2: Validación con Reintentos

```python
MAX_INTENTOS = 3
intentos = 0

while intentos < MAX_INTENTOS:
    valor = int(input("Ingrese un número entre 1 y 10: "))
    
    if 1 <= valor <= 10:
        print("¡Valor correcto!")
        break
    else:
        intentos += 1
        print(f"Error. Intentos restantes: {MAX_INTENTOS - intentos}")

if intentos == MAX_INTENTOS:
    print("Máximo de intentos alcanzado")
```

---

## Patrón 3: Acumulador con Promedio

```python
numeros = [10, 20, 30, 40, 50]
suma = 0
cantidad = 0

for numero in numeros:
    suma += numero
    cantidad += 1

promedio = suma / cantidad
print(f"Promedio: {promedio}")
```

---

## Patrón 4: Encontrar Máximo/Mínimo

```python
numeros = [23, 45, 12, 67, 34]

maximo = numeros[0]  # Inicializar con primer elemento

for numero in numeros:
    if numero > maximo:
        maximo = numero

print(f"El máximo es: {maximo}")
```

---

<!-- _class: lead -->

# Buenas Prácticas

---

## 1. Condiciones Claras

```python
# ❌ Confuso
if not (not es_activo):
    hacer_algo()

# ✓ Claro
if es_activo:
    hacer_algo()
```

---

## 2. Variables Descriptivas en Condiciones

```python
# ❌ Difícil de leer
if a > 18 and b == True and c != 0:
    hacer_algo()

# ✓ Más claro
es_mayor_edad = a > 18
esta_activo = b
tiene_saldo = c != 0

if es_mayor_edad and esta_activo and tiene_saldo:
    hacer_algo()
```

---

## 3. Evitar Anidación Excesiva

```python
# ❌ Muy anidado
if condicion1:
    if condicion2:
        if condicion3:
            hacer_algo()

# ✓ Mejor: combinar condiciones
if condicion1 and condicion2 and condicion3:
    hacer_algo()
```

---

## 4. Usar Constantes para Valores Mágicos

```python
# ❌ "Números mágicos"
if edad >= 18 and edad <= 65:
    calcular_descuento()

# ✓ Constantes descriptivas
EDAD_MINIMA = 18
EDAD_MAXIMA = 65

if edad >= EDAD_MINIMA and edad <= EDAD_MAXIMA:
    calcular_descuento()
```

---

## 5. Nombres Descriptivos en Lazos

```python
# ❌ Poco claro
for i in lista:
    procesar(i)

# ✓ Descriptivo
for estudiante in lista_estudiantes:
    procesar_estudiante(estudiante)
```

---

<!-- _class: lead -->

# Resumen

---

## Conceptos Clave

**Condicionales:**
- `if` → Una sola condición
- `if-else` → Dos alternativas
- `if-elif-else` → Múltiples alternativas

**Lazos:**
- `while` → Repite mientras condición sea True
- `for` → Itera sobre secuencias

**Control de lazos:**
- `break` → Sale del lazo
- `continue` → Salta a la siguiente iteración

---

## Estructura de un Programa con Control de Flujo

```python
# 1. Validación de entrada
edad = int(input("Ingrese edad: "))

# 2. Decisión
if edad >= 18:
    print("Mayor de edad")
else:
    print("Menor de edad")

# 3. Lazo para procesar
for i in range(5):
    print(f"Iteración {i}")

# 4. Lazo con condición
contador = 0
while contador < 3:
    print(contador)
    contador += 1
```

---

## ¿Cuándo usar cada estructura?

**`if`:** Una decisión simple
**`if-elif-else`:** Múltiples opciones excluyentes
**`while`:** Repetir hasta que algo cambie
**`for`:** Procesar cada elemento de una colección
**`break`:** Salir anticipadamente de un lazo
**`continue`:** Saltar elementos específicos

---

## Errores Comunes a Evitar

❌ Olvidar la indentación
❌ Olvidar los dos puntos (`:`)
❌ Lazos infinitos (no cambiar la condición)
❌ Confundir `=` con `==`
❌ No validar la entrada del usuario
❌ Anidación excesiva

---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

El control de flujo es lo que hace que tus programas sean **inteligentes y útiles**.

Practicá con ejercicios para dominar estas estructuras fundamentales.
