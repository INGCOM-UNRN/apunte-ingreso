# Ejercicios de Programación - Primeros Pasos

## Ejercicios de Programación

Estos ejercicios tienen **ayuda decreciente**. Los primeros te dan casi todo resuelto, los últimos solo el enunciado.

:::{important} Metodología
Para TODOS los ejercicios:

1. **Responder las 5 preguntas** antes de programar
2. **Hacer el pseudocódigo o diagrama** en papel
3. **Prueba de escritorio** con al menos 2 casos
4. **Recién ahí programar en Python**
5. **Probar con los mismos casos** de la prueba de escritorio
:::

---

### Nivel 1: Con Diagrama Completo (Ejercicios 1-3)

Estos ejercicios te dan el diagrama de flujo completo. Tu tarea es traducirlo a Python.

---

### Ejercicio 1: Suma de Dos Números

**Enunciado:** Pedir dos números al usuario y mostrar su suma.

**Diagrama de flujo (completo):**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input1[/LEER num1/]
    Input2[/LEER num2/]
    Process[suma = num1 + num2]
    Output[/MOSTRAR suma/]
    End([FIN])
    
    Start --> Input1
    Input1 --> Input2
    Input2 --> Process
    Process --> Output
    Output ---> End

    style End fill:#FFB6C1
    style Input1 fill:#87CEEB
    style Input2 fill:#87CEEB
    style Output fill:#87CEEB
    style Process fill:#FFE4B5
    style Start fill:#90EE90
```

**Casos de prueba:**
- num1 = 5, num2 = 3 → suma = 8
- num1 = -2, num2 = 7 → suma = 5

**Ayuda:** Traducí cada caja del diagrama a una línea de Python:
```python
# INICIO
# LEER num1 → num1 = int(input(...))
# LEER num2 → ...
# suma = num1 + num2
# MOSTRAR suma → print(...)
# FIN
```

---

### Ejercicio 2: Calcular Precio Final con IVA

**Enunciado:** Pedir el precio de un producto y calcular el precio final agregando 21% de IVA.

**Diagrama de flujo (completo):**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER precio/]
    Calc1[iva = precio * 0.21]
    Calc2[precioFinal = precio + iva]
    Output[/MOSTRAR precioFinal/]
    End([FIN])
    
    Start --> Input
    Input --> Calc1
    Calc1 --> Calc2
    Calc2 --> Output
    Output ---> End

    style Calc1 fill:#FFE4B5
    style Calc2 fill:#FFE4B5
    style End fill:#FFB6C1
    style Input fill:#87CEEB
    style Output fill:#87CEEB
    style Start fill:#90EE90
```

**Casos de prueba:**
- precio = 100 → precioFinal = 121
- precio = 50 → precioFinal = 60.5

**Ayuda:** El IVA se calcula multiplicando por 0.21 (que es el 21%).

---

### Ejercicio 3: Par o Impar

**Enunciado:** Pedir un número y decir si es par o impar.

**Diagrama de flujo (completo):**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER numero/]
    Decision{numero % 2 == 0?}
    OutputPar[/MOSTRAR Es par/]
    OutputImpar[/MOSTRAR Es impar/]
    End([FIN])
    
    Start --> Input
    Input --> Decision
    Decision -->|Sí| OutputPar
    Decision -->|No| OutputImpar
    OutputPar ---> End
    OutputImpar ---> End

    style Decision fill:#FFD700
    style End fill:#FFB6C1
    style Input fill:#87CEEB
    style OutputImpar fill:#87CEEB
    style OutputPar fill:#87CEEB
    style Start fill:#90EE90
```

**Casos de prueba:**
- numero = 8 → "Es par"
- numero = 13 → "Es impar"

**Ayuda:** El operador `%` (módulo) da el resto de la división. Si el resto es 0, es par.

---

### Nivel 2: Con Pseudocódigo Completo (Ejercicios 4-6)

Estos ejercicios te dan el pseudocódigo completo. Tu tarea es traducirlo a Python.

---

### Ejercicio 4: Multiplicar Dos Números

**Enunciado:** Pedir dos números y mostrar su producto (multiplicación).

**Pseudocódigo (completo):**

```
INICIO MultiplicarNumeros
    MOSTRAR "Ingrese el primer número:"
    LEER num1
    
    MOSTRAR "Ingrese el segundo número:"
    LEER num2
    
    producto = num1 * num2
    
    MOSTRAR "El producto es:", producto
