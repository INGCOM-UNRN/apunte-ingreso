---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Control de Flujo en Python'
footer: 'Condicionales y estructuras de repetición'
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Control de Flujo en Python

**Condicionales y estructuras de repetición**

<!--
¡Buenas! Hoy nos metemos en uno de los temas más divertidos y poderosos de la programación: el Control de Flujo. Hasta ahora veníamos escribiendo recetas de cocina que se leían de arriba a abajo sin chistar. Hoy vamos a darle cerebro a nuestros programas para que puedan tomar decisiones y repetir tareas aburridas por nosotros.
-->
---

## ¿Qué vas a aprender?

* Cómo hacer que tu programa **tome decisiones** (`if`, `elif`, `else`)
* Repetir acciones con **`while`** y **`for`**
* Controlar lazos con **`break`** y **`continue`**
* **Patrones comunes** de programación

<!--
¿Cuál es el menú de hoy? Vamos a aprender a usar la sentencia `if` para decidir qué camino tomar. Después vamos a ver cómo repetir cosas con `while` y `for`, que son los caballos de batalla de cualquier programador. También vamos a ver cómo frenar o saltar pasos con `break` y `continue`. Y para cerrar, algunos patrones que van a usar hasta el hartazgo.
-->
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

<!--
Imaginen que su programa es un tren. Sin control de flujo, va derecho por la vía, estación por estación, sin poder desviarse. Eso es aburrido y poco útil. Con control de flujo, ponemos cambios de vía. Dependiendo de la hora, del clima, o de lo que quiera el usuario, el tren toma un camino u otro. Eso es inteligencia.
-->
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

<!--
Piensen en un semáforo. Es el ejemplo clásico. El auto (tu programa) llega a la esquina y mira. ¿Está en verde? Avanzo. ¿Amarillo? Precaución. ¿Rojo? Freno. Esa capacidad de observar el estado actual (`color_semaforo`) y actuar en consecuencia es lo que vamos a construir hoy.
-->
---

## Ejemplos del Mundo Real

**🏧 Cajero Automático:** ¿El PIN es correcto? Permitir 3 intentos
**🎮 Videojuego:** ¿El jugador chocó? Loop principal del juego
**🌡️ Termostato:** ¿Temperatura baja? Encender/apagar calefacción
**📱 App de Mensajes:** ¿Hay conexión? Revisar nuevos mensajes

<!--
Esto no es teoría abstracta, lo ven todos los días. Cuando el cajero te pide el PIN y te da 3 intentos, hay un contador y una condición. En un videojuego, el `loop` principal pregunta todo el tiempo '¿te chocaron?'. El termostato de casa decide si prender la estufa. Todo esto son `if` y `bucles`.
-->
---

<!-- _class: lead -->

# Condicionales: `if`

<!--
Arrancamos con el `if`. Es la unidad básica de decisión. 'Si pasa esto, hacé aquello'. Corta la bocha.
-->
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

<!--
La sintaxis es simple pero estricta. `if`, la condición, y los dos puntos `:`. Si la condición es `True` (verdadera), se ejecuta lo que está indentado abajo. Si no, el programa sigue de largo y se saltea ese bloque. Fíjense en el ejemplo de la edad.
-->
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

<!--
Desglosemos la anatomía del `if`. La palabra reservada `if`. La condición `temperatura > 30` que devuelve Verdadero o Falso. Los dos puntos `:`, que son como abrir la puerta. Y la indentación, que es el contenido de la habitación. Si no abrís la puerta (condición False), no entrás a la habitación.
-->
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

<!--
¡Ojo al piojo con esto! En Python, la indentación no es estética, es LEY. Si escribís pegado al margen izquierdo, estás fuera del bloque. Tenés que dejar 4 espacios (o un tabulador). Es la forma que tiene Python de saber dónde empieza y dónde termina el bloque de decisión.
-->
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

<!--
Las condiciones son preguntas de Sí o No. ¿Es mayor de 18? ¿Es igual a 18? ¿Es distinto de 21? Cualquier expresión que se pueda evaluar a `True` o `False` sirve acá.
-->
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

<!--
El bloque indentado puede tener una, dos o mil líneas. Todo lo que esté corrido a la derecha bajo el `if` se ejecuta en conjunto. Si la condición falla, se saltea TODO ese bloque. La línea 'Fin del programa', al estar sin indentar, se ejecuta siempre, pase lo que pase.
-->
---

<!-- _class: lead -->

# Condicionales: `if-else`

<!--
A veces no alcanza con 'hacer o no hacer'. A veces queremos 'hacer esto O hacer aquello'. Ahí entra el `else` (si no).
-->
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

