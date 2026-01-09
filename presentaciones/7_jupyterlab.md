---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Guía de JupyterLab'
footer: 'Introducción práctica para estudiantes'

---

<!-- _paginate: false -->
<!-- _header: '' -->

# Guía de Uso de JupyterLab

**Introducción práctica para estudiantes principiantes**

<!--
Notas del orador:
- Bienvenida entusiasta a los estudiantes
- Mencionar que JupyterLab será su herramienta principal durante el curso
- Enfatizar que no necesitan experiencia previa
- Duración estimada: 30-40 minutos
- Asegurar que todos tienen acceso a un navegador web actualizado
-->

<!--
¡Hola a todos! Bienvenidos a esta sesión práctica. Hoy no vamos a ver código complejo, sino que vamos a aprender a usar la herramienta que nos va a acompañar durante todo el curso: JupyterLab. Es como aprender a usar el torno antes de empezar a hacer muebles. No se preocupen si nunca programaron antes, esta herramienta está pensada para aprender y experimentar.
-->
---

## ¿Qué es JupyterLab?

**JupyterLab** es un entorno de desarrollo interactivo que te permite escribir y ejecutar código Python directamente en tu navegador web.

**Funciona como un "cuaderno digital"** donde podés combinar:
- 💻 Código Python
- 📝 Texto explicativo
- 📊 Resultados y gráficos

**En un mismo lugar**

<!--
Notas del orador:
- Empezar con pregunta: "¿Alguien usó alguna vez Google Colab o Jupyter Notebook?"
- Analogía: "Es como tener un cuaderno de laboratorio digital donde experimentás con código"
- Enfatizar que NO es un editor de texto tradicional como Visual Studio Code
- Mencionar que es especialmente útil para aprendizaje y experimentación
- Destacar que combina documentación Y código ejecutable
- Ejemplo cotidiano: "Como escribir una receta de cocina donde podés probar cada paso"
- Verificar: "¿Tiene sentido la diferencia con un editor normal?"
- Tiempo: 3 minutos
-->

<!--
JupyterLab es un entorno mágico. Imaginen un cuaderno de la escuela donde pueden escribir notas, pero además, pueden escribir fórmulas matemáticas y la hoja las resuelve sola. Eso es Jupyter. Combina texto explicativo (como un libro) con código vivo que pueden ejecutar y modificar. Es perfecto para aprender porque ven el resultado ahí mismo, al lado de la explicación.
-->
---

## Ventajas de JupyterLab

✅ **No necesitás instalar nada**: Todo funciona en el navegador
✅ **Inmediato**: Ves los resultados al instante
✅ **Interactivo**: Podés modificar el código y probar
✅ **Visual**: Perfecto para aprender y experimentar

**Usaremos JupyterLite:** Una versión especial que funciona completamente en el navegador

<!--
Notas del orador:
- Leer cada ventaja y dar ejemplo breve de cada una
- "No instalar nada" → Mencionar que evita problemas de configuración
- "Inmediato" → Contrastar con compilar en C/Java
- "Interactivo" → "Pueden cambiar un valor y ver qué pasa al instante"
- "Visual" → Mostrar que pueden ver gráficos directamente
- Explicar diferencia JupyterLab vs JupyterLite (lite = más liviano, en el browser)
- Mencionar que es perfecto para el curso porque todos tienen mismo ambiente
- Tiempo: 2-3 minutos
-->

<!--
¿Por qué usamos esto y no otra cosa? Primero, la barrera de entrada es bajísima. No hay que instalar nada, todo corre en el navegador. Segundo, el feedback es inmediato: escribís, ejecutás y ves. Y tercero, fomenta la experimentación. Pueden cambiar un numerito y ver qué pasa sin romper nada. Vamos a usar una versión 'Lite' que es súper rápida y liviana.
-->
---

## Accediendo a JupyterLab

**Paso 1:** Abrir tu navegador web favorito
- Chrome, Firefox, Edge, Safari

**Paso 2:** Ingresar a la URL:
```
https://ingcom-unrn.github.io/jupyterlite/lab/index.html
```

**Paso 3:** Esperar la carga inicial
- La primera vez puede tardar unos segundos
- Verás el logo de Jupyter con una barra de progreso

💡 **Tip:** Guardá esta URL en favoritos (Ctrl+D)

