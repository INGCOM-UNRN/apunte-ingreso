---
title: Primeros Pasos - Cómo Plantear Algoritmos
short_title: 0 - Primeros Pasos
subtitle: Guía práctica paso a paso para diseñar soluciones antes de programar
---

(primeros-pasos-algoritmos)=
# Primeros Pasos: Cómo Plantear Algoritmos

¡Bienvenido! Esta es probablemente la guía más importante que vas a leer en todo el curso. ¿Por qué? Porque te va a enseñar a **pensar** antes de programar.

::::{note} Resumen del Capítulo (TL;DR)

En este capítulo vas a aprender:
- **Qué es un algoritmo** y por qué es importante diseñarlo antes de programar.
- **Cómo analizar un problema** con preguntas clave.
- **Diagramas de flujo:** representar tu solución visualmente.
- **Pseudocódigo:** escribir la solución en "español estructurado".
- **Pruebas de escritorio:** verificar que tu algoritmo funciona **antes** de escribir código.
- **Traducir** tu diseño a código Python.

**Tiempo estimado:** 4-6 horas (¡vale la pena!)
::::

---

## ¿Por qué esta guía es TAN importante?

::::{warning} La verdad incómoda

**Problema común:** Muchos estudiantes abren Python y empiezan a escribir código directamente.

**¿Qué pasa?**
- El código no funciona.
- Se pierden en medio del problema.
- Pasan horas buscando errores.
- Se frustran y abandonan.

**La solución:** Planificar ANTES de programar.
::::

**Analogía del Arquitecto:**

Imaginate que querés construir una casa:
- **Mal enfoque:** Comprás ladrillos y empezás a apilarlos sin pensar.
- **Buen enfoque:** Primero hacés un plano, después construís.

Programar es igual:
- **Mal enfoque:** Abrís Python y empezás a escribir.
- **Buen enfoque:** Diseñás el algoritmo, lo probás en papel, después programás.

---

## 1. ¿Qué es un Algoritmo?

::::{tip} Conceptos Clave

**TL;DR:** Un algoritmo es una **receta** que tiene pasos claros y ordenados para resolver un problema.

**Analogía:** Es como una receta de cocina, pero para computadoras.

**Vocabulario:**
1. **Algoritmo:** Secuencia de pasos precisos que resuelven un problema.
2. **Paso:** Una acción única y clara ("mezclar harina", "leer un número").
3. **Entrada:** Los datos que necesitás al inicio (ingredientes).
4. **Salida:** El resultado que obtenés al final (la comida lista).
5. **Proceso:** Lo que hacés con las entradas para obtener las salidas (cocinar).
::::

### Ejemplo: Receta vs Algoritmo

:::::{grid} 1 1 2 2

::::{grid-item-card} Receta de Panqueques 🥞
**Ingredientes (Entrada):**
- 2 huevos
- 1 taza de harina
- 1 taza de leche

**Pasos (Proceso):**
1. Batir los huevos.
2. Agregar harina y leche.
3. Mezclar hasta que esté suave.
4. Calentar la sartén.
5. Verter mezcla y cocinar 2 min cada lado.

**Resultado (Salida):**
- Panqueques listos.
::::

::::{grid-item-card} Algoritmo: Promedio de 2 Números 🔢
**Entrada:**
- Primer número
- Segundo número

**Proceso:**
1. Leer el primer número.
2. Leer el segundo número.
3. Sumar ambos números.
4. Dividir la suma entre 2.

**Salida:**
- El promedio.
::::

:::::

### Características de un BUEN Algoritmo

Un algoritmo debe ser:

1. **Preciso:** Cada paso debe ser super claro.
   - ❌ "Mezclar"
   - ✅ "Mezclar con batidora eléctrica durante 2 minutos u 8 minutos con batidora manual"

2. **Finito:** Debe terminar en algún momento.
   - ❌ "Seguí cocinando"
   - ✅ "Cocinar hasta que esté dorado (aprox. 2 min)"

3. **Efectivo:** Debe ser posible realizarlo.
   - ❌ "Volar hasta la luna"
   - ✅ "Caminar hasta la panadería"

4. **Ordenado:** Los pasos deben seguir un orden lógico.
   - ❌ "Servir la sopa, calentar el agua, cortar verduras"
   - ✅ "Cortar verduras, calentar el agua, servir la sopa"

::::{note} Quiz Rápido

¿Cuál es un buen algoritmo para hacer un sándwich?

**Opción A:**
1. Agarrar pan.
2. Poner jamón.
3. Fin.

**Opción B:**
1. Agarrar 2 rebanadas de pan.
2. Ponerlas sobre un plato.
3. Colocar 2 fetas de jamón sobre una rebanada.
4. Cubrir con la otra rebanada.
5. Cortar por la mitad (opcional).

**Respuesta:** B es mejor porque es más preciso y claro.
::::

---

(las-cinco-preguntas)=
## 2. Las 5 Preguntas Mágicas

Antes de diseñar cualquier algoritmo, respondé estas 5 preguntas. **No te saltes este paso.**

```{figure} 0_primeros_pasos/cinco_preguntas.svg
:label: fig-cinco-preguntas
:align: center
:width: 95%

Las 5 Preguntas Mágicas para analizar cualquier problema algorítmico
```

::::{tip} Las 5 Preguntas Mágicas

1. **¿Qué datos necesito?** (Entrada)
2. **¿Qué resultado quiero?** (Salida)
3. **¿Qué pasos debo seguir?** (Proceso)
4. **¿Hay situaciones especiales?** (Casos especiales)
5. **¿Necesito repetir algo?** (Repeticiones)
::::

### ¿De donde salen estas preguntas?

Esta guía es una aplicación directa del {ref}`método de Pólya <polya-comprender>`:

| Etapa de Pólya | Preguntas que Usamos |
|:---------------|:---------------------|
| 1. Comprender el problema | Preguntas 1, 2 y 4 |
| 2. Concebir un plan | Pregunta 3 y 5 |
| 3. Ejecutar el plan | Diagrama de flujo / Pseudocódigo |
| 4. Examinar la solución | Pruebas de escritorio |

### Ejemplo Completo: Promedio de 3 Números

**Problema:** Necesito un programa que calcule el promedio de 3 números.

