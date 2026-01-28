---
title: Guía de Markdown Básico
short_title: G - Markdown
subtitle: Aprende a dar formato a tus celdas en Jupyter
---

# Guía de Markdown Básico para Jupyter

## Introducción

Cuando trabajás en un cuaderno de Jupyter, hay dos tipos de celdas principales:

1. **Celdas de código**: Donde escribís Python y lo ejecutás
2. **Celdas Markdown**: Donde escribís texto con formato para documentar tu trabajo

Esta guía te enseña a usar **Markdown**, un lenguaje de formato de texto súper simple que te permite crear documentos con títulos, listas, énfasis, enlaces y más, todo escribiendo texto plano.

:::{tip} ¿Por qué aprender Markdown?
- 📝 **Documentá tu código**: Explicá qué hace cada parte de tu programa
- 📚 **Organizá tu trabajo**: Dividí tu notebook en secciones claras
- 🎨 **Mejorá la presentación**: Hacé que tus entregas se vean profesionales
- 🚀 **Habilidad transferible**: Markdown se usa en GitHub, foros, documentación técnica, etc.
:::

:::{note} Recordatorio
Para crear una celda Markdown en Jupyter:
1. Seleccioná una celda
2. Presioná `M` (o elegí "Markdown" en el menú desplegable)
3. Escribí tu contenido usando la sintaxis que veremos
4. Presioná `Shift+Enter` para renderizar (mostrar con formato)
:::

---

## 1. Títulos y Subtítulos

Los títulos se crean usando el símbolo `#` (numeral). Cuantos más `#` uses, más pequeño es el título.

### Sintaxis

```markdown
# Título Principal (nivel 1)
## Título de Sección (nivel 2)
### Subsección (nivel 3)
#### Título menor (nivel 4)
##### Aún más chico (nivel 5)
###### El más pequeño (nivel 6)
```

### Resultado

Se verá así (simulado con tamaño de fuente):

<div style="font-size: 2em; font-weight: bold;">Título Principal (nivel 1)</div>
<div style="font-size: 1.5em; font-weight: bold;">Título de Sección (nivel 2)</div>
<div style="font-size: 1.25em; font-weight: bold;">Subsección (nivel 3)</div>

### Ejemplo práctico en tu notebook

```markdown
# Trabajo Práctico 1: Variables y Operadores

## Ejercicio 1: Suma de números

En este ejercicio vamos a sumar dos números ingresados por el usuario.

### Solución

[...tu código aquí...]
```

:::{important} Buena práctica
- Usá **un solo** `#` (título nivel 1) por notebook (generalmente al inicio)
- Usá `##` para cada ejercicio o sección principal
- Usá `###` para subsecciones dentro de un ejercicio
:::

---

## 2. Énfasis: Negrita y Cursiva

Podés resaltar palabras o frases usando asteriscos `*` o guiones bajos `_`.

### Sintaxis

```markdown
*texto en cursiva* o _texto en cursiva_

**texto en negrita** o __texto en negrita__

***texto en negrita y cursiva*** o ___texto en negrita y cursiva___
```

### Resultado

*texto en cursiva*

**texto en negrita**

***texto en negrita y cursiva***

### Cuándo usar cada uno

- **Negrita**: Para términos importantes, palabras clave, advertencias
  - Ejemplo: "La variable **debe** ser un entero positivo"
- *Cursiva*: Para énfasis suave, términos técnicos en inglés, nombres de variables
  - Ejemplo: "Guardamos el resultado en la variable *suma_total*"

### Ejemplo práctico

```markdown
**Importante:** La función `input()` siempre retorna un *string*.
Por eso **debemos** convertirlo con `int()` o `float()`.
```

---

## 3. Listas

Las listas te ayudan a organizar información de forma clara.

### Listas sin orden (viñetas)

Usá `-`, `*` o `+` al inicio de cada línea:

```markdown
- Primer elemento
- Segundo elemento
- Tercer elemento

* También funciona con asterisco
* Otro elemento

+ Y con el signo más
+ Último elemento
```

**Resultado:**

- Primer elemento
- Segundo elemento
- Tercer elemento

### Listas numeradas (ordenadas)

Usá números seguidos de un punto:

```markdown
1. Primera instrucción
2. Segunda instrucción
3. Tercera instrucción
```

**Resultado:**

1. Primera instrucción
2. Segunda instrucción
3. Tercera instrucción

:::{tip} Truco para listas numeradas
No importa qué números uses, Markdown los ordena automáticamente:

```markdown
1. Primer elemento
1. Segundo elemento (escribí 1, pero se muestra como 2)
1. Tercer elemento (escribí 1, pero se muestra como 3)
```