<!--
Notas del orador:
- Mostrar en pantalla cómo acceder a la URL
- Enfatizar que NO necesitan instalar nada en su computadora
- Mencionar que funciona en cualquier sistema operativo
- Advertir que la primera carga puede tardar 10-15 segundos
- Sugerir que agreguen a favoritos AHORA (hacer todos juntos)
- Verificar que todos hayan cargado correctamente
- Tiempo: 3 minutos + tiempo de espera de carga
-->

<!--
Vamos a entrar todos juntos. Abran su navegador (Chrome o Firefox andan bárbaro). Entren a la URL que ven en pantalla. La primera vez tarda un cachito en cargar porque está bajando toda la magia al navegador. Una vez que cargue, guárdenla en favoritos porque la van a usar siempre. ¿Alguien tuvo problemas para entrar?
-->
---

<!-- _class: lead -->

# La Interfaz de JupyterLab

<!--
Notas del orador:
- Transición: "Ahora que todos tienen JupyterLab abierto, conozcamos la interfaz"
- Hacer zoom a la interfaz si es necesario
- Mencionar que al principio puede parecer abrumador pero es simple
- Comparar con otras aplicaciones que conocen (Word, navegador web)
- Tiempo: 1 minuto
-->

<!--
Bien, ya estamos adentro. No se asusten por todos los botones. La interfaz tiene 4 partes clave. Arriba, el menú de siempre (Archivo, Editar...). A la izquierda, sus archivos y carpetas. Al medio, la mesa de trabajo donde pasa la acción. Y abajo, una barrita de estado que nos dice qué está pasando. Vamos a verlas una por una.
-->
---

## Componentes Principales

La interfaz de JupyterLab se divide en **4 áreas principales**:

1. 🔝 **Barra de Menú Superior**
2. 📁 **Panel Lateral Izquierdo** (File Browser)
3. 📄 **Área de Trabajo Central**
4. ℹ️ **Barra de Estado Inferior**

<!--
Notas del orador:
- Señalar cada área en la pantalla mientras las mencionás
- Dibujar mentalmente con el cursor si es remoto
- Pedir que identifiquen cada área en su pantalla
- Mencionar que nos vamos a enfocar en el área central (la más importante)
- Preguntar: "¿Todos pueden ver estas 4 áreas?"
- Tiempo: 2 minutos
-->

<!--
El menú de arriba es el centro de control. Acá pueden crear archivos nuevos, guardar, cortar y pegar. Lo más importante acá es el menú 'Kernel' (que ya vamos a ver qué es) y el menú 'Run' para correr el código. Tip de pro: apréndanse los atajos de teclado, ahorran muchísimo tiempo.
-->
---

## 1. Barra de Menú Superior

En la parte superior encontrás los menús principales:

- **File**: Crear, abrir, guardar archivos
- **Edit**: Copiar, pegar, deshacer
- **View**: Modificar la apariencia
- **Run**: Ejecutar código
- **Kernel**: Controlar el intérprete de Python
- **Help**: Acceso a la documentación

**Atajo útil:** `Ctrl + Shift + C` para ver todos los atajos de teclado

<!--
A la izquierda tienen el explorador de archivos. Es igual que el Finder o el Explorador de Windows. Acá van a ver las carpetas con los ejercicios del curso. Pueden hacer doble clic para abrir cosas y arrastrar archivos para moverlos. Mantengan esto ordenado para no perderse.
-->
---

## 2. Panel Lateral Izquierdo

Este panel muestra todos los archivos disponibles:

📁 **Carpetas**: Organizan los notebooks por tema
📓 **Notebooks** (archivos `.ipynb`): Los cuadernos de práctica
📄 **Otros archivos**: Datos, imágenes, etc.

**Similar al explorador de archivos de Windows o Finder en Mac**

<!--
El área central es donde van a pasar el 99% del tiempo. Acá se abren los notebooks. Pueden tener varios abiertos en pestañas, como en el navegador. Pueden arrastrarlas para poner dos notebooks lado a lado si quieren comparar código. Es muy flexible.
-->
---

## 3. Área de Trabajo Central

**El área más importante**

Aquí es donde abrís y trabajás con tus notebooks

Podés tener **múltiples notebooks abiertos** al mismo tiempo, organizados en pestañas

<!--
La barra de abajo es el tablero del auto. Les dice si Python está listo para trabajar ('Idle') o si está pensando ('Busy'). También les dice en qué archivo están. Si ven que el círculo de la derecha está lleno, es que Python está trabajando.
-->
---

## 4. Barra de Estado Inferior

Muestra información útil:

- 🐍 El kernel que está ejecutándose (Python)
- 🔌 Estado de la conexión
- 📋 Información del archivo actual

<!--
Vamos a abrir nuestro primer notebook. Vayan a la carpeta '01_fundamentos' y denle doble clic al archivo. ¿Ven cómo se abre en el medio? Fíjense que el archivo termina en `.ipynb`, eso significa 'IPython Notebook', el nombre viejo de esta tecnología.
-->
---

<!-- _class: lead -->

# Trabajar con Notebooks

<!--
Un notebook es una lista de 'celdas'. Piensen en ladrillos. Hay ladrillos de texto (Markdown) donde les explicamos cosas, y ladrillos de código (Code) donde ustedes escriben Python. Pueden reconocer las de código porque tienen un `[ ]` a la izquierda. Las de texto son solo... texto.
-->
---

## Abrir un Notebook

**Paso a paso:**

1. En el panel izquierdo, buscá la carpeta correspondiente
2. Hacé **doble clic** sobre el archivo `.ipynb`
3. El notebook se abrirá en el área central

**Organización recomendada:**
- `01_fundamentos/` → Empezá por aquí
- `02_control_flujo/`
- `03_estructuras/`
- `04_funciones/`
- `05_modulos/`

<!--
Hay dos formas de interactuar con una celda. Si le hacen un clic, la seleccionan (borde azul). Esto es para moverla, copiarla o borrarla. Si le hacen doble clic (o Enter), entran a escribir (borde verde). Es como 'seleccionar el archivo' vs 'abrir el archivo'. Acostúmbrense a cambiar de modo con Esc y Enter.
-->
---

## Estructura de un Notebook

Un notebook está compuesto por **celdas**. Hay dos tipos principales:

**1. Celdas de Código** (`In [ ]:`)
- Contienen código Python
- Se pueden ejecutar
- Muestran resultados

**2. Celdas de Markdown**
- Contienen texto explicativo
- Pueden tener formato (negritas, listas, etc.)
- No se ejecutan, solo se visualizan

<!--
Para que el código haga algo, hay que ejecutar la celda. La forma lenta es el botón de 'Play'. La forma ninja es `Shift + Enter`. Eso ejecuta la celda actual y te manda a la siguiente. Pruébenlo con la celda que dice 'print hola'. ¡Magia!
-->
---

## Modos de Trabajo

JupyterLab tiene **dos modos**:

**Modo Comando** (borde azul)
- Para navegar entre celdas
- Usar atajos de teclado
- **Activar:** `Esc`

**Modo Edición** (borde verde)
- Para escribir código o texto
- Editar el contenido de la celda
- **Activar:** `Enter` o doble clic

<!--
¡Felicidades! Acaban de ejecutar su primer código Python. Fíjense que apareció un numerito en el corchete `[1]`. Eso significa 'esta es la primera celda que se ejecutó'. El resultado aparece justo abajo. Simple y claro.
-->
---

## Ejecutar Celdas

**Forma 1: Atajo de teclado** (recomendado)
```
Shift + Enter
```
Ejecuta la celda y pasa a la siguiente

**Forma 2: Botón Play**
- Botón ▶️ en la barra de herramientas

**Forma 3: Menú**
- `Run` → `Run Selected Cells`

<!--
Ojo con los números. No indican el orden de las celdas en la hoja, sino el orden en que USTEDES las ejecutaron. Si ejecutan la de abajo y después la de arriba, los números van a quedar desordenados. Python recuerda el orden de ejecución, no el visual.
-->
---

## Ejemplo: Primera Ejecución

**Celda de código:**
```python
print("¡Hola, JupyterLab!")
```

**Después de ejecutar (Shift + Enter):**
```
In [1]: print("¡Hola, JupyterLab!")
¡Hola, JupyterLab!
```

**`In [1]`** indica que es la primera celda ejecutada

<!--
Esto es lo mejor de Jupyter: la experimentación. Vayan a la celda del nombre, cambien 'María' por su nombre y ejecuten de vuelta. ¿Ven cómo cambia el resultado? No tengan miedo de tocar. Si rompen algo, siempre se puede arreglar.
-->
---

## Números de Ejecución

```python
In [1]: x = 10        # Primera celda ejecutada
In [2]: y = 20        # Segunda celda ejecutada
In [3]: print(x + y)  # Tercera celda ejecutada
30
```

**El número indica el orden en que ejecutaste las celdas**

⚠️ **Importante:** Puede ser diferente al orden visual en el notebook