**Aplicando las 5 preguntas:**

**1. ¿Qué datos necesito?**
- Tres números.
- Pueden ser decimales (ej: 7.5, 8.2, 9.0).
- Los llamo: `numero1`, `numero2`, `numero3`.

**2. ¿Qué resultado quiero?**
- El promedio de los tres números.
- Es un número decimal.
- Lo llamo: `promedio`.

**3. ¿Qué pasos debo seguir?**
- Pedir el primer número.
- Pedir el segundo número.
- Pedir el tercer número.
- Sumar los tres números.
- Dividir la suma entre 3.
- Mostrar el resultado.

**4. ¿Hay situaciones especiales?**
- No, siempre son 3 números.
- No hay restricciones especiales.

**5. ¿Necesito repetir algo?**
- No, solo calculo un promedio.

---

## 3. Herramientas para Diseñar: Diagramas de Flujo

::::{tip} Conceptos Clave

**TL;DR:** Los diagramas de flujo son **esquemas** con formas que representan cada paso de tu algoritmo.

**Analogía:** Es como el mapa del tesoro o las instrucciones para armar un mueble: en vez de leer texto, seguís las flechas y formas.

**Vocabulario:**
1. **Símbolo:** Cada forma geométrica (óvalo, rectángulo, etc.).
2. **Flujo:** El camino que sigue el algoritmo (las flechas).
3. **Decisión:** Un punto donde el camino se divide (rombo).
::::

### Los Símbolos Básicos

Estos son los símbolos fundamentales:

```{figure} 0_primeros_pasos/simbolos_flujo.svg
:label: fig-simbolos-flujo
:align: center
:width: 95%

Símbolos estándar de diagramas de flujo
```

**Resumen de símbolos:**

| Símbolo | Significado | Pseudocódigo |
|:--------|:------------|:--------|
| **Óvalo** |  Comienzo | `INICIO` |
| **Rectángulo** | Proceso | `suma ⟸ a + b` |
| **Paralelogramo** | Entrada o Salida | `LEER numero`, `MOSTRAR numero` |
| **Rombo** | Decisión (Sí/No) | `SI ¿edad >= 18?: ... SINO ... FINSI`|
| **Rombo** | {term}`Lazo` | `MIENTRAS ¿edad >= 18? ... FIN MIENTRAS`|
| **Óvalo** | Fin | `FIN` |

Al guardar un valor, o resultado de expresión, utilizaremos `⟸` para distinguirlo del uso en las comparaciones.

:::{important} Guardaespacio y delimitadores

1. **Guardaespacio (`...`):** Los puntos suspensivos actúan como un *placeholder* o guardaespacio en los "Símbolos del {term}`lazo`". Indican la existencia de un bloque de instrucciones arbitrario. (Los `...` no son parte del pseudocódigo, simplemente una llamada a que _puede ir ahí_).

2. **Delimitadores de Alcance (`FIN`, `SINO`):** En pseudocódigo lineal, cláusulas como `FIN SI` o `FIN MIENTRAS` son obligatorias para definir el alcance (*scope*) léxico de la estructura. A diferencia de los diagramas de flujo (donde las flechas indican el cierre) o lenguajes como Python (que usan indentación), estos delimitadores evitan la ambigüedad sintáctica, especialmente al anidar múltiples estructuras de decisión o iteración. 

:::

### Reglas de Diagramas

1. **Siempre se empieza con INICIO.**
2. **Siempre se termina con FIN.**
3. **Las flechas muestran el orden.**
4. **Los rombos tienen 2 salidas: Sí y No.**
5. **Escribir claro dentro de cada símbolo.**
6. **No cruzar flechas.**

### Ejemplo 1: Sumar Dos Números

**Problema:** Pedir dos números, sumarlos y mostrar el resultado.

Este es un diagrama de flujo simple que sigue una secuencia lineal (sin decisiones ni lazos). Muestra claramente el flujo de entrada (leer números), proceso (sumar) y salida (mostrar resultado).

```{mermaid}
flowchart TD
    Start([INICIO])
    Input1[/Leer numero1/]
    Input2[/Leer numero2/]
    Process[suma = numero1 + numero2]
    Output[/MOSTRAR suma/]
    End([FIN])
    
    Start --> Input1
    Input1 --> Input2
    Input2 --> Process
    Process --> Output
    Output ---> End
    
    style Start fill:#90EE90
    style End fill:#FFB6C1
    style Input1 fill:#87CEEB
    style Input2 fill:#87CEEB
    style Output fill:#87CEEB
    style Process fill:#FFE4B5
```

**Explicación paso a paso:** (Que también es el pseudocódigo)

1. `INICIO` ➠ Arrancamos acá.
2. `Leer numero1` ➠ Le pedimos al usuario el primer número.
3. `Leer numero2` ➠ Le pedimos el segundo número.
4. `suma = numero1 + numero2` ➠ Hacemos la cuenta.
5. `MOSTRAR suma` ➠ Le mostramos el resultado al usuario.
6. `FIN` ➠ Terminó el programa.


### Ejemplo 2: ¿Es Mayor de Edad?

**Problema:** Preguntar la edad y decir si es mayor o menor de edad.

Aquí introducimos una **decisión**. El rombo evalúa una {term}`condición` (¿edad >= 18?) y divide el flujo en dos caminos posibles: uno si la condición es verdadera ("Sí") y otro si es falsa ("No"). Solo se ejecuta uno de los dos caminos.

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER edad/]
    Decision{edad >= 18?}
    OutputYes[/MOSTRAR<br/>Sos mayor de edad/]
    OutputNo[/MOSTRAR<br/>Sos menor de edad/]
    End([FIN])
    
    Start --> Input
    Input --> Decision
    Decision -->|Sí| OutputYes
    Decision -->|No| OutputNo
    OutputYes --> End
    OutputNo ---> End
    
    style Start fill:#90EE90
    style End fill:#FFB6C1
    style Input fill:#87CEEB
    style Decision fill:#FFD700
    style OutputYes fill:#87CEEB
    style OutputNo fill:#87CEEB
