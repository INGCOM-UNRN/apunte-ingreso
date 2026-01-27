---
title: Índice General del Apunte
subtitle: Referencia completa de todos los temas del curso de Introducción a la Programación
---

# Índice General del Apunte de Python

Este índice proporciona una vista global y navegable de todos los contenidos del apunte. Cada sección incluye referencias cruzadas directas a los temas correspondientes.

---

## 📚 Estructura del Curso

### Parte I: Fundamentos y Metodología

#### [0. Primeros Pasos: Cómo Plantear Algoritmos](0_primeros_pasos.md)

Guía fundamental para diseñar soluciones antes de programar.

**Secciones principales:**
- ¿Por qué esta guía es tan importante?
- {ref}`primeros-pasos-algoritmos` - ¿Qué es un algoritmo?
- {ref}`las-cinco-preguntas` - Las 5 Preguntas Mágicas para analizar problemas
- Diagramas de flujo: representación visual de algoritmos
- Pseudocódigo: escribir soluciones en "español estructurado"
- Pruebas de escritorio: verificar el algoritmo antes de programar
- Traducción de diseño a código Python

**Temas clave:**
- Características de un buen algoritmo
- Símbolos de diagramas de flujo (inicio/fin, entrada/salida, proceso, decisión)
- Patrones comunes de algoritmos
- Ejercicios paso a paso

---

#### [0b. Cómo Pensar: Método de Pólya](0_como_pensar.md)

Estrategia sistemática para resolver problemas computacionales y algorítmicos.

**Las Cuatro Etapas:**
1. {ref}`polya-comprender` - Comprender el problema
   - Preguntas clave
   - Traducción a especificación
   - Identificar entradas, salidas y restricciones

2. {ref}`polya-planificar` - Concebir un plan
   - Estrategias de planificación
   - Dividir y conquistar
   - Buscar patrones
   - Simplificar el problema

3. Ejecutar el plan
   - Implementar la solución
   - Validar paso a paso

4. Verificar y reflexionar
   - Probar con casos de borde
   - Optimizar
   - Generalizar la solución

**Ejemplos trabajados:**
- Cálculo de promedio
- Búsqueda del máximo
- Validación de entrada

---

### Parte II: Conceptos Fundamentales de Python

#### [1. Fundamentos de Programación](1_fundamentos.md)

Introducción a los conceptos básicos de Python.

**Secciones:**

**1.1 Introducción**
- ¿Qué es programar?
- ¿Por qué Python? 🐍

**1.2 {ref}`primer-programa`**
- El legendario "Hola Mundo"
- Anatomía de un programa
- Ejecutar código en Python

**1.3 {ref}`variables`**
- {ref}`creacion-variables` - Qué es una variable
- Asignación de valores
- Nombres de variables (convenciones)
- Tipos de datos básicos

**1.4 Tipos de Datos Fundamentales**
- **Números:** `int` (enteros), `float` (decimales)
- **Texto:** `str` (cadenas)
- **Booleanos:** `bool` (True/False)
- Conversión entre tipos (`int()`, `float()`, `str()`)

**1.5 Operadores**
- Aritméticos: `+`, `-`, `*`, `/`, `//`, `%`, `**`
- Comparación: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Lógicos: `and`, `or`, `not`
- Precedencia de operadores

**1.6 Entrada y Salida**
- `input()` - Leer datos del usuario
- `print()` - Mostrar información
- Formateo de salida

**1.7 Comentarios**
- Comentarios de una línea (`#`)
- Comentarios multilínea (`"""`)
- Buenas prácticas de documentación

**Ejercicios incluidos:**
- Variables y tipos
- Operaciones matemáticas
- Conversión de tipos
- Entrada y salida

---

#### [2. Control de Flujo](2_control_flujo.md)

Estructuras que permiten tomar decisiones y repetir acciones.

**Secciones:**

**2.1 Introducción**
- {ref}`control-flujo` - ¿Qué es el control de flujo?
- Analogía del semáforo 🚦
- Programa "tonto" vs programa "inteligente"