<!--
A veces necesitan más espacio. Pueden agregar celdas nuevas con el botón `+` o presionando `B` (de Below, abajo) cuando están en modo comando (azul). Prueben crear una celda y hacer una suma simple.
-->
---

<!-- _class: lead -->

# Editando Celdas

<!--
Si se equivocaron o crearon una celda de más, la borran con la tijerita o presionando `D` dos veces rápido (DD). Cuidado que no pregunta '¿estás seguro?'. Pero tranquilos, `Z` deshace la eliminación.
-->
---

## Modificar el Código

Podés modificar cualquier celda para experimentar:

1. **Seleccioná la celda** (clic sobre ella)
2. **Entrá en modo edición** (Enter o doble clic)
3. **Modificá el código**
4. **Ejecutá nuevamente** (Shift + Enter)

**Ejemplo:**
```python
nombre = "María"
print(f"Hola, {nombre}")
```

**Cambialo por:**
```python
nombre = "Tu Nombre"  # ¡Poné tu nombre aquí!
print(f"Hola, {nombre}")
```

<!--
A veces quieren escribir texto en vez de código. Pueden cambiar el tipo de celda en el menú desplegable de arriba. 'Code' es para Python, 'Markdown' es para texto. También pueden usar `M` y `Y` como atajos. Prueben crear una celda de texto y escribir 'Hola'.
-->
---

## Crear una Nueva Celda

**Opción 1: Botón**
- Clic en el botón **➕** en la barra de herramientas

**Opción 2: Teclado (en modo comando)**
- `A` → Insertar celda **arriba** (Above)
- `B` → Insertar celda **abajo** (Below)

💡 **Tip:** `B` es el más usado (insertar abajo)

<!--
Guardar es sagrado. Jupyter guarda solo cada tanto, pero no se confíen. `Ctrl + S` cada vez que hagan algo importante. El disquete de arriba también funciona. Hágannos caso: guarden seguido.
-->
---

## Eliminar una Celda

**Opción 1: Menú**
- `Edit` → `Delete Cells`

**Opción 2: Teclado (en modo comando)**
- Presioná `D` dos veces: `D`, `D`

⚠️ **Cuidado:** No hay confirmación
Si eliminaste por error: `Ctrl + Z` para deshacer

<!--
Miren la pestaña del archivo arriba. Si tiene un puntito negro o gris, es que hay cambios sin guardar. Si tiene una 'x', está guardado. Es una forma rápida de saber si están seguros.
-->
---

## Cambiar el Tipo de Celda

**Opción 1: Menú desplegable**
- En la barra de herramientas: `Code` o `Markdown`

**Opción 2: Teclado (en modo comando)**
- `Y` → Convertir a celda de **código**
- `M` → Convertir a celda de **Markdown**

<!--
Hablemos del 'Kernel'. Es el cerebro de Python que vive atrás del notebook. Cuando ustedes ejecutan una celda, el notebook le manda el mensaje al Kernel, el Kernel piensa y devuelve la respuesta. Si el Kernel se muere, el notebook no hace nada.
-->
---

<!-- _class: lead -->

# Guardando Tu Trabajo

<!--
El Kernel tiene memoria. Si definen `x=10` en una celda, el Kernel se acuerda de `x` para siempre (hasta que lo reinicien). Por eso pueden usar variables de una celda en otra. Es una conversación continua, no frases aisladas.
-->
---

## Guardar el Notebook

**Opción 1: Atajo de teclado** (recomendado)
```
Ctrl + S  (Windows/Linux)
Cmd + S   (Mac)
```

**Opción 2: Menú**
- `File` → `Save Notebook`

**Opción 3: Botón**
- Icono de disquete 💾 en la barra de herramientas

<!--
Volvemos al tema del orden. Como el Kernel recuerda lo que ejecutaron, si saltan de la celda 1 a la 10 y vuelven a la 5, pueden tener resultados raros. Traten de mantener un flujo lógico de arriba a abajo para no confundirse.
-->
---

## Indicador de Guardado

En la pestaña del notebook verás:

**Punto negro (●)** al lado del nombre
→ Hay cambios sin guardar

**Sin punto**
→ Todo guardado correctamente

```
ejercicio_1.ipynb ●   ← Sin guardar
ejercicio_1.ipynb     ← Guardado ✓
```

💡 JupyterLab guarda automáticamente cada pocos minutos, pero es buena práctica **guardar manualmente** después de cambios importantes

