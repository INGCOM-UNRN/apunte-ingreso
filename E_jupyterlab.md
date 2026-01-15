---
title: Guía de uso de JupyterLab
short_title: 0x0005h - JupyterLab
subtitle: Introducción práctica a JupyterLab para estudiantes principiantes
---

## Introducción

¡Bienvenido a tu primera experiencia con **JupyterLab**! Esta guía está diseñada para que puedas comenzar a trabajar con los cuadernos de práctica sin complicaciones. No te preocupes si nunca programaste antes: vamos a ver todo paso a paso.

:::{note} ¿Qué es JupyterLab?
**JupyterLab** es un entorno de desarrollo interactivo que te permite escribir y ejecutar código Python directamente en tu navegador web. Funciona como un "cuaderno digital" donde podés combinar código, texto explicativo y resultados en un mismo lugar.
:::

En este curso, vas a usar una versión especial de JupyterLab llamada **JupyterLite**, que funciona completamente en tu navegador sin necesidad de instalar nada en tu computadora.

:::{tip} Ventajas de JupyterLab
- ✅ **No necesitás instalar nada**: Todo funciona en el navegador
- ✅ **Inmediato**: Ves los resultados al instante
- ✅ **Interactivo**: Podés modificar el código y probar
- ✅ **Visual**: Perfecto para aprender y experimentar
:::

:::{warning} Acceso a los archivos

Por como está armado este entorno de programación, nosotros no tenemos acceso de ningún tipo a los cambios que hagan en los cuadernos, por lo que es necesario que si quieren compartirlos o guardalos, lo hagan por fuera de la herramienta. Esto también significa que ustedes deben de descargar los cuadernos y hacerles backup, ya que, esta información está en su computadora.

:::

---

## Accediendo a JupyterLab

### Paso 1: Abrir el navegador web

Primero, abrí tu navegador web favorito (Chrome, Firefox, Edge, Safari). JupyterLab funciona mejor en navegadores modernos y actualizados. Aunque, técnicamente, podés utilizarlo desde el teléfono, la falta de teclado y la pantalla reducida complicaría mucho su uso. Una tablet es viable, pero igual es recomendable contar con un teclado.

### Paso 2: Ingresar a la URL

En la barra de direcciones, ingresá la siguiente URL:

```
https://ingcom-unrn.github.io/jupyterlite/lab/index.html
```

:::{important} Guardar en Favoritos
Te recomendamos **guardar esta URL en tus favoritos** (Ctrl+D en la mayoría de los navegadores) para acceder rápidamente en el futuro.
:::

### Paso 3: Esperar la carga inicial

La primera vez que accedas, JupyterLab puede tardar unos segundos en cargar. Verás una pantalla de carga con el logo de Jupyter.

**[CAPTURA: Pantalla de carga de JupyterLab con el logo naranja de Jupyter y una barra de progreso. Fondo oscuro con el texto "Loading JupyterLite" visible.]**

:::{note} Primera Carga
La primera carga puede demorar un poco más porque está descargando los archivos necesarios. Las siguientes veces será mucho más rápido.
:::

---

## La Interfaz de JupyterLab

Una vez que cargue completamente, verás la interfaz principal de JupyterLab. Vamos a conocer cada parte:

**[CAPTURA: Vista completa de la interfaz de JupyterLab mostrando: barra de menú superior, panel lateral izquierdo con el explorador de archivos, área de trabajo central con un notebook abierto, y la barra de estado inferior.]**

### Componentes Principales

La interfaz de JupyterLab se divide en varias áreas:

```{figure} 7/interfaz_jupyterlab.svg
:label: fig-interfaz-jupyterlab
:align: center
:width: 100%

Componentes principales de la interfaz de JupyterLab
```

**[NOTA SVG: Crear diagrama que muestre las 4 áreas principales numeradas: 1) Barra de menú superior, 2) Panel lateral izquierdo (file browser), 3) Área de trabajo central, 4) Barra de estado inferior. Usar colores distintivos para cada área.]**

#### 1. Barra de Menú Superior

En la parte superior encontrarás los menús principales:

- **File**: Crear, abrir, guardar archivos
- **Edit**: Copiar, pegar, deshacer
- **View**: Modificar la apariencia
- **Run**: Ejecutar código
- **Kernel**: Controlar el intérprete de Python
- **Help**: Acceso a la documentación

:::{tip} Atajos de Teclado
JupyterLab tiene muchos atajos de teclado útiles. Presioná `Ctrl + Shift + C` (o `Cmd + Shift + C` en Mac) para ver una lista completa.
:::

#### 2. Panel Lateral Izquierdo (File Browser)

Este panel te muestra todos los archivos disponibles, similar al explorador de archivos de Windows o Finder en Mac.

**[CAPTURA: Panel lateral izquierdo mostrando la estructura de carpetas con los notebooks de práctica organizados. Debe verse claramente el ícono de carpeta y los archivos .ipynb con el ícono característico de notebook.]**

Aquí verás:
- 📁 **Carpetas**: Organizan los notebooks por tema
- 📓 **Notebooks** (archivos `.ipynb`): Los cuadernos de práctica
- 📄 **Otros archivos**: Datos, imágenes, etc.

#### 3. Área de Trabajo Central

