---
title: Guía de uso de JupyterLab
short_title: E - JupyterLab
subtitle: Introducción práctica a JupyterLab para estudiantes principiantes
---

## Introducción

¡Bienvenido a tu primera experiencia con **JupyterLab**! Esta guía está diseñada para que puedas comenzar a trabajar con los cuadernos de práctica sin complicaciones. No te preocupes si nunca programaste antes: vamos a ver todo paso a paso.

:::{note} ¿Qué es JupyterLab?
**JupyterLab** es un entorno de desarrollo interactivo que te permite escribir y ejecutar código Python directamente en tu navegador web. Funciona como un “cuaderno digital” donde podés combinar código, texto explicativo y resultados en un mismo lugar.
:::

En este curso, vas a usar una versión especial de JupyterLab llamada **JupyterLite**, que funciona completamente en tu navegador sin necesidad de instalar nada en tu computadora.

:::{tip} Ventajas de JupyterLab
- ✅ **No necesitás instalar nada**: Todo funciona en el navegador
- ✅ **Inmediato**: Ves los resultados al instante
- ✅ **Interactivo**: Podés modificar el código y probar
- ✅ **Visual**: Perfecto para aprender y experimentar
:::

:::{warning} Acceso a los archivos

Por como está armado este entorno de programación, nosotros no tenemos acceso de ningún tipo a los cambios que hagan en los cuadernos, por lo que es necesario que, si quieren compartirlos o guardarlos, lo hagan por fuera de la herramienta. Esto también significa que ustedes deben descargar los cuadernos y hacerles backup, ya que esta información está en su computadora.

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

```{figure} ./E_jupyterlab/loading.png
:label: jupyterlab_loading
:alt: Captura: Pantalla de carga de JupyterLab
:align: center
Pantalla de carga de JupyterLab
```

:::{note} Primera Carga
La primera carga puede demorar un poco más porque está descargando los archivos necesarios. Las siguientes veces será mucho más rápido.
:::

---

## Configuración previa

Completamente opcional, pero si se sienten más cómodos pueden cambiar el idioma de la interfaz a español, aunque no cambia todo, los puede ayudar a que la herramienta no sea tan dura.

En la barra de menú, buscamos "Settings"

```{figure} ./E_jupyterlab/cambio_idioma_1.png
:label: jupyterlab_cambio_idioma_1
:alt: CAPTURA: Vista completa de la interfaz
:align: center
Menú "Settings"
```

Y después "Language", para elegir "Spanish"

```{figure} ./E_jupyterlab/cambio_idioma_2.png
:label: jupyterlab_cambio_idioma_2
:alt: CAPTURA: Vista completa de la interfaz
:align: center
Y elegimos español.
```

## La Interfaz de JupyterLab

Una vez que cargue completamente, verás la interfaz principal de JupyterLab. Vamos a conocer cada parte:

```{figure} ./E_jupyterlab/principal.png
:label: jupyterlab_principal
:alt: CAPTURA: Vista completa de la interfaz
:align: center
Vista completa de la interfaz de JupyterLab
```

### Componentes Principales

La interfaz de JupyterLab se divide en varias áreas:

```{figure} ./E_jupyterlab/principal_anotado.png
:label: fig-interfaz-jupyterlab
:align: center
:width: 100%

Componentes principales de la interfaz de JupyterLab
```

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

```{figure} ./E_jupyterlab/panel_izquierdo.png
:label: fig-jupyterlab-panel-izquierdo
:alt: CAPTURA: Panel lateral izquierdo
:align: center
Panel lateral izquierdo mostrando la estructura de carpetas con los archivos en el espacio de trabajo.
```

Acá vas a ver:
- 📁 **Carpetas**: Organizan los notebooks y otros archivos.
- 📓 **Notebooks** (archivos `.ipynb`): Los cuadernos de práctica
- 📄 **Documentos Markdown** (archivos `.md`): Para apuntes y textos con formato.
- 📄 **Otros archivos**: Datos, imágenes, etc.

#### 3. Área de Trabajo Central

Esta es el área más importante. Aquí es donde abrirás y trabajarás con tus notebooks. Podés tener múltiples notebooks abiertos al mismo tiempo, organizados en pestañas.

Apenas abrimos JupyterLab, veremos el Lanzador, que contiene los atajos para crear archivos nuevos (y vacíos):