**2.2 Condicionales**
- **`if` simple:** Ejecutar código si se cumple condición
- **`if-else`:** Elegir entre dos caminos
- **`if-elif-else`:** Múltiples condiciones
- Operador ternario: `x if condicion else y`
- Condicionales anidados

**2.3 Lazos (Bucles)**
- **`while`:** Repetir mientras se cumpla condición
  - Estructura básica
  - Control de lazos con `break` y `continue`
  - Lazo infinito (y cómo evitarlo)
  - Patrones comunes: contador, acumulador, centinela

- **`for`:** Iterar sobre secuencias
  - Recorrer listas, tuplas, cadenas
  - `range()`: generar secuencias numéricas
  - `enumerate()`: obtener índice y valor
  - Lazos anidados

**2.4 Match-Case (Python 3.10+)**
- Sintaxis básica
- Patterns (patrones de coincidencia)
- Guards (condiciones adicionales)
- Wildcard (`_`)

**Patrones de Control de Flujo:**
- Validación de entrada
- Búsqueda en secuencias
- Procesamiento por lotes
- Menús interactivos

**Errores Comunes:**
- Condiciones mal formuladas
- Lazos infinitos
- Indentación incorrecta
- Off-by-one errors

**Ejercicios:**
- Validación de edad
- Calculadora simple
- Números pares en rango
- Factorial
- Suma de lista

---

#### [3. Estructuras de Datos](3_estructuras.md)

Colecciones para organizar y manipular múltiples valores.

**Secciones:**

**3.1 Introducción**
- {ref}`estructuras-datos` - Del dato individual a las colecciones
- ¿Por qué necesitamos estructuras de datos?
- Comparación visual: ¿cuál elegir?

**3.2 Listas (list)**
- Crear listas: `[]`, `list()`
- Indexación y slicing
- Métodos principales:
  - Agregar: `append()`, `insert()`, `extend()`
  - Eliminar: `remove()`, `pop()`, `clear()`
  - Ordenar: `sort()`, `reverse()`
  - Buscar: `index()`, `count()`
- Listas por comprensión
- Listas anidadas (matrices)
- Mutabilidad

**3.3 Tuplas (tuple)**
- Crear tuplas: `()`, `tuple()`
- Inmutabilidad
- Desempaquetado de tuplas
- Usos comunes: retornar múltiples valores
- Métodos: `count()`, `index()`

**3.4 Conjuntos (set)**
- Crear conjuntos: `{}`, `set()`
- Características: sin orden, sin duplicados
- Operaciones de conjuntos:
  - Unión: `|`, `union()`
  - Intersección: `&`, `intersection()`
  - Diferencia: `-`, `difference()`
  - Diferencia simétrica: `^`, `symmetric_difference()`
- Métodos: `add()`, `remove()`, `discard()`
- Verificar pertenencia: `in`

**3.5 Diccionarios (dict)**
- Crear diccionarios: `{}`, `dict()`
- Pares clave-valor
- Acceder a valores: `[]`, `get()`
- Agregar/modificar elementos
- Métodos principales:
  - `keys()`, `values()`, `items()`
  - `update()`, `pop()`, `popitem()`
  - `setdefault()`
- Diccionarios por comprensión
- Diccionarios anidados

**3.6 Comparación de Estructuras**

| Estructura | Ordenada | Mutable | Duplicados | Acceso | Uso Principal |
|------------|----------|---------|------------|--------|---------------|
| Lista | ✅ | ✅ | ✅ | Por índice | Colección general |
| Tupla | ✅ | ❌ | ✅ | Por índice | Datos inmutables |
| Conjunto | ❌ | ✅ | ❌ | N/A | Elementos únicos |
| Diccionario | ✅* | ✅ | Claves no | Por clave | Pares clave-valor |

**Patrones Comunes:**
- Procesar lista con filtrado
- Buscar duplicados
- Contar frecuencias con diccionarios
- Agrupar datos relacionados

**Errores Comunes:**
- Modificar lista mientras se itera
- Confundir mutabilidad vs inmutabilidad
- Claves duplicadas en diccionarios
- Index out of range