Esto es útil cuando agregás o quitás elementos: no tenés que renumerar todo.
:::

### Listas anidadas (con subcategorías)

Indentá (agregá espacios) para crear subniveles:

```markdown
- Estructuras de datos
  - Listas
    - Mutables
    - Ordenadas
  - Tuplas
    - Inmutables
    - Ordenadas
  - Diccionarios
    - Pares clave-valor
```

**Resultado:**

- Estructuras de datos
  - Listas
    - Mutables
    - Ordenadas
  - Tuplas
    - Inmutables
    - Ordenadas
  - Diccionarios
    - Pares clave-valor

### Ejemplo práctico

```markdown
## Pasos para resolver el ejercicio:

1. Leer el enunciado completo
2. Identificar:
   - Datos de entrada
   - Datos de salida
   - Restricciones
3. Diseñar el algoritmo
4. Implementar en Python
5. Probar con casos de ejemplo
```

---

## 4. Código

Hay dos formas de mostrar código en Markdown: en línea y en bloques.

### Código en línea

Para mencionar código dentro de una oración, rodealo con backticks (`` ` ``):

```markdown
La función `print()` muestra texto en pantalla.
Para leer datos usamos `input()`.
Recordá que `edad >= 18` es una comparación, no una asignación.
```

**Resultado:**

La función `print()` muestra texto en pantalla.
Para leer datos usamos `input()`.
Recordá que `edad >= 18` es una comparación, no una asignación.

:::{note} ¿Dónde está el backtick?
El backtick (`` ` ``) NO es la comilla simple (`'`). En teclados latinoamericanos suele estar:
- Junto a la tecla `P` (necesitás presionar dos veces)
- O con `AltGr + }` y luego `Espacio`
:::

### Bloques de código

Para fragmentos más largos, usá tres backticks antes y después:

````markdown
```python
def suma(a, b):
    """Suma dos números y retorna el resultado."""
    return a + b

resultado = suma(5, 3)
print(f"La suma es: {resultado}")
```
````

**Resultado:**

```python
def suma(a, b):
    """Suma dos números y retorna el resultado."""
    return a + b

resultado = suma(5, 3)
print(f"La suma es: {resultado}")
```

:::{tip} Especificar el lenguaje
Escribir `python` después de los tres backticks iniciales activa el resaltado de sintaxis (colores).
Otros lenguajes comunes: `javascript`, `java`, `c`, `bash`, `sql`
:::

### Ejemplo práctico

```markdown
## Solución Ejercicio 3

Para calcular el área de un círculo usamos la fórmula A = πr².

En Python, podemos importar `math.pi` para obtener el valor de π:

```python
import math

radio = float(input("Ingresá el radio: "))
area = math.pi * radio ** 2
print(f"El área es: {area:.2f}")
```

El método `.2f` en el f-string redondea a 2 decimales.
```

---

## 5. Enlaces (Links)

Creá enlaces a páginas web o recursos externos.

### Sintaxis

```markdown
[texto visible](URL)
```

### Ejemplos

```markdown
[Documentación oficial de Python](https://docs.python.org/es/3/)

[Descargar Python](https://www.python.org/downloads/)

Visitá [Google](https://www.google.com) para buscar más información.
```

**Resultado:**

