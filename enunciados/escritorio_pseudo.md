## Pruebas de Escritorio (10 ejercicios)

En estos ejercicios debés verificar si un algoritmo funciona correctamente realizando una **prueba de escritorio**. Para cada uno:

1. Crear una tabla de traza con las variables necesarias
2. Ejecutar el algoritmo paso a paso con los valores dados
3. Verificar si el resultado es correcto
4. Si hay errores, indicar en qué paso ocurren

---

### Ejercicio 1: Área de Rectángulo (Diagrama de Flujo)

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input1[/LEER base/]
    Input2[/LEER altura/]
    Process[area = base * altura]
    Output[/MOSTRAR area/]
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

**Caso de prueba:** base = 5, altura = 8

**Tareas:**
1. Crear tabla de traza con columnas: Paso | Línea | base | altura | area | Salida
2. Ejecutar paso a paso
3. ¿Cuál es el resultado final?
4. ¿Es correcto? Verificar: 5 × 8 = 40

---

### Ejercicio 2: Descuento del 10% (Diagrama de Flujo)

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER precio/]
    Calc1[descuento = precio * 0.10]
    Calc2[precioFinal = precio - descuento]
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

**Caso de prueba:** precio = 250

**Tareas:**
1. Crear tabla: Paso | Línea | precio | descuento | precioFinal | Salida
2. Ejecutar paso a paso
3. ¿El precio final es 225? (250 - 25 = 225)

---

### Ejercicio 3: Número Positivo o Negativo (Diagrama de Flujo)

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER numero/]
    Decision{numero > 0?}
    OutputPos[/MOSTRAR Positivo/]
    OutputNeg[/MOSTRAR Negativo/]
    End([FIN])
    
    Start --> Input
    Input --> Decision
    Decision -->|Sí| OutputPos
    Decision -->|No| OutputNeg
    OutputPos ---> End
    OutputNeg ---> End

    style Decision fill:#FFD700
    style End fill:#FFB6C1
    style Input fill:#87CEEB
    style OutputNeg fill:#87CEEB
    style OutputPos fill:#87CEEB
    style Start fill:#90EE90
```

**Casos de prueba:**
- Caso 1: numero = 15
- Caso 2: numero = -7

**Tareas:**
1. Hacer DOS pruebas de escritorio (una por cada caso)
2. Verificar que cada uno tome el camino correcto
3. ¿Qué pasa con el cero? ¿Es un problema del algoritmo?

---

### Ejercicio 4: Tabla del 5 (Diagrama de Flujo)

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    Start([INICIO])
    Init[i = 1]
    Condition{i <= 5?}
    Calc[resultado = 5 * i]
    Output[/MOSTRAR resultado/]
    Increment[i = i + 1]
    End([FIN])
    
    Start --> Init
    Init --> Condition
    Condition -->|Sí| Calc
    Calc --> Output
    Output --> Increment
    Increment --> Condition
    Condition -->|No| End

    style Calc fill:#FFE4B5
    style Condition fill:#FFD700
    style End fill:#FFB6C1
    style Increment fill:#FFE4B5
    style Init fill:#FFE4B5
    style Output fill:#87CEEB
    style Start fill:#90EE90
```

**Caso de prueba:** Ejecutar el lazo completo

**Tareas:**
1. Tabla: Iteración | i | i <= 5? | resultado | Salida
2. Ejecutar hasta que el lazo termine
3. ¿Cuántas veces se ejecuta el lazo?
4. ¿Los resultados son: 5, 10, 15, 20, 25?

---

### Ejercicio 5: Mayor de Tres Números (Diagrama de Flujo)

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    Start([INICIO])
    Input1[/LEER a/]
    Input2[/LEER b/]
    Input3[/LEER c/]
    Dec1{a > b?}
    Dec2{a > c?}
    Dec3{b > c?}
    Out1[/MOSTRAR a es mayor/]
    Out2[/MOSTRAR b es mayor/]
    Out3[/MOSTRAR c es mayor/]
    End([FIN])
    
    Start --> Input1
    Input1 --> Input2
    Input2 --> Input3
    Input3 --> Dec1
    Dec1 -->|Sí| Dec2
    Dec1 -->|No| Dec3
    Dec2 -->|Sí| Out1
    Dec2 -->|No| Out3
    Dec3 -->|Sí| Out2
    Dec3 -->|No| Out3
    Out1 ---> End
    Out2 ---> End
    Out3 ---> End

    style Dec1 fill:#FFD700
    style Dec2 fill:#FFD700
    style Dec3 fill:#FFD700
    style End fill:#FFB6C1
    style Input1 fill:#87CEEB
    style Input2 fill:#87CEEB
    style Input3 fill:#87CEEB
    style Out1 fill:#87CEEB
    style Out2 fill:#87CEEB
    style Out3 fill:#87CEEB
    style Start fill:#90EE90
