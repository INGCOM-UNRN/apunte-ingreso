# Ejercicios Parsons - Ordenar Pseudocódigo

## ¿Qué son los Problemas Parsons?

Los **problemas Parsons** son ejercicios donde te dan todas las líneas de un algoritmo **desordenadas**, y tu tarea es **ordenarlas correctamente**. Es como armar un rompecabezas con código.

:::{tip} ¿Por Qué son Útiles?

Los ejercicios Parsons te ayudan a:
- **Aprender la estructura** de los algoritmos sin escribir desde cero
- **Reconocer patrones** comunes en programación
- **Entender el flujo** de ejecución
- **Practicar la indentación** (los espacios que marcan bloques)
- **Reducir la carga cognitiva** al no tener que recordar sintaxis

**Son más fáciles que escribir código desde cero, pero igual te enseñan la lógica.**
:::

---

## Cómo Resolver un Problema Parsons

**Proceso paso a paso:**

1. **Leer el enunciado** y entender qué debe hacer el algoritmo
2. **Identificar la estructura general:**
   - ¿Tiene entrada (LEER)?
   - ¿Tiene proceso (cálculos)?
   - ¿Tiene salida (MOSTRAR)?
   - ¿Tiene decisiones (SI)?
   - ¿Tiene lazos (MIENTRAS)?
3. **Buscar el INICIO y FIN** - siempre van primero y último
4. **Agrupar líneas relacionadas:**
   - Las líneas con más indentación van dentro de bloques
   - Los bloques tienen inicio y fin (`SI...FIN_SI`, `MIENTRAS...FIN_MIENTRAS`)
5. **Verificar el orden lógico:**
   - ¿Las variables se usan después de ser creadas?
   - ¿Los cálculos se hacen con datos ya disponibles?
   - ¿La salida es lo último?

---

## Sintaxis de Pseudocódigo Usada

Esta es la sintaxis que usamos en estos ejercicios:

| Elemento | Sintaxis | Ejemplo |
|:---------|:---------|:--------|
| Inicio | `INICIO NombreAlgoritmo` | `INICIO CalcularPromedio` |
| Fin | `FIN` | `FIN` |
| Asignación | `variable ⟸ valor` | `suma ⟸ a + b` |
| Entrada | `LEER variable` | `LEER edad` |
| Salida | `MOSTRAR mensaje` | `MOSTRAR "Resultado:", x` |
| Comentario | `# texto` | `# Calcular el total` |
| Condición | `SI condición ENTONCES` | `SI edad >= 18 ENTONCES` |
| Sino | `SINO` | `SINO` |
| Fin condición | `FIN_SI` | `FIN_SI` |
| Lazo mientras | `MIENTRAS condición HACER` | `MIENTRAS i <= 10 HACER` |
| Fin mientras | `FIN_MIENTRAS` | `FIN_MIENTRAS` |
| Lazo para | `PARA var DESDE inicio HASTA fin HACER` | `PARA i DESDE 1 HASTA 10 HACER` |
| Fin para | `FIN_PARA` | `FIN_PARA` |

---

## Ejercicios

Los ejercicios están ordenados por **dificultad creciente** y **longitud creciente**:

- **Ejercicios 1-5:** Algoritmos secuenciales simples (3-5 líneas)
- **Ejercicios 6-10:** Con decisiones (SI/SINO) (6-9 líneas)
- **Ejercicios 11-15:** Con lazos simples (8-12 líneas)
- **Ejercicios 16-20:** Complejos con decisiones y lazos anidados (12-18 líneas)

---

### Nivel 1: Secuenciales Simples (Ejercicios 1-5)

---

### Ejercicio 1: Saludar

**Enunciado:** Mostrar un saludo personalizado. Pedir el nombre del usuario y saludarlo.

**Líneas desordenadas:**

```
FIN
MOSTRAR "Hola,", nombre
INICIO Saludar
LEER nombre
MOSTRAR "Ingrese su nombre:"
```

**Pistas:**
- ¿Cuál es la primera línea de todo algoritmo?
- ¿Primero mostramos el mensaje o leemos?
- ¿Cuál es la última línea?