FIN
```

**Casos de prueba:**
- num1 = 4, num2 = 7 → producto = 28
- num1 = -3, num2 = 5 → producto = -15

**Ayuda:** Cada línea del pseudocódigo se traduce casi directamente a Python.

---

### Ejercicio 5: Verificar Mayoría de Edad

**Enunciado:** Pedir la edad y verificar si es mayor de edad (>= 18).

**Pseudocódigo (completo):**

```
INICIO VerificarMayoriaEdad
    MOSTRAR "Ingrese su edad:"
    LEER edad
    
    SI edad >= 18 ENTONCES
        MOSTRAR "Sos mayor de edad"
    SINO
        MOSTRAR "Sos menor de edad"
    FIN_SI
FIN
```

**Casos de prueba:**
- edad = 20 → "Sos mayor de edad"
- edad = 15 → "Sos menor de edad"
- edad = 18 → "Sos mayor de edad" (caso borde)

**Ayuda:** `SI ... ENTONCES ... SINO` se traduce a `if ... : ... else:`

---

### Ejercicio 6: Contar del 1 al N

**Enunciado:** Pedir un número N y mostrar todos los números del 1 al N.

**Pseudocódigo (completo):**

```
INICIO ContarHastaN
    MOSTRAR "Ingrese un número:"
    LEER n
    
    contador = 1
    MIENTRAS contador <= n HACER
        MOSTRAR contador
        contador = contador + 1
    FIN_MIENTRAS
FIN
```

**Casos de prueba:**
- n = 5 → muestra: 1, 2, 3, 4, 5
- n = 3 → muestra: 1, 2, 3

**Ayuda:** `MIENTRAS ... HACER` se traduce a `while ...:`. No olvides incrementar el contador.

---

### Nivel 3: Con Estructura Parcial (Ejercicios 7-10)

Estos ejercicios te dan parte del código o estructura. Completá lo que falta.

---

### Ejercicio 7: Calcular Promedio de Tres Notas

**Enunciado:** Pedir tres notas y calcular su promedio.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Tres notas (números)
2. **¿Qué resultado quiero?** El promedio de las tres notas
3. **¿Qué pasos debo seguir?** Leer las tres notas, sumarlas, dividir por 3
4. **¿Hay situaciones especiales?** No (asumimos notas válidas)
5. **¿Necesito repetir algo?** No

**Estructura parcial (completá lo que falta):**

```python
# Pedir las tres notas
nota1 = int(input("Nota 1: "))
# _____ (completá para nota2)
# _____ (completá para nota3)

# Calcular el promedio
# suma = _____
# promedio = _____

# Mostrar el resultado
# print(_____)
```

**Casos de prueba:**
- notas: 8, 7, 9 → promedio = 8.0
- notas: 10, 6, 8 → promedio = 8.0

---

### Ejercicio 8: Número Positivo, Negativo o Cero

**Enunciado:** Pedir un número y decir si es positivo, negativo o cero.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Un número
2. **¿Qué resultado quiero?** Clasificarlo en positivo/negativo/cero
3. **¿Qué pasos debo seguir?** Leer el número, verificar con if
4. **¿Hay situaciones especiales?** Sí, el cero es un caso especial
5. **¿Necesito repetir algo?** No

**Estructura parcial:**

```python
numero = int(input("Ingrese un número: "))

if numero > 0:
    # _____ (completá)
elif numero < 0:
    # _____ (completá)
else:
    # _____ (completá - caso del cero)