**Ejercicios:**
- Manejo de listas
- Operaciones con conjuntos
- Diccionarios de contactos
- Análisis de datos

---

#### [4. Funciones](4_funciones.md)

Bloques de código reutilizables que realizan tareas específicas.

**Secciones:**

**4.1 Introducción**
- {ref}`funciones` - ¿Qué es una función?
- ¿Por qué usar funciones?
- Beneficios: reutilización, organización, abstracción

**4.2 {ref}`definir-funciones`**
- Tu primera función
- Sintaxis: `def nombre(parametros):`
- Llamar funciones
- Anatomía de una función

**4.3 Parámetros y Argumentos**
- Parámetros posicionales
- Parámetros con valores por defecto
- Argumentos por palabra clave (keyword arguments)
- `*args`: número variable de argumentos posicionales
- `**kwargs`: número variable de argumentos por palabra clave

**4.4 Retorno de Valores**
- Sentencia `return`
- Retornar múltiples valores (tuplas)
- Funciones sin `return` (retornan `None`)
- Return temprano para control de flujo

**4.5 Scope (Alcance de Variables)**
- Variables locales vs globales
- Palabra clave `global`
- Palabra clave `nonlocal`
- LEGB rule (Local, Enclosing, Global, Built-in)

**4.6 Documentación de Funciones**
- Docstrings: `"""..."""`
- Convención de documentación
- Acceder a docstrings: `help()`, `__doc__`

**4.7 Funciones Lambda**
- Sintaxis: `lambda parametros: expresion`
- Casos de uso: funciones anónimas simples
- Uso con `map()`, `filter()`, `sorted()`

**4.8 Funciones como Objetos de Primera Clase**
- Asignar funciones a variables
- Pasar funciones como argumentos
- Retornar funciones desde funciones
- Callbacks

**4.9 Recursión**
- Concepto de función recursiva
- Caso base y caso recursivo
- Ejemplos: factorial, Fibonacci
- Limitaciones y stack overflow

**Patrones de Funciones:**
- Validación de entrada
- Procesamiento y transformación
- Funciones helper (auxiliares)
- Composición de funciones

**Buenas Prácticas:**
- Una función, una responsabilidad
- Nombres descriptivos
- Documentar con docstrings
- Evitar efectos secundarios
- Mantener funciones cortas

**Errores Comunes:**
- Olvidar `return`
- Modificar parámetros mutables
- Usar valores por defecto mutables
- Recursión sin caso base

**Ejercicios:**
- Funciones matemáticas
- Validadores
- Procesamiento de listas
- Funciones recursivas

---

### Parte III: Temas Avanzados y Herramientas

#### [A. F-Strings y Formateo de Cadenas](A_fstrings.md)

Técnicas modernas para formatear texto en Python.

**Contenido:**
- Métodos antiguos:
  - Concatenación con `+`
  - Método `.format()`
  - Operador `%` (estilo C)

- **F-Strings (Python 3.6+):** ✨
  - Sintaxis: `f"texto {variable}"`
  - Expresiones dentro de f-strings
  - Formateo de números: `.2f`, `.3e`
  - Alineación: `<`, `>`, `^`
  - Rellenar con caracteres
  - Debug con `=` (Python 3.8+)

- Casos de uso:
  - Mensajes dinámicos
  - Reportes formateados
  - Logging y debugging

**Ejemplos prácticos:**
- Tabla de precios
- Mensajes personalizados
- Formateo de fechas y números

---

#### [B. Manejo de Excepciones](B_excepciones.md)

Controlar errores y mantener el programa funcionando.

**Secciones:**

**B.1 Introducción**
- {ref}`excepciones-capitulo` - Los errores son parte del juego
- Programa frágil vs programa robusto

**B.2 {ref}`que-son-excepciones`**
- Analogía: alarma de seguridad
- Tipos comunes de excepciones:
  - `ValueError`: valor inapropiado
  - `TypeError`: tipo incorrecto
  - `ZeroDivisionError`: división por cero
  - `IndexError`: índice fuera de rango
  - `KeyError`: clave no existe en diccionario
  - `FileNotFoundError`: archivo no encontrado
  - `AttributeError`: atributo no existe

