---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'JupyterLab - Parte 2/2' -->

# <!-- fit --> Workflows
## Trabajo eficiente en Jupyter
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Transformar el uso básico en un proceso productivo y profesional.
- Gancho: "¿Alguna vez pasaron horas arreglando un error para darse cuenta de que solo tenían que reiniciar el kernel? Hoy aprendemos a trabajar en serio."
-->

---

<!-- _header: 'Workflow típico' -->

# Flujo de trabajo

**1. Exploración inicial:**
* Cargar datos
* Ver primeras filas
* Entender estructura

**2. Limpieza:**
* Corregir errores
* Manejar datos faltantes

**3. Análisis:**
* Calcular estadísticas
* Visualizar

**4. Documentar:**
* Añadir conclusiones
* Exportar resultados

<!--
NOTAS DEL ORADOR:
- El ciclo de vida de un notebook no es lineal, es iterativo.
- Pero la estructura final debe parecer lineal para que sea legible.
-->

---

<!-- _header: 'Desarrollo iterativo' -->

# Iterar rápidamente

**Ventaja de notebooks:**
```python
# Celda 1: Cargar datos (ejecutar 1 vez)
datos = cargar_dataset()

# Celda 2: Probar diferentes análisis
# Modificar y re-ejecutar solo esta celda
resultado = analizar(datos, metodo="opcion1")
print(resultado)
```

**No recargar datos cada vez**
* Más rápido
* Menos errores

<!--
NOTAS DEL ORADOR:
- Esta es la "Killer Feature" de Jupyter.
- Si cargar datos tarda 10 minutos, no querés hacerlo cada vez que cambiás una coma en el gráfico.
-->

---

<!-- _header: 'Debugging' -->

# Depurar en notebooks

**Print debugging:**
```python
def procesar(datos):
    print(f"Entrada: {datos[:5]}")  # Ver primeros
    resultado = transformar(datos)
    print(f"Después: {resultado[:5]}")
    return resultado
```

**Variables intermedias:**
```python
# Dividir en pasos
paso1 = filtrar(datos)
paso2 = transformar(paso1)
paso3 = agregar(paso2)
```

**Ver variables:** `%whos`

<!--
NOTAS DEL ORADOR:
- En scripts tradicionales, usás un debugger.
- En notebooks, usás la inspección de variables vivas.
-->

---

<!-- _header: 'Testing rápido' -->

# Probar funciones

**Verificar en celda separada:**
```python
# Celda 1: Definir función
def calcular_promedio(numeros):
    return sum(numeros) / len(numeros)

# Celda 2: Tests rápidos
assert calcular_promedio([1, 2, 3]) == 2
assert calcular_promedio([10]) == 10
print("✅ Tests pasados")
```

**Fácil de modificar y re-probar**

<!--
NOTAS DEL ORADOR:
- Unit testing informal.
- Permite verificar la lógica antes de aplicarla a millones de datos.
-->

---

<!-- _header: 'Organización' -->

# Dividir en secciones

**Usar títulos Markdown:**
```markdown
# 1. Carga de datos

# 2. Preprocesamiento

# 3. Análisis exploratorio

# 4. Modelado

# 5. Resultados
```

**Colapsar secciones:**
* Click en barra lateral izquierda
* Ver solo lo que importa

<!--
NOTAS DEL ORADOR:
- Usar la tabla de contenidos (ToC) es vital en notebooks largos.
-->

---

<!-- _header: 'Reutilizar código' -->

# Importar desde archivos

**Cuando código crece:**
```python
# archivo: utilidades.py
def funcion_util1():
    pass

def funcion_util2():
    pass
```

**En notebook:**
```python
# Importar módulo local
from utilidades import funcion_util1

# Recargar si modifica
%load_ext autoreload
%autoreload 2
```

<!--
NOTAS DEL ORADOR:
- Regla: Si copias y pegas una función entre notebooks, movela a un archivo `.py`.
- `autoreload` es magia: actualiza el código importado sin reiniciar el kernel.
-->