<!--
A veces el Kernel se marea o las variables quedan sucias. La solución informática universal: reiniciar. `Kernel -> Restart` borra toda la memoria y arranca de cero. Es como apagar y prender la compu. Muy útil para limpiar.
-->
---

<!-- _class: lead -->

# El Kernel de Python

<!--
La mejor forma de reiniciar es 'Restart Kernel and Run All Cells'. Esto limpia todo y vuelve a ejecutar todo desde arriba en orden. Si su notebook funciona bien haciendo esto, es un notebook sólido. Úsenlo antes de entregar un trabajo.
-->
---

## ¿Qué es el Kernel?

El **kernel** es el "motor" que ejecuta tu código Python

**Pensalo como un intérprete de Python** corriendo en segundo plano

**Cuando ejecutás una celda:**
1. 📤 El notebook envía tu código al kernel
2. ⚙️ El kernel ejecuta el código
3. 📥 El kernel devuelve el resultado

<!--
Si hacen un bucle infinito (un programa que nunca termina), el Kernel se queda ocupado para siempre. Van a ver un asterisco `[*]` en la celda. Para frenarlo, usen el botón de 'Stop' (el cuadrado) o 'Interrupt Kernel'. Es el freno de mano.
-->
---

## Estado del Kernel

El kernel **mantiene la memoria** de todo lo ejecutado

**Ejemplo:**

**Celda 1:**
```python
x = 10
```

**Celda 2** (ejecutada después):
```python
print(x)  # Imprime: 10
```

El kernel "recuerda" que `x = 10` incluso en celdas separadas

<!--
Los atajos son vida. `A` y `B` para crear celdas. `DD` para borrar. Son los que más van a usar en 'Modo Comando' (azul). Apréndanselos y van a volar.
-->
---

## Orden de Ejecución

⚠️ **Importante:** El kernel recuerda el **orden en que ejecutaste** las celdas, no el orden en que están escritas

**El número `In [n]:` te indica el orden de ejecución**

```python
In [2]: y = x + 5   # Ejecutada segunda
In [1]: x = 10      # Ejecutada primera
```

Aunque `y = x + 5` está primero visualmente, `x = 10` se ejecutó primero

<!--
En 'Modo Edición' (verde), `Shift + Enter` es su mejor amigo. `Tab` les autocompleta código (buenísimo para no escribir todo) y `Shift + Tab` les muestra la ayuda de una función. Úsenlos.
-->
---

## Reiniciar el Kernel

A veces necesitás **"empezar de cero"**

Reiniciar el kernel **borra toda la memoria**

**Cuándo reiniciar:**
- ❌ Variables no definidas pero deberían estarlo
- 🔄 Querés ejecutar todo desde el principio
- 🐛 Comportamiento extraño del código

<!--
No se abrumen. Hay mil atajos, pero con esos 5 o 6 que vimos hacen el 90% del trabajo. Si alguna vez se olvidan, `Ctrl + Shift + C` les muestra la lista completa. Es el machete oficial.
-->
---

## Cómo Reiniciar el Kernel

**Opción 1: Solo reiniciar**
- `Kernel` → `Restart Kernel`

**Opción 2: Reiniciar y ejecutar todo**
- `Kernel` → `Restart Kernel and Run All Cells`
- **Recomendado:** Verifica que todo funcione en orden

**Opción 3: Botón**
- Icono 🔄 en la barra de herramientas

<!--
Buenas prácticas para no volverse locos. 1: Ejecuten en orden. Si definen una variable abajo y la tratan de usar arriba, va a fallar la primera vez (porque la de abajo no corrió todavía). Mantengan la lógica secuencial.
-->
---

## Interrumpir la Ejecución

Si una celda está tardando mucho o entró en un loop infinito:

**Botón:** ⏹️ en la barra de herramientas
**Menú:** `Kernel` → `Interrupt Kernel`

```python
# Ejemplo de loop infinito (¡No ejecutes esto!)
while True:
    print("Esto nunca termina...")
```

Si ejecutaste esto por error, **interrumpí el kernel** con ⏹️

<!--
2: De vez en cuando, reinicien todo. Les asegura que su código es reproducible y no depende de algo que borraron hace media hora pero quedó en memoria.
-->
---

<!-- _class: lead -->

# Atajos de Teclado Esenciales

<!--
3: Guarden. En serio. No hay nada peor que perder media hora de trabajo porque se colgó el navegador. `Ctrl + S` es un tic nervioso que tienen que desarrollar.
-->
---