**B.3 Capturar Excepciones**
- Estructura `try-except`
- Capturar excepciones específicas
- Múltiples bloques `except`
- Capturar múltiples excepciones: `except (Type1, Type2)`
- Bloque `else`: ejecutar si no hay excepción
- Bloque `finally`: ejecutar siempre

**B.4 Lanzar Excepciones**
- Sentencia `raise`
- Re-lanzar excepciones
- Crear excepciones personalizadas (herencia de `Exception`)

**B.5 Mejores Prácticas**
- Capturar excepciones específicas (no `except:` desnudo)
- No silenciar errores
- Logging de errores
- Limpiar recursos con `finally`

**Patrones Comunes:**
- Validación de entrada robusta
- Manejo de archivos
- Conversión segura de tipos
- Reintentos con límite

**Errores Comunes:**
- Capturar excepciones demasiado amplias
- Ignorar excepciones silenciosamente
- Usar excepciones para control de flujo normal

**Ejercicios:**
- Calculadora robusta
- Lectura de archivos con manejo de errores
- Validador con excepciones personalizadas

---

#### [C. Módulos y Bibliotecas](C_modulos.md)

Referencia completa de módulos estándar y tipos de datos.

**Secciones:**

**C.1 Introducción**
- {ref}`referencia-tipos` - La Biblioteca Estándar de Python
- Importar módulos: `import`, `from ... import`

**C.2 {ref}`referencia-str` - Cadenas (str)**

**Mapa de Métodos:**

*Búsqueda y Verificación:*
- `str.find(sub)` → int
- `str.index(sub)` → int
- `str.count(sub)` → int
- `str.startswith(prefix)` → bool
- `str.endswith(suffix)` → bool
- `str.isdigit()`, `str.isalpha()`, `str.isalnum()` → bool

*Transformación:*
- `str.upper()`, `str.lower()`, `str.capitalize()` → str
- `str.title()`, `str.swapcase()` → str
- `str.strip()`, `str.lstrip()`, `str.rstrip()` → str
- `str.replace(old, new)` → str

*División y Unión:*
- `str.split(sep)` → list
- `str.join(iterable)` → str
- `str.splitlines()` → list

*Formato:*
- `str.format()` → str
- `str.center(width)`, `str.ljust(width)`, `str.rjust(width)` → str
- `str.zfill(width)` → str

**C.3 Listas (list) - Referencia Completa**
- Todos los métodos con ejemplos
- Patrones de uso común

**C.4 Diccionarios (dict) - Referencia Completa**
- Métodos avanzados
- Patrones de uso común

**C.5 Módulos Útiles**
- `math`: funciones matemáticas
- `random`: números aleatorios
- `datetime`: fechas y horas
- `os`: interacción con sistema operativo
- `sys`: parámetros del sistema
- `json`: trabajar con JSON
- `re`: expresiones regulares

**Ejercicios:**
- Manipulación avanzada de cadenas
- Uso de módulos estándar
- Procesamiento de archivos JSON

---

### Parte IV: Estilo y Buenas Prácticas

#### [D. Guía de Estilo](D_estilo.md)

Pautas para escribir código limpio y profesional basadas en PEP 8.

**Secciones:**

**D.1 Introducción**
- ¿Por qué importa el estilo?
- PEP 8: la guía oficial de Python
- ¿Entra en el examen?
- Apertura a sugerencias y debate

**D.2 Principios Clave**
- "El código se lee más veces de las que se escribe"
- Consistencia
- Simplicidad sobre complejidad

**D.3 Las Reglas**

**Regla {ref}`0x0000h`:** La claridad y legibilidad son de máxima importancia
- Código autodocumentado
- Evitar "cleverness" innecesaria

**Regla {ref}`0x0001h`:** Los identificadores deben ser descriptivos
- Nombres de variables: `snake_case`
- Nombres de funciones: `verbo_sustantivo()`
- Nombres de constantes: `MAYUSCULAS_CON_GUION`
- Nombres de clases: `PascalCase`