```

**Casos de prueba:**
- numero = 10 → "Positivo"
- numero = -5 → "Negativo"
- numero = 0 → "Cero"

---

### Ejercicio 9: Tabla de Multiplicar

**Enunciado:** Pedir un número y mostrar su tabla de multiplicar del 1 al 10.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Un número
2. **¿Qué resultado quiero?** La tabla del 1 al 10 de ese número
3. **¿Qué pasos debo seguir?** Leer número, lazo del 1 al 10, multiplicar y mostrar
4. **¿Hay situaciones especiales?** No
5. **¿Necesito repetir algo?** Sí, 10 veces

**Estructura parcial:**

```python
numero = int(input("Ingrese un número: "))

# Usar un lazo while o for
i = 1
while i <= 10:
    # resultado = _____
    # print(_____)
    # i = _____
```

**Caso de prueba:**
- numero = 7 → muestra: 7, 14, 21, 28, 35, 42, 49, 56, 63, 70

**Pista:** Dentro del lazo, multiplicá `numero * i`.

---

### Ejercicio 10: Sumar Números Hasta Cero

**Enunciado:** Pedir números al usuario y sumarlos. Cuando ingrese 0, terminar y mostrar la suma total.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Números hasta que ingrese 0
2. **¿Qué resultado quiero?** La suma de todos los números (sin contar el 0)
3. **¿Qué pasos debo seguir?** Inicializar suma en 0, lazo que lee números y los suma, terminar cuando sea 0
4. **¿Hay situaciones especiales?** El 0 termina pero no se suma
5. **¿Necesito repetir algo?** Sí, mientras no ingresen 0

**Pistas (sin código):**
- Usá una variable `suma` inicializada en 0
- Usá un lazo `while` que se repita mientras el número NO sea 0
- Lee el número ANTES del lazo y también DENTRO del lazo
- Al final del lazo, mostrar la suma

**Caso de prueba:**
- Ingresos: 5, 3, 8, 2, 0 → suma = 18

---

### Nivel 4: Solo las 5 Preguntas (Ejercicios 11-13)

Estos ejercicios te dan las 5 preguntas respondidas. Vos hacés el resto.

---

### Ejercicio 11: Calcular Factorial

**Enunciado:** Pedir un número N y calcular su factorial (N! = 1 × 2 × 3 × ... × N).

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Un número entero N
2. **¿Qué resultado quiero?** El factorial de N
3. **¿Qué pasos debo seguir?** Leer N, multiplicar 1 × 2 × 3 × ... × N
4. **¿Hay situaciones especiales?** 0! = 1, números negativos no tienen factorial
5. **¿Necesito repetir algo?** Sí, multiplicar N veces

**Tareas:**
1. Hacer el pseudocódigo o diagrama
2. Prueba de escritorio con N = 5 (resultado debe ser 120)
3. Programar en Python

**Casos de prueba:**
- N = 5 → 120 (5! = 1×2×3×4×5)
- N = 3 → 6 (3! = 1×2×3)
- N = 0 → 1 (caso especial)

**Pista:** Usá una variable `factorial = 1` y multiplicala N veces.

---

### Ejercicio 12: Contar Dígitos de un Número

**Enunciado:** Pedir un número entero y contar cuántos dígitos tiene.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** Un número entero
2. **¿Qué resultado quiero?** La cantidad de dígitos
3. **¿Qué pasos debo seguir?** Dividir el número por 10 repetidamente hasta que sea 0, contar cuántas veces
4. **¿Hay situaciones especiales?** Los números negativos (considerá su valor absoluto)
5. **¿Necesito repetir algo?** Sí, mientras el número sea mayor que 0

**Tareas:**
1. Hacer el pseudocódigo o diagrama
2. Prueba de escritorio con número = 12345 (resultado = 5)
3. Programar en Python

**Casos de prueba:**
- numero = 12345 → 5 dígitos
- numero = 7 → 1 dígito
- numero = 1000 → 4 dígitos

**Pista:** En cada iteración, dividí el número por 10 (división entera `//`) y aumentá un contador.

---

### Ejercicio 13: Adivinar un Número

**Enunciado:** El programa "piensa" un número del 1 al 100. El usuario intenta adivinarlo. El programa dice si el número ingresado es mayor, menor o correcto. Cuando adivine, mostrar cuántos intentos le tomó.

**Las 5 Preguntas (respondidas):**