```

**Explicación paso a paso:**

1. `INICIO` ➠ Arrancamos.
2. `LEER edad` ➠ Pedimos la edad.
3. `SI ¿edad >= 18?:` **DECISIÓN** ➠ Acá el camino se divide.
  - **4 Si** `MOSTRAR "Sos mayor de edad"` ➠ cuando la respuesta es `Sí` (edad es 18 o más).
  - `SINO` ➠ pasamos a las instrucciones cuando la condición es falsa.
  - **4 No** `"MOSTRAR Sos menor de edad"` ➠ cuando la respuesta es `No` (edad es menos de 18).
  - `FIN_SI` ➠ finalizamos el bloque de instrucciones del `SI`.
5. `FIN` ➠ Los dos caminos se juntan y termina.

Es importante destacar que, como la respuesta depende del valor de `edad`, el resultado va a ser único, en función de si cumple o no la condición lógica del rombo.

::::{tip} Tip

En un rombo (decisión), **siempre** hay DOS caminos de salida. Si tu pregunta tiene más de dos respuestas, necesitás más rombos.

Ejemplo: ¿El semáforo está en rojo, amarillo o verde?
- Necesitás 2 rombos: primero preguntar "¿es rojo?", si no, "¿es amarillo?", si no, "es verde".

_Vamos a ver ejemplos más adelante de esto._

::::

### Ejemplo 3: Contar del 1 al 5

**Problema:** Mostrar los números del 1 al 5.

Este diagrama muestra un {term}`lazo`. Observá cómo la flecha vuelve hacia atrás después de incrementar el {term}`contador`, creando un ciclo que se repite hasta que la condición (`contador <= 5`) deja de cumplirse.

```{mermaid}
flowchart TD
    Start([INICIO])
    Init[contador = 1]
    Condition{contador <= 5?}
    Output[/MOSTRAR contador/]
    Increment[contador = contador + 1]
    End([FIN])
    
    Start --> Init
    Init --> Condition
    Condition -->|Sí| Output
    Output --> Increment
    Increment --> Condition
    Condition ---->|No| End
    
    style Start fill:#90EE90
    style End fill:#FFB6C1
    style Init fill:#FFE4B5
    style Condition fill:#FFD700
    style Output fill:#87CEEB
    style Increment fill:#FFE4B5
```

**Explicación paso a paso:**

1. `INICIO` ➠ Arrancamos.
1. `contador ⟸ 1` ➠ Empezamos a contar desde 1.
2. `MIENTRAS ¿contador <= 5?` ➠ Preguntamos: "¿El contador es 5 o menos?".
     - 2.1. `MOSTRAR contador` ➠ Imprimimos el número actual.
     - 2.2. `contador = contador + 1` ➠ Le sumamos 1 al contador.
     - 2.3. `FIN_MIENTRAS` ➠ Volvemos al condicional.
3. `FIN` 

::::{warning} ¡Atención!

Este es un {term}`lazo` o {term}`bucle`. Es cuando una parte del diagrama se repite. La flecha hace una curva para volver al condicional.

**¿Cómo sé que no va a ser infinito?**
- Porque el `contador` aumenta en cada vuelta.
- _Eventualmente_ `contador` será 6.
- En ese momento, la pregunta "`¿contador <= 5?`" será **No**.
- Y sale del {term}`lazo`.
::::

---

## 4. Herramientas para Diseñar: Pseudocódigo

::::{tip} Conceptos Clave

**TL;DR:** El pseudocódigo es escribir tu algoritmo en "español estructurado" - no es código real, pero se parece.

**Analogía:** Es como escribir la letra de una canción antes de componerla. No es la música final, pero tiene la estructura.

**Vocabulario:**
1. **Pseudocódigo:** Código que se parece a un lenguaje de programación, pero está en español.
2. **Palabra clave:** Palabras especiales que usamos (`LEER`, `SI`, `MIENTRAS`).
3. **{term}`Indentación`:** Espacios al inicio de una línea para mostrar explícitamente a qué instrucción pertenece.
::::

### ¿Por Qué Usar Pseudocódigo?

**Ventajas:**
- No te distraés con la {term}`sintaxis` de Python.
- Podés pensar en la lógica pura.
- Es fácil de leer para cualquiera.
- Rápido de escribir y modificar.
- Sirve como "plano" para programar.

### Las Palabras Clave que Vamos a Usar

Además de las instrucciones traducidas de forma 'directa' de los diagramas de flujo, agregaremos algunas más.

| Palabra | Significado | Ejemplo |
|:--------|:------------|:--------|
| `INICIO` | Comienza el algoritmo | `INICIO NombreDelAlgoritmo` |
| `FIN` | Termina el algoritmo | `FIN` |
| `LEER` | Pedir entrada del usuario | `LEER edad` |
| `MOSTRAR` | Mostrar algo en pantalla | `MOSTRAR "Hola"` |
| `⟸` | {term}`Asignación` | `suma ⟸ a + b` |
| `SI ... :` | {term}`Condicional` | `SI edad >= 18 ENTONCES` |
| `SINO` | Camino NO del `SI` | `SINO` |
| `FIN_SI` | Fin de condición | `FIN_SI` |
| `#` | Comentario | `# Esto es un comentario` |

Y vamos a usar tres tipos de lazos que veremos a continuación.

| Palabra | Significado | Ejemplo |
|:--------|:------------|:--------|
| `MIENTRAS` | Lazo mientras | `MIENTRAS contador <= 5` |
| `FIN_MIENTRAS` | Fin del lazo | `FIN_MIENTRAS` |
| `PARA` | Lazo para | `PARA i DESDE 1 HASTA 10` |
| `FIN_PARA` | Fin del lazo para | `FIN_PARA` |

### Plantilla Básica

Todo algoritmo en pseudocódigo sigue una estructura estándar. Comienza con `INICIO` seguido del nombre del algoritmo, contiene los pasos a seguir en el medio, y termina con `FIN`. Esta estructura clara ayuda a organizar el pensamiento y facilita la traducción posterior a código real de cualquier lenguaje de programación.

```
INICIO NombreDelAlgoritmo
    # Acá van los pasos
FIN
```

### Ejemplo 1: Sumar Dos Números

Este es el ejemplo más simple de un algoritmo: sumar dos números ingresados por el usuario. Ilustra los conceptos básicos de entrada (LEER), procesamiento (operación aritmética con ⟸), y salida (MOSTRAR). Es el "Hola Mundo" de los algoritmos: simple pero completo.