**Otras reglas incluyen:**
- Espaciado y indentación (4 espacios)
- Líneas en blanco para separar secciones
- Longitud de línea (máximo 79-100 caracteres)
- Importaciones al inicio del archivo
- Comentarios útiles (no obvios)
- Orden de importaciones
- Manejo de espacios en operadores
- Evitar comparaciones booleanas redundantes

**Ejemplos de Código:**
- ❌ Incorrecto vs ✅ Correcto en cada regla

**Herramientas:**
- `pylint`: analizador de código
- `black`: formateador automático
- `flake8`: verificador de estilo

---

### Parte V: Herramientas y Evaluación

#### [E. Introducción a JupyterLab](E_jupyterlab.md)

Guía práctica para usar JupyterLab en el curso.

**Contenido:**
- Accediendo a JupyterLab
  - Paso 1: Abrir navegador
  - Paso 2: Ingresar URL
  - Paso 3: Esperar carga inicial

- La interfaz de JupyterLab:
  - Barra de menú superior
  - Panel lateral izquierdo (File Browser)
  - Área de trabajo central

- Trabajar con Notebooks:
  - Crear nuevo notebook
  - Tipos de celdas: Code y Markdown
  - Ejecutar celdas: `Shift+Enter`
  - Atajos de teclado útiles

- Funciones básicas:
  - Guardar trabajo
  - Descargar notebooks
  - Subir archivos
  - Organizar en carpetas

- Tips y trucos:
  - Autocompletado con `Tab`
  - Ayuda con `?`
  - Reiniciar kernel

---

#### [F. Rúbrica de Evaluación](F_rubrica.md)

Sistema de evaluación por niveles para entregas de código.

**Secciones:**

**F.1 Filosofía de Evaluación**
- Evaluación formativa vs sumativa
- Aprender de los errores

**F.2 Dimensiones de Evaluación**

1. **Corrección Funcional (40%)**
   - ¿El programa hace lo que debe hacer?
   - Manejo de casos de borde
   - Ausencia de errores en ejecución

2. **Legibilidad y Estilo (30%)**
   - Nombres descriptivos
   - Comentarios útiles
   - Formato consistente
   - Adherencia a PEP 8

3. **Diseño y Estructura (20%)**
   - Uso apropiado de funciones
   - Estructuras de datos adecuadas
   - Lógica clara y organizada
   - Modularidad

4. **Apropiación de Herramientas (10%)**
   - Uso efectivo de características de Python
   - Aprovechamiento de funciones built-in
   - Conocimiento de la biblioteca estándar

**F.3 Niveles de Evaluación**

- **{ref}`nivel-10` - Excelencia (100 puntos)**
  - Todas las dimensiones sobresalientes
  - Código profesional

- **Nivel 9 - Muy Bueno (90 puntos)**
  - Funciona perfectamente
  - Estilo consistente con mínimas observaciones

- **Nivel 8 - Bueno (80 puntos)**
  - Funciona correctamente
  - Algunas mejoras de estilo

- **Nivel 7 - Satisfactorio (70 puntos)**
  - Funciona en casos principales
  - Estilo básico presente

- **Nivel 6 - Suficiente (60 puntos)**
  - Funciona con errores menores
  - Estilo inconsistente

- **Nivel 5 o menos - Insuficiente (<60 puntos)**
  - No funciona o errores graves
  - Falta de estilo o estructura

**F.4 Ejemplos por Nivel**
- Código comentado para cada nivel
- Qué se espera en cada categoría

---

#### [Z. Uso Responsable de IA](Z_ia.md)

Guía para usar herramientas de IA de forma ética y efectiva.

**Secciones:**

**Z.1 Filosofía de Uso**
- La IA como herramienta de aprendizaje, no de reemplazo
- Principios fundamentales:
  - Entender antes de usar
  - Citar y dar crédito
  - Verificar y validar
  - Aprender del proceso

**Z.2 Cuándo Usar IA**

✅ **Usos Apropiados:**
- Explicar conceptos que no entendés
- Sugerir enfoques alternativos
- Depurar errores después de intentar vos mismo
- Generar casos de prueba
- Aprender sintaxis nueva
- Revisar y mejorar código propio

