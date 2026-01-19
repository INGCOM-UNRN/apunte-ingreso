# 🐍 Apunte de Ingreso - Ingeniería en Computación

Bienvenidos a este apunte creado para el Curso de Ingreso a la carrera de Ingeniería en Computación. Este material introduce la programación desde cero utilizando Python como lenguaje de enseñanza.

## Contenido del material (y curso)

### [Capítulo 0: Introducción a la Programación](./00_primeros_pasos.md)

- Concepto de algoritmo (secuencia de pasos precisos)
- Las 5 preguntas mágicas (método sistemático de análisis)
- Diagramas de flujo (símbolos estándar, reglas de construcción)
- Pseudocódigo (sintaxis estructurada con delimitadores explícitos)
- Pruebas de escritorio (validación manual con casos de prueba)
- Traducción a Python (del diseño a la implementación)

### [Capítulo 1: Fundamentos de Python](./1_fundamentos.md) 

- Variables y nombres
- Tipos de datos (`int`, `float`, `str`, `bool`) con conversiones
- Operadores (aritméticos, comparación, lógicos) con precedencia
- Entrada/salida (`input` y `print`)
- Conversión de tipos (casting explícito e implícito)

### [Capítulo 2: Control de Flujo](2_control_flujo.md)

- Estructuras condicionales (`if`, `elif`, `else`) con diagramas
- Operador ternario (expresiones condicionales)
- Bucles `while` y `for` con visualizaciones
- Control de bucles (`break`, `continue`, `pass`)

### [Capítulo 3: Estructuras de Datos](./3_estructuras.md)

- Listas (crear, modificar, métodos, slicing avanzado)
- Tuplas (inmutabilidad, unpacking múltiple)
- Diccionarios (CRUD completo, métodos, comprensiones)
- Sets (operaciones matemáticas, álgebra de conjuntos)
- Strings avanzados (métodos, formato, f-strings)
- Estructuras anidadas (listas de diccionarios, etc.)

### [Capítulo 4: Funciones](./4_funciones.md)

- Definir y llamar funciones
- Parámetros y argumentos
- Valores de retorno, `return` y `None`
- Scope (local y global) con diagramas
- Recursión (visualización del stack)
- Documentación (docstrings completos)

### [Capítulo 5: Método de Pólya](./0_como_pensar.md)

Guía sistemática para abordar problemas de programación basada en el método del matemático George Pólya. Presenta un marco de cuatro etapas (comprender, planificar, ejecutar y examinar) que estructura el pensamiento algorítmico y reduce errores conceptuales. Especialmente recomendado para quienes se inician en programación, ya que proporciona una metodología clara de resolución de problemas aplicable a cualquier desafío computacional.

Les recomendamos que lean este capítulo para ayudarlos a los problemas algorítmicos, pero las técnicas aplican también a matemática.

## Ejercicios

Siendo que la programación se aprende y desarrolla practicando, hemos creado un muy amplio repositorio de ejercicios, pueden acceder al [Gimnasio](./enunciados/gimnasio.md) para ver con que pueden desarrollar sus habilidades de programación.


## Material Adicional

Estos apéndices complementan el material principal del curso con profundizaciones y herramientas prácticas. Aunque no son estrictamente necesarios para aprobar, proporcionan conocimientos valiosos que mejorarán significativamente la calidad del código y la comprensión de buenas prácticas profesionales.

### [Apéndice A: F-Strings](./A_fstrings.md)

Guía completa sobre f-strings (formatted string literals), la forma moderna y elegante de trabajar con texto en Python desde la versión 3.6. Cubre desde sintaxis básica hasta formateo avanzado de números, alineación de texto, y expresiones complejas dentro de cadenas. Este apéndice enseña a crear mensajes claros y bien formateados, reemplazando técnicas antiguas de concatenación y `.format()` con una sintaxis más legible y eficiente.

### [Apéndice B: Excepciones](./B_excepciones.md)

Introducción al manejo profesional de errores en Python mediante excepciones. Explica cómo anticipar, capturar y gestionar errores de forma controlada usando bloques `try-except-finally`, mejorando la robustez y confiabilidad de los programas. Aunque no es fundamental para aprobar el curso de ingreso, dominar excepciones permite crear código más resiliente que maneja situaciones inesperadas sin fallar abruptamente.

### [Apéndice C: Módulos y Biblioteca Estándar](./C_modulos.md)

Referencia completa de los métodos más importantes para los cinco tipos de datos fundamentales en Python: strings (`str`), listas (`list`), diccionarios (`dict`), conjuntos (`set`) y tuplas (`tuple`). Funciona como manual de consulta rápida para operaciones comunes, explicando características como mutabilidad, métodos disponibles y casos de uso típicos. Esencial para escribir código idiomático aprovechando las herramientas integradas del lenguaje.

### [Apéndice D: Cuestiones de Estilo](./D_estilo.md)

Recopilación exhaustiva de reglas de estilo basadas en PEP 8 y buenas prácticas de la comunidad Python. Establece convenciones para nomenclatura, espaciado, estructura de código y documentación que hacen el código más legible y mantenible. Cada regla está numerada (formato 0x0000h) para facilitar referencias cruzadas y feedback. Aunque no se evalúan explícitamente en exámenes, aplicar estas reglas mejora significativamente la calidad profesional del código.

### [Apéndice E: JupyterLab](./E_jupyterlab.md)

Guía práctica de JupyterLab, el entorno de desarrollo interactivo utilizado en el curso para ejecutar código Python en el navegador. Explica conceptos básicos como celdas de código, ejecución interactiva, atajos de teclado y gestión de cuadernos (notebooks). Especialmente útil para estudiantes que nunca usaron entornos interactivos, proporciona las herramientas necesarias para aprovechar al máximo los ejercicios prácticos del curso.

### [Apéndice F: Rúbrica de Evaluación](./F_rubrica.md)

Sistema detallado de evaluación por niveles (0 a 10) para entregas de código práctico. Define criterios transparentes que balancean corrección funcional (40%), legibilidad (30%), diseño (20%) y apropiación de herramientas (10%). Incluye ejemplos concretos de código para cada nivel, penalizaciones por uso de características avanzadas no enseñadas, y checklist de autoevaluación. Fundamental para entender qué se espera en cada entrega y cómo mejorar sistemáticamente.

## ¿Cómo instalo Python?

Para el curso de ingreso, no es necesario instalar nada, solo tenés que visitar nuestro [JupyterLab](https://ingcom-unrn.github.io/jupyterlite/lab/index.html) que tiene todo listo para empezar a programar desde el navegador. También podés consultar la guía de uso en el [Apéndice E: JupyterLab](./E_jupyterlab.md).

Lo importante de usar esta herramienta, es que la misma puede funcionar en donde sea, incluyendo televisores inteligentes, telefonos y tablets, pero es fundamental contar con un teclado dedicado, ya que es necesario escribir el código.

## Sobre Asistentes de Código e IA Generativa

Estamos ante un cambio de paradigma en el desarrollo de software. No obstante, al igual que una calculadora no sustituye la comprensión aritmética, un LLM no reemplaza la lógica algorítmica. Deben dominar la programación para instruir a la IA con precisión técnica y evaluar críticamente el output recibido.

Una advertencia fundamental: el "copy-paste" indiscriminado de consignas genera una ilusión de competencia. Si la IA resuelve el problema por ustedes sin su supervisión activa, quien practica es el modelo, mientras que su capacidad de resolución de problemas se atrofia.

## ¿Necesitas Ayuda?

¡No te quedes con dudas! Programar es un desafío y preguntar es parte fundamental del aprendizaje.

### Canales de Consulta
- **En las Clases:** Pregunta directamente a docentes y ayudantes
- **Grupos de WhatsApp:** Consultas rápidas

### ¿Cómo Hacer una Buena Pregunta?
1. **Describe el problema:** ¿Qué intentás hacer?
2. **Mostrá tu código:** Comparte el fragmento relevante
3. **Explica el error:** ¿Qué mensaje aparece? Copialo
4. **Contá qué intentaste:** Qué soluciones probaste

**¡Preguntar bien es una habilidad profesional para desarrollar!** ¡Y todas las preguntas son válidas!.

## Consejos de Estudio

### HACER:
- 💻 Escribir código **todos los días** (aunque sea un ratito)
-  Cometer errores y **aprender de ellos**
- 🔄 Repetir conceptos difíciles
- 🤝 Explicar lo aprendido a alguien más
- 🛠️ Crear proyectos pequeños propios
- 📝 Tomar notas con tus propias palabras

### NO HACER:
- 📖 Leer sin ejecutar código
- 🏃 Saltar capítulos o secciones
- 📋 Copiar código sin entenderlo
- ⏩ Ir muy rápido sin practicar
- 😰 Frustrarse con los errores (son normales)

## 🎊 ¡Éxitos!

**Recordá qué:**

💡 *"El código no se aprende leyendo, se aprende escribiendo"*

🚀 **La práctica constante es la clave del éxito**

🤝 **Estamos acá para ayudarte**