---

### Ejercicio 2: Calcular Doble

**Enunciado:** Pedir un número y mostrar su doble.

**Líneas desordenadas:**

```
doble ⟸ numero * 2
MOSTRAR "El doble es:", doble
INICIO CalcularDoble
LEER numero
MOSTRAR "Ingrese un número:"
FIN
```

**Pistas:**
- ¿Qué necesitamos antes de calcular el doble?
- ¿El cálculo va antes o después de leer?

---

### Ejercicio 3: Sumar Tres Números

**Enunciado:** Pedir tres números y mostrar su suma.

**Líneas desordenadas:**

```
LEER num2
suma ⟸ num1 + num2 + num3
LEER num1
MOSTRAR "La suma es:", suma
INICIO SumarTres
FIN
LEER num3
```

**Pistas:**
- Necesitamos leer los tres números antes de sumarlos
- El orden de lectura puede ser num1, num2, num3

---

### Ejercicio 4: Calcular Área de Círculo

**Enunciado:** Pedir el radio de un círculo y calcular su área (π × radio²). Usar π = 3.1416.

**Líneas desordenadas:**

```
area ⟸ 3.1416 * radio * radio
MOSTRAR "El área es:", area
INICIO CalcularAreaCirculo
LEER radio
FIN
MOSTRAR "Ingrese el radio:"
```

**Pistas:**
- La fórmula usa radio multiplicado por sí mismo
- Necesitamos el radio antes de calcular

---

### Ejercicio 5: Convertir Horas a Minutos

**Enunciado:** Pedir una cantidad de horas y convertirlas a minutos (1 hora = 60 minutos).

**Líneas desordenadas:**

```
INICIO ConvertirHoras
minutos ⟸ horas * 60
MOSTRAR "Son:", minutos, "minutos"
FIN
LEER horas
MOSTRAR "Ingrese las horas:"
```

**Pistas:**
- 1 hora = 60 minutos, entonces multiplicamos por 60
- Primero leemos, después calculamos, después mostramos

---

### Nivel 2: Con Decisiones (Ejercicios 6-10)

---

### Ejercicio 6: Mayor de Edad

**Enunciado:** Pedir la edad y decir si es mayor o menor de edad (>= 18).

**Líneas desordenadas:**

```
SINO
FIN_SI
LEER edad
INICIO MayorDeEdad
SI edad >= 18 ENTONCES
    MOSTRAR "Sos mayor de edad"
FIN
    MOSTRAR "Sos menor de edad"
```

**Pistas:**
- El `SI` tiene un `ENTONCES` al final
- Lo que está indentado (con espacios) va dentro del SI
- El `SINO` va después de la primera opción
- Todo termina con `FIN_SI`

---

### Ejercicio 7: Número Positivo o Negativo

**Enunciado:** Pedir un número y decir si es positivo o negativo.

**Líneas desordenadas:**

```
INICIO PositivoNegativo
    MOSTRAR "Es positivo"
FIN_SI
LEER numero
SI numero >= 0 ENTONCES
SINO
FIN
    MOSTRAR "Es negativo"
```

**Pistas:**
- Usar >= 0 para incluir el cero como positivo
- Recuerda la indentación dentro del SI y SINO

---

### Ejercicio 8: Aprobar o Desaprobar

**Enunciado:** Pedir una nota (0-10) y decir si aprobó (>= 6) o desaprobó.

**Líneas desordenadas:**

```
LEER nota
FIN
    MOSTRAR "Aprobado"
FIN_SI
SINO
SI nota >= 6 ENTONCES
INICIO AprobarDesaprobar
    MOSTRAR "Desaprobado"
MOSTRAR "Ingrese la nota:"
```

**Pistas:**
- En Argentina se aprueba con 6 o más
- La estructura es igual al ejercicio anterior

---

### Ejercicio 9: Descuento por Compra

**Enunciado:** Si la compra es mayor a $1000, aplicar 10% de descuento. Mostrar el total final.

**Líneas desordenadas:**