```
INICIO SumarDosNumeros
    # Pedir los números
    MOSTRAR "Ingrese el primer número:"
    LEER numero1
    
    MOSTRAR "Ingrese el segundo número:"
    LEER numero2
    
    # Hacer la suma
    suma ⟸ numero1 + numero2
    
    # Mostrar el resultado
    MOSTRAR "La suma es:", suma
FIN
```

**Leelo en voz alta como si fuera español:**
- "Algoritmo para sumar dos números".
- "Mostrar 'Ingrese el primer número'".
- "Leer numero1".
- Y así...

### Ejemplo 2: Mayor de Edad

Este ejemplo introduce el concepto de decisión con la estructura `SI-ENTONCES-SINO`. El algoritmo toma una decisión basándose en una condición (edad >= 18) y ejecuta diferentes acciones según el resultado. Es fundamental para entender cómo los programas pueden tomar diferentes caminos según los datos.

```
INICIO MayorDeEdad
    # Pedir edad
    MOSTRAR "Ingrese su edad:"
    LEER edad
    
    # Verificar
    SI edad >= 18 ENTONCES
        MOSTRAR "Sos mayor de edad"
    SINO
        MOSTRAR "Sos menor de edad"
    FIN_SI
FIN
```

**Fijate:**
- El `SI` tiene un `ENTONCES` al final.
- Lo que está dentro del SI está **indentado** (con espacios).
- Hay un `SINO` para el caso contrario.
- Cierra con `FIN_SI`.

### Ejemplo 3: Contar del 1 al 5

Este ejemplo muestra cómo repetir acciones con la estructura `MIENTRAS`. Los lazos o bucles son esenciales en programación: permiten repetir un bloque de código mientras se cumpla una condición. Observá cómo el contador se incrementa en cada iteración, y cómo eventualmente la condición se vuelve falsa para terminar el lazo.

```
INICIO ContarHastaCinco
    # Empezar desde 1
    contador ⟸ 1
    
    # Repetir mientras sea menor o igual a 5
    MIENTRAS contador <= 5 HACER
        MOSTRAR contador
        contador ⟸ contador + 1
    FIN_MIENTRAS
    
    MOSTRAR "¡Terminé de contar!"
FIN
```

**Notá:**
- `MIENTRAS ... HACER` es un {term}`lazo`.
- Todo lo que está dentro (indentado) se repite.
- `contador ⟸ contador + 1` es muy importante; si no, el {term}`lazo` sería infinito (contador debe 'dirigirse' hacia el valor del condicional).
- Cierra con `FIN_MIENTRAS`.

### Ejemplo 4: Promedio de 3 Números

Este ejemplo combina múltiples conceptos: entrada de datos (leer tres números), procesamiento (sumar y dividir), y salida (mostrar el resultado). El diagrama de flujo que lo acompaña ilustra visualmente cómo se ejecuta el algoritmo paso a paso, mostrando las cajas de entrada, proceso y salida. Es un ejemplo completo de un algoritmo práctico.

```{mermaid}
flowchart TD
    Start([INICIO])
    
    subgraph Entrada [📥 ENTRADA DE DATOS]
        Input1[/LEER num1/]
        Input2[/LEER num2/]
        Input3[/LEER num3/]
    end
    
    subgraph Proceso [⚙️ PROCESAMIENTO]
        Calc1[suma = num1 + num2 + num3]
        Calc2[promedio = suma / 3]
    end
    
    subgraph Salida [📤 SALIDA]
        Output[/MOSTRAR promedio/]
    end
    
    End([FIN])
    
    Start --> Input1
    Input1 --> Input2
    Input2 --> Input3
    Input3 --> Calc1
    Calc1 --> Calc2
    Calc2 --> Output
    Output ---> End
    
    style Start fill:#90EE90
    style End fill:#FFB6C1
    style Input1 fill:#87CEEB
    style Input2 fill:#87CEEB
    style Input3 fill:#87CEEB
    style Calc1 fill:#FFE4B5
    style Calc2 fill:#FFE4B5
    style Output fill:#87CEEB
    style Entrada fill:#E6F3FF
    style Proceso fill:#FFF9E6
    style Salida fill:#F0FFF0
```

**Pseudocódigo correspondiente:**

```
INICIO CalcularPromedio
    suma ⟸ 0
    # Entrada de datos
    MOSTRAR "Ingrese el primer número:"
    LEER num1
    
    MOSTRAR "Ingrese el segundo número:"
    LEER num2
    
    MOSTRAR "Ingrese el tercer número:"
    LEER num3
    
    # Procesamiento
    suma ⟸ num1 + num2 + num3
    promedio ⟸ suma / 3
    
    # Salida
    MOSTRAR "El promedio es:", promedio
FIN
```

::::{tip} Tip de Organización

Fijate que organizamos el pseudocódigo en 3 secciones:
1. **Entrada de datos:** Todo lo que pedimos al usuario.
2. **Procesamiento:** Los cálculos y operaciones.
3. **Salida:** Lo que mostramos.

Esto hace que sea mucho más fácil de leer y entender.
::::

---

(pruebas-escritorio)=
## 5. Pruebas de Escritorio: Verificar que Funciona

::::{tip} Conceptos Clave

**TL;DR:** Las pruebas de escritorio son "ejecutar" tu algoritmo **en papel** para verificar que funciona ANTES de programar.

**Analogía:** Es como cuando revisás tu tarea de matemáticas antes de entregarla. Verificás cada paso con valores de ejemplo.

**Vocabulario:**
1. **Traza:** El seguimiento paso a paso de la ejecución.
2. **Tabla de traza:** Tabla donde anotamos los valores de las variables.
3. **Caso de prueba:** Un ejemplo con valores específicos.
4. **Verificación:** Comprobar que el resultado es correcto.
::::

### ¿Por Qué Hacer Pruebas de Escritorio?

**Razones importantes:**

1. **Encontrar errores de lógica** antes de programar.
2. **Entender cómo funciona** tu algoritmo.
3. **Ahorrar tiempo:** es más fácil corregir el pseudocódigo que código Python.
4. **Ganar confianza:** sabés que va a funcionar.
5. **Practicar** el pensamiento algorítmico.