<!--
El `if-else` cubre todos los casos. Es binario. Si llueve, llevo paraguas. SI NO (`else`), llevo anteojos de sol. No hay punto medio acá. O entrás al `if` o entrás al `else`.
-->
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

<!--
Es como tirar una moneda. Cara o Cruz. No puede caer de canto (bueno, en programación no). Si la condición del `if` es verdadera, ejecutamos el primer bloque. Si es falsa, automáticamente caemos en el `else`. Es la red de seguridad para 'todo lo demás'.
-->
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

<!--
¿Cuándo lo usamos? Cuando las opciones son mutuamente excluyentes y cubren todo el espectro de posibilidades que nos interesa. Aprobado/Desaprobado. Mayor/Menor. Encendido/Apagado.
-->
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

<!--
Miren la diferencia. A la izquierda, el `if` solo. Si no hay sol, no hago nada. A la derecha, el `if-else`. Si no hay sol, tengo un plan B (quedarme en casa). El `else` garantiza que SIEMPRE pase algo.
-->
---

<!-- _class: lead -->

# Condicionales: `if-elif-else`

<!--
¿Y si hay más de dos opciones? No todo es blanco o negro. A veces hay gris, rojo, azul... Para eso está el `elif`, que es una abreviación de 'else if'.
-->
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

<!--
Esta estructura es una escalera. El programa va bajando escalón por escalón preguntando. ¿Se cumple la 1? No. ¿La 2? No. ¿La 3? Sí. Entro ahí y me voy. El `else` final es opcional y sirve como 'si no fue ninguna de las anteriores'.
-->
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

<!--
El sistema de notas es el mejor ejemplo. No es solo aprobar o reprobar. Tenés A, B, C, D... Fíjense cómo vamos preguntando en orden.
-->
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

<!--
Esto es clave: el programa es vago. En cuanto encuentra una condición verdadera, ejecuta ese bloque y SE VA. No sigue preguntando. Si sacaste 95, entra en el primer `if`, imprime 'Excelente' y salta al final. No pierde tiempo mirando si es mayor a 70.
-->
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

<!--
El orden importa muchísimo. Si preguntás primero '¿es mayor a 40?', un alumno con 90 va a entrar ahí y le vas a decir 'Regular'. Siempre ordenen las condiciones de la más específica a la más general, o usen rangos bien definidos.
-->
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

<!--
Un ejemplo práctico con el clima. Fíjense cómo cubrimos todo el rango de temperaturas. Desde el infierno (35 grados) hasta el frío polar (else).
-->
---

<!-- _class: lead -->

# Lazos: `while`

<!--
Cambiamos de marcha. Dejamos las decisiones y pasamos a la repetición. Los Lazos o Bucles (`loops`). El primero es el `while` (mientras).
-->
---

## ¿Qué es un Lazo?

Un **lazo** (loop o bucle) permite ejecutar código **repetidamente**.

El lazo `while` continúa ejecutándose **mientras** una condición sea verdadera.

```python
while condicion:
    # Bloque de código que se repite
    # mientras la condición sea True
```

<!--
El `while` es el hermano repetitivo del `if`. Mientras la condición sea verdadera, el bloque de código se repite una y otra vez. Es ideal cuando no sabés cuántas veces tenés que repetir algo.
-->
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

<!--
Miren este contador. Arranca en 1. Pregunta: ¿1 <= 5? Sí. Imprime y suma 1. Ahora vale 2. ¿2 <= 5? Sí... y así hasta que vale 6. Ahí la condición falla y el lazo termina.
-->
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

<!--
Acá tienen el paso a paso. Es fundamental entender que la condición se evalúa ANTES de cada iteración. Si de entrada es falsa, el cuerpo del lazo nunca se ejecuta.
-->
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

<!--
¡Peligro! Si se olvidan de incrementar el contador, la condición `1 <= 5` va a ser verdadera por los siglos de los siglos. Eso es un 'infinite loop' y les va a colgar el programa. Siempre asegúrense de que la condición de salida se pueda cumplir.
-->
---

## Checklist Anti-Lazos-Infinitos

Antes de ejecutar un `while`, verificá:

- [ ] ¿La condición puede volverse `False`?
- [ ] ¿Modifico las variables de la condición dentro del lazo?
- [ ] ¿Hay una forma de salir del lazo?

**Tip:** Si tu programa "se colgó", probablemente tenés un lazo infinito. Presiona **Ctrl+C** para detenerlo.

<!--
Háganse un tatuaje mental con este checklist. Antes de correr un `while`: ¿Tengo condición de salida? ¿Estoy modificando la variable que controla el lazo? Si no, Ctrl+C es su mejor amigo para matar el proceso.
-->
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