## Modo Comando (Esc)

| Atajo | Acción |
|
---
----|
---
-----|
| `A` | Insertar celda arriba |
| `B` | Insertar celda abajo |
| `D`, `D` | Eliminar celda |
| `M` | Convertir a Markdown |
| `Y` | Convertir a código |
| `Ctrl + S` | Guardar |

<!--
4: Comenten su código. Usen las celdas de Markdown para explicar qué están pensando. Su 'yo del futuro' se los va a agradecer cuando tenga que repasar esto en dos semanas.
-->
---

## Modo Edición (Enter)

| Atajo | Acción |
|
---
----|
---
-----|
| `Shift + Enter` | Ejecutar y pasar a siguiente |
| `Ctrl + Enter` | Ejecutar sin cambiar celda |
| `Tab` | Autocompletar |
| `Shift + Tab` | Ver documentación |
| `Esc` | Salir a modo comando |

<!--
5: Dividan y vencerán. No hagan una celda gigante de 100 líneas. Hagan celdas chicas, lógicas. Una para definir variables, otra para procesar, otra para mostrar. Es más fácil de leer y de debuggear.
-->
---

## Ver Todos los Atajos

**Dentro de JupyterLab:**

Presioná `Ctrl + Shift + C` (o `Cmd + Shift + C` en Mac)

Verás una lista completa de todos los atajos disponibles

<!--
Problemas típicos. Si ven el asterisco `[*]` eterno, el Kernel se colgó o está pensando mucho. Esperen un poco, y si no, interrrumpan o reinicien.
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
Si les dice 'NameError: name x is not defined', es que no ejecutaron la celda donde está `x`, o la ejecutaron después de usarla, o escribieron mal el nombre. Chequeen el orden de ejecución (los numeritos).
-->
---

## 1. Ejecutá las Celdas en Orden

✅ **Buena práctica:**
```python
# Celda 1 (ejecutás primero)
x = 10

# Celda 2 (ejecutás después)
print(x)  # Funciona correctamente
```

❌ **Mala práctica:**
```python
# Celda 2 (ejecutás primero)
print(x)  # Error: x no está definida

# Celda 1 (ejecutás después)
x = 10
```

<!--
Si ven el puntito negro en la pestaña, es que no guardaron. No cierren la pestaña así nomás. Guarden primero.
-->
---

## 2. Reiniciá y Ejecutá Todo Regularmente

Cada tanto, es buena idea:

1. `Kernel` → `Restart Kernel and Run All Cells`
2. Verificar que todo funcione en orden

Esto asegura que tu notebook funciona correctamente de principio a fin

<!--
Si no encuentran su archivo, miren el panel de la izquierda. A veces entramos en carpetas sin querer. La casita los lleva al inicio. Busquen los `.ipynb`.
-->
---

## 3. Guardá Frecuentemente

Acostumbrate a presionar `Ctrl + S` regularmente

**No esperes a terminar todo para guardar**

Guardá después de:
- ✅ Resolver un ejercicio
- ✅ Escribir código importante
- ✅ Hacer cambios significativos

<!--
¿Cómo estudiar con esto? No lo lean como un PDF. Es interactivo. Ejecuten celda por celda. Miren qué pasa. Traten de predecir el resultado antes de ejecutarlo. Esa es la forma activa de aprender.
-->
---

## 4. Documentá Tu Código

Usá celdas de Markdown para:
- ✍️ Explicar qué hace tu código
- 📝 Anotar dudas o ideas
- 🎯 Describir el objetivo de cada ejercicio

```python
# Bueno: Código con comentarios explicativos
edad = 25  # Edad del usuario en años
es_mayor = edad >= 18  # Verificar si es mayor de edad
```

<!--
Cuando hagan ejercicios: lean bien, piensen la estrategia, y recién ahí escriban código. Prueben con distintos valores. ¿Qué pasa si pongo un número negativo? ¿Si pongo texto? Experimenten.
-->
---

## 5. Mantené las Celdas Cortas

❌ **Evitar:**
```python
# 50 líneas de código sin separar
x = 10
y = 20
# ... muchas líneas más ...
resultado = calcular()
```

✅ **Preferir:**
```python
# Celda 1: Definir variables
x = 10
y = 20
```

```python
# Celda 2: Hacer cálculo
resultado = calcular()
```

<!--
Rompan cosas. En serio. No va a explotar la computadora. Borren líneas, cambien nombres, hagan lío. Después reinician el Kernel y acá no pasó nada. El miedo a romper es el enemigo del aprendizaje.
-->
---