```{figure} ./E_jupyterlab/lanzador.png
:label: fig-jupyterlab-lanzador
:alt: CAPTURA: Lanzador
:align: center
El lanzador contiene los atajos para crear los tipos de archivos conocidos por JupyterLab
```


Jupyterlab admite reorganizar la vista, solo tenés que arrastrar la ficha con el archivo abierto y acomodarlo donde quieras; podés dejar varios archivos abiertos al mismo tiempo.

```{figure} ./E_jupyterlab/area_trabajo.png
:label: fig-jupyterlab-area-trabajo
:alt: CAPTURA: Espacio de trabajo principal
:align: center
Espacio de trabajo organizado con dos archivos abiertos simultaneamente.
```

#### 4. Barra de Estado Inferior

Muestra información útil como:
- El kernel que está ejecutándose (Python)
- Estado de la conexión
- Información del archivo actual

```{figure} ./E_jupyterlab/barra_estado.png
:label: fig-jupyterlab-barra-estado
:alt: CAPTURA: Barra de estado
:align: center
Barra de estado del espacio de trabajo.
```

---

## Navegando por los Archivos

### Explorando las Carpetas

En el panel lateral izquierdo, verás una estructura organizada con los cuadernos.

Para navegar, solo es necesario **Hacer doble clic en un archivo** para abrirlo.

```{figure} ./E_jupyterlab/panel_izquierdo_detalle.png
:label: fig-jupyterlab-panel-izquierdo-detalle
:alt: CAPTURA: Panel lateral izquierdo, detalle en la ruta y botones
:align: center
Detalle de la barra de botones del panel izquierdo.
```

De este panel podemos ver, de arriba hacia abajo:

1. En azul, el botón para abrir el lanzador (para crear archivos o consolas)
2. Un botón para crear directorios.
3. Un botón para subir archivos al espacio de trabajo.
4. Un botón para recargar la vista (por si tenemos más de una ventana abierta con los cuadernos)
5. Un botón para filtrar la lista de archivos.
6. La barra de direcciones de directorios, el botón de 'carpeta' es la raíz.
7. El listado de archivos en la ubicación actual, indicada por 6.

Cuando abrimos un directorio, vamos a ver que la barra de direcciones (6) cambia, podemos hacer click en el primer botón para volver a la raíz.

:::{tip} Organización
Los cuadernos están organizados siguiendo el orden del apunte. Te recomendamos trabajarlos en secuencia:
- `01_fundamentos.ipynb` → Empezá por acá
- `02_control_flujo.ipynb`
- `03_estructuras.ipynb`
- `04_funciones.ipynb`
:::

### Abrir un Notebook

Para abrir tu primer notebook:

1. En el panel izquierdo, buscá la carpeta correspondiente
2. Hacé **doble clic** sobre el archivo `.ipynb` que querés abrir
3. El notebook se abrirá en el área central


```{figure} ./E_jupyterlab/cuaderno_abierto.png
:label: fig-jupyterlab-cuaderno-abierto
:alt: CAPTURA: Panel lateral izquierdo, con un archivo seleccionado y este mismo abierto
:align: center
Un cuaderno seleccionado y abierto.
```

:::{note} Extensión .ipynb
Los notebooks de Jupyter tienen la extensión `.ipynb` (Interactive Python Notebook). Estos archivos contienen código, texto y resultados juntos.
:::

### Abriendo un archivo Markdown

Si no indicamos nada, al hacer doble click en un documento de este tipo, será abierto para su modificación y solo veremos el "código" con el que está hecho. Si no lo queremos modificar y lo queremos ver en su representación final, lo tenemos que abrir en su 'vista previa.

```{figure} ./E_jupyterlab/vista_edicion_md.png
:label: fig-jupyterlab-vista-edicion_md
:alt: CAPTURA: Como se ve un archivo markdown abierto directamente
:align: center
Un archivo markdown abierto con doble click
```

Para verlo "bonito" tenemos que ubicar el archivo en el panel izquierdo, y darle botón derecho:

```{figure} ./E_jupyterlab/abrir_como.png
:label: fig-jupyterlab-abrir-como
:alt: CAPTURA: En el panel lateral izquierdo, botón derecho sobre un archivo un archivo.
:align: center
Abrir en modo "Vista previa"
```

Y lo podremos ver en su "vista previa", que transforma el [código markdown](./G_markdown.md) en el formato apropiado.

