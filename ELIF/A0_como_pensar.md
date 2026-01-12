---
title: El Método Pólya (Versión Escolar)
short_title: 0 - Método Pólya
subtitle: Cómo resolver problemas sin volverse loco en el intento
---

(polya-escolar)=
# El Método Pólya para Resolver Problemas

¡Hola! 👋 ¿Alguna vez te quedaste trabado en un problema de matemáticas o de programación sin saber por dónde empezar? ¡No te preocupes! George Pólya, un profe de matemática muy groso, inventó un método de 4 pasos para resolver cualquier problema. Es como una receta de cocina, pero para el cerebro.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender una estrategia de 4 pasos (Entender, Planear, Hacer, Revisar) para resolver problemas difíciles sin desesperarte.
::::

---

## 1. Comprender el Problema: ¿De qué estamos hablando? 🤔

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Antes de intentar resolver nada, asegurate de entender bien qué te están pidiendo.

**Analogía:** Imaginate que un amigo te pide que le compres "eso que le gusta" en el kiosco. Si vas y comprás caramelos, pero él quería papas fritas, fallaste. Primero tenés que preguntar: "¿Qué te gusta? ¿Salado o dulce? ¿De qué marca?". Eso es comprender el problema.

**Vocabulario:**
1.  **Datos de entrada (Input):** La información que te dan para empezar (los ingredientes).
2.  **Datos de salida (Output):** Lo que tenés que conseguir al final (la torta terminada).
3.  **Restricciones:** Las reglas que no podés romper (ej: "sin usar calculadora").
::::

**Preguntas para hacerte:**
*   ¿Qué me dan? (Datos)
*   ¿Qué tengo que devolver? (Resultado)
*   ¿Hay alguna trampa o condición especial?

**Quiz Rápido: ¿Verdadero o Falso?**

1.  Lo primero que hay que hacer ante un problema es empezar a escribir código a lo loco. ( **Falso**: Primero hay que entender).
2.  Si no entiendo el problema, es imposible que lo resuelva bien. ( **Verdadero**).

---

## 2. Concebir un Plan: ¿Cómo lo vamos a hacer? 🗺️

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Armá una estrategia paso a paso antes de ponerte a trabajar.

**Analogía:** Si te vas de vacaciones a un lugar que no conocés, no te subís al auto y empezás a manejar para cualquier lado. Primero mirás el mapa, elegís la ruta y calculás la nafta. Eso es planificar.

**Vocabulario:**
1.  **Algoritmo:** Una serie de pasos ordenados para resolver algo.
2.  **Pseudocódigo:** Escribir la solución en "castellano a lo indio", sin preocuparse por la sintaxis perfecta de programación.
3.  **Dividir y conquistar:** Partir un problema gigante en problemas chiquitos más fáciles.
::::

**Estrategias útiles:**
*   ¿Ya resolviste algo parecido antes? ¡Usá esa idea!
*   Hacé un dibujito o esquema.
*   Escribí los pasos en papel.

---

## 3. Ejecutar el Plan: ¡Manos a la obra! 🔨

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Ahora sí, traducí tu plan a código Python siguiendo los pasos que pensaste.

**Analogía:** Es el momento de cocinar. Ya tenés la receta (el plan) y los ingredientes (los datos). Ahora tenés que mezclar, batir y hornear siguiendo las instrucciones al pie de la letra.

**Vocabulario:**
1.  **Implementar:** Escribir el código real en la computadora.
2.  **Sintaxis:** Las reglas de escritura del lenguaje (dónde van los paréntesis, los dos puntos, etc.).
::::

**Consejo:** Si te trabás en una parte, no borres todo. Revisá tu plan. A veces el error está en el plan, no en el código.

---

## 4. Examinar la Solución: ¿Quedó bien? 🧐

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Revisá si tu solución funciona bien y si se puede mejorar.

**Analogía:** Terminaste de armar el mueble. Antes de usarlo, lo mirás bien. ¿Sobraron tornillos? ¿Se mueve si lo empujás? ¿Quedó chueco? Si encontrás un error, lo arreglás. Y si quedó bien, pensás: "¿La próxima vez podría armarlo más rápido?".

**Vocabulario:**
1.  **Testing (Pruebas):** Probar tu programa con diferentes datos para ver si falla.
2.  **Casos borde:** Esos casos raros que rompen todo (ej: ¿qué pasa si el usuario pone un 0? ¿o un número negativo?).
3.  **Optimizar:** Hacer que el código sea más rápido o más fácil de leer.
::::

**Preguntas para el final:**
*   ¿Funciona con datos normales?
*   ¿Funciona con datos raros?
*   ¿Se entiende lo que escribí?

---

### Ejemplo Práctico: El Promedio 📊

**Problema:** Calcular el promedio de 3 notas.

1.  **Comprender:**
    *   Entrada: 3 números (pueden tener coma).
    *   Salida: 1 número (el promedio).
    *   Fórmula: (nota1 + nota2 + nota3) / 3.

2.  **Planificar:**
    *   Pedir nota 1.
    *   Pedir nota 2.
    *   Pedir nota 3.
    *   Sumar las tres.
    *   Dividir por 3.
    *   Mostrar el resultado.

3.  **Ejecutar:**
    ```python
    n1 = float(input("Nota 1: "))
    n2 = float(input("Nota 2: "))
    n3 = float(input("Nota 3: "))
    promedio = (n1 + n2 + n3) / 3
    print(f"El promedio es: {promedio}")
    ```

4.  **Examinar:**
    *   Pruebo con 10, 10, 10. Da 10. ¡Bien!
    *   Pruebo con 0, 0, 0. Da 0. ¡Bien!
    *   ¿Se puede mejorar? Podría usar una lista si fueran muchas notas, pero para 3 está bien así.

---

### Resumen Final
¡Excelente! 🎉 Ahora tenés una herramienta poderosa. No te lances a escribir código sin pensar. **Frená, pensá (Pólya) y después programá.** ¡Vas a ver cómo todo sale más fácil!