<!--
El patrón del Acumulador es un clásico. Una variable (la bolsa) que empieza vacía (0). Recorro cosas y las voy sumando a la bolsa. Al final, tengo el total. Se usa para todo: sumas, promedios, inventarios.
-->
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

<!--
El contador regresivo es lo mismo pero restando. Útil para... bueno, para lanzamientos de cohetes y para iterar listas al revés.
-->
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

<!--
Este es EL caso de uso del `while`: validar input. 'Mientras me des basura, te sigo pidiendo el dato'. No sabés si el usuario va a tardar 1 intento o 50, así que el `while` es perfecto acá.
-->
---

<!-- _class: lead -->

# Lazos: `for`

<!--
Ahora pasamos al `for`. Es el lazo elegante. Se usa cuando querés recorrer una colección de cosas (una lista, una frase) o repetir algo una cantidad exacta de veces.
-->
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

<!--
La diferencia mental es clave: `while` es 'mientras pase esto'. `for` es 'para cada elemento de esto'. El `for` es más seguro porque difícilmente generes un lazo infinito.
-->
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

<!--
`range(5)` es una función mágica que nos da los números 0, 1, 2, 3, 4. El `for` toma uno por uno y lo guarda en la variable `i` (o como la llamen) para que la uses.
-->
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

<!--
La función `range` es muy flexible. Puede ir hasta un número, ir de un inicio a un fin, o ir saltando de a pasos (step). Jueguen con esto.
-->
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

<!--
Acá es donde Python brilla. `for fruta in frutas`. Se lee como español. No tenés que andar con índices `i`, ni corchetes. Python te da el elemento directamente.
-->
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

<!--
Los strings también son colecciones (de letras). Así que podés iterar sobre una palabra letra por letra.
-->
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

<!--
A veces necesitás el índice (la posición) y el valor. `enumerate` te da las dos cosas. Es mucho más 'pythónico' que usar un contador manual.
-->
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

---
---
---
---
---
---
---
---
---<!--
Un clásico de la primaria: las tablas. Fíjense cómo usamos el `for` para ir del 1 al 10 y f-strings para que quede todo alineado y prolijo.
-->
---
5 x  1 =   5
5 x  2 =  10
5 x  3 =  15
...
5 x 10 =  50
```

<!--
Otro patrón clásico: sumar elementos de una lista. Es igual al acumulador que vimos antes, pero más limpio con un `for`.
-->
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

<!--
Batalla de titanes: `while` vs `for`. ¿Cuál uso?
-->
---

<!-- _class: lead -->

# `while` vs `for`

<!--
Resumen brutal: Si sabés cuántas veces va a pasar (o tenés una lista), usá `for`. Si no tenés idea y depende de una condición dinámica (como que el usuario escriba 'salir'), usá `while`.
-->
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

<!--
Miren los ejemplos. Validación -> `while`. Recorrer lista -> `for`. Repetir N veces -> `for` con range. Simple.
-->
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

<!--
Esta tabla es para tenerla a mano. El `while` es más flexible pero más riesgoso. El `for` es más estructurado y seguro.
-->
---

## Tabla Comparativa

| Aspecto | `while` | `for` |
|
---
---
---|
---
---
---|
---
----|
| **Iteraciones** | Número desconocido | Número conocido |
| **Condición** | Puede ser compleja | Implícita |
| **Uso típico** | Validaciones, menús | Procesar colecciones |
| **Riesgo** | Lazo infinito | Menor riesgo |

<!--
A veces queremos tener más control dentro del lazo. Para eso existen `break` (romper) y `continue` (continuar).
-->
---

<!-- _class: lead -->

# Control de Lazos: `break` y `continue`

<!--
`break` es el botón de ejección. No importa si la condición sigue siendo verdadera o si faltan elementos, `break` corta el lazo en seco y salta afuera.
-->
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

<!--
El uso más común del `break`: búsquedas. Voy mirando elementos. ¿Es este? Sí. Listo, `break`, dejo de buscar. No tiene sentido seguir mirando si ya encontré lo que quería.
-->
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

<!--
`continue` es más sutil. Dice: 'Listo con esta vuelta, pasemos a la siguiente'. Ignora todo lo que queda de código en ESA iteración y vuelve arriba.
-->
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

<!--
Fíjense acá. Si es par, `continue`. O sea, no imprimas, andá al siguiente número. Resultado: solo se imprimen los impares.
-->
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

<!--
En resumen: `break` destruye el lazo. `continue` solo saltea la vuelta actual.
-->
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

<!--
Acá combinamos todo. Un `while` para los intentos. Un `continue` si no escribiste nada (te doy otra chance sin contar intento). Un `break` si acertaste. Es lógica de login real.
-->
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

<!--
Lazos Anidados. Un lazo adentro de otro. Como un reloj: por cada vuelta de la aguja de horas, la de minutos da 60 vueltas.
-->
---

<!-- _class: lead -->

# Lazos Anidados

<!--
El lazo externo (i) se queda quieto mientras el interno (j) hace todo su recorrido. Después el externo avanza un paso y el interno arranca de nuevo. Ojo que esto puede hacer el programa lento si los números son grandes.
-->
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

<!--
Tablas de multiplicar completas. Por cada número del 1 al 5 (externo), multiplico por 1 al 10 (interno).
-->
---

## Ejemplo: Tabla de Multiplicar Completa

```python
for numero in range(1, 6):
    print(f"\nTabla del {numero}:")
    for multiplicador in range(1, 11):
        resultado = numero * multiplicador
        print(f"{numero} x {multiplicador:2d} = {resultado:3d}")
