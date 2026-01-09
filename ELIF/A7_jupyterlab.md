---
title: Guía de JupyterLab (Versión Escolar)
short_title: 7 - JupyterLab
subtitle: Tu cuaderno digital para programar
---

(jupyterlab-escolar)=
# Guía de uso de JupyterLab

¡Hola! 👋 Bienvenido a tu laboratorio de programación. JupyterLab es la herramienta donde vas a escribir, probar y ver funcionar tus programas. Es como tu cuaderno de clases, pero mucho más poderoso.

::::{admonition} Resumen del Capítulo (TL;DR)
:class: note
Vas a aprender a usar JupyterLab, una web donde podés escribir código Python y ver el resultado al instante, todo sin instalar nada en tu compu.
::::

---

## 1. ¿Qué es JupyterLab? 🤔

::::{admonition} Conceptos Clave
:class: tip

**TL;DR:** Es una página web donde escribís código y texto juntos en un mismo archivo llamado "Notebook".

**Analogía:** Imaginate un cuaderno escolar mágico. En una hoja podés escribir explicaciones (como en Lengua), en otra podés hacer cuentas que se resuelven solas (como en Matemáticas) y en otra podés pegar gráficos que se actualizan solos. Todo en el mismo cuaderno. Eso es un Jupyter Notebook.

**Vocabulario:**
1.  **Notebook (Cuaderno):** El archivo donde trabajás. Tiene extensión `.ipynb`.
2.  **Celda:** Cada "renglón" o bloque del cuaderno. Puede ser de texto o de código.
3.  **Kernel:** El cerebro de Python que vive "detrás" del cuaderno y ejecuta tus órdenes.
::::

### ¿Por qué lo usamos?
*   ✅ **No instalás nada:** Funciona en el navegador (Chrome, Firefox).
*   ✅ **Interactivo:** Escribís código, apretás "Play" y ves qué pasa ahí mismo.
*   ✅ **Ordenado:** Podés mezclar explicaciones con código para que se entienda mejor.

---

(accediendo-escolar)=
## 2. Entrando al Laboratorio 🚪

1.  Abrí tu navegador (Chrome, Edge, Firefox).
2.  Entrá al link que te dieron los profes (o el de JupyterLite).
3.  ¡Listo! Vas a ver una pantalla parecida a esto:

*(Acá imaginá una captura de pantalla de JupyterLab)*

A la izquierda tenés tus archivos (como el Explorador de Windows) y a la derecha tu área de trabajo.

---

(celdas-escolar)=
## 3. Las Celdas: Los ladrillos de tu cuaderno 🧱

Un Notebook está hecho de **celdas**. Hay dos tipos principales:

1.  **Celdas de Código:** Acá escribís Python. Tienen un `[ ]` al costado.
2.  **Celdas de Texto (Markdown):** Acá escribís explicaciones, títulos, etc.

**Quiz Rápido: ¿Verdadero o Falso?**

1.  En una celda de texto puedo escribir código Python y que funcione. ( **Falso**: Solo es texto, no se ejecuta).
2.  Un Notebook puede tener todas las celdas que quieras. ( **Verdadero**).

---

(ejecutando-codigo-escolar)=
## 4. ¡Hacé correr tu código! ▶️

Para que la compu lea tu código y haga algo, tenés que **ejecutar la celda**.

**¿Cómo se hace?**
1.  Hacé clic en la celda que querés ejecutar.
2.  Apretá las teclas `Shift + Enter` (Mayús + Enter).
3.  ¡Magia! ✨ El resultado aparece justo abajo.

```python
# Probá esto en una celda:
print("¡Hola Jupyter!")
```

### El numerito misterioso `In [1]:`
Cuando ejecutás una celda, aparece un número al costado (ej: `In [1]`). Eso te dice el **orden** en que se ejecutaron las cosas.
*   Si ves un asterisco `In [*]`, significa que la compu está **pensando** (ejecutando). ¡Paciencia!

---

(kernel-escolar)=
## 5. El Kernel: El cerebro detrás de escena 🧠

El Kernel es el motor de Python. A veces se puede marear o colgar (como cuando se te tilda el celu).

**Si todo falla:**
1.  Buscá el menú **Kernel**.
2.  Elegí **Restart Kernel** (Reiniciar Kernel).
3.  Es como apagar y prender la compu. Borra la memoria de las variables, pero tu código escrito queda guardado.

---

(atajos-escolar)=
## 6. Atajos para ser un Pro ⌨️

Si querés programar rápido como en las películas, usá estos atajos:

*   **`Shift + Enter`**: Ejecutar celda y pasar a la siguiente.
*   **`Ctrl + S`**: Guardar (¡hacelo seguido!).
*   **`A`**: Crear celda Arriba (Above).
*   **`B`**: Crear celda aBajo (Below).
*   **`D, D`**: Borrar celda (apretá D dos veces rápido).

---

(ejercicios-escolar)=
## 7. Misión de Entrenamiento 🏋️

¡A probar si entendiste!

### Misión 1: El Saludo
1.  Creá un nuevo Notebook.
2.  En la primera celda, escribí `print("¡Estoy programando!")` y ejecutala.

### Misión 2: Matemáticas Rápidas
1.  En una celda nueva, escribí `5 * 8 + 2` y ejecutala.
2.  ¿Viste el resultado abajo?

### Misión 3: El Error
1.  Escribí `print("Hola"` (sin cerrar el paréntesis) y ejecutala.
2.  Mirá el error rojo. ¡No te asustes! Jupyter te avisa qué pasó.
3.  Corregilo y volvé a ejecutar.

---

### Resumen Final
¡Excelente! 🎉 Ya sabés manejar tu cuaderno digital. JupyterLab va a ser tu mejor amigo durante todo el curso. Acordate: `Shift + Enter` es tu tecla mágica. ¡A programar!