```
LEER monto
    descuento ⟸ monto * 0.10
FIN_SI
SI monto > 1000 ENTONCES
INICIO DescuentoCompra
    total ⟸ monto - descuento
MOSTRAR "Total a pagar:", total
FIN
SINO
    total ⟸ monto
```

**Pistas:**
- 10% = 0.10
- Si hay descuento, restamos. Si no hay, el total es el monto original
- Ambas ramas del SI calculan el total

---

### Ejercicio 10: Número Par o Impar

**Enunciado:** Pedir un número y decir si es par o impar usando el operador módulo (%).

**Líneas desordenadas:**

```
    MOSTRAR "Es par"
INICIO ParImpar
FIN
LEER numero
SINO
FIN_SI
SI numero % 2 == 0 ENTONCES
    MOSTRAR "Es impar"
```

**Pistas:**
- El operador % da el resto de la división
- Si el resto al dividir por 2 es 0, es par
- Si no es 0, es impar

---

### Nivel 3: Con Lazos Simples (Ejercicios 11-15)

---

### Ejercicio 11: Contar del 1 al 5

**Enunciado:** Mostrar los números del 1 al 5 usando un lazo MIENTRAS.

**Líneas desordenadas:**

```
FIN_MIENTRAS
    MOSTRAR i
INICIO Contar1a5
i ⟸ 1
FIN
    i ⟸ i + 1
MIENTRAS i <= 5 HACER
```

**Pistas:**
- Inicializar i en 1 antes del lazo
- El lazo se repite mientras i <= 5
- Dentro del lazo: mostrar i, luego incrementarlo
- No olvides el FIN_MIENTRAS

---

### Ejercicio 12: Suma de 1 al N

**Enunciado:** Pedir un número N y calcular la suma de 1 hasta N.

**Líneas desordenadas:**

```
i ⟸ 1
    suma ⟸ suma + i
FIN
MIENTRAS i <= n HACER
LEER n
INICIO SumaHastaN
FIN_MIENTRAS
    i ⟸ i + 1
MOSTRAR "La suma es:", suma
suma ⟸ 0
```

**Pistas:**
- Inicializar suma en 0
- Inicializar i en 1
- Acumular: suma = suma + i
- Incrementar i en cada iteración

---

### Ejercicio 13: Tabla de Multiplicar

**Enunciado:** Pedir un número y mostrar su tabla de multiplicar del 1 al 10.

**Líneas desordenadas:**

```
    i ⟸ i + 1
FIN
MIENTRAS i <= 10 HACER
    MOSTRAR numero, "x", i, "=", resultado
FIN_MIENTRAS
INICIO TablaMultiplicar
i ⟸ 1
    resultado ⟸ numero * i
LEER numero
```

**Pistas:**
- i va de 1 a 10
- En cada iteración: calcular resultado, mostrarlo, incrementar i

---

### Ejercicio 14: Contar Pares hasta N

**Enunciado:** Pedir N y mostrar todos los números pares desde 2 hasta N.

**Líneas desordenadas:**

```
    MOSTRAR par
FIN_MIENTRAS
par ⟸ 2
INICIO ContarPares
LEER n
    par ⟸ par + 2
FIN
MIENTRAS par <= n HACER
```

**Pistas:**
- Empezar en 2 (primer par)
- Incrementar de 2 en 2 (par = par + 2)
- Continuar mientras par <= n

---

### Ejercicio 15: Contar Dígitos

**Enunciado:** Pedir un número y contar cuántos dígitos tiene.

**Líneas desordenadas:**

```
FIN
LEER numero
    contador ⟸ contador + 1
FIN_MIENTRAS
INICIO ContarDigitos
MIENTRAS numero > 0 HACER
MOSTRAR "Tiene", contador, "dígitos"
    numero ⟸ numero / 10
contador ⟸ 0
```

**Pistas:**
- Inicializar contador en 0
- Dividir el número por 10 repetidamente
- Contar cuántas veces se divide
- Continuar mientras numero > 0

---

### Nivel 4: Complejos (Ejercicios 16-20)

---

### Ejercicio 16: Validar Entrada