Esta es el área más importante. Aquí es donde abrirás y trabajarás con tus notebooks. Podés tener múltiples notebooks abiertos al mismo tiempo, organizados en pestañas.

#### 4. Barra de Estado Inferior

Muestra información útil como:
- El kernel que está ejecutándose (Python)
- Estado de la conexión
- Información del archivo actual

---

## Navegando por los Archivos

### Explorando las Carpetas

En el panel lateral izquierdo, verás una estructura organizada con los cuadernos de práctica.

**[CAPTURA: Vista detallada del explorador de archivos mostrando carpetas expandidas con nombres descriptivos como "01_fundamentos", "02_control_flujo", etc. Cada carpeta debe mostrar algunos archivos .ipynb dentro.]**

Para navegar:

1. **Hacer clic en una carpeta** para expandirla y ver su contenido
2. **Hacer doble clic en un archivo** para abrirlo
3. **Usar los íconos superiores** para cambiar la vista

:::{tip} Organización
Los cuadernos están organizados siguiendo el orden del apunte. Te recomendamos trabajarlos en secuencia:
- `01_fundamentos/` → Empezá por aquí
- `02_control_flujo/`
- `03_estructuras/`
- `04_funciones/`
- `05_modulos/`
:::

### Abrir un Notebook

Para abrir tu primer notebook:

1. En el panel izquierdo, buscá la carpeta correspondiente
2. Hacé **doble clic** sobre el archivo `.ipynb` que querés abrir
3. El notebook se abrirá en el área central

**[CAPTURA: Secuencia de dos imágenes mostrando: 1) Cursor sobre un archivo .ipynb en el file browser, 2) El mismo notebook ya abierto en el área central con su contenido visible.]**

:::{note} Extensión .ipynb
Los notebooks de Jupyter tienen la extensión `.ipynb` (Interactive Python Notebook). Estos archivos contienen código, texto y resultados juntos.
:::

---

## Anatomía de un Notebook

Una vez abierto un notebook, verás que está compuesto por **celdas**. Cada celda puede contener código Python o texto explicativo.

**[CAPTURA: Vista de un notebook abierto mostrando claramente diferentes tipos de celdas: una celda de Markdown con texto formateado, seguida de una celda de código con código Python, y debajo el resultado de la ejecución.]**

### Tipos de Celdas

```{figure} 7/tipos_celdas.svg
:label: fig-tipos-celdas
:align: center
:width: 90%

Tipos de celdas en un Jupyter Notebook: Markdown para texto y Code para código ejecutable
```

**[NOTA SVG: Crear diagrama que muestre dos celdas: una celda de Markdown con texto formateado (título, lista, negrita) y una celda de código con código Python simple y su output. Incluir etiquetas claras indicando "Celda Markdown" y "Celda Code".]**

#### Celdas de Markdown (Texto)

Contienen texto explicativo, títulos, listas, etc. Se usan para documentar y explicar el código.

Características:
- 📝 No se ejecutan como código
- 📄 Soportan formato: **negritas**, *cursivas*, títulos, listas
- 🔗 Pueden incluir enlaces y fórmulas matemáticas

#### Celdas de Código

Contienen código Python que podés ejecutar.

Características:
- 💻 Se ejecutan cuando las corrés
- 📊 Muestran los resultados debajo
- 🔢 Tienen un número de ejecución `In [1]:`

**[CAPTURA: Vista detallada de una celda de código mostrando: el prompt "In [1]:", el código Python dentro de la celda, el botón de ejecutar, y debajo el resultado con "Out [1]:"]**

### Seleccionar una Celda

Para trabajar con una celda, primero tenés que **seleccionarla**:

- **Hacer clic** sobre la celda
- Verás un **borde coloreado** alrededor (azul o verde según el modo)

**[CAPTURA: Dos imágenes lado a lado mostrando: 1) Celda en "modo comando" con borde azul, 2) Celda en "modo edición" con borde verde y cursor parpadeando dentro.]**

### Modos de una Celda

JupyterLab tiene dos modos principales:

#### Modo Comando (Borde Azul)

En este modo podés:
- Navegar entre celdas con las flechas ↑↓
- Crear, eliminar, copiar celdas
- Cambiar el tipo de celda

**Activarlo**: Presionar `Esc` o hacer clic fuera del área de texto

#### Modo Edición (Borde Verde)

En este modo podés:
- Escribir y editar el contenido de la celda
- Modificar código o texto

**Activarlo**: Presionar `Enter` o hacer doble clic dentro de la celda

:::{important} Diferencia Clave
- **Azul = Navegar**: Trabajás con la celda como un todo
- **Verde = Editar**: Trabajás dentro de la celda
:::

---

## Ejecutando Código Python

Ahora viene la parte más emocionante: **ejecutar tu primer código Python**.

### Tu Primera Ejecución

Vamos a ejecutar una celda de código paso a paso:

**Paso 1**: Seleccioná una celda de código (debe tener código Python dentro)

**Paso 2**: Ejecutá la celda usando **uno** de estos métodos:

- **Método 1**: Presionar `Shift + Enter` (más común)
- **Método 2**: Presionar el botón ▶️ en la barra de herramientas
- **Método 3**: Menú `Run` → `Run Selected Cells`

