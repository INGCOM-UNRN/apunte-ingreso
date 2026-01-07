---
marp: true
theme: default
paginate: true
header: 'Guía de JupyterLab'
footer: 'Introducción práctica para estudiantes'
style: |
  section {
    font-size: 26px;
  }
  h1 {
    color: #1976d2;
  }
  code {
    background-color: #f5f5f5;
  }
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

---

## 2. Panel Lateral Izquierdo

Este panel muestra todos los archivos disponibles:

📁 **Carpetas**: Organizan los notebooks por tema
📓 **Notebooks** (archivos `.ipynb`): Los cuadernos de práctica
📄 **Otros archivos**: Datos, imágenes, etc.

**Similar al explorador de archivos de Windows o Finder en Mac**

---

## 3. Área de Trabajo Central

**El área más importante**

Aquí es donde abrís y trabajás con tus notebooks

Podés tener **múltiples notebooks abiertos** al mismo tiempo, organizados en pestañas

---

## 4. Barra de Estado Inferior

Muestra información útil:

- 🐍 El kernel que está ejecutándose (Python)
- 🔌 Estado de la conexión
- 📋 Información del archivo actual

---

<!-- _class: lead -->

# Trabajar con Notebooks

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

---

<!-- _class: lead -->

# Editando Celdas

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

---

## Crear una Nueva Celda

**Opción 1: Botón**
- Clic en el botón **➕** en la barra de herramientas

**Opción 2: Teclado (en modo comando)**
- `A` → Insertar celda **arriba** (Above)
- `B` → Insertar celda **abajo** (Below)

💡 **Tip:** `B` es el más usado (insertar abajo)

---

## Eliminar una Celda

**Opción 1: Menú**
- `Edit` → `Delete Cells`

**Opción 2: Teclado (en modo comando)**
- Presioná `D` dos veces: `D`, `D`

⚠️ **Cuidado:** No hay confirmación
Si eliminaste por error: `Ctrl + Z` para deshacer

---

## Cambiar el Tipo de Celda

**Opción 1: Menú desplegable**
- En la barra de herramientas: `Code` o `Markdown`

**Opción 2: Teclado (en modo comando)**
- `Y` → Convertir a celda de **código**
- `M` → Convertir a celda de **Markdown**

---

<!-- _class: lead -->

# Guardando Tu Trabajo

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

---

<!-- _class: lead -->

# El Kernel de Python

---

## ¿Qué es el Kernel?

El **kernel** es el "motor" que ejecuta tu código Python

**Pensalo como un intérprete de Python** corriendo en segundo plano

**Cuando ejecutás una celda:**
1. 📤 El notebook envía tu código al kernel
2. ⚙️ El kernel ejecuta el código
3. 📥 El kernel devuelve el resultado

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

---

## Orden de Ejecución

⚠️ **Importante:** El kernel recuerda el **orden en que ejecutaste** las celdas, no el orden en que están escritas

**El número `In [n]:` te indica el orden de ejecución**

```python
In [2]: y = x + 5   # Ejecutada segunda
In [1]: x = 10      # Ejecutada primera
```

Aunque `y = x + 5` está primero visualmente, `x = 10` se ejecutó primero

---

## Reiniciar el Kernel

A veces necesitás **"empezar de cero"**

Reiniciar el kernel **borra toda la memoria**

**Cuándo reiniciar:**
- ❌ Variables no definidas pero deberían estarlo
- 🔄 Querés ejecutar todo desde el principio
- 🐛 Comportamiento extraño del código

---

## Cómo Reiniciar el Kernel

**Opción 1: Solo reiniciar**
- `Kernel` → `Restart Kernel`

**Opción 2: Reiniciar y ejecutar todo**
- `Kernel` → `Restart Kernel and Run All Cells`
- **Recomendado:** Verifica que todo funcione en orden

**Opción 3: Botón**
- Icono 🔄 en la barra de herramientas

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

---

<!-- _class: lead -->

# Atajos de Teclado Esenciales

---

## Modo Comando (Esc)

| Atajo | Acción |
|-------|--------|
| `A` | Insertar celda arriba |
| `B` | Insertar celda abajo |
| `D`, `D` | Eliminar celda |
| `M` | Convertir a Markdown |
| `Y` | Convertir a código |
| `Ctrl + S` | Guardar |

---

## Modo Edición (Enter)

| Atajo | Acción |
|-------|--------|
| `Shift + Enter` | Ejecutar y pasar a siguiente |
| `Ctrl + Enter` | Ejecutar sin cambiar celda |
| `Tab` | Autocompletar |
| `Shift + Tab` | Ver documentación |
| `Esc` | Salir a modo comando |

---

## Ver Todos los Atajos

**Dentro de JupyterLab:**

Presioná `Ctrl + Shift + C` (o `Cmd + Shift + C` en Mac)

Verás una lista completa de todos los atajos disponibles

---

<!-- _class: lead -->

# Buenas Prácticas

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

---

## 2. Reiniciá y Ejecutá Todo Regularmente

Cada tanto, es buena idea:

1. `Kernel` → `Restart Kernel and Run All Cells`
2. Verificar que todo funcione en orden