::::{note} Historia Real

**Estudiante A:** No hace pruebas de escritorio
- Escribe 50 líneas de código Python.
- No funciona.
- Pasa 2 horas buscando el error.
- Se frustra.

**Estudiante B:** Hace pruebas de escritorio
- Encuentra un error en el pseudocódigo en 5 minutos.
- Lo corrige.
- Programa en Python.
- Funciona a la primera.

**¿Cuál preferís ser?**
::::

### Cómo Hacer Pruebas de Escritorio

**Paso 1: Preparar la Tabla**

Crear una tabla con:
- Una columna por cada **{term}`variable`**.
- Filas para cada **paso**.
- Columna extra para **salida** (si hay print).

**Paso 2: Elegir Valores de Prueba**

Elegir números que:
- Sean fáciles de calcular mentalmente.
- Cubran diferentes casos (positivos, negativos, cero).
- No sean muy grandes.

**Paso 3: Ejecutar Paso a Paso**

- Ir línea por línea del pseudocódigo.
- Actualizar la tabla en cada {term}`asignación`.
- Marcar cuando hay salida.
- Seguir las condiciones (SI/MIENTRAS).

**Paso 4: Verificar**

- ¿El resultado final es correcto?
- ¿Tiene sentido?
- ¿Probamos casos diferentes?

### Ejemplo Completo: Promedio de 2 Números

**Pseudocódigo:**

```
LEER num1
LEER num2
suma ⟸ num1 + num2
promedio ⟸ suma / 2
MOSTRAR promedio
```

**Caso de prueba:** `num1 = 8`, `num2 = 12`

**Tabla de traza:**

| Paso | Línea | num1 | num2 | suma | promedio | Salida |
|:-----|:------|:-----|:-----|:-----|:---------|:-------|
| 1 | LEER num1 | 8 | - | - | - | - |
| 2 | LEER num2 | 8 | 12 | - | - | - |
| 3 | suma ⟸ num1 + num2 | 8 | 12 | 20 | - | - |
| 4 | promedio ⟸ suma / 2 | 8 | 12 | 20 | 10 | - |
| 5 | MOSTRAR promedio | 8 | 12 | 20 | 10 | "El promedio es: 10" |

**Verificación:**
- ¿20 / 2 = 10? ✅ Sí.
- ¿El promedio de 8 y 12 es 10? ✅ Sí.
- **¡Funciona!**

### Ejemplo con Decisión: Par o Impar

Este ejemplo combina el uso del {term}`operador` módulo (%) con una estructura de decisión. El operador módulo retorna el resto de una división, y es fundamental para determinar si un número es par o impar. El diagrama de flujo muestra claramente cómo la decisión divide el flujo del algoritmo en dos caminos posibles, uno para cada resultado.

```{mermaid}
flowchart TD
    Start([INICIO])
    Input[/LEER numero/]
    Decision{numero % 2 == 0?}
    OutputPar[/MOSTRAR<br/>Es par/]
    OutputImpar[/MOSTRAR<br/>Es impar/]
    End([FIN])
    
    Start --> Input
    Input --> Decision
    Decision -->|Sí<br/>resto = 0| OutputPar
    Decision -->|No<br/>resto = 1| OutputImpar
    OutputPar --> End
    OutputImpar ---> End
    
    style Start fill:#90EE90
    style End fill:#FFB6C1
    style Input fill:#87CEEB
    style Decision fill:#FFD700
    style OutputPar fill:#87CEEB
    style OutputImpar fill:#87CEEB
```

**Pseudocódigo:**

```
LEER numero
SI numero % 2 == 0 ENTONCES
    MOSTRAR "Es par"
SINO
    MOSTRAR "Es impar"
FIN_SI
```

**Caso de prueba 1:** `numero = 6`

| Paso | número | numero % 2 | {term}`Condición` | Salida |
|:-----|:-------|:-----------|:----------|:-------|
| 1 | 6 | - | - | - |
| 2 | 6 | 0 | 0 == 0 → Verdadero | - |
| 3 | 6 | 0 | Entra al SI | "Es par" |

**Caso de prueba 2:** `numero = 7`

| Paso | número | numero % 2 | Condición | Salida |
|:-----|:-------|:-----------|:----------|:-------|
| 1 | 7 | - | - | - |
| 2 | 7 | 1 | 1 == 0 → Falso | - |
| 3 | 7 | 1 | Entra al SINO | "Es impar" |

**Verificación:**
- 6 es par ✅
- 7 es impar ✅
- **¡Funciona para ambos casos!**

::::{note} Recordatorio del Operador %

El operador `%` (módulo) te da el **resto** de una división:
- `6 % 2 = 0` (6 dividido 2 es 3, resto 0).
- `7 % 2 = 1` (7 dividido 2 es 3, resto 1).
- `10 % 3 = 1` (10 dividido 3 es 3, resto 1).

**Truco para par/impar:**
- Si `numero % 2 == 0`, el número es par.
- Si `numero % 2 == 1`, el número es impar.
::::

### Ejemplo con Lazo: Suma de 1 al 5

**Pseudocódigo:**

```
suma ⟸ 0
i ⟸ 1
MIENTRAS i <= 5 HACER
    suma ⟸ suma + i
    i ⟸ i + 1
FIN_MIENTRAS
MOSTRAR suma
```

**Tabla de traza:**

| Paso | i | suma | i <= 5 | Acción | Salida |
|:-----|:--|:-----|:-------|:-------|:-------|
| 1 | - | 0 | - | Inicializar suma | - |
| 2 | 1 | 0 | - | Inicializar i | - |
| 3 | 1 | 0 | Verdadero | Entra al lazo | - |
| 4 | 1 | 1 | - | suma = 0 + 1 | - |
| 5 | 2 | 1 | - | i = 1 + 1 | - |
| 6 | 2 | 1 | Verdadero | Vuelve al MIENTRAS | - |
| 7 | 2 | 3 | - | suma = 1 + 2 | - |
| 8 | 3 | 3 | - | i = 2 + 1 | - |
| 9 | 3 | 3 | Verdadero | Vuelve al MIENTRAS | - |
| 10 | 3 | 6 | - | suma = 3 + 3 | - |
| 11 | 4 | 6 | - | i = 3 + 1 | - |
| 12 | 4 | 6 | Verdadero | Vuelve al MIENTRAS | - |
| 13 | 4 | 10 | - | suma = 6 + 4 | - |
| 14 | 5 | 10 | - | i = 4 + 1 | - |
| 15 | 5 | 10 | Verdadero | Vuelve al MIENTRAS | - |
| 16 | 5 | 15 | - | suma = 10 + 5 | - |
| 17 | 6 | 15 | - | i = 5 + 1 | - |
| 18 | 6 | 15 | Falso | Sale del lazo | - |
| 19 | 6 | 15 | - | - | "La suma es: 15" |