**[CAPTURA: Imagen mostrando los tres métodos: 1) Teclado con las teclas Shift y Enter resaltadas, 2) Botón "Run" en la barra de herramientas con una flecha señalándolo, 3) Menú Run desplegado con "Run Selected Cells" resaltado.]**

**Paso 3**: Observá el resultado que aparece debajo de la celda

### Ejemplo Práctico

Supongamos que tenés esta celda de código:

```python
# Mi primer programa en Python
print("¡Hola, mundo!")
print("Estoy aprendiendo Python")
```

Cuando la ejecutás (`Shift + Enter`), verás:

```
¡Hola, mundo!
Estoy aprendiendo Python
```

**[CAPTURA: Vista "antes y después" mostrando: 1) Celda con el código y sin número de ejecución, 2) La misma celda después de ejecutar con "In [1]:" y el output visible debajo.]**

### Entendiendo el Output

Después de ejecutar una celda:

- Aparece un **número entre corchetes**: `In [1]:`
  - Este número indica el orden de ejecución
  - Si ves `In [*]:` significa que está ejecutándose

- Debajo aparece el **resultado**:
  - Texto impreso con `print()`
  - Valores devueltos
  - Gráficos o tablas

:::{tip} Ejecutar Todo
Si querés ejecutar todas las celdas del notebook de una vez, andá a `Run` → `Run All Cells`. Esto es útil cuando abrís un notebook para la primera vez.
:::

### ¿Qué Pasa Si Hay un Error?

No te preocupes: **los errores son normales** y parte del aprendizaje. Si hay un error en el código, Python te lo mostrará.

**[CAPTURA: Ejemplo de celda con error mostrando: el código con un error intencional (ej: variable no definida), y debajo el mensaje de error en rojo con el traceback visible.]**

Los mensajes de error incluyen:
- 🔴 Texto en rojo indicando que hubo un problema
- 📍 El tipo de error (ej: `NameError`, `SyntaxError`)
- 📝 Una descripción del problema
- 📄 La línea donde ocurrió

:::{note} Aprender de los Errores
Los errores son tus **maestros más honestos**. Leé el mensaje de error con atención: Python te está diciendo exactamente qué salió mal y dónde.
:::

---

## Editando Celdas

### Modificar el Código

Podés modificar cualquier celda para experimentar:

1. **Seleccioná la celda** (clic sobre ella)
2. **Entrá en modo edición** (Enter o doble clic)
3. **Modificá el código**
4. **Ejecutá nuevamente** (Shift + Enter)

**Ejemplo**: Cambiá este código:

```python
nombre = "María"
print(f"Hola, {nombre}")
```

Por este:

```python
nombre = "Tu Nombre"  # ¡Poné tu nombre aquí!
print(f"Hola, {nombre}")
```

:::{tip} Experimentar es Clave
**No tengas miedo de modificar el código**. La mejor forma de aprender es experimentando. Si algo sale mal, siempre podés volver a la versión original.
:::

### Crear una Nueva Celda

Para agregar tu propio código:

**Opción 1**: Usando botones
- Hacé clic en el botón **➕** en la barra de herramientas

**Opción 2**: Usando teclado (en modo comando)
- Presioná `A` para insertar una celda **arriba** (Above)
- Presioná `B` para insertar una celda **abajo** (Below)

**[CAPTURA: Barra de herramientas con el botón "+" (agregar celda) claramente resaltado, y al lado el indicador de teclado mostrando las teclas "A" y "B".]**

### Eliminar una Celda

Si querés eliminar una celda:

**Opción 1**: Usando el menú
- `Edit` → `Delete Cells`

**Opción 2**: Usando teclado (en modo comando)
- Presionar `D` dos veces (D, D)

:::{warning} Cuidado al Eliminar
Al eliminar una celda, **no hay confirmación**. Si eliminaste algo por error, presioná `Ctrl + Z` inmediatamente para deshacer.
:::

### Cambiar el Tipo de Celda

Para cambiar entre código y texto:

**Opción 1**: Menú desplegable en la barra de herramientas
- Seleccioná `Code` o `Markdown`

**Opción 2**: Atajos de teclado (en modo comando)
- `Y` para convertir a celda de **código**
- `M` para convertir a celda de **Markdown** (texto)

**[CAPTURA: Menú desplegable mostrando las opciones "Code", "Markdown", y "Raw" con "Code" seleccionado.]**

---

## Guardando Tu Trabajo

Es importante guardar tu progreso regularmente.

### Guardar el Notebook

**Opción 1**: Atajo de teclado
- `Ctrl + S` (Windows/Linux)
- `Cmd + S` (Mac)

**Opción 2**: Menú
- `File` → `Save Notebook`

**Opción 3**: Botón
- Icono de disquete 💾 en la barra de herramientas

**[CAPTURA: Tres formas de guardar mostradas visualmente: 1) Teclado con Ctrl+S resaltado, 2) Menú File con Save Notebook resaltado, 3) Icono de disquete en la barra de herramientas.]**

:::{important} Guardado Automático
JupyterLab guarda automáticamente tu trabajo cada pocos minutos, pero es buena práctica **guardar manualmente** después de cambios importantes.
:::

### Indicador de Guardado