Esto asegura que tu notebook funciona correctamente de principio a fin

---

## 3. Guardá Frecuentemente

Acostumbrate a presionar `Ctrl + S` regularmente

**No esperes a terminar todo para guardar**

Guardá después de:
- ✅ Resolver un ejercicio
- ✅ Escribir código importante
- ✅ Hacer cambios significativos

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

---

<!-- _class: lead -->

# Solución de Problemas

---

## Problema: El Kernel No Responde

**Síntomas:** La celda muestra `In [*]:` por mucho tiempo

**Soluciones:**
1. ⏳ Esperar unos segundos (puede ser un cálculo lento)
2. ⏹️ Interrumpir el kernel (botón stop)
3. 🔄 Si persiste, reiniciar el kernel

---

## Problema: Variables No Definidas

**Error:** `NameError: name 'x' is not defined`

**Causa:** La celda que define `x` no fue ejecutada

**Solución:**
1. Buscá la celda donde se define la variable
2. Ejecutala con `Shift + Enter`
3. Volvé a ejecutar la celda con error

💡 **Tip:** Hacé `Restart and Run All` si no estás seguro

---

## Problema: Cambios No Guardados

**Síntomas:** Ves el punto negro (●) en la pestaña

**Solución:**
- Presioná `Ctrl + S` para guardar

---

## Problema: No Encuentro un Archivo

**Soluciones:**
1. Verificá que estás en el directorio correcto
2. Usá la barra de búsqueda del file browser
3. Revisá que el archivo tenga extensión `.ipynb`

---

<!-- _class: lead -->

# Estrategia de Aprendizaje

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

---

## Trabajar con Ejercicios

Cuando trabajes en ejercicios:

1. 📖 **Leé** el enunciado completo
2. 🤔 **Pensá** la solución antes de escribir código
3. ✍️ **Escribí** tu código en una nueva celda
4. ▶️ **Ejecutá** y probá con diferentes valores
5. 🔍 **Compará** con la solución propuesta (si hay)

---

## Experimentar es Clave

💡 **No tengas miedo de modificar el código**

La mejor forma de aprender es experimentando

Si algo sale mal:
- ✅ Podés volver a la versión original
- ✅ Reiniciar el kernel y empezar de nuevo
- ✅ Cada error es una oportunidad de aprender

---

<!-- _class: lead -->

# Checklist de Habilidades

---

## ✅ Navegación Básica

- [ ] Acceder a JupyterLab en el navegador
- [ ] Navegar por el explorador de archivos
- [ ] Abrir un notebook existente
- [ ] Identificar los componentes de la interfaz

---

## ✅ Trabajo con Celdas

- [ ] Diferenciar celdas de código y Markdown
- [ ] Seleccionar una celda
- [ ] Cambiar entre modo comando y edición
- [ ] Ejecutar una celda de código
- [ ] Crear una nueva celda
- [ ] Eliminar una celda

---

## ✅ Ejecución de Código

- [ ] Ejecutar código Python básico
- [ ] Leer mensajes de error
- [ ] Modificar código y volver a ejecutar
- [ ] Ver los resultados (output)

---

## ✅ Gestión del Kernel

- [ ] Entender qué es el kernel
- [ ] Reiniciar el kernel
- [ ] Ejecutar todas las celdas
- [ ] Interrumpir una ejecución

---

## ✅ Productividad

- [ ] Guardar el notebook
- [ ] Usar autocompletado (Tab)
- [ ] Ver documentación (Shift + Tab)
- [ ] Usar al menos 3 atajos de teclado

---

## ✅ Buenas Prácticas

- [ ] Ejecutar celdas en orden
- [ ] Documentar mi código
- [ ] Experimentar con modificaciones
- [ ] Buscar soluciones a errores comunes

---

<!-- _class: lead -->

# Resumen

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

---

## Conceptos Clave (cont.)

**Kernel:**
- Motor que ejecuta el código
- Mantiene memoria de lo ejecutado
- Se puede reiniciar para empezar de cero

**Modos:**
- Comando (azul) → Navegación
- Edición (verde) → Escribir

---

## Atajos Esenciales

| Atajo | Acción |
|-------|--------|
| `Shift + Enter` | Ejecutar celda |
| `A` / `B` | Insertar celda arriba/abajo |
| `D`, `D` | Eliminar celda |
| `M` / `Y` | Markdown / Código |
| `Ctrl + S` | Guardar |
| `Esc` / `Enter` | Modo comando / edición |

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

---

## ¡A Programar!

Recordá:

1. 🎯 **Empezá con calma**: No intentes aprender todo de una vez
2. 🔬 **Experimentá**: Probá, modificá, rompé cosas (y arreglalas)
3. 🐛 **Los errores son buenos**: Cada error es una oportunidad
4. 💪 **Practicá regularmente**: Mejor 30 min diarios que 3 horas una vez
5. ❓ **Preguntá**: Si no entendés algo, buscá ayuda

---

<!-- _paginate: false -->

# ¡Éxito en Tu Aprendizaje!

**Cada programador experto comenzó donde estás vos ahora.**

Lo que los distingue es la **práctica constante** y la **curiosidad**.

**¡Vos también podés lograrlo!** 🐍✨

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