---

<!-- _header: 'Configuración inicial' -->

# Celda de setup

**Primera celda estándar:**
```python
# Imports
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Configuración
%matplotlib inline
pd.set_option('display.max_rows', 100)
plt.style.use('seaborn-v0_8')

# Semilla para reproducibilidad
np.random.seed(42)

print("✅ Setup completo")
```

<!--
NOTAS DEL ORADOR:
- Convención: Todos los imports arriba.
- Configuración global evita sorpresas más adelante.
-->

---

<!-- _header: 'Evitar errores comunes' -->

# Buenas prácticas

**❌ Ejecutar celdas fuera de orden:**
```python
# Celda 5
resultado = procesar(datos)

# Celda 3 (ejecutar después)
datos = cargar()  # ❌ Orden incorrecto
```

**✅ Mantener orden lógico:**
* Ejecutar todo desde arriba
* Restart & Run All periódicamente

<!--
NOTAS DEL ORADOR:
- El estado oculto es el enemigo.
- Si el notebook solo funciona si ejecutás la celda 5 antes de la 3, está roto.
-->

---

<!-- _header: 'Estado limpio' -->

# Reiniciar regularmente

**Verificar reproducibilidad:**
1. Kernel → Restart & Clear Output
2. Cell → Run All

**¿Todo funciona?**
* ✅ Código reproducible
* ❌ Dependencias ocultas

**Hacer esto antes de compartir**

<!--
NOTAS DEL ORADOR:
- La prueba de fuego.
- Si falla, arreglar el orden de las celdas.
-->

---

<!-- _header: 'Versionado' -->

# Git con notebooks

**Problema:** `.ipynb` es JSON
* Diffs ilegibles
* Conflictos difíciles

**Soluciones:**
```bash
# 1. Limpiar outputs antes de commit
jupyter nbconvert --clear-output notebook.ipynb

# 2. Usar herramientas especiales
pip install nbdime
nbdiff notebook1.ipynb notebook2.ipynb

# 3. Exportar a .py también
jupyter nbconvert --to python notebook.ipynb
```

<!--
NOTAS DEL ORADOR:
- Los gráficos en base64 dentro del JSON hacen que los diffs de git sean gigantes e inútiles.
- `nbdime` (Notebook Diff & Merge) es la herramienta estándar.
-->

---

<!-- _header: 'Compartir notebooks' -->

# Exportar para otros

**HTML (más común):**
```bash
jupyter nbconvert --to html notebook.ipynb
```
* Se ve en cualquier navegador
* Incluye outputs y gráficos

**PDF (presentaciones):**
```bash
jupyter nbconvert --to pdf notebook.ipynb
```
* Requiere LaTeX instalado

<!--
NOTAS DEL ORADOR:
- HTML es universal. El PDF es más formal.
-->

---

<!-- _header: 'NBViewer' -->

# Compartir online

**NBViewer:**
* nbviewer.jupyter.org
* Pegar URL de GitHub
* Renderiza notebook

**GitHub:**
* Renderiza `.ipynb` automáticamente
* Sin necesidad de herramientas extra

**Colab:**
* colab.research.google.com
* Ejecutar notebooks en la nube

<!--
NOTAS DEL ORADOR:
- GitHub a veces es lento renderizando. NBViewer es el backup confiable.
-->

---

<!-- _header: 'Extensiones útiles' -->

# Potenciar JupyterLab

**Instalar extensiones:**
```bash
pip install jupyterlab-git
pip install jupyterlab-lsp
pip install jupyterlab-code-formatter
```

**Habilitar:**
* Settings → Extension Manager
* Buscar e instalar

**Populares:**
* Git integration
* Code formatter (black/autopep8)
* Variable Inspector
* Table of Contents

<!--
NOTAS DEL ORADOR:
- JupyterLab es extensible.
- El formateador de código es esencial para mantener PEP 8 sin esfuerzo.
-->

---

<!-- _header: 'Atajos productivos' -->