En la pestaña del notebook verás:
- **Punto negro (●)** al lado del nombre: hay cambios sin guardar
- **Sin punto**: todo guardado correctamente

**[CAPTURA: Dos pestañas de notebook mostrando: 1) "ejercicio_1.ipynb ●" con el punto indicando cambios sin guardar, 2) "ejercicio_1.ipynb" sin punto después de guardar.]**

---

## El Kernel de Python

El **kernel** es el "motor" que ejecuta tu código Python. Es importante entender cómo funciona.

### ¿Qué es el Kernel?

Pensá en el kernel como un intérprete de Python que está corriendo en segundo plano. Cuando ejecutás una celda, el kernel:

1. Recibe tu código
2. Lo ejecuta
3. Te devuelve el resultado

```{figure} 7/kernel_funcionamiento.svg
:label: fig-kernel
:align: center
:width: 80%

Funcionamiento del kernel: ciclo de ejecución entre el notebook y el intérprete Python
```

**[NOTA SVG: Crear diagrama de flujo circular mostrando: Usuario → Celda de código → Kernel (con logo Python) → Resultado → Usuario. Incluir flechas indicando el flujo y etiquetas en cada paso.]**

### Estado del Kernel

El kernel **mantiene la memoria** de todo lo ejecutado. Por ejemplo:

**Celda 1**:
```python
x = 10
```

**Celda 2** (ejecutada después):
```python
print(x)  # Imprime: 10
```

El kernel "recuerda" que `x = 10` incluso en celdas separadas.

:::{important} Orden de Ejecución
El kernel recuerda el **orden en que ejecutaste** las celdas, no el orden en que están escritas. El número `In [n]:` te indica esto.
:::

### Reiniciar el Kernel

A veces necesitás "empezar de cero". Reiniciar el kernel **borra toda la memoria**.

**Cuándo reiniciar:**
- 🔄 Querés empezar desde el principio
- 🐛 Hay comportamientos extraños
- 🚫 El código se quedó "colgado"

**Cómo reiniciar:**

**Opción 1**: Menú
- `Kernel` → `Restart Kernel...`

**Opción 2**: Botón
- Icono de reinicio ⟳ en la barra de herramientas

**[CAPTURA: Menú Kernel desplegado mostrando las opciones: "Restart Kernel", "Restart Kernel and Clear Outputs", "Restart Kernel and Run All Cells".]**

:::{tip} Restart and Run All
La opción más útil suele ser **"Restart Kernel and Run All Cells"**: reinicia todo y ejecuta todas las celdas en orden desde el principio. Perfecto para verificar que tu código funcione correctamente.
:::

### Interrumpir la Ejecución

Si una celda está tardando demasiado o entró en un lazo infinito:

**Opción 1**: Botón
- Icono de detener ⏹️ en la barra de herramientas

**Opción 2**: Menú
- `Kernel` → `Interrupt Kernel`

**Opción 3**: Atajo
- Presionar `I, I` (la letra I dos veces en modo comando)

**[CAPTURA: Celda ejecutándose con "In [*]:" y el símbolo de ocupado visible, con una flecha señalando el botón de stop en la barra de herramientas.]**

---

## Trabajando con Múltiples Notebooks

Podés tener varios notebooks abiertos al mismo tiempo.

### Abrir Múltiples Archivos

Simplemente hacé doble clic en varios archivos `.ipynb`. Cada uno se abrirá en una pestaña nueva.

**[CAPTURA: Área de trabajo mostrando 3 pestañas abiertas con diferentes notebooks: "01_variables.ipynb", "02_operadores.ipynb", "03_control.ipynb".]**

### Cambiar entre Pestañas

- **Clic** en la pestaña para cambiar
- `Ctrl + Shift + [` y `Ctrl + Shift + ]` para navegar entre pestañas

### Organizar la Pantalla

Podés ver dos notebooks lado a lado:

1. **Arrastrá** la pestaña de un notebook hacia un costado
2. Se dividirá la pantalla
3. Soltá la pestaña

**[CAPTURA: Vista de pantalla dividida mostrando dos notebooks abiertos lado a lado, con una línea divisoria en el medio que se puede arrastrar.]**

:::{tip} Comparar Código
Esto es muy útil para comparar tu solución con el ejemplo, o trabajar con dos ejercicios relacionados al mismo tiempo.
:::

---

## Atajos de Teclado Esenciales

Dominar estos atajos te hará **mucho más eficiente**.

### Atajos Universales

| Atajo | Acción |
|-------|--------|
| `Ctrl + S` | Guardar notebook |
| `Ctrl + Z` | Deshacer |
| `Ctrl + Shift + Z` | Rehacer |
| `Ctrl + F` | Buscar en el notebook |

### Atajos en Modo Comando (Azul)

| Atajo | Acción |
|-------|--------|
| `Enter` | Entrar a modo edición |
| `A` | Insertar celda arriba |
| `B` | Insertar celda abajo |
| `D, D` | Eliminar celda |
| `M` | Convertir a Markdown |
| `Y` | Convertir a código |
| `↑/↓` | Navegar entre celdas |
| `Shift + ↑/↓` | Seleccionar múltiples celdas |

### Atajos en Modo Edición (Verde)