```{figure} ./E_jupyterlab/vista_previa_md.png
:label: fig-jupyterlab-vista-previa-md
:alt: CAPTURA: Como se ve un archivo markdown abierto con la vista previa.
:align: center
Un archivo markdown abierto con botón derecho
```



---

## Anatomía de un Notebook

Una vez abierto un notebook, verás que está compuesto por **celdas**. Cada celda puede contener código Python o texto explicativo.

### La barra de herramientas del espacio de trabajo

El espacio de trabajo tiene unos accesos directos para manipular las celdas del cuaderno.

```{figure} ./E_jupyterlab/toolbar_left.png
:label: fig-jupyterlab-toolbar-left
:alt: CAPTURA: Parte izquierda de la barra de herramientas del espacio de trabajo
:align: center
Parte izquierda de la barra de herramientas del espacio de trabajo
```

De izquierda a derecha, los botones son:

1. **💾 Guardar cuaderno**: Graba los cambios en tu navegador (equivalente a Ctrl+S)
2. **➕ Agregar celda**: Inserta una nueva celda debajo de la actual
3. **✂️ Cortar**: Corta la celda seleccionada (puedes pegarla en otro lugar)
4. **📋 Copiar**: Copia la celda seleccionada sin eliminarla
5. **📄 Pegar**: Pega la celda cortada o copiada debajo de la actual
6. **▶️ Ejecutar celda**: Corre el código de la celda actual o renderiza el Markdown
7. **⏹️ Detener ejecución**: Interrumpe un código que está corriendo (útil si se colgó)
8. **🔄 Reiniciar Núcleo**: Reinicia Python desde cero, borrando todas las variables de memoria
9. **⏩ Ejecutar todas las celdas**: Ejecuta todas las celdas del notebook de arriba hacia abajo
10. **📝 Tipo de celda**: Cambia entre Code (código Python), Markdown (texto con formato) o Raw (texto plano)
11. **⬇️ Descargar cuaderno**: Descarga el archivo .ipynb a tu computadora

### Tipos de Celdas

```{figure} ./E_jupyterlab/cuaderno.png
:label: fig-jupyterlab-cuaderno
:alt: CAPTURA: Cuaderno abierto en el espacio de trabajo
:align: center
Cuaderno abierto en el espacio de trabajo con celdas de texto y código.
```

#### Celdas de Markdown (Texto)

Contienen texto explicativo, títulos, listas, etc. Se usan para documentar y explicar el código.

Características:
- 📝 No se ejecutan como código
- 📄 Soportan formato: **negritas**, *cursivas*, títulos, listas
- 🔗 Pueden incluir enlaces y fórmulas matemáticas

Para modificar una celda de este tipo, es necesario hacer doble click en la misma, que pasará a verse como la segunda celda de la captura. Cuando terminamos de modificarla, es necesario "ejecutar" para que esta se transforme en la representación visual final como está en la primera celda con el botón ▶️ o con "Shift + Enter".

Los encabezados jerárquicos (que se crean con `#`) permiten que el documento tenga una estructura.

#### Celdas de Código

Contienen código Python que podés ejecutar.

Características:
- 💻 Se ejecutan cuando las corrés
- 📊 Muestran los resultados debajo
- 🔢 Tienen un número de orden de ejecución, por ejemplo `[1]:` para la primera


### Seleccionar una Celda

Para trabajar con una celda, primero tenés que **seleccionarla**:

- **Hacer clic** sobre la celda
- Verás un **borde coloreado** alrededor de color azul.


### Modos de una Celda

JupyterLab tiene dos modos principales:

#### Modo Comando

En este modo podés:
- Navegar entre celdas con las flechas ↑↓
- Crear, eliminar, copiar celdas
- Cambiar el tipo de celda

**Activarlo**: Presionar `Esc` o hacer clic fuera del área de texto

#### Modo Edición

En este modo podés:
- Escribir y editar el contenido de la celda
- Modificar código o texto

**Activarlo**: Presionar `Enter` o hacer doble clic dentro de la celda

### Botones en la celda

```{figure} ./E_jupyterlab/toolbar_cell.png
:label: fig-jupyterlab-toolbar-cell
:alt: CAPTURA: Botones en la celda activa
:align: center
Botones en la celda activa
```

De izquierda a derecha, estos botones aparecen al seleccionar una celda:

1. **📑 Duplicar celda**: Crea una copia exacta de la celda seleccionada debajo de ella
2. **⬆️ Mover celda arriba**: Intercambia posición con la celda de arriba
3. **⬇️ Mover celda abajo**: Intercambia posición con la celda de abajo
4. **⤴️ Crear celda vacía arriba**: Inserta una nueva celda vacía encima de la actual
5. **⤵️ Crear celda vacía abajo**: Inserta una nueva celda vacía debajo de la actual
6. **🗑️ Borrar celda**: Elimina la celda seleccionada (cuidado: no pide confirmación)


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

```{figure} ./E_jupyterlab/celda_estados.png
:label: fig-jupyterlab-celda_estados
:alt: CAPTURA: Espacio de trabajo con celdas antes y despues de ser ejecutadas
:align: center
Espacio de trabajo con celdas antes y despues de ser ejecutadas
```

### Entendiendo el Output

Después de ejecutar una celda:

- Aparece un **número entre corchetes**: `[1]:`
  - Este número indica el orden de ejecución
  - Si ves `[*]:` significa que está ejecutándose

- Debajo aparece el **resultado**:
  - Texto impreso con `print()`
  - Valores devueltos
  - Gráficos o tablas

:::{tip} Ejecutar Todo
Si querés ejecutar todas las celdas del notebook de una vez, andá a `Run` → `Run All Cells`. Esto es útil cuando abrís un notebook para la primera vez.
:::

### ¿Qué Pasa Si Hay un Error?

No te preocupes: **los errores son normales** y parte del aprendizaje. Si hay un error en el código, Python te lo mostrará.

```{figure} ./E_jupyterlab/error.png
:label: fig-jupyterlab-error
:alt: CAPTURA: Ejemplo de celda con error
:align: center
Ejemplo de celda con error.
```

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

La opción "Raw" es para uso avanzado de la herramienta, y como tal no lo veremos ahora.

---

## Guardando Tu Trabajo

Es importante guardar tu progreso regularmente, pero tenés que tener algo presente. Tu trabajo está **únicamente** en tu computadora, y en un lugar dentro del navegador, no como un archivo en el disco. Para pasar tu trabajo a otra computadora, o para compartirlo, o para hacer un backup, es necesario descargar el cuaderno.

### Guardar el Notebook

**Opción 1**: Atajo de teclado
- `Ctrl + S` (Windows/Linux)
- `Cmd + S` (Mac)

**Opción 2**: Menú
- `File` → `Save Notebook`

**Opción 3**: Botón
- Icono de disquete 💾 en la barra de herramientas

:::{important} Guardado Automático
JupyterLab guarda automáticamente tu trabajo cada pocos minutos, pero es buena práctica **guardar manualmente** después de cambios importantes.
:::

### Indicador de Guardado

En la pestaña del notebook verás:
- **Punto negro (●)** al lado del nombre: hay cambios sin guardar
- **Sin punto**: todo guardado correctamente


```{figure} ./E_jupyterlab/estado_cuaderno.png
:label: fig-jupyterlab-estado-cuaderno
:alt: CAPTURA: Dos fichas con cuadernos, uno sin guardar y otro guardado.
:align: center
Captura de cómo se ve un cuaderno sin guardar y uno que lo está.
```

---

## El Kernel de Python

El **kernel** es el “motor” que ejecuta tu código Python. Es importante entender cómo funciona.

### ¿Qué es el Kernel?

Pensá en el kernel como un intérprete de Python que está corriendo en segundo plano. Cuando ejecutás una celda, el kernel:

1. Recibe tu código
2. Lo ejecuta
3. Te devuelve el resultado

```{figure} ./E_jupyterlab/kernel_funcionamiento.svg
:label: fig-kernel
:align: center
:width: 80%

Funcionamiento del kernel: ciclo de ejecución entre el notebook y el intérprete Python
```

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

El kernel “recuerda” que `x = 10` incluso en celdas separadas.

:::{important} Orden de Ejecución
El kernel recuerda el **orden en que ejecutaste** las celdas, no el orden en que están escritas. El número `[n]:` te indica esto.
:::

### Reiniciar el Kernel

A veces necesitás “empezar de cero”. Reiniciar el kernel **borra toda la memoria**.

**Cuándo reiniciar:**
- 🔄 Querés empezar desde el principio
- 🐛 Hay comportamientos extraños
- 🚫 El código se quedó “colgado”

**Cómo reiniciar:**

**Opción 1**: Menú
- `Kernel` → `Restart Kernel...`