**Verificación:**
- 1 + 2 + 3 + 4 + 5 = 15 ✅
- El lazo se ejecutó 5 veces ✅
- **¡Funciona!**

::::{warning} Observación Importante

Fijate que en cada vuelta del {term}`lazo`:
1. Sumamos el valor actual de `i` a `suma`.
2. Aumentamos `i` en 1.

Si nos olvidamos de `i ⟸ i + 1`, el lazo sería **infinito** porque `i` siempre sería 1.
::::

---

## 6. Ejercicios Resueltos Paso a Paso

Ahora vamos a resolver problemas completos, siguiendo TODOS los pasos que aprendimos.

### Ejercicio 1: Calculadora Simple

**Problema:** Hacer una calculadora que pida dos números y una operación (+, -, *, /) y muestre el resultado.

#### Paso 1: Las 5 Preguntas

1. **¿Qué datos necesito?**
   - Dos números (pueden ser decimales).
   - Una operación: "+", "-", "*" o "/".

2. **¿Qué resultado quiero?**
   - El resultado de la operación.

3. **¿Qué pasos debo seguir?**
   - Pedir el primer número.
   - Pedir la operación.
   - Pedir el segundo número.
   - Según la operación, hacer el cálculo correspondiente.
   - Mostrar el resultado.

4. **¿Hay situaciones especiales?**
   - División por cero (no se puede).
   - Operación inválida (que no sea +, -, *, /).

5. **¿Necesito repetir algo?**
   - No.

#### Paso 2: Pseudocódigo

```
ALGORITMO Calculadora
    INICIO
        # Variables
        num1, num2, resultado: Real
        operacion: Texto
        
        # Entrada
        MOSTRAR "Ingrese el primer número:"
        LEER num1
        
        MOSTRAR "Ingrese la operación (+, -, *, /):"
        LEER operacion
        
        MOSTRAR "Ingrese el segundo número:"
        LEER num2
        
        # Procesamiento
        SI operacion == "+" ENTONCES
            resultado ⟸ num1 + num2
        SINO SI operacion == "-" ENTONCES
            resultado ⟸ num1 - num2
        SINO SI operacion == "*" ENTONCES
            resultado ⟸ num1 * num2
        SINO SI operacion == "/" ENTONCES
            SI num2 != 0 ENTONCES
                resultado ⟸ num1 / num2
            SINO
                MOSTRAR "Error: No se puede dividir por cero"
                FIN
            FIN_SI
        SINO
            MOSTRAR "Operación inválida"
            FIN
        FIN_SI
        
        # Salida
        MOSTRAR "El resultado es:", resultado
    FIN
FIN_ALGORITMO
```

#### Paso 3: Prueba de Escritorio

**Caso 1:** `num1 = 10`, `operacion = "+"`, `num2 = 5`

| Paso | num1 | operacion | num2 | resultado | Salida |
|:-----|:-----|:----------|:-----|:----------|:-------|
| 1 | 10 | - | - | - | - |
| 2 | 10 | "+" | - | - | - |
| 3 | 10 | "+" | 5 | - | - |
| 4 | 10 | "+" | 5 | 15 | - |
| 5 | 10 | "+" | 5 | 15 | "El resultado es: 15" |

**Verificación:** 10 + 5 = 15 ✅

**Caso 2:** `num1 = 10`, `operacion = "/"`, `num2 = 0`

| Paso | num1 | operacion | num2 | Condición | Salida |
|:-----|:-----|:----------|:-----|:----------|:-------|
| 1 | 10 | - | - | - | - |
| 2 | 10 | "/" | - | - | - |
| 3 | 10 | "/" | 0 | - | - |
| 4 | 10 | "/" | 0 | operacion == "/" → Sí | - |
| 5 | 10 | "/" | 0 | num2 != 0 → No | "Error: No se puede dividir por cero" |

**Verificación:** Detecta el error ✅

#### Paso 4: Código Python

```python
# Calculadora simple
num1 = float(input("Ingrese el primer número: "))
operacion = input("Ingrese la operación (+, -, *, /): ")
num2 = float(input("Ingrese el segundo número: "))

if operacion == "+":
    resultado = num1 + num2
    print(f"El resultado es: {resultado}")
elif operacion == "-":
    resultado = num1 - num2
    print(f"El resultado es: {resultado}")
elif operacion == "*":
    resultado = num1 * num2
    print(f"El resultado es: {resultado}")
elif operacion == "/":
    if num2 != 0:
        resultado = num1 / num2
        print(f"El resultado es: {resultado}")
    else:
        print("Error: No se puede dividir por cero")
else:
    print("Operación inválida")
```

### Ejercicio 2: Número Positivo, Negativo o Cero

**Problema:** Leer un número y decir si es positivo, negativo o cero.

#### Paso 1: Las 5 Preguntas

1. **Entrada:** Un número (puede ser decimal).
2. **Salida:** "Positivo", "Negativo" o "Cero".
3. **Pasos:** Leer número, comparar con 0, mostrar mensaje.
4. **Casos especiales:** El cero es un caso especial (no es ni positivo ni negativo).
5. **Repeticiones:** No.

#### Paso 2: Pseudocódigo

```
ALGORITMO PositivoNegativoCero
    INICIO
        numero: {term}`Flotante<Real>`
        
        MOSTRAR "Ingrese un número:"
        LEER numero
        
        SI numero > 0 ENTONCES
            MOSTRAR "El número es positivo"
        SINO SI numero < 0 ENTONCES
            MOSTRAR "El número es negativo"
        SINO
            MOSTRAR "El número es cero"
        FIN_SI
    FIN
FIN_ALGORITMO
```