| Atajo | Acción |
|-------|--------|
| `Esc` | Salir a modo comando |
| `Ctrl + Enter` | Ejecutar celda (quedarse en ella) |
| `Shift + Enter` | Ejecutar celda (ir a la siguiente) |
| `Alt + Enter` | Ejecutar y crear nueva abajo |
| `Tab` | Autocompletar código |
| `Shift + Tab` | Ver documentación |

:::{tip} Hoja de Referencia
Presioná `Ctrl + Shift + C` para ver **todos** los atajos disponibles. No necesitás memorizarlos todos: los más comunes los aprenderás naturalmente con el uso.
:::

---

## Funciones Útiles de JupyterLab

### Autocompletado de Código

Mientras escribís código, presioná `Tab` y JupyterLab te sugerirá opciones:

```python
# Escribí "pri" y presioná Tab
pri[Tab] → print()
```

**[CAPTURA: Celda mostrando el menú de autocompletado emergente con sugerencias como "print", "print()", "property", mientras el usuario escribe código.]**

:::{tip} Explorar Métodos
Si tenés una variable y querés ver qué métodos tiene, escribí el nombre, un punto, y presioná Tab:
```python
lista = [1, 2, 3]
lista.[Tab]  # Te muestra: append, remove, sort, etc.
```
:::

### Ver Documentación

Para ver información sobre una función:

1. Poné el cursor sobre el nombre de la función
2. Presioná `Shift + Tab`
3. Verás un popup con la documentación

**[CAPTURA: Popup de documentación mostrando información sobre la función print(), incluyendo su firma, parámetros y descripción.]**

Presionar `Shift + Tab` **varias veces** expande la documentación.

### Buscar en el Notebook

Para buscar texto en tu notebook:

1. Presioná `Ctrl + F`
2. Aparecerá una barra de búsqueda
3. Escribí lo que buscás
4. Usá las flechas para navegar entre resultados

**[CAPTURA: Barra de búsqueda en la parte superior del notebook con un término buscado y resaltado en amarillo en las celdas.]**

---

## Buenas Prácticas

Seguir estas recomendaciones te ayudará a aprovechar mejor JupyterLab:

### 1. Ejecutá las Celdas en Orden

:::{important} Orden Secuencial
Aunque podés ejecutar las celdas en cualquier orden, lo mejor es ejecutarlas **de arriba hacia abajo** siguiendo la secuencia. Esto evita confusiones con variables no definidas.
:::

**Mala práctica:**
```python
# Celda 2 (ejecutás primero)
print(x)  # Error: x no está definida

# Celda 1 (ejecutás después)
x = 10
```

**Buena práctica:**
```python
# Celda 1 (ejecutás primero)
x = 10

# Celda 2 (ejecutás después)
print(x)  # Funciona correctamente
```

### 2. Reiniciá y Ejecutá Todo Regularmente

Cada tanto, es buena idea:
1. `Kernel` → `Restart Kernel and Run All Cells`
2. Verificar que todo funcione en orden

Esto asegura que tu notebook funciona correctamente de principio a fin.

### 3. Guardá Frecuentemente

Acostumbrate a presionar `Ctrl + S` regularmente. No esperes a terminar todo para guardar.

### 4. Documentá Tu Código

Usá celdas de Markdown para:
- ✍️ Explicar qué hace tu código
- 📝 Anotar dudas o ideas
- 🎯 Describir el objetivo de cada ejercicio

```python
# Bueno: Código con comentarios explicativos
edad = 25  # Edad del usuario en años
es_mayor = edad >= 18  # Verificar si es mayor de edad
```

### 5. Mantené las Celdas Cortas

En lugar de una celda gigante:

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

### 6. Limpiá los Outputs Antiguos

Si tu notebook tiene muchos resultados viejos:
- `Edit` → `Clear All Outputs`
- Esto reduce el tamaño del archivo y lo hace más limpio

---

## Solución de Problemas Comunes

### Problema: El Kernel No Responde

**Síntomas:** La celda muestra `In [*]:` por mucho tiempo

**Soluciones:**
1. Esperar unos segundos (puede ser un cálculo lento)
2. Interrumpir el kernel (botón ⏹️)
3. Si persiste, reiniciar el kernel

### Problema: Variables No Definidas

**Error:** `NameError: name 'x' is not defined`

**Causa:** La celda que define `x` no fue ejecutada

**Solución:**
1. Buscá la celda donde se define la variable
2. Ejecutala
3. Volvé a ejecutar la celda con error

:::{tip} Restart and Run All
Si no estás seguro qué se ejecutó y qué no, hacé `Restart Kernel and Run All Cells`.
:::

### Problema: Cambios No Guardados

**Síntomas:** Ves el punto negro (●) en la pestaña

**Solución:**
- Presioná `Ctrl + S` para guardar

### Problema: El Notebook Se Ve Raro

**Síntomas:** Formato extraño, celdas que no se ven bien

**Soluciones:**
1. Refrescar la página (F5)
2. Cerrar y volver a abrir el notebook
3. Limpiar la caché del navegador

### Problema: No Encuentro un Archivo

**Soluciones:**
1. Verificá que estás en el directorio correcto
2. Usá la barra de búsqueda del file browser
3. Revisá que el archivo tenga extensión `.ipynb`

---

## Consejos para Estudiantes