**Opción 2**: Botón
- Icono de reinicio ⟳ en la barra de herramientas

:::{tip} Restart and Run All
La opción más útil suele ser **“Restart Kernel and Run All Cells”**: reinicia todo y ejecuta todas las celdas en orden desde el principio. Perfecto para verificar que tu código funcione correctamente.
:::

### Interrumpir la Ejecución

Si una celda está tardando demasiado o entró en un lazo infinito:

**Opción 1**: Botón
- Icono de detener ⏹️ en la barra de herramientas

**Opción 2**: Menú
- `Kernel` → `Interrupt Kernel`

**Opción 3**: Atajo
- Presionar `I, I` (la letra I dos veces en modo comando)


```{figure} ./E_jupyterlab/advertencia_reinicio.png
:label: fig-jupyterlab-advertencia-reinicio
:alt: CAPTURA: Aviso al reiniciar el kernel
:align: center
Advertencia al momento de reiniciar el Kernel.
```

```{figure} ./E_jupyterlab/celda_colgada.png
:label: fig-jupyterlab-celda-colgada
:alt: CAPTURA: Celda que quedó trabada
:align: center
Celda que esta trabada y que botones podemos usar para frenarla.
```

En algunos casos, detener la ejecución no es suficiente, y es necesario usar "Reiniciar kernel ⟳".

---

## Trabajando con Múltiples Notebooks

Podés tener varios notebooks abiertos al mismo tiempo.

### Abrir Múltiples Archivos

Simplemente hacé doble clic en varios archivos `.ipynb`. Cada uno se abrirá en una pestaña nueva.

```{figure} ./E_jupyterlab/multiples_cuadernos.png
:label: fig-jupyterlab-multiples_cuadernos
:alt: CAPTURA: Múltiples cuadernos abiertos
:align: center
Área de trabajo mostrando 3 pestañas abiertas con diferentes notebooks: “01_variables.ipynb”, “02_operadores.ipynb”, “03_control.ipynb”.
```

### Cambiar entre Pestañas

- **Clic** en la pestaña para cambiar
- `Ctrl + Shift + [` y `Ctrl + Shift + ]` para navegar entre pestañas

### Organizar la Pantalla

Podés ver dos notebooks lado a lado:

1. **Arrastrá** la pestaña de un notebook hacia un costado
2. Se dividirá la pantalla
3. Soltá la pestaña

```{figure} ./E_jupyterlab/area_trabajo.png
:label: fig-jupyterlab-area-trabajo-2
:alt: CAPTURA: Múltiples cuadernos de par en par
:align: center
Área de trabajo mostrando dos secciones en paralelo
```
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

```{figure} ./E_jupyterlab/complete.png
:label: fig-jupyterlab-autocompletado
:alt: CAPTURA: Vista de autocompletado
:align: center
Sugerencia de completado de funciones con `print`
```

:::{tip} Explorar Métodos
Si tenés una variable y querés ver qué métodos tiene, escribí el nombre, un punto, y presioná Tab:
```python
lista = [1, 2, 3]
lista.[Tab]  # Te mostrará: append, remove, sort, etc.
```
:::

### Ver Documentación

Para ver información sobre una función:

1. Poné el cursor sobre el nombre de la función
2. Presioná `Shift + Tab`
3. Verás un popup con la documentación


```{figure} ./E_jupyterlab/docstring.png
:label: fig-jupyterlab-docstring
:alt: CAPTURA: Vista del docstring de `print`
:align: center
Popup de documentación mostrando información sobre la función print(), incluyendo su firma, parámetros y descripción.
```

Presionar `Shift + Tab` **varias veces** expande la documentación.

### Buscar en el Notebook

Para buscar texto en tu notebook:

1. Presioná `Ctrl + F`
2. Aparecerá una barra de búsqueda
3. Escribí lo que buscás
4. Usá las flechas para navegar entre resultados

Va a mostrar cuantas veces aparece también.

```{figure} ./E_jupyterlab/busqueda.png
:label: fig-jupyterlab-busqueda
:alt: CAPTURA: Buscando en un archivo
:align: center
Barra de búsqueda en la parte superior del notebook con un término buscado y resaltado en amarillo en las celdas.
```

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

**Síntomas:** La celda muestra `[*]:` por mucho tiempo

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

Los notebooks son **perfectos para experimentar**, con una celda para cada experimento del ejercicio.

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
- Buscá “JupyterLab tutorial español” en YouTube
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
## Glosario

Este glosario contiene los términos clave sobre JupyterLab y notebooks interactivos que se trataron en este capítulo.

:::{glossary}
JupyterLab
:  Entorno de desarrollo interactivo basado en web que permite escribir y ejecutar código Python en {term}`notebooks <notebook>`. Interfaz moderna que combina código, texto, visualizaciones y resultados. Sucesor de Jupyter Notebook.

Jupyter
:  Proyecto open source que desarrolla herramientas para computación interactiva. Incluye {term}`JupyterLab`, Jupyter Notebook y JupyterHub. Nombre viene de Julia, Python y R (lenguajes principales).

JupyterLite
:  Versión de {term}`JupyterLab` que funciona completamente en el navegador sin servidor. No requiere instalación. Usa WebAssembly para ejecutar Python en el navegador. Ideal para educación.

Notebook
:  El cuaderno es un documento interactivo que combina {term}`celdas<cell>` de código ejecutable, texto explicativo (Markdown), y resultados/visualizaciones. Extensión `.ipynb` (IPython Notebook). También conocido como **cuaderno**.

Cell
:  La celda es la unidad básica de un {term}`notebook`. Puede ser de {term}`código<Code cell>` (ejecutable) o {term}`Markdown` (texto). Se ejecutan individualmente con Shift+Enter.

Code cell
:  La celda de código es un tipo de {term}`celda<cell>` que contiene código Python ejecutable. Al ejecutarla, muestra el resultado debajo. Identificable por `[ ]:` a la izquierda. Puede tener múltiples líneas.

Markdown cell
:  {term}`celda<cell>` que contiene texto con formato usando {term}`Markdown`. Se renderiza como HTML al ejecutarla. Útil para explicaciones, títulos, listas. No ejecuta código.

Markdown
:  Lenguaje de marcado ligero para dar formato a texto. Usa símbolos simples: `#` para títulos, `**negrita**`, `*cursiva*`, `- lista`. Se convierte a HTML. Fácil de leer y escribir.

Kernel
:  Proceso que ejecuta el código en un {term}`notebook`. Mantiene el estado (variables, funciones definidas). Python tiene su propio kernel. Puede reiniciarse si hay problemas.

Restart kernel
:  Reiniciar el kernel es detener y volver a iniciar el {term}`kernel`, limpiando toda la memoria. Todas las variables y funciones se pierden. Útil cuando hay errores o para empezar de cero.

Command mode
:  Modo de {term}`notebook` para navegar y manipular celdas. Borde azul en la celda activa. Atajos: `A` (insertar arriba), `B` (insertar abajo), `DD` (borrar), `M` (Markdown), `Y` (código).

Edit mode
:  El **modo edición** en los {term}`notebook` se utiliza para editar contenido de una celda. Borde verde en la celda activa. Atajos normales de editor. Entrar: presionar `Enter`. Salir: presionar `Esc`.

Run cell
:  Procesar el contenido de una **celda**. En celdas de código, ejecuta el código y muestra resultado. En Markdown, renderiza el texto. Atajo: `Shift+Enter` (ejecuta y avanza).

Output
:  La salida, es el resultado que aparece debajo de una {term}`celda de código<Code cell>` después de ejecutarla. Puede ser texto, números, gráficos, errores. Se guarda en el {term}`notebook`.

[ ]
:  Indicador a la izquierda de una {term}`celda de código<Code cell>`. Muestra número de ejecución. `[ ]` = no ejecutada, `[1]` = primera ejecución, `[*]` = ejecutando.

Out[ ]
:  Indicador del {term}`output` de una celda. `Out[1]` corresponde a `[1]`. No todas las celdas tienen output (ej: asignaciones). Solo aparece si hay valor de retorno.

Explorador de archivos
:  Panel lateral izquierdo de {term}`JupyterLab` que muestra directorios y archivos. Permite navegar, crear, renombrar, eliminar archivos. Similar al explorador de Windows/Finder.

Main area
:  El área de trabajo, o workspace, es la zona central de {term}`JupyterLab` donde se abren {term}`notebooks <notebook>`, archivos, terminales. Puede tener múltiples pestañas. Arrastrar pestañas divide la pantalla.

Launcher

:  El lanzador es la pantalla inicial de {term}`JupyterLab` para crear nuevos {term}`notebooks <notebook>`, archivos, consolas, terminales. Aparece al abrir JupyterLab o cerrar todas las pestañas.