#### Paso 3: Python

```python
numero = float(input("Ingrese un número: "))

if numero > 0:
    print("El número es positivo")
elif numero < 0:
    print("El número es negativo")
else:
    print("El número es cero")
```

### Ejercicio 3: Tabla de Multiplicar

**Problema:** Mostrar la tabla de multiplicar de un número del 1 al 10.

#### Paso 1: Las 5 Preguntas

1. **Entrada:** Un número.
2. **Salida:** 10 líneas con las multiplicaciones.
3. **Pasos:** Leer número, repetir del 1 al 10, en cada repetición multiplicar y mostrar.
4. **Casos especiales:** Funciona con cualquier número.
5. **Repeticiones:** Sí, 10 veces.

#### Paso 2: Pseudocódigo

```
ALGORITMO TablaMultiplicar
    INICIO
        numero, i, resultado: {term}`Entero`
        
        MOSTRAR "Ingrese un número:"
        LEER numero
        
        MOSTRAR "Tabla del", numero, ":"
        
        PARA i DESDE 1 HASTA 10 HACER
            resultado ⟸ numero * i
            MOSTRAR numero, "x", i, "=", resultado
        FIN_PARA
    FIN
FIN_ALGORITMO
```

#### Paso 3: Prueba de Escritorio (parcial)

**Caso:** `numero = 5`

| i | resultado | Salida |
|:--|:----------|:-------|
| 1 | 5 | "5 x 1 = 5" |
| 2 | 10 | "5 x 2 = 10" |
| 3 | 15 | "5 x 3 = 15" |
| ... | ... | ... |
| 10 | 50 | "5 x 10 = 50" |

#### Paso 4: Python

```python
numero = int(input("Ingrese un número: "))

print(f"Tabla del {numero}:")

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i} = {resultado}")
```

### Ejercicio 4: Suma de Números Hasta que el Usuario Diga "Basta"

**Problema:** Pedir números al usuario, sumarlos, y parar cuando ingrese 0.

#### Paso 1: Las 5 Preguntas

1. **Entrada:** Números (cantidad desconocida), hasta que ingrese 0.
2. **Salida:** La suma de todos los números.
3. **Pasos:** Inicializar suma en 0, pedir número, mientras no sea 0, sumarlo y pedir otro.
4. **Casos especiales:** Si el primer número es 0, la suma es 0.
5. **Repeticiones:** Sí, pero no sabemos cuántas (depende del usuario).

#### Paso 2: Pseudocódigo

```
ALGORITMO SumaHastaCero
    INICIO
        numero, suma: {term}`Flotante<Real>`
        
        suma ⟸ 0
        
        MOSTRAR "Ingrese un número (0 para terminar):"
        LEER numero
        
        MIENTRAS numero != 0 HACER
            suma ⟸ suma + numero
            MOSTRAR "Ingrese otro número (0 para terminar):"
            LEER numero
        FIN_MIENTRAS
        
        MOSTRAR "La suma total es:", suma
    FIN
FIN_ALGORITMO
```

#### Paso 3: Prueba de Escritorio

**Caso:** Usuario ingresa: 5, 10, 15, 0

| Paso | numero | suma | Condición | Salida |
|:-----|:-------|:-----|:----------|:-------|
| 1 | - | 0 | - | - |
| 2 | 5 | 0 | - | - |
| 3 | 5 | 0 | 5 != 0 → Verdadero | - |
| 4 | 5 | 5 | - | - |
| 5 | 10 | 5 | - | - |
| 6 | 10 | 5 | 10 != 0 → Verdadero | - |
| 7 | 10 | 15 | - | - |
| 8 | 15 | 15 | - | - |
| 9 | 15 | 15 | 15 != 0 → Verdadero | - |
| 10 | 15 | 30 | - | - |
| 11 | 0 | 30 | - | - |
| 12 | 0 | 30 | 0 != 0 → Falso | - |
| 13 | 0 | 30 | Sale del lazo | "La suma total es: 30" |

**Verificación:** 5 + 10 + 15 = 30 ✅

#### Paso 4: Python

```python
suma = 0

numero = float(input("Ingrese un número (0 para terminar): "))

while numero != 0:
    suma = suma + numero
    numero = float(input("Ingrese otro número (0 para terminar): "))

print(f"La suma total es: {suma}")
```

---

## 8. Patrones Comunes que Vas a Ver Siempre

Hay ciertos "patrones" que aparecen una y otra vez en programación. Si los reconocés, programar es mucho más fácil.

### Patrón 1: El Acumulador

El {term}`acumulador` es uno de los patrones más fundamentales en programación. Consiste en una {term}`variable` que va "acumulando" o "juntando" valores a medida que se procesan datos. Es especialmente útil para calcular sumas, productos, o cualquier operación que necesite combinar múltiples valores en uno solo. El concepto clave es mantener un total parcial que se actualiza en cada iteración.

**¿Qué es?** Una variable que va "juntando" valores.

**Ejemplo:** Sumar números

```
suma ⟸ 0
PARA cada numero HACER
    suma ⟸ suma + numero
FIN_PARA
```

**Clave:** 
- Empezar en 0 (o 1 para multiplicación).
- En cada vuelta, sumar (o multiplicar) y guardar el resultado.

### Patrón 2: El Contador

El {term}`contador` es otro patrón esencial que aparece constantemente en programación. A diferencia del acumulador que suma valores, el contador simplemente cuenta cuántas veces ocurre algo. Es útil para estadísticas, validaciones, o cualquier situación donde necesitás saber "cuántos" elementos cumplen cierta condición. La clave es incrementar en 1 cada vez que se cumple la condición.

**¿Qué es?** Una variable que cuenta cuántas veces pasa algo.

**Ejemplo:** Contar cuántos números son positivos.

```
contador ⟸ 0
PARA cada numero HACER
    SI numero > 0 ENTONCES
        contador ⟸ contador + 1
    FIN_SI
FIN_PARA
```

**Clave:**
- Empezar en 0.
- Cuando pasa lo que querés contar, sumar 1.

### Patrón 3: Buscar el Máximo (o Mínimo)