1. **¿Qué datos necesito?** El número secreto (fijo en el código o aleatorio), intentos del usuario
2. **¿Qué resultado quiero?** Decir "ganaste" cuando adivine y mostrar cantidad de intentos
3. **¿Qué pasos debo seguir?** Generar número secreto, lazo: leer intento, comparar, dar pista, repetir hasta que adivine
4. **¿Hay situaciones especiales?** Verificar que el número esté entre 1 y 100
5. **¿Necesito repetir algo?** Sí, hasta que adivine

**Tareas:**
1. Hacer el pseudocódigo o diagrama
2. Prueba de escritorio (simulá algunos intentos)
3. Programar en Python

**Pista:** Para empezar, podés usar un número fijo como `numeroSecreto = 42`. Más adelante podés usar `import random` para generar uno aleatorio.

---

### Nivel 5: Solo Enunciado (Ejercicios 14-15)

Estos ejercicios solo tienen el enunciado. Vos hacés TODO el proceso.

---

### Ejercicio 14: Números Primos

**Enunciado:** Pedir un número N y verificar si es primo o no. Un número es primo si solo es divisible por 1 y por sí mismo.

**Casos de prueba:**
- N = 7 → "Es primo"
- N = 10 → "No es primo"
- N = 2 → "Es primo"

**Proceso completo:**
1. Responder las 5 preguntas
2. Hacer pseudocódigo o diagrama
3. Prueba de escritorio con los casos dados
4. Programar en Python
5. Probar con los mismos casos

**Pistas:**
- Un número es primo si ningún número entre 2 y N-1 lo divide exactamente
- Usá un lazo para probar divisores
- Si encontrás un divisor, no es primo

---

### Ejercicio 15: Serie de Fibonacci

**Enunciado:** Pedir un número N y mostrar los primeros N términos de la serie de Fibonacci. La serie comienza con 0 y 1, y cada término siguiente es la suma de los dos anteriores: 0, 1, 1, 2, 3, 5, 8, 13, ...

**Casos de prueba:**
- N = 7 → 0, 1, 1, 2, 3, 5, 8
- N = 5 → 0, 1, 1, 2, 3

**Proceso completo:**
1. Responder las 5 preguntas
2. Hacer pseudocódigo o diagrama
3. Prueba de escritorio con N = 5
4. Programar en Python
5. Probar con los casos dados

**Pistas:**
- Necesitás tres variables: los dos números anteriores y el actual
- En cada iteración: calcular el nuevo término, mostrar, y actualizar las variables

---

## Soluciones

:::{admonition} 💡 Antes de Ver las Soluciones
:class: warning

**Para las Pruebas de Escritorio:** Intentá hacerlas completamente vos mismo primero. El objetivo es que aprendas a verificar algoritmos.

**Para los Ejercicios de Programación:** Seguí TODOS los pasos:
1. Las 5 preguntas
2. Pseudocódigo/diagrama
3. Prueba de escritorio
4. Código Python
5. Pruebas

Solo consultá las soluciones si:
- Ya intentaste seriamente
- Estás trabado y no sabés cómo seguir
- Querés comparar tu solución con otra

:::

---

### Soluciones - Ejercicios de Programación

#### Solución Ejercicio 1: Suma de Dos Números

```python
# Pedir dos números
num1 = int(input("Ingrese el primer número: "))
num2 = int(input("Ingrese el segundo número: "))

# Calcular la suma
suma = num1 + num2

# Mostrar el resultado
print("La suma es:", suma)
```

---

#### Solución Ejercicio 2: Precio con IVA

```python
# Pedir el precio
precio = float(input("Ingrese el precio del producto: "))

# Calcular IVA y precio final
iva = precio * 0.21
precio_final = precio + iva

# Mostrar el resultado
print("Precio final con IVA:", precio_final)
```

**Nota:** Usamos `float()` porque el precio puede tener decimales.

---

#### Solución Ejercicio 3: Par o Impar

```python
# Pedir el número
numero = int(input("Ingrese un número: "))

# Verificar si es par o impar
if numero % 2 == 0:
    print("Es par")
else:
    print("Es impar")
```

---

#### Solución Ejercicio 4: Multiplicar Dos Números