**Enunciado:** Pedir un número entre 1 y 10. Si no está en ese rango, volver a pedirlo.

**Líneas desordenadas:**

```
MIENTRAS numero < 1 O numero > 10 HACER
FIN
    LEER numero
INICIO ValidarEntrada
LEER numero
FIN_MIENTRAS
    MOSTRAR "Error. Ingrese entre 1 y 10:"
MOSTRAR "Número válido:", numero
MOSTRAR "Ingrese un número (1-10):"
```

**Pistas:**
- Leer una vez antes del lazo
- Si no es válido, mostrar error y leer de nuevo
- Continuar hasta que sea válido (1 a 10)

---

### Ejercicio 17: Suma de Pares e Impares

**Enunciado:** Pedir N números y mostrar la suma de los pares y la suma de los impares por separado.

**Líneas desordenadas:**

```
    SI numero % 2 == 0 ENTONCES
sumaPares ⟸ 0
FIN_MIENTRAS
FIN
MIENTRAS i <= n HACER
i ⟸ 1
        sumaImpares ⟸ sumaImpares + numero
    LEER numero
INICIO SumaParesImpares
FIN_SI
MOSTRAR "Suma pares:", sumaPares
LEER n
MOSTRAR "Suma impares:", sumaImpares
        sumaPares ⟸ sumaPares + numero
    SINO
    i ⟸ i + 1
sumaImpares ⟸ 0
```

**Pistas:**
- Inicializar dos acumuladores: sumaPares y sumaImpares
- Dentro del lazo, leer cada número
- Usar % 2 para verificar si es par
- Si es par, sumar a sumaPares; si no, a sumaImpares

---

### Ejercicio 18: Encontrar el Mayor

**Enunciado:** Pedir N números y encontrar cuál es el mayor.

**Líneas desordenadas:**

```
INICIO EncontrarMayor
FIN
    FIN_SI
LEER n
MIENTRAS i <= n HACER
mayor ⟸ -999999
MOSTRAR "El mayor es:", mayor
FIN_MIENTRAS
    SI numero > mayor ENTONCES
    LEER numero
    i ⟸ i + 1
i ⟸ 1
        mayor ⟸ numero
```

**Pistas:**
- Inicializar mayor con un valor muy pequeño
- Leer cada número y comparar con el mayor actual
- Si es más grande, actualizar mayor
- Al final, mayor tiene el valor más grande

---

### Ejercicio 19: Adivinar Número

**Enunciado:** El programa tiene un número secreto (42). El usuario intenta adivinarlo. 
El programa da pistas ("mayor" o "menor") hasta que acierte.

**Líneas desordenadas:**

```
MOSTRAR "Intenta adivinar:"
INICIO AdivinaNumero
    SINO SI intento < numeroSecreto ENTONCES
FIN_MIENTRAS
    FIN_SI
        MOSTRAR "¡Correcto! Ganaste"
        MOSTRAR "El número es mayor"
LEER intento
    SI intento == numeroSecreto ENTONCES
FIN
MIENTRAS intento != numeroSecreto HACER
    SINO
numeroSecreto ⟸ 42
        MOSTRAR "El número es menor"
```

**Pistas:**
- Asignar el número secreto (42) al inicio
- Pedir el primer intento
- Mientras no acierte: dar pista y pedir otro intento
- Usar SI anidados: primero verificar ==, luego <, luego (resto es >)

---

### Ejercicio 20: Factorial

**Enunciado:** Pedir un número N y calcular su factorial (N! = 1 × 2 × 3 × ... × N).

**Líneas desordenadas:**

```
    SINO
factorial ⟸ 1
        i ⟸ i + 1
LEER n
    FIN_SI
INICIO CalcularFactorial
SI n < 0 ENTONCES
FIN_MIENTRAS
FIN
    MOSTRAR "El factorial es:", factorial
MOSTRAR "Error: no existe factorial de negativos"
        factorial ⟸ factorial * i
    MIENTRAS i <= n HACER
        i ⟸ 1
```

**Pistas:**
- Validar que n no sea negativo
- Si es negativo, mostrar error y terminar
- Si es válido, inicializar factorial en 1
- Multiplicar factorial por cada número de 1 a n
- La estructura es: SI-SINO, y dentro del SINO está el MIENTRAS

---

## Soluciones

:::{admonition} 💡 Antes de Ver las Soluciones
:class: warning

**¡Intentá resolver los ejercicios vos mismo primero!**

Los problemas Parsons son para **practicar reconocer patrones** y **entender la estructura**.

Solo mirá las soluciones si:
- Ya lo intentaste varias veces
- Querés verificar tu respuesta
- Querés entender por qué está ordenado así

:::

---

### Soluciones Nivel 1 (1-5)

#### Solución Ejercicio 1: Saludar

```
INICIO Saludar
MOSTRAR "Ingrese su nombre:"
LEER nombre
MOSTRAR "Hola,", nombre
FIN
```

**Explicación:**
1. Todo algoritmo empieza con INICIO
2. Primero mostramos el mensaje pidiendo el nombre
3. Leemos el nombre
4. Mostramos el saludo usando el nombre
5. Terminamos con FIN

---

#### Solución Ejercicio 2: Calcular Doble

```
INICIO CalcularDoble
MOSTRAR "Ingrese un número:"
LEER numero
doble ⟸ numero * 2
MOSTRAR "El doble es:", doble
FIN
```

**Explicación:**
- Entrada: pedir y leer el número
- Proceso: calcular doble = numero * 2
- Salida: mostrar el resultado

---

#### Solución Ejercicio 3: Sumar Tres Números

```
INICIO SumarTres
LEER num1
LEER num2
LEER num3
suma ⟸ num1 + num2 + num3
MOSTRAR "La suma es:", suma
FIN
```

**Explicación:**
- Leer los tres números en orden
- Sumarlos
- Mostrar el resultado

---

#### Solución Ejercicio 4: Calcular Área de Círculo

```
INICIO CalcularAreaCirculo
MOSTRAR "Ingrese el radio:"
LEER radio
area ⟸ 3.1416 * radio * radio
MOSTRAR "El área es:", area
FIN
```

**Explicación:**
- Fórmula del área: π × r²
- radio * radio calcula r²
- Multiplicamos por pi (3.1416)

---

#### Solución Ejercicio 5: Convertir Horas a Minutos

```
INICIO ConvertirHoras
MOSTRAR "Ingrese las horas:"
LEER horas
minutos ⟸ horas * 60
MOSTRAR "Son:", minutos, "minutos"
FIN
```

**Explicación:**
- 1 hora = 60 minutos
- Multiplicamos las horas por 60

---

### Soluciones Nivel 2 (6-10)

#### Solución Ejercicio 6: Mayor de Edad

```
INICIO MayorDeEdad
LEER edad
SI edad >= 18 ENTONCES
    MOSTRAR "Sos mayor de edad"
SINO
    MOSTRAR "Sos menor de edad"
FIN_SI
FIN
```

**Explicación:**
- SI con condición edad >= 18
- Rama del SI (con indentación)
- SINO para la otra opción
- Rama del SINO (con indentación)
- FIN_SI cierra la estructura
- FIN termina el algoritmo

---

#### Solución Ejercicio 7: Positivo o Negativo

```
INICIO PositivoNegativo
LEER numero
SI numero >= 0 ENTONCES
    MOSTRAR "Es positivo"
SINO
    MOSTRAR "Es negativo"
FIN_SI
FIN
```

**Explicación:**
- Usamos >= 0 para considerar el cero como positivo
- Estructura SI-SINO estándar

---

#### Solución Ejercicio 8: Aprobar o Desaprobar

```
INICIO AprobarDesaprobar
MOSTRAR "Ingrese la nota:"
LEER nota
SI nota >= 6 ENTONCES
    MOSTRAR "Aprobado"
SINO
    MOSTRAR "Desaprobado"
FIN_SI
FIN
```

**Explicación:**
- nota >= 6 es la condición de aprobación
- Mismo patrón que los anteriores

---

#### Solución Ejercicio 9: Descuento por Compra