.ipynb
: Extensión de archivos de {term}`notebook` Jupyter. Significa “IPython Notebook”. Es un archivo JSON que guarda celdas, código, outputs y metadata. Formato estándar de Jupyter.

IPython
: Shell interactivo mejorado de Python. Base del {term}`kernel` de Jupyter. Agrega funcionalidades: autocompletado, magic commands, historial. “Interactive Python”.

Magic Command
:  Los **comandos mágicos** son instrucciones especiales de {term}`IPython` que empiezan con `%` (línea) o `%%` (celda). Ejemplos: `%timeit`, `%matplotlib inline`, `%%bash`. Funciones útiles pre-construidas.

Autocompletado
:  Funcionalidad que sugiere completar código mientras escribís. Presionar `Tab` muestra opciones. Ahorra tiempo y evita errores de tipeo. Funciona con variables, funciones, métodos.

Introspección
:  Examinar propiedades de un objeto en Python. En Jupyter: `objeto?` muestra documentación, `objeto??` muestra código fuente. `Tab` después de `objeto.` muestra métodos/atributos.

Shift+Enter
:  Atajo de teclado principal en {term}`notebooks <notebook>`. Ejecuta la {term}`cell` actual y avanza a la siguiente (o crea una nueva). El más usado en Jupyter.

Ctrl+Enter
:  Atajo para ejecutar {term}`cell` actual SIN avanzar a la siguiente. Útil cuando querés ejecutar la misma celda múltiples veces seguidas.

Alt+Enter
:  Atajo para ejecutar {term}`cell` actual e insertar una nueva celda vacía debajo. Útil para flujo de trabajo rápido al crear notebooks nuevos.

Checkpoint
:  El punto de guardado es una copia de seguridad automática del {term}`notebooks <notebook>` en cierto momento. JupyterLab guarda periódicamente. Puede revertir a checkpoints anteriores desde menú File.

Export
:  Convertir un {term}`notebook** a otros formatos. Opciones: HTML, PDF, Python (.py), Markdown, LaTeX. Útil para compartir o crear documentos estáticos.

Inspector
:  Herramienta (extensión) que muestra todas las variables activas en el {term}`kernel` con sus valores y tipos. Útil para {term}`debugging`. No siempre está disponible en todas las instalaciones.

Terminal
:  Consola de sistema operativo integrada en {term}`JupyterLab`. Permite ejecutar comandos shell (bash, cmd). Útil para instalar paquetes, git, operaciones de archivos.

Consola
:  Shell interactivo de Python integrado en {term}`JupyterLab`. Similar a ejecutar `python` en terminal. Útil para pruebas rápidas sin crear {term}`notebook`. También conocida como **consola**.

Pestaña
:  Documento abierto en el {term}`área de trabajo<Main area>` de JupyterLab. Puede ser {term}`notebook`, archivo, terminal, consola. Múltiples tabs permiten trabajar con varios archivos simultáneamente.

Widget interactivo
:  Elemento de interfaz gráfica en {term}`notebook` (botones, sliders, dropdowns). Permite interacción sin editar código. Requiere biblioteca `ipywidgets`. Útil para visualizaciones dinámicas.

Extension
:  Plugin que agrega funcionalidades a {term}`JupyterLab`. Ejemplos: temas, linters, debuggers, variable inspectors. Se instalan con `pip` o desde el navegador de extensiones.

Kernel busy
:  Estado del {term}`kernel` cuando está ejecutando código. Indicador en esquina superior derecha (círculo lleno). No se pueden ejecutar otras celdas hasta que termine.

Kernel idle
:  Estado del {term}`kernel` cuando no está ejecutando nada. Indicador en esquina superior derecha (círculo vacío). Listo para ejecutar código.

Debugger
:  El depurador es una herramienta para encontrar errores ejecutando código paso a paso. JupyterLab tiene debugger visual integrado. Permite inspeccionar variables, establecer breakpoints, ver stack.

Breakpoint
:  Marcador en código donde el {term}`Debugger` pausará la ejecución. Permite inspeccionar estado del programa en ese punto. Se establece en el margen izquierdo de la celda.

Linter
:  Herramienta que analiza código en busca de errores de estilo y posibles bugs sin ejecutarlo. Ejemplo: flake8, pylint. Algunas extensiones integran linters en JupyterLab.
:::