### Estrategia de Aprendizaje

:::{tip} Método de Estudio con Notebooks
1. **Primera pasada:** Leé todas las celdas sin ejecutar
2. **Segunda pasada:** Ejecutá cada celda y observá los resultados
3. **Tercera pasada:** Modificá el código y experimentá
4. **Práctica:** Resolvé los ejercicios en un nuevo notebook
:::

### Cómo Experimentar

Los notebooks son **perfectos para experimentar**:

```python
# Original
nombre = "Ana"
print(nombre)
```

**Experimento 1:** ¿Qué pasa si cambio el valor?
```python
nombre = "Carlos"
print(nombre)
```

**Experimento 2:** ¿Puedo usar números?
```python
nombre = 123
print(nombre)
```

**Experimento 3:** ¿Qué pasa si lo dejo vacío?
```python
nombre = ""
print(nombre)
```

:::{important} Aprender Haciendo
La programación se aprende **experimentando**. No tengas miedo de probar cosas nuevas. Si rompe algo, simplemente reiniciá el kernel y empezá de nuevo.
:::

### Tomar Notas Personales

Usá celdas de Markdown para tus propias notas:

```markdown
### Mis Notas - Variables

- Las variables son como "cajas" que guardan valores
- No hace falta declararlas antes de usarlas
- Puedo cambiar su valor cuando quiera

**Duda:** ¿Puedo usar espacios en los nombres? → Probar
```

### Trabajar con Ejercicios

Cuando trabajes en ejercicios:

1. **Leé** el enunciado completo
2. **Pensá** la solución antes de escribir código
3. **Escribí** tu código en una nueva celda
4. **Ejecutá** y probá con diferentes valores
5. **Compará** con la solución propuesta (si hay)

---

## Recursos Adicionales

### Documentación Oficial