```python
# Pedir los números
num1 = int(input("Ingrese el primer número: "))
num2 = int(input("Ingrese el segundo número: "))

# Calcular el producto
producto = num1 * num2

# Mostrar el resultado
print("El producto es:", producto)
```

---

#### Solución Ejercicio 5: Mayoría de Edad

```python
# Pedir la edad
edad = int(input("Ingrese su edad: "))

# Verificar
if edad >= 18:
    print("Sos mayor de edad")
else:
    print("Sos menor de edad")
```

---

#### Solución Ejercicio 6: Contar del 1 al N

```python
# Pedir el número
n = int(input("Ingrese un número: "))

# Contar del 1 al n
contador = 1
while contador <= n:
    print(contador)
    contador = contador + 1
```

**Alternativa con for:**

```python
n = int(input("Ingrese un número: "))

for i in range(1, n + 1):
    print(i)
```

---

#### Solución Ejercicio 7: Promedio de Tres Notas

```python
# Pedir las tres notas
nota1 = float(input("Nota 1: "))
nota2 = float(input("Nota 2: "))
nota3 = float(input("Nota 3: "))

# Calcular el promedio
suma = nota1 + nota2 + nota3
promedio = suma / 3

# Mostrar el resultado
print("El promedio es:", promedio)
```

---

#### Solución Ejercicio 8: Positivo, Negativo o Cero

```python
numero = int(input("Ingrese un número: "))

if numero > 0:
    print("Positivo")
elif numero < 0:
    print("Negativo")
else:
    print("Cero")
```

---

#### Solución Ejercicio 9: Tabla de Multiplicar

```python
numero = int(input("Ingrese un número: "))

i = 1
while i <= 10:
    resultado = numero * i
    print(f"{numero} x {i} = {resultado}")
    i = i + 1
```

**Alternativa con for:**

```python
numero = int(input("Ingrese un número: "))

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i} = {resultado}")
```

---

#### Solución Ejercicio 10: Sumar Números Hasta Cero

```python
suma = 0
numero = int(input("Ingrese un número (0 para terminar): "))

while numero != 0:
    suma = suma + numero
    numero = int(input("Ingrese un número (0 para terminar): "))

print("La suma total es:", suma)
```

---

#### Solución Ejercicio 11: Calcular Factorial

**Pseudocódigo:**

```
INICIO CalcularFactorial
    LEER n
    
    SI n < 0 ENTONCES
        MOSTRAR "Error: no existe factorial de negativos"
    SINO SI n == 0 ENTONCES
        MOSTRAR "El factorial es: 1"
    SINO
        factorial = 1
        i = 1
        MIENTRAS i <= n HACER
            factorial = factorial * i
            i = i + 1
        FIN_MIENTRAS
        MOSTRAR "El factorial es:", factorial
    FIN_SI
FIN
```

**Código Python:**

```python
n = int(input("Ingrese un número: "))

if n < 0:
    print("Error: no existe factorial de números negativos")
elif n == 0:
    print("El factorial es: 1")
else:
    factorial = 1
    i = 1
    while i <= n:
        factorial = factorial * i
        i = i + 1
    print("El factorial es:", factorial)
```

**Alternativa con for:**

```python
n = int(input("Ingrese un número: "))

if n < 0:
    print("Error: no existe factorial de números negativos")
elif n == 0:
    print("El factorial es: 1")
else:
    factorial = 1
    for i in range(1, n + 1):
        factorial = factorial * i
    print("El factorial es:", factorial)
```

---

#### Solución Ejercicio 12: Contar Dígitos

**Pseudocódigo:**

```
INICIO ContarDigitos
    LEER numero
    
    # Convertir a positivo si es negativo
    SI numero < 0 ENTONCES
        numero = -numero
    FIN_SI
    
    # Caso especial: el 0 tiene 1 dígito
    SI numero == 0 ENTONCES
        digitos = 1
    SINO
        digitos = 0
        MIENTRAS numero > 0 HACER
            numero = numero / 10  # división entera
            digitos = digitos + 1
        FIN_MIENTRAS
    FIN_SI
    
    MOSTRAR "Cantidad de dígitos:", digitos
FIN
```

