---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'JupyterLab - Parte 1/2' -->

# <!-- fit --> JupyterLab
## Entorno interactivo
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Familiarizarse con la herramienta de trabajo del curso.
- Gancho: "¿Y si les dijera que pueden escribir código, ver los resultados, tomar notas y hacer gráficos, todo en el mismo lugar?"
-->

---

<!-- _header: '¿Qué es JupyterLab?' -->

# JupyterLab

**Entorno de desarrollo interactivo:**
* Notebooks con código + texto + gráficos
* Ejecutar código por celdas
* Ideal para aprendizaje y exploración
* Usado en ciencia de datos e investigación

**Combina código, documentación y resultados**

<!--
NOTAS DEL ORADOR:
- "Notebook" como cuaderno de laboratorio de un científico.
- REPL (Read-Eval-Print Loop) con esteroides.
-->

---

<!-- _header: 'Instalación' -->

# Instalar JupyterLab

**Con pip:**
```bash
pip install jupyterlab
```

**Iniciar:**
```bash
jupyter lab
```

**Se abre en navegador automáticamente**
* URL: `http://localhost:8888`

<!--
NOTAS DEL ORADOR:
- Recordar que es una aplicación web local. No necesita internet para funcionar.
-->

---

<!-- _header: 'Interfaz' -->

# Componentes principales

**Panel izquierdo:**
* Explorador de archivos
* Notebooks abiertos
* Índice del documento

**Área central:**
* Notebooks y archivos
* Pestañas múltiples

**Panel derecho (opcional):**
* Inspector de variables
* Ayuda contextual

<!--
NOTAS DEL ORADOR:
- Recorrido visual rápido por la interfaz.
- Mencionar la posibilidad de "drag & drop" de celdas.
-->

---

<!-- _header: 'Crear notebook' -->

# Nuevo notebook

**Pasos:**
1. Click en **+** (Launcher)
2. Seleccionar **Python 3** en Notebook
3. Se crea archivo `.ipynb`

**O desde menú:**
* File → New → Notebook

<!--
NOTAS DEL ORADOR:
- Explicar la extensión `.ipynb` (IPython Notebook).
-->

---

<!-- _header: 'Celdas' -->

# Tipos de celdas

**Code (código):**
```python
# Celda de código Python
x = 10
y = 20
print(x + y)
```

**Markdown (texto):**
```markdown
# Título
## Subtítulo

Este es **texto formateado** con Markdown.
```

**Cambiar tipo:** menú desplegable o atajos

<!--
NOTAS DEL ORADOR:
- La distinción clave: Code se ejecuta en Python, Markdown se renderiza como HTML.
-->

---

<!-- _header: 'Ejecutar celdas' -->

# Ejecutar código

**Ejecutar celda actual:**
* `Shift + Enter` → ejecuta y avanza
* `Ctrl + Enter` → ejecuta y queda en celda
* Botón ▶️ en toolbar

**Ejecutar todo:**
* Run → Run All Cells

**Estado:**
* `In [1]:` → ejecutada
* `In [*]:` → ejecutando
* Sin número → no ejecutada

<!--
NOTAS DEL ORADOR:
- `Shift + Enter` es el atajo más importante que aprenderán hoy.
- Explicar el asterisco `[*]` como indicador de "ocupado".
-->

---

<!-- _header: 'Atajos útiles' -->

# Atajos de teclado

**Modo comando (celda sin editar):**
* `A` → insertar celda arriba
* `B` → insertar celda abajo
* `DD` → eliminar celda
* `M` → cambiar a Markdown
* `Y` → cambiar a Code

**Modo edición (editando celda):**
* `Esc` → salir a modo comando
* `Tab` → autocompletar
* `Shift + Tab` → ayuda rápida

<!--
NOTAS DEL ORADOR:
- Productividad. No usar el mouse para todo.
- A (Above), B (Below).
-->

---

<!-- _header: 'Markdown en celdas' -->

# Formatear texto

**Títulos:**
```markdown
# Título 1
## Título 2
### Título 3
```

**Énfasis:**
```markdown
**negrita**
*cursiva*
`código en línea`
```

**Listas:**
```markdown
* Item 1
* Item 2
  * Sub-item
```

<!--
NOTAS DEL ORADOR:
- Ya vieron esto en la guía de Markdown, pero repasarlo aquí contextualiza su uso en Jupyter.
-->

---

<!-- _header: 'Markdown avanzado' -->

# Más formateo

**Código:**
````markdown
```python
def saludar():
    print("Hola")
```
````

**LaTeX:**
```markdown
Fórmula en línea: $E=mc^2$

Bloque:
$$
\int_a^b f(x)dx = F(b) - F(a)
$$
```

**Enlaces:**
```markdown
[Texto del enlace](https://ejemplo.com)
```

<!--
NOTAS DEL ORADOR:
- Soporte de LaTeX es excelente para ingeniería y matemáticas.
-->

---

<!-- _header: 'Variables persistentes' -->

# Estado compartido

**Las variables persisten entre celdas:**
```python
# Celda 1
x = 10
y = 20

# Celda 2 (ejecutar después)
print(x + y)  # 30
```