- [JupyterLab Documentation](https://jupyterlab.readthedocs.io/)
- [Jupyter Notebook Tutorial](https://jupyter-notebook.readthedocs.io/)

### Atajos de Teclado

Descargá una hoja de referencia de atajos:
- Dentro de JupyterLab: `Help` → `Keyboard Shortcuts`
- O presioná `Ctrl + Shift + C`

### Videos Tutoriales

Si preferís aprender viendo:
- Buscá "JupyterLab tutorial español" en YouTube
- Hay excelentes tutoriales visuales

---

## Resumen y Checklist

¡Felicitaciones! Ya conocés los conceptos básicos de JupyterLab. Usá este checklist para verificar que dominás las habilidades esenciales:

### ✅ Checklist de Habilidades

Marcá lo que ya sabés hacer:

#### Navegación Básica
- [ ] Acceder a JupyterLab en el navegador
- [ ] Navegar por el explorador de archivos
- [ ] Abrir un notebook existente
- [ ] Identificar los componentes de la interfaz

#### Trabajo con Celdas
- [ ] Diferenciar celdas de código y Markdown
- [ ] Seleccionar una celda
- [ ] Cambiar entre modo comando y edición
- [ ] Ejecutar una celda de código
- [ ] Crear una nueva celda
- [ ] Eliminar una celda

#### Ejecución de Código
- [ ] Ejecutar código Python básico
- [ ] Leer mensajes de error
- [ ] Modificar código y volver a ejecutar
- [ ] Ver los resultados (output)

#### Gestión del Kernel
- [ ] Entender qué es el kernel
- [ ] Reiniciar el kernel
- [ ] Ejecutar todas las celdas
- [ ] Interrumpir una ejecución

#### Productividad
- [ ] Guardar el notebook
- [ ] Usar autocompletado (Tab)
- [ ] Ver documentación (Shift + Tab)
- [ ] Usar al menos 3 atajos de teclado

#### Buenas Prácticas
- [ ] Ejecutar celdas en orden
- [ ] Documentar mi código
- [ ] Experimentar con modificaciones
- [ ] Buscar soluciones a errores comunes

:::{tip} Práctica Continua
No te preocupes si no dominás todo inmediatamente. Estas habilidades se desarrollan con la práctica. **Cada vez que uses JupyterLab, te sentirás más cómodo.**
:::

---

## ¡A Programar!

Ya tenés todo lo necesario para empezar a trabajar con los notebooks de práctica. Recordá:

1. 🎯 **Empezá con calma**: No intentes aprender todo de una vez
2. 🔬 **Experimentá**: Probá, modificá, rompé cosas (y arreglalas)
3. 🐛 **Los errores son buenos**: Cada error es una oportunidad de aprender
4. 💪 **Practicá regularmente**: Mejor 30 minutos diarios que 3 horas una vez
5. ❓ **Preguntá**: Si no entendés algo, buscá ayuda

:::{note} Acceso a los Notebooks
Recordá que los notebooks de práctica están en:
```
https://ingcom-unrn.github.io/jupyterlite/lab/index.html
```
¡Guardate este link en favoritos!
:::

---

## Próximos Pasos

Una vez que domines JupyterLab, estás listo para:

1. 📗 **Capítulo 1**: Fundamentos de Python
   - Variables y tipos de datos
   - Operadores
   - Entrada y salida

2. 📘 **Capítulo 2**: Control de Flujo
   - Condicionales (if/else)
   - Lazos (while/for)
   - Comprensiones

3. 📙 **Y seguir adelante** con los demás capítulos

:::{important} ¡Éxito en Tu Aprendizaje!
Cada programador experto comenzó exactamente donde estás vos ahora. Lo que los distingue es la **práctica constante** y la **curiosidad**. ¡Vos también podés lograrlo!
:::

---

**¿Listo para empezar?** Abrí tu primer notebook y ¡escribí tu primera línea de código Python! 🐍✨

---

(glosario-jupyterlab)=
## Glosario de Terminología 📖

Este glosario contiene los términos clave sobre JupyterLab y notebooks interactivos que se trataron en este capítulo.

:::{admonition} 💡 Cómo usar este glosario
:class: tip

- **Consultalo cuando encuentres un término nuevo**
- Los términos pueden referenciarse con {term}`término` en el texto
- Incluye terminología de entornos interactivos y notebooks
- **Ideal para cuando empieces a usar JupyterLab**
:::

```{glossary}
JupyterLab
  Entorno de desarrollo interactivo basado en web que permite escribir y ejecutar código Python en {term}`notebooks <notebook>`. Interfaz moderna que combina código, texto, visualizaciones y resultados. Sucesor de Jupyter Notebook.

Jupyter
  Proyecto open source que desarrolla herramientas para computación interactiva. Incluye {term}`JupyterLab`, Jupyter Notebook y JupyterHub. Nombre viene de Julia, Python y R (lenguajes principales).

JupyterLite
  Versión de {term}`JupyterLab` que funciona completamente en el navegador sin servidor. No requiere instalación. Usa WebAssembly para ejecutar Python en el navegador. Ideal para educación.

Notebook
Cuaderno
  Documento interactivo que combina {term}`celdas <celda>` de código ejecutable, texto explicativo (Markdown), y resultados/visualizaciones. Extensión `.ipynb` (IPython Notebook). También conocido como **cuaderno**.

Celda
Cell
  Unidad básica de un {term}`notebook`. Puede ser de {term}`código` (ejecutable) o {term}`Markdown` (texto). Se ejecutan individualmente con Shift+Enter. También conocida como **cell** en inglés.

Celda de código
Code cell
  {term}`Celda` que contiene código Python ejecutable. Al ejecutarla, muestra el resultado debajo. Identificable por `In [ ]:` a la izquierda. Puede tener múltiples líneas.

Celda de Markdown
Markdown cell
  {term}`Celda` que contiene texto con formato usando {term}`Markdown`. Se renderiza como HTML al ejecutarla. Útil para explicaciones, títulos, listas. No ejecuta código.

Markdown
  Lenguaje de marcado ligero para dar formato a texto. Usa símbolos simples: `#` para títulos, `**negrita**`, `*cursiva*`, `- lista`. Se convierte a HTML. Fácil de leer y escribir.

Kernel
  Proceso que ejecuta el código en un {term}`notebook`. Mantiene el estado (variables, funciones definidas). Python tiene su propio kernel. Puede reiniciarse si hay problemas.

Reiniciar kernel
Restart kernel
  Detener y volver a iniciar el {term}`kernel`, limpiando toda la memoria. Todas las variables y funciones se pierden. Útil cuando hay errores o para empezar de cero.

Modo comando
Command mode
  Modo de {term}`notebook` para navegar y manipular celdas. Borde azul en la celda activa. Atajos: `A` (insertar arriba), `B` (insertar abajo), `DD` (borrar), `M` (Markdown), `Y` (código).

Modo edición
Edit mode
  Modo de {term}`notebook` para editar contenido de una celda. Borde verde en la celda activa. Atajos normales de editor. Entrar: presionar `Enter`. Salir: presionar `Esc`.

Ejecutar celda
Run cell
  Procesar el contenido de una {term}`celda`. En celdas de código, ejecuta el código y muestra resultado. En Markdown, renderiza el texto. Atajo: `Shift+Enter` (ejecuta y avanza).

Output
Salida
  Resultado que aparece debajo de una {term}`celda de código` después de ejecutarla. Puede ser texto, números, gráficos, errores. Se guarda en el {term}`notebook`. También conocida como **salida**.

In [ ]
  Indicador a la izquierda de una {term}`celda de código`. Muestra número de ejecución. `In [ ]` = no ejecutada, `In [1]` = primera ejecución, `In [*]` = ejecutando.

Out[ ]
  Indicador del {term}`output` de una celda. `Out[1]` corresponde a `In [1]`. No todas las celdas tienen output (ej: asignaciones). Solo aparece si hay valor de retorno.

File Browser
Explorador de archivos
  Panel lateral izquierdo de {term}`JupyterLab` que muestra directorios y archivos. Permite navegar, crear, renombrar, eliminar archivos. Similar al explorador de Windows/Finder.

Área de trabajo
Workspace
Main area
  Zona central de {term}`JupyterLab` donde se abren {term}`notebooks <notebook>`, archivos, terminales. Puede tener múltiples pestañas. Arrastrar pestañas divide la pantalla.

Launcher
Lanzador
  Pantalla inicial de {term}`JupyterLab` para crear nuevos {term}`notebooks <notebook>`, archivos, consolas, terminales. Aparece al abrir JupyterLab o cerrar todas las pestañas.

.ipynb
  Extensión de archivos de {term}`notebook` Jupyter. Significa "IPython Notebook". Es un archivo JSON que guarda celdas, código, outputs y metadata. Formato estándar de Jupyter.

IPython
  Shell interactivo mejorado de Python. Base del {term}`kernel` de Jupyter. Agrega funcionalidades: autocompletado, magic commands, historial. "Interactive Python".

Magic Command
Comando mágico
  Comandos especiales de {term}`IPython` que empiezan con `%` (línea) o `%%` (celda). Ejemplos: `%timeit`, `%matplotlib inline`, `%%bash`. Funciones útiles pre-construidas.

Autocompletado
Autocomplete
  Funcionalidad que sugiere completar código mientras escribís. Presionar `Tab` muestra opciones. Ahorra tiempo y evita errores de tipeo. Funciona con variables, funciones, métodos.

Introspección
  Examinar propiedades de un objeto en Python. En Jupyter: `objeto?` muestra documentación, `objeto??` muestra código fuente. `Tab` después de `objeto.` muestra métodos/atributos.

Shift+Enter
  Atajo de teclado principal en {term}`notebooks <notebook>`. Ejecuta la {term}`celda` actual y avanza a la siguiente (o crea una nueva). El más usado en Jupyter.

Ctrl+Enter
  Atajo para ejecutar {term}`celda` actual SIN avanzar a la siguiente. Útil cuando querés ejecutar la misma celda múltiples veces seguidas.

Alt+Enter
  Atajo para ejecutar {term}`celda` actual e insertar una nueva celda vacía debajo. Útil para flujo de trabajo rápido al crear notebooks nuevos.

Checkpoint
Punto de guardado
  Copia de seguridad automática del {term}`notebook` en cierto momento. JupyterLab guarda periódicamente. Puede revertir a checkpoints anteriores desde menú File.

Exportar notebook
Export
  Convertir un {term}`notebook` a otros formatos. Opciones: HTML, PDF, Python (.py), Markdown, LaTeX. Útil para compartir o crear documentos estáticos.

Variable inspector
  Herramienta (extensión) que muestra todas las variables activas en el {term}`kernel` con sus valores y tipos. Útil para debugging. No siempre está disponible en todas las instalaciones.

Terminal
  Consola de sistema operativo integrada en {term}`JupyterLab`. Permite ejecutar comandos shell (bash, cmd). Útil para instalar paquetes, git, operaciones de archivos.

Console
Consola
  Shell interactivo de Python integrado en {term}`JupyterLab`. Similar a ejecutar `python` en terminal. Útil para pruebas rápidas sin crear {term}`notebook`. También conocida como **consola**.

Tab
Pestaña
  Documento abierto en el {term}`área de trabajo` de JupyterLab. Puede ser {term}`notebook`, archivo, terminal, consola. Múltiples tabs permiten trabajar con varios archivos simultáneamente.

Widget interactivo
Interactive widget
  Elemento de interfaz gráfica en {term}`notebook` (botones, sliders, dropdowns). Permite interacción sin editar código. Requiere biblioteca `ipywidgets`. Útil para visualizaciones dinámicas.

Extensión
Extension
  Plugin que agrega funcionalidades a {term}`JupyterLab`. Ejemplos: temas, linters, debuggers, variable inspectors. Se instalan con `pip` o desde el navegador de extensiones.

Kernel ocupado
Kernel busy
  Estado del {term}`kernel` cuando está ejecutando código. Indicador en esquina superior derecha (círculo lleno). No se pueden ejecutar otras celdas hasta que termine.

Kernel inactivo
Kernel idle
  Estado del {term}`kernel` cuando no está ejecutando nada. Indicador en esquina superior derecha (círculo vacío). Listo para ejecutar código.

Debugger
Depurador
  Herramienta para encontrar errores ejecutando código paso a paso. JupyterLab tiene debugger visual integrado. Permite inspeccionar variables, establecer breakpoints, ver stack.

Breakpoint
Punto de interrupción
  Marcador en código donde el {term}`debugger` pausará la ejecución. Permite inspeccionar estado del programa en ese punto. Se establece en el margen izquierdo de la celda.

Linter
  Herramienta que analiza código en busca de errores de estilo y posibles bugs sin ejecutarlo. Ejemplo: flake8, pylint. Algunas extensiones integran linters en JupyterLab.
```

:::{tip} Referencias cruzadas
Este glosario complementa los glosarios de programación Python de los capítulos anteriores, enfocándose en la herramienta JupyterLab.
:::

:::{admonition} Glosarios relacionados
:class: seealso

**Glosarios de Python:**
- {ref}`glosario-fundamentos` - Variables, tipos, operadores
- {ref}`glosario-control-flujo` - Condicionales, bucles, patrones
- {ref}`glosario-estructuras` - Listas, diccionarios, sets
- {ref}`glosario-funciones` - def, return, scope, parámetros
- {ref}`referencia-tipos` - import, archivos, módulos
- {ref}`glosario-excepciones` - try-except, raise, manejo de errores

**Este glosario complementa** la terminología de Python con conceptos específicos de entornos interactivos y notebooks.
:::

---

**Fin del Capítulo 7 - Guía de JupyterLab**