[Documentación oficial de Python](https://docs.python.org/es/3/)

Visitá [Google](https://www.google.com) para buscar más información.

### Enlaces útiles para tu notebook

```markdown
## Referencias

- [Tutorial oficial de Python](https://docs.python.org/es/3/tutorial/)
- [Stack Overflow](https://stackoverflow.com) - Para buscar soluciones a errores
- [PEP 8 - Guía de estilo](https://peps.python.org/pep-0008/)
```

---

## 6. Imágenes

Similar a los enlaces, pero con un signo de exclamación `!` al inicio.

### Sintaxis

```markdown
![texto alternativo](URL_de_la_imagen)
```

### Ejemplo

```markdown
![Logo de Python](https://www.python.org/static/community_logos/python-logo.png)
```

:::{note} Texto alternativo
El "texto alternativo" se muestra si la imagen no carga, y es importante para accesibilidad.
:::

### Imágenes locales

Si tenés una imagen guardada en tu carpeta:

```markdown
![Diagrama de flujo](./imagenes/diagrama_ejercicio1.png)
```

---

## 7. Citas (Blockquotes)

Usá el símbolo `>` al inicio de la línea para crear una cita.

### Sintaxis

```markdown
> Esto es una cita.
> Puede tener múltiples líneas.

> "La simplicidad es la máxima sofisticación." - Leonardo da Vinci
```

**Resultado:**

> Esto es una cita.
> Puede tener múltiples líneas.

> "La simplicidad es la máxima sofisticación." - Leonardo da Vinci

### Ejemplo práctico

```markdown
> **Recordatorio importante:** Siempre validá la entrada del usuario antes de procesarla.
> Un programa robusto anticipa errores y los maneja apropiadamente.
```

---

## 8. Líneas horizontales

Creá separadores visuales con tres o más guiones, asteriscos o guiones bajos:

```markdown
---

***

___
```

Todos producen el mismo resultado: una línea horizontal:

---

### Ejemplo de uso

```markdown
## Ejercicio 1: Suma
[código del ejercicio 1]

---

## Ejercicio 2: Promedio
[código del ejercicio 2]
```

---

## 9. Tablas

Las tablas organizan datos en filas y columnas.

### Sintaxis básica

```markdown
| Columna 1 | Columna 2 | Columna 3 |
|-----------|-----------|-----------|
| Dato 1    | Dato 2    | Dato 3    |
| Dato 4    | Dato 5    | Dato 6    |
```

**Resultado:**

| Columna 1 | Columna 2 | Columna 3 |
|-----------|-----------|-----------|
| Dato 1    | Dato 2    | Dato 3    |
| Dato 4    | Dato 5    | Dato 6    |

### Alineación de columnas

Podés controlar la alineación con dos puntos `:`:

```markdown
| Izquierda | Centro  | Derecha |
|:----------|:-------:|--------:|
| Texto     | Texto   | Texto   |
| Más       | Texto   | Aquí    |
```

**Resultado:**

| Izquierda | Centro  | Derecha |
|:----------|:-------:|--------:|
| Texto     | Texto   | Texto   |
| Más       | Texto   | Aquí    |

### Ejemplo práctico: Comparación de tipos de datos

```markdown
| Tipo      | Mutable | Ordenado | Duplicados | Ejemplo              |
|-----------|:-------:|:--------:|:----------:|----------------------|
| Lista     | ✓       | ✓        | ✓          | `[1, 2, 3]`         |
| Tupla     | ✗       | ✓        | ✓          | `(1, 2, 3)`         |
| Set       | ✓       | ✗        | ✗          | `{1, 2, 3}`         |
| Dict      | ✓       | ✓*       | ✗ (claves) | `{"a": 1, "b": 2}` |
```

---

## 10. Escapar caracteres especiales

Si necesitás mostrar un carácter que Markdown usa para formato, precedelo con `\`:

```markdown
\* Esto NO es una viñeta porque escapé el asterisco

Para mostrar el símbolo \# sin crear un título, escapalo.

Los backticks se escapan así: \`print()\`
```

**Resultado:**

\* Esto NO es una viñeta porque escapé el asterisco

Para mostrar el símbolo \# sin crear un título, escapalo.

---

## Plantilla de Notebook Bien Documentado

Acá tenés un ejemplo completo de cómo estructurar un notebook con buen uso de Markdown:

````markdown
# Trabajo Práctico 2: Control de Flujo

**Alumno:** Juan Pérez  
**Fecha:** 27 de enero de 2026  
**Curso:** Introducción a la Programación

---

## Índice

1. [Ejercicio 1: Validación de edad](#ejercicio-1)
2. [Ejercicio 2: Tabla de multiplicar](#ejercicio-2)
3. [Ejercicio 3: Números primos](#ejercicio-3)

---

## Ejercicio 1: Validación de edad

### Enunciado

Escribir un programa que solicite la edad del usuario y determine si es:
- Menor de edad (< 18)
- Adulto (18-64)
- Adulto mayor (≥ 65)

### Análisis

**Entrada:** Un número entero (edad)  
**Salida:** Mensaje indicando la categoría  
**Restricciones:** La edad debe ser un número positivo

### Solución

```python
# Solicitar edad al usuario
edad = int(input("Ingresá tu edad: "))

# Validar entrada
if edad < 0:
    print("Error: La edad no puede ser negativa")
elif edad < 18:
    print("Sos menor de edad")
elif edad < 65:
    print("Sos adulto")
else:
    print("Sos adulto mayor")
```

### Pruebas

Probé el programa con los siguientes casos:

| Entrada | Salida esperada      | ¿Funciona? |
|---------|----------------------|:----------:|
| 15      | "Sos menor de edad"  | ✓          |
| 30      | "Sos adulto"         | ✓          |
| 70      | "Sos adulto mayor"   | ✓          |
| -5      | "Error: ..."         | ✓          |

### Reflexión

> **Aprendizaje:** Es importante validar la entrada del usuario para evitar errores.
> En este caso, chequeo que la edad no sea negativa.

---

## Ejercicio 2: Tabla de multiplicar

[... y así sucesivamente ...]

---

## Referencias

- [Apunte del curso](enlace)
- [Documentación de Python](https://docs.python.org/es/3/)
````

---

## Consejos para Usar Markdown en tus Notebooks

### ✅ Buenas prácticas

1. **Documentá mientras escribís**: No dejes la documentación para el final
2. **Sé claro y conciso**: No escribas párrafos gigantes, usá listas
3. **Usá títulos consistentemente**: Mantené una jerarquía lógica (no saltees niveles)
4. **Incluí tu razonamiento**: Explicá *por qué* elegiste una solución, no solo el código
5. **Probá el formato**: Ejecutá la celda Markdown (`Shift+Enter`) para ver cómo queda

### ❌ Errores comunes

1. **Olvidar espacios**: Después del `#` o `-` debe haber un espacio
   ```markdown
   # Título correcto
   #Título incorrecto (falta espacio)
   
   - Lista correcta
   -Lista incorrecta (falta espacio)
   ```

2. **Mezclar código con markdown**: Si querés mostrar código, usá los backticks
   ```markdown
   ❌ Usá la función print() para mostrar texto
   ✓ Usá la función `print()` para mostrar texto
   ```

3. **No dejar líneas en blanco**: Entre elementos diferentes, dejá una línea vacía
   ```markdown
   ## Título
   
   Párrafo de texto.
   
   - Lista
   - De elementos
   ```

4. **Abusar del formato**: No uses negrita y cursiva en todo
   ```markdown
   ❌ **La *función* `print()` es *muy* importante y la *usamos* para *mostrar***
   ✓ La función `print()` muestra texto en pantalla.
   ```

---

## Atajos de Teclado Útiles en Jupyter

Mientras trabajás con celdas Markdown:

| Atajo             | Acción                                    |
|-------------------|-------------------------------------------|
| `M`               | Convertir celda a Markdown                |
| `Y`               | Convertir celda a Code (Python)           |
| `Shift + Enter`   | Ejecutar celda y pasar a la siguiente     |
| `Ctrl + Enter`    | Ejecutar celda y quedarse en ella         |
| `A`               | Insertar celda arriba (*above*)           |
| `B`               | Insertar celda abajo (*below*)            |
| `DD`              | Eliminar celda (presionar D dos veces)    |
| `Z`               | Deshacer eliminación de celda             |
| `Enter`           | Entrar en modo edición                    |
| `Esc`             | Salir del modo edición                    |

---

## Recursos Adicionales

### Para practicar

- **[Markdown Tutorial](https://www.markdowntutorial.com/)**: Tutorial interactivo (en inglés)
- **[Dillinger](https://dillinger.io/)**: Editor online para practicar Markdown
- **[CommonMark](https://commonmark.org/help/)**: Referencia rápida en 60 segundos

### Hojas de referencia (Cheat Sheets)

Guardá estos enlaces para consulta rápida:

- [Markdown Cheatsheet by Adam Pritchard](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Markdown Guide - Basic Syntax](https://www.markdownguide.org/basic-syntax/)

---

## Ejercicio de Práctica

Creá una nueva celda Markdown en tu notebook y reproducí lo siguiente:

```markdown
# Mi Primera Celda Markdown

## Sobre mí

Hola, me llamo **[Tu Nombre]** y estoy aprendiendo *Python*.

### Mis objetivos en este curso

1. Aprender los fundamentos de programación
2. Crear mis propios programas
3. Resolver problemas con código

---

### Lo que aprendí hoy

- Markdown básico
- Títulos con `#`
- Listas con `-` o números
- Código con `` `backticks` ``

> "El código es como el humor. Cuando lo tenés que explicar, es malo." - Cory House

**Próximos pasos:** Seguir practicando y documentando mis programas.
```

---

## Conclusión

Markdown es una herramienta poderosa y simple para documentar tu trabajo. Con lo que aprendiste en esta guía ya podés:

✓ Organizar tus notebooks con títulos y secciones  
✓ Destacar información importante con negrita y cursiva  
✓ Crear listas para estructurar ideas  
✓ Mostrar código de forma clara  
✓ Agregar enlaces y referencias  
✓ Crear tablas para comparar datos  

:::{tip} Práctica constante
La mejor forma de dominar Markdown es usarlo regularmente. Empezá documentando cada ejercicio que hagas, y pronto se convertirá en algo natural.
:::

---

**¡Ahora te toca a vos!** Abrí un notebook de Jupyter, creá una celda Markdown, y empezá a practicar. 🚀