**⚠️ Cuidado con orden de ejecución:**
* Ejecutar celdas fuera de orden puede causar errores
* Reiniciar kernel limpia todo

<!--
NOTAS DEL ORADOR:
- El peligro oculto de los notebooks: El estado oculto.
- Si borrás una celda, la variable que definiste en ella sigue en memoria hasta reiniciar.
-->

---

<!-- _header: 'Kernel' -->

# Administrar el kernel

**Kernel = intérprete Python:**
* Mantiene variables en memoria
* Ejecuta el código

**Acciones:**
* **Restart** → limpia todo, empieza de cero
* **Restart & Run All** → limpia y ejecuta todo
* **Interrupt** → detener ejecución

**Menú Kernel o toolbar**

<!--
NOTAS DEL ORADOR:
- "Apagar y volver a encender" es la solución al 90% de los problemas en Jupyter.
- `Interrupt` si caemos en un lazo infinito.
-->

---

<!-- _header: 'Ayuda rápida' -->

# Obtener ayuda

**Símbolo ?:**
```python
# Ver documentación
print?
len?
list.append?
```

**Shift + Tab:**
* Presionar dentro de paréntesis
* Muestra firma de función
* Presionar 2 veces → más detalle

**?? para ver código fuente:**
```python
mi_funcion??
```

<!--
NOTAS DEL ORADOR:
- No hace falta ir a Google para todo. La documentación vive en el notebook.
-->

---

<!-- _header: 'Autocompletado' -->

# Tab completion

**Autocompletar:**
```python
# Escribir y presionar Tab
import ma<Tab>  # → math

# Métodos de objetos
texto = "hola"
texto.<Tab>  # Muestra todos los métodos
```

**Muy útil para explorar**

<!--
NOTAS DEL ORADOR:
- Excelente para descubrir métodos de objetos desconocidos.
-->

---

<!-- _header: 'Comandos mágicos' -->

# Magic commands

**Comandos especiales con %:**
```python
# Medir tiempo de ejecución
%timeit sum(range(1000))

# Ver variables
%whos

# Ejecutar script externo
%run mi_script.py

# Directorio actual
%pwd

# Listar archivos
%ls
```

<!--
NOTAS DEL ORADOR:
- Magics de línea (`%`) vs Magics de celda (`%%`).
-->

---

<!-- _header: 'Magic commands dobles' -->

# %% para celdas completas

**Comandos con %%:**
```python
%%timeit
# Todo el código de la celda
total = 0
for i in range(1000):
    total += i
```

```python
%%writefile archivo.txt
Este texto se escribe
en el archivo
```

<!--
NOTAS DEL ORADOR:
- `%%writefile` es genial para crear archivos de prueba.
-->

---

<!-- _header: 'Gráficos inline' -->

# Matplotlib en notebooks

**Mostrar gráficos:**
```python
import matplotlib.pyplot as plt

# Datos
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

# Crear gráfico
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('x²')
plt.title('Función cuadrática')
plt.show()
```

**Gráfico aparece bajo la celda**

<!--
NOTAS DEL ORADOR:
- Visualización de datos es el punto fuerte de Jupyter.
-->

---

<!-- _header: 'Organización' -->

# Estructura de notebook

**Buena práctica:**
```markdown
# Título del proyecto
Descripción breve

## 1. Importaciones
[celda con imports]

## 2. Configuración
[constantes y parámetros]

## 3. Carga de datos
[código para cargar]

## 4. Análisis
[celdas de análisis]

## 5. Conclusiones
[resumen y resultados]
```

<!--
NOTAS DEL ORADOR:
- Un notebook es una historia. Debe tener narrativa.
-->

---

<!-- _header: 'Guardar y exportar' -->

# Gestión de archivos

**Guardar:**
* `Ctrl + S` o `Cmd + S`
* Autoguardado activado por defecto

**Exportar:**
* File → Export Notebook As...
  * HTML (para compartir)
  * PDF (requiere LaTeX)
  * Python (.py)
  * Markdown

<!--
NOTAS DEL ORADOR:
- Exportar a HTML es la forma más fácil de enviar un trabajo práctico.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Notebook de análisis

**Celda 1 (Markdown):**
```markdown
# Análisis de números primos
Verificar si números son primos
```

**Celda 2 (Code):**
```python
def es_primo(n):
    """Verifica si n es primo."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
```

---

<!-- _header: 'Ejemplo práctico' -->

# Notebook de análisis (cont.)

**Celda 3 (Code):**
```python
# Encontrar primos hasta 50
primos = [n for n in range(2, 51) if es_primo(n)]
print(f"Primos encontrados: {len(primos)}")
print(primos)
```

**Celda 4 (Markdown):**
```markdown
## Resultados
Se encontraron 15 números primos entre 2 y 50.
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**JupyterLab:**
* Entorno interactivo
* Celdas de código y Markdown
* Ejecutar por partes
* Variables persistentes

**Atajos útiles:**
* `Shift + Enter` → ejecutar
* `B` → nueva celda abajo
* `M` / `Y` → cambiar tipo
* `Tab` → autocompletar

**Próximo:**
* Workflows y tips avanzados

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?