# Atajos avanzados

**Modo comando:**
* `Shift + M` → fusionar celdas
* `Ctrl + Shift + -` → dividir celda
* `00` → reiniciar kernel
* `H` → mostrar todos los atajos

**Modo edición:**
* `Ctrl + ]` → indentar
* `Ctrl + [` → desindentar
* `Ctrl + /` → comentar/descomentar

<!--
NOTAS DEL ORADOR:
- `00` (cero cero) es el atajo secreto para reiniciar rápido.
-->

---

<!-- _header: 'Snippets' -->

# Fragmentos reutilizables

**Crear templates:**
```python
# Template de análisis
"""
# Análisis: [NOMBRE]
Fecha: [FECHA]
Autor: [TU NOMBRE]

## Objetivo
[DESCRIBIR]

## Datos
[FUENTE]
"""
```

**Guardar en archivos `.ipynb` base**

<!--
NOTAS DEL ORADOR:
- Tener un "esqueleto" de notebook ahorra tiempo de configuración.
-->

---

<!-- _header: 'Performance' -->

# Medir y optimizar

**Celda específica:**
```python
%%timeit
# Código a medir
resultado = sum(range(10000))
```

**Función específica:**
```python
%timeit sum(range(10000))
```

**Profile completo:**
```python
%prun funcion_compleja(datos)
```

<!--
NOTAS DEL ORADOR:
- No adivinar qué es lento. Medirlo.
-->

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis

**1. Setup (celda 1):**
```python
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
```

**2. Cargar (celda 2):**
```python
df = pd.read_csv("datos.csv")
print(f"Filas: {len(df)}")
df.head()
```

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis (cont.)

**3. Limpiar (celda 3):**
```python
# Eliminar nulos
df = df.dropna()

# Convertir tipos
df['fecha'] = pd.to_datetime(df['fecha'])
```

**4. Analizar (celda 4):**
```python
# Estadísticas
stats = df.describe()

# Visualizar
df['columna'].plot(kind='hist')
plt.title("Distribución")
plt.show()
```

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis (cont.)

**5. Conclusiones (celda Markdown):**
```markdown
## Resultados

* Se encontraron X patrones
* Variable Y es significativa
* Recomendaciones:
  1. Primera acción
  2. Segunda acción
```

**6. Exportar:**
* File → Export → HTML

---

<!-- _header: 'Tips finales' -->

# Consejos prácticos

**✅ Hacer:**
* Reiniciar kernel frecuentemente
* Documentar con Markdown
* Nombrar notebooks descriptivamente
* Limpiar outputs antes de commit
* Ejecutar todo antes de compartir

**❌ Evitar:**
* Celdas muy largas (>50 líneas)
* Variables globales excesivas
* Ejecutar fuera de orden
* Código sin documentar

<!--
NOTAS DEL ORADOR:
- Resumen de higiene de notebooks.
-->

---

<!-- _header: 'Alternativas' -->

# Otros entornos similares

**Google Colab:**
* Online, gratis
* GPU disponible
* Ideal para ML

**VSCode:**
* Soporte nativo `.ipynb`
* Integrado con IDE

**Databricks:**
* Colaborativo
* Para Big Data

<!--
NOTAS DEL ORADOR:
- JupyterLab no es la única opción, pero es el estándar de facto.
-->

---

<!-- _class: inverse -->

# <!-- fit --> ¡JupyterLab completo!
## Entorno productivo para Python

---

<!-- _header: 'Resumen' -->

# Para recordar

**JupyterLab permite:**
* Desarrollo iterativo
* Documentación integrada
* Visualizaciones inline
* Compartir resultados

**Workflow:**
1. Setup inicial
2. Explorar datos
3. Analizar iterativamente
4. Documentar conclusiones
5. Exportar resultados

**Mantener reproducibilidad:**
* Reiniciar kernel
* Ejecutar todo
* Limpiar outputs

---

<!-- _class: centered -->

# ¿Preguntas?