```

**Caso de prueba:** a = 12, b = 8, c = 15

**Tareas:**
1. Seguir el diagrama con estos valores
2. ¿Qué decisiones se toman? (¿Sí o No en cada rombo?)
3. ¿El resultado es correcto? (c debería ser el mayor)

---

### Ejercicio 6: Conversión de Temperatura (Pseudocódigo)

**Pseudocódigo:**

```
INICIO ConversionTemp
    LEER celsius
    fahrenheit = (celsius * 9/5) + 32
    MOSTRAR fahrenheit
FIN
```

**Caso de prueba:** celsius = 25

**Tareas:**
1. Tabla: Paso | celsius | fahrenheit | Salida
2. ¿El resultado es 77? (25°C = 77°F)
3. Verificar con la fórmula

---

### Ejercicio 7: Calcular Edad (Pseudocódigo)

**Pseudocódigo:**

```
INICIO CalcularEdad
    LEER anioNacimiento
    anioActual = 2024
    edad = anioActual - anioNacimiento
    MOSTRAR edad
FIN
```

**Caso de prueba:** anioNacimiento = 2006

**Tareas:**
1. Tabla: Paso | anioNacimiento | anioActual | edad | Salida
2. ¿El resultado es 18?
3. ¿Qué pasaría si cambiamos anioActual a 2025?

---

### Ejercicio 8: Aprobar o Desaprobar (Pseudocódigo)

**Pseudocódigo:**

```
INICIO VerificarAprobacion
    LEER nota
    SI nota >= 6 ENTONCES
        MOSTRAR "Aprobado"
    SINO
        MOSTRAR "Desaprobado"
    FIN_SI
FIN
```

**Casos de prueba:**
- Caso 1: nota = 7
- Caso 2: nota = 4
- Caso 3: nota = 6 (caso borde)

**Tareas:**
1. Hacer TRES pruebas de escritorio
2. Verificar cada condición
3. ¿El caso borde (6) funciona correctamente?

---

### Ejercicio 9: Sumar Números Pares del 2 al 10 (Pseudocódigo)

**Pseudocódigo:**

```
INICIO SumarPares
    suma = 0
    numero = 2
    MIENTRAS numero <= 10 HACER
        suma = suma + numero
        numero = numero + 2
    FIN_MIENTRAS
    MOSTRAR suma
FIN
```

**Caso de prueba:** Ejecutar completamente

**Tareas:**
1. Tabla: Iteración | numero | numero <= 10? | suma
2. ¿Cuántas iteraciones hay?
3. ¿El resultado final es 30? (2+4+6+8+10 = 30)

---

### Ejercicio 10: Encontrar el Mínimo (Pseudocódigo)

**Pseudocódigo:**

```
INICIO EncontrarMinimo
    LEER a
    LEER b
    SI a < b ENTONCES
        minimo = a
    SINO
        minimo = b
    FIN_SI
    MOSTRAR minimo