❌ **Usos Inapropiados:**
- Copiar código directamente sin entender
- Generar código de exámenes o evaluaciones individuales
- Evitar el proceso de aprendizaje
- Usar sin verificar
- Presentar código IA como propio sin comprensión

**Z.3 Técnicas de Prompting Efectivo**
- Estructura de un buen prompt:
  - Contexto
  - Tarea específica
  - Restricciones
  - Formato esperado

- Técnicas avanzadas:
  - Prompting iterativo
  - Chain-of-thought prompting
  - Few-shot learning
  - Pedir explicaciones paso a paso

**Z.4 Verificación y Aprendizaje**
- Cómo validar código generado por IA
- Hacer preguntas críticas
- Experimentar con modificaciones
- Entender cada línea

**Z.5 Ética y Citación**
- Dar crédito cuando corresponde
- Transparencia con docentes
- Integridad académica

**Ejemplos:**
- Prompts efectivos vs inefectivos
- Cómo iterar y mejorar prompts
- Depuración asistida por IA

---

## 🎯 Recursos Adicionales

### Ejercicios Prácticos

Los ejercicios están organizados en Jupyter Notebooks en la carpeta `cuadernos/`:

- `1_fundamentos.ipynb` - Ejercicios de variables, tipos y operadores
- `2_control_flujo.ipynb` - Ejercicios de if, while, for
- `3_estructuras.ipynb` - Ejercicios de listas, tuplas, sets, diccionarios
- `4_funciones.ipynb` - Ejercicios de funciones y recursión
- `B_excepciones.ipynb` - Ejercicios de manejo de excepciones

### Banco de Ejercicios

`enunciados.md` contiene 50 ejercicios adicionales organizados por:
- **Nivel:** Básico, Intermedio, Avanzado
- **Habilidades:** Slicing, manipulación de listas, lazos, funciones, etc.
- Cada ejercicio incluye una sección de ayuda colapsada

### Guías Técnicas

- `GEMINI.md` - Directivas para el CLI de Gemini (generación de contenido)
- `manual_myst/` - Guía de sintaxis MyST Markdown
- `manual_mermaid/` - Guía para crear diagramas

---

## 🗺️ Cómo Navegar Este Apunte

### Por Nivel de Dificultad

**🌱 Principiante Absoluto:**
1. Empezá por {ref}`primeros-pasos-algoritmos`
2. Seguí con {ref}`primer-programa`
3. Aprendé {ref}`variables` y tipos de datos
4. Practicá con ejercicios de `1_fundamentos.ipynb`

**🌿 Nivel Básico:**
1. Dominá {ref}`control-flujo` (if, while, for)
2. Entendé {ref}`estructuras-datos` (listas y diccionarios)
3. Practicá con ejercicios de nivel básico

**🌳 Nivel Intermedio:**
1. Profundizá en {ref}`funciones`
2. Aprendé {ref}`excepciones-capitulo`
3. Consultá {ref}`referencia-tipos` para técnicas avanzadas
4. Trabajá ejercicios de nivel intermedio y avanzado

**🎓 Nivel Avanzado:**
1. Estudiá diseño modular y buenas prácticas
2. Seguí {ref}`0x0000h` y la guía de estilo completa
3. Revisá la {ref}`nivel-10` para código profesional
4. Implementá proyectos complejos

### Por Tema de Interés

**🔢 Matemáticas y Cálculos:**
- Operadores aritméticos en {ref}`fundamentos`
- Módulo `math` en {ref}`referencia-tipos`
- Funciones matemáticas en {ref}`funciones`

**📝 Procesamiento de Texto:**
- Cadenas en {ref}`fundamentos`
- {ref}`referencia-str` - Métodos de cadenas
- F-strings en A_fstrings.md
- Expresiones regulares en módulo `re`

**📊 Análisis de Datos:**
- Listas y diccionarios en {ref}`estructuras-datos`
- Patrones de procesamiento
- Funciones de agregación

**🎮 Programas Interactivos:**
- `input()` y validación
- Lazos con {ref}`control-flujo`
- Menús con match-case
- {ref}`excepciones-capitulo` para robustez

### Por Necesidad Específica

**❓ "¿Cómo hago para...?"**

- **...leer datos del usuario?** → Ver `input()` en {ref}`fundamentos`
- **...repetir código?** → Ver lazos en {ref}`control-flujo`
- **...almacenar múltiples valores?** → Ver listas en {ref}`estructuras-datos`
- **...organizar código?** → Ver {ref}`funciones`
- **...manejar errores?** → Ver {ref}`excepciones-capitulo`
- **...buscar un método específico?** → Consultá {ref}`referencia-tipos`

**🐛 "Tengo un error..."**

- **`SyntaxError`** → Revisá indentación y sintaxis básica
- **`NameError`** → Variable no definida, revisá nombres
- **`TypeError`** → Tipos incompatibles, revisá conversiones
- **`IndexError`** → Índice fuera de rango, revisá límites
- **`KeyError`** → Clave no existe, usá `.get()` en diccionarios
- **Más errores** → Consultá {ref}`que-son-excepciones`

**✨ "Quiero mejorar mi código"**

1. Revisá {ref}`0x0000h` y siguientes reglas de estilo
2. Consultá la {ref}`nivel-10` de excelencia
3. Usá funciones para modularizar
4. Agregá docstrings y comentarios útiles
5. Manejá excepciones apropiadamente

---

## 🔍 Referencias Rápidas

### Operadores Más Usados

```python
# Aritméticos
+    # Suma
-    # Resta
*    # Multiplicación
/    # División (float)
//   # División entera
%    # Módulo (resto)
**   # Potencia

# Comparación
==   # Igual a
!=   # Distinto de
<    # Menor que
>    # Mayor que
<=   # Menor o igual
>=   # Mayor o igual

# Lógicos
and  # Y lógico
or   # O lógico
not  # Negación

# Pertenencia
in       # Está en
not in   # No está en
```

### Métodos Más Usados

```python
# Listas
lista.append(x)       # Agregar al final
lista.insert(i, x)    # Insertar en posición
lista.remove(x)       # Eliminar elemento
lista.pop(i)          # Eliminar y retornar
lista.sort()          # Ordenar
lista.reverse()       # Invertir
len(lista)            # Longitud

# Diccionarios
dict.keys()           # Todas las claves
dict.values()         # Todos los valores
dict.items()          # Pares clave-valor
dict.get(k, default)  # Obtener con default
dict.update(otro)     # Actualizar/agregar

# Cadenas
str.upper()           # A mayúsculas
str.lower()           # A minúsculas
str.strip()           # Quitar espacios
str.split(sep)        # Dividir en lista
str.replace(old, new) # Reemplazar
str.find(sub)         # Buscar posición
str.startswith(prefix)# ¿Empieza con?
str.endswith(suffix)  # ¿Termina con?
```

### Funciones Built-in Esenciales

```python
print()      # Mostrar en consola
input()      # Leer del usuario
len()        # Longitud
type()       # Tipo de dato
int()        # Convertir a entero
float()      # Convertir a decimal
str()        # Convertir a cadena
range()      # Generar secuencia
enumerate()  # Índice y valor
zip()        # Combinar iterables
map()        # Aplicar función
filter()     # Filtrar elementos
sorted()     # Ordenar (retorna nueva)
sum()        # Sumar elementos
min()        # Mínimo
max()        # Máximo
abs()        # Valor absoluto
round()      # Redondear
```

---

## 📖 Convenciones de Este Apunte

### Iconos y Símbolos

- 🐍 Python
- ✅ Correcto / Buena práctica
- ❌ Incorrecto / Mala práctica
- ⚠️ Advertencia importante
- 💡 Tip o sugerencia
- 🔍 Para explorar más
- 🎯 Objetivo de aprendizaje
- 📝 Ejercicio
- 🐛 Debugging / Errores comunes

### Bloques de Contenido

::::{note}
**Nota:** Información complementaria o aclaración.
::::

::::{tip}
**Consejo:** Sugerencia práctica para aplicar mejor.
::::

::::{important}
**Importante:** Concepto clave que no podés perderte.
::::

::::{warning}
**Advertencia:** Algo que puede causar errores o confusión.
::::

::::{danger}
**Peligro:** Error grave o problema serio a evitar.
::::

### Referencias Cruzadas

Las referencias con `{ref}` son enlaces clicables a secciones específicas:
- `{ref}primer-programa` → Enlace a "Tu Primer Programa"
- `{ref}control-flujo` → Enlace a "Control de Flujo"
- `{ref}0x0000h` → Enlace a regla de estilo específica

---

## 🎓 Ruta de Aprendizaje Sugerida

### Semana 1-2: Fundamentos
- [ ] Completar {ref}`primeros-pasos-algoritmos`
- [ ] Leer {ref}`fundamentos` completo
- [ ] Practicar con `1_fundamentos.ipynb`
- [ ] Entender variables, tipos y operadores

### Semana 3-4: Control de Flujo
- [ ] Estudiar {ref}`control-flujo`
- [ ] Dominar if-else y lazos while
- [ ] Practicar con `2_control_flujo.ipynb`
- [ ] Implementar validaciones y menús

### Semana 5-6: Estructuras de Datos
- [ ] Aprender {ref}`estructuras-datos`
- [ ] Practicar listas y diccionarios intensivamente
- [ ] Completar `3_estructuras.ipynb`
- [ ] Resolver ejercicios de nivel intermedio

### Semana 7-8: Funciones y Modularidad
- [ ] Estudiar {ref}`funciones`
- [ ] Practicar con `4_funciones.ipynb`
- [ ] Refactorizar código anterior usando funciones
- [ ] Aprender recursión básica

### Semana 9-10: Robustez y Estilo
- [ ] Aprender {ref}`excepciones-capitulo`
- [ ] Estudiar guía de estilo {ref}`0x0000h`
- [ ] Completar `B_excepciones.ipynb`
- [ ] Revisar y mejorar código anterior

### Semana 11-12: Consolidación
- [ ] Consultar {ref}`referencia-tipos` según necesidad
- [ ] Resolver ejercicios avanzados
- [ ] Implementar proyecto integrador
- [ ] Revisar contra {ref}`nivel-10`

---

## 🤝 Cómo Usar Este Índice

1. **Búsqueda rápida:** Usá `Ctrl+F` (o `Cmd+F`) para buscar términos específicos
2. **Navegación por enlaces:** Hacé click en los enlaces para ir directamente a las secciones
3. **Marcadores:** Guardá este índice en favoritos para acceso rápido
4. **Referencias cruzadas:** Los enlaces `{ref}` te llevan a secciones específicas con contexto

---

## 📚 Glosario Rápido

**Algoritmo:** Secuencia de pasos para resolver un problema

**Variable:** Espacio en memoria para almacenar un valor

**Tipo de dato:** Categoría de valor (int, float, str, bool)

**Función:** Bloque de código reutilizable

**Parámetro:** Variable en la definición de función

**Argumento:** Valor pasado al llamar función

**Retorno:** Valor que devuelve una función

**Lazo (bucle):** Estructura para repetir código

**Iteración:** Una ejecución del lazo

**Lista:** Colección ordenada y mutable

**Tupla:** Colección ordenada e inmutable

**Conjunto (set):** Colección sin orden ni duplicados

**Diccionario:** Colección de pares clave-valor

**Excepción:** Error que ocurre durante ejecución

**Módulo:** Archivo Python con código reutilizable

**Scope:** Ámbito donde una variable es accesible

**Inmutable:** No se puede modificar después de crearse

**Iterable:** Objeto que se puede recorrer (lista, tupla, str)

---

## 💬 Retroalimentación

Este apunte es un documento vivo que se mejora continuamente. Si encontrás:
- Errores o inconsistencias
- Secciones poco claras
- Temas que faltan
- Sugerencias de mejora

No dudes en consultar con tu docente o contribuir mediante issues en el repositorio.

---

**Última actualización:** 2026-01-26

**Versión:** 1.0

**Autores:** Equipo docente del Curso de Introducción a la Programación

---