<!-- _class: lead -->

# Solución de Problemas

<!--
Checklist mental. ¿Saben entrar? ¿Saben abrir un notebook? ¿Saben ejecutar? Si tienen tildes en estos casilleros, ya tienen la base.
-->
---

## Problema: El Kernel No Responde

**Síntomas:** La celda muestra `In [*]:` por mucho tiempo

**Soluciones:**
1. ⏳ Esperar unos segundos (puede ser un cálculo lento)
2. ⏹️ Interrumpir el kernel (botón stop)
3. 🔄 Si persiste, reiniciar el kernel

<!--
¿Entienden la diferencia entre código y texto? ¿Saben crear celdas nuevas? ¿Saben borrar las que sobran? Bien, vamos bien.
-->
---

## Problema: Variables No Definidas

**Error:** `NameError: name 'x' is not defined`

**Causa:** La celda que define `x` no fue ejecutada

**Solución:**
1. Buscá la celda donde se define la variable
2. Ejecutala con `Shift + Enter`
3. Volvé a ejecutar la celda con error

💡 **Tip:** Hacé `Restart and Run All` si no estás seguro

<!--
¿Ya escribieron su primer 'Hola Mundo'? ¿Vieron el output? ¿Entendieron por qué salió eso? Excelente.
-->
---

## Problema: Cambios No Guardados

**Síntomas:** Ves el punto negro (●) en la pestaña

**Solución:**
- Presioná `Ctrl + S` para guardar

<!--
¿Entienden que el Kernel es el motor? ¿Saben reiniciarlo si se traba? Fundamental para no frustrarse.
-->
---

## Problema: No Encuentro un Archivo

**Soluciones:**
1. Verificá que estás en el directorio correcto
2. Usá la barra de búsqueda del file browser
3. Revisá que el archivo tenga extensión `.ipynb`

<!--
¿Guardaron el archivo? ¿Saben usar el autocompletado? Estas son las herramientas que los van a hacer más rápidos.
-->
---

<!-- _class: lead -->

# Estrategia de Aprendizaje

<!--
Y lo más importante: ¿Están ejecutando en orden? ¿Están documentando? Esas son las costumbres que los van a hacer buenos programadores.
-->
---

## Método de Estudio con Notebooks

**1. Primera pasada:** Leé todas las celdas sin ejecutar
- Entendé el contexto general

**2. Segunda pasada:** Ejecutá cada celda una por una
- Observá los resultados
- Comprendé qué hace cada parte

**3. Tercera pasada:** Experimentá modificando el código
- Cambiá valores
- Agregá prints
- Probá diferentes enfoques

<!--
Resumiendo: JupyterLab es su laboratorio. Combina la teoría y la práctica en una sola pantalla. Úsenlo, explorenlo y háganlo suyo.
-->
---

## Trabajar con Ejercicios

Cuando trabajes en ejercicios:

1. 📖 **Leé** el enunciado completo
2. 🤔 **Pensá** la solución antes de escribir código
3. ✍️ **Escribí** tu código en una nueva celda
4. ▶️ **Ejecutá** y probá con diferentes valores
5. 🔍 **Compará** con la solución propuesta (si hay)

<!--
El Kernel es su amigo (aunque a veces se empaca). Los modos comando y edición son como manejar y escribir. Y los atajos de teclado son sus superpoderes.
-->
---

## Experimentar es Clave

💡 **No tengas miedo de modificar el código**

La mejor forma de aprender es experimentando

Si algo sale mal:
- ✅ Podés volver a la versión original
- ✅ Reiniciar el kernel y empezar de nuevo
- ✅ Cada error es una oportunidad de aprender

<!--
Acá tienen la lista de atajos para imprimir o copiar. Péguenla cerca del monitor las primeras semanas hasta que les salga de memoria.
-->
---

<!-- _class: lead -->

# Checklist de Habilidades

<!--
Si se traban o quieren saber más, la documentación oficial es muy buena. Y recuerden la URL de acceso, ténganla a mano.
-->
---

## ✅ Navegación Básica

- [ ] Acceder a JupyterLab en el navegador
- [ ] Navegar por el explorador de archivos
- [ ] Abrir un notebook existente
- [ ] Identificar los componentes de la interfaz

<!--
Consejos finales: Paciencia. Nadie nace sabiendo. La curiosidad es su mejor combustible. Prueben, fallen, arreglen y aprendan. Y sobre todo, practiquen un poquito todos los días.
-->
---