FIN
```

**Casos de prueba:**
- Caso 1: a = 15, b = 23
- Caso 2: a = 50, b = 30

**Tareas:**
1. Dos pruebas de escritorio completas
2. Verificar que en cada caso se elige el menor
3. ¿Qué pasa si a == b?

## Soluciones

### Solución Ejercicio 1: Área de Rectángulo

**Tabla de traza:**

| Paso | Línea | base | altura | area | Salida |
|:-----|:------|:-----|:-------|:-----|:-------|
| 1 | LEER base | 5 | - | - | - |
| 2 | LEER altura | 5 | 8 | - | - |
| 3 | area = base * altura | 5 | 8 | 40 | - |
| 4 | MOSTRAR area | 5 | 8 | 40 | "40" |

**Verificación:** ✅ 5 × 8 = 40 es correcto.

---

### Solución Ejercicio 2: Descuento del 10%

**Tabla de traza:**

| Paso | Línea | precio | descuento | precioFinal | Salida |
|:-----|:------|:-------|:----------|:------------|:-------|
| 1 | LEER precio | 250 | - | - | - |
| 2 | descuento = precio * 0.10 | 250 | 25 | - | - |
| 3 | precioFinal = precio - descuento | 250 | 25 | 225 | - |
| 4 | MOSTRAR precioFinal | 250 | 25 | 225 | "225" |

**Verificación:** ✅ 250 - 25 = 225 es correcto.

---

### Solución Ejercicio 3: Positivo o Negativo

**Caso 1: numero = 15**

| Paso | numero | numero > 0? | Salida |
|:-----|:-------|:------------|:-------|
| 1 | 15 | - | - |
| 2 | 15 | Sí | - |
| 3 | 15 | Sí | "Positivo" |

**Caso 2: numero = -7**

| Paso | numero | numero > 0? | Salida |
|:-----|:-------|:------------|:-------|
| 1 | -7 | - | - |
| 2 | -7 | No | - |
| 3 | -7 | No | "Negativo" |

**Problema identificado:** ⚠️ ¿Qué pasa si numero = 0?
- El algoritmo diría "Negativo", pero 0 no es negativo
- **Solución:** Agregar un caso especial para el cero

---

### Solución Ejercicio 4: Tabla del 5

**Tabla de traza:**

| Iteración | i | i <= 5? | resultado | Salida |
|:----------|:--|:--------|:----------|:-------|
| - | 1 | - | - | - |
| 1 | 1 | Sí | 5 | "5" |
| - | 2 | - | - | - |
| 2 | 2 | Sí | 10 | "10" |
| - | 3 | - | - | - |
| 3 | 3 | Sí | 15 | "15" |
| - | 4 | - | - | - |
| 4 | 4 | Sí | 20 | "20" |
| - | 5 | - | - | - |
| 5 | 5 | Sí | 25 | "25" |
| - | 6 | - | - | - |
| Fin | 6 | No | - | - |

**Verificación:** ✅ Se ejecuta 5 veces. Resultados: 5, 10, 15, 20, 25.

---

### Solución Ejercicio 5: Mayor de Tres Números

**Con a = 12, b = 8, c = 15:**

| Paso | Decisión | Resultado |
|:-----|:---------|:----------|
| 1-3 | Leer a, b, c | a=12, b=8, c=15 |
| 4 | ¿a > b? (12 > 8) | Sí → ir a paso 5 |
| 5 | ¿a > c? (12 > 15) | No → ir a "c es mayor" |
| 6 | Mostrar | "c es mayor" |

**Verificación:** ✅ Correcto, 15 es el mayor de los tres.

---

### Solución Ejercicio 6: Conversión de Temperatura

**Tabla de traza:**

| Paso | celsius | fahrenheit | Salida |
|:-----|:--------|:-----------|:-------|
| 1 | 25 | - | - |
| 2 | 25 | 77 | - |
| 3 | 25 | 77 | "77" |

**Cálculo:** (25 × 9/5) + 32 = 45 + 32 = 77

**Verificación:** ✅ 25°C = 77°F es correcto.

---

### Solución Ejercicio 7: Calcular Edad

**Tabla de traza:**

| Paso | anioNacimiento | anioActual | edad | Salida |
|:-----|:---------------|:-----------|:-----|:-------|
| 1 | 2006 | - | - | - |
| 2 | 2006 | 2024 | - | - |
| 3 | 2006 | 2024 | 18 | - |
| 4 | 2006 | 2024 | 18 | "18" |

**Si cambiamos anioActual a 2025:** edad = 2025 - 2006 = 19

**Nota:** Este algoritmo necesitaría actualizarse cada año. Mejor sería obtener el año actual del sistema.

---

### Solución Ejercicio 8: Aprobar o Desaprobar

**Caso 1: nota = 7**

| Paso | nota | nota >= 6? | Salida |
|:-----|:-----|:-----------|:-------|
| 1 | 7 | Sí | "Aprobado" |

**Caso 2: nota = 4**

| Paso | nota | nota >= 6? | Salida |
|:-----|:-----|:-----------|:-------|
| 1 | 4 | No | "Desaprobado" |

**Caso 3: nota = 6 (caso borde)**

| Paso | nota | nota >= 6? | Salida |
|:-----|:-----|:-----------|:-------|
| 1 | 6 | Sí | "Aprobado" |

**Verificación:** ✅ El caso borde funciona correctamente (>= incluye el 6).

---

### Solución Ejercicio 9: Sumar Pares del 2 al 10

**Tabla de traza:**

| Iteración | numero | numero <= 10? | suma |
|:----------|:-------|:--------------|:-----|
| Inicio | - | - | 0 |
| - | 2 | - | 0 |
| 1 | 2 | Sí | 2 |
| - | 4 | - | 2 |
| 2 | 4 | Sí | 6 |
| - | 6 | - | 6 |
| 3 | 6 | Sí | 12 |
| - | 8 | - | 12 |
| 4 | 8 | Sí | 20 |
| - | 10 | - | 20 |
| 5 | 10 | Sí | 30 |
| - | 12 | - | 30 |
| Fin | 12 | No | 30 |

**Verificación:** ✅ 5 iteraciones. Resultado: 30 (2+4+6+8+10).

---

### Solución Ejercicio 10: Encontrar el Mínimo

**Caso 1: a = 15, b = 23**

| Paso | a | b | a < b? | minimo | Salida |
|:-----|:--|:--|:-------|:-------|:-------|
| 1 | 15 | - | - | - | - |
| 2 | 15 | 23 | - | - | - |
| 3 | 15 | 23 | Sí | 15 | - |
| 4 | 15 | 23 | - | 15 | "15" |

**Caso 2: a = 50, b = 30**

| Paso | a | b | a < b? | minimo | Salida |
|:-----|:--|:--|:-------|:-------|:-------|
| 1 | 50 | - | - | - | - |
| 2 | 50 | 30 | - | - | - |
| 3 | 50 | 30 | No | 30 | - |
| 4 | 50 | 30 | - | 30 | "30" |

**Si a == b:** El algoritmo funcionaría igual, minimo = a (o b, da lo mismo).


## Consejos Finales

:::{tip} Consejos

**Pruebas de Escritorio:**
- Hacelas con papel y lápiz, no en la computadora
- Seguí CADA paso del algoritmo
- No te saltees filas de la tabla
- Verificá el resultado final con una calculadora si es necesario
:::

---

**¡Éxitos con los ejercicios! 🚀**