**Código Python:**

```python
numero = int(input("Ingrese un número: "))

# Convertir a positivo si es negativo
if numero < 0:
    numero = -numero

# Caso especial: el 0
if numero == 0:
    digitos = 1
else:
    digitos = 0
    while numero > 0:
        numero = numero // 10  # División entera
        digitos = digitos + 1

print("Cantidad de dígitos:", digitos)
```

**Alternativa más corta (convirtiendo a string):**

```python
numero = input("Ingrese un número: ")
# Remover el signo negativo si existe
if numero.startswith('-'):
    numero = numero[1:]
print("Cantidad de dígitos:", len(numero))
```

---

#### Solución Ejercicio 13: Adivinar un Número

**Pseudocódigo:**

```
INICIO AdivinaNumero
    numeroSecreto = 42  # o generar aleatorio
    intentos = 0
    adivinado = FALSO
    
    MOSTRAR "Adivina el número entre 1 y 100"
    
    MIENTRAS adivinado == FALSO HACER
        LEER intento
        intentos = intentos + 1
        
        SI intento == numeroSecreto ENTONCES
            adivinado = VERDADERO
            MOSTRAR "¡Ganaste! Te tomó", intentos, "intentos"
        SINO SI intento < numeroSecreto ENTONCES
            MOSTRAR "El número es MAYOR"
        SINO
            MOSTRAR "El número es MENOR"
        FIN_SI
    FIN_MIENTRAS
FIN
```

**Código Python (versión simple con número fijo):**

```python
numero_secreto = 42
intentos = 0
adivinado = False

print("Adivina el número entre 1 y 100")

while not adivinado:
    intento = int(input("Tu intento: "))
    intentos = intentos + 1
    
    if intento == numero_secreto:
        adivinado = True
        print(f"¡Ganaste! Te tomó {intentos} intentos")
    elif intento < numero_secreto:
        print("El número es MAYOR")
    else:
        print("El número es MENOR")
```

**Versión con número aleatorio:**

```python
import random

numero_secreto = random.randint(1, 100)
intentos = 0
adivinado = False

print("Adivina el número entre 1 y 100")

while not adivinado:
    intento = int(input("Tu intento: "))
    intentos = intentos + 1
    
    if intento == numero_secreto:
        adivinado = True
        print(f"¡Ganaste! Te tomó {intentos} intentos")
    elif intento < numero_secreto:
        print("El número es MAYOR")
    else:
        print("El número es MENOR")
```

---

#### Solución Ejercicio 14: Números Primos

**Las 5 Preguntas:**

1. **¿Qué datos necesito?** Un número N
2. **¿Qué resultado quiero?** Decir si es primo o no
3. **¿Qué pasos debo seguir?** Verificar si algún número entre 2 y N-1 divide a N
4. **¿Hay situaciones especiales?** Sí: 1 no es primo, 2 es el único par primo
5. **¿Necesito repetir algo?** Sí, probar todos los divisores posibles

**Pseudocódigo:**

```
INICIO VerificarPrimo
    LEER n
    
    SI n < 2 ENTONCES
        MOSTRAR n, "no es primo"
    SINO SI n == 2 ENTONCES
        MOSTRAR n, "es primo"
    SINO
        esPrimo = VERDADERO
        divisor = 2
        
        MIENTRAS divisor < n Y esPrimo == VERDADERO HACER
            SI n % divisor == 0 ENTONCES
                esPrimo = FALSO
            FIN_SI
            divisor = divisor + 1
        FIN_MIENTRAS
        
        SI esPrimo == VERDADERO ENTONCES
            MOSTRAR n, "es primo"
        SINO
            MOSTRAR n, "no es primo"
        FIN_SI
    FIN_SI
FIN
```

**Código Python:**

```python
n = int(input("Ingrese un número: "))

if n < 2:
    print(f"{n} no es primo")
elif n == 2:
    print(f"{n} es primo")
else:
    es_primo = True
    divisor = 2
    
    while divisor < n and es_primo:
        if n % divisor == 0:
            es_primo = False
        divisor = divisor + 1
    
    if es_primo:
        print(f"{n} es primo")
    else:
        print(f"{n} no es primo")
```