## ✅ Trabajo con Celdas

- [ ] Diferenciar celdas de código y Markdown
- [ ] Seleccionar una celda
- [ ] Cambiar entre modo comando y edición
- [ ] Ejecutar una celda de código
- [ ] Crear una nueva celda
- [ ] Eliminar una celda

<!--
¡Éxitos! Están empezando un camino increíble. JupyterLab va a ser su compañero de ruta. Domínenlo y tendrán la mitad de la batalla ganada. ¡Nos vemos en el próximo capítulo!
-->
---

## ✅ Ejecución de Código

- [ ] Ejecutar código Python básico
- [ ] Leer mensajes de error
- [ ] Modificar código y volver a ejecutar
- [ ] Ver los resultados (output)

<!--
Ahora que ya tienen la herramienta, pueden empezar con el contenido real. Fundamentos, Control de Flujo... todo los espera. ¡A programar se ha dicho!
-->
---

## ✅ Gestión del Kernel

- [ ] Entender qué es el kernel
- [ ] Reiniciar el kernel
- [ ] Ejecutar todas las celdas
- [ ] Interrumpir una ejecución

<!--
NO MORE NOTES
-->
---

## ✅ Productividad

- [ ] Guardar el notebook
- [ ] Usar autocompletado (Tab)
- [ ] Ver documentación (Shift + Tab)
- [ ] Usar al menos 3 atajos de teclado

<!--
NO MORE NOTES
-->
---

## ✅ Buenas Prácticas

- [ ] Ejecutar celdas en orden
- [ ] Documentar mi código
- [ ] Experimentar con modificaciones
- [ ] Buscar soluciones a errores comunes

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Resumen

<!--
NO MORE NOTES
-->
---

## Conceptos Clave

**JupyterLab:**
- Entorno interactivo para Python
- Funciona en el navegador
- Combina código, texto y resultados

**Notebooks:**
- Compuestos por celdas
- Dos tipos: código y Markdown
- Se ejecutan con `Shift + Enter`

<!--
NO MORE NOTES
-->
---

## Conceptos Clave (cont.)

**Kernel:**
- Motor que ejecuta el código
- Mantiene memoria de lo ejecutado
- Se puede reiniciar para empezar de cero

**Modos:**
- Comando (azul) → Navegación
- Edición (verde) → Escribir

<!--
NO MORE NOTES
-->
---

## Atajos Esenciales

| Atajo | Acción |
|
---
----|
---
-----|
| `Shift + Enter` | Ejecutar celda |
| `A` / `B` | Insertar celda arriba/abajo |
| `D`, `D` | Eliminar celda |
| `M` / `Y` | Markdown / Código |
| `Ctrl + S` | Guardar |
| `Esc` / `Enter` | Modo comando / edición |

<!--
NO MORE NOTES
-->
---

## Recursos

**Acceso a JupyterLab:**
```
https://ingcom-unrn.github.io/jupyterlite/lab/index.html
```

**Ver atajos:**
`Ctrl + Shift + C` dentro de JupyterLab

**Documentación oficial:**
[jupyterlab.readthedocs.io](https://jupyterlab.readthedocs.io/)

<!--
NO MORE NOTES
-->
---

## ¡A Programar!

Recordá:

1. 🎯 **Empezá con calma**: No intentes aprender todo de una vez
2. 🔬 **Experimentá**: Probá, modificá, rompé cosas (y arreglalas)
3. 🐛 **Los errores son buenos**: Cada error es una oportunidad
4. 💪 **Practicá regularmente**: Mejor 30 min diarios que 3 horas una vez
5. ❓ **Preguntá**: Si no entendés algo, buscá ayuda

<!--
NO MORE NOTES
-->
---

<!-- _paginate: false -->

# ¡Éxito en Tu Aprendizaje!

**Cada programador experto comenzó donde estás vos ahora.**

Lo que los distingue es la **práctica constante** y la **curiosidad**.

**¡Vos también podés lograrlo!** 🐍✨

<!--
NO MORE NOTES
-->
---

## Próximos Pasos

Una vez que domines JupyterLab:

**📗 Capítulo 1: Fundamentos de Python**
- Variables y tipos de datos
- Operadores
- Entrada y salida

**📘 Capítulo 2: Control de Flujo**
- Condicionales (if/else)
- Lazos (while/for)

**📙 Y seguir adelante** con los demás capítulos