```
INICIO DescuentoCompra
LEER monto
SI monto > 1000 ENTONCES
    descuento ⟸ monto * 0.10
    total ⟸ monto - descuento
SINO
    total ⟸ monto
FIN_SI
MOSTRAR "Total a pagar:", total
FIN
```

**Explicación:**
- Si monto > 1000: calcular descuento y restar
- Si no: el total es el monto sin cambios
- En ambos casos, al final tenemos la variable total
- Mostramos total después del FIN_SI

---

#### Solución Ejercicio 10: Par o Impar

```
INICIO ParImpar
LEER numero
SI numero % 2 == 0 ENTONCES
    MOSTRAR "Es par"
SINO
    MOSTRAR "Es impar"
FIN_SI
FIN
```

**Explicación:**
- numero % 2 da el resto de dividir por 2
- Si resto == 0, es par
- Si resto != 0 (es decir, resto == 1), es impar

---

### Soluciones Nivel 3 (11-15)

#### Solución Ejercicio 11: Contar del 1 al 5

```
INICIO Contar1a5
i ⟸ 1
MIENTRAS i <= 5 HACER
    MOSTRAR i
    i ⟸ i + 1
FIN_MIENTRAS
FIN
```

**Explicación:**
1. Inicializar i en 1 (antes del lazo)
2. Condición del lazo: i <= 5
3. Dentro del lazo: mostrar i
4. Incrementar i (i = i + 1)
5. FIN_MIENTRAS cierra el lazo
6. El lazo se ejecuta 5 veces (i = 1, 2, 3, 4, 5)

---

#### Solución Ejercicio 12: Suma de 1 al N

```
INICIO SumaHastaN
LEER n
suma ⟸ 0
i ⟸ 1
MIENTRAS i <= n HACER
    suma ⟸ suma + i
    i ⟸ i + 1
FIN_MIENTRAS
MOSTRAR "La suma es:", suma
FIN
```

**Explicación:**
- suma empieza en 0 (acumulador)
- i empieza en 1 (contador)
- En cada vuelta: suma = suma + i (acumular)
- Incrementar i
- Al final, suma tiene 1+2+3+...+n

---

#### Solución Ejercicio 13: Tabla de Multiplicar

```
INICIO TablaMultiplicar
LEER numero
i ⟸ 1
MIENTRAS i <= 10 HACER
    resultado ⟸ numero * i
    MOSTRAR numero, "x", i, "=", resultado
    i ⟸ i + 1
FIN_MIENTRAS
FIN
```

**Explicación:**
- Leer el número del cual queremos la tabla
- i va de 1 a 10
- En cada vuelta: calcular resultado, mostrarlo, incrementar i
- Ejemplo: si numero=7, muestra 7x1=7, 7x2=14, ..., 7x10=70

---

#### Solución Ejercicio 14: Contar Pares hasta N

```
INICIO ContarPares
LEER n
par ⟸ 2
MIENTRAS par <= n HACER
    MOSTRAR par
    par ⟸ par + 2
FIN_MIENTRAS
FIN
```

**Explicación:**
- par empieza en 2 (primer número par)
- Incrementar de 2 en 2 (par = par + 2)
- Esto genera: 2, 4, 6, 8, ... hasta n
- Ejemplo: si n=10, muestra 2, 4, 6, 8, 10

---

#### Solución Ejercicio 15: Contar Dígitos

```
INICIO ContarDigitos
LEER numero
contador ⟸ 0
MIENTRAS numero > 0 HACER
    numero ⟸ numero / 10
    contador ⟸ contador + 1
FIN_MIENTRAS
MOSTRAR "Tiene", contador, "dígitos"
FIN
```

**Explicación:**
- Dividir número por 10 elimina el último dígito
- Ejemplo: 12345 / 10 = 1234, 1234 / 10 = 123, ...
- Contar cuántas veces se puede dividir
- Cuando numero llega a 0, terminamos
- Ejemplo: 12345 → 5 dígitos (se divide 5 veces)

**Nota:** Esta solución usa división entera (/) que en pseudocódigo asumimos que descarta decimales.

