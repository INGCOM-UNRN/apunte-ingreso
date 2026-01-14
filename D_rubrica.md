---
title: Rúbrica de Evaluación de Prácticas
short_title: 0x0003h - Rúbrica
subtitle: Sistema de evaluación por niveles para entregas de código en Python
---

## Introducción

Esta rúbrica establece un sistema de evaluación de 10 niveles para las entregas de código en el curso. El objetivo es proporcionar un marco transparente y objetivo que valore tanto la **corrección funcional** como la **calidad del código**, con especial énfasis en la **legibilidad**, **claridad** y **apropiación de las herramientas** utilizadas.

:::{important} Principio Fundamental
La evaluación prioriza la **claridad y simplicidad** sobre la sofisticación técnica. El uso de características avanzadas del lenguaje que no han sido cubiertas en el curso puede resultar en una **penalización** o **descalificación** de la entrega, incluso si el código funciona correctamente.
:::

### Filosofía de Evaluación

La rúbrica se fundamenta en los siguientes principios:

1. **Progresión pedagógica:** Se espera que utilices únicamente las herramientas y conceptos presentados hasta el momento del curso
2. **Claridad sobre complejidad:** Un código simple y legible es preferible a una solución compleja y "elegante"
3. **Proceso sobre resultado:** Se valora la estructura del pensamiento reflejada en el código
4. **Buenas prácticas:** Adherencia a las reglas de estilo establecidas (ver {ref}`0x0000h`)

:::{warning} Sobre el Uso de Herramientas Externas
El uso de **herramientas de generación automática de código** (IA, Copilot, ChatGPT, etc.) para resolver ejercicios del exámen está **prohibido** y constituye una falta grave. Las entregas sospechosas de ser generadas automáticamente serán evaluadas con nivel 0 y reportadas.

Sin embargo, podés usar estas herramientas para:
- Entender conceptos teóricos
- Generar casos de prueba
- Obtener explicaciones de errores
- Reformular código que ya escribiste

La clave es que **el código final debe ser tuyo y reflejar tu nivel de comprensión actual**.
:::

---

## Dimensiones de Evaluación

Cada entrega se evalúa según cuatro dimensiones principales:

### 1. Corrección Funcional (40%)

¿El programa resuelve el problema planteado correctamente?

- Casos normales funcionan
- Casos límite manejados apropiadamente
- No produce errores inesperados
- Validación de entradas adecuada

### 2. Legibilidad y Estilo (30%)

¿El código es fácil de leer y entender?

- Nombres descriptivos ({ref}`0x0001h`)
- Indentación consistente ({ref}`0x0005h`)
- Espaciado apropiado ({ref}`0x0004h`)
- Comentarios útiles ({ref}`0x001Dh`)
- Estructura clara

### 3. Diseño y Estructura (20%)

¿El código está bien organizado?

- Descomposición en funciones apropiada ({ref}`0x0016h`)
- Responsabilidad única por función ({ref}`0x000Ch`)
- Flujo lógico coherente
- Reutilización de código

### 4. Apropiación de Herramientas (10%)

¿Se utilizan las herramientas del nivel apropiado?

- Usa solo conceptos ya enseñados
- No usa características "avanzadas" innecesariamente
- Solución acorde al nivel del curso

---

## Niveles de Evaluación

(nivel-10)=
### Nivel 10: Excelencia (100 puntos)

**Código ejemplar que supera las expectativas del curso.**

#### Características

**Corrección funcional:**
- ✓ Funciona perfectamente en todos los casos de prueba
- ✓ Maneja casos límite y excepcionales con elegancia
- ✓ Validación exhaustiva de entradas
- ✓ Mensajes de error claros y útiles

**Legibilidad:**
- ✓ Nombres de variables y funciones excepcionalmente descriptivos
- ✓ Código autoexplicativo, comentarios solo donde aportan valor
- ✓ Estilo impecable, sigue todas las reglas del curso
- ✓ Estructura visual clara y consistente