Encontrar el valor máximo o mínimo en un conjunto de datos es un problema clásico en programación. Este patrón mantiene el "mejor" valor encontrado hasta el momento y lo compara con cada nuevo valor. Si se encuentra uno mejor, se reemplaza. Es fundamental para ordenamiento, búsquedas, y optimización. El truco está en empezar con el primer valor como candidato inicial.

**¿Qué es?** Encontrar el número más grande (o más chico).

**Ejemplo:** Encontrar el número más grande.

```
maximo ⟸ primer_numero
PARA cada numero HACER
    SI numero > maximo ENTONCES
        maximo ⟸ numero
    FIN_SI
FIN_PARA
```

**Clave:**
- Empezar con el primer valor.
- Si encontrás uno más grande, reemplazarlo.

### Patrón 4: La Bandera (Flag)

La {term}`bandera` o flag es una {term}`variable` {term}`booleana<Booleano>` (Verdadero/Falso) que "recuerda" si algo ocurrió durante el procesamiento. Es útil cuando necesitás verificar la presencia de algo sin importar cuántas veces ocurra. Una vez que la bandera se activa (cambia a Verdadero), permanece así. Este patrón es común en validaciones, búsquedas, y control de flujo.

**¿Qué es?** Una variable que "recuerda" si algo pasó.

**Ejemplo:** Ver si hay algún número negativo.

```
hay_negativo ⟸ Falso
PARA cada numero HACER
    SI numero < 0 ENTONCES
        hay_negativo ⟸ Verdadero
    FIN_SI
FIN_PARA

SI hay_negativo ENTONCES
    MOSTRAR "Hay al menos un negativo"
FIN_SI
```

**Clave:**
- Empezar en Falso.
- Cuando encontrás lo que buscás, cambiar a Verdadero.
- Al final, chequear el valor.

### Patrón 5: Validación de Entrada

La validación de entrada es crucial para crear programas robustos. Este patrón usa un {term}`lazo` que se repite hasta que el usuario ingrese un dato válido. Es esencial para prevenir errores y garantizar que el programa reciba datos dentro del rango esperado. Combina lazos con condiciones para crear una experiencia de usuario más amigable y programas más confiables.

**¿Qué es?** Seguir pidiendo un dato hasta que sea válido.

**Ejemplo:** Pedir una edad entre 1 y 120.

```
REPETIR
    MOSTRAR "Ingrese edad (1-120):"
    LEER edad
    SI edad < 1 O edad > 120 ENTONCES
        MOSTRAR "Edad inválida, intente de nuevo"
    FIN_SI
HASTA QUE edad >= 1 Y edad <= 120

# Acá ya tengo una edad válida
```

**Clave:**
- Usar un {term}`lazo` que repite hasta tener un valor válido.
- Dar feedback al usuario si se equivoca.

---


## 9. Resumen y Consejos Finales

```{figure} 0_primeros_pasos/proceso_completo.svg
:label: fig-proceso-completo
:align: center
:width: 95%

Proceso completo de 4 pasos: de problema a código con tiempos estimados
```

::::{tip} El Proceso Completo

**Cuando te dan un problema, seguí estos pasos:**

1. **Leer y entender:** No empieces hasta entender completamente.
2. **Responder las 5 preguntas:** Entrada, salida, proceso, casos especiales, repeticiones.
3. **Hacer diagrama de flujo O pseudocódigo:** Elegí el que te resulte más fácil.
4. **Hacer prueba de escritorio:** Con al menos 2 casos diferentes.
5. **Si funciona en papel, programar en Python:** Traducir paso a paso.
6. **Probar el código:** Con los mismos casos de la prueba de escritorio.
7. **Si no funciona, volver al pseudocódigo:** Buscar el error en la lógica.

**¡NO salteés pasos!** Cada uno tiene su propósito.
::::

### Conexión con el Método de Pólya

Recordá que esta guía es una aplicación del {ref}`método de Pólya <polya-comprender>`:

1. **Comprender** → Las 5 preguntas.
2. **Planificar** → Diagrama de flujo / Pseudocódigo.
3. **Ejecutar** → Prueba de escritorio.
4. **Verificar** → Código Python y pruebas.

### Consejos de Oro

1. **Empezá simple:** Resolvé primero el caso más básico, después agregá complejidad.
2. **Comentá tu código:** Explicá el "por qué", no solo el "qué".
3. **Usá nombres claros:** `suma_total` es mejor que `x`.
4. **Probá casos extremos:** Números muy grandes, muy chicos, cero, negativos.
5. **Pedí ayuda:** Si estás trabado más de 30 minutos, consultá.

---

## 10. Ejercicios para Practicar

Para poner en práctica todo lo aprendido, hemos preparado una colección completa de ejercicios organizados por nivel de dificultad y con distintos niveles de ayuda (desde diagramas completos hasta solo enunciados).

👉 **[Ir a los Ejercicios de Programación](../enunciados/programacion.md)**

Allí encontrarás ejercicios clásicos como sumas, promedios, tablas de multiplicar, factoriales, series de Fibonacci y más. ¡Te recomendamos hacerlos todos!

---

## 11. Conclusión

::::{important} Lo Más Importante

**Pensar ANTES de programar** es la habilidad más valiosa que podés desarrollar.

- Los diagramas de flujo y el pseudocódigo **no son una pérdida de tiempo**.
- Las pruebas de escritorio **te ahorran HORAS de depuración**.
- Un algoritmo bien diseñado se programa **10 veces más rápido**.

**La programación no es tipear rápido, es PENSAR bien.**
::::

### Próximos Pasos

Ahora que sabés plantear algoritmos, estás listo para:

1. Profundizar en {ref}`Fundamentos de Python <fundamentos>`.
2. Dominar el {ref}`Control de Flujo <control-flujo>`.
3. Aplicar el {ref}`método de Pólya <polya-comprender>` a problemas más complejos.

### Mensaje Final

No te desanimes si al principio te resulta lento. **Todos los programadores profesionales** pasan por este proceso (algunos en papel, otros mentalmente, pero todos lo hacen).

Con práctica, este proceso se vuelve natural y rápido. La inversión de tiempo ahora te ahorrará DÍAS de frustración después.

**¡Éxito en tu camino como programador! 🚀**