---

### Soluciones Nivel 4 (16-20)

#### Solución Ejercicio 16: Validar Entrada

```
INICIO ValidarEntrada
MOSTRAR "Ingrese un número (1-10):"
LEER numero
MIENTRAS numero < 1 O numero > 10 HACER
    MOSTRAR "Error. Ingrese entre 1 y 10:"
    LEER numero
FIN_MIENTRAS
MOSTRAR "Número válido:", numero
FIN
```

**Explicación:**
- Leer una vez antes del lazo
- Si no está en el rango [1,10], entrar al lazo
- Dentro del lazo: mostrar error y leer de nuevo
- Salir del lazo cuando el número sea válido
- Este patrón se llama "validación con re-lectura"

---

#### Solución Ejercicio 17: Suma de Pares e Impares

```
INICIO SumaParesImpares
LEER n
sumaPares ⟸ 0
sumaImpares ⟸ 0
i ⟸ 1
MIENTRAS i <= n HACER
    LEER numero
    SI numero % 2 == 0 ENTONCES
        sumaPares ⟸ sumaPares + numero
    SINO
        sumaImpares ⟸ sumaImpares + numero
    FIN_SI
    i ⟸ i + 1
FIN_MIENTRAS
MOSTRAR "Suma pares:", sumaPares
MOSTRAR "Suma impares:", sumaImpares
FIN
```

**Explicación:**
- Dos acumuladores: sumaPares y sumaImpares
- Lazo que se repite n veces
- Dentro del lazo: leer cada número
- Verificar si es par (% 2 == 0)
- Si es par, sumarlo a sumaPares
- Si es impar, sumarlo a sumaImpares
- Al final, mostrar ambas sumas

---

#### Solución Ejercicio 18: Encontrar el Mayor

```
INICIO EncontrarMayor
LEER n
mayor ⟸ -999999
i ⟸ 1
MIENTRAS i <= n HACER
    LEER numero
    SI numero > mayor ENTONCES
        mayor ⟸ numero
    FIN_SI
    i ⟸ i + 1
FIN_MIENTRAS
MOSTRAR "El mayor es:", mayor
FIN
```

**Explicación:**
- Inicializar mayor con un valor muy pequeño (para que el primer número lo supere)
- Leer n números
- Para cada número: si es mayor que el actual "mayor", actualizarlo
- Al final, mayor contiene el valor más grande
- Este es el algoritmo clásico de "búsqueda del máximo"

---

#### Solución Ejercicio 19: Adivinar Número

```
INICIO AdivinaNumero
numeroSecreto ⟸ 42
MOSTRAR "Intenta adivinar:"
LEER intento
MIENTRAS intento != numeroSecreto HACER
    SI intento == numeroSecreto ENTONCES
        MOSTRAR "¡Correcto! Ganaste"
    SINO SI intento < numeroSecreto ENTONCES
        MOSTRAR "El número es mayor"
    SINO
        MOSTRAR "El número es menor"
    FIN_SI
    LEER intento
FIN_MIENTRAS
FIN
```

**Explicación:**
- Fijar el número secreto (42)
- Leer el primer intento
- Mientras no acierte (intento != numeroSecreto):
  - Si acertó: felicitar (aunque esto no se ejecuta en este lazo)
  - Si intento < secreto: "es mayor"
  - Si intento > secreto: "es menor"
  - Leer otro intento
- Salir del lazo cuando acierte

**Nota:** La condición del MIENTRAS hace que cuando acierte, salga del lazo directamente.

---

#### Solución Ejercicio 20: Factorial

```
INICIO CalcularFactorial
LEER n
SI n < 0 ENTONCES
    MOSTRAR "Error: no existe factorial de negativos"
SINO
    factorial ⟸ 1
    i ⟸ 1
    MIENTRAS i <= n HACER
        factorial ⟸ factorial * i
        i ⟸ i + 1
    FIN_MIENTRAS
    MOSTRAR "El factorial es:", factorial
FIN_SI
FIN
```