**Versión optimizada (solo hasta la raíz cuadrada):**

```python
import math

n = int(input("Ingrese un número: "))

if n < 2:
    print(f"{n} no es primo")
elif n == 2:
    print(f"{n} es primo")
else:
    es_primo = True
    # Solo necesitamos probar hasta la raíz cuadrada
    limite = int(math.sqrt(n)) + 1
    
    for divisor in range(2, limite):
        if n % divisor == 0:
            es_primo = False
            break
    
    if es_primo:
        print(f"{n} es primo")
    else:
        print(f"{n} no es primo")
```

---

#### Solución Ejercicio 15: Serie de Fibonacci

**Las 5 Preguntas:**

1. **¿Qué datos necesito?** Un número N (cantidad de términos)
2. **¿Qué resultado quiero?** Los primeros N términos de Fibonacci
3. **¿Qué pasos debo seguir?** Empezar con 0 y 1, cada nuevo término es suma de los dos anteriores
4. **¿Hay situaciones especiales?** Si N = 1 solo mostrar 0, si N = 2 mostrar 0 y 1
5. **¿Necesito repetir algo?** Sí, N veces

**Pseudocódigo:**

```
INICIO Fibonacci
    LEER n
    
    SI n >= 1 ENTONCES
        anterior1 = 0
        anterior2 = 1
        MOSTRAR anterior1
        
        SI n >= 2 ENTONCES
            MOSTRAR anterior2
            
            contador = 3
            MIENTRAS contador <= n HACER
                actual = anterior1 + anterior2
                MOSTRAR actual
                
                # Actualizar para la próxima iteración
                anterior1 = anterior2
                anterior2 = actual
                contador = contador + 1
            FIN_MIENTRAS
        FIN_SI
    FIN_SI
FIN
```

**Código Python:**

```python
n = int(input("¿Cuántos términos desea ver? "))

if n >= 1:
    anterior1 = 0
    anterior2 = 1
    print(anterior1, end=" ")
    
    if n >= 2:
        print(anterior2, end=" ")
        
        contador = 3
        while contador <= n:
            actual = anterior1 + anterior2
            print(actual, end=" ")
            
            # Actualizar variables
            anterior1 = anterior2
            anterior2 = actual
            contador = contador + 1
    
    print()  # Salto de línea al final
```

**Versión con for:**

```python
n = int(input("¿Cuántos términos desea ver? "))

if n >= 1:
    anterior1 = 0
    anterior2 = 1
    print(anterior1, end=" ")
    
    if n >= 2:
        print(anterior2, end=" ")
        
        for i in range(3, n + 1):
            actual = anterior1 + anterior2
            print(actual, end=" ")
            
            # Actualizar variables
            anterior1 = anterior2
            anterior2 = actual
    
    print()  # Salto de línea al final
```

---

## Consejos Finales

:::{tip} Consejos para los ejercicios de programación

- **NO empieces a tipear código directamente**
- Primero las 5 preguntas, después pseudocódigo/diagrama
- La prueba de escritorio te ahorra horas de debugging
- Si el código no funciona, volvé al pseudocódigo (el error está en la lógica, no en Python)
- Probá con VARIOS casos, no solo uno

:::

:::{important} Errores Comunes a Evitar

1. **Saltear la planificación:** "Ya sé cómo hacerlo, voy directo al código"
   - Resultado: código que no funciona y no sabés por qué

2. **No hacer prueba de escritorio:** "Confío en que está bien"
   - Resultado: errores lógicos que son difíciles de encontrar

3. **Probar con un solo caso:** "Funcionó con 5, ya está"
   - Resultado: falla con otros valores

4. **No leer el enunciado completo:** Empezar antes de entender el problema
   - Resultado: resolver el problema equivocado

5. **No verificar casos especiales:** Solo probar casos "normales"
   - Resultado: el programa falla con valores límite (0, negativos, etc.)

:::

---

**¡Éxitos con los ejercicios! 🚀**

*Recuerda: La programación se aprende programando, pero **programar bien** se aprende **planificando primero**.*