```

<!--
Esto es muy común para gráficos o matrices. El externo maneja las filas, el interno las columnas (o los caracteres de la línea).
-->
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

<!--
Vamos a ver los 'Greatest Hits' de los patrones de control de flujo. Estas estructuras las van a copiar y pegar en mil proyectos.
-->
---

<!-- _class: lead -->

# Patrones Comunes

<!--
El menú infinito. `while True` crea un bucle eterno, y usamos `break` en la opción de 'Salir' para cortarlo. Es la base de cualquier CLI (interfaz de línea de comandos).
-->
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

<!--
Validación robusta. Te pido el dato. Si está bien, `break`. Si no, te aviso y te descuento un intento. Si te quedás sin intentos, fuiste.
-->
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

<!--
Promedio. Necesitás dos acumuladores: uno para la suma total y otro (contador) para saber cuántos elementos eran. Al final dividís.
-->
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

<!--
Búsqueda del máximo (Rey de la colina). Asumís que el primero es el rey. Vas desafiando con los demás. Si alguien es más grande, le saca la corona (`maximo = numero`).
-->
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

<!--
Para cerrar, consejos para que su código no sea un plato de fideos.
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
Eviten las dobles negaciones. `if not (not activo)` es confuso. `if activo` es claro. La legibilidad cuenta.
-->
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

<!--
Pongan nombres booleanos a las condiciones complejas. En lugar de un `if` kilométrico, guarden el resultado en una variable `es_valido` y usen eso. Se lee como prosa.
-->
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

<!--
El 'Arrow Code' (código flecha) es feo. Si tenés muchos `if` anidados, intentá reestructurar. A veces usar `and` ayuda, o retornar antes.
-->
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

<!--
Nada de números mágicos. Si ven un `18` o un `65` sueltos en el código, no se entiende qué son. Definan constantes `EDAD_JUBILACION = 65`. Ayuda a entender y a cambiarlo fácil mañana.
-->
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

<!--
En los `for`, la variable iteradora importa. `for x in y:` no me dice nada. `for cliente in lista_clientes:` me cuenta una historia.
-->
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

<!--
Hicimos un viaje largo. Repasemos las herramientas que sumaron a su cinturón hoy.
-->
---

<!-- _class: lead -->

# Resumen

<!--
If/Else para decidir. While/For para repetir. Break/Continue para controlar. Con esto ya pueden resolver casi cualquier problema lógico.
-->
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

<!--
Fíjense cómo se combinan. Entrada de datos, validación, decisiones y procesos repetitivos. Es el esqueleto de cualquier software.
-->
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

<!--
Acá tienen el machete oficial. Úsenlo para decidir qué herramienta sacar de la caja.
-->
---

## ¿Cuándo usar cada estructura?

**`if`:** Una decisión simple
**`if-elif-else`:** Múltiples opciones excluyentes
**`while`:** Repetir hasta que algo cambie
**`for`:** Procesar cada elemento de una colección
**`break`:** Salir anticipadamente de un lazo
**`continue`:** Saltar elementos específicos

<!--
Y cuidado con los clásicos errores: la indentación (siempre 4 espacios), los dos puntos, y los bucles infinitos. Son el bautismo de fuego de todo programador Python.
-->
---

## Errores Comunes a Evitar

❌ Olvidar la indentación
❌ Olvidar los dos puntos (`:`)
❌ Lazos infinitos (no cambiar la condición)
❌ Confundir `=` con `==`
❌ No validar la entrada del usuario
❌ Anidación excesiva

<!--
¡Eso es todo amigos! Ahora les toca a ustedes. El control de flujo se aprende rompiendo y arreglando lazos. ¡A codear!
-->
---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

El control de flujo es lo que hace que tus programas sean **inteligentes y útiles**.

Practicá con ejercicios para dominar estas estructuras fundamentales.