**Explicación:**
- Primero validar: si n < 0, mostrar error y terminar
- Si n >= 0:
  - factorial empieza en 1 (neutro multiplicativo)
  - i va de 1 a n
  - En cada vuelta: factorial = factorial * i
  - Ejemplo: 5! = 1 × 1 × 2 × 3 × 4 × 5 = 120
- Mostrar el resultado

**Casos especiales:**
- 0! = 1 (el lazo no se ejecuta, factorial queda en 1)
- 1! = 1 (el lazo se ejecuta una vez: 1 × 1 = 1)

---

## Consejos para Resolver Problemas Parsons

:::{tip} Estrategias Efectivas

**1. Busca la estructura primero:**
   - INICIO siempre va primero
   - FIN siempre va último
   - Si hay SI, debe tener FIN_SI
   - Si hay MIENTRAS, debe tener FIN_MIENTRAS

**2. Usa la indentación como pista:**
   - Lo que está indentado va **dentro** de un bloque
   - Las líneas con más espacios están "anidadas"

**3. Identifica bloques:**
   - SI...FIN_SI
   - MIENTRAS...FIN_MIENTRAS
   - PARA...FIN_PARA

**4. Sigue el flujo lógico:**
   - Entrada (LEER) → Proceso (cálculos) → Salida (MOSTRAR)
   - Las variables deben existir antes de usarse
   - Los cálculos usan variables ya leídas

**5. Verifica condiciones:**
   - Las condiciones de SI y MIENTRAS deben tener sentido
   - Los contadores deben inicializarse antes del lazo
   - Los acumuladores deben empezar en 0 (suma) o 1 (producto)

:::

:::{important} Errores Comunes

❌ **Usar una variable antes de leerla o asignarla**
   - Incorrecto: primero `suma ⟸ a + b`, después `LEER a`
   - Correcto: primero `LEER a`, después `suma ⟸ a + b`

❌ **Olvidar incrementar el contador en un lazo**
   - Resultado: lazo infinito
   - Siempre incrementar: `i ⟸ i + 1`

❌ **Mal indentación**
   - Lo que va dentro del SI/MIENTRAS debe estar indentado
   - Afecta la legibilidad y el significado

❌ **Olvidar cerrar estructuras**
   - Todo SI necesita FIN_SI
   - Todo MIENTRAS necesita FIN_MIENTRAS

❌ **Inicializar mal los acumuladores**
   - Para sumas: empezar en 0
   - Para productos: empezar en 1
   - Para búsqueda de máximo: empezar muy bajo
   - Para búsqueda de mínimo: empezar muy alto

:::

---

## Ejercicios Adicionales (Práctica Libre)

Si querés más práctica, intentá **desordenar** estos algoritmos vos mismo y luego ordenarlos:

### Extra 1: Promedio de Tres Números

```
INICIO Promedio
LEER num1
LEER num2
LEER num3
suma ⟸ num1 + num2 + num3
promedio ⟸ suma / 3
MOSTRAR "El promedio es:", promedio
FIN
```

### Extra 2: Encontrar el Mínimo de Tres

```
INICIO MinimoTres
LEER a
LEER b
LEER c
minimo ⟸ a
SI b < minimo ENTONCES
    minimo ⟸ b
FIN_SI
SI c < minimo ENTONCES
    minimo ⟸ c
FIN_SI
MOSTRAR "El mínimo es:", minimo
FIN
```

### Extra 3: Números Pares Ascendentes y Descendentes

```
INICIO ParesAscDesc
LEER n
# Ascendente
i ⟸ 2
MIENTRAS i <= n HACER
    MOSTRAR i
    i ⟸ i + 2
FIN_MIENTRAS
# Descendente
SI n % 2 == 0 ENTONCES
    i ⟸ n
SINO
    i ⟸ n - 1
FIN_SI
MIENTRAS i >= 2 HACER
    MOSTRAR i
    i ⟸ i - 2
FIN_MIENTRAS
FIN
```

---

**¡Éxitos practicando con los Problemas Parsons! 🧩**

*Recordá: ordenar código es más fácil que escribirlo desde cero, pero igual te enseña los patrones fundamentales de programación.*