**Diseño:**
- ✓ Excelente descomposición en funciones con propósitos únicos
- ✓ Abstracción apropiada al nivel del curso
- ✓ Código DRY (Don't Repeat Yourself) sin duplicación
- ✓ Flujo lógico intuitivo y bien pensado

**Apropiación:**
- ✓ Usa exactamente las herramientas apropiadas para el nivel
- ✓ Demuestra comprensión profunda de los conceptos
- ✓ No recurre a soluciones "mágicas" o no enseñadas

#### Ejemplo de Código Nivel 10

```python
def calcular_promedio_aprobados(calificaciones):
    """Calcula el promedio de las calificaciones aprobadas.
    
    Solo considera calificaciones mayores o iguales a 6.
    Si no hay calificaciones aprobadas, retorna 0.
    
    Args:
        calificaciones (list): Lista de números entre 0 y 10
        
    Returns:
        float: Promedio de aprobados o 0 si no hay
    """
    NOTA_MINIMA_APROBACION = 6
    NOTA_MINIMA = 0
    NOTA_MAXIMA = 10
    
    # Validar que la lista no esté vacía
    if not calificaciones:
        return 0
    
    # Filtrar y acumular calificaciones aprobadas
    suma_aprobados = 0
    cantidad_aprobados = 0
    
    for calificacion in calificaciones:
        # Validar rango
        if calificacion < NOTA_MINIMA or calificacion > NOTA_MAXIMA:
            continue
        
        # Contar solo aprobados
        if calificacion >= NOTA_MINIMA_APROBACION:
            suma_aprobados += calificacion
            cantidad_aprobados += 1
    
    # Evitar división por cero
    if cantidad_aprobados == 0:
        return 0
    
    promedio = suma_aprobados / cantidad_aprobados
    return promedio
```

**Por qué es nivel 10:**
- Validación completa y robusta
- Nombres claros y constantes bien definidas
- Maneja todos los casos límite
- Documentación completa
- Flujo lógico claro
- Usa solo estructuras básicas (if, for)

---

(nivel-9)=
### Nivel 9: Muy Bueno (90 puntos)

**Código de alta calidad con mínimas oportunidades de mejora.**

#### Características

**Diferencias con Nivel 10:**
- Puede tener alguna validación faltante menor
- Documentación ligeramente menos completa
- Algún nombre de variable podría ser más descriptivo
- Casos límite manejados pero sin refinamiento extra

**Lo que mantiene:**
- Funciona correctamente en casos principales
- Estilo muy bueno
- Estructura clara
- Apropiación correcta de herramientas

#### Ejemplo de Código Nivel 9

```python
def calcular_promedio_aprobados(calificaciones):
    """Calcula el promedio de las calificaciones aprobadas."""
    if not calificaciones:
        return 0
    
    suma_aprobados = 0
    cantidad_aprobados = 0
    
    for nota in calificaciones:
        if nota >= 6:  # Nota mínima de aprobación
            suma_aprobados += nota
            cantidad_aprobados += 1
    
    if cantidad_aprobados == 0:
        return 0
    
    return suma_aprobados / cantidad_aprobados
```

**Diferencias con nivel 10:**
- Falta validación del rango de notas
- Docstring menos detallado
- No usa constantes con nombre
- Pero cumple perfectamente con lo esencial

---

(nivel-8)=
### Nivel 8: Bueno (80 puntos)

**Código sólido que cumple con los requisitos principales.**

#### Características

**Aspectos positivos:**
- ✓ Funciona correctamente para casos normales
- ✓ Estructura básica clara
- ✓ Nombres generalmente descriptivos
- ✓ Estilo mayormente correcto

**Oportunidades de mejora:**
- Puede faltar alguna validación importante
- Documentación presente pero básica
- Alguna repetición de código menor
- Manejo de casos límite incompleto

#### Ejemplo de Código Nivel 8

```python
def promedio_aprobados(notas):
    """Calcula promedio de aprobados."""
    suma = 0
    contador = 0
    
    for nota in notas:
        if nota >= 6:
            suma = suma + nota
            contador = contador + 1
    
    if contador > 0:
        resultado = suma / contador
    else:
        resultado = 0
    
    return resultado
```

**Por qué es nivel 8:**
- Funciona bien pero no valida lista vacía explícitamente
- Nombres correctos pero genéricos (`suma`, `contador`)
- No usa `+=` (aunque es válido no usarlo)
- Docstring muy básico
- Falta manejo de notas inválidas

---

(nivel-7)=
### Nivel 7: Satisfactorio (70 puntos)

**Código que funciona pero con varias áreas de mejora.**

#### Características

**Lo que funciona:**
- Resuelve el problema principal
- Estructura básica comprensible
- Usa las herramientas apropiadas

**Problemas presentes:**
- Varios nombres poco descriptivos
- Falta validación de casos importantes
- Estilo inconsistente en algunas partes
- Documentación ausente o muy pobre
- Alguna confusión en la lógica

#### Ejemplo de Código Nivel 7

```python
def funcion(lista):
    s = 0
    c = 0
    for x in lista:
        if x >= 6:
            s = s + x
            c = c + 1
    if c > 0:
        return s / c
    else:
        return 0
```

**Problemas:**
- Nombres no descriptivos (`s`, `c`, `x`, `funcion`)
- Sin docstring
- Funciona pero difícil de entender a primera vista
- No valida entrada
- Estilo aceptable pero mejorable

---

(nivel-6)=
### Nivel 6: Apenas Suficiente (60 puntos)

**Código que cumple mínimamente pero con problemas significativos.**

#### Características

**Problemas notables:**
- Funcionalidad básica presente pero frágil
- Múltiples nombres poco claros
- Lógica confusa o redundante
- Sin documentación
- Manejo deficiente de casos especiales
- Errores de estilo múltiples

**Aspectos positivos:**
- Aún resuelve el caso básico
- Muestra comprensión mínima del problema

#### Ejemplo de Código Nivel 6

```python
def f(l):
    s=0
    c=0
    for i in range(len(l)):
        if l[i]>=6:
            s=s+l[i]
            c=c+1
    return s/c if c>0 else 0
```

**Problemas graves:**
- Nombres completamente crípticos
- Sin espacios alrededor de operadores
- Usa `range(len())` en lugar de iterar directamente
- Sin validación
- Sin documentación
- Expresión condicional innecesariamente compacta

---

(nivel-5)=
### Nivel 5: Insuficiente (50 puntos)

**Código con problemas significativos que comprometen su funcionalidad.**

#### Características

**Problemas críticos:**
- Funciona solo en algunos casos particulares
- Errores lógicos evidentes
- Código muy difícil de leer
- No maneja errores básicos
- Estructura confusa

**Lo que aún está presente:**
- Intento legítimo de resolver el problema
- Uso básico de estructuras de control

#### Ejemplo de Código Nivel 5

```python
def calcular(lista):
    suma=0
    for elemento in lista:
        if elemento>=6:
            suma=suma+elemento
    return suma/len(lista)  # ERROR: no cuenta solo aprobados
```

**Problemas críticos:**
- Error lógico: divide por total en lugar de cantidad de aprobados
- No maneja lista vacía (división por cero)
- Sin espacios
- Resultado incorrecto

---

(nivel-4)=
### Nivel 4: Muy Insuficiente (40 puntos)

**Código con errores fundamentales y comprensión limitada.**

#### Características

**Problemas severos:**
- Errores lógicos múltiples
- No resuelve el problema planteado
- Puede tener errores de sintaxis
- Estructura muy deficiente
- Confusión conceptual evidente

**Aspectos rescatables:**
- Muestra algún intento de estructura
- Uso básico de Python

#### Ejemplo de Código Nivel 4

```python
def promedio(lista):
    suma=0
    contador=6
    for i in lista:
        suma=suma+i
        contador=contador+1
    return suma/contador
```

**Errores fundamentales:**
- Inicializa `contador` en 6 (¿?)
- No filtra por aprobados
- Lógica completamente incorrecta
- No entiende el problema

---

(nivel-3)=
### Nivel 3: Inaceptable (30 puntos)

**Código que apenas ejecuta o no resuelve el problema.**

#### Características

**Problemas graves:**
- No resuelve el problema planteado
- Múltiples errores de lógica
- Posibles errores de sintaxis
- Demuestra comprensión muy limitada

#### Ejemplo de Código Nivel 3

```python
def calcular_promedio(lista):
    for i in lista:
        suma = i + i
    return suma / i
```

**Errores críticos:**
- `suma` no inicializada antes del loop
- Lógica sin sentido (`i + i`)
- Divide por último elemento, no por cantidad
- No filtra aprobados

---

(nivel-2)=
### Nivel 2: Fallido (20 puntos)

**Código que no ejecuta o está fundamentalmente roto.**

#### Características

- Errores de sintaxis que impiden ejecución
- Lógica inexistente o sin sentido
- No demuestra comprensión del problema
- Puede estar incompleto

#### Ejemplo de Código Nivel 2

```python
def promedio(lista)
    suma = 0
    for nota lista:
        if nota > 6
            suma = nota
    promedio = suma
```

**Errores fatales:**
- Sin `:` en definición de función
- Sintaxis incorrecta en `for`
- Sin `:` en `if`
- Lógica sin sentido

---

(nivel-1)=
### Nivel 1: No Entregado (10 puntos)

**Entrega ausente, vacía o plagio evidente.**

#### Se aplica cuando:

- No se entregó nada
- Archivo vacío o con código placeholder
- **Plagio detectado** (copia de compañero o internet)
- **Código generado por IA** sin comprensión
- Código completamente irrelevante al problema

:::{danger} Plagio y Generación Automática
Las entregas que constituyan plagio o uso inapropiado de herramientas automáticas recibirán **nivel 1** automáticamente y se reportarán según el régimen académico de la institución.

**Indicadores de generación automática:**
- Uso de características avanzadas no enseñadas
- Estilo de código inconsistente con entregas previas
- Comentarios en inglés o excesivamente detallados
- Type hints avanzados
- Comprehensions complejas en etapas tempranas
- Patrones de código típicos de IA (uso de `any()`, `all()`, etc. antes de enseñarse)
:::

---

(nivel-0)=
### Nivel 0: Descalificación (0 puntos)

**Reservado para casos excepcionales de fraude académico.**

#### Se aplica cuando:

- Plagio confirmado y reincidente
- Entrega maliciosa (código que intenta dañar el sistema)
- Violación grave de normas académicas

---

## Criterios de Penalización

Además de los niveles base, existen penalizaciones específicas que pueden aplicarse:

### Uso de Características No Enseñadas (-10 a -30 puntos)

El uso de características del lenguaje que **no han sido cubiertas** en el curso resulta en penalización:

**Penalización Menor (-10 puntos):**
- List comprehensions antes de ser enseñadas
- Operador ternario (`x if cond else y`)
- Métodos de string avanzados no vistos
- Funciones built-in no presentadas

```python
# ❌ Penalización si no se vieron comprehensions
aprobados = [n for n in notas if n >= 6]

# ✓ Correcto en nivel básico
aprobados = []
for nota in notas:
    if nota >= 6:
        aprobados.append(nota)
```

**Penalización Media (-20 puntos):**
- Funciones lambda
- `map()`, `filter()`, `reduce()`
- Decoradores
- Generadores
- Context managers no enseñados

**Penalización Grave (-30 puntos o descalificación):**
- Imports no autorizados (`numpy`, `pandas`, etc.)
- Programación orientada a objetos
- Metaprogramación
- Características que claramente exceden el nivel

:::{warning} ¿Cómo Saber Qué Está Permitido?
**Regla simple:** Solo podés usar lo que fue **explícitamente enseñado** en las clases hasta el momento de la entrega.

Si tenés dudas, preguntá en el foro o consulta con los docentes **antes** de entregar.
:::

### Violaciones de Estilo Graves (-5 a -15 puntos)

**Penalización Menor (-5 puntos):**
- Inconsistencias menores de espaciado
- Algunos nombres poco descriptivos
- Indentación inconsistente en partes

**Penalización Media (-10 puntos):**
- Múltiples violaciones de nomenclatura
- Código difícil de leer por formato
- Ausencia total de documentación

**Penalización Grave (-15 puntos):**
- Código completamente ilegible
- Violación sistemática de todas las reglas
- Nombres ofensivos o inapropiados

### Errores Funcionales Críticos (-20 a -40 puntos)

**Errores que comprometen la funcionalidad:**
- No maneja caso de entrada vacía (-10)
- División por cero no controlada (-15)
- Errores de lógica fundamentales (-20)
- Crashes en casos básicos (-30)

---

## Tabla de Referencia Rápida

| Nivel | Puntos | Descripción Breve | Funciona | Estilo | Diseño |
|-------|--------|-------------------|----------|--------|--------|
| 10 | 100 | Excelente, ejemplar | ✓✓✓ | ✓✓✓ | ✓✓✓ |
| 9 | 90 | Muy bueno, mínimas mejoras | ✓✓✓ | ✓✓ | ✓✓ |
| 8 | 80 | Bueno, sólido | ✓✓ | ✓✓ | ✓✓ |
| 7 | 70 | Satisfactorio | ✓✓ | ✓ | ✓ |
| 6 | 60 | Apenas suficiente | ✓ | ✓ | ✓ |
| 5 | 50 | Insuficiente | ✓ | ✗ | ✗ |
| 4 | 40 | Muy insuficiente | ✗ | ✗ | ✗ |
| 3 | 30 | Inaceptable | ✗ | ✗ | ✗ |
| 2 | 20 | Fallido | ✗✗ | ✗✗ | ✗✗ |
| 1 | 10 | No entregado/Plagio | ✗✗✗ | ✗✗✗ | ✗✗✗ |
| 0 | 0 | Descalificación | - | - | - |

**Leyenda:**
- ✓✓✓ Excelente
- ✓✓ Bueno
- ✓ Aceptable
- ✗ Deficiente
- ✗✗ Muy deficiente
- ✗✗✗ Inaceptable

---

## Ejemplos Comparativos por Nivel

Para ilustrar las diferencias entre niveles, consideramos el siguiente problema:

```{admonition} Problema
:class: note
Escribir una función que reciba una lista de números y retorne cuántos son pares.
```

### Solución Nivel 10

```python
def contar_pares(numeros):
    """Cuenta la cantidad de números pares en una lista.
    
    Un número es par si es divisible por 2 (resto 0).
    
    Args:
        numeros (list): Lista de números enteros
        
    Returns:
        int: Cantidad de números pares encontrados
        
    Examples:
        >>> contar_pares([1, 2, 3, 4, 5])
        2
        >>> contar_pares([])
        0
    """
    # Validación de entrada
    if not numeros:
        return 0
    
    contador_pares = 0
    
    for numero in numeros:
        if numero % 2 == 0:
            contador_pares += 1
    
    return contador_pares
```

### Solución Nivel 8

```python
def contar_pares(numeros):
    """Cuenta números pares."""
    cantidad = 0
    
    for numero in numeros:
        if numero % 2 == 0:
            cantidad = cantidad + 1
    
    return cantidad
```

### Solución Nivel 6

```python
def contar(lista):
    c = 0
    for n in lista:
        if n%2==0:
            c=c+1
    return c
```

### Solución Nivel 4

```python
def contar_pares(lista):
    contador=0
    for i in range(len(lista)):
        if lista[i]/2==0:  # ERROR: usa / en lugar de %
            contador=contador+1
    return contador
```

---

## Guía para Autoevaluación

Antes de entregar tu código, usá este checklist:

### Checklist Funcional

- [ ] ¿Probé el código con al menos 3 casos diferentes?
- [ ] ¿Funciona con entradas vacías?
- [ ] ¿Maneja valores límite (0, negativos, muy grandes)?
- [ ] ¿Validé las entradas del usuario?
- [ ] ¿Los resultados son correctos?

### Checklist de Estilo

- [ ] ¿Todos los nombres son descriptivos? ({ref}`0x0001h`)
- [ ] ¿Hay espacios alrededor de operadores? ({ref}`0x0004h`)
- [ ] ¿La indentación es consistente (4 espacios)? ({ref}`0x0005h`)
- [ ] ¿Las líneas tienen menos de 79 caracteres? ({ref}`0x000Fh`)
- [ ] ¿Cada función tiene su docstring? ({ref}`0x000Ah`)

### Checklist de Diseño

- [ ] ¿Descompuse el problema en funciones? ({ref}`0x0016h`)
- [ ] ¿Cada función hace una sola cosa? ({ref}`0x000Ch`)
- [ ] ¿Evité repetir código?
- [ ] ¿El flujo es fácil de seguir?

### Checklist de Apropiación

- [ ] ¿Usé solo conceptos ya enseñados en clase?
- [ ] ¿Puedo explicar cada línea de mi código?
- [ ] ¿Escribí este código yo mismo/a?
- [ ] ¿Entiendo por qué funciona?

:::{tip} Si Respondiste "No" a Alguna Pregunta
Ese es un punto de mejora **antes** de entregar. Revisá el código y ajustalo hasta poder responder "Sí" a todas las preguntas relevantes a tu nivel.
:::

---

## Progresión Esperada

Es normal y esperado que tu nivel mejore a lo largo del curso:

### Primeras Entregas
- **Objetivo:** Nivel 6-7
- Enfoque: Lograr que funcione, entender sintaxis básica
- No te preocupes demasiado por la perfección

### Entregas Intermedias
- **Objetivo:** Nivel 7-8
- Enfoque: Mejorar estilo, validaciones, estructura
- Incorporar feedback de entregas anteriores

### Entregas Finales
- **Objetivo:** Nivel 8-9
- Enfoque: Código limpio, bien diseñado, robusto
- Demostrar madurez en la programación

:::{note} Nivel 10 es Aspiracional
El nivel 10 representa código excepcional que supera las expectativas. No es necesario alcanzarlo para aprobar con excelencia. Un nivel 8-9 consistente demuestra dominio completo del material.
:::

---

## Preguntas Frecuentes

### ¿Puedo usar funciones built-in de Python?

**Depende.** Podés usar las funciones que fueron **explícitamente enseñadas**:

**Generalmente permitidas:**
- `print()`, `input()`
- `len()`, `range()`
- `int()`, `float()`, `str()`
- `sum()` (si fue presentado)
- Métodos básicos de strings: `.lower()`, `.upper()`, `.strip()`

**Generalmente NO permitidas:**
- `map()`, `filter()`, `reduce()`
- `any()`, `all()`, `zip()`
- Imports externos

**Regla de oro:** Si no lo viste en clase, preguntá antes de usarlo.

### ¿Qué pasa si mi código funciona, pero es "feo"?

Tu nota se verá afectada. Recordá que la legibilidad vale **30%** de la evaluación. Un código que funciona perfectamente, pero es ilegible no supera nivel 7.

### ¿Puedo copiar código de internet?

**No.** Copiar código sin entenderlo constituye plagio y resultará en nivel 1. Podés:
- Consultar documentación oficial de Python
- Leer explicaciones de conceptos
- Ver ejemplos para **entender** técnicas

Pero el código entregado **debe ser tuyo**.

### ¿Qué pasa si uso algo "avanzado" sin darme cuenta?

Si es un uso menor y el resto del código demuestra comprensión apropiada, probablemente solo sea una observación. Pero si el código completo está por encima del nivel del curso, se considerará sospechoso de generación automática.

### ¿Cómo sé qué tan "descriptivo" debe ser un nombre?

Un buen test: ¿Otra persona que lee tu código puede entender qué hace la variable sin contexto adicional? ({ref}`0x0001h`)

```python
# ❌ Poco descriptivo
x = 25
t = 100

# ✓ Descriptivo
edad_minima = 25
tiempo_espera_segundos = 100
```

### ¿Los comentarios mejoran mi nota?

**Solo si son útiles.** Comentarios que explican lo obvio no aportan:

```python
# ❌ Comentario redundante
i = i + 1  # Incrementa i en 1

# ✓ Comentario útil
i += 1  # Saltamos el encabezado para procesar solo datos
```

Ver {ref}`0x001Dh` para guías sobre comentarios.

### ¿Qué pasa si entrego tarde?

Las políticas de entregas tardías son independientes de esta rúbrica y se especifican en el programa de la materia. Esta rúbrica evalúa **calidad de código**, no puntualidad.

---

## Recursos para Mejorar

### Antes de Entregar

1. **Revisá las reglas de estilo:** {ref}`0x0000h` y siguientes
2. **Aplicá el método de Pólya:** Ver {ref}`polya-comprender`
3. **Probá tu código exhaustivamente**
4. **Pedí feedback a compañeros** (sin copiar código)

### Después de Recibir Feedback

1. **Leé los comentarios cuidadosamente**
2. **Identificá patrones** en tus errores
3. **Practicá las áreas débiles**
4. **Consultá en el foro** si no entendés algo

### Recursos Adicionales

- Documentación oficial de Python: [docs.python.org](https://docs.python.org)
- PEP 8 (Guía de estilo): {ref}`pep-8-ref`
- Foro del curso (para consultas)
- Horarios de consulta con docentes

---

## Conclusión

Esta rúbrica busca ser una herramienta de **transparencia** y **aprendizaje**. El objetivo no es solo asignar una calificación, sino ayudarte a:

1. **Entender** qué se espera en cada nivel
2. **Identificar** áreas de mejora específicas
3. **Progresar** sistemáticamente en tus habilidades
4. **Desarrollar** buenos hábitos de programación

:::{admonition} Mensaje Final
:class: important
La programación es una habilidad que se desarrolla con **práctica** y **reflexión**. No te desanimes si tus primeras entregas no alcanzan el nivel deseado. Cada ejercicio es una oportunidad de aprender y mejorar.

Lo más importante no es el nivel que alcanzás hoy, sino la **trayectoria de mejora** que demostrás a lo largo del curso.

¡Éxitos en tus entregas!
:::

---

## Referencias

- {ref}`0x0000h` - Reglas de estilo completas
- {ref}`polya-comprender` - Método de resolución de problemas
- {ref}`pep-8-ref` - Guía de estilo oficial de Python
- [Código limpio en Python](https://realpython.com/python-code-quality